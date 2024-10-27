---
author: Nicolò Traini
title: Easy productivity boosts
summary: simple and effective ways to better manage your work time
slug: easy-productivity-boosts
translationKey: easy-productivity-boosts
description: A summary of easy productivity boosts to better manage your work time.
keywords:
  [programming, productivity, window manager, vim, WPM, typing, bottleneck]
date: 2024-10-22
topics: [debugging]
draft: true
---

Every job consists of its own special set of core and peripheral skills. In the table below, I
listed some that apply to software developers: for every row there's a core skill on the left
column and a related peripheral skill on the right column:

{{< styled-table >}}

| Core skill (high cognitive)   | Related peripheral skill (low cognitive)                    |
| ----------------------------- | ----------------------------------------------------------- |
| writing new code              | typing                                                      |
| debugging old code            | managing open windows and their placement on your screen(s) |
| thinking about your own code  | navigating your codebase                                    |
| reviewing other people's code | managing source control (branches, commits, pull requests)  |
| etc...                        |                                                             |

{{< /styled-table >}}

Most people, when prompted about improving their own productivity at work, will start reasoning
about how to be faster in core, high cognitive skills, aka the ones that "really matter". In my
opinion, this line of thinking is misleading for at least four reasons:

- Getting faster at core skills is a very long and strenuous path. It usually takes years of
  hands-on experience and/or very good mentoring before one starts noticing significant improvements.
  Reducing time spent in low cognitive activities is instead mostly painless, a very mechanical
  process with very few or no added mental burden, and some of the results can be as fast as
  instantaneous;
- Since most people think core skills are the only ones that "really matter", almost nobody trains
  for peripheral skills. They are generally considered as a given, or something you should just
  strive to be "good enough" at. This virtually means that actively focusing on low cognitive
  activities is not only easier, but it will also make you stand out way more from other developers
  just because the competition is almost non-existent;
- By never practicing low cognitive activities, they will never become muscle memory and their
  mental toll will inevitably be higher than in needs to be. Hunt-and-peck typing or a single
  browser instance with a hundred tabs open, for example, represent distractions and require
  precious brain power that could instead be entirely reserved for complex activities;
- Core skills are highly domain-specific, while the same peripheral skills are usually helpful in
  multiple disciplines, even when they come from wildly different domains and contexts. Being able to
  debug faster will only make me a better programmer, while being able to type faster will make me a
  better programmer, accountant, writer, content editor, marketer, manager...

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
had the chance to practice them. In my experience, though, incorporating even a small subset of the
following tips is more than enough to noticeably improve your productivity. My personal
recommendation is to try out each of these techniques as early as possible in your programming
career in order to minimize the inherent friction of disrupting well-established routines and
breaking setups (especially for long-term boosts), but they can just as easily apply to senior
engineers as well—you just have to want to do it.

### Typing

In my experience, reaching a very fast typing speed is the single best thing you can do for boosting
your productivity at work. The advantages it brings are huge, and it is dead easy to train. It is so
easy, in fact, that some people are able to type fast without ever explicitly training for speed;
they just have been typing normally for a very long time. Should you wait several years to become a
"naturally fast" typist, or should you train for just a short amount of time and not have to think
about it anymore for the rest of your life? This is a question unexperienced people understandably
ask in online forums, but the most upvoted response can be totally misleading. A common adage says
working on typing is just a waste of time because

> if you're spending more time typing than thinking about what you're typing, then you're not
> thinking enough.

Another guy in the same response pool from which I fished the above quote asserts that typing fast
is

> completely not important. programming is 95% thinking and 5% doing.

I am convinced this kind of response attracts shares and upvotes because it sounds really smart,
plausible and just the right amount of harsh, even though it is not true at all. I used to agree
with these statements as well, but I still learned how to type at around 110 {{< abbreviation
term="WPM" explanation="Words Per Minute" >}} (starting from a base of around 60 WPM) in something
like six months. I did not do it because I wanted to be more productive, I just enjoyed being able
to type fast. What my experience then taught me is that being able to type fast directly helped me
in being a much more productive programmer in many ways I initially did not even consider: I could
sketch out different ideas in code and find the right solution for a given problem much more quickly
by just trying out different approaches; I could take longer and much more detailed notes during
important calls and meetings which would then help me recollect their context more precisely and
with less confusion at any time; I could transfer my thoughts into writing much more swiftly and
effortlessly so I felt like I could completely focus on a given task without having to think about
unrelated things (such as the position of the letter `B` on my keyboard); I could communicate much
more clearly to my teammates and more often achieve what I was aiming for because I could easily
type long, in-depth messages in the same amount of time in which I used to be able to write just two
short messages... These are just some examples of what I noticed I could do both faster and better
than before, but hopefully by now I have convinced you that downplaying fast typing is complete
nonsense and you should definitely focus on improving your typing speed. If you are unsure on which
peripheral skill to start training first, start here.

#### Short-term typing improvements

Default keyboard layouts are just terrible. If you are born after 1980 and have been using a
computer for a while, at some point you inevitably start asking yourself questions about weird and
inconvenient keyboard layout choices that can only be answered with "It made sense when keyboards
were a part of the typewriter". That may be true, but it does not change the fact that keyboards are
now a part of the computer and a computer is not a typewriter. Why is the `CTRL` key so far away
from the home row, despite its use being so frequent? Why is the `CAPS LOCK` key in the home row,
right next to the `A` key, despite its use being so rare? It would make sense to just swap the
position of those two keys—and that is exactly what some people do. It is such a simple and
reasonable software tweak that some operating systems (such as Ubuntu and macOS) even allow you to
swap `CTRL` and `CAPS LOCK` from their default keyboard settings page, without installing any
third-party script or tool.

