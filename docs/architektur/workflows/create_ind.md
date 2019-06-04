---
layout: default
title: Erstelle Indikator
parent: Workflows
grand_parent: Architektur
---

# Erstelle Indikator

- [**Beschreibung**](#des)

Dieser _Workflow_ hat die Aufgabe alle Indikator spezifischen Funktionalitäten bereitzustellen. Beispielsweise sind für einen einzelnen Indikator unterschiedliche Zeitschnitte oder Funktionen möglich, diese werden hiermit geprüft und bereitgestellt. Um die Komplexität zu minimieren, wurden die aufgerufenen Funktionalitäten auf dem Backend nicht in die Beschreibung einbezogen. Diese können jedoch über den Punkt [**Backend**]({{site.baseurl}}/docs/backend/) nachgelesen werden. 

Wird über die [**Urlparamter**]({{site.baseurl}}/docs/frontend/url_paramter) oder das Indiatorauswahlmenü ein Indikator definiert, führt die Anwendung den folgend abgebildeten _Workflow_ aus. War der Prozess erfolgreich wird der _Workflow_ [**_Add Indikator to Map_**]({{site.baseurl}}/docs/architektur/workflows/add_to_map.html) ausgeführt.

<iframe src="{{site.baseurl}}/assets/html/create_ind.html" frameborder="0" allowfullscreen onload="this.width=screen.width*0.5;this.height=screen.height;"></iframe>

## Beschreibung {#des}
1. Im ersten Schritt wird geschaut ob bereits ein Indikator in der URL übergeben wurde oder altenativ eine Auswahl über das Auswahlmenü erfolgte.
2. Da jeder Indikator seine eigene Farbgebung besitzt, wird ein durch den Nutzer definiertes [**_Farbschema_**]({{site.baseurl}}/docs/frontend/menu/farbschema.html) zurückgesetzt.
3. Aufbauend wird die [**Legende**]({{site.baseurl}}/docs/frontend/map/legende.html) erzeugt, welche ihre Informationen immer  für den gewählten Indikator anzeigt. Die notwendigen Informationen 
4. Da jeder Indikator unterschiedliche Zeitschnitte besitzt, muss für jeden Indikator geprüft werden ob dieser für den Zeitschnitt bereitgestellt werden kann. Dies übernimmt die _init()_ Funktion des [**_zeitslider_**]({{site.baseurl}}/docs/frontend/slider/zeitslider.html). Ist der Indikator für den gewünschten Zeitschnitt nicht verfügbar, wird über den [**_alertmanager_**]({{site.baseurl}}/docs/frontend/alert_manager) eine entsprechende Meldung ausgegeben.
5. Im nächsten Schritt wird die Räumliche Analyseebene initiiert und vom Objekt [**raeumliche_visualisierung**]({{site.baseurl}}/docs/frontend/menu/raeumliche_analyseebene) über die Funktion _getRaeumlicheGliederung()_ abgefragt ob sich die Karte in der _Gebietsansicht_ oder _Rasteransicht_ befindet.
    1. **Rasteransicht**
        1. Über das Objekt [**_rasterweite_slider_**]({{site.baseurl}}/docs/frontend/slider/rasterweite_slider.html) wird geprüft ob der Indikator in der gewählten Auflösung zur Verfügung gestellt werden kann. Wenn nicht wird der Paramter **Rasterweite** auf 0 gesetzt, was der Weite von 100m entspricht, da alle Indikatoren in dieser Rasterweite verfügbar sind.
        2. 
    2. **Gebietsansicht**