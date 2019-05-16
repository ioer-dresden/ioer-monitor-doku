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


## Variablen

| Name | Type | Default | Info |
|------|----------|------|-----|
| **endpoint_id** | String | "area_info_content" | Identifikator für diesen Dialogfenster |
| **selector_toolbar** | String | "#ind_stat" | Identifikator von Toolbar-ikone |
| **text** | Object{Object} | Object{Object} | Sprachen- lokalisierung. Jedes untergeordnetes Objekt beinhaltet die Übersetzungen in die jeweilige Sprache  |

## Funktionen

| Funktion |  Parameter | Return | Beschreibung |
|-------------| -----------| -----------|-----------|
| **init** |  | void | deaktiviert das Element für den Raster Raumgliederung |
| **open** |  | void | Schreibt alle nötigen Parametern, setzt den HTLM für das Modul und öffnet den Dialogfenster |
| **populateChartSettingsWithValues** |  | void | Holt alle nötigen Werte vom Backend und schreibt die in *Chart* Objekt |
| **getAllValues** | geoJSON | Object[] | Extrahiert die nötigen Einträge aus GeoJSON |
| **getCurrentValue** | geoJSON, ags (String)| Number | Holt den Wert für den ausgewählen Gebiet |
| **getAreaCount** | geoJSON | Number | Zahlt die Gebiete, die den jeweiligen Indikator haben |
| **parseStringPointToComma** | Number | String | Transformiert den Dezimaltrennzeichen |
| **calculateStatistics** | values (Number[]), decimal (Number) | Object | Berechnet alle Statistiken |
| **calculateAverage** | values (Number[]) | Number | Berechnet den Mittelwert |
| **calculateMedian** | values (Number[])| Number | Berechnet den Median |
| **calculateStDeviation** | values (Number[]), average (Number) | Number | Berechnet Standardabweichung |
| **getDecimalSpaces** |  | Number | Holt die Anzahl der Dezimalstellen |
| **roundNumber** | Number, decimal (Number) | Number | Runder einen Zahl |
| **sortObjectAscending** | objectArray (Object[]), key1 (String), key2 (String) | Object[] | Sortiert den Array aufsteigend |
| **getOnlyValues** | objectArray (Object[]) | Number[] | Holt nur die Numerischen Werte aus Data |
| **getDistributionFunctionValues** | sortedObjectArray | Object[] | Liefert die Werte für die Verteilungsfunktion |
| **getDeviationValues** | objectArray (Object[]), mean (Number) | Object[] | Liefert die Werte für die Abweichungen vom Mittelwert |
| **getDensityFunctionIntervalValues** | data (Object[]) ,intervalCount (Number),decimal (Number) | Object[] | Ermittelt die Intervalenparametern für die Dichtefunktion |
| **findSelectedAreaInInterval** | intervalArray (Object[]), selectedAgs (String) | Object | Sucht in allen Intervalen (die für Dichtefunktion festgelegt worden sind) nach einem bestimmten Gebiet |

## Objekte

### Chart

Dieses **Objekt** beinhaltet die wichtigsten Variablen und steuert die graphische Darstellung der Daten
 
#### Variablen
 
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
 
#### Funktionen

| Funktion |  Parameter | Return | Beschreibung |
|-------------| -----------| -----------|-----------|
**init** |  | void | setzt die Container-dimensionen für die Visualisierung, zeichnet die Visualisierung, setzt die Interaktiven Elemente |

#### Objekte

##### Controller

Dieses Objekt kontrolliert die Zeichnung von Grafiken und Menüs

###### Funktionen
  
| Funktion |  Parameter | Return | Beschreibung |
|-------------| -----------| -----------|-----------|
**setInteractiveElements** | svg (HTML element), chart_width (Number), chart_height (Number), margin (Number) | void | Setzt die Funktionalität von Dropdown Menü für die Visualisierungsauswahl |
**showVisualisation** | selection (String), svg (HTML element), chart_width (Number), chart_height (Number), margin (Number) | void | setzt die richtigen Parameter für die Visualisierungsmethoden. Visualisierungsmethodenwahl basiert auf DropDown Menü selection |
**drawOrderedValuesChart** | parameters (Object) | void | Zeichnet die Visualisierung: Werte aufsteigend als Balkendiagramm. Basiert aud 'D3' Visualisierungsbibliothek |
**drawDensityFunctionChart** | parameters (Object) | void | Zeichnet die Visualisierung: Dichtefunktion. Basiert aud 'D3' Visualisierungsbibliothek |
**drawCumulativeDistributionChart** | parameters (Object) | void | Zeichnet die Visualisierung: Kumulative Verteilung. Basiert aud 'D3' Visualisierungsbibliothek |
  