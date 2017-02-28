---
layout: post
title: Jak utworzyc RSS feed do jekyll'a.
date: 03-03-2017
published: false
tags: dsp2017 tutorial feed rss
categories: posts tutorial
---

#### Hej!

Podczas przygotowywania się do [Daj się poznać 2017](http://dajsiepoznac.pl/) musiałem podjąć [kilka ważnych decyzji.]()

Teraz przejdę do tematu który najbardziej napsuł mi krwi a okzał się najprostszym ze wszystkich :smile:. A mianowicie, CO TO JEST **RSS feed kategorii konkursowej** ??<!--more-->

Tak wiem, pewnie wyjdę na ignoratna, gbura czy innego takiego, ale nigdy w życiu z żadnego RSSa nie korzystałem. A że z "generowaniem kontentu" dopiero zaczynam, to nigdy tez nie miałem powodu by takowy posiadać. 

Poszperałem, poszukałem i okazało się że Jekyll ma takie cudo jak [jekyll-feed](https://github.com/jekyll/jekyll-feed). Ale ja, osoba nie piśmienna w Ruby, mogłem tylko sobie popatrzeć jak to generuje mi plik feed.xml w katalogu głównym strony. Na podstawie analizy tego pliku doszedłem do wniosku że ten cały _jeszcze przez chwilę_ mityczny RSS to nic innego jak prosty XML (jakby rozszerzenie na to nie wskazywało :confused: ).

No więc co trzeba zrobić, aby bez znajomości Ruby stworzyć sobie takiego własnego RSSa (ja akurat potrzebowałem do stron opisanych tagiem _nie mam pojęcia czemu nie kategorią, czegoś chyba nie ogarnąłem_ [dsp2017]({{site.url}}/dsp2017/)) ??

Bierzemy sobie takiego gotowego już feed.xml'ka jak ten

{% highlight xml linenos %}
{% raw %}
---
layout: null
---
<?xml version="1.0" encoding="UTF-8"?>
<rss version="2.0" xmlns:atom="http://www.w3.org/2005/Atom">
  <channel>
    <title>{{ site.title | xml_escape }}</title>
    <description>{{ site.description | xml_escape }}</description>
    <link>{{ site.url }}{{ site.baseurl }}/</link>
    <atom:link href="{{ "/feed.xml" | prepend: site.baseurl | prepend: site.url }}" rel="self" type="application/rss+xml" />
    {% for post in site.posts limit:10 %}
      <item>
        <title>{{ post.title | xml_escape }}</title>
        <description>{{ post.content | xml_escape }}</description>
        <pubDate>{{ post.date | date: "%a, %d %b %Y %H:%M:%S %z" }}</pubDate>
        <link>{{ post.url | prepend: site.baseurl | prepend: site.url }}</link>
        <guid isPermaLink="true">{{ post.url | prepend: site.baseurl | prepend: site.url }}</guid>
      </item>
    {% endfor %}
  </channel>
</rss>
{% endraw %}
{% endhighlight %}

i przerabiamy pod konkretne wymagania. Ja miałem dwa. Pierwszy, aby nie były to **site.posts** tylko **site.tags.dsp2017** _(im więcej razy to piszę, tym głupsze mi się to wydaje... chyba to poprawię na **categories**)_ oraz aby **title** nie był tytułem strony, tylko aby wskazywał na posty konkursowe dsp2017.

Przeróbki raczej trudne nie są, tak więc mój gotowy _już nie mityczny_ RSS wygląda tak

{% highlight xml %}
 {% raw %}
  ---
  layout: null
  permalink: /dsp2017feed/
  ---
  <?xml version="1.0" encoding="utf-8"?>
  <rss version="2.0" xmlns:atom="http://www.w3.org/2005/Atom">
    <channel>
      <title>DSP2017 Posts</title>
      <description>Posty konkursowe Daj się poznac 2017</description>
      <link>{{site.baseurl | prepend: site.url}}</link>
      {% for post in site.tags.dsp2017 %}
        {% unless post.draft %}
          <item>
            <title>{{ post.title | xml_escape }}</title>
            <description>{{ post.content | xml_escape }}</description>
            <pubDate>{{ post.date | date_to_xmlschema }}</pubDate>
            <link>{{ post.url | prepend: site.baseurl | prepend: site.url }}</link>
          </item>
        {% endunless %}
      {% endfor %}
    </channel>
  </rss>
  {% endraw %}
{% endhighlight %}

Po dodaniu mu **front matters** permalinku spełnia on wymagania konkursowe narzucone przez Maćka.

k.
