---
layout: post
title: Dlaczego wybrałem Jekyll'a zamast wordpress'a (czyli o tym jak narzekam na swoją niewiedzę)
date: 04-03-2017
published: true
tags: dsp2017 jekyll opinion
categories: posts 
--- 

#### Hej!

Dzisiaj natchnęło mnie, żeby napisać słów kilka o systemie "blogowania" z którego korzystam. 

[Jekyll](jekyllrb.com) bo o nim mowa, jest serwerkiem generującym statyczne strony internetowe z markdowna. 

<!--more-->

### README FIRST 
Zanim przeczytasz dalej, proszę... podpisz krwią [tę umowę](#agreement)

### Najpierw o problemach

Niby brzmi fajnie... ale jest napisany w Ruby... RUBY... r... u... b... y... Ehhh... Uruchomienie tego na windowsie... To lekkie wyzwanie :smile:
Niby bierzesz sobie [chocolatey](https://chocolatey.org/), wykonujesz 

{% highlight text %}
 choco install ruby
{% endhighlight %}

i działa. No i niby tak. Udało się odpalić, wygenerować stronę, ale zrobienie z tym czegokolwiek wymagało dosintalowania różnych ruby-rzeczy na których totalnie się nie znam.

A poza tym... Mam kilka pierdołowatych pomysłów jak go ~~poprawić~~ dopasować bardziej do mnie, no więc dopisałbym sobie coś. Ale jak, skoro jest w ruby :disappointed:

No ale koniec marudzenia...

### Teraz te plusy

Największy z nich to fakt, że Github, taka strona dla geeków/dev'ów/i innych niemających życia, umożliwia uruchomienie go... tam gdzieś w tle :smile:

A co to oznacza?

A tylko tyle i aż tyle, że bierzesz sobie git'a, odpalasz ulubiony edytor tekstu i nie przejmujesz się zupełnie tym, jak i gdzie hostować swojego bloga! Żadnego użerania się z VPS'em, żadnych opłat. Nic. 

Wbijasz na Github'a, zakładasz za darmo konto tutaj

<img src="{{site.baserl}}/images/gh_registration_screen.jpg">

tworzysz repo.

<img src="{{site.baserl}}/images/gh_create_repo_screen.png">

W celu włączenia sobie hostingu wchodzisz w ustawienia repo

<img src="{{site.baserl}}/images/gh_go_to_setting_screen.png">

przestawiasz **GitHub Pages** z 
{% highlight text %}
 None
{% endhighlight %}

na 
{% highlight text %}
 master branch
{% endhighlight %}

<img src="{{site.baserl}}/images/gh_enable_sites_screen.png">

i możesz założyć że użeranie się z hostingiem masz już z głowy. Serio. Widziałeś kiedyś prostszy hosting :smile: :question: 

Ja nie.

Teraz w celu opublikowania jakiejkolwiek strony klonujemy utworzone przez nas repo, przechodzimy na mastera, odnajdujemy katalog 

{% highlight text %}
  _posts
{% endhighlight %}

dodajesz tam plik w formacie 

{% highlight text %}
 ROK-MIESIAC-DZIEN-NAZWA-ODDZIELANA-KRESKAMI.md
{% endhighlight %}

i to co najważniejsze. Na samej górze należy wrzucić coś co się nazywa **[From Matter](https://jekyllrb.com/docs/frontmatter/)** Tak, to jest jedyne upierdziostwo w związku z tym o czym tutaj piszę (poza faktem, że silnik jest w ruby :smile: ).

Wygląda to mniej więcej tak

{% highlight yaml %}
---
layout: post
title: Magiczy tytuł posta
---
{% endhighlight %}

gdzie w prosty sposób definiujesz którego layout (z katalogu _layouts) chcesz w tym przypadku użyć i zaczynasz.

Korzystając z markdown'a oraz liquid'a (o którym pewnie napiszę jeszcze kiedyś) możesz pisać co Ci tylko ślina na... palce (??) przyniesie. Tylko pamiętaj o podpisanej umowie!


<a name="agreement"></a>

### Umowa

Ja, niżej podpisany, zdrowy na ciele i umyśle zobowiązuję się do:
1. niewykorzystywania zdobytej tutaj wiedzy do torturowania innych swoimi wypocinami
2. przestrzegania punktu pierwszego

Jedyną sytuacją zwalniającą z powyższej umowy jest świadoma i całkowicie dobrowolna chęć czytania moich postów przez osoby trzecie wymienione w pkt 1.

:smile:

Dzięki za czytanie (dobrowolne hehe :blush: )! 
k.
