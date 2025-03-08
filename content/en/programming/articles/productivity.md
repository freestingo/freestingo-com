---
author: Nicolò Traini
title: The simplest and most overlooked productivity boost
summary: reflections on the (still mostly untapped) potential of touch typing
slug: the-simplest-and-most-overlooked-productivity-boost
translationKey: the-simplest-and-most-overlooked-productivity-boost
description: Reflections on the (still mostly untapped) potential of touch typing.
keywords:
  [programming, productivity, WPM, typing, bottleneck]
date: 2025-03-07
topics: [productivity]
---

Most people, when prompted into sharing pieces of productivity advice, will mention techniques that
are both very vaguely defined and incredibly hard to master. Refining task prioritization, time
management and interpersonal communication skills, for example, usually require hands-on experience
and/or excellent mentoring; both very long and strenous paths. There is inherently nothing wrong
with working on improving those abilities, but it is completely misleading to suggest focusing on
those before having completely mastered the basics—that is, the dumb, mechanical, low-cognitive,
peripheral aspects of your work. In my opinion, you should focus on these boring activities first
instead, and only then transition to the more complex, high-level core skills. 

The first obvious reason is low-cognitive skills, by definition, can be isolated and trained upon
quite easily. Counter-intuitively, though, very few people spend their time training them. In most
of the companies I have come across they are always considered as a "given", or at best something
you should strive to be "good enough" at. Moreover, some cultures tend to associate negative aspects
to this kind of optimizations. Getting to know all of your keyboard shortcuts could be frowned upon
by colleagues convinced that life is too precious to be wasted in front of a `man` page. The good
news is you can take advantage of these cultural connotations by consciously working on exactly
those kind of optimizations and enjoy the side-effects of the whole process as well. Besides just
simply getting better at using your keyboard, for example, you will inevitably become a more
well-rounded employee. Peripheral skills are shared by multiple disciplines: touch typing, for
example, will make you not only a better programmer but also a better accountant, writer, content
editor, marketer, manager, and so on. Furthermore, you will more easily stand out from the crowd,
just for the simple reason that, as I said before, very few people actively practice the most
tedious part of their jobs. It is trivial to win the race, when you are the only runner on the
field.

In my experience, mastering touch typing is the single best thing you can do for increasing your
productivity at work. The advantages it brings are huge, and it is dead easy to train. It is so
easy, in fact, that some people are able to do it without having done a single touch typing drill in
their lives—they just have been typing for a very long time. Should you wait several years to become
a "natural" typist, or should you train for some months and not have to think about it anymore for
the rest of your life? This is a question unexperienced people understandably ask themselves, and
again, the most common response can be totally misleading. A popular adage says working on your
typing is just a waste of time because "if you're spending more time typing than thinking about what
you're typing, then you're not thinking enough". A similar outlook will suggest that typing fast is
"completely not important. programming is 95% thinking and 5% doing". I am convinced this kind of
response is very common because it sounds really smart, plausible and just the right amount of
harsh, even though it is not true at all. 

I used to agree with these statements as well throughout the whole six-month training period in
which I learnt how to type at around 110 {{< abbreviation term="WPM" explanation="Words Per Minute"
>}} (starting from a baseline of around 60 WPM). I did not do it because I wanted to be more
productive, I just enjoyed being able to type fast. During the following years, I slowly started to
realize how being able to type fast has directly helped (and continues to help) me in being a much
more productive programmer, even in many ways I initially did not even consider. I could sketch out
different ideas in code and find the right solution for a given problem much more quickly by just
trying out different approaches, in the same amount of time it used to take me to only write down
one of them; I could take longer and much more detailed notes during important calls and meetings,
or I could document complex tasks or workflows much more comprehensively in memos which would then
help me recollect their original context more precisely and with less confusion at any time in the
future; I could transfer my thoughts into my laptop much more swiftly and effortlessly, so I could
completely focus on a given task without having to think about unrelated, distracting things (such
as the position of the letter `B` on my keyboard); I could communicate much more clearly to my
teammates and more often achieve what we were aiming for because I could easily type long, clear,
in-depth messages and reduce overall ambiguity... ironically, the overlap these benefits have with
the various areas of expertise mentioned at the start of the article is significant. Such a
simultaneous improvement for such a small price—some months of mindless typing practice—is
definitely an enticing proposal.

