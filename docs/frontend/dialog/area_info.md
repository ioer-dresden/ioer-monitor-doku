---
layout: default
title: Gebietsprofil
parent: Dialog
grand_parent: Frontend
---

# Statistik


### Beschreibung
Dieses Modul zeigt alle verfügbaren Indiikatorenwerte von ausgewähltem Region in einer tabellarischen Form.  
Zum Vergleich werden auch die Werte von Übergeordneten Regionen dargestellt.
Alle Dverfügbaren Daten von einem Region können heruntergeladen werden.

![Image]({{site.baseurl}}/assets/images/area_info.png)


## Variablen
| Name | Type | Default | Info |
|------|----------|------|-----|
| **endpoint_id** | String | "area_info_content" | Identifikator für diesen Dialogfenster |
| **AGS** | String | false | Der amtlischer Gemeindeschlüssel von gewähltem Region |
| **Name** | String | false | Die Name von gewähltem Region |
| **data** | array | false | Alle Indikator-relevanten Werte: aus *RequestManager.getSpatialOverview(indikatorauswahl.getSelectedIndikator(),ags)* |
| **lan** | String | false | Sprachwahl des Nutzers |
| **time** | number | 0 | Zeitschnittwahl des Nutzers |
| **columnList** | array[String] | ["category","indicator", "value", "relevanceYear","defaultComparisonValue", "defaultDifference"] | Die Spaltennamen für die Tabellenspalten |
| **text** | Object{Object} | Object{Object} | Sprachen- lokalisierung. Jedes untergeordnetes Objekt beinhaltet die Übersetzungen in die jeweilige Sprache  |

## Funktionen

| Funktion |  Parameter | Return | Beschreibung |
|-------------| -----------| -----------|-----------|
| ** open ** | ags (String) , gen (String) | void | Die 'main' Funktion vom Modul. Aufgerufen von indikator_json.setPopUp(). Ruft die notwendigen Daten vom Backend auf. Eingabeparameter: AGS = amtlischer Gemeindeschlüssel; gen= Name vom Gebiet |
| ** getAllParameters ** | ags, gen | Object | Setzt alle für das Modul notwendigen Parametern (außer die JSON Indikator-Daten von Backend) |
| ** extractRelevantDataFromJSON ** | data (JSON Object), lan (String) | array[Object] | Bereitet den vom Backend erhaltenen JSON auf. Die relevanten Werte für jeden Indikator werden in einem Objekt geschrieben. Ein Array von diesen Indikator-Objekten bildet die Grundlage für den tabellarischen Darstellung  |
| ** selectColumnsForTable ** | data, columnList | array[][String] | TODO |
| ** initDropdown ** | Parameter | Return | Beschreibung |
| ** Name ** | Parameter | Return | Beschreibung |
| ** Name ** | Parameter | Return | Beschreibung |
| ** Name ** | Parameter | Return | Beschreibung |
| ** Name ** | Parameter | Return | Beschreibung |
| ** Name ** | Parameter | Return | Beschreibung |
