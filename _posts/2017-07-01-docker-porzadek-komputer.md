---
layout: post
title: Docker, czyli o tym jak udaje mi się zachować porządek na kompuerze, pracując przy różnych projektach w różnch technologiach
summary: Post popisujący w jaki sposób udaje mi się prawie wszystkie wymagane frameworki, biblioteki, serwery etc uruchomić w dockerze, a po skończonym projekcie usunąć z komputera, czyli pozostawić natywną maszynę (albo bardziej system) bez uszczerbku śmieci które wiele z tych usług pozostawia.
published: true
tags: docker
categories: posts ideas
--- 

### Hej!!

Dzisiaj naszła mnie taka myśl, że podzielę się z wami swoim sposobem na to, aby pracując z różnymi frameworkami, serwerami, środowiskami uruchomieniowymi, nadal mieć w natywnym systemie porządek. <!--more--> Przez to określenie mam na myśli stan, w którym po zakończonym projekcie nie muszę spędzić 4/5/6/123h w "Dodaj/usuń programy" aby usunąć wszystkie śmieci zainstalowane przez system (jeśli kiedykolwiek próbowałeś/próbowałaś odinstalować MS-SQL'a z systemu, tak kompletnie, to wiesz o czym mówię :wink: )

#### Docker - po co komu wieloryb na komputerze?!

HA! Jak to po co... po to żeby on, dźwigał na swych barkach (wieloryb ma barki... :confused: :question_mark: ) cięzar uruchamiania tego "wszystkiego" co jest potrzebne do projektu, a nie nasz kochany, natywny... windows'ik/linux'it/osx'ik. Wpis o samym dockerze pojawi się w późniejszym terminie, teraz czysto teoretycznie wyjaśnie do czego go dość aktywnie wykorzystuję.

#### No więc jak to go tak do tego żeby tamto...

Do codziennej pracy w projekcie w pracy potrzebuję Visual Studio, .NET Framework'a, MSSQL'a, MQRabbita oraz IIS'a. Do swojego pet-project'u potrzebuję Visual Studio Code, .NET Core, MongoDb oraz nginx. Do jeszcze jednego projektu w którym pomagam koledze używam Visual Studio Code, PHPMyAdmin, MySQL'a oraz serwer napisany w PHPie. 

Wiecie co by się stałosię gdybym to wszystko i jeszcze więcej posadził na swoim biednym komputerku?

Pewnie nic. Macie rację. No może poza tym, że zamulałby trochę komputer bardziej niż zwykle. Ale po kiego grzyba mi to wszystko lokalnie, jak większośc z tych projektów jest bardzo "tymczasowa"?

Do większości z tych projektów (i nie tylko tych, serio) potrzebuję edytor kodu (Visual Studio/Visual Studio Code), MSSMS (nie znalazłem ładnego panelu jak PHPMyAdmin do MSSQL'a), .NET Framework (to tylko moje lenistwo... :wink: ) oraz wspomnianego wcześniej wielorybka (docker'a).

Dlaczemu to tak?

A no dlatemu: <br>
VS - natywnie <br>
.NET Framework - natywnie <br>
MSSQL - odpalony w dockerze <br>
MQRabbit - docker <br>
IIS - niestety natywnie... kolejny punkt dla lenistwa :sad: <br>
.NET Core - natywnie (lenistwo) <br>
MongoDB - docker <br>
nginx - oczywiście że docker, widział ktoś to dobrze działające na łindołsie ?? <br>
phpmyadmin - docker <br>
mysql - docker <br>
php - docker <br>

Jak widać, poza kilkoma punktami gdzie lenistwo dość mocno przeważyło, do pracy w większości projektów wystarczyłby edytor tekstu + docker. I nie jest to tylko moje zdanie, czytałem artykuł o człowieku (jak znajdę do podlinkuję) który na komputerze ma zainstalowanego sublime'a oraz dockera i nic więcej. Takie maszyny potem wieeeele czasu naprawdę szybko działają :smile:

Mam nadzieję, że ten wpisik pokazał wam że... można. Można obejść się bez instalowania natywnie Ruby, PHP, Pythona, .NET'a, MSSQL'a, MySql'a, Mongo i kto wie czego tam jeszcze, gdy tylko potrzebujemy z tego skorzystać. 

Z wielką ochotą pomoże nam w tym wszystkim nasz kochany wielorybek :wink: .

W późniejszym czasie dopiszę krótki tutorialik jak z tego ładnie korzystać.

3maj-cie się ciepło.

k.