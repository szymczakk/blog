---
layout: post
title: Strefy czasowe... Elon nie leć na Marsa, nie ogarniemy tego
summary: 
published: true
tags: .net c# timezones hint 
categories: posts 
--- 

### Hej!

Ostatnio w pracy musiałem integrowac się z zewnętrznym API które w jednym z zapytań przesyłało mi daty...<br>
Dwa dni walczyłem z rozwiązaniem problemu z tym związanego...
<br>
<!--more-->
<br>
**STACK**: .NET Core na backendzie, API RESTowe do danych i vanilaJS na forncie<br>
**PROBLEM**: Parsowanie dat do nieodpowiedniego formatu oraz błędnej strefy czasowej.
<br>
<br>
Z API dostaję datę w formacie "rok-mieciąc-dzień" czyli np "2020-02-02" oznaczające drugi luty 2020. Czyli w formacie żadnym.
<br>
Na backendzie wykonywalem sobie proste
```
DateTime.Parse()
```
które formatowało mi tę datę "poprawnie" a mianowicie ustawiało mi ją jako 
```
02.02.2020 00:00:00 UTC+1 
```
<br>
Jednak największy problem się zaczął gdy tę datę musiałem wysłać do kalendarza na frontend. Okazało się że defaultowo parsowanie dat do JSON'a nie generuje ich w formacie ISO8601 bo nie wysyła informacji o strefie czasowej. 
<br>
Rozwiązaniem okazuje się na backendzie wszystkie te daty zrobić 
```.ToUniversalTime()```
oraz 
```.ToString("o")```
co sprawi że taka data wygeneruje się w poprawnym formacie ISO8601.
<br><br>
Ale w tym momencie pojawia się całkiem inny problem.
<br>
Data ``` 02.02.2020 00:00:00 UTC+1``` po zrobieniu ```.ToUniversalTime()``` stanie się datą ``` 01.02.2020 23:00:00 UTC``` czyli cofnie się o dzień.
<br><br>
Długo szukałem rozwiązania tego problemu (bo danych z API nie mogłem dostać w innym formacie) po czym okazało się że ```DateTime.Parse()``` ma opcję przyjęcia enuma typu ```DateTimeStyles``` ktory zawiera w sobie między innymi wartość ```64``` czyli ```DateTimeStyles.AssumeUniversal```
<br><br>
Dzięki temu podzas parsowania daty wartość
```2020-02-02```
nie ustawia się jako **UTC+1** (czyli nasza lokalna strefa) a jako **UTC**. Dzięki temu wykonanie na tym 
```.ToUinversalTime().ToString("o")``` odda poprawna datę.
<br><br>
Elonie, prosze.... Nie leć na Marsa... Strefy czasowe na jednej planecie są już bardzo upierdliwe a co dopiero międzyplanetarna ich wersja :smile:
<br><br>
k.