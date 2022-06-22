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







# Einleitung

Eine Sommerpause macht noch keine Fussballpause...

Während der Ball im Profifußball ruht, lässt sich die gewonnene Zeit ideal nutzen um zum einem den Amateurplätzen des Landes Besuche abzustatten und zum anderen einen schnellen Blick auf die Daten der vergangenen Saison zu werfen.

Die folgenden Plots untersuchen **alle** Pressingaktionen der Bundesliga-Saison 2021/2022 (in Summe 96.688) mit Blick auf das Spielfelddrittel in dem sie stattfanden.

Im Mittel startete ein Team in dieser Saison 5372 Pressingaktionen. Über 44% davon fanden im Mittelfeld statt. Ein Wert der innerhalb der Liga kaum streut. Beim Defensiv- und Angriffspressing sieht es hingegen anders aus. So stechen gerade die Topteams mit hohen Anteilen im Angriffspressing und geringen Anteilen im Defensivpressing heraus.

Dass diese Pressingkonstellation zwangsläufig zu Erfolg, bzw. die gegenteilige Variante zu Misserfolg führt ist jedoch keinesfalls gesagt. Dies zeigen die Beispiele Hertha BSC und Leverkusen. Trotz einer ähnlichen Verteilung der Pressingaktionen über das Feld ist das Ergebnis ein gänzlich anderes.


|Team             | Defensivpressing| Offensivpressing| Tore| Gegentore| Position|
|:----------------|----------------:|----------------:|----:|---------:|--------:|
|Bayer Leverkusen |              35%|              21%|   80|        47|        3|
|Hertha BSC       |              37%|              19%|   37|        71|       16|

# Pressingzonen

Der Plot zeigt für jedes Team ob der **Anteil der Pressingaktionen** im jeweiligen Spielfelddrittel über oder unter dem Mittelwert der Liga liegt. Die Teams sind dabei entsprechend des Tabellenplatzes angeordnet.

Das heißt Hertha BSC Berlin startet, relativ gesehen, überdurchschnittlich viele Pressingaktionen im eigenen Defensivdrittel und einen unterdurchschnittlichen Anteil der Pressingaktionen in den anderen beiden Spielfelddritteln.

<img src="{{< blogdown/postref >}}index_files/figure-html/plot-anteil-1.png" width="672" style="display: block; margin: auto;" />

Analog zum obigen Plot bezieht sich dieser auf die absoluten Werte.

Der VfL Bochum startete beispielsweise in allen Dritteln des Spielfeldes überdurchschnittlich viele Pressingaktionen. In der absoluten Betrachtung deuten diese Zahlen natürlich auch auf relativ hohe/niedrige Ballbesitzanteile hin.



<center>
!(index_files/figure-html/plot-total-1.png)
</center>

# Fokus Angriffspressing

Angriffspressing erfährt in den letzten Jahren viel Aufmerksamkeit. Hierzulande mit Sicherheit auch aufgrund Jürgen Klopps Vorliebe für diesen Spielstil. Seine Motivation dafür ist simpel:

> "Alles, was du den Gegner unter Druck machen lässt, macht es für ihn bedeutend schwieriger." <footer>--- Jürgen Klopp</footer>

