---
layout: post
title: Async over sync problem
summary:
published: true
tags: net .net async await sync problem
categories: posts
---

### Hi!

Today I was forced to use .NET Framework MVC 5 (not core!!) as a small sample/test project. And I felt into a trap...
<br>
<!--more-->
<br>
... as I generated boilerplate MVC app and move on to proper implementation.
<br>
<br>
I was supposed to fetch data from the external API and show them on the web. As simple as it looks like.
<br>
With additional class, it was 7 lines of code. Approx. 4 mins of writing. And done.
<br>
<br>
But wait...
<br>
<br>
Debugger attached, code executed, API called but no result returned. It took me an additional 5 or 10 mins to figure out the problem.
<br>
<br>
.Net Framework MVC boilerplate is by default SYNC.
<br>
<br>

`public ActionResult Index()`

<br>
<br>
.Net Framework Core MVC boilerplate is by default ASYNC.
<br>
<br>

`public async Task<IActionResult> Index()`

<br>
<br>

I'm so used to .Net core, that it took me so much time to figure out, that I forgot to `await` my code and change the action signature to `async` one.
<br>
<br>
As the only symptom of such a situation was debugger never going into the code that was after first `await` keyword. It was the only clue that I forgot about `async` signature...
<br>
<br>
Shame on me :wink:
<br>
<br>
k.