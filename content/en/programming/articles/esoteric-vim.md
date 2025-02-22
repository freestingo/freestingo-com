---
author: Nicolò Traini
title: Esoteric Vim
summary: lesser-known features and their time-saving, real-life applications
slug: esoteric-vim
translationKey: esoteric-vim
description: A list of lesser-known Vim features and their time-saving, real-life applications
keywords: [programming, productivity, vim]
date: 2025-02-20
topics: [vim]
---

This is a compendium of useful, lesser-known Vim idioms I have stumbled upon and have actually used
in real life, saving me dozens (if not hundreds) of hours of work. The article is meant both as a
resource for the curious vimmer wanting to expand their skill set, and as an answer to the question
puzzled non-vimmers ask themselves whenever they accidentally open Vim and cannot figure out how to
close it: why in the world do people even bother learning this weird text editor in the first place?

### 1. Adding explicit number values to existing enum classes

One day at work I had to add explicit values to a `TranslationCodeId` C# enum we were using. This
was needed because keeping them implicit could (and actually did) allow programmers to silently add
new values in the middle, effectively making all subsequent ones shift downward and possibly
creating discrepancies if any of them were also being persisted in their numeric form somewhere else,
like a database.

Basically I had to turn this:

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

into this:

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

It is after all a conceptually very easy edit, but it can easily become a nightmare if your enum
does not contain six values only, but, say, 800. Doing it manually would simply be unthinkable, or
at the very least a painfully boring, incredibly time-consuming task. In Vim, you can do it all in
two steps:

1. Assign `0` to all enum fields:

   `:g/,$/v/\/\//norm $i = 0`

   {{< details summary="Explanation" open=true >}}

   - `:g` executes commands on all matching lines; `:v` executes commands on all non-matching lines.
     You can nest `:v` into `:g` in order to [only operate on lines that match `foo`, but do not
     match `bar`](https://vimhelp.org/repeat.txt.html#multi-repeat "'multi-repeat' on vimhelp.org").
     We can leverage this feature to only target actual enum fields and skip all the code comments
     by first matching all lines that end with a comma (`,$`), and then excluding all lines from the
     previous match that contain two forward-slashes (`\/\/`)
   - `norm $i = 0` is a [`normal`](https://vimhelp.org/various.txt.html#%3Anormal "':normal' on vimhelp.org")
     command telling Vim to navigate to the end of the current line and insert `= 0` right before
     the cursor
     {{< /details >}}

2. Increment all numeric values sequentially:

   `vi}/0,$<Enter>ng<C-a>`

   {{< details summary="Explanation" open=true >}}

   - `vi}` selects all text within curly brackets
   - `/0,$<Enter>` [navigates to the first occurrence](https://vimhelp.org/pattern.txt.html#%2F "'/' on vimhelp.org")
     of a zero followed by a comma at the end of a line
   - `n` navigates to the next search result. At this point, all zeroes except the first one should
     be selected
   - `g<C-a>` [sequentially increments](https://vimhelp.org/change.txt.html#CTRL-A "Command documentation on vimhelp.org")
     all numbers within the current selection
     {{< /details >}}

Your enum class should now correctly show all of its explicit values [like this]({{< ref
"#enum-post-1" >}}).
