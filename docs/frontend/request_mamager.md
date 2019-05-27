---
layout: default
title: Request-Manager
has_children: false
permalink: /docs/frontend/request_manager
parent: Frontend
---
# Request-Manager

Um die Kommunikation mit dem [**Backend**]({{site.baseurl}}/docs/backend/) so unkompliziert wie möglich zu gestalten, wurde nach dem [**Command Pattern**](https://en.wikipedia.org/wiki/Command_pattern) diese Klasse implementiert.
Hierbei kommuniziert er mit dem **PHP**- und **Flask**-Backend, da jedes andere Aufgaben hat um dem Clienten die gewünschten Informationen bereitzustellen.

### Funktionen

![UML]({{site.baseurl}}/assets/images/request_manager.png)

Nachfolgend werden die _static_ Functions vorgestellt, welche mit dem _query.php_ Endpoint kommunizieren und damit im Backend auf PHP basieren. Die KOmmunikation mit dem **PHP**-Backend erfolgt dabei via _HTTP_-**POST**. Alle Funktionen sind dabei  _static_. 

| Funktion | Paramter | Return Value | Beschreibung |
|----------|----------|--------------|--------------|
| **getGeoJSON** | - ID des Indikators - Jahr - Raumgliederung - gewünschte AGS als **Array** - Anzahl der KLassen - Klassifizierung | [JSON-Object]({{site.baseurl}}/assets/data/getGeoJSON.json){:target="_blank"}{: .btn}| Diese Methode holt die GeoJSON vom Backend, welche anhand der übergebenen Parameter auf dem Server generiert wird (PHP Klasse-[**JSON**]({{site.baseurl}}/docs/backend/map/json.html)|
| **getAvabilityIndicator** | - ID des Indikators | Object | Die Funktion prüft ob der gewählte Indikator in der gewählten räumlichen Gliederung (Raster/Gebiete) verfügbar ist.|
|**getAllAvaliableIndicators** | | [Object]({{site.baseurl}}/assets/data/allAvaliableIndicators.json){:target="_blank"}{: .btn}| Diese Funktionen holt alle verfügbaren Indikatoren vom Backend für die gewählte Raumgliederung |
|**getJahre**| ID des Indikators | [Array]({{site.baseurl}}/assets/data/getYears.txt){:target="_blank"}{: .btn} | Methode welche alle verfügbaren Jahre für einen Indikator vom Backend holt |
|**getRaumgliederung** | ID des Indikators | Object | Diese Funktion holt vom Backend alle verfügbaren Raumgliederungen für den angegebenen Indikator |
| **getCountGeometries** | ID der Raumgliederung | Object {Number} | Mit dieser Methode wird ermittelt, wie viele Geometrien auf dem Clienten gerendert werden sollen, z.B. um dies in der Progressbar anzuzeigen |
| **getZusatzlayer** | Id des Layers`s | GeoJSON | Diese Funktion holt alle _**Zusatzlayer**_ (z.B. Gemeindegrenzen, Gewässer ) vom Backend. |
| **getTableExpandValues** | Array mit den Expand ID's, Array mit den gesetzten AGS | [Object]({{site.baseurl}}/assets/data/tableExpand.json){:target="_blank"}{: .btn}| Diese Funktion holt alle notwendigen Informationen vom Server, um die **Tabelle zu erweitern** ja nachdem welche ID's im Array gespeichert sind |
| **getTrendValues** | ID des Indikators, AGS, Setting-Object z.B. ```{"forecast":"false", "all_points" :"true", "compare" : "false"}``` [Request]({{site.baseurl}}/assets/data/getTrendReq.json){:target="_blank"}{: .btn}| [Object]({{site.baseurl}}/assets/data/getTrendResp.json){:target="_blank"}{: .btn}| Diese Funktion holt die für die Erstellung der Entwicklungsgraphen notwendigen Daten vom Backend |
| **handleLink** |Object ```{"id":"set","val": urlparamter.getAllUrlParameter()};``` | State Object| Funktion welche für einen erstellten Maplink alle notwendigen Paramter vom Backend holt, um die Karte zu erstellen. |
| **getSpatialOverview** | ID des Indikators, AGS | [Object]({{site.baseurl}}/assets/data/getSpatialOverview.json){:target="_blank"}{: .btn}| Diese Funktion ruft für einen übergebenen Indikator und AGS. alle verfügbaren Indikatorwerte vom BAckend ab. Diese Funktion wird vor allem für das [**Gebietsprofil**]({{site.baseurl}}/docs/frontend/dialog/area_info.html) genutzt |
| **sendMailFeedback** | Name, Sender, Nachricht | | Diese Funktion sendet über das **Flask**-Microframework eine Mail und wird für die **Feedbackfunktion** genutzt |
| **sendMailError** | Name, Nachricht | | Diese Funktion sendet über das **Flask**-Microframework eine Mail an die Kerngruppe und wird bei Fehlermeldungen verwendet |

____

Die vorher aufgezählten Funktionen haben die Aufgabe Anfragen zu formulieren, die jetzt vorgestellten Funktionen senden die Anfrage an den Server. Durch diese Aufteilung wird die Komplexität verringert. Hierbei ist die Logik immer gleich:

&rarr; es wird ein JSON-Object mit der Anfrage gebildet und den nachfolgenden Funktionen übergeben. Diese stellen die Anfrage via **Ajax** an das Backend.

| Funktion | Paramter | Return Value | Beschreibung |
|----------|----------|--------------|--------------|
|**sendRequestPHP** | Object | Server success | Diese Funktion sendet alle Anfragen an das PHP-Backend und stellt das Ergebnis bereit. |
|**sendRequestFlask** | Objekt | Server success | Diese Funktion sendet alle Anfragen an das Flask Micro-Framework |
| **cancel** | | | Diese Funktion beendet die laufende **_asynchrone_**-Funktion |