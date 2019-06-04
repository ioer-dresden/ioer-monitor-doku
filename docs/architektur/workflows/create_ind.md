---
layout: default
title: Erstelle Indikator
parent: Workflows
grand_parent: Architektur
---

# Erstelle Indikator

- [**Beschreibung**](#des)

Dieser _Workflow_ hat die Aufgabe alle Indikator-spezifischen Funktionalitäten bereitzustellen und die Karte auf Basis des gesetzten Indikators letztendlich zu visualisieren. Beispielsweise sind für einen einzelnen Indikator unterschiedliche Zeitschnitte oder Funktionen möglich, diese werden hiermit geprüft und bereitgestellt. Um die Komplexität zu minimieren, wurden die aufgerufenen Funktionalitäten auf dem Backend nicht in die Beschreibung einbezogen. Diese können jedoch über den Punkt [**Backend**]({{site.baseurl}}/docs/backend/) nachgelesen werden. 

____

Wird über die [**Urlparamter**]({{site.baseurl}}/docs/frontend/url_paramter) oder das Indiatorauswahlmenü ein Indikator definiert, führt die Anwendung den folgend abgebildeten _Workflow_ aus. War der Prozess erfolgreich wird der _Workflow_ [**_Add Indikator to Map_**]({{site.baseurl}}/docs/architektur/workflows/add_to_map.html) ausgeführt. 

<iframe src="{{site.baseurl}}/assets/html/create_ind.html" frameborder="0" allowfullscreen onload="this.width=screen.width*0.5;this.height=screen.height;"></iframe>

## Beschreibung {#des}
der Komplette Workflow wird über das Objekt [**indikatorauswahl**]({{site.baseurl}}/docs/frontend/menu/indikatorauswahl.html) mit der Funktion _setIndicator(ID des Indikator)_ aufgerufen. 

1. Im ersten Schritt wird geschaut ob bereits ein Indikator in der URL übergeben wurde oder altenativ eine Auswahl über das Auswahlmenü erfolgte.
2. Da jeder Indikator seine eigene Farbgebung besitzt, wird ein durch den Nutzer definiertes [**_Farbschema_**]({{site.baseurl}}/docs/frontend/menu/farbschema.html) zurückgesetzt.
3. Aufbauend wird die [**Legende**]({{site.baseurl}}/docs/frontend/map/legende.html) erzeugt, welche ihre Informationen immer  für den gewählten Indikator anzeigt. Die notwendigen Informationen 
4. Da jeder Indikator unterschiedliche Zeitschnitte besitzt, muss für jeden Indikator geprüft werden ob dieser für den Zeitschnitt bereitgestellt werden kann. Dies übernimmt die _init()_ Funktion des [**_zeitslider_**]({{site.baseurl}}/docs/frontend/slider/zeitslider.html). Ist der Indikator für den gewünschten Zeitschnitt nicht verfügbar, wird über den [**_alertmanager_**]({{site.baseurl}}/docs/frontend/alert_manager) eine entsprechende Meldung ausgegeben.
5. Im nächsten Schritt wird die Räumliche Analyseebene initiiert und vom Objekt [**raeumliche_visualisierung**]({{site.baseurl}}/docs/frontend/menu/raeumliche_visualisierung) über die Funktion _getRaeumlicheGliederung()_ abgefragt ob sich die Karte in der _Gebietsansicht_ oder _Rasteransicht_ befindet.
Folgend werden die Zweige näher erläutert, welche je nach Auswahl genommen werden:
    1. **Rasteransicht**
        1. Über das Objekt [**_rasterweite_slider_**]({{site.baseurl}}/docs/frontend/slider/rasterweite_slider.html) wird geprüft ob der Indikator in der gewählten Auflösung zur Verfügung gestellt werden kann. Wenn nicht wird der Paramter **Rasterweite** auf 0 gesetzt, was der Weite von 100m entspricht, da alle Indikatoren in dieser Rasterweite verfügbar sind.
        2. Über das Objekt [**_indikator_raster_**]({{site.baseurl}}/docs/frontend/map/indikator_raster.html) wird die Funktion _init()_ aufgerufen, welche den **Mapserver** anweist eine neue Indikatorkarte zu generieren und diese der Karte hinzufügt.
    2. **Gebietsansicht**
        1. Da jeder Indikator unterschiedliche Räumliche Auswahlmöglichkeiten besitzt, muss für jeden Indikator dieses Menü neu gesetzt werden. Dies wird über die Funktion _fill()_ des Objektes [**raeumliche_analyseebene**]({{site.baseurl}}/docs/frontend/menu/raeumliche_analyseebene) ermöglicht. 
        2. Anschließend wird bei einem gesetzen Indikator geprüft, ob dieser innerhalb der Auswahl für die Räumliche Analyseebene zur Verfügung steht, falls nicht wird eine entsprechende Meldung über den [**_alertmanager_**]({{site.baseurl}}/docs/frontend/alert_manager) ausgegeben. Wenn ja wird der URL-Parameter über die MEthode _updateURLParamter()_ des Objektes [**urlparamter**]({{site.baseurl}}/docs/frontend/url_paramter) neu gesetzt.
        3. Jetzt wird die zweite Raumebene geprüft, ob der Nutzer eine eigene Gebietskulisse erstellt hat, deren AGS in der URL abgelegt sind. Ist dies nicht der Fall kann die Karte auf der Basis der **Räumlichen Analyseebene** ([**raeumliche_analyseebene**]({{site.baseurl}}/docs/frontend/menu/raeumliche_analyseebene)) erstellt werden. Wenn **ja**, wird über die Bibliothek [**Semantic-UI**](https://semantic-ui.com/modules/dropdown.html){:target="blank"} der Erstellungsvorgang getriggert.
        4. Hat der Nutzer die Gebietskulisse nochmals fein gegliedert, wird das Objekt [**raumgliederung**]({{site.baseurl}}/docs/frontend/menu/raumgliederung) aufgerufen und hier die Methode _init()_, welche prüft ob der Indikator gesetzt werden kann und im letzten Schritt über das Object [**indikator_json**]({{site.baseurl}}/docs/frontend/map/indikator_json.html) die Indikatorkarte hinzufügt.