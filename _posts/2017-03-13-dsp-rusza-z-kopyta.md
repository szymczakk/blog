---
layout: post
title: Daj się poznać rusza dzisiaj z kopyta!
summary: Maciek A. jednak zdecydował się zrobić dogrywkę w zapisach. Aż jestem sam ciekaw co z tego wyjdzie, oraz ile osób da radę ukończyć konkurs
published: true
tags: dsp2017 maciek aniserowicz
categories: posts 
--- 

### HEJ!

Dzisiaj można już oficjalnie ogłosić że [Daj się poznać 2017](http://dajsiepoznac.pl/) ruszyło! Dogrywkowa runda rejestracji zakmnęła się o północy. Zarejestrowało się ponad 900 osób! WOOW! :anguished:

Jako że już drugi tydzień męczę alexę i na razie odpowiada mi "hello world" to odpiszę jak to skąd pomysł żeby wziąć udział oraz jak to będzie mniej więcej wyglądało.

<!--more-->

#### Skąd pomysł na udział w daj się poznać ?

No więc (tak wiem, nie powinno się zaczynać zdania od "no więc"... i co z tego :laughing: ) jak już pisałem [tutaj]({{site.baseurl}}{% post_url 2017-03-01-daj-sie-poznac-czas-zaczac %}) w firmie w której pracuję wpadli na pomysł aby zorganizować hackaton z Alexą w roli głównej. A że zupełnym przypadkiem wyszło tak, że dzień po tym jak na najwyższym szczeblu padł taki pomysł miałem 1-1 ze [swoim TeamLeader'em](https://twitter.com/flatplanet_pl) i akurat byłem na fazie jarania się tym gadaczem od Amazonu no to na mnie spadło ogarnięcie tego wydarzenia. No więc zaczałem kminić ocb z tym małym pudełkiem i jak zmusić je (może bardziej ją...) do robienia tego co chcę (brzmi trochę jak marzenie każdego faceta). Aż tu nagle Maciek wyjeżdża z daj się poznać. Jako że ja do tych bardziej leniwych należę to w głowie od razu mi się zapaliła lampka "uuuu... ziomuś! dawaj, dwie pieczenie na jednym ogniu" no i się zgłosiłem. 

W ogóle to najpierw chciałem zgłosić jakiś mały projekcik oparty o [Meteor'a](https://www.meteor.com/) bo chciałem go poznac... Nawet już napisałem sobie pierwszy post pod tytułem "Dlaczego wybrałem Meteor'a na konkurs daj się poznać". I musiałem go wyrzucić. Potem pomysł był, żeby napisać jakiś własny projekt (a kilka pomysłów na apki mam) w [.net core](https://www.microsoft.com/net/core). No ale nadal gdzieś tam po głowie gibało mi się że ta alexa na mnie czeka. No więc wymyśliłem sobie, że...

#### A teraz o projekcie

połączę Alexę i .Net Core. 

Pierwszy pomysł był żeby połączyć Alexę i Node JS. No bo jednak z zamiłowania jestem JS'owcem. I ja chyba chciałbym pracować w Nołdzie. No ale chęć poznania Core wygrała. 

Tak więc (od tego tez nie powinno zaczynać się zdań...?) mamy sobie Alexę, pudełko oooo takie

<img src="https://images-na.ssl-images-amazon.com/images/I/61ikAJnULvL._SL1000_.jpg" alt="Echo dot" />

które jest naszym interface'm między nami a serwerami. Ona przez usługi AWS'a będzie komunikowała się z moim backend'em napisanym w .net core, gdzieś tam pewnie w chmurze. On (backend) będzie podzielony na mikroserwisy. Chyba 3. Jeden będzie odpowiadał za komunikację z Alexą. Drugi za komunikację z serwerem MUD'a a trzeci za łaczenie tych odpowiedzi i przetwarzanie rządania Alexa -> MUD, MUD -> Alexa.

Myślę że w następnych postach będę pisał o tym jak to przebijam się przez Alexę i .Net Core. Zobaczymy czy się pokochają czy znienawidzą :wink:

dzięki za czas poświęcony na czytanie!

k.