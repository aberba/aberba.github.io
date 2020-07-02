---
title:  "Why no one is using your D library"
date:   2020-07-02 10:20:23
categories: [D]
tags: [D]
---

![No one](/images/2020-why-no-one-is-using-your-d-library.png) 

Here's the thing. When something looks good, most of us are hard-wired to think it also tastes good. Yeah that's a real thing. Some food chains go even as far to make their product look good on camera...watch this video.

<div class="embed-container">
<iframe class="embed" src="https://www.youtube.com/embed/oSd0keSj2W8" width="560" height="315" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture"  allowfullscreen="allowfullscreen"> </iframe>
</div>

First of all, if you have published a D package in the [Dub](https://code.dlang.org) package repository, congratulations. 

> ## You are awesome ♥️

Doing that alone shows that you care to provide others with something they can also use to get job done. 

But if your package lacks great documentation, some of us are NOT going to see its appeal from a first impression. And the **first impression** thing is very important.

> ## It LOOKS good, it TASTES good.

Yeah, many of us are not "smart enough" and spoiled :) so you'll need to dumb it down for us. This includes new D users looking to try something new.

> ## Do it, for me!! Please, I'm begging you!!

But seriously, we use third-party packages mostly when we want to **GET THE JOB DONE™**. Quite often its convenient to have a brief documentation in at least your `README.md` file:

* What it is
* What it can do (feature list)
* How to install and use it
* Example(s) of how to use it
* Link to your docs or website
* Maybe link to your API specs (build docs)
* And any other necessary information

Now, you don't have to put _every_ example in the README. And whilst you are at it, please don't put cryptic code that shows **every cleaver feature your package has got** in it as a first or only example. That's not an example, that belongs in your `unittest`.

> ## We just started dating, spare me that for later.

You know, my quick little research tells me all [the most popular packages on dub](https://code.dlang.org) have at least a fairly good documentation in their README to get you started. That speaks to why many people are using it. Bots, CI/CD whatever, its still being used. 

Also if you've got a real documentation, its also good to have it referenced.

## :> But you can check the build docs
Jeez, come on! That's an API specification/definition, not a documentation. The English can be misleading but they are not the same thing. Friends at Swagger [have even written about it](https://swagger.io/resources/articles/difference-between-api-documentation-specification/). 

> API documentation, API specifications, and API definitions are all related, but they are different entities. And each of these serves an important purpose.

## :> Its not  big deal deal, check the `examples` folder
That's not good as a first impression to get me hooked. 

> :> It doesn't look good, it most likely won't taste good as well.

The `examples` folder is always welcomed for more detailed use cases. 

## :> Nah, I'm not into this whole Open Source responsibility thing.
Then I take my "congratulations" back. But seriously, its unfair to leave me in the dark. You owe me one. I just congratulated you. 

If you want your package to be used by everyone, it has to be...watch this video.

<div class="embed-container">
<iframe src="https://www.youtube.com/embed/an74PBcdgx4" width="560" height="315" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture"  allowfullscreen="allowfullscreen"> </iframe>
</div>

So I'll just leave it there. Thanks for reading. 