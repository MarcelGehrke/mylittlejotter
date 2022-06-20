---
title: Pressingzonen Bundesliga Saison 2021/2022
author: Marcel Gehrke
date: '2022-06-20'
slug: []
categories:
  - R
  - Football
tags:
  - R
  - Football
hero: /assets/images/default-hero.webp
---

# tl;dr

Die erfolgreichsten Bundesliga Teams der Saison 2021/2022 - Bayern München und Borussia Dortmund - stechen wieder durch Angriffspressing hervor. In Kombination mit hochwertigen Kadern führt dies zu den meisten erzielten Toren und, zumindest im Fall des FC Bayern, zu wenigen Gegentoren.

Aber auch Teams mit weniger teuren Kadern wie Hoffenheim und der 1. FC Köln pressen relativ hoch. Im Falle der Kölner geht dies mit wenigen Gegentoren einher.

Neben Leipzig presst Leverkusen auffällig selten im Angriffsdrittel, vor allem in Relation zu anderen Teams mit hohen Marktwerten.


```r
knitr::opts_chunk$set(echo = FALSE, fig.align = "center")
library(worldfootballR)
library(tidyverse)
library(magrittr)
library(stringr)
library(ggsoccer)
library(ggtext)
library(RColorBrewer)
library(glue)
library(cowplot)
library(janitor)
library(rvest)
library(polite)
library(ggimage)
```





# Einleitung

Die folgenden Plots untersuchen **alle** Pressingaktionen der Bundesliga-Saison 2021/2022 hinsichtlich des Spielfelddrittels in dem sie stattfanden.

Im Mittel startete ein Team in dieser Saison 5372 Pressingaktionen. Über 44% davon finden im Mittelfeld statt. Ein Wert der auch innerhalb der Liga kaum streut. Beim Defensiv- und Angriffspressing sieht es hingegen anders aus. So stechen gerade die Topteams mit hohen Anteilen im Angriffspressing und geringen Anteilen im Defensivpressing heraus.

Dass diese Pressingkonstellation jedoch zwangsläufig zu Erfolg, bzw. die gegenteilige Variante zum Misserfolg führt ist jedoch keinesfalls gesagt. Dies zeigen die Beispiele Hertha BSC und Leverkusen. Trotz einer ähnlichen Verteilung der Pressingaktionen über das Feld ist das Ergebnis ein gänzlich anderes.


|Team             | Anteil Defensivpressing| Anteil Offensivpressing| Tore| Gegentore| Position|
|:----------------|-----------------------:|-----------------------:|----:|---------:|--------:|
|Bayer Leverkusen |                     35%|                     21%|   80|        47|        3|
|Hertha BSC       |                     37%|                     19%|   37|        71|       16|

# Pressingzonen Bundesliga Saison 2021/2022

Der Plot zeigt für jedes Team ob der **Anteil der Pressingaktionen** im jeweiligen Spielfelddrittel über oder unter dem Mittelwert der Liga liegt. Die Teams sind dabei entsprechend des Tabellenplatzes angeordnet.

D.h. Hertha BSC Berlin startet relativ gesehen überdurchschnittlich viele Pressingaktionen im eigenen Defensivdrittel und einen unterdurchschnittlich geringen Anteil der Pressingaktionen in den anderen beiden Spielfelddritteln.

<img src="{{< blogdown/postref >}}index_files/figure-html/plot-anteil-1.png" width="672" style="display: block; margin: auto;" />

Analog zum obigen Plot bezieht sich dieser auf die absoluten Werte.

D.h. der VfL Bochum startete in allen Dritteln des Spielfeldes überdurchschnittliche viele Pressingaktionen. In der absoluten Betrachtung deuten diese Zahlen natürlich auch auf relativ hohe/niedrige Ballbesitzanteile hin.

<img src="{{< blogdown/postref >}}index_files/figure-html/plot-total-1.png" width="672" style="display: block; margin: auto;" />

# Fokus Angriffspressing

Angriffspressing erfährt in den letzten Jahren viel Aufmerksamkeit. Hierzulande mit Sicherheit auch aufgrund Jürgen Klopps Vorliebe für diesen Spielstil. Seine Motivation dafür ist simpel:

> "Alles, was du den Gegner unter Druck machen lässt, macht es für ihn bedeutend schwieriger." <footer>--- Jürgen Klopp</footer>

Zeitgleich birgt Angriffspressing aber auch einige Risiken. Führt es nicht zum Erfolg bietet es dem gegnerischen Team die Chance einen vielversprechenden Konter zu fahren, u.a. dadurch, dass i.d.R. mit relativ wenigen Passspielen viele gegnerische Spieler [gepackt](https://de.wikipedia.org/wiki/Packing_(Fußball)) werden können.

## Kaderwerte

Um erfolgreiches Angriffspressing betreiben zu können bedarf es also zum einem einer Strategie im Falle eines gescheiterten Versuchs, aber auch Spieler die technisch und auch körperlich in der Lage sind diese Laufintensive spielweise kollektiv umzusetzen.

Aus diesem Grund lohnt ein Blick auf die Kaderwerte, als Indikator für die Qualität einer Mannschaft. Der Plot zeigt den durchschnittlichen Marktwert der Top-20 Spieler nach Marktwert der Kader jedes Vereins in Relation zum Anteil der Pressingaktionen im Angriffsdrittel. 

Die Beschränkung auf die Top-20 soll einen Spieltagskader abbilden und ein verwässern durch Spieler aus dem erweiterten Kader verhindern. 

Auffällig ist, dass die beiden Top-Teams der Bundesliga auch das meiste Angriffspressing betreiben, zeitglich aber auch, dass Leverkusen wenig Hoffenheim und der 1. FC Köln jedoch anteilig recht viel Angriffspressing betreiben. 

Die horizontalen und vertikalen orangenen Linien zeigen in diesem und den folgenden Plots die jeweiligen Mittelwerte an. 

<img src="{{< blogdown/postref >}}index_files/figure-html/att_pressing_vs_value-1.png" width="672" style="display: block; margin: auto;" />

## Tore & Gegentore

Wie übersetzt sich die Nutzung von Angriffsoressing nun in Tore und Gegentore?

Wir betrachten zunächst die Gegentore. Schließlich ist Pressing per se eine Defensivaktion, die - unabhängig von etwaigen Kontern und Ballbesitzphasen die eingeleitet werden können - den Gegner vom Torerfolg abhält.

Dabei zeigt sich, dass Teams die zu Angriffspressing neigen weniger Gegentore bekommen. Selbstredend interagiert dies, wie gezeigt, mit der Qualität des Kaders, spannend ist jedoch auch hier wieder der 1. FC Köln, der trotz eines geringen Kaderwertes und hohen Anteilen Angriffspressing wenig Gegentore bekommt.

<img src="{{< blogdown/postref >}}index_files/figure-html/att_pressing_vs_goalsagainst-1.png" width="672" style="display: block; margin: auto;" />

Positiv ist die Beziehung zwischen Angriffspressing und erzielten Toren. Jedoch zeigt sich mit den Blick auf den eigenen Torerfolg ein deutlich stärkeres Gefälle zwischen den Teams mit einem hohen Marktwert und dem Rest. Dies zeigen vor allem Leipzig und Leverkusen, welche trotz niedriger Anteile des Angriffspressings überdurchschnittlich viele Tore erzielt haben.

<img src="{{< blogdown/postref >}}index_files/figure-html/att_pressing_vs_goalsfor-1.png" width="672" style="display: block; margin: auto;" />


