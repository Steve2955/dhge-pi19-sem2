# Informationsverarbeitung

## Grundlagen der Programmierung

### Einteilung der Programmiersprachen

- Sprachen zur Beschreibung von Daten und zur Formulierung von Verarbeitungsvorschriften
- Schnittstelle zwischen Benutzer und Maschine

| Maschinenorientierte Sprachen                                                   | Problemorientierte Sprachen                                             |
|---------------------------------------------------------------------------------|-------------------------------------------------------------------------|
| - Orientieren sich am Befehlssatz der zugrundeliegenden Hardware                | - Sprache orientiert sich an den zu lösenden Problemstellungen          |
| - Programmierung für einen spezifischen Prozessor (nicht Plattformübergreifend) | - Bsp.: imperative, funktionale, logische o. deskriptive Programmierung |
| - sehr einfache Befehle -> Komplexe Programmierung                              | - auch "höhere Programmiersprachen"                                     |
| - Assembler-Programmierung = Vereinfachung durch mnemonische Ersetzungen        | - plattformunabhängige Entwicklung durch Verwendung von Compilern       |
| - hohe Effizienz                                                                | - einfachere Programmierung                                             |

#### Problemorientierte Programmiersprachen

- zu sehr großen Teil von der zugrundeliegenden Maschine unabhängig
- definierter Kern: Wesen der Sprachen überall gleich
- eventuell maschinen-/plattformspezifische Erweiterungen
- sog. Quellprogramme werden mit Übersetzyngswerkzeugen in Maschinensprache des Rechners übersetzt

##### Imperative Programmiersprachen

- Folge von Anweisungen
- Weg der Verarbeitung im Vordergrund
- Bsp.: C, Pascal, Fortan, Cobol, Basic

##### Funktionale Programmiersprachen

- Funktionen die Eingabegrößen in Ausgabegrößen abbilden
- Funktionen bestehen aus Audrücken, die sich aus Operationen zusammen setzen
- Bsp.: Lisp

##### Deskriptive Programmiersprachen

- Ergebnis selbst im Vordergrund -> Sprache beschreibt Eigenschaften des gewünschten Ergebnis
- Programm liefert alle Eingabewerte, die diese Bedingungen erfüllen
- keine Manipulation der Eingabegrößen
- oft Abfragesprachen für Datenbanken -> Bsp.: SQL

##### Prädikative Programmiersprachen

- Beweis in einem System aus Tatsachen und Regeln im Vordergrund (= Wissensbasis)
- Benutzer formuliert Anfrage an das System, die dieses versucht mit "richtig" oder "falsch" zu beantworten
- Bsp.: Prolog

##### Objektorientierte Programmiersprachen

- Zusammenfassen der zur Lösung von Teilproblemen notwendigen Daten und Operationen zu Objekten
- Objekte kommunizieren über Signale und Botschaften miteinander
- Einige imperative Vertretter sind durch objektorientierte Programmierung erweitert wurden
- Bsp.: C++, Java, Smalltalk

#### Maschinenorientierte Programmiersprachen

- Orientierung an der vorliegenden Hardware (Befehlssatz des Zentralprozessors)
- Typische Vertretter: Assemblersprachen
**Befehl**
- kleinste, nicht weiter zerlegbare Einheit einer Programmiersprache
- bezeichnen einzelne Arbeitsschritte
- bei problemorientierten Sprachen: Anweisung (oft keine einzelnen Schritte, sondern komplexere Abläufe)
- nicht weiter zerlegbare Anweisung = elementare Answeisung
- Befehl = Operationsteil + Adressteil

##### Adressierungsarten

- unmittelbare Adressierung: Operand direkt im Adressteil des Befehls (kein Speicherzugriff nötig)
- absolute/direkte Adressierung: die im Adressteil angegebene Adresse gibt den Aufenthaltsort de Operanden an
- indirekte Adressierung: Adressteil gibt Adresse der Speicherzelle an, in der sich die Adresse des Operanden befindet
- symbolische Adressierung: Zuordnung einer Speicherzelle zu frei wählbarem Namen (wird während des Linkens durch absolute Adresse ersetzt)
- indizierte Adressierung: Summe des Adressteils und dem Wert eines Indexregisters gibt die Adresse des Operanden an
- relative Adressierung: ählich indizierte Adressierung, Basisregister statt Indexregister
- PC-relative Adressierung: Berechnung der nächsten Adresse relativ zur aktuell bearbeiteten Adresse (Sonderform der relativen Addressierung)
- virtuelle Adressierung: Ansprechen von Speicherbereichen außerhalb des Hauptspeichers (Ein-/Auslagern der Daten)

## Sprachen

### Syntax einer Sprache

#### Grundlegende Begriffe
