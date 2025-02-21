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
resource for the curious vimmer wanting to expand their skill set, and as an answer to puzzled
non-vimmers asking themselves why in the world people even bother using this program in the first
place.

### Adding explicit number values to existing enum classes

In one task, I had to add explicit values to a `TranslationCodeId` C# enum we were using. This was
needed because keeping the values implicit could (and actually did) allow programmers to silently
add new values in the middle, effectively making all subsequent values shift downward and possibly
creating discrepancies if any of these values were also being persisted somewhere else.

Basically I had to turn this:

```csharp {lineNos=inline tabWidth=4 style=github-dark anchorlinenos=true lineanchors=enum}
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

```csharp {lineNos=inline tabWidth=4 style=github-dark}
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

It is after all a technically very easy edit, but it easily becomes a nightmare if your enum does
not only contain 6 values, but, say, 800. Doing it manually would simply be unthinkable, or at the
very least a painfully boring, incredibly time-consuming task. In Vim, you can do it all in five
easy steps in something like twenty seconds:

1. Use a [visual block](https://vimdoc.sourceforge.net/htmldoc/usr_10.html#10.5) to place a {{<
   highlight csharp "hl_inline=true,style=github-dark" >}}0 {{< / highlight >}} at the beginning
   of every enum field line:

   `<C-v>/}kI0 <Esc>`

   Breaking it down:

   - _before running the command_: place your cursor on the first character of [your first enum field]({{< ref "#enum-4" >}})
   - `<C-v>` starts the visual block selection
   - `/}k` jumps to the [closing bracket]({{< ref "#enum-16" >}}) while still selecting and
     navigates one line up, in order to rest the cursor on what is the last enum field line
   - `I0 <Esc>` inserts a {{< highlight csharp "hl_inline=true,style=github-dark" >}}0 {{< /
     highlight >}} followed by a whitespace character before every selected line

2. The previous action unfortunately also adds the {{< highlight csharp
   "hl_inline=true,style=github-dark" >}}0 {{< / highlight >}} before all the commented out lines.
   You can easily remove those with the
   [substitute](https://vimdoc.sourceforge.net/htmldoc/usr_10.html#10.2) command, technically
   replacing all instances of {{< highlight csharp "hl_inline=true,style=github-dark" >}}0 {{< /
   highlight >}} before double slashes with empty space:

   `:%s/0 \/\//\/\/`

   Breaking it down:

   - `:%s/old/new` for example substitutes the word `old` with the word `new` once for every line in
     your currently open file. We want to substitute {{< highlight csharp
     "hl_inline=true,style=github-dark" >}}0 //{{< / highlight >}} with just {{< highlight csharp
     "hl_inline=true,style=github-dark" >}}//{{< / highlight >}}, but in our command we have to
     escape forward-slashes with back-slashes since the substitute command supports regex syntax

3. You should now have a {{< highlight csharp "hl_inline=true,style=github-dark" >}}0 {{< /
   highlight >}} sitting just behind every field in the enum definition. You can match the numbers
   you added to the actual enum values by just selecting all text inside curly brackets and
   [sequentially incrementing](https://neovim.io/doc/user/change.html#v_g_CTRL-A) the first instance
   of a number in every highlighted line:

   `vi}ojjg<C-a>`

   Breaking it down:

   - `vi}` selects all text inside curly brackets
   - `ojj` switches the cursor position from the end to the start of your current selection, and
     navigates two lines down in order to exclude the first enum field from the visual block
   - `g<C-a>` sequentially increments the first instance of a number in every currently highlighted line

4. All you have to do now is to make your code compile: record a macro for fixing line syntax. A
   command sequence you could use for this purpose could be:

   `qfdf $i = <Esc>px/,<Enter>^q`

   Breaking it down:

   - _before running the command_: place your cursor back on the [start of the first field line]({{<
     ref "#enum-4" >}})
   - `qf` starts the macro recording on the `f` key
   - `df ` deletes all text up until (also including) the first whitespace character in the line
   - `$` puts the cursor at the end of the line
   - `i = <Esc>` inserts the `=` right before the comma
   - `px` pastes back the number you previously deleted with `df ` into its right place and deletes
     the redundant whitespace
   - `/,<Enter>^` navigates to the next comma and puts the cursor at the start of the line, so that
     your macro will then be easily sequenceable
   - `q` ends the macro recording
