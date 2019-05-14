---
layout: default
title: Statistik
parent: Dialog
grand_parent: Frontend
---
# Statistik

### Beschreibung
Dieses Modul Visualisiert die Statistischen Kennzahlen von ausgewählten Regionen.

![Image]({{site.baseurl}}/assets/images/statistik_werte.png "Alle Werte")

![Image]({{site.baseurl}}/assets/images/statistik_dichte.png "Wahrscheinlichkeitsdichte")

![Image]({{site.baseurl}}/assets/images/statistik_verteilung.png "Kumulative Verteilung")


#### Variablen
| Name | Type | Default | Info |
|------|----------|------|-----|
| **endpoint_id** | String | "area_info_content" | Identifikator für diesen Dialogfenster |
| **selector_toolbar** | String | "#ind_stat" | Identifikator von Toolbar-ikone |

| **text** | Object{Object} | Object{Object} | Sprachen- lokalisierung. Jedes untergeordnetes Objekt beinhaltet die Übersetzungen in die jeweilige Sprache  |

## Funktionen

| Funktion |  Parameter | Return | Beschreibung |
|-------------| -----------| -----------|-----------|
| **init** |  | void |  |
| **open** |  | void |  |
| **populateChartSettingsWithValues** |  | void |  |
| **getAllValues** | geoJSON | void |  |
| **getCurrentValue** | geoJSON, ags | void |  |
| **getAreaCount** | geoJSON | void |  |
| **parseStringPointToComma** |  | void |  |
| **calculateStatistics** |  | void |  |
| **calculateAverage** |  | void |  |
| **calculateMedian** |  | void |  |
| **calculateStDeviation** |  | void |  |
| **getDecimalSpaces** |  | void |  |
| **roundNumber** |  | void |  |
| **sortObjectAscending** |  | void |  |
| **getOnlyValues** |  | void |  |
| **getDistributionFunctionValues** |  | void |  |
| **getDeviationValues** |  | void |  |
| **getDensityFunctionIntervalValues** |  | void |  |
| **findSelectedAreaInInterval* |  | void |  |


## Objekte

 ###Chart

 Dieses **Objekt** beinhaltet die wichtigsten Variablen und steuert die graphische Darstellung der Daten
 
 ####Varriablen
 
| Name | Type | Default | Info |
|------|----------|------|-----|
 | **Name** | String | false | Die Name von gewähltem Region |
 | **ags** | String | false | Der amtlischer Gemeindeschlüssel von gewähltem Region |
 | **data** | array | false | Alle Indikator-relevanten Werte: aus *RequestManager.getSpatialOverview(indikatorauswahl.getSelectedIndikator(),ags)* |
 | **lan** | String | false | Sprachwahl des Nutzers |
 | **ind** | String | false | Indikator-id |
 | **indText** | String | false | Indikator-name |
 | **indUnit** | String | false | Indikator- Einheit |
 | **decimalSpaces** | Number | 0 | Anzahl der Nulstellen für den indikator |
 | **allValuesJSON** | JSON Object | false | Vom Backend erhaltenes JSON Objekt mit Indikatorwert für alle Regionen |
 | **currentValue** | Number | false | Der Indikator-wert für den ausgewählten Region |
 | **allValuesObjectArray** | Object[] | false | Die vom Backend erhaltene Indikatoreninformationen ans Object Array |
 | **densityIntervalCount** | Number | 25 | Die Anzahl von Intervalen für die Visualisierung von Wahrscheinlichkeitsdichte |
 | **areaCount** | Number | false | Gesamt-anzahl von Gebieten |
 | **selectedChart** | String | "valueChart" | Name/Bezeichnung der ausgewählten Visualisierung |
 | **statistics** | Object | false | Beinhaltet die statistischen Werte (min/max, median, Mittelwert, Standartabweichung) |
 
 ####Funktionen
 
 | Funktion |  Parameter | Return | Beschreibung |
 |-------------| -----------| -----------|-----------|
  **init** |  | void |  |
  
  ####Objekte
  
  #####Controller
  
  DiesesObjekt 