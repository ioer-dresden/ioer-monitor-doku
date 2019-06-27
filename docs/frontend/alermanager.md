---
layout: default
title: Alert-Manager
has_children: false
permalink: /docs/frontend/alert_manager
parent: Frontend
---

# Alert Manager

![alert]({{site.baseurl}}/assets/images/alert.png)

Der Alert-Manager bündelt alle Hinweise,Warnungen und Fehler innerhalb der Anwendung. Das Objekt wird über _alert_manager_ aufgerufen und befindet sich in der gleichnamigen .js.
Nachfolgend sind seine Funktionen dokumentiert.

[Code](https://github.com/ioer-dresden/ioer-monitor/blob/master/frontend/src/alert_manager.js){:target="blank"}{: .btn .btn-green }

## Funktionen

|  Funktion |  Parameter | Beschreibung |
|-------------| -----------|-----------|
|**leaveESCInfo**| void | weißt den Nutzer darauf hin, das er die Funktion via _ESC_ verlassen kann. |
|**alertUpdate**| String:version | weißt den Nutzer darauf hin das die Anwendung auf den Stand _version_ aktualisiert wurde. |
|**alertNoIndicatorChosen**| void |  weißt den Nutzer darauf hin, das er für die Funktionalität erst einen Indikator wählen muss. |
|**alertError**| String:error | weißt den Nutzer darauf hin das ein Fehler aufgetreten ist. Wurde ein Fehler mitgeliefert wird dieser auch angezeigt |
|**alertNotInTimeShift**|void| weißt den Nutzer darauf hin das der gewählte Zeitschnitt nicht für das gewählte Jahr verfügbar ist. |