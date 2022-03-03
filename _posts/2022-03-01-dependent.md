---
title: Dependent
category: dev
tags: dev fist-shaking javascript
published: false
---

I was talking to a professional developer friend the other day, and he was suprised by my refusal to use off-site JavaScript libraries and my bending over backwards to avoid using ``npm``.  While I recognize that our use cases are different; I'm still concerned with learning, so prefer doing things myself, and he has to be a lot more concerned with pace of development.

Nonetheless, I remain amazed at how willing even professional developers are to include random ``npm`` modules that they haven't vetted.

## Chains, and not the fun kind

For those who are unfamiliar, ``npm`` is a system for creating JavaScript modules that you or anyone else can plug into their applicastions.  It's a good idea in theory, in that it allows you to find libraries that do something you need and install them without having to re-invent the wheel.  But where I get nervous is from a security standpoint.  Depending on how your actually workflow works, it's *very* easy to end up automatically downloading someone else's code without realizing you're doing it.

On the one hand, this is very convenient, as it means you'll be keeping things up to date.  This can be important from a security standpoint.  But at the same time, you're taking a lot of risk.  How do you know the *new* version of a given module hasn't introduced some vulnerability or another?  More than that, how do you know that the person or people maintaining a given module are keeping *their* dependencies updated?  Do you even know what those dependencies are?

Therein lies the biggest problem for me.  When you choose to install a given module, you're also choosing every module it depends on.  These dependency chains can run *deep*.  Back in 2016, a single programmer [removed a bunch of his modules](https://qz.com/646467/how-one-programmer-broke-the-internet-by-deleting-a-tiny-piece-of-code/) from ``npm`` due to a dispute over naming rights (he was angry about having to rename one of them due to a (newer) corporation having trademarked the name).  Suddenly, developers all over the world were finding their projects not building because a dependency of a dependency of a dependency (...) was no longer there.  Specifically, it was a very simple module called ``leftpad``, which adds leading characters to a string of text.  But it was depended on by some major web applications and frameworks, including [React](https://en.wikipedia.org/wiki/React_\(JavaScript_library\)) (a ubiquitous JavaScript library originally developed by Facebook).

This isn't the only time this has happened, either.  Just over a month ago, at the beginning of 2022, another open source developer [sabotaged](https://www.bleepingcomputer.com/news/security/dev-corrupts-npm-libs-colors-and-faker-breaking-thousands-of-apps/) two of his products, one of which has some 19,000 projects relying on it.  I largely agree with his criticism, namely that he was in essence doing free work for major corporations who use his code.  This is a big problem in the open source ecosystem, where Fortune 500 companies often operate as free riders.  But anyway, once again projects that depended on these modules were suddenly behaving strangely (in this case, printing an endless loop to the browser console).  This demonstrates just how vulnerable large swaths of the internet are: what happens the first time someone compromises a GitHub or NPM repo and adds some truly malicious code?

The other reason I avoid ``npm`` is due to bloat.  All these dependencies may be included because of features that I don't need.  It's easy to end up adding a module only to find that you're download a couple hundred MB of dependency chain.  If none of this supports what I'm ultimately trying to get done, what's the point?

This is the same reason I avoid other people's libraries whenever possible, namely that I simply don't need most of what they allow.  Why include it, then?  If I do end up using one, probably in the case of something that's beyond my capabilities, I don't like pulling it from the developer's site or CDN for the same reasons I mistrust ``npm``.  Things can change, whether deliberately or accidentally, and can break the app.  This is doubly true where I'm writing desktop programs rather than a web page, since I don't want my program to be dependent on internet access without a specific need.

## Automation

For myself, I also worry that relying too much on someone eles's code will make me lazy as a developer.  I should at least think a little bit about how to accomplish something, and only re-use code (that I've written, if at all possible) if it's a good fit.  Plus, by using my own code, modifying it to fit a new need will be a lot easier.

[...]

To be clear, I'm not categorically against any of these tools.  I'm simply explaining why *I* avoid them.  If my needs were different, I'd probably feel differently.  I don't especially care what other people use for their purposes, and it's not like my criticisms have any bearing on the larger development community.

For me right now, I find the best thing about these libraries is that I can check the code and see how they work.  This is a fantastic resource for learning, particularly in situations where I don't even know what to ask, much less how to do it.  