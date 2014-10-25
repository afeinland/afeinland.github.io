---
layout: post
title: "How to Acclimate Yourself to a Large Codebase"
date: 2014-09-26 14:30:00
categories: blog post
---

This week marks the end of my first internship. I had many new experiences, one of which was working on a large codebase. Diving in head first to 10,000+ lines of code was quite daunting, and I quickly realized that I needed a set of guidelines to help me get my bearings in this sea of code. Here is what I came up with:

===

_1) Develop a High Level Understanding of the Application._

You need to know _what_ the application does before you can dig into the _how_. Ask someone who is familiar with the codebase to give you a primer on the general behavior of the application. What does the app do? What devices does it interface with? Don't worry about digging into the code just yet. Focus on understanding the gist of what the app does.

Once you have a handle on the behavior of the app, start looking through the code. As a general rule, only about twenty percent of the functions account for eighty percent of the app's behavior. Find these functions and read the documentation on them, and you will be on your way to achieving a thorough, high level understanding of the applications behavior.

===

_2) Don't Dilly Dally ... Get Coding!_

Staring at the code will only get you so far. Writing your own code and observing how the app responds is the next step in acclimating yourself to your new codebase. Write some tests. Change some parameters. Break something! Do what you need to do in order to become comfortable with the codebase.

In addition to writing code, write documentation too. It doesn't have to be an extensive, heavily formatted document or wiki - a simple text file will do. Writing out the behavior of the app in plain english will not only help solidify your understanding of the application, it will also make it easier for others to identify where your understanding may be incorrect.

===

_3) Ask Questions._

While this point pretty much goes without saying, you may find yourself several function calls deep asking "WTF is going on?!" If the comments in the code are not clear enough (or non-existant) and the documentation doesn't help much either, don't be afraid to ask questions. The more specific a question you give, the more helpful an answer you will receive. If you are having trouble distilling your confusion into a few specific questions, you may not have a clear enough understanding of the app's behavior, and should refer back to the first point. You have no greater resource than the other engineers around you, so don't be afraid to ask for help whenever you truly need it.
