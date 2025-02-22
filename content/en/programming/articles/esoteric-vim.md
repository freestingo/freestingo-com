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
three steps:

1. Insert the first {{< highlight csharp "hl_inline=true,style=github-dark" >}}0{{< / highlight >}}
   manually. This gives you a template you can then iterate and adapt automatically to all the other
   fields:

   `gg/,<Enter>i = 0<Esc>`

   {{< details summary="Explanation" open=true >}}

   - `gg/,<Enter>` first places your cursor at the start of the file, then on the nearest comma
     character it finds through [pattern search](https://vimhelp.org/pattern.txt.html#%2F "'/' on vimhelp.org")
   - `i = 0<Esc>` inserts the explicit value
     {{< /details >}}

2. Insert another value on the next field, but this time record all your actions into a Vim
   [macro](https://vimhelp.org/repeat.txt.html#q "'q recording' on vimhelp.org") so that all changes
   can be indefinitely executed automatically later. One simple way to do it could be just to copy
   the value from the previous field, paste it next to the current field and increment it:

   `nnqm<C-o>y2F <C-i>P<C-a>nnq`

   {{< details summary="Explanation" open=true >}}

   - `nn` places your cursor on the comma at the end of the next field you are about to edit,
     because you are telling Vim to go to the next search result twice and the last thing you
     searched was the `,` character.
   - `qm` starts recording a macro, saving it on the `m` key. Our intention is to perform all
     necessary commands in order to both update the current field and land the cursor on the right
     spot at the end of our sequence; this last point is key because, when done right, it will
     easily allow us to just iterate our macro executions without doing any further manual
     adjustments
   - `<C-o>y2F ` navigates to the [previous cursor
     position](https://vimhelp.org/motion.txt.html#CTRL-O "jump list documentation on vimhelp.org")
     and copies all text going backwards until the second whitespace character it finds
   - `<C-i>P` navigates back to where we were before the previous jump and pastes our text right
     before the cursor position
   - `<C-a>` [increments](https://vimhelp.org/change.txt.html#CTRL-A "Command documentation on
vimhelp.org") the number currently sitting under your cursor
   - `nnq` again places your cursor at the end of the next field you are about to edit, and ends the
     macro recording
     {{< /details >}}

3. Now you can just let Vim do all the work. For example, if your enum has 800 fields, you can just
   do:

   `798@m`

   {{< details summary="Explanation" open=true  >}}

   - [prefixing any number before a command](https://vimhelp.org/intro.txt.html#count "count documentation on vimhelp.org")
     will execute said command not once but exactly that many amount of times. In this case, 798
     times. Why 798? Because you have 800 enum fields, but you already
     fixed the first one in step 1, and the second one in step 2
   - `@m` executes the macro you previously saved on the `m` key
     {{< /details >}}

Your enum class should now correctly show all of its explicit values [like this]({{< ref
"#enum-post-1" >}}). By composing pretty simple commands (pattern search, jump list navigation,
sequential number increments) you are quickly able to express complex behaviours and fulfill in
twenty seconds what would otherwise have been a pretty tedious afternoon.
