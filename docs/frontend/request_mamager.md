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

Nachfolgend werden die _static_ Functions vorgestellt, welche mit dem _query.php_ Endpoint kommunizieren und damit im Backend auf PHP basieren.
| Funktion | Paramter | Return Value | Beschreibung |
|----------|----------|--------------|--------------|
| getGeoJSON | - ID des Indikators - Jahr - Raumgliederung - gewünschte AGS als **Array** - Anzahl der KLassen - Klassifizierung | Indikatorkarte als **GeoJSON** [Beispiel]({{site.baseurl}}/assets/data/getGeoJSON.json){:target="_blank"}{: .btn} | TODO|