As a reference, I am sampling below some of the best typing tips and techniques I know and use
pretty much every day, grouping them by {{< abbreviation term="ROI" explanation="Return On Investment" >}} 
time-frames. Short-term improvements represent minimal changes to your current
workflow, bearing instant but small productivity boosts. Medium-term improvements are instead
important changes to your current workflow and setup, bearing equally remarkable productivity
boosts noticeable after some hours/days of routine adjustments. Long-term improvements constitute
very big changes to your current workflow and setup, bearing huge productivity boosts usually
noticeable after several weeks or months of practice. My personal recommendation is to try out all
of them as early as possible in your programming career in order to minimize the inherent friction
of disrupting well-established routines and breaking existing setups, but they can just as easily
apply to senior engineers as well—in the end, it all depends on how much you actually care about
typing.

#### Short-term improvements

If you are born after 1980 and have been using a computer for a while, at some point you inevitably
start asking yourself questions about weird and inconvenient keyboard layout choices that can only
be answered with "It made sense when keyboards were part of typewriters". That may be true, but it
does not change the fact that keyboards are now part of computers and a computer is not a
typewriter. Why is the `CTRL` key so far away from the home row, despite its use being so frequent?
Why is the `CAPS LOCK` key in the home row, right next to the `A` key, despite its use being so
rare? It would make sense to just swap the position of those two keys—and that is exactly what some
people do. It is such a simple and reasonable software tweak that some operating systems (such as
Ubuntu and macOS) even allow you to swap `CTRL` and `CAPS LOCK` from their default keyboard settings
page, without installing any third-party script or tool.

