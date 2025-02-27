---
author: Nicolò Traini
title: Esoteric Vim
summary: niche features and their time-saving, real-life applications
slug: esoteric-vim
translationKey: esoteric-vim
description: A list of niche Vim features and their time-saving, real-life applications
keywords: [programming, productivity, vim]
date: 2025-02-20
topics: [vim]
---

This is a compendium of useful yet lesser-known Vim idioms I actually use in my everyday editing,
saving me dozens (if not hundreds) of hours of work. The article is meant both as a resource for the
curious vimmer wanting to expand their vocabulary, and as an answer to the question puzzled
non-vimmers ask themselves whenever they accidentally open Vim and cannot figure out how to close
it: why in the world do people even bother learning this weird text editor in the first place?

### 1. Assigning numbers to existing enum classes

Implicit value enum members could allow programmers to silently add new members in the middle,
effectively making all subsequent values shift downward and possibly creating discrepancies if any
of them were also being persisted somewhere else in their numeric form.

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

   // ...
}
```

We therefore need to add explicit values next to all members. It is after all a very easy edit, but
it can quickly become a nightmare if your enum does not contain six fields only, but, say, 800. A
manual update of every single line would simply be unthinkable, or at the very least a painfully
boring, incredibly time-consuming task. In Vim, you can do it all in two steps:

#### 1.1. Assign `0` to all enum fields

```vim {style=github-dark}
:g/,$/v/\/\//norm $i = 0
```

- `:g` is a [`global`](https://vimhelp.org/repeat.txt.html#%3Aglobal "'global' on vimhelp.org")
   command: it executes any given action on all matching lines. `:v` instead operates on all
   non-matching lines. You can nest `:v` into `:g` in order to [only operate on lines that match
   `foo`, but do not match `bar`](https://vimhelp.org/repeat.txt.html#multi-repeat "'multi-repeat' on vimhelp.org").
   We can leverage this feature to only target actual enum fields and skip all
   code comments by first matching all lines that end with a comma (`,$`), and then excluding all
   lines from the previous match that contain two forward-slashes (`\/\/`).
- `norm $i = 0` is a [`normal`](https://vimhelp.org/various.txt.html#%3Anormal "':normal' on vimhelp.org")
   command that jumps to the end of the current line and inserts `= 0` right before your cursor.

#### 1.2. Increment all numeric values sequentially

```vim {style=github-dark}
vi}/0,$<Enter>ng<C-a>
```

- `vi}` selects all text within curly brackets.
- `/0,$<Enter>` [searches and jumps to the first occurrence](https://vimhelp.org/pattern.txt.html#%2F "'/' on vimhelp.org")
   of a zero followed by a comma at the end of a line.
- `n` navigates to the next search result. At this point, all zeroes except the first one should
   be selected.
- `g<C-a>` [sequentially increments](https://vimhelp.org/change.txt.html#CTRL-A "Command documentation on vimhelp.org")
   all numbers within the current selection.

Your enum class should now correctly show all of its explicit values like this[^1]:

```csharp {lineNos=inline tabWidth=4 style=github-dark}
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

    // ...
}
```

### 2. Fixing verbose SQL insert scripts

All highlighted lines in the following script end with wrong characters:

```sql {lineNos=inline tabWidth=4 style=github-dark hl_lines=[13,17,20]}
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

```vim {style=github-dark}
:/VALUES$/+,/^GO$/-2s/;$/,/ | /^GO$/-s/,$/;/
```

