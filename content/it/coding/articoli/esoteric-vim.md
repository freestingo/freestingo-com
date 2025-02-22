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

Un giorno a lavoro dovevo esplicitare i valore di una enum C# chiamata `TranslationCodeId`. Era
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
di questo tipo diventa subito un compito lunghissimo e noiosissimo. Con Vim, puoi completarlo in tre
passaggi:

1. Inserisci il primo {{< highlight csharp "hl_inline=true,style=github-dark" >}}0{{< / highlight >}}
   a mano come una sorta di template da adattare automaticamente a tutti gli altri campi:

   `gg/,<Enter>i = 0<Esc>`

   {{< details summary="Spiegazione" open=true >}}

   - `gg/,<Enter>` posiziona il cursore prima all'inizio del file, poi sulla virgola più vicina
     tramite la [ricerca per pattern](https://vimhelp.org/pattern.txt.html#%2F "'/' su vimhelp.org")
   - `i = 0<Esc>` inserisce il nostro valore esplicito
     {{< /details >}}

2. Inserisci un altro valore sul prossimo campo enum, ma questa volta registra tutte le tue azioni
   in una [macro](https://vimhelp.org/repeat.txt.html#q "'q recording' su vimhelp.org") in modo da
   poterli poi ri-eseguire automaticamente in futuro. Un modo semplice per farlo potrebbe essere
   copiare il valore dal campo precedente, incollarlo alla destra del campo corrente e incrementarlo
   di uno:

   `nnqm<C-o>y2F <C-i>P<C-a>nnq`

   {{< details summary="Spiegazione" open=true >}}

   - `nn` posiziona il cursore sulla virgola appena dopo il campo enum che stai per modificare,
     perché stai dicendo a Vim di passare al prossimo risultato di ricerca due volte, e l'ultima
     cosa cercata è il carattere `,`
   - `qm` fa partire la registrazione della macro, salvandola sul tasto `m`. La nostra intenzione è
     eseguire i comandi necessari sia per modificare il campo corrente, sia per piazzare il cursore
     sul punto giusto alla fine della sequenza. Questo ultimo punto è di fondamentale importanza: ci
     permetterà di iterare l'esecuzione della nostra macro a nostro piacimento, senza bisogno di
     alcun intervento manuale
   - `<C-o>y2F ` naviga alla [posizione precedente](https://vimhelp.org/motion.txt.html#CTRL-O "'jump list' su vimhelp.org")
     e copia il testo alla sinistra del cursore fino al secondo spazio
   - `<C-i>P` riposiziona il cursore alla sua posizione originaria prima del salto e incolla il
     testo sulla sinistra del cursore
   - `<C-a>` [incrementa](https://vimhelp.org/change.txt.html#CTRL-A "'C-a' su vimhelp.org") il
     numero su cui risiede attualmente il tuo cursore
   - `nnq` posiziona il cursore sulla virgola successiva, e chiude la registrazione macro
     {{< /details >}}

3. Fai fare il lavoro sporco a Vim. Ad esempio, se la tua enum contiene 800 campi puoi fare:

   `798@m`

   {{< details summary="Spiegazione" open=true >}}

   - [prefiggere un qualsiasi numero prima di un comando](https://vimhelp.org/intro.txt.html#count "'count' su vimhelp.org") farà eseguire il comando non una volta sola, ma esattamente tante
     volte quante indicate dal numero stesso; in questo caso, 798 volte. Come mai 798? Perché ci
     sono 800 campi in tutto, ma ti sei già occupato del primo nello step 1 e del secondo nello step
     2
   - `@m` esegue la macro precedentemente salvata sul tasto `m`
     {{< /details >}}

La tua enum ora dovrebbe mostrare correttamente tutti i valori numerici in maniera esplicita [in
questo modo]({{< ref "#enum-post-1" >}}). Combinando diversi comandi abbastanza semplici presi
singolarmente (ricerca per pattern, navigazione della _jump list_, incrementi numerici sequenziali)
puoi esprimere comportamenti molto complessi e portare a termine in venti secondi quello che sarebbe
altrimenti stato un pomeriggio di tedio.
