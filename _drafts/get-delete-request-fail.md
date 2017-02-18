---
published: false
tags: dsp2017
---
Hej, 

dzisiaj w pracy, zauważyłem iż jeden z programistów robił bardzo dziwną rzecz. 

{% highlight C# %}
[HttpGet]
public ActionResposne Deltete(int id){
   service.Delete(id);
   return Get();
}
{% endhighlight %}

Niestety takie zapytanie jest bardzo niebezpieczną sprawą, (zwłaszcza w sytuacji, gdy taka akcja nie jest schowana za jakimś "logowaniem"). 
Dlaczego?

Roboty biegające po sieci (między innymi gógla) klikają sobie we wszyskie znalezione GET'owe linki, a co za tym idzie? W momencie gdy taki robot namierzy nam taki link (dostępnym bez logowania) wykasuje nam całą bazę nie patrząc na to co się dzieje.

GET nie powinien prowadzić do żadnych zmian po stronie serwera.

Pamiętajcie o tym :)

k.