In addition, if you are not from an English-speaking country, your default keyboard layout will most
likely be different than the English one. Italian keyboard layouts, for example, prioritize easy
access to very common Italian characters such as accented vowels at the expense of less common or
niche punctuation symbols, such as `@` or square or curly brackets. This is good news for all
Italians except for programmers, which most likely will never use `ò` in their source files while
employing hundreds of `[]`, `{}` and so on. The easiest fix I found is to just use the English
keyboard layout, and rely on your `COMPOSE` key for the rare time you actually need to write a
non-English character. Using three separate keystrokes (`COMPOSE` + `o` + `` ` ``) instead of one
for an `ò` once or twice a day is way faster than using two modifier keys (`ALT GR` + `SHIFT` + `[`)
instead of none every time you want to open a curly bracket.

Another quick and easy keyboard tweak is to just shorten the key repeat delay time and increase the
key repeat rate. These two settings control how long you need to press down a single key before the
operating system starts registering it as multiple repeated keystrokes, and how many times a key
should be repeated in one second. In my experience, I found most people can manage way shorter delay
times and way higher repeat rates than what some operating systems (i.e. Windows) will actually let
you set in their settings pages (a rare exception I can think of could be someone with a disability
that severely hinders finger movement). Check out and experiment with these two settings in your
computer; if you configure it right, this small change will instantly translate into a faster typing
experience whenever you find yourself holding down single keys for whatever reason. Some could argue
that this tweak is a config smell because you should never rely too much on holding down single keys
to do stuff—you should just know the correct keyboard shortcut instead. While I agree with this
sentiment, I still think that tweaking your key repeat settings is always worth doing. First of all,
nothing is stopping you to investigate and learn the proper keyboard shortcuts even after you did
the tweak. Second, there actually are some tasks for which there are no other mouse-free solutions
other than holding down a single key, such as deleting a certain amount of letters from a long word
or a certain amount of words from a long sentence. It is true that you can execute intricate
commands like "delete the previous thirteen words from the current caret position" inside text
editors such as Vim, but that implies you have spent some time counting the exact number of words
that need to be deleted and inputting the correct key sequence to execute said command. In my
experience, after applying the key repeat tweak, holding down `CTRL` + `BACKSPACE` until I delete
thirteen words is way faster than making sure I need to delete exactly thirteen words and then
typing `d13b` in Vim's normal mode.

#### Medium-term typing improvements

Touch typing is virtually the "one weird trick" for reaching very fast typing speeds. Touch typing
essentially means being able to type accurately on your keyboard without ever looking at it. The
idea is to optimize the typing process by evenly distributing key presses among all of your fingers
except for your thumbs, one of which has exclusive access to the spacebar. A touch typist, for
example, does not need to see where the `P` key is before pressing it because they already know by
heart that it is right above their right pinky finger, so they just press it with their pinky.
Memorizing the position of all the keys on your keyboard sounds hard, because it undeniably is. The
good news is that nowadays there are tons of websites dedicated to teaching touch typing, making it
very easy to practice and master at your own preferred pace. I found [this](https://www.keybr.com/ "Keybr touch typing training website") website to be particularly helpful, for example, because it
forces you to work on your weaknesses and avoid indulging in easy exercises, making your practice
sessions more fruitful and efficient.

Somewhat counter-intuitively, mastering touch typing is a sufficient but not necessary condition of
being able to type fast. Some people are able to reach very high WPM counts with just four fingers
plus one thumb. If you do not want to bother learning touch typing, you can still [work on your
sheer typing speed](https://monkeytype.com/ "Monkeytype") and even [challenge your
friends](https://play.typeracer.com/ "TypeRacer - Play typing games and race friends") while you do
it. In my opinion you should strive for reaching a typing speed of at least 100 WPM, but even 90 WPM
or 80 WPM are well above average.

#### Long-term typing improvements

Why do computer keyboards follow the QWERTY layout? The answer has actually nothing to do with how
computers work, and instead everything to do with—you guessed it—how typewriters used to work. This
means there is literally no reason we should keep producing new computers with this layout, but we
still do anyway because... who knows. People argue we are used to QWERTY and it would be hard to
switch to a different layout. This is exactly like saying we are used to English as a _lingua
franca_ and it would be hard to switch to a different language. In the real world, newborns have no
concept of grammar and can learn to speak English as their first language just as easily as, say,
Chinese. Similarly, people who have never seen a keyboard before have no concept of keyboard layouts
and can learn to type in Dvorak just as easily as in QWERTY. I bet learning any post-QWERTY keyboard
layout from scratch is actually easier than learning QWERTY from scratch, since post-QWERTY layouts
are optimized for ease of typing while QWERTY is optimized for avoiding typewriter jamming. My
opinion stems from the fact that I initially learned how to type with QWERTY and used it for the
longest time, up until I decided to switch to the Colemak layout and re-learn how to touch type with
it. The high initial level of friction and uncomfortableness was only due to the fact that I was
virtually learning a second language for my fingers, but that is basically all there is to it; just
after some days of practice I could already notice the sheer number of common words I was able to
type without even moving my hands from the home rows.

- home row and rolling movements optimizations are the focus for colemak
- the more an action is repeated, the more minimizing movement is important: use economy of motion
  in guitar picking and fretting as metaphor

### Managing open windows

#### Short-term

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

### Possible friction points for long-term optimizations

A custom tailored programming environment can be a huge productivity boost for individual
programmers, but nobody works in a vacuum. In some cases it could even introduce unnecessary
friction and hurt the overall team's productivity. Some variables to be carefully taken in
consideration before going down the heavy customization path are:

- intra-company or intra-team IDE variance
  - if you use a custom vim build but the whole team only knows and uses Visual Studio, for example,
    your productivity will plummet the moment you encounter a problem that you don't know how to
    solve and your team only knows how to solve through Visual Studio custom commands
- amount of time you will spend pair programming
  - looking at a completely foreign setup for a colleague can be daunting; you will risk spending
    more time explaining your setup than actually doing the work you're supposed to

A very simple way to neutralize this kind of friction is just to have all of your optimizations
easily revertable at any time.
