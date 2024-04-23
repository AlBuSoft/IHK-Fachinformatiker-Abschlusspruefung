# Zustandsdiagramm
- [Pseudoustände](#pseudozustände)
    - [Startzustand](#startzustand)
    - [Endzustand](#endzustand)
    - [Terminator](#terminator)
    - [Kreuzung](#kreuzung)
    - [Entscheidung](#entscheidung)
- [Verschachtelung](#verschachtelung)
    - [Flache Historie](#flache-historie)
    - [Tiefe Historie](#tiefe-historie)
- [Zustandsregionen](#zustandsregionen)
    - [Gabelung](#gabelung)
    - [Verinigung](#vereinigung)
- [Beispieldiagramme](#beispieldiagramme)

## Pseudozustände

### **Startzustand**
Jedes Zustandsdiagramm weist einen **Startzustand**. Er besitzt keine eingehenden Transitionen und nur genau eine ausgehende Transition, die angibt, in welchem Zustand begonnen wird. Der Startzustand selbst kann nicht eingenommen werden. Neu erzeugte Objekte befinden sich immer in dem auf den Startzustand folgenden Zustand.

![alt](Zustandsdiagramm_Startzustand.svg)

### **Endzustand**
Besitzt keine ausgehenden Transitionen. Das Objekt bzw. die Ebene hat den Endzustand erreicht (Objekt kann ewig im Endzustand existieren).

![alt](Zustandsdiagramm_Endzustand.svg)

### **Terminator**
Beendet sofort die Ausführung der gesamten Zustandsmaschine, um abrupte Abbrüche zu erzwingen, z. B. im Falle eines Fehlers.

![alt](Zustandsdiagramm_Terminator.svg)

### **Kreuzung**
Werden verwendet, um mehrere Transitionen zu verbinden. Der Kontrollfluss wird nicht aufgeteilt.

![alt](Zustandsdiagramm_Kreuzung.svg)

### **Entscheidung**
Knoten, von dem mehrere alternative Transitionen ausgehen können. Pfad hängt von Bedingungen an ausgehenden Kanten ab.

![alt](Zustandsdiagramm_Entscheidung.svg)

## Verschachtelung
Zustände können durch Verschachtelung miteinander kombiniert werden. Dadurch enstehen Unter- und Oberzustände. Die UML2 kennt folgende Pseudo-Zustände, die bei Verschachtelung von Bedeutung sind.

### **Flache Historie**
Der flache Historiezustand speichert den Zustand einer Ebene. Beim Verlassen des Unterzustands wird der aktuelle Kontrollfluss gesichert. Beim Betreten wird der Zustand wieder hergestellt.

![alt](Zustandsdiagramm_FlacheHistorie.svg)

### **Tiefe Historie**
Im tiefen Historiezustand werden alle Zustände über die gesamte Schachtelungstiefe hinweg gespeichert.

![alt](Zustandsdiagramm_TiefeHistorie.svg)

## Zustandsregionen
Regionen enthalten Zustände und Zustandsübergänge und werden durch gestrichelte Linien zu Trennung der Bereiche dargestellt. Sie definieren nebenläufige Bereiche innerhalb eines Zustands. Beim Eintritt werden die nebenläufigen Regionen beide aktiv. Beim Verlassen werden die Kontrollflüsse wieder zusammengeführt. Die UML2 kennt folgende Pseudo-Zustände, die bei Zustandsregionen von Bedeutung sind.

![Zustandsdiagramm Regionen](zustandsdiagramm_regionen.png)

### **Gabelung**
Aufspaltung des Kontrollflusses in mehrere parallelen Zustände. Ausgehende Kanten tragen keine Ereignisse oder Bedingungen.

![alt](Zustandsdiagramm_Gabelung.svg)

### **Vereinigung**
Vereinigung des Kontrollflusses von mehreren parallelen Zuständen. Eingehende Kanten tragen keine Ereignisse oder Bedingungen.

![alt](Zustandsdiagramm_Vereinigung.svg)

## Beispieldiagramme
![Beispieldiagramm 1](zustandsdiagramm_beispiel1.png)
![Beispieldiagramm 2](zustandsdiagramm_beispiel2.png)
![Beispieldiagramm 3](zustandsdiagramm_beispiel3.png)
![Beispieldiagramm 4](zustandsdiagramm_beispiel4.png)
![Beispieldiagramm 5](zustandsdiagramm_beispiel5.png)

&uarr; [Zurück nach oben](#top)


