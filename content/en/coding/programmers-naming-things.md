---
author: Nicolo Traini
title: Programmers naming things
summary: and not being very good at it, to be honest
slug: programmers-naming-things
# draft: true
date: 2024-06-06
---

> There are only two hard things in Computer Science: cache invalidation and naming things.

If you're a programmer, you've probably heard this joke before. If you're not a programmer, you're now probably wondering how on Earth could naming things be any harder than this scary-sounding _[cache invalidation](https://www.reddit.com/media?url=https%3A%2F%2Fi.redd.it%2Fmalf7gt4qdj21.jpg "comic strip on Reddit")_ business. It turns out — it is harder. Or at least it looks like it is, judging by the sheer amount of bad names I have encountered so far in the coding world. I've been writing code for a little more than three years now so I'm hardly an expert, yet my findings are more than enough to fill this article and still have enough leftovers for maybe two or three more articles as well.

In order for the non-programmer to understand how this could even be possible in the first place, though, I think it's necessary to give credit where credit is due. Programmers routinely write software. Software is made of code, code is made of tons of different semantic parts, and most parts can be named ([almost](https://github.com/AnanthaRajuC/Reserved-Key-Words-list-of-various-programming-languages "'Reserved Keywords list of various programming languages' on GitHub")) whatever — it's [your choice](https://www.youtube.com/watch?v=ozYaB5WrD_0 "'It's your choice.flv' on YouTube"). But there's a catch: you should really strive for meaningful, consistent, coherent, self-explaining names. Programmers spend way more time reading code than writing it, and code is already hard enough to read as it is ­— you don't want to [make it any harder on yourself](https://www.youtube.com/watch?v=mSUNnCwj1WY "'programming war crimes' on YouTube") whenever possible. You probably know what `gC` is meant to be now that you've just created it, but I can assure you won't have the faintest idea three months from now, when people will have found a bug stemming from that very code that now looks like a slightly more intellegible version of [Wingdings](https://lingojam.com/WingdingsTranslator "Wingdings Translator"). Just calling it `getCustomers` or something similar could probably have been a useful _memento_ instead, sparing you some serious head-scratching and time-wasting debugging.

So far so good. Let's just use descriptive names then, shall we? Well, it's not that easy. First of all, there is no standard on how to choose a good name. There are [guidelines](https://xkcd.com/927/ "comic strip on xkcd.com"), and even those [contradict each other](https://blog.ploeh.dk/2015/08/17/when-x-y-and-z-are-great-variable-names/) if you take into consideration different programming paradigms or even just different languages. It's easy enough to learn what is considered good for a specific language, but the average, experienced programmer has to simultaneously be fluent in multiple languages, and guidelines easily become a huge blur pretty fast. The same name could be a perfect fit for my code, and an [abomination](https://x.com/jamesiry/status/598547781515485184 "functional programmers on Twitter") in yours. Also, let's say you find a perfect name for a key part of your logic. Congratulations, you just did what you had to do just for one of the hundred other variables or functions you'll be creating today. It's not enough just to be good once — you have to be consistent. It's not impossible; most programmers manage to do it every day, but it's not easy by any means.

After shedding some light on these very high stakes, no wonder programmers suck at naming things when they are not coding. They are literally burnt out. They don't want to have anything to do with it, unless someone is paying them to do it. They're the pop artists fostering an unknown harsh-noise side-project while they're not busy recording the next million-dollar album, they're the higher-grossing directors who can't wait to go home and watch their favourite Z-movie tape. A command-line app called [`thefuck`](https://github.com/nvbn/thefuck "'thefuck' on GitHub") is basically a glass of cool, refreshing water after an eight-hour walk through the digital, unforgiving desert.

To wrap it all up, I've compiled below a list of what I think are the worst names ever given by programmers. I'll include a short explaination for each entry in order to explain why, in my opinion, they are good examples of this kind of digital poetic justice tech people inflict on their own kind. Enjoy!

<!-- - C (successor to B)
- C++
- YAML (YAML Ain't Markup Language) -->
