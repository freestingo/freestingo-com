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
di questo tipo diventa subito un compito lunghissimo e noiosissimo. Con Vim, puoi completarlo in due
passaggi:

1. Assegna `0` a ciascun campo:

   `:g/,$/v/\/\//norm $i = 0`

   {{< details summary="Spiegazione" open=true >}}

   - `:g` esegue comandi sulle linee contenenti un determinato pattern, mentre `:v` esegue comandi
     sulle linee NON contenenti un determinato pattern. Si può quindi innestare un `:v` dentro un
     `:g` per [operare solo su linee contenenti `foo`, ma non `bar`](https://vimhelp.org/repeat.txt.html#multi-repeat "'multi-repeat' su vimhelp.org").
     Possiamo sfruttare questa feature per isolare i campi enum e ignorare eventuali commenti
     prima matchando le linee che finiscono con una virgola (`,$`), poi escludendo le linee che
     contengono un doppio slash (`\/\/`)
   - `norm $i = 0` è un comando [`normal`](https://vimhelp.org/various.txt.html#%3Anormal "':normal' su vimhelp.org")
     con cui navighiamo alla fine della linea corrente e inseriamo `= 0` appena prima del cursore.
     {{< /details >}}

2. Incrementa tutti i valori numerici in maniera sequenziale:

   `vi}/0,$<Enter>ng<C-a>`

   {{< details summary="Spiegazione" open=true >}}

   - `vi}` seleziona tutto il testo all'interno delle parentesi graffe
   - `/0,$<Enter>` [naviga alla prima istanza](https://vimhelp.org/pattern.txt.html#%2F "'/' su vimhelp.org")
     di uno zero seguito da una virgola posta a fine linea
   - `n` naviga al prossimo risultato di ricerca. A questo punto dovresti aver selezionato tutti gli
     zeri tranne il primo
   - `g<C-a>` [incrementa sequenzialmente](https://vimhelp.org/change.txt.html#CTRL-A "'CTRL-A' su vimhelp.org")
     tutti i numeri attualmente selezionati
     {{< /details >}}

La tua enum ora dovrebbe mostrare correttamente tutti i valori numerici in maniera esplicita [in
questo modo]({{< ref "#enum-post-1" >}}).
