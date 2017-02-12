---
published: false
tags: dsp2017
---
Hej,

dzisiaj w pracy, zauważyłem iż jeden z programistów zrobił bardzo dziwną rzecz, a mianowicie

{% highlight C# %}
[HttpGet]
public ActionResponse Delete(int id){
    service.Delete(id);
    return Get();
}
{% endhighlight %}

niby... wszystko było by ok, ale z takim zapytaniem jest jeden problem.

Jeśli nie schowamy takiej akcji za jakimś "logowaniem" to roboty google (i nie tylko) wyczyszczą nam całą bazę.

Dlaczego?

Działają one na takiej zasadzie, że przeszukują wszystkie możliwe linki, a każdy jeden GET starają się odwiedzić.

Pamiętajcie że każdy GET powininen prowadzić tylko i wyłącznie do akcji które nie wprowadzają żadnych zmian na serwerze.
ŻADNYCH.

k.