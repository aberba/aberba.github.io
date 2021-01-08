---
title: "Why foo/bar/baz examples suck"
date: 2020-12-15 10:20:23
categories: [programming]
tags: [D]
---

![No one](/images/2021-foo-bar-baz.png)

Its not uncommon to come across code like this:

```d
foo(bar(baz(1), 2));
```

Now, this is just a basic example to illustrate the use of abstract names in
example code. This habit has become so common to the point that some known
languages use those in their official docs. This is very troubling and here are
3 reasons why.

### 1. Abstract and has no real meaning

Without using real names, examples require some level of cognitive effort to
visualize and contextualize their use case. This cognitive load, even when
small, adds up to the difficulty of understating the code. This is akin to using
single letters as variable names in code. They are a mess to read and
understand.

> of course, with some very very very few exceptions

Try to understand this code:

```d
int total = apples(2) + water(10)' // 😟 What ??
```

> Hey, the names doesn't really matter 🤷‍♀️ Focus on the idea 😉

### 2. Not beginner friendly

Coding is a very practical trade and reflects real-world problem solving, be it
domain specific or generic. Using unreal names takes the reader far from this
reality into total obscurity.

![Foo sucks](/images/2021-foo-example.jpg)

This is a not a good experience for beginners. It's not even good for seasoned
developers either, except they might be able to get around it. In fact, it is an
abomination to do this in official language docs.

> Great docs (examples) sell, don't make it a tough sell.

### 3. Boring and not interesting

Imagine reading a book, maybe a novel 😰, with `foo`, `bar` and `baz` all over
the place. Every character in the book is either called `foo`, `bar`or`baz`.
That's a torture stake.

This a essentially what you are doing in code when you illustrate an idea or an
algorithm with abstract variable, function or class names. Code that is hard to
read without contextualizing those symbols to real world references.

Yes, writing real variable names involve work. However, unless you are writing
`foo`, `bar` and `baz` for your personal use, you are passing on the tax to
someone else.

> Please use real meaningful names 🗣🎙