Zeitgleich birgt Angriffspressing aber auch einige Risiken. Führt es nicht zum Erfolg bietet es dem gegnerischen Team die Chance einen vielversprechenden Konter zu fahren, unter anderem dadurch, dass in der Regel mit relativ wenigen Passspielen viele gegnerische Spieler [gepackt](https://de.wikipedia.org/wiki/Packing_(Fußball)) werden können.

## Angrifsspressing und Kaderwerte

Um erfolgreiches Angriffspressing zu betreiben bedarf es also zum einem einer Strategie im Falle eines gescheiterten Versuchs, aber auch Spieler die technisch und auch körperlich in der Lage sind diese laufintensive spielweise kollektiv umzusetzen.

Aus diesem Grund lohnt ein Blick auf die Kaderwerte als Indikator für die Qualität einer Mannschaft. Der Plot zeigt den durchschnittlichen Marktwert der Top-20 Spieler der Bundesligisten in Relation zum Anteil der Pressingaktionen im Angriffsdrittel. 

Die Beschränkung auf die Top-20 soll einen Spieltagskader abbilden und ein verwässern durch Spieler aus dem erweiterten Kader verhindern. 

Auffällig ist, dass die beiden Top-Teams der Bundesliga auch das meiste Angriffspressing betreiben, zeitglich aber auch, dass Leverkusen wenig, Hoffenheim und der 1. FC Köln jedoch anteilig recht viel Angriffspressing betreiben. 

Die horizontalen und vertikalen orangenen Linien zeigen in diesem und den folgenden Plots die jeweiligen Mittelwerte an. 



<center>

!(index_files/figure-html/att_pressing_vs_value-1.png)

</center>

## Tore & Gegentore

Wie übersetzt sich die Nutzung von Angriffspressing nun in Tore und Gegentore?

Zunächst ein Blick auf die Gegentore. Schließlich ist Pressing per se eine Defensivaktion, die - unabhängig von etwaigen Kontern und Ballbesitzphasen die eingeleitet werden können - den Gegner vom Torerfolg abhält.

Dabei zeigt sich, dass Teams die zu Angriffspressing neigen weniger Gegentore bekommen. Selbstredend interagiert dies, wie gezeigt, mit der Qualität des Kaders, spannend ist jedoch auch hier wieder der 1. FC Köln, der trotz eines geringen Kaderwertes und hohen Anteilen Angriffspressings wenig Gegentore bekommt.



<center>

!(index_files/figure-html/att_pressing_vs_goalsagainst-1.png)

</center>

Positiv ist die Beziehung zwischen Angriffspressing und erzielten Toren. Jedoch zeigt sich mit den Blick auf den eigenen Torerfolg ein deutlich stärkeres Gefälle zwischen den Teams mit einem hohen Marktwert und dem Rest. Dies zeigen vor allem Leipzig und Leverkusen, welche trotz niedriger Anteile des Angriffspressings überdurchschnittlich viele Tore erzielt haben.



<center>

!(index_files/figure-html/att_pressing_vs_goalsfor-1.png)

</center>

# Code & Session Info

Der Code der genutzt wurde um die Daten aufzubereiten und darzustellen findet sich [hier](https://github.com/MarcelGehrke/bundesliga_pressing)


```
## R version 4.2.0 Patched (2022-06-09 r82473)
## Platform: aarch64-apple-darwin20 (64-bit)
## Running under: macOS Monterey 12.4
## 
## Matrix products: default
## BLAS:   /Library/Frameworks/R.framework/Versions/4.2-arm64/Resources/lib/libRblas.0.dylib
## LAPACK: /Library/Frameworks/R.framework/Versions/4.2-arm64/Resources/lib/libRlapack.dylib
## 
## locale:
## [1] en_US.UTF-8/en_US.UTF-8/en_US.UTF-8/C/en_US.UTF-8/en_US.UTF-8
## 
## attached base packages:
## [1] stats     graphics  grDevices utils     datasets  methods   base     
## 
## other attached packages:
##  [1] ggimage_0.3.1        polite_0.1.1         rvest_1.0.2         
##  [4] janitor_2.1.0        cowplot_1.1.1        glue_1.6.1          
##  [7] RColorBrewer_1.1-3   ggtext_0.1.1         ggsoccer_0.1.6      
## [10] magrittr_2.0.2       forcats_0.5.1        stringr_1.4.0       
## [13] dplyr_1.0.9          purrr_0.3.4          readr_2.1.2         
## [16] tidyr_1.2.0          tibble_3.1.6         ggplot2_3.3.6       
## [19] tidyverse_1.3.1      worldfootballR_0.5.6
## 
## loaded via a namespace (and not attached):
##  [1] nlme_3.1-157       fs_1.5.2           usethis_2.1.5      lubridate_1.8.0   
##  [5] httr_1.4.2         rprojroot_2.0.2    tools_4.2.0        backports_1.4.1   
##  [9] bslib_0.3.1        utf8_1.2.2         R6_2.5.1           mgcv_1.8-40       
## [13] DBI_1.1.3          colorspace_2.0-3   robotstxt_0.7.13   withr_2.4.3       
## [17] tidyselect_1.1.2   curl_4.3.2         compiler_4.2.0     cli_3.3.0         
## [21] xml2_1.3.3         labeling_0.4.2     bookdown_0.27      sass_0.4.1        
## [25] scales_1.2.0       digest_0.6.29      yulab.utils_0.0.4  rmarkdown_2.14    
## [29] pkgconfig_2.0.3    htmltools_0.5.2    dbplyr_2.2.0       fastmap_1.1.0     
## [33] highr_0.9          htmlwidgets_1.5.4  rlang_1.0.2        readxl_1.4.0      
## [37] rstudioapi_0.13    farver_2.1.0       gridGraphics_0.5-1 jquerylib_0.1.4   
## [41] generics_0.1.2     jsonlite_1.7.3     ggplotify_0.1.0    Matrix_1.4-1      
## [45] Rcpp_1.0.8         munsell_0.5.0      fansi_1.0.2        lifecycle_1.0.1   
## [49] stringi_1.7.6      yaml_2.2.2         snakecase_0.11.0   grid_4.2.0        
## [53] crayon_1.4.2       lattice_0.20-45    splines_4.2.0      haven_2.5.0       
## [57] gridtext_0.1.4     hms_1.1.1          magick_2.7.3       knitr_1.39        
## [61] pillar_1.7.0       ratelimitr_0.4.1   markdown_1.1       reprex_2.0.1      
## [65] evaluate_0.15      blogdown_1.10      ggfun_0.0.6        modelr_0.1.8      
## [69] vctrs_0.4.1        tzdb_0.3.0         cellranger_1.1.0   gtable_0.3.0      
## [73] assertthat_0.2.1   cachem_1.0.6       xfun_0.31          formattable_0.2.1 
## [77] tufte_0.12         broom_0.8.0        memoise_2.0.1      ellipsis_0.3.2    
## [81] here_1.0.1
```

