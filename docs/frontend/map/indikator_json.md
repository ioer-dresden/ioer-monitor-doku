---
layout: default
title: Indikator JSON
parent: Kartenansicht
grand_parent: Frontend
---
# Indikator JSON
Dieses **Objekt** stellt alle wichtigen Funktionen bereit, mit welchen die vom [**Backend**]({{site.baseurl}}/docs/backend) empfangenen _GeoJSON_ visualisiert werden können. Über **_indikator_json_** wird das Objekt aufgerufen.
## Variablen

| Name | Type | Default | Info |
|------|----------|------|-----|
| **json_layer** | Object | false | Ist das [**Leaflet-GeoJSON**](https://leafletjs.com/reference-1.4.0.html#geojson){:target="_blank"}-Objekt welches generiert wird.|
| **json_file** | Object | false | Ist das vom Server als Response übermittelte JSON, als Objekt |
| **ags_count** | Int | false | Gibt die Anzahl der visualisierten [**AGS**]() an, also wie viele Gebiete in der Karte visualisiert wurden |

## Funktionen

|  Funktion |  Paramter | Return | Info |
|:-------------|:-----------|:-----------|
| **getJSONLayer** | | Object:json_layer| gibt den Parameter **_json_layer_** zurück |
| **getJSONFile** | | Object:json_file| gibt den Paramter **_json_file_** zurück |
| **init** |String:raumgl, Callback:callback | | holt die GeoJSON vom [**Backend**]({{site.baseurl}}/docs/backend) über die Methode _getGeoJSON_ des [**RequestManagers**]({{site.baseurl}}/docs/frontend/request_manager). Während des Ladevorganges wird die [**Progressbar**]({{site.baseurl}}/docs/frontend/view/progressbar.html) eingeblendet. |
//TODO