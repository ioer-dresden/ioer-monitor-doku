---
layout: default
title: On Start
parent: Workflows
grand_parent: Architektur
---

# On Start
Dieses Kapitel beschreibt den _Workflow_, innerhalb des erstmaligen Aufrufes der Anwendung vom Browser. Dabei wird der hier dokumentierte _Workflow_ von der Klasse [**App**]({{site.baseurl}}/docs/frontend/app) in der Methode _main_ ausgeführt.  

<iframe src="{{site.baseurl}}/assets/html/on_start.html" frameborder="0" allowfullscreen onload="this.width=screen.width;this.height=screen.height;"></iframe>

## Beschreibung
Wie der Name schon sagt, besteht die Hauptaufgabe in der Bereitstellung aller primären Funktionalitäten und der Bindung ans **_DOM_**. Dies sind vor allem die Auswahlemüs innerhalb der [Toolbar]({{site.baseurl}}/docs/frontend/menu/toolbar.html). Hierbei werden die möglichen Inhalte vom Backend abgefragt und die Menüs befüllt. 