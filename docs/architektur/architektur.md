---
layout: default
title: Architektur
nav_order: 2
permalink: /docs/architektur
has_children: true
has_toc: false
---
## Inhalt
- [Architektur](#architektur)
- [Programmiersprachen](#programmlanguage)

## Architektur {#architektur}

Bei dem IÖR-Monitor handelt es sich um eine klassische _Client-Server_ Architekt, mit den dazu gehörigen Service Layern. Im folgenden Diagramm ist die Kommunikation innerhalb des Backend grob zusammengefasst. Durch fehlende administrative Rechte und auch aus Zeitmangel während des Entwicklungs- bzw. Konzeptionsvorgangs musste die bereits teilweise ungünstige Konzeption fortgeführt werden. Um die Kommunikation so abstrakt wie möglich zu gestalten wurde ein [**Request Manager**]({{site.baseurl}}/docs/frontend/request_manager) im [**Frontend**]({{site.baseurl}}/docs/frontend/) implementiert.
<iframe src="{{site.baseurl}}/assets/html/architektur.html" frameborder="0" allowfullscreen onload="this.width=screen.width*0.5;this.height=screen.height*0.4;"></iframe>
Um die Rasterkarten dem Clienten zur Verfügung zu stellen, wird ein [**MapServer**](https://mapserver.org/) verwendet. Da [**MapScript**](https://mapserver.org/sq/mapscript/index.html) zum Zeitpunkt der Implementierung kein _PHP 7_ unterstützt, welches auf dem **monitor.ioer.de - Server** installiert, wurde der **maps.ioer.de -Server** mit _PHP 5_ eingesetzt. Dieser erstellt die angeforderten Karten-Grafiken und sendet diese in Form eines [**WMS**](https://mapserver.org/sq/ogc/wms_server.html) über den Apache-Webserver zurück. Die Geometrien, welche für die Generierung von Gebietseinheiten innerhalb der Vektoransicht benötigt werden, liegen in einer [**PostgreSQL7**](https://www.postgresql.org/)-Datenbank. In dieser Datenbank werden auch die Geometrien der Zusatzlayer gespeichert, welche in der Raster- und Vektoransicht als zusätzliche Layer geladen werden können. Die Indikatoren und deren Werte sind in einer [**MySQL8**](https://www.mysql.com/de/)-Datenbank gespeichert. Für jedes Jahr, liegt eine entsprechende Tabelle vor, in welcher alle verfügbaren Indikatoren und deren Werteausprägungen vorhanden sind. Auch die Freigabe, Farbliche Gestaltung, zusätzliche Inhalte, Fehlercodes und Hinweistexte der Indikatoren sind in entsprechenden Tabellen abgelegt.

## Eingesetzte Programmiersprachen {#programmlanguage}
<iframe src="{{site.baseurl}}/assets/html/chartVerteilung.html" frameborder="0" allowfullscreen onload="this.width=screen.width*0.5;this.height=screen.height*0.4;"></iframe>
[**PHP**](https://www.php.net/manual/de/intro-whatis.php){:target="_blank"} in der Version **7** ist dei dominierende serverseitige Programmiersprache, auf dem Clienten ist es [**JavaScript**](https://developer.mozilla.org/de/docs/Web/JavaScript) mit der Erweierung [**Typescript**](https://www.typescriptlang.org/). [**Python**](https://www.python.org/) wurde nur verwendet um mit der Hilfe des [**Flask**](http://flask.pocoo.org/) Microservice clientenseitig-Mails zu versenden, direkt über den _IÖR_-Mailserver.