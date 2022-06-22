---
title: Pressingzonen Bundesliga Saison 2021/2022
author: Marcel Gehrke
date: '2022-06-22'
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

Die erfolgreichsten Bundesliga Teams der Saison 2021/2022 - Bayern München und Borussia Dortmund - stechen wieder durch Angriffspressing hervor. In Kombination mit hochwertigen Kadern führt dies zu den meisten erzielten Toren und - zumindest im Fall des FC Bayern - zu wenigen Gegentoren.

Aber auch Teams mit weniger teuren Kadern wie Hoffenheim und der 1. FC Köln pressen relativ hoch. Im Falle der Kölner geht dies mit wenigen Gegentoren einher.

Neben Leipzig presst Leverkusen auffällig selten im Angriffsdrittel, vor allem in Relation zu anderen Teams mit hohen Marktwerten.







# Eine Sommerpause macht noch keine Fussballpause...

Während der Ball im Profifussball ruht, lässt sich die gewonnene Zeit ideal nutzen um zum einem den Amateurplätzen des Landes Besuche abzustatten und dabei eine Wurst vom Holzkohlegrill zu genießen und zum anderen um einen schnellen Blick auf die Daten der vergangenen Saison zu werfen.

Die folgenden Plots untersuchen **alle** Pressingaktionen der Bundesliga-Saison 2021/2022 (in Summe 96.688) mit Blick auf das Spielfelddrittel in dem sie stattfanden.

Im Mittel startete ein Team in dieser Saison 5372 Pressingaktionen. Über 44% davon fanden im Mittelfeld statt. Ein Wert der innerhalb der Liga kaum streut. Beim Defensiv- und Angriffspressing sieht es hingegen anders aus. So weisen gerade die Topteams hohe Anteile im Angriffspressing und geringe Anteilen im Defensivpressing auf.

Dass diese Pressingkonstellation zwangsläufig zu Erfolg, bzw. die gegenteilige Variante zu Misserfolg führt ist jedoch keinesfalls gesagt. Dies zeigen die Beispiele Hertha BSC und Leverkusen. Trotz einer ähnlichen Verteilung der Pressingaktionen über das Feld ist das Ergebnis ein gänzlich anderes.


|Team             | Def.-Pressing.| Off.-Pressing| Tore| Gegentore| Position|
|:----------------|--------------:|-------------:|----:|---------:|--------:|
|Bayer Leverkusen |            35%|           21%|   80|        47|        3|
|Hertha BSC       |            37%|           19%|   37|        71|       16|

# Pressingzonen

Der Plot zeigt für jedes Team ob der **Anteil der Pressingaktionen** im jeweiligen Spielfelddrittel über oder unter dem Mittelwert der Liga liegt. Die Teams sind dabei entsprechend des Tabellenplatzes angeordnet.

Das heißt Hertha BSC Berlin startet, relativ gesehen, überdurchschnittlich viele Pressingaktionen im eigenen Defensivdrittel und einen unterdurchschnittlichen Anteil der Pressingaktionen in den anderen beiden Spielfelddritteln.

<img src="{{< blogdown/postref >}}index_files/figure-html/plot-anteil-1.png" width="672" style="display: block; margin: auto;" />

Analog zum obigen Plot bezieht sich dieser auf die absoluten Werte.

Der VfL Bochum startete beispielsweise in allen Dritteln des Spielfeldes überdurchschnittlich viele Pressingaktionen. In der absoluten Betrachtung deuten diese Zahlen natürlich auch auf relativ hohe/niedrige Ballbesitzanteile hin.

<img src="{{< blogdown/postref >}}index_files/figure-html/plot-total-1.png" width="672" style="display: block; margin: auto;" />

Beide Plots unterstreichen erwartungsgemäß, dass die Teams aus dem oberen Tabellendrittel zumeist offensiver pressen als jene aus dem unteren Tabellendrittel. Auffallend sind jedoch Teams die seltener offensiv pressen als erwartet, beispielsweise Leverkusen und Leipzig, aber auch Teams die häufiger als erwartet Angriffspressing nutzen, wie der 1. FC Köln oder auch der VfL Bochum.

