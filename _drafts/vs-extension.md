---
layout: post
title: Mój pierwszy (i pewnie jedyny) dodatek do VS Code
tags: vs-code project
categories: jekyll projekty
---

#### Hej!

Dzisiaj podjąłem ważną decyzję. Jak mam pisać posty w Jekyll'u i używać [jemoji](https://github.com/jekyll/jemoji) to musze mieć jakieś rozszerzenie podpowiadające mi te cholerne emotki.
<!--more-->
No nie mogę ciągle jechać na tym [cheat sheat'cie](http://www.webpagefx.com/tools/emoji-cheat-sheet/)... No nie mogę... Dwa monitory to za mało :unamused: ... No bo jak to zrobić, na jednym projekt/kod/coś o czym piszę, na drugim VS Code z postem i co chwila ALT+TAB bo tu emotka, tam emotka. No nie, tak być nie może. 

Odpaliłem sobie szukajkę extenszonuf do VS Code a tam pustka, nie ma nic na ten temat.
No to myślę sobie, napiszę swój!

Więc bierzmy się do pracy!

[Lecę na tym tutorialu](https://code.visualstudio.com/docs/extensions), a to co tutaj opiszę to taki najważniejszy skrót.

### Krok pierwszy
Po wyguglaniu ocb z tymi extenszonami zassałem sobie Yo-man'a, `generator-code` i wyklikałem, że będę to pisał w `TypeScript'cie`. Zobaczymy co z tego dalej wyjdzie.

### Krok drugim
Dobra, po przebrnięciu [pierwszego tutorialu](https://code.visualstudio.com/docs/extensions/example-hello-world), dowiedziałem się tyle, że muszę exportować funkcję `activate` a jeśli używam czegoś co wymaga, :wink: _w stronę .NET'a_, czegoś co implementuje `IDisposable` to należy też wyexportować funckję `deactivate`. To są najważniejsze rzeczy, które trzeba po nim wiedzieć.

