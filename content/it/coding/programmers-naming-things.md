---
author: Nicolo Traini
title: Programmatori che nominano cose
summary: e nemmeno troppo bene, a dir la verità
slug: programmatori-che-nominano-cose
translationKey: programmers-naming-things
description: Un compendio dei peggiori nomi mai dati da programmatori
keywords: [worst of, programming, cache invalidation, javascript, vim, php]
date: 2024-06-06
topics: [worst of, debugging, PHP, javascript, vim]
---

> There are only two hard things in Computer Science: cache invalidation and naming things.

Se sei un programmatore, molto probabilmente conosci già questa battuta. Se non sei un programmatore,
adesso ti starai chiedendo come cavolo possa essere difficile dare nomi a cose, specie se paragonato
a questa fantomatica
_[cache invalidation](https://www.reddit.com/media?url=https%3A%2F%2Fi.redd.it%2Fmalf7gt4qdj21.jpg "fumetto su Reddit")_.
In realtà, è molto difficile. O perlomeno così pare, stando alla quantità immane di nomi orribili
pullulanti nel sottobosco tech incontrati da me finora. Scrivo codice da poco più di tre anni,
non mi considero assolutamente un esperto; tuttavia, ho già trovato esempi in abbondanza per questo
articolo, e ne avanzerebbero comunque abbastanza per altri due o tre articoli senza troppi problemi.

Per spiegare al non-programmatore come sia possibile tutto ciò, comunque, bisogna dare a Cesare quel
che è di Cesare. I programmatori in genere scrivono software. I software sono composti da codice,
il codice è composto da moltissime parti diverse e molte di queste parti possono essere nominate
([quasi sempre](https://github.com/AnanthaRajuC/Reserved-Key-Words-list-of-various-programming-languages "'Reserved Keywords list of various programming languages' su GitHub"))
a piacimento: [fai come ti pare](https://www.youtube.com/watch?v=ozYaB5WrD_0 "'It's your choice.flv' su YouTube").
Ma attenzione! sarebbe meglio scegliere nomi significativi, coerenti, logici e auto-esplicativi.
Dopotutto si passa molto più tempo a leggere codice che a scriverlo, e il codice in generale
è già abbastanza difficile da leggere così com'è — perchè mai dovremmo
[complicarci la vita](https://www.youtube.com/watch?v=mSUNnCwj1WY "'programming war crimes' su YouTube"),
se possiamo evitarlo? Oggi questo `gC` per te non ha segreti perchè l'hai appena creato, ma ti
assicuro che non avrai la più pallida idea di cosa significhi tra tre mesi, quando avranno
trovato un bug relativo proprio a quella parte di codice ora straordinariamente più simile
a caratteri randomici in [Wingdings](https://lingojam.com/WingdingsTranslator "Wingdings Translator")
che a un qualcosa scritto da un essere umano. Se l'avessi chiamato `getCustomers`
fin dall'inizio ti saresti risparmiato una logorante sessione di debugging e, soprattutto,
non avresti sprecato tempo prezioso.

Finora tutto chiaro. Allora basta usare sempre nomi descrittivi! Purtroppo la realtà non è così semplice.
Innanzitutto, [non esiste uno standard](https://xkcd.com/927/ "comic strip on xkcd.com")
chiaro e condiviso riguardo la scelta di un buon nome. Ci sono alcune linee guida, ma anche loro
[si contraddicono tra loro](https://blog.ploeh.dk/2015/08/17/when-x-y-and-z-are-great-variable-names/)
non appena fai riferimento a paradigmi diversi, o anche solo a linguaggi diversi. È relativamente
semplice studiare le convenzioni di un linguaggio, ma in media il programmatore esperto sa usare tre,
quattro linguaggi diversi: in un attimo le linee guida si accavallano tra loro, creando una sorta
di mappazzone sfocato e inintellegibile. Lo stesso nome potrebbe essere ottimo per il mio codice,
e un [abominio](https://x.com/jamesiry/status/598547781515485184 "functional programmers on Twitter")
per il tuo. Come? Nonostante tutto sei riuscito a trovare il nome perfetto per una parte cruciale
della tua logica? Congratulazioni, hai semplicemente fatto quello che dovevi fare per una sola
delle centinaia di altri variabili e funzioni che creerai nel resto della giornata. Non basta
essere bravi una volta: bisogna essere bravi sempre. Non è impossibile; la maggior parte dei
programmatori ci riesce ogni giorno, ma non è facile.

Dopo aver visto un po' più da vicino la natura di questi patemi giornalieri, diventa quindi ovvio il
motivo per cui i programmatori fanno così schifo a dare nomi alle cose quando non stanno scrivendo
codice. Sono praticamente in burnout. Non vogliono saperne niente, a meno che non vengano pagati
per farlo. Sono i cantanti pop che pubblicano a nome del loro side-project harsh-noise quando
non stanno incidendo il prossimo disco da classifica, sono i registi che non vedono l'ora di
tornare a casa e spararsi il loro Z-movie preferito in videocassetta. Chiamare
[`thefuck`](https://github.com/nvbn/thefuck "'thefuck' su GitHub")
la tua app da linea di comando è praticamente un provvidenziale bicchiere di acqua fresca
dopo la traversata giornaliera di otto ore del deserto digitale. È un perpetuo
contrappasso dantesco, inflitto dai programmatori alla loro stessa gente.

Entriamo quindi senza ulteriori indugi in questo inferno semantico: il vostro Virgilio
ha stilato qui sotto una piccola collezione in ordine alfabetico dei nomi peggiori
mai dati da dei programmatori. Per ciascun elemento potrete trovare un breve commento
sul perché l'ho incluso, o sul perché il nome è così terribile. Buon divertimento!

### CoC

**CoC** è un plugin di autocompletamento testuale per [vim](https://www.vim.org/ "vim home-page"),
un editor di testo da linea di comando. **CoC** sembra un acronimo, e infatti lo è!
Significa **Conquer Of Completion**. Non saprei cos'è peggio: il nome completo che
sembra il titolo di un gioco flash alla Call of Duty dei primi anni 2000, o l'acronimo
stesso che pare proprio [quella parola lì](https://www.youtube.com/watch?v=YA8l2POQ1No "'The Office - Cock' su YouTube").
Questo è uno dei motivi per cui la gente normale pensa che gli utenti di **vim** siano strani.

### GIMP

Un altro acronimo: significa [GNU Image Manipulation Program](https://www.gimp.org/ "GIMP home-page").
Sì, un team intero di sviluppatori ha pensato a questo acronimo e nessuno ha obiettato.
Se non capite perché dovrebbe essere un nome così strano, provate a inserire `"gimp"` nella barra di ricerca per immagini di Google e
[ammirate i risultati](https://www.google.com/search?sca_esv=4ce04de13f7e18f6&sca_upv=1&q=gimp&uds=ADvngMhiT0nRpSjbJPjWq9wKOmhO5M4yafYUActcLRzkXct9ifp40-rxmQDurT4o_qJO4V3T5MshTn0O_bZSLo7HXdcOc6LAT2IqKsXjVfSPsxsu-N6WMLQuKar-rCQlGC49VlMvphVrtq7uop9ygsYs1Q0zr_y6dfe7iShjdtTCbepAd1FBUYXdZQ-YfhbK3MwRbv0mV2YNjg2-0eLJnSVX9gUHqHoGfSav-qGa6vOn9t-QnOr-9aW6yEvCJJyzXBKlpOJl7L9-iMAom-w7OW_CPb0QCOcSzw&udm=2&prmd=ivnmbtz&sa=X&ved=2ahUKEwjFpp7s08mGAxWNgP0HHZ9JMgIQtKgLegQIFBAB&biw=1488&bih=624&dpr=1.25 "Immagini risultanti per 'gimp'").

### JavaScript

**JavaScript** è la vera lingua franca del web contemporaneo. Gira in tutti i browser ed è
ciò che consente ai siti web di caricare dati in maniera dinamica. Ora è davvero dappertutto,
ma le sue origini sono umili: all'epoca, **Java** era il linguaggio più chiacchierato.
A giudicare dal nome, **JavaScript** sarebbe una sorta di spin-off di **Java**. Sbagliato.
I due linguaggi non hanno praticamente nulla in comune. L'unico motivo per cui **JavaScript**
contiene **Java** nel suo nome è perché **Java** a quei tempi suonava figo. Una pura operazione
di marketing, clout-chasing potremmo dire. In fondo è lo stesso motivo per cui oggi, nel 2024,
anche l'app più semplice e basilare viene descritta come
["AI-Powered"](https://www.scaruffi.com/singular/sin00.html "Intelligence is not Artificial, introduzione al libro")
da qualche parte nel sito aziendale. Il ribattezzamento successivo in **ECMAScript**, comunque,
[non migliorò per niente la situazione](https://james-iry.blogspot.com/2009/05/brief-incomplete-and-mostly-wrong.html#:~:text=1995%20%2D%20Brendan%20Eich,is%20renamed%20ECMAScript. "A brief, incomplete, and mostly wrong history of programming languages").

### less

**less** è un programma eseguibile da linea di comando per visualizzare file di testo.
Perché il nome **less**? Perché il programma
[è stato pensato come sostituto](https://man7.org/linux/man-pages/man1/less.1.html "manuale Linux per 'less'")
di **more**, il vecchio paginatore con meno funzionalità. Da qui, il nome — _**less** is **more**_. Capìta?

### scrot

Un'altra app da linea di comando per fare gli **SCR**eensh**OT**.
[Non sto scherzando](https://man.archlinux.org/man/scrot.1 "Manuale di 'scrot'").
Forse uno dei motivi per cui esiste ancora lo stereotipo del programmatore barricato in casa,
completamente distaccato dal mondo esterno.

### T_PAAMAYIM_NEKUDOTAYIM

_Eh?_ Non preoccuparti, [i mobili della tua cucina sono al sicuro](https://www.youtube.com/watch?v=r_qjf_iiCMk).
È solo un _error code_ abbastanza frequente quando si programma in
[PHP](https://phpsadness.com/sad/1 "Unexpected T_PAAMAYIM_NEKUDOTAYIM").
La [documentazione ufficiale](https://www.php.net/manual/en/language.oop5.paamayim-nekudotayim.php "Scope Resolution Operator (::)")
ci dice:

> The Scope Resolution Operator (also called _**Paamayim Nekudotayim**_) or in simpler terms,
> the double colon, is a token that allows access to a constant, static property,
> or static method of a class or one of its parents.

Ok, quindi sarebbero praticamente i due punti doppi. Bene. Ma perché dovrebbe "_anche chiamarsi **Paamayim Nekudotayim**_"?

> _**Paamayim Nekudotayim**_ would, at first, seem like a strange choice for naming a double-colon.
> However, while writing the Zend Engine 0.5 (which powers PHP 3), that's what the Zend team
> decided to call it. It actually does mean double-colon - in Hebrew!

Ah, capito. O meglio, non ho capito niente. Perché non usare un semplice **T_DOUBLE_COLON**
in inglese, come tutti gli altri _error codes_? Perché PHP mi costringe a decifrare
lo slang ebraico quando sto solo cercando di debuggare il mio codice?
[Phil Sturgeon si è fatto la stessa domanda](https://philsturgeon.com/wtf-is-t-paamayim-nekudotayim/ "WTF is T_PAAMAYIM_NEKUDOTAYIM")
nella IRC, e gli hanno risposto così:

> philsturgeon, the token name was kept around because conservative people felt
> that removing it would be too much of a change, and might confuse users.

Aspetta, per caso stiamo parlando degli stessi _conservative people_ che hanno
pure colonie nella West Bank? Hanno iniziato a colonizzare anche i progetti
open source ora? Dobbiamo allarmarci? Gli Stati Uniti in tutto questo cosa dicono?
Nel 2010 un tale Chad, di nome e di fatto, orchestrò un attacco terroristico a
danni dei **PHP Internals** chiedendo se fosse possibile tradurre in inglese il
token (trovate l'archivio dell'intera, delirante discussione
[qui](https://web.archive.org/web/20221209141424/https://grokbase.com/t/php/php-internals/10ayegjgg4/rename-t-paamayim-nekudotayim-to-t-double-colon/10ay7h1f2a "[PHP-INTERNALS] rename T_PAAMAYIM_NEKUDOTAYIM to T_DOUBLE_COLON")).
Dopo più di dieci anni, non è cambiato nulla.

### YAML

In realtà **YAML** non è poi così tremendo, ma comunque lo includo a mo' di capro
espiatorio per tutti gli [acronimi ricorsivi](https://www.techopedia.com/definition/21636/recursive-acronym "Recursive Acronym definition su Techopedia")
in giro per il mondo tech. La ricorsione è buffa per circa dieci o quindici secondi;
da lì in poi diventa solo fastidiosa. Nel nostro caso, **YAML** è doppiamente "buffo":
sta per **YAML Ain't Markup Language**, anche se in realtà
[è proprio un _markup language_](https://www.redhat.com/en/topics/automation/what-is-yaml "'What is YAML?' su Red Hat").
Lo so, molto divertente.