# Fokus Angriffspressing

Angriffspressing erfährt in den letzten Jahren viel Aufmerksamkeit. Hierzulande sicherlich auch aufgrund Jürgen Klopps Vorliebe für diesen Spielstil. Seine Motivation dafür ist simpel:

> "Alles, was du den Gegner unter Druck machen lässt, macht es für ihn bedeutend schwieriger." <footer>--- Jürgen Klopp</footer>

Zeitgleich birgt Angriffspressing aber auch einige Risiken. Führt es nicht zum Erfolg, bietet es dem gegnerischen Team die Chance einen vielversprechenden Konter zu fahren, unter anderem dadurch, dass in der Regel mit relativ wenigen Passspielen viele gegnerische Spieler [gepackt](https://de.wikipedia.org/wiki/Packing_(Fußball)) werden können.

## Angriffsspressing und Kaderwerte

Um erfolgreiches Angriffspressing zu betreiben bedarf es also zum einem einer Strategie im Falle des Scheiterns, aber auch Spieler die technisch und auch körperlich in der Lage sind diese laufintensive spielweise kollektiv umzusetzen.

Aus diesem Grund lohnt ein Blick auf die Kaderwerte als Indikator für die Qualität einer Mannschaft. Der Plot zeigt den durchschnittlichen Marktwert der Top-20 Spieler der Bundesligisten in Relation zum Anteil der Pressingaktionen im Angriffsdrittel. 

Die Beschränkung auf die Top-20 soll einen Spieltagskader abbilden und ein verwässern durch Spieler aus dem erweiterten Kader verhindern. 

Auffällig ist, dass die beiden Top-Teams der Bundesliga auch das meiste Angriffspressing betreiben, zeitgleich aber auch, dass Leverkusen wenig, Hoffenheim und der 1. FC Köln jedoch anteilig recht viel Angriffspressing betreiben. 

Die horizontalen und vertikalen orangenen Linien zeigen in diesem und den folgenden Plots die jeweiligen Mittelwerte an. 

<img src="{{< blogdown/postref >}}index_files/figure-html/att_pressing_vs_value-1.png" width="672" style="display: block; margin: auto;" />

## Tore & Gegentore

Wie übersetzt sich die Nutzung von Angriffspressing nun in Tore und Gegentore?

Zunächst ein Blick auf die Gegentore. Schließlich ist Pressing per se eine Defensivaktion, die - unabhängig von etwaigen Kontern und Ballbesitzphasen die eingeleitet werden können - den Gegner vom Torerfolg abhält.

Dabei zeigt sich, dass Teams die zu Angriffspressing neigen weniger Gegentore bekommen. So bekommen lediglich Leverkusen und Union Berlin trotz unterdurchschnittlichem Angriffspressing auch unterdurchschnittliche wenig Gegentore. Während nur Hoffenheim trotz relativ viel Angriffspressing überdurchschnittliche viele Gegentore bekommt.

Selbstredend interagiert dies, wie gezeigt, mit der Qualität des Kaders, spannend ist jedoch auch hier wieder der 1. FC Köln, der trotz eines geringen Kaderwertes und hohen Anteilen Angriffspressings wenig Gegentore bekommt.

<img src="{{< blogdown/postref >}}index_files/figure-html/att_pressing_vs_goalsagainst-1.png" width="672" style="display: block; margin: auto;" />

Positiv ist die Beziehung zwischen Angriffspressing und erzielten Toren. Jedoch zeigt sich mit den Blick auf den eigenen Torerfolg ein deutlich stärkeres Gefälle zwischen den vier Teams mit den höchsten Marktwerten und dem Rest. Dies zeigen vor allem Leipzig und Leverkusen, welche trotz niedriger Anteile des Angriffspressings überdurchschnittlich viele Tore erzielt haben.

<img src="{{< blogdown/postref >}}index_files/figure-html/att_pressing_vs_goalsfor-1.png" width="672" style="display: block; margin: auto;" />

# Code

Der Code der genutzt wurde um die Daten aufzubereiten und darzustellen findet sich [hier](https://github.com/MarcelGehrke/bundesliga_pressing).
