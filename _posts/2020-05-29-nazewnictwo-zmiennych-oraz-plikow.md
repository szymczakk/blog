---
layout: post
title: Sposoby nazywania zmiennych oraz plików
summary:
published: true
tags: tech caseing
categories: posts
---

## Hej!

Dzisiaj po krótce o tym jakie są sposoby (i jak to się standardowo robi w różnych technologiach/językach) nazywania zmiennych oraz plików.
<br>
<!--more-->

### <strong>TLDR</strong>;
- camelCase
- PascalCase
- snake_case
- kebab-case

## Skąd to się wzięło

Spacje (' '). Wszystkiemu są wine spacje. Bardzo wiele programów rezerwuje sobie spacje, jako znaki specjalnie. Prowadzi to do tego, że nie jesteśmy w stanie używać spacji w kodzie/komputerze w taki sam sposób w jaki robimy to naturalnie

Na przykład: `ala ma kota` będzie w większość języków programowania niepoprawną zmienną (pomijam fakt, że jest to po polsku, a jak wiadomo, tego się nie robi kompilatorowi ani innym programistom, programuje się po angielsku).
<br><br>
~~ala ma kota = 5~~
<br><br>
Poprawną jej wersją będzie zapis ...
<br><br>

## 1) camelCase

`alaMaKota = 5`

Jest to koncepcja stosowana między innymi w języku JavaScritp. Polega na tym, że pierwsza litera pierwszego słowa w naszym 'zdaniu' jest mała, a każda następne słowo jest z wielkiej.

## 2) PascalCase

`AlaMaKota = 5`

Konceptka gdzie z wielkiej lietry pisze się każdy wyryaz. Bardzo rzadko spotykana, jeśli chodzi o zmienne, ale np w świecie .NET'a jest to konwencja stosowana w nazewnictwie klas.

## 3) snake_case

`ala_ma_kota = 5`

Sposób w którym każdy kolejny wyraz, pisany najczęściej z małej litery, oddziela się '_' podłogą/podkreślnikiem. Używany między innymi w pythonie (w przypadku małych liter) a gdzy wszystkie będą wielkie
<br>
`ALA_MA_KOTA = 5`
<br>
to między innymi w Javie do deklaracji enumów lub stałych.

## 4) kebab-case

`ala-ma-kota = 5`

Wygląda jak snake case, ale zamiast podłogi/porkreślnika stosuje się myślnik. Bardzo popularny w języku Lisp.

## a co z tymi plikami?

Nazwy plików, bardzo często odpowiadają konwencji nazw zmiennych w językach. Dla przykładu w C# gdy klasę nazwiemy

`AlaMaKota`

tak samo powinien nazywać się plik w którym znajduje się ta klasa.