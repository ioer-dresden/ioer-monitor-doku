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
| **getGeoJSON** | - ID des Indikators - Jahr - Raumgliederung - gewünschte AGS als **Array** - Anzahl der KLassen - Klassifizierung | JSON-Object [Beispiel]({{site.baseurl}}/assets/data/getGeoJSON.json){:target="_blank"}{: .btn}| Diese Methode holt die GeoJSON vom Backend, welche anhand der übergebenen Parameter auf dem Server generiert wird (PHP Klasse-[**JSON**]({{site.baseurl}}/docs/backend/map/json.html)|
| **getAvabilityIndicator** | - ID des Indikators | Object | Die Funktion prüft ob der gewählte Indikator in der gewählten räumlichen Gliederung (Raster/Gebiete) verfügbar ist.|
|**getAllAvaliableIndicators** | | Object [Beispiel]({{site.baseurl}}/assets/data/allAvaliableIndicators.json){:target="_blank"}{: .btn}| Diese Funktionen holt alle verfügbaren Indikatoren vom Backend für die gewählte Raumgliederung |
|**getJahre**| ID des Indikators | Array [Beispiel (S12RG)]({{site.baseurl}}/assets/data/getYears.txt){:target="_blank"}{: .btn} | Methode welche alle verfügbaren Jahre für einen Indikator vom Backend holt |  