In addition, if you are not from an English-speaking country, your default keyboard layout will most
likely be different than the English one. Italian keyboard layouts, for example, prioritize easy
access to very common Italian characters such as accented vowels, at the expense of less common or
niche punctuation symbols such as `@`, `~` or square/curly brackets. This is good news for all
Italians except Italian programmers, which most likely will never use something like `ò` in their
source files. The easiest fix I found is to just use the English keyboard layout, and rely on your
`COMPOSE` key for the rare time you actually need to write a non-English character. Using three
separate keystrokes (`` COMPOSE + o + ` ``) instead of one for an `ò` once or twice a day is way
faster than using two modifier keys (`ALT GR + SHIFT + [`) instead of one every time you want to
open or close a curly bracket.

Another quick and easy keyboard tweak is to just shorten the key repeat delay time and increase the
key repeat rate. These two settings control how long you need to press down a single key before the
operating system starts registering it as multiple repeated keystrokes, and how many times a key
should be repeated in one second. In my experience, I found most people can manage way shorter delay
times and way higher repeat rates than what some operating systems (i.e. Windows) will actually let
you set in their settings pages. Check out and experiment with these two settings in your computer;
if you configure it right, this small change will instantly translate into a faster typing
experience whenever you find yourself holding down single keys for whatever reason. Some could argue
that this tweak is a config smell because you should never rely too much on holding down single keys
to do stuff—you should just know the correct keyboard shortcut instead. While I agree with this
sentiment, I still think that tweaking your key repeat settings is always worth doing. First of all,
nothing is stopping you to investigate and learn the proper keyboard shortcuts even after you did
the tweak. Second, there are some tasks for which there are no other mouse-free solutions other than
holding down a single key, or the intended correct keyboard shortcut actually takes longer to
execute. You can type intricate commands like "delete the previous thirteen words from the current
caret position" inside text editors such as [Vim]({{< ref "programming/articles/esoteric-vim/" >}}),
but that implies you have spent some time counting the exact number of words that need to be deleted
and inputting the correct key sequence to execute said command. In my experience, after applying the
key repeat tweak, holding down `CTRL` + `BACKSPACE` until I delete thirteen words is way faster than
making sure I need to delete exactly thirteen words and then typing `d13b` in Vim's normal mode.

#### Medium-term improvements

Touch typing is the "one weird trick" for reaching very fast typing speeds. Touch typing essentially
means typing accurately on your keyboard without ever looking at it. The idea is to optimize the
typing process by evenly distributing key presses among all of your fingers except for your thumbs,
one of which has exclusive access to the spacebar. A touch typist, for example, does not need to see
where the `P` key is before pressing it because they already know by heart that it is right above
their right pinky finger, so they just press it with their pinky. Memorizing the position of all the
keys on your keyboard sounds hard, but in reality it is not that complicated; it is just a little
awkward when you first practice it. The good news is that nowadays there are tons of websites
dedicated to teaching touch typing offering excellent typing drills and mnemonic exercises, making
it very easy for you to process and master your own keyboard in whatever way you see fit. I found
[this](https://www.keybr.com/ "Keybr touch typing training website") website to be particularly
helpful, for example, because it forces you to work on your weaknesses and avoid indulging in easy
exercises, making your practice sessions both more fruitful and efficient.

Somewhat counter-intuitively, touch typing is a sufficient but not necessary condition of being able
to type fast. Some people are able to reach very high WPM counts while still looking at their own
keyboard and not distributing all keystrokes between all fingers in an even fashion. It is harder,
but still doable. If for any particular reason you do not want to bother learning touch typing, you
can still [work on your sheer typing speed](https://monkeytype.com/ "Monkeytype") and even
[challenge your friends](https://play.typeracer.com/ "TypeRacer - Play typing games and race
friends") while you do it. In my opinion you should strive for reaching a typing speed of at least
100 WPM. How reasonable of a goal is it? It depends. Some days ago my girlfriend agreed to
undertaking her first ever typing speed test. She is an example of someone I would consider having
good enough familiarity with electronic devices without ever actively practicing typing on them; not
really a geek, but not really a novice either. On her first run, she scored 60 WPM. She tried again,
and scored 76 WPM on her second run. Keep in mind she is not a touch typist—she types with the
index, middle and ring fingers on her left hand, and just the middle finger on the right hand—and
the words she had to type in those two tests were in English, which is not her first language. So,
basically, she managed to reach a good above-average speed in two minutes while typing very
inefficiently and without relying on the muscle memory she would have had if the test was in
Italian. The point I want to make with this example is not that my girlfriend nurtures some kind of
hidden typing talents, but that your baseline speed is probably much higher than you think,
especially if you have never actually measured it. I believe my girlfriend could very easily reach
an average of 80 WPM with just an hour or two of practice without changing anything about the way
she types; unfreezing one or two more fingers on her right hand would also most likely bring her
already very close to 100 WPM. Alas, we will never know for sure since she could not care less about
typing.

#### Long-term improvements

The best thing you can do for your long-term typing experience is to learn an alternative keyboard
layout. Why are computers equipped with QWERTY keyboards anyway? The answer has actually nothing to
do with how computers work, and instead everything to do with—you guessed it—how typewriters used to
work. This means there is literally no reason we should keep producing new computers with this
layout, but we still do anyway. People argue we are used to QWERTY and it would be hard to switch to
a different layout. I respectfully disagree. First of all, these are clearly not the same people
that keep shifting things around in literally all of the most used programs ever. Somehow ditching
QWERTY for a more sensible layout is "crazy", "too confusing" and could "repel potential users",
while moving the "share screen" button in Slack for the third time this year is an "update", a "good
UX improvement" and generates "genuine interest in the app". Make your own mind up. In addition,
people are not born with predefined concepts of "keyboard layouts" in their minds and can learn how
to type in QWERTY just as easily as in, say, DVORAK, similarly to how newborns in the real world
have no concept of grammar and can learn to speak English as their first language just as easily as,
say, Chinese. I think learning any post-QWERTY keyboard layout from scratch is actually easier than
learning QWERTY from scratch, since post-QWERTY layouts are optimized for ease of typing while
QWERTY is optimized for minimizing mechanical errors in typewriters. My opinion is unfortunately
only supported by common sense and anecdotal evidence derived from my own personal experience. As
far as I know, nobody has published a scientific study on the process through which different people
first learn how to type on different keyboard layouts (if you know one, please send it to me!). I
can only find publications such as [this
one](https://www.researchgate.net/publication/252214871_Comparing_Different_Keyboard_Layouts_Aspects_of_QWERTY_DVORAK_and_alphabetical_keyboards
"ResearchGate - Comparing Different Keyboard Layouts: Aspects of QWERTY, DVORAK and alphabetical
keyboards") that compare the results of making QWERTY-native typists use different keyboard layouts,
which is totally useless. This is what this publication says about the "DVORAK Layout vs QWERTY"
speed comparison:

> Norman did controlled experiments where he compared performance on the QWERTY keyboard, the DVORAK
> keyboard, the alphabetic keyboard and a random layout. They found that novice users performed
> better (measured in typing speed, not number of errors) with the QWERTY layout than with the
> [DVORAK layout]. This is probably caused by prior experience with the [QWERTY keyboard]—This is a
> common problem in these experiments.

What all these kind of publications have in common, though, is the sheer amount of quantitative data
embarrassingly putting the QWERTY layout far behind pretty much any other alternative layout in
terms of economy of motion. As most musicians and sportspeople know, economy of motion is crucial
when trying to add a dozen BPMs to your scale exercise or shave off an extra second from your lap
time. In typing, economy of motion is achieved in two ways: 1) maximizing the usage of home row
keys; 2) minimizing same-finger keystroke combos. [This page](https://www.keybr.com/layouts "Keyboard layouts comparison on keybr.com") makes it very easy to visually compare layouts by
enumerating economy of motion-related data and showing a usage frequency chart for each layout. The
page seems not to disclose where this data comes from, but its results are remarkably similar to the
ones also present in the above publication, so I think they are credible. QWERTY is literally the
worst layout in all considered metrics, at least for (but not limited to) the English language. The
Colemak layout, other than having the best home row statistics, also features one more optimization
not immediately evident from the above results: it is designed to maximize "rolling" movements, aka
[the kind of finger tapping you do when you want to express
impatience](https://www.youtube.com/watch?v=pHaAW1doeSU "'Impatient person tapping on a table with
fingers' stock video footage from YouTube"). This is a very natural movement everyone already knows
how to do very efficiently and very comfortably. This feature, alongside home row usage
maximization, makes Colemak a great layout choice if you are looking for a more comfortable and
effortless typing experience.

So far I have only talked about the measured advantages of non-QWERTY layouts, and argued for an
utopic scenario in which QWERTY and its obsolete idiosyncrasies are forever abandoned for a more
ergonomic, typewriter-agnostic experience. But what about real life? What about people who already
know how to type in QWERTY, and would need to re-learn everything from scratch in case they would
switch to a different keyboard layout? Is the whole process worth it? It depends on how much do you
care about economy of finger motion. If you are like the absolute vast majority of people, you do
not care at all. You probably did not even know other keyboard layouts existed until you started
reading this article—that is understandable. The question is: should you care? We know that
professionals involved in finger-centric activities such as guitarists and pianists care a lot about
economy of finger motion. They in fact care so much that they devote entire afternoons to practicing
the same motions over and over, identifying and correcting excess movement to reduce and hopefully
eliminate all unnecessary stress and muscle tension. They do all this in order to develop good
technique that will both reduce the chance of injury and allow them to glide through the
fretboard/keyboard more efficiently. If people pay you to spend time in front of a computer, I argue
you are also part of the "professionals involved in finger-centric activities" group and should care
about economy of finger motion.

In isolation, learning touch typing has a much more positive effect on economy of motion than just
switching to a non-QWERTY layout. Usually, though, people who switch to alternative layouts will
also be forced to learn how to touch type. If you are a <70 WPM non-touch typist, I think you should
seriously consider switching layouts. You would still have to go through a re-training process
anyway for touch typing alone, but layout switching also gives you the added advantage of unlocking
higher potential speed caps and achieving a more confortable technique that no amount of QWERTY
practicing will ever bring you. If you are a ~100 WPM QWERTY touch typist, I still think it is worth
switching but the ROI time frame will be longer, simply because it will take more time to reach your
old QWERTY typing speed. Therefore, the sooner you switch, the better.

I switched from QWERTY to Colemak on 2021 and so far I have not had any reason to regret it. Before
the switch, I was already able to type 110 WPM with QWERTY. It took me around six months (~30
minutes of everyday practice) to reach and eventually surpass that speed using the new layout, but
the improvements in finger comfort and the amounts of relieved tension were noticeable since the
beginning. I am still able to type in QWERTY on my computer keyboard even though my top QWERTY speed
has now mostly decreased to an average of 70 WPM, but it is not clear how much of this decline is
only due to the layout switching or simply from the fact that I have not been practicing QWERTY
anymore since 2021. My QWERTY thumb-typing abilities on phone screens have remained completely
intact. A Colemak-specific advantage for QWERTY-native typists I only realized _in medias res_ is
that your most common keyboard shortcuts will look the same in both layouts. Even after switching,
you will still be able to copy (`CTRL + C`), cut (`CTRL + X`), paste (`CTRL + V`), select all (`CTRL + A`),
undo (`CTRL + Z`) and close windows (`CTRL + W`) without re-training your muscle memory. To
be completely honest, I still have yet to come across a valid argument against learning alternative
keyboard layouts. I will quote some of the ones I most commonly found being thrown around down below
alongside my own response to them, in order to let you make you own mind up about this whole
switching matter by also hearing the other side of the argument.

> Fallacy: _QWERTY is faster because most of the fastest typists use QWERTY._

This is like saying men are able to create compose much better classical music than women
because most of the best classical composers are men. The reason is purely statistical and has
nothing to do with the merits of the layouts themselves. Most of the fastest typist use QWERTY
simply because the vast majority of people use QWERTY.

> Fallacy: _If [alternative layout] is actually better than QWERTY, then [alternative layout] would
> have long become the new standard._

This statement is very popular because it sounds logical, but history teaches us the world
rarely follows logical reasoning. Most times normality is very far from what would be considered
"logical". For example, since the overall population gender distribution is roughly 50% male and
50% female, it would make sense for a company striving to only hire the absolute best people to
be consisted of 50% male and 50% female employees. What happens instead is that companies prefer
hiring uncapable men to perfectly competent women to the point that some states explicitly have
to force companies to hire women, and people (mostly men) are convinced this coercing practice
superimposed by the law makes it very unfair for the men that are left out. Go figure.

> Fallacy: _Even if [alternative layout] is better, the comfort/speed improvement rate compared to
> QWERTY is too slim to make the switching effort worth it._

Again, nobody that I know of has yet done any kind of fair or accurate comparative study about
keyboard layout usage and how they relate to comfort/speed improvements—this kind of discussion
will inevitably draw from anecdotical evidence and/or personal past experience with the topic.
But for the sake of the argument, let's just assume we know for a fact that switching to DVORAK
gives typists an average 4% increase in speed over QWERTY. In fact, this is exactly what the
above-mentioned publication reports, before reaching the same conclusion:

> Dvorak trained students with his keyboard and they were said to “sweep the field”. [...] According
> to West’s findings the QWERTY users reached a typing speed of 81.95 wpm and the DVORAK trained
> users achieved 84.90 wpm. This is a 4% superiority for Dvorak’s keyboard. This does not sound like
> “sweeping the field” and it is questionable whether QWERTY users will be persuaded by this small
> gain to switch over to [DVORAK].

A 4% speed increase does not seem worth the effort at first glance, but it starts sounding very
enticing as soon as you realize that any kind of small gain, when repeated hundreds of thousands of
times throughout the day, will start to add up and reach distinguishable mass very quickly. Let's
say, as a highly conservative estimate, that the average employee spends a total of three hours out
of their eight-hour work day just typing. From an employer perpective, this means your company could
potentially benefit from more than two hours (140 minutes) of monthly additional work being done for
free for each employee that switches to a 4% faster keyboard layout. This result alone is plenty
persuading for any employer, but let's not stop there. A 4% speed increase is an artificially low
value because it assumes that people were already great touch typists before the switch. What
normally happens instead is that most employees are not touch typists, and will have to learn both
touch typing and a new layout simultaneously during the re-training process. After a hypothetically
long re-training during 24 total hours, given a reasonable starting average WPM of 50 and a
reasonable final average WPM of 110, every employee will be not just 4%, but 120% faster. The
difference in impact is simply striking. Again, from an employer perspective this means that **every
employee will then be able to work 33 hours more every month** compared to before and the typing
classes will have not only basically paid for themselves, but also generated significant profit.
From an employee perspective, this means you could potentially be able to slack off for more than
four days every month and get paid to do it, without any noticeable decrease in work performance. I
suspect that as soon as CEOs realize this, there will be mandatory typing courses and custom
mechanical keyboards with ergonomic layouts available in all kinds of offices. Luckily for
employees, CEOs do not seem to care about keyboards at all yet and prefer alternative ways of
boosting productivity, such as fun team-building activities and company events in luxury resorts.

<!--
Every job consists of its own special set of core and peripheral skills. In the table below, I
listed some of the ones related to software developing: for every row I put a core skill on the left
column and a related peripheral skill on the right column.

{{< styled-table >}}

| Core skill (high cognitive)   | Related peripheral skill (low cognitive)                    |
| ----------------------------- | ----------------------------------------------------------- |
| writing new code              | typing                                                      |
| debugging old code            | managing open windows and their placement on your screen(s) |
| thinking about your own code  | navigating your codebase                                    |
| reviewing other people's code | managing source control (branches, commits, pull requests)  |
| etc...                        |                                                             |

{{< /styled-table >}}

When they want to boost their own productivity, most people will start reasoning about how to be
faster in core, high cognitive skills, aka the ones that "really matter". In my opinion, this line
of thinking is misleading for at least four reasons:

- Getting faster at core skills is a very long and strenuous path. It usually takes years of
  hands-on experience and/or very good mentoring before one starts noticing significant
  improvements. Reducing time spent in low cognitive activities is instead mostly painless, a very
  mechanical process with very few or no added mental burden, and some of the results can be as fast
  as instantaneous.
- Since most people think core skills are the only ones that "really matter", almost nobody trains
  for peripheral skills. They are generally considered as a given, or something you should just
  strive to be "good enough" at. This virtually means that actively focusing on low cognitive
  activities is not only easier, but it will also make you stand out way more from other developers
  just because the competition is almost non-existent.
- By never practicing low cognitive activities, they will never become muscle memory and their
  mental toll will inevitably be higher than in needs to be. Hunt-and-peck typing or a single
  browser instance with a hundred tabs open, for example, represent distractions and require
  precious brain power that could instead be entirely reserved for complex activities.
- Core skills are highly domain-specific, while the same peripheral skills are usually helpful in
  multiple disciplines, even when they come from wildly different domains and contexts. Being able
  to debug faster will only make me a better programmer, while being able to type faster will make
  me a better programmer, accountant, writer, content editor, marketer, manager...

As a corollary to these reasons I am enumerating below some of the most useful, low-cognitive
productivity boosts I know and use every day in my software developer work day. They are grouped by
topic and by an arbitrary {{< abbreviation term="ROI" explanation="Return On Investment" >}} time
frame:

- **short-term**: minimal changes to your current workflow, bearing instant but small productivity
  boosts;
- **medium-term**: significant changes to your current workflow and setup, bearing equally
  significant productivity boosts noticeable after some hours/days of routine adjustments;
- **long-term**: very big changes to your current workflow and setup, bearing huge productivity
  boosts usually noticeable after several weeks or months of practice.

Many tips or tricks are missing simply because I have not stumbled upon them yet, or I have not yet
had the chance to incorporate them into my workflow and verify their value firsthand. In my
experience, though, applying even a small subset of the following tips is more than enough to
noticeably improve your productivity. My personal recommendation is to try out each of these
techniques as early as possible in your programming career in order to minimize the inherent
friction of disrupting well-established routines and breaking setups (especially when going for
long-term boosts), but they can just as easily apply to senior engineers as well—you just have to
want to do it.

## Everything below is still a work in progress and will be fleshed out sometime in the future.

### Managing open windows

- short-term: use default keyboard shortcuts for switching/opening/closing windows
- medium-term: sort windows in dedicated virtual desktops/workspaces
- long-term: use a custom tiling window manager

In this case, medium- and long-term solutions almost manage to abstract away completely the number
of external screens you need to have in order to work productively.

### Navigating your codebase

- short-term: minimize right-click context menu usage (learn what keyboard shortcuts are available
  in your IDE for your most common actions)
- medium-term: learn how to fuzzy search filenames and file content (most IDEs have some kind of
  fuzzy search function already built-in)
- long-term: use a terminal-based text editor
  - seamless shell integration
  - endless configuration choices
  - they are very old, therefore they are everywhere (your linux server that runs your company's
    tools overnight will have `vi`, but will not have `vscode`)

### Managing source control

- short-term: learn git stashing (useful for local configurations, staging/prod connection strings,
  work in progress, etc.)
- medium-term: use git aliases and github/gitlab CLI for creating pull requests
- long-term: use a terminal-based git browser

!-->