---
layout: default
title: Gebietsprofil
parent: Dialog
grand_parent: Frontend
---

# Gebietsprofil

### Beschreibung
Dieses Modul zeigt alle verfügbaren Indiikatorenwerte von ausgewähltem Region in einer tabellarischen Form.  
Zum Vergleich werden auch die Werte von Übergeordneten Regionen dargestellt.
Alle Dverfügbaren Daten von einem Region können heruntergeladen werden.

![Image]({{site.baseurl}}/assets/images/area_info.png )


## Variablen

| Name | Type | Default | Info |
|------|----------|------|-----|
| **endpoint_id** | String | "area_info_content" | Identifikator für diesen Dialogfenster |
| **ags** | String | false | Der amtlischer Gemeindeschlüssel von gewähltem Region |
| **name** | String | false | Die Name von gewähltem Region |
| **spatialunit** | String | false | Raumgliederung des gewählten Gebietes |
| **parentSpatialUnits** | String[] | false | Namen der übergeordneten Raumgliederungsgebieten |
| **data** | array | false | Alle Indikator-relevanten Werte: aus *RequestManager.getSpatialOverview(indikatorauswahl.getSelectedIndikator(),ags)* |
| **lan** | String | false | Sprachwahl des Nutzers |
| **time** | number | 0 | Zeitschnittwahl des Nutzers |
| **relevance** | String | false | Grundaktualität |
| **columnList** | String[] |  | Die Spaltennamen für die Tabellenspalten |
| **text** | Object{Object} | Object{Object} | Sprachen- lokalisierung. Jedes untergeordnetes Objekt beinhaltet die Übersetzungen in die jeweilige Sprache  |

## Funktionen

| Funktion |  Parameter | Return | Beschreibung |
|-------------| -----------| -----------|-----------|
| **open** | ags (String) , gen (String) | void | Die 'main' Funktion vom Modul. Aufgerufen von indikator_json.setPopUp(). Ruft die notwendigen Daten vom Backend auf. Eingabeparameter: AGS = amtlischer Gemeindeschlüssel; gen= Name vom Gebiet |
| **init** |  | void | Setzt den onClick Verhalten von .csv-download Ikone, ruft den Export_Helper.exportTable() auf |
| **getAllParameters** | ags, gen | Object | Setzt alle für das Modul notwendigen Parametern (außer die JSON Indikator-Daten von Backend) |
| **getColumnList** | spatialUnit (String) | String[] | Bestimmt welche Spalten und in welcher Reihenfolge die Tabelle beinhalten soll. Spalten entfernen, neue zufügen oder Reihefolge ändern hier! |
| **extractRelevantDataFromJSON** | data (JSON Object), lan (String) | Object[] | Bereitet den vom Backend erhaltenen JSON auf. Die relevanten Werte für jeden Indikator werden in einem Objekt geschrieben. Ein Array von diesen Indikator-Objekten bildet die Grundlage für den tabellarischen Darstellung  |
| **selectColumnsForTable** | data (Object[]), columnList (String[]) | String[][] | Selektiert die für Tabelle notwendigen Spalten aus Gesamtdaten |
| **getColumnDefsForDataTables** | columnList (String[]) | Object[] | Gibt die für DataTables benötigte Spaltenformatierung zurück. Spaltenformattierung hier anpassen! |
| **writeHTML** | parameters (Object), text (Object{Object}) | HTML Element(s) | Setzt die HTML Elemente für das Dialogfenster |
| **getTAbleHeaderHTML** | parameters (Object), text (Object{Object}) | HTML Element(s) | Formatiert die Table Headers, auf columnList basierend |
| **createDialogWindow** | parameters(Object), text (Object{Object}), html (HTML Element(s)) | void | Initialisiert den Dialogfenster |
| **drawTable** | parameters(Object) | void | Zeichnet die Table. Nutzt die [DataTables](https://datatables.net/) Library ) |
| **getDataTablesLanguage** | lan (String) | Object | Liefert ein Sprach-objekt für die Lokalisierung von [DataTables](https://datatables.net/) User-Interface  |
| **roundNumber** | indicatorId (String), number (Number) | Float | Rundet einen Indikatorwert. Rundung erfolgt auf basis von vom Backend erhaltenen Dezimalstellen-Regeln  |
