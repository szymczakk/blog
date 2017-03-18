---
layout: post
title: Konfiguracja CI dla mojego konkursowego projektu.
summary: Wpis opisujący moją prawie 3godzinną drogę przez konfigurowanie continous integration dla projektu .NET Core-preview3, czyli najnowszej wersji która jest aktualnie zmieniana i o tym dlaczego uparłem się na Travis'a a skończyłem w AppVeyor'ze.
published: true
tags: dsp2017 ci travis appveyor
categories: posts 
--- 

### HEJ!

Jak to zapewne każdy kto rozpoczyna nowy projekt na daj się poznać, zamierzam napisać o tym jak to sobie skonfigurowałem środowisko do pracy. Żeby żyło się lepiej... :wink:

<!--more-->

_(mały edit na samym końcu)_

## CI

CI - continous integration, w języku lokalnych ludzi "ciągła integracja" (ale tragiczne tłumaczenie). Narzędzie (element procesu, łotewa) służące ciągłemu pobieraniu naszego kodu, budowaniu go i odpalaniu testów w celu sprawdzenia czy to co pchamy do repo ma jako taki sens. Z popularnych aplikacji/serwisów do CI można wyróżnić [TeamCity](https://www.jetbrains.com/teamcity/) (używam w pracy), [Jenkinsa](https://jenkins.io/) i [Travisa](https://travis-ci.org/). Dlaczego akurat te 'wyróżniłem'? Bo z nimi miałem jako taką styczność (o innych na tym etapie pracy nie słyszałem, nie czytałem, nie szukałem).

Z uwagi na to że TeamCity używam w pracy, nie chciałem go do swojego projektu. Jenkins nie ma darmowej wersji w chmurze, tak więc został Travis.

### Travis
Nie wiem dlaczego, ale już dawno dawno temu zafiksowałem się na punkcie [Travis'a](https://travis-ci.org/). Nigdy na poważnie z niego nie korzystałem ale bardzo chciałem. No więc jedziemy. Wbijam na Travis'a, łączę się z githubem, wskazuje repo... i co dalej :confused: :question: :question:

Pierwsza (i słuszna jak się okazało) myśl 
> "ukradnę" komuś konfigurację :smiling_imp:

a że ostanio coraz częściej ogarniam sobie projekty open-source + [Piotrek Gankiewicz pisał na swoim blogu o CI](http://piotrgankiewicz.com/2017/03/13/net-core-continuous-deployment-part-i-travis-ci-integration/) no to mam już cel! Pomalutku, pocichutku zakradam się na jego bloga, w dziale portfolio znajduję projekt Warden (na razie jeszcze nikt mnie nie zauważył), odnajduję [kod projektu](https://github.com/warden-stack), plik '.travis.yml' dowolnego serwisu i jestem w domu. Teraz tylko szybkie Kopy-pejst i CI gotowe :smiling_imp:

#### a tu zonk. 

Okazjuje się że piotrek ma to przygotowane pod .NET Core-preview2. Ale nie, zmiana z preview2 na preview3 nie może być zmianą czysto kosmetyczną. Oni musieli przejść z JSON'ów na CSPROJ'e... Ehhhh... no to dobra. Szablon już mam. Jest dobrze! Teraz przelecimy szybko dokumentację travisa, podmienimy wersję, ogarniemy pliki .sh (które też ukradłem...) i git. 

#### a tu zonk2.

według dokumentacji travisa, CI które tak bardzo chciałem wypróbować nie wspiera preview3. Ale odkrycie tego nie było takie proste, nie myślcie sobie. Dwie godziny orałem te pliki w poszukiwaniu błędu. No ale travis sam się w tym momencie dla mnie skreślił (będę smutał). Rozwiązanie tej sytuacji okazało się bardzo proste (o czym na końcu wpisu), ale dotarło do mnie za późno i musiałem znaleźć sobie jakieś inne CI dla swojego super-mega-oxi-action-intelligence-plus projektu.


### AppVeyor

Nie zrażony swoją porażką (która nie była moja, ale o tym za chwilę) zacząłem guuglać czym by tu zastąpić Travis'a. Tak natrafiłem na link do stronki [AppVeyor](https://www.appveyor.com/). Okazało się, że serwis ten obsługuje całe CI na Windowsach! (ponoć stoi to na Azure). No to przecież prosciej być nie może, nie :wink:. Dodatkowo AppVeyor'a można skonfigurować bez użycia plików 'yaml', tylko poprzez samo wyklikanie sobie wszystkiego w konfiguracji (co polecam tylko cześciowo, ale o tym tez za chwilę). Tak więc do roboty.

Po zarejestrowaniu się na stronce (ja zrobiłem to przy pomocy mojego konta na GitHubie) przechodzimy do tworzenia nowego projektu.

Pierwszym ekranem który nam się ukaże jest miejsce gdzie można wybrać sobie źródełko naszej aplikacji. U mnie, dzięki rejestracji przez GH wszystko miałem już zaczytane

<img src="{{site.baserl}}/images/appveyor/e1.png">

Wybieramy projekt ktory chcemy budować i przechodzimy dalej.

Kolejnym krokiem jest zakładka SETTINGS i tu zaczyna się nasza mała magia. Z najważniejszych ustawień uważam że należy wyklikać sobie środowisko które będzie nam budowało naszą aplikację

<img src="{{site.baserl}}/images/appveyor/e2.png">

oraz zmienne środowiskowe wykorzystywane przez apkę (klucze i inne takie).

Kolejnym elementem który ustawiłem w tej konfiguracji była zakładka "Build" gdzie wpisałem swoje mega-turbo zaawansowane skrypty które AppVeyor ma odpalać

<img src="{{site.baserl}}/images/appveyor/e3.png">

następnie podobnie należy zrobić w zakładce test, tylko podać skrypt do odpalania testów

<img src="{{site.baserl}}/images/appveyor/e4.png">

i na tę chwilę to jest wszystko co ustawiłem w swoim CI aby pobierało i budowało moją aplikację. 

Ostatnią ciekawą rzeczą (o której wpomniałem wcześniej) jest fakt, że po takim "wyklikaniu" sobie wszystkich ustawień, można wejść w zakładkę "Export YAML" i pobrać sobie cały pliczek konfiguracyjny

<img src="{{site.baserl}}/images/appveyor/e5.png">

Pisałem wcześniej iż uważam że takie wyklikanie sobie jest "po części" dobre. Moim zdaniem jest tak dlatego, że jeśli wszystko wyklikamy sobie w środowisku, to nie mam szans przejrzeć zmian, które zostały wprowadzone w konfiguracji naszego Continous Integration. A tak, dzięki trzymaniu tego w GIT'cie mamy szansę zawsze wrócić do poprzedniej konfigracji, lub sprawdzić kto co zmienił i dowiedzieć się dlaczego. To jest właśnie powód, dla którego nie napisałem tutaj o tym, że w pierwszej zakładce ustawień "General" jest flaga, która pozwala całkowicie zignorować plik appveyor.yaml i oprzec całą konfigurację tylko o panel web'owy. Ale NIE POLECAM tego robić.

Po takiej konfiguracji, każdy mój commit do repo ktore podpiąłem pod to CI uruchamia builda oraz wszystkie testy.

#### Dygresja dotycząca Travisa

Jak wspomniałem wcześniej, miałem problem z konfiguracją Travis'a pod preview3. Dlaczego? Bo w dokumentacji, były wyraźnie wyszczególnione wersje które działają w Travisie (i preview3 tam nie było). Napisałem do nich na twitterze i następnego dnia dostałem odpowiedź

<img src="{{site.baserl}}/images/appveyor/e6.png">

wbijam na podrzuconego przez nich [pull-requesta](https://github.com/travis-ci/travis-ci/issues/7255), patrzę, a tam poprawki w dokumentacji dotyczące .NET Core. I wyraźnie napisane, że nie to, iż Travis wspiera tylko te dwie wersje wypisane w dokumentacji. Jedyne co, to trzeba podać wersję pod którą chce się budować. Czyli należy wejść na stronę .net core, sprwadzić sobie wersję, wpisać ją... i ponoć wszystko bangla. Niestety nie mam już na razie czasu aby to sprawdzić.


### Następny krok

Kolejnym krokiem w konfiguracji środowiska będzie konfiguracja CD (continous delivery). Na 99% będę opakowywał swóją apkę w dockera i wrzucał na [Heroku](heroku.com)

Dzięki za poświęcony mi czas!

k.

### Edit

Dobra, wymiękłem... Jednak tak się zafiksowałem na punkcie Travis'a, że zaraz po napisaniu tego posta zabrałem się za próbę zbudowania apki w Travisie i się udało. Dzięki poprawionej wersji dokumentacji, podałem odpowiednią wersję .Net Core SDK jako parametr do builda i wszystko na zielono.

Sory AppVeyor, ale zostanę przy Travisie :blink:
