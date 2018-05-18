---
layout: post
title: Ważna uwaga podczas korzystania z System.Threading.Tasks.Task
summary: Ważna szybka uwaga dotycząca korzystania z System.Threading.Tasks.Task.
published: true
tags: c# tpl
categories: posts 
--- 

### Hej!

Wiesz co. Tak dzisiaj zauważyłem pewną ciekawostę :smile: i postanowiłem się nią podzielić z Tobą.

Klepalem sobie kod, z użyciem dużej ilości Task'ów gdy nagle okazało się, że co chwila dostaję timeout'y.

Timeout tu, timeout tam... Thready mi umierają... Kminiłem i kminiłem o co to mu tu może chodzić. 
<!--more-->

No i wykmniłem!

Gdy tworzysz sobie nowego Task'a (zwłaszcza łatwo popełnic ten bład gdy zwraca sie Task'a z funkcji) nie zapomnij wykonać tego w jednej z dwóch dopuszczalnych form:

``` 
var task = new Taks(() => doSomething());
Task.Run(task);
```

lub w bardziej skrótowej formie

```
Task.Run(() => doSomething());
```

inaczej dostaniesz Task'a którego nigdy nie uruchomisz... A długo się szuka takiego błedu w kodzie...

k. :wink:
