---
author: Nicolò Traini
title: Easy productivity boosts
summary: simple and effective ways to better manage your work time
slug: easy-productivity-boosts
translationKey: easy-productivity-boosts
description: A summary of easy productivity boosts to better manage your work time.
keywords: [programming, productivity, window manager, vim, WPM, typing, bottleneck]
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
about how to be faster in high cognitive skills, aka the core skills, the ones that "really matter".
In my opinion, this line of thinking is unfruitful and problematic for (at least) four reasons:

- Getting faster at core skills is a very long and strenuous path. It usually takes years of
hands-on experience and/or very good mentoring before one starts noticing significant improvements.
Reducing time spent in low cognitive activities is instead mostly painless, a very mechanical
process with very few or no added mental burden, and some of the results can be as fast as
instantaneous;
- As the introduction states, everybody working on their productivity naturally aims for their core
skill set. Improving your core skills puts you in a race which not only is very long and hard, but
also features many, many other racers aiming for your same goals. On the contrary, almost nobody
trains for peripheral skills or low cognitive activities! They are generally considered as a given,
stuff you should be only "good enough" at. This virtually means that actively focusing on those
kinds of activities is not only easier, but it will also make you stand out way more and set you
apart from everybody else;
- Core skills are highly domain-specific, while the same peripheral skills are usually helpful in
multiple disciplines, even when they come from wildly different domains and contexts. Being able to
debug faster will only make me a better programmer, while being able to type faster will make me a
better programmer, accountant, writer, content editor, marketer, manager...
- if you never train low-effort activities, they will never become "muscle memory" and their mental
toll will actually be very similar to the one required for high-effort activities, making your
whole work harder than it needs to be; hunt-and-peck typing or a single browser instance with a
hundred tabs open, for example, represent distractions and require precious thought that could
instead be used exclusively for things that "really matter"

These are all the low-effort production boosts that I know and use every day on Ubuntu and Windows
at work. They are all grouped by topic and ranked according to these goal types:

- short-term: instant but small improvements, with minimal or no changes to your current setup
- short-term: big improvements, noticeable after some hours/days of routine adjustments
- long-term: huge improvements that require significant changes to your current setup, noticeable
  usually after several weeks/months of practice

### Typing

- short-term: remap CTRL and CAPS-LOCK keys; switch to EN keyboard layout; increase key-repeat speed
- medium-term: learn touch typing (reaching 100 WPM would be also a huge help)
- long-term: switch to a non-QWERTY keyboard layout

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
