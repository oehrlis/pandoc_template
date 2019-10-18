# Generelle Information

## Datenbank Versionen

Mit dem neuen Release Zyklus hat Oracle eine neue Bezeichnung für die Critical Patch Updates eingeführt. Die Critical Patch Updates für Oracle 12.2.0.1 heissen Release-Updates, abgekürzt RU. Dementsprechend wurden unsere Tests angepasst. Bei Oracle 12c werden neu die Patch Set Updates respektive Release Updates, wo verfügbar, getestet. Aktuell gibt es nur Patch Set Updates für 12.1.0.2, respektive Release Updates für Oracle 12.2.0.1, 18.0.0.0 und 19.0.0.0. Für Oracle 11.2.0.4 gibt es seit Januar 2019 keinen regulären Critical Patch Update mehr. Der Premier Support endete per 1. Januar 2015. Per 31. Dezember 2018 ist auch der Extended Support Fee Waiver abgelaufen. Seit dem 1. Januar 2019 wird für diesen Release ein Extended Support Vertrag benötigt, um Patch sowie Critical Patch Update herunterladen zu können. Siehe auch My Oracle Support 742060.1 Note Release Schedule of Current Database Releases. Siehe auch in der My Oracle Support [742060.1](https://support.oracle.com/epmos/faces/DocumentDisplay?id=742060.1) *Note Release Schedule of Current Database Releases*.


Neben einem PSU respektive RU für die Datenbank, gibt es für Oracle Java VM entsprechende Patches. Mehr dazu in der My Oracle Support Note [1929745.1](https://support.oracle.com/epmos/faces/DocumentDisplay?id=1929745.1) In der Note wird darauf hingewiesen, dass die Post Install Tasks im UPGRADE Mode ausgeführt werden sollten, wenn die JavaVM installiert ist.

Neben dem PSU, Oracle Java VM PSU gibt es zusätzlich quartalweise ein proaktiver Bundle Patch. Die Bundle Patches sind ein Superset der PSU und enthalten neben den Security Fixes weiter Bugfixes. Mehr dazu in der My Oracle Support Note [1998563.1](https://support.oracle.com/epmos/faces/DocumentDisplay?id=1998563.1) und [1962125.1](https://support.oracle.com/epmos/faces/DocumentDisplay?id=1962125.1). Mit der Installation des Combo Patch, welcher den PSU, JVM PSU und BP enthält, ist das Datenbank System jeweils auf dem aktuellsten Patchlevel.

Seit November 2015 hat Oracle für die Versionsbezeichnung der neuen Bundle Patches, Patch Set Updates und Security Patches ein neues Format eingeführt. Neu wird statt der 5. Stelle das Release Datum in der Form YYMMDD angehängt:


* **YY** letzte zwei Ziffern vom Jahr
* **MM** Monat (2 Ziffern)
* **DD** Tag im Monat (2 Ziffern)

## Weblogic Server

Bis zur Weblogic Version 12.1.1 wurden die Patches jeweils mit BEA Smart Update (BSU) eingespielt. Ab Version 12.1.2 wird Smart Update durch das im Datenbankumfeld bekannte OPatch abgelöst. Ein Patchen mit BSU ist ab dieser Version nicht mehr möglich.
