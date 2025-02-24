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

This is a compendium of useful yet lesser-known Vim idioms I actually use in my everyday editing,
saving me dozens (if not hundreds) of hours of work. The article is meant both as a resource for the
curious vimmer wanting to expand their skill set, and as an answer to the question puzzled
non-vimmers ask themselves whenever they accidentally open Vim and cannot figure out how to close
it: why in the world do people even bother learning this weird text editor in the first place?

### 1. Adding explicit number values to existing enum classes

One day at work I had to add explicit values to a `TranslationCodeId` C# enum we were using. This
was needed because keeping them implicit could (and actually did) allow programmers to silently add
new values in the middle, effectively making all subsequent ones shift downward and possibly
creating discrepancies if any of them were also being persisted in their numeric form somewhere
else, like a database.

```csharp {lineNos=inline tabWidth=4 style=github-dark anchorlinenos=true lineanchors=enum-pre}
public enum TranslationCodeId
{
   // buttons
   BUTTON_Accept,
   BUTTON_Cancel,

   // labels
   LABEL_Actions,
   LABEL_Column,

   // messages
   MESSAGE_Confirm,
   MESSAGE_GoBack,

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

Your enum class should now correctly show all of its explicit values like this{{< footnote id="footnote-1-source" label="1" anchor="footnote-1-target" >}}:

```csharp {lineNos=inline tabWidth=4 style=github-dark anchorlinenos=true lineanchors=enum-post}
public enum TranslationCodeId
{
    // buttons
    BUTTON_Accept = 0,
    BUTTON_Cancel = 1,

    // labels
    LABEL_Actions = 2,
    LABEL_Column = 3,

    // messages
    MESSAGE_Confirm = 4,
    MESSAGE_GoBack = 5,

    // ...continues...
}
```

### 2. Fixing verbose SQL insert scripts

All highlighted lines in the following script end with wrong characters:

```sql {lineNos=inline tabWidth=4 style=github-dark hl_lines=[13,17,20] anchorlinenos=true lineanchors=sql-pre}
INSERT INTO AdminTranslationCodeText
    (AdminTranslationCodeTextId, AdminTranslationCodeId, LanguageId, Text)
    VALUES
    (NEWID(), 'BUTTON_Accept', 'it', 'Accetta'),
    (NEWID(), 'BUTTON_Accept', 'en', 'Accept'),

    (NEWID(), 'BUTTON_Cancel', 'it', 'Annulla'),
    (NEWID(), 'BUTTON_Cancel', 'en', 'Cancel'),

    (NEWID(), 'LABEL_Actions', 'it', 'Azioni'),
    (NEWID(), 'LABEL_Actions', 'en', 'Actions'),

    (NEWID(), 'LABEL_Column', 'it', 'Colonna');
    (NEWID(), 'LABEL_Column', 'en', 'Column'),

    (NEWID(), 'MESSAGE_Confirm', 'it', 'Conferma'),
    (NEWID(), 'MESSAGE_Confirm', 'en', 'Confirm');

    (NEWID(), 'MESSAGE_GoBack', 'it', 'Torna indietro'),
    (NEWID(), 'MESSAGE_GoBack', 'en', 'Go back'),
GO
```

This usually happens when working on the same file in spurts, each time adding or rearranging lines
and possibly forgetting to check their syntax. Whatever the reason behind the mistakes, how do we
fix them? If you are in an IDE or, at the very least, in a text-editor with syntax highlighting
support, the only way forward is to use your eyes to scan the whole file for red, squiggly lines and
slowly fix all of them one at a time. You could be a little faster with shortcuts to jump through
the current file errors' position list, but you would still need to mentally evaluate the line
context every time in order to correctly decide whether you must be replacing a semicolon with a
comma, or viceversa. With Vim, you can completely offload the mental burden of context evaluation to
your editor instead, and fix everything in one go:

`:/VALUES$/+,/^GO$/-2s/;$/,/ | /^GO$/-s/,$/;/`

{{< details summary="Explanation" open=true >}}

The command is made respectively by two
[`substitute`](https://vimhelp.org/change.txt.html#%3Asubstitute "'substitute' on vimhelp.org")
commands: the first one replaces all misplaced semicolons with commas and the second one replaces
all misplaced commas with a semicolons. We achieve this by prefixing each `:s` call with a custom
[range](https://vimhelp.org/cmdline.txt.html#%5Brange%5D "'range' on vimhelp.org") in order to
restrict the amount of text each command can interact with. In our case, we want to only replace
semicolons from line 4 to line 19, and replace commas only on line 20: we can target these two
ranges referencing the `VALUES` and `GO` relative positions in the file{{</* footnote
id="footnote-2-source" label="2" anchor="footnote-2-target" */>}}.

{{< /details >}}

### 3. Adapt columns of data from external sources

Copying CIDR column from this table: https://neolution.atlassian.net/browse/FRC-2113

1. Paste subnet mask table data
2. Create vimscript table

   `` `[v`]:'<,'>s/\/\(\d\d\)\t.*\t255\(.*\)\t.*/'\1': '255\2',/<Enter>gv:'<,'>j<Enter>:s/\(.*\)/{ \1 }/ ``

   explanation: https://vim.fandom.com/wiki/Selecting_your_pasted_text

3. Copy table into register `m` for later use

   `"myy`

4. Copy snippets of code into different registers for later use

   `/new Re<Enter>"ayf";;"byf";;"cy$`

5. Paste addresses

6. Remove empty lines from your pasted text

   `` `[v`]:'<,'>g/^$/d<C-o> ``

   explanation: https://vim.fandom.com/wiki/Selecting_your_pasted_text

7. Transform into C# code

   `` `[v`]:'<,'>s/\(.*\)\/\(.*\)$/\='<C-r>a' . submatch(1) . '<C-r>b' . <C-r>m[submatch(2)] . '<C-r>c' ``

## Notes

1. It is also possible to do the whole thing on one pass:
   {#footnote-1-target}

   `let n=0 | g/,$/v/\/\//execute "norm $i = " . n | let n=n+1`

   This version of the command basically replaces the hardcoded `0` with an appended custom variable
   that is incremented on every line.{{< footnote label="return" anchor="footnote-1-source" >}}

2. For small scripts like the one in the example, it would actually be both easier and faster to
   just use line numbers (`:4,19s/;$/,/ | 20s/,$/;/`). Most times though you will be dealing with
   very long files spanning multiple screenfuls—retrieving the exact line numbers in those cases
   could be too cumbersome. Just keep in mind both approaches are nonetheless correct and will
   result in the same outcome.{{< footnote label="return" anchor="footnote-2-source" >}}
   {#footnote-2-target}
