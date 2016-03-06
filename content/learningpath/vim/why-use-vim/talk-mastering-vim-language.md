+++
topic = "vim"
categories = ["vim"]
learning = "Why use vim?"
type = "talk"
video = "https://www.youtube.com/watch?v=wlR5gYd6um0"
date = "2016-02-27T23:47:56-03:00"
title = "Talk mastering Vim language"
+++

He had started the talk, saying about typing not be the bottleneck (made a reference, for an article about tdd, that says exactly the same about TDD), but he says that what is the bottleneck is the time he is thinking how to type...

One point that caught my attention, and I agree with that is that we as programmers, we spent most of our time **editing text**, **not writing text**, and that's a true fact.

Vim focus on edit text firstly, while most of editors when you press a key of keyboard you are literally insert such character in the text, vim in the other hand it's editing the text by this keyword pressed, in other words it's trigging some functionality of vim.

He give some tips of how remember git commands, by split into categories:

**Verbs**

- d => **Delete**
- c => **Change**
- > => **Indent**
- v => **Visually select**
- y => **Yank** (copy)

**Noun in Vim -- Motions**

- w => **word** (forward by a "word")
- b => **back** (back by a "word")
- 2j => down 2 lines

**Noun in Vim -- Text Objects**

- iw => **inner word** (works from anywhere in a word)
- it => **inner tag** (the contents of an HTML tag)
- i => **inner quotes**
- ip => **inner paragraph**
- as => **a sentance**

**Nouns in Vim -- Parameterized Text Objects**

- f, F => "find" next character
- t, T => "find" next character
- / => Search (up to the next match)

By memorize 30 key mappings it's possible to achieve 2000 distinct commands.
