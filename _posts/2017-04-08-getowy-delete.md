---
layout: post
title: Get'owy delete
date: 2017-04-08 22:00:00
published: true
tags: dsp2017
categories: posts
---
#### Hej, 

dzisiaj w pracy, zauważyłem iż jeden z programistów robił bardzo dziwną rzecz. 

Popatrzcie chwilkę na ten prosty kawałek kodu i powiedzcie mi co jest z nim nie tak... <!--more-->

{% highlight C# %}
[HttpGet]
public ActionResposne Deltete(int id){
   service.Delete(id);
   return Get();
}
{% endhighlight %}

<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>

Wyłapaliście ?
Takie zapytanie jest bardzo niebezpieczną sprawą, (zwłaszcza w sytuacji, gdy taka akcja nie jest schowana za jakimś "logowaniem"). 

Dlaczego?

Roboty biegające po sieci (między innymi gógla) klikają sobie we wszyskie znalezione GET'owe linki, a co za tym idzie? W momencie gdy taki robot namierzy nam taki link (dostępnym bez logowania) wykasuje nam całą bazę nie patrząc na to co się dzieje. A wydaje mi się że nie jest to porządane zachwanie :confused:, prawda ?

Wedlug dobrych zasad REST'a GET nie powinien prowadzić do żadnych zmian po stronie serwera. Po każdym zapytaniu stan naszej aplikacji powinien być niezmieniony.

Pamiętajcie o tym :)

k.
