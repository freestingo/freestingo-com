---
author: Nicolò Traini
title: Esoterismi Vim
summary: comandi poco comuni e il loro utilizzo nel lavoro di tutti i giorni
slug: esoterismi-vim
translationKey: esoteric-vim
description: Una lista delle funzioni meno conosciute di Vim e il loro utilizzo nel lavoro di tutti i giorni
keywords: [programming, productivity, vim]
date: 2025-02-20
topics: [vim]
---

Questo è un compendio di funzioni poco conosciute ma utilissime di Vim che uso personalmente nel mio
editing giornaliero per risparmiare decine (se non centinaia) di ore di lavoro. L'articolo vuole
essere sia una risorsa per il vimmaro curioso in cerca di nuovi comandi, sia una risposta alla
domanda che il resto del mondo si pone quando per sbaglio apre Vim e non riesce a capire come
chiuderlo: perché mai dovrei usare un editor di testo così strampalato?

### 1. Aggiungere valori numerici espliciti a una classe enum

Dovevo esplicitare i valore di una enum C# chiamata `TranslationCodeId` come parte di un task. Era
necessario perché lasciarli impliciti avrebbe potuto permettere (nel nostro caso, ha permesso)
l'aggiunta di nuovi valori nel mezzo della definizione, causando uno shift in tutti i campi
successivi e quindi discrepanze nel caso in cui questi venissero anche salvati nella loro forma
numerica in altre parti dell'applicazione (nel nostro caso, un database).

In pratica dovevo trasformare questo:

```csharp {lineNos=inline tabWidth=4 style=github-dark anchorlinenos=true lineanchors=enum-pre}
public enum TranslationCodeId
{
   // buttons
   Button_Accept,
   Button_Cancel,

   // labels
   Label_Actions,
   Label_Column,

   // messages
   Message_Confirm,
   Message_GoBack,

   // ...continues...
}
```

in questo:

```csharp {lineNos=inline tabWidth=4 style=github-dark anchorlinenos=true lineanchors=enum-post}
public enum TranslationCodeId
{
    // buttons
    Button_Accept = 0,
    Button_Cancel = 1,

    // labels
    Label_Actions = 2,
    Label_Column = 3,

    // messages
    Message_Confirm = 4,
    Message_GoBack = 5,

    // ...continues...
}
```

Si tratta di un _change_ allo stesso tempo concettualmente semplicissimo, ma tecnicamente infernale
non appena la enum non contiene solo sei campi come qui sopra ma, ad esempio, 800. Un lavoro manuale
di questo tipo diventa subito un compito lunghissimo e noiosissimo. Con Vim, puoi completarlo in
cinque passaggi nel giro di venti secondi circa:

1. Usa un [_visual block_](https://vimhelp.org/visual.txt.html#visual-block "'visual-block' su vimhelp.org")
   per inserire un {{< highlight csharp "hl_inline=true,style=github-dark" >}}0 {{< / highlight >}}
   prima di ogni campo enum:

   `<C-v>/}kI0 <Esc>`

   {{< details summary="Spiegazione" >}}
   - _prerequisiti_: posiziona il cursore sul primo carattere del [primo campo enum]({{< ref
     "#enum-pre-4" >}})
   - `<C-v>` apre la selezione _visual block_
   - `/}k` espande la selezione fino alla [graffa di chiusura]({{< ref "#enum-pre-16" >}}) e naviga
     una linea verso l'alto, in modo da posizionare il cursore sulla [riga dell'ultimo campo
     enum]({{< ref "#enum-pre-15" >}})
   - `I0 <Esc>` inserisce lo {{< highlight csharp "hl_inline=true,style=github-dark" >}}0 {{< /
     highlight >}} seguito da uno spazio prima di tutte le righe selezionate
   {{< /details >}}

2. Lo step precedente purtroppo aggiunge lo {{< highlight csharp "hl_inline=true,style=github-dark"
   >}}0 {{< / highlight >}} anche nelle righe contenenti commenti. Puoi rimuoverli facilmente col
   comando [_substitute_](https://vimhelp.org/change.txt.html#%3Asubstitute "Documentazione del comando su vimhelp.org"):

   `:%s/0 \/\//\/\/`

   {{< details summary="Spiegazione" >}}
   - `:%s/old/new` ad esempio sostituisce la parola `old` con `new` una volta per ogni riga nel tuo
     file corrente. Noi vogliamo sostituire {{< highlight csharp "hl_inline=true,style=github-dark"
     >}}0 //{{< / highlight >}} con {{< highlight csharp "hl_inline=true,style=github-dark"
     >}}//{{< / highlight >}}, ma dobbiamo anteporre un _back-slash_ a ogni _forward-slash_ in
     quanto il comando supporta la sintassi regex
   {{< /details >}}

3. A questo punto dovresti avere uno {{< highlight csharp "hl_inline=true,style=github-dark" >}}0
   {{< / highlight >}} appena prima di ogni campo enum. Puoi ora trasformare la colonna di zeri
   negli reali valori di ciascun campo semplicemente [incrementandoli in modo
   sequenziale](https://vimhelp.org/change.txt.html#CTRL-A "Documentazione del comando su vimhelp.org"):

   `vi}ojjg<C-a>`

   {{< details summary="Spiegazione" >}}
   - `vi}` seleziona tutto il testo all'interno delle parentesi graffe
   - `ojj` sposta il cursore dall'ultima riga alla prima riga della tua selezione corrente, e naviga
     due righe verso il basso in modo da escludere il primo campo enum dal _visual block_
   - `g<C-a>` incrementa in modo sequenziale il primo numero in ciascuna delle righe attualmente
     selezionate
   {{< /details >}}

4. Ora dobbiamo solo far compilare il codice: registra una
   [macro](https://vimhelp.org/repeat.txt.html#q "'q recording' su vimhelp.org") in cui aggiusti la
   sintassi per la prima riga problematica. Una possibile sequenza di comandi utile a questo scopo
   potrebbe essere:

   `qfdf $i = <Esc>px/,<Enter>^q`

   {{< details summary="Spiegazione" >}}
   - _prerequisiti_: posiziona il cursore di nuovo sul primo carattere del [primo campo enum]({{<
     ref "#enum-pre-4" >}})
   - `qf` fa partire la registrazione della nostra macro salvandola sul tasto `f`
   - `df` rimuove tutti i caratteri fino al primo spazio nella riga (incluso)
   - `$` posiziona il cursore sulla fine della riga
   - `i = <Esc>` inserisce `=` appena prima della virgola
   - `px` incolla i caratteri rimossi precedentemente con `df` nel posto giusto e rimuove lo spazio
     bianco, ormai inutile
   - `/,<Enter>^` naviga alla prossima virgola e posiziona il cursore all'inizio della riga, in modo
     da tornare al punto di partenza e rendere la macro facilmente ripetibile in sequenza
   - `q` completa la registrazione della macro
   {{< /details >}}

5. Esegui la macro tante volte quanto necessarie per aggiustare tutti i campi rimanenti. Ad esempio,
   se la tua enum contiene 800 campi, puoi semplicemente fare:

   `799@f`

   {{< details summary="Spiegazione" >}}
   - `799` dice a Vim di eseguire il comando successivo 799 volte. Perché 799? Perché hai 800 campi,
     ma ti sei già occupato del primo nello step 4.
   - `@f` esegue la macro salvata sul tasto `f`
   {{< /details >}}

La tua enum ora dovrebbe mostrare correttamente tutti i valori numerici in maniera esplicita [in
questo modo]({{< ref "#enum-post-1" >}}). Combinando diversi comandi abbastanza semplici presi
singolarmente (_visual blocks_, sostituzioni regex, incrementi numerici sequenziali e macro) hai
immediatamente completato quello che sarebbe altrimenti stato un pomeriggio di tedio.
