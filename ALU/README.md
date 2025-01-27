# Aufbau und Funktionsweise einer Minecraft-ALU

![ALU Konstruktion](bilder/alu.png)

Eine **Arithmetic Logic Unit (ALU)** ist ein zentraler Bestandteil von CPUs, die arithmetische und logische Operationen durchführt. In Minecraft habe ich eine 8-Bit ALU nachgebaut, die mehrere grundlegende Operationen unterstützt, darunter Addition, Subtraktion, Inkrementierung, Dekrementierung und Logikoperationen. Hier erkläre ich den Aufbau, die Funktionsweise und stelle die Logik hinter den Komponenten vor – unterstützt durch die Bilder meiner Konstruktion.

---

## **1. Überblick über die ALU**

![ALU Übersicht](bilder/Pasted image 20250127195824.png)

Die ALU in Minecraft setzt sich aus mehreren logischen und arithmetischen Modulen zusammen. 

Die Logik hinter der ALU:  
![ALU Design](bilder/alu-design.png)  

Das gesamte ALU-Layout als Schaltplan im Überblick:  
![ALU Layout](bilder/fulldesign-layout.png)  

---

## **2. Komponenten der ALU**

Schauen wir uns jetzt die einzelnen Komponenten genauer an. Fangen wir mit dem 8-Bit Adder an.

### **2.1 Der 8-Bit Adder**
Der **Adder** ist eines der zentralen Elemente der ALU. Er addiert zwei 8-Bit-Zahlen und gibt das Ergebnis sowie ein Übertragsbit (Carry-Out) aus.  

Minecraft-Nachbau des Adders:  
![8-Bit Adder](bilder/8-bit-adder.png)  

Die schematische Darstellung zeigt, wie die Module miteinander verbunden sind:  
![8-Bit Adder Schema](bilder/8-bit-adder-scem.png)  

Die Logik des Adders in einem vereinfachten Schaltplan:  
![8-Bit Adder Design](bilder/8-bit-adder-design.png)  

Ein 8-Bit Adder besteht aus 8 Full Addern. Ein einzelner Full Adder sieht wie folgt aus:

#### 2.1.1 Der Full Adder als einzelne Komponente

Ein einzelner Full Adder ist im folgendem Diagramm, mithilfe von Logikgattern, dargestellt:  
![Full Adder Design](bilder/full-adder-design.png)

In Minecraft sieht es folgendermaßen aus:  

![Full Adder Schema](bilder/full-adder-scem.png)  
![Full Adder](bilder/full-adder.png)

---

### **2.2 Der 8-Bit Subtractor**
Der **Subtractor** ist dafür verantwortlich, eine 8-Bit-Zahl von einer anderen zu subtrahieren. Er arbeitet ähnlich wie der Adder, verwendet jedoch ein Borrow-Bit statt eines Carry-Outs.  

Minecraft-Nachbau des Subtractors:  
![8-Bit Subtractor](bilder/8-bit-subtractor.png)  

Eine Darstellung der Logik des Subtractors:  
![8-Bit Subtractor Design](bilder/8-bit-subtractor-design.png)  

Die schematische Übersicht der Verbindungen:  
![8-Bit Subtractor Schema](bilder/8-bit-subtractor-scem.png)  

Ein 8-Bit Subtractor besteht aus 8 Full Subtrators. Ein einzelner Full Subtractor sieht wie folgt aus:

#### 2.2.1 Der Full Subtractor als einzelne Komponente

![Full Subtractor Design](bilder/full-subtractor-design.png)

Er besteht, wie auch der Full Adder, aus zwei AND-Gates, zwei XOR-Gates und einem OR-Gate. Jedoch kommen hier noch zwei NOT-Gates hinzu.  
In Minecraft sieht es folgendermaßen aus:  

![Full Subtractor Schema](bilder/full-subtractor-scem.png)  
![Full Subtractor](bilder/full-subtractor.png)

---

### **2.3 Der 8-Bit Incrementer und Decrementer**
Der **Incrementer** erhöht den Wert einer 8-Bit-Zahl um 1, während der **Decrementer** ihn um 1 verringert.  

- **Incrementer**  
  Physischer Aufbau:  
  ![8-Bit Incrementer](bilder/8-bit-incrementer.png)  
  Schema:  
  ![8-Bit Incrementer Schema](bilder/8-bit-incrementer-scem.png)  

- **Decrementer**  
  Physischer Aufbau:  
  ![8-Bit Decrementer](bilder/8-bit-decrementer.png)  
  Schema:  
  ![8-Bit Decrementer Schema](bilder/8-bit-decrementer-scem.png)  

Der Incrementer und Decrementer verwenden sieben Half Adder bzw. Half Subtractor und ein NOT-Gate.

#### 2.3.1 Half Adder und Half Subtractor

Der Aufbau für den Half Adder ist folgender:  
![Half Adder Design](bilder/half-adder-design.png)

In Minecraft umgesetzt sieht es folgendermaßen aus:  
![Half Adder Schema](bilder/half-adder-scem.png)  
![Half Adder](bilder/half-adder.png)

Der Half Subtractor hat zusätzlich ein NOT-Gate:  
![Half Subtractor Design](bilder/Pasted image 20250127202403.png)

In Minecraft umgesetzt sieht es folgendermaßen aus:  
![Half Subtractor Schema](bilder/half-subtractor-scem.png)  
![Half Subtractor](bilder/half-subtractor.png)

---

## **3. Logikbausteine der ALU**

### **3.1 Der 2-Bit Decoder**
Der **Decoder** wandelt eine 2-Bit-Eingabe in eine spezifische Ausgabe um, die nur einen einzigen Ausgang aktiviert.  

Minecraft-Nachbau des Decoders:  
![2-Bit Decoder](bilder/2-bit-decoder.png)  

Schematische Darstellung:  
![Binary Decoder Design](bilder/binary-decoder-design 1.png)

---

### **3.2 Logikgatter**
Logikgatter bilden die Grundlage jeder ALU. Sie werden verwendet, um AND-, OR-, NOT- und XOR-Operationen durchzuführen.  

Die wichtigsten Logikgatter als Schaltplan:  
![Logikgatter Schema](bilder/gates.png)

---

## **5. Gesamtübersicht**

Abschließend gibt es hier eine schematische Deckblatt-Ansicht der gesamten ALU:  
![Deckblatt Design](bilder/full-design-cover.png)

Zusätzlich wurde die Eingabe eines 2-Bit-Opcodes umgesetzt, mit dem bestimmt wird, welche Recheneinheit aktiv ist:  

- Erstes Bit:  
  ![Operator Links](bilder/op-left.png)  
- Zweites Bit:  
  ![Operator Rechts](bilder/op-right.png)  

Die AND-Gates, die die Einheiten aktivieren:  
![Operator Gates](bilder/op-gates.png)  
Schema dazu:  
![Operator Gates Schema](bilder/op-gates-scem.png)

