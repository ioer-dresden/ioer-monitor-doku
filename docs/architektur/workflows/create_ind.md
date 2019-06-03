---
layout: default
title: Erstelle Indikator
parent: Workflows
grand_parent: Architektur
---

# Erstelle Indikator

- [**Beschreibung**](#des)

Wird über die [**Urlparamter**]({{site.baseurl}}/docs/frontend/url_paramter) oder das Indiatorauswahlmenü ein Indikator definiert, führt die Anwendung den folgend abgebildeten _Workflow_ aus. War der Prozess erfolgreich wird der _Workflow_ [**_Add Indikator to map_**]({{site.baseurl}}/docs/architektur/workflows/add_to_map.html) ausgeführt.

<iframe src="{{site.baseurl}}/assets/html/create_ind.html" frameborder="0" allowfullscreen onload="this.width=screen.width*0.5;this.height=screen.height;"></iframe>

## Beschreibung {#des}
1. Im ersten Schritt wird geschaut ob bereits ein Indikator in der URL übergeben wurde oder altenativ eine Auswahl über das Auswahlmenü erfolgte.
2. Da jeder Indikator seine eigene Farbgebung besitzt, wird ein durch den Nutzer definiertes [**_Farbschema_**]({{site.baseurl}}/docs/frontend/menu/farbschema.html) zurückgesetzt.
3. Aufbauend wird die [**Legende**]({{site.baseurl}}/docs/frontend/map/legende.html) erzeugt, welche immer für den gewählten Indikator erzeugt wird.
//TODO