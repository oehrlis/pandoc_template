# Trivadis Empfehlung

## Oracle Datenbank

Das höchste Base Ranking im Rahmen des Common Vulnerability Scoring System ([CVSS](http://www.first.org/cvss/)) im Bereich der reinen Datenbank liegt beim vorliegenden CPU bei 9.8 von 10 und betrifft die Core RDBMS Komponente in 11.2.0.4, 12.1.0.2, 12.2.0.1, 18c und 19c auf allen Betriebssystemen. Zudem kann diese Sicherheitslücke remote über das Netzwerk ausgenutzt werden.

Mit 9 Korrekturen für Sicherheitslücken beim Oracle Database Server ist dies ein etwas grösserer CPU. Die Sicherheitslücken können teilweise remote über das Netzwerk ausgenutzt werden.

Der CPU konnte auf allen unseren Testumgebungen mit kleineren Issues installiert werden. Aufgrund des sehr hohen CVSS Rating für Core RDBMS wird empfohlen das Critical Patch Update auf allen entsprechenden Systemen einzuspielen. Bei allen Systemen ist es ebenfalls sinnvoll, das Critical Patch Update einzu-spielen, speziell wenn das letzte Critical Patch Update übersprungen wurde. Die My Oracle Support Note [1929745.1](https://support.oracle.com/epmos/faces/DocumentDisplay?id=1929745.1) enthält weitere Informationen zu den speziellen Oracle Java VM Patches.

Dieser Patch **ist** einzuspielen, wenn:

* Nur der Oracle Client installiert ist.

Sicherheitslücken sind ausnutzbar, wenn folgende Optionen installiert oder benutzt werden:

 * Oracle 11.2 Core RDBMS, Java VM, Oracle Text
 * Oracle 12.1 Core RDBMS, Java VM, Oracle Text
 * Oracle 12.2 Core RDBMS, Java VM, Oracle Text, Spatial
 * Oracle 18 Core RDBMS, Java VM, Oracle Text, Spatial
 * Oracle 19 Core RDBMS, Java VM

## Oracle Fusion Middleware

Das höchste Ranking im Rahmen des Common Vulnerability Scoring System ([CVSS](http://www.first.org/cvss/)) liegt bei 9.8 von maximal 10.0 Punkten. Mit 9.8 Punkten sind Komponenten wie Oracle Security Service, Oracle SOA Suite, Oracle WebCenter Site und der Weblogic Server selbst betroffen. Alle Sicherheitslücken mit einem Score von 9 sind remote ohne Authentifizierung ausnutzbar. Weitere Details sind in der Support Note [2534806.1](https://support.oracle.com/epmos/faces/DocumentDisplay?id=2534806.1) Critical Patch Update (CPU) Program July 2019 Patch Availability Document (PAD) dokumentiert.

Da der Grossteil der Lücken ohne Authentifizierung und remote ausgenutzt werden können, wird das Einspielen des Juli 2019 Patches empfohlen.

Für den Oracle WebLogic Server werden in diesem Critical Patch Update diverse Sicherheitslücken mit einem Base Score von 9.8 und diverse mit tieferem Score behoben. Daher wird empfohlen, dieses Critical Patch Update einzuspielen.

Ab CPU Oktober 2017 empfiehlt Oracle in der Readme die Verwendung und/oder Upgrade des JDK, welches dem WebLogic Servers zugrunde liegt, je nach WebLogic Server Release auf folgende Versionen:

* Java SE Development Kit 8, Update 221 (JDK 8u221)
* Java SE Development Kit 7, Update 231 (JDK 7u231)
* Java SE Development Kit 6 ist End of Life

| CVE #          | Base Score | Affected WebLogic Server Release |
| -------------- | ---------- | -------------------------------- |
| CVE-2019-2856  | 9.8        | 12.2.1.3                         |
| CVE-2018-15756 | 7.5        | 10.3.6, 12.1.3.0,12.2.1.3        |
| CVE-2016-7103  | 6.1        | 10.3.6, 12.1.3.0, 12.2.1.3       |
| CVE-2019-2824  | 5.5        | 10.3.6, 12.1.3.0, 12.2.1.3       |
| CVE-2019-2827  | 5.5        | 10.3.6, 12.1.3.0, 12.2.1.3       |


## Oracle Enterprise Manager Base Platform

Für Oracle Enterprise Manager Cloud Control wird empfohlen auf die neuste Version von Oracle Enterprise Manager Cloud Control 13c Release 3 zu wechseln.

* Base Platform OMS home PSU [29433931](https://support.oracle.com/epmos/faces/ui/patch/PatchDetail.jspx?patchId=29433931)
* 
Die von der Enterprise Manager Base Platform benutzte Datenbank und der Applikationsserver muss wie eine normale Datenbank respektive Applikationsserver betrachtet werden. Wir empfehlen deshalb das Einspielen des CPUs.

## Oracle Audit Vault and Database Firewall

Die Patch Set Updates respektive Bundle Patches for Oracle Audit Vault and Database Firewall werden üblicherweise mit einer Verzögerung veröffentlicht. Der aktuell letzte Patch für AVDF ist [29030059](https://support.oracle.com/epmos/faces/ui/patch/PatchDetail.jspx?patchId=29030059). In der My Oracle Support Note [1328209.1](https://support.oracle.com/epmos/faces/DocumentDisplay?id=1328209.1) werden jeweils die aktuellsten Bundle Patch für AVDF 12 Release 1 und 12 Release 2 ausgewiesen.

* [New Oracle Audit Vault and Database Firewall](http://www.oradba.ch/2013/01/new-oracle-audit-vault-and-database-firewall)
* Oracle Technology Network [Oracle Audit Vault and Database Firewall](http://www.oracle.com/us/products/database/security/audit-vault-database-firewall/overview/index.html)
* Oracle Audit Vault and Database Firewall 12.1 and Database Firewall 5.x bundled patch reference [1328209.1](https://support.oracle.com/epmos/faces/DocumentDisplay?id=1328209.1)
* Oracle Technology Network [What's New in Oracle Audit Vault and Database Firewall Release 12.2](http://www.oracle.com/technetwork/database/database-technologies/audit-vault-and-database-firewall/overview/audit-vault-firewall-whatsnew-1958269.html)