- The command is made respectively by two
  [`substitute`](https://vimhelp.org/change.txt.html#%3Asubstitute "'substitute' on vimhelp.org")
  commands: the first one replaces all misplaced semicolons with commas and the second one replaces
  all misplaced commas with a semicolons. We achieve this by prefixing each `:s` call with a custom
  [range](https://vimhelp.org/cmdline.txt.html#%5Brange%5D "'range' on vimhelp.org") in order to
  restrict the amount of text each command can interact with. In our case, we want to only replace
  semicolons from line 4 to line 19, and replace commas only on line 20: we can target these two
  ranges by relatively referencing the positions of `VALUES` and `GO`[^2].

### 3. Integrate columns of data from external sources into your project

The nature of this use case could not be more varied. Maybe your marketing team is sending you new
translations, or your product manager is sending you new email template titles. In our example, you
are sent a bunch of IPs you will need to whitelist in your C# application. This is the Jira table
they currently live in (actual values obscured for privacy):

{{< styled-table >}}

| Region       | Location   | CIDR               |
| ------------ | ---------- | ------------------ |
| EMEA         | Manchester | XXX.XXX.XXX.XXX/20 |
| APAC         | Melbourne  | XXX.XXX.XXX.XXX/22 |
| APAC         | Melbourne  | XXX.XXX.XXX.XXX/22 |
| Americas     | Washington | XXX.XXX.XXX.XXX/24 |
| Americas     | Washington | XXX.XXX.XXX.XXX/18 |
| Americas     | Washington | XXX.XXX.XXX.XXX/20 |
| Americas     | Washington | XXX.XXX.XXX.XXX/23 |
| ...          | ...        | ...                |

{{< /styled-table >}}

And this is how the existing whitelisted IP list looks like:

```csharp {lineNos=inline tabWidth=4 style=github-dark anchorlinenos=true lineanchors=ip-pre}
var list = new List<RestrictedIPAddress>()
{
   new RestrictedIPAddress { Address = IPAddress.Parse("XXX.XXX.XXX.XXX"), SubnetMask = IPAddress.Parse("255.255.255.0") },
   new RestrictedIPAddress { Address = IPAddress.Parse("XXX.XXX.XXX.XXX"), SubnetMask = IPAddress.Parse("255.255.192.0") },
   new RestrictedIPAddress { Address = IPAddress.Parse("XXX.XXX.XXX.XXX"), SubnetMask = IPAddress.Parse("255.255.192.0") },
   new RestrictedIPAddress { Address = IPAddress.Parse("XXX.XXX.XXX.XXX"), SubnetMask = IPAddress.Parse("255.255.192.0") },
   // ...
};
```

From a programmer's perspective, the task is pretty simple: all you need to do is basically map each
CIDR address into its corresponding C# object. Nonetheless, the amount of mind-numbingly boring
copy-paste actions needed is directly proportional to the amount of IPs specified in the
table—usually, a lot. The only excitement you will ever get out of this is finding the correct
`SubnetMask` value for each subnet prefix length. Wouldn't it be great if there was a way to let
your editor instantly do all the mapping instead? This way you would not even need to double check
your results since any error-prone human intervention would be removed from the actual editing.
In Vim you can, with some preparations beforehand:

#### 3.1. Create a Vimscript dictionary

Use subnet prefixes as keys, and `SubnetMask` addresses as values. This will come in handy later
when constructing our mapping command. Copy all cells from the first table in [this cheat-sheet page](https://www.aelius.com/njh/subnet_sheet.html "Subnet Mask Cheat Sheet"),
and paste them into your file. It should look something like this:

``` {style=github-dark}
/30 4 2 255.255.255.252 1/64
/29 8 6 255.255.255.248 1/32
/28 16 14 255.255.255.240 1/16
/27 32 30 255.255.255.224 1/8
/26 64 62 255.255.255.192 1/4
/25 128 126 255.255.255.128 1/2
/24 256 254 255.255.255.0 1
/23 512 510 255.255.254.0 2
/22 1024 1022 255.255.252.0 4
/21 2048 2046 255.255.248.0 8
/20 4096 4094 255.255.240.0 16
/19 8192 8190 255.255.224.0 32
/18 16384 16382 255.255.192.0 64
/17 32768 32766 255.255.128.0 128
/16 65536 65534 255.255.0.0 256
```

Discard everything besides the first and the fourth column, and format the result into a
Vimscript dictionary:

```vim {style=github-dark}
`[v`]:'<,'>s/^.\(\d*\).\{-}\(255.*\)\t.*/'\1': '\2',/ | '<,'>j | s/.*/{ & }/
```

- `` `[v`] `` selects all pasted text. `` `[ `` lets you jump to the start of the text you just
   changed, while `` `] `` moves to its end.
- `` :'<,'> `` is a range restricting the following command only to currently-selected lines. When
   entering a command from Visual mode you do not have to actually type the `'<,'>` part—Vim
   fills it in for you.
- `'<,'>s/^.\(\d*\).\{-}\(255.*\)\t.*/'\1': '\2',` looks daunting but it is basically just
   a regex substitution in which we retain the first and fourth columns in capture groups, so that
   we can then format them to our liking.
- `'<,'>j` [collapses all selected lines into one line](https://vimhelp.org/change.txt.html#%3Ajoin "'join' on vimhelp.org").
- `s/.*/{ & }/` surrounds the current line in curly brackets.
{#select-last-pasted-text}

Save your dictionary for later use and remove it from your file:

```html {style=github-dark}
"mdd
```

- `"m` saves whatever text is deleted next into the `m` [register](https://vimhelp.org/change.txt.html#registers "'registers' on vimhelp.org")[^3].
- `dd` deletes the current line.

#### 3.2. Save text snippets into registers for an easier typing experience

You can store parts of C# code that do not change between different `RestrictedIPAddress`
declarations each in its own separate register to be able to not only reduce future typing errors,
but also retrieve them faster.

```vim {style=github-dark}
/new Re<Enter>"ayf";;"byf";;"cy$
```

- `/new Re<Enter>` moves your cursor to a line in which a `new RestrictedIPAddress`
   is being instantiated.
- `"ayf"` copies `new RestrictedIPAddress { Address = IPAddress.Parse("` into register `a`.
- `;;` navigates to the next closing quote.
- `"byf"` copies `"), SubnetMask = IPAddress.Parse("` into register `b`.
- `"cy$` copies `") },` into register `c`.

#### 3.3. Map CIDR addresses into `new RestrictedIPAddress`'es

Copy all new addresses from your external source and paste them in the current file, whenever you
want the new `RestrictedIPAddresses` to be (most likely [at the end of the list]({{< ref "#ip-pre-7" >}})).
If you are lucky, your IPs will already be arranged neatly one by one on neighboring, subsequent
lines. If you are unlucky and are forced to work with Jira tables, you might get something that
looks more like this:

```csharp {lineNos=inline tabWidth=4 style=github-dark anchorlinenos=true lineanchors=cidr-pre}
   new RestrictedIPAddress { Address = IPAddress.Parse("XXX.XXX.XXX.XXX"), SubnetMask = IPAddress.Parse("255.255.192.0") },
   new RestrictedIPAddress { Address = IPAddress.Parse("XXX.XXX.XXX.XXX"), SubnetMask = IPAddress.Parse("255.255.192.0") },
XXX.XXX.XXX.XXX/20

XXX.XXX.XXX.XXX/22

XXX.XXX.XXX.XXX/22

XXX.XXX.XXX.XXX/24

XXX.XXX.XXX.XXX/18

XXX.XXX.XXX.XXX/20

XXX.XXX.XXX.XXX/23
};
```

Remove all redundant empty lines from your pasted text before continuing:

```vim {id=empty-line-remover,style=github-dark}
`[v`]:'<,'>g/^$/d
```

- `:g/^$/d` is a [`global`](https://vimhelp.org/repeat.txt.html#%3Aglobal "'global' on vimhelp.org")
  command that deletes all empty lines (`^$` in regex-speak). We restrict its action by [again]({{< ref "#select-last-pasted-text" >}})
  only selecting the pasted lines as its range.

All the prep work is now done. Map all of your IPs into C# objects!

```vim {id=mapping-command,style=github-dark}
gv:'<,'>s/\(.*\)\/\(.*\)$/\='<C-r>a' . submatch(1) . '<C-r>b' . <C-r>m[submatch(2)] .  '<C-r>c'
```

- At its heart, this command is basically just a regex substitution in which we discard the
  forward-slash in the CIDR line, capture the IP address at its left, capture the subnet prefix at
  its right, and insert those two values in a C# line template. This would result in such a line:
  
  ```csharp {lineNos=inline tabWidth=4 style=github-dark}
     new RestrictedIPAddress { Address = IPAddress.Parse("XXX.XXX.XXX.XXX"), SubnetMask = IPAddress.Parse("20") },
  ```
  
  The problem with that line is that the `SubnetMask` value is wrong. We need to somehow be able to
  tell Vim to dynamically replace those prefix lengths with actual addresses. This is exactly the
  purpose of [sub-replace expressions](https://vimhelp.org/change.txt.html#sub-replace-expression "'sub-replace-expression' on vimhelp.org").
  You can start a sub-replace expression by starting your string with `\=`. We therefore paste
  (`<C-r>m`) the dictionary we saved earlier on register `m` and pass it the captured prefix
  length (`submatch(2)`) as a key to retrieve the correct `SubnetMask` for each line.

It is worth noting that you only ever need to do the above prep work once, making the whole workflow
particularly efficient for periodical tasks. Subnet mask cheat-sheets are not going to change in the
foreseeable future—once you generate your vimscript dictionary and type out [the last mapping command]({{< ref "#mapping-command" >}}),
you can just assign it directly to a keymap of your choice, for example `<leader>cidr`[^4].
Given you have also assigned the [empty-line remover]({{< ref "#empty-line-remover" >}}) command to
the `<leader>rel` keymap, for example, all you ever need to do next time you are sent a bunch of IPs
to whitelist is:

```vim {style=github-dark}
p<leader>rel<leader>cidr
```

Enjoy your free time.

[^1]: It is also possible to do the whole thing on one pass:

      ```vim {style=github-dark}
      let n=0 | g/,$/v/\/\//execute "norm $i = " . n | let n=n+1
      ```

      This version of the command basically replaces the hardcoded `0` with an appended custom variable
      that is incremented on every line.

[^2]: For small scripts like the one in the example, it would actually be both easier and faster to
      just use line numbers:

      ```vim {style=github-dark}
      :4,19s/;$/,/ | 20s/,$/;/
      ```

      Most times though you will be dealing with very long files spanning multiple
      screenfuls—retrieving the exact line numbers in those cases could be too cumbersome. Just keep
      in mind both approaches are nonetheless correct and will result in the same outcome.

[^3]: There is no reason it has to be the `m` register specifically. I just find it easier to
    remember since we are using its contents to **m**ap stuff, but it is also possible to achieve the
    same results using pretty much any other named register instead.

[^4]: Vim stores your last executed command on the `:` read-only register.
