## 4. Technologien
Da die Lambda-Architektur eine Spezifikation für den Systementwurf darstellt und keine Technologien vorschreibt, können Entwickler selbst entscheiden, welche Tools sie nutzen wollen, und gegebenenfalls auf Technologien zurückgreifen, die sie bereits kennen. Die nachfolgende Abbildung zeigt die möglichen Technologien, die sich zur Umsetzung der Lambda-Architektur eignen, sortiert nach deren Einsatz in den verschiedenen Layern.

![Technologien und Layer](./images/Tools.png)  
Abbildung 5: Technologien für die einzelnen Layer [**[SuSh16]**](7_Literaturverzeichnis.md)  

Im Folgenden wird für jeden Layer jeweils beispielhaft eine Technologie vorgestellt.

### 4.1 Batch Layer
Da der Batch Layer sehr große Datenmengen hält und diese nicht nur von einer einzelnen Maschine verarbeitet werden können, werden Technologien benötigt, welche die Berechnung auf mehrere Maschinen verteilen können. Dabei stellt Apache Hadoop das beliebteste Tool dar. [**[SuSh16]**](7_Literaturverzeichnis.md)   

![hadoop Logo](./images/hadoop-logo.png)  
Abbildung 6: hadoop-Logo [**[HaBi17]**](7_Literaturverzeichnis.md)    

Apache Hadoop ist ein Framework zur Speicherung großer Datenmengen in Computerclustern. Seine Aufgabe ist es, Aufgaben und Berechnungen zu planen, diese zu überwachen und erneut auszuführen, wenn Fehler auftreten oder die Aufgaben gar fehlschlagen. Dabei werden die Daten basierend auf dem MapReduce-Algorithmus redundant auf den einzelnen Rechnern verteilt. [**[ApHa18]**](7_Literaturverzeichnis.md)    

Der MapReduce-Algorithmus wird zur Verteilung von Berechnungen auf mehrere Rechner verwendet, sodass diese parallel ausgeführt werden können. Abbildung 7 zeigt die Phasen des MapReduce-Verfahrens.  

![MapReduce Ablauf](./images/MapReduce-Ablauf.png)  
Abbildung 7: MapReduce-Ablauf [**[HaBi17]**](7_Literaturverzeichnis.md)    
   

1. Im ersten Schritt wird die große Datenmenge in viele kleine unabhängige Blöcke aufgeteilt, welche von den Map-Tasks vollständig parallel verarbeitet werden.  
2. Im zweiten Schritt werden die vielen Zwischenergebnisse sortiert und an den Reduce-Task übergeben.
3. Sofern alle Zwischenergebnisse vorliegen, wird aus ihnen im dritten Schritt das Endergebnis berechnet und ausgegeben.

### 4.2 Speed Layer
Im Speed Layer werden die Daten im Systemspeicher selbst verarbeitet und benötigen daher entsprechende Technologien, welche zur Echtzeitverarbeitung von großen Datenmengen geeignet sind. Hierbei hat sich unter Anderem Apache Storm als geeignet erwiesen.  

![Storm Logo](./images/storm-logo.PNG)  
Abbildung 8: Storm-Logo [**[ApSt15]**](7_Literaturverzeichnis.md)   

Apache Storm ist ein Open Source Rechensystem, welches für die Echtzeitverarbeitung großer Datenmengen verwendet wird. Es eignet sich unter Anderem für Echtzeitanalysen und kontinuierliche Berechnungen, weswegen es ein gutes Tool für den Speed Layer darstellt. [**[ApSt15]**](7_Literaturverzeichnis.md)  

![Storm Ablauf](./images/storm-Ablauf.png)  
Abbildung 9: Storm-Ablauf [**[HaBi17]**](7_Literaturverzeichnis.md)       

Wie in Abbildung 9 zu sehen, ist Apache Storm dafür verantwortlich, aus den eingehenden Daten die Real Time Views zu erstellen. Dabei übernimmt es die Parallelisierung der Abfragen und die Partitionierung und wiederholt bei Fehleraufkommen die notwendigen Schritte. Die Datenbank, in welche die Real Time Views gespeichert werden, kann dabei vom Entwickler selbst bestimmt werden. [**[ApSt15]**](7_Literaturverzeichnis.md)  

### 4.3 Serving Layer
Um die zusammengeführten finalen Views zu speichern, wird eine Datenbank mit guter Performance benötigt. Dabei ist es wichtig, dass die Datensätze schnell gelesen und geschrieben werden können. Eine gute Datenbank hierfür bietet Apache HBase. [**[SuSh16]**](7_Literaturverzeichnis.md)  

![HBase Logo](./images/hbase-logo.png)  
Abbildung 10: HBase-Logo [**[ApHB19]**](7_Literaturverzeichnis.md)   

HBase ist keine relationale Datenbank, sondern ein verteiltes Speichersystem für strukturierte Daten und ähnelt einer MapReduce-Anwendung.

[☜ 3. Architektur](3_Architektur.md)
   |   [5. Vorteile ☞](5_Vorteile.md)