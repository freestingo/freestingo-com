---
author: Nicolo Traini
title: Programmers naming things
summary: and not being very good at it, to be honest
slug: programmers-naming-things
description: A look into the reasons behind the worst names ever given to something by programmers
keywords: [worst of, programming, cache invalidation, javascript, vim, php]
date: 2024-06-06
topics: [worst of, debugging, PHP, javascript, vim]
---

> There are only two hard things in Computer Science: cache invalidation and naming things.

If you're a programmer, you've probably heard this joke before. If you're not a programmer, you're now
 wondering how on Earth could naming things be any harder than this scary-sounding
 _[cache invalidation](https://www.reddit.com/media?url=https%3A%2F%2Fi.redd.it%2Fmalf7gt4qdj21.jpg "comic strip on Reddit")_
 business. It turns out — it is harder. Or at least it looks like it is, judging by the sheer amount
 of horrible names I have encountered so far in the coding world. I've been writing code for a little
 more than three years now so I'm hardly an expert, yet my findings are more than enough to make my
 point in this article and still have enough leftovers for maybe two or three more articles as well.

In order for the non-programmer to understand how this could even be possible in the first place,
though, I think it's necessary to give credit where credit is due. Programmers routinely write software.
Software is made of code, code is made of tons of different parts, and most of these parts can be named
([almost](https://github.com/AnanthaRajuC/Reserved-Key-Words-list-of-various-programming-languages "'Reserved Keywords list of various programming languages' on GitHub"))
whatever — it's [your choice](https://www.youtube.com/watch?v=ozYaB5WrD_0 "'It's your choice.flv' on YouTube").
But there's a catch: you should really strive for meaningful, consistent, coherent, self-explaining names.
Programmers spend way more time reading code than writing it, and code is already hard enough to read as it is ­—
you don't want to [make it any harder on yourself](https://www.youtube.com/watch?v=mSUNnCwj1WY "'programming war crimes' on YouTube")
whenever possible. You probably know what that `gC` is meant to be now that you've just created it, but I
can assure you won't have the faintest idea three months from now, when people will have found a bug stemming
from that very code that now looks like a slightly more intellegible version of
[Wingdings](https://lingojam.com/WingdingsTranslator "Wingdings Translator").
Just calling it `getCustomers` or something similar could probably have been a useful _memento_ instead,
sparing you some serious head-scratching and time-wasting debugging.

So far so good. Let's just use descriptive names then, shall we? Well, it's not that easy.
First of all, there is [no common standard](https://xkcd.com/927/ "comic strip on xkcd.com")
clearly dictating how to choose names. There are just guidelines, but even those
[contradict each other](https://blog.ploeh.dk/2015/08/17/when-x-y-and-z-are-great-variable-names/)
if you take into consideration different programming paradigms or even just different languages.
It's easy enough to learn what is considered good for a specific language, but the average, experienced
programmer has to simultaneously be fluent in multiple languages; guidelines easily become a huge
blur pretty fast. The same name could be a perfect fit for my code, and an
[abomination](https://x.com/jamesiry/status/598547781515485184 "functional programmers on Twitter")
for yours. But let's just assume you managed to find a perfect name for a key part of your logic.
Congratulations, you just did what you had to do just for one of the hundred other variables or
functions you'll be creating today. It's not enough just to be good once — you have to be consistent.
It's not impossible; most programmers manage to do it every day, but it's not easy by any means.

After shedding some light on these very high stakes, no wonder programmers suck at naming things
when they are not coding. They are literally burnt out. They don't want to have anything to do with it,
unless someone is paying them to do it. They're the pop artists fostering an unknown harsh-noise
side-project while they're not busy recording the next million-dollar album, they're the
higher-grossing directors who can't wait to go home and watch their favourite Z-movie tape.
Naming your command-line app called
[`thefuck`](https://github.com/nvbn/thefuck "'thefuck' on GitHub")
is basically gulping a glass of cool, refreshing water after an eight-hour daily walk through
the digital, unforgiving desert. It's a neverending Dantesque poetic justice programmers
like to inflict on their own kind.

Let's go ahead and dive into this semantic hellscape then; Virgil (yours truly) has conveniently compiled
a list below, enumerating the worst names ever given by programmers, in alphabetical order.
For each entry you can find a short comment explaining why that name was worth including
and why they are so bad. Enjoy!

### CoC

**CoC** is a plugin for the [vim](https://www.vim.org/ "vim homepage") text editor, unlocking
auto-completion for multiple different languages. **CoC** looks like an acronym, and sure enough,
it is! It stands for **Conquer Of Completion**. I honestly can't decide what's worse: the actual
full name looking like an early-2000s, Call-of-Duty-ripoff flashgame title, or the acronym
sounding like, you know,
[that](https://www.youtube.com/watch?v=YA8l2POQ1No "'The Office - Cock' on YouTube").
This is why normal people think **vim** users are weird.

### GIMP

Another acronym — it stands for [GNU Image Manipulation Program](https://www.gimp.org/ "GIMP home page").
Yes, an entire team of software developers just came up with that, and found nothing wrong with it.
The `"gimp"`
[image search results](https://www.google.com/search?sca_esv=4ce04de13f7e18f6&sca_upv=1&q=gimp&uds=ADvngMhiT0nRpSjbJPjWq9wKOmhO5M4yafYUActcLRzkXct9ifp40-rxmQDurT4o_qJO4V3T5MshTn0O_bZSLo7HXdcOc6LAT2IqKsXjVfSPsxsu-N6WMLQuKar-rCQlGC49VlMvphVrtq7uop9ygsYs1Q0zr_y6dfe7iShjdtTCbepAd1FBUYXdZQ-YfhbK3MwRbv0mV2YNjg2-0eLJnSVX9gUHqHoGfSav-qGa6vOn9t-QnOr-9aW6yEvCJJyzXBKlpOJl7L9-iMAom-w7OW_CPb0QCOcSzw&udm=2&prmd=ivnmbtz&sa=X&ved=2ahUKEwjFpp7s08mGAxWNgP0HHZ9JMgIQtKgLegQIFBAB&biw=1488&bih=624&dpr=1.25 "'gimp' Google image search results")
have to be one of the funniest things I've ever seen.

### JavaScript

**JavaScript** is the _de-facto lingua franca_ of modern web. It runs in everyone's browser,
and it's the thing that makes websites load stuff dynamically. Now it's ubiquitous, but its
origins date back to the times when **Java** was one of the most talked about programming
languages. Judging by the name, you'd think **JavaScript** was some kind of technology that
built on top of **Java**. Wrong. The two languages virtually have nothing in common. The only
reason **JavaScript** contains **Java** in its name is because **Java** sounded cool at the
time. Pure marketing, clout-chasing, if you will. It's the same reason behind the fact that
now, in 2024, even the most basic and bare-bones calendar app is being described as
["AI-Powered"](https://www.scaruffi.com/singular/sin00.html "Intelligence is not Artificial, introduction")
somewhere in the company website. The later attempt of renaming the language into **ECMAScript**,
anyway, [did not fare any better](https://james-iry.blogspot.com/2009/05/brief-incomplete-and-mostly-wrong.html#:~:text=1995%20%2D%20Brendan%20Eich,is%20renamed%20ECMAScript. "A brief, incomplete, and mostly wrong history of programming languages").

### less

This is a command-line program for viewing text files. Why the name **less**? It's because it's
meant to be [an expansion and a replacement](https://man7.org/linux/man-pages/man1/less.1.html "'less' Linux manual page")
for **more**, the old pager with limited features.  Hence, the name — **less** is **more**. Get it? Unfortunately, we all do.

### scrot

Another command-line app that lets you take **SCR**eensh**OT**s.
[I am not kidding](https://man.archlinux.org/man/scrot.1 "'scrot' manual page").
If there's anything reinforcing the age-old stereotype of programmers being cave-dwellers,
completely detached from reality — this has to be it.

### T_PAAMAYIM_NEKUDOTAYIM

_Come again?_ Don't worry, your furniture won't start floating. It's just an error code you can get while programming in
[PHP](https://phpsadness.com/sad/1 "Unexpected T_PAAMAYIM_NEKUDOTAYIM").
This is what the
[official documentation](https://www.php.net/manual/en/language.oop5.paamayim-nekudotayim.php "Scope Resolution Operator (::)")
has to say about it:

> The Scope Resolution Operator (also called _**Paamayim Nekudotayim**_) or in simpler terms,
> the double colon, is a token that allows access to a constant, static property, or static method
> of a class or one of its parents.

Ok, so it's basically a double colon. Cool, I guess. But why is it "_also called **Paamayim Nekudotayim**_"?

> _**Paamayim Nekudotayim**_ would, at first, seem like a strange choice for naming a double-colon.
> However, while writing the Zend Engine 0.5 (which powers PHP 3), that's what the Zend team
> decided to call it. It actually does mean double-colon - in Hebrew!

Oh, so that explains it. Except it does not explain anything at all. Why not just use a boring, English
**T_DOUBLE_COLON** like all other error codes do? Why am I forced to decipher colloquial Hebrew when trying
to debug some code?
[Phil Sturgeon actually asked](https://philsturgeon.com/wtf-is-t-paamayim-nekudotayim/ "WTF is T_PAAMAYIM_NEKUDOTAYIM")
on IRC, and got this answer:

> philsturgeon, the token name was kept around because conservative people felt that removing
> it would be too much of a change, and might confuse users.

Wait, are these the same "conservative people" that are now occupying the West Bank? Have they started colonizing
code bases too? Should the open source community be worried? Does the USA know about this? In 2010, some guy
aptly named Chad launched a terrorist attack aimed at the **PHP Internals** headquarters, asking if the
exotically named token could please be translated to English (you can find the whole, delirious discussion
[here](https://web.archive.org/web/20221209141424/https://grokbase.com/t/php/php-internals/10ayegjgg4/rename-t-paamayim-nekudotayim-to-t-double-colon/10ay7h1f2a "[PHP-INTERNALS] rename T_PAAMAYIM_NEKUDOTAYIM to T_DOUBLE_COLON")).
After more than ten years, nothing has changed.

### YAML

To be fair **YAML** is not that bad, but I'm still bashing it as a scape-goat for all the "clever"
[recursive acronyms](https://www.techopedia.com/definition/21636/recursive-acronym "Recursive Acronym definition on Techopedia")
floating around in tech. The recursion novelty lasts for about ten or fifteen seconds – from then on it
just becomes straight up annoying. Specifically, **YAML** doubles down on the "humor": it means
**YAML Ain't Markup Language**, even though
[it actually is a markup language](https://www.redhat.com/en/topics/automation/what-is-yaml "'What is YAML?' on Red Hat").
I know, hilarious.
