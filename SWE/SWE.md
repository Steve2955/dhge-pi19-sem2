# Vertiefung Programmierung/Objektorientierte Programmierung

## Unterschiede C/C++

- Namen können explizit Namespaces zugeordnet werden (vermeidung von Namenskollisionen)
	- identische Namen können in unterschiedlichen Namespaces existieren
	- Der Zugriff auf einen Namespace erfolgt über den Scope-Operator ```::``` (Alternativ: ```using namespace::name;```)
- Prototypen sind in C++ Pflicht!
- ```struct's``` sind automatisch auch ```typdef's```
- keine ```void*```-Pointer
	- ```nullptr``` sollte konsequent statt ```NULL``` verwendet werden
- Typ ```auto```: Compiler ordnet Typ automatisch zu -> muss direkt deklariert werden
- Typumwandlungen
	- C-Cast: ```((typ) wert)``` (deprecated)
	- C++ Cast: ```typ(wert)```
	- ```static_cast<typ> (wert)``` -> vgl. alter C-Cast (Bitmuster bleibt gleich, zur Compilezeit geprüft)
	- ```reinterpret_cast<typ> (wert)``` -> Cast mit minimalen Prüfungen
	- ```dynamic_cast<typ> (wert)``` -> Konvertierung zwischen verwandten Pointern, zur Laufzeit geprüft)
	- ```const_cast<typ> (wert)``` -> keine Typänderung, nur ```const``` zu Variablen hinzufügen oder entfernen
- enum-Werte sind nicht ```int``` -> Typumwandlung notwendig
- Konstanten ```const``` sind echte Konstanten -> vgl. ```#define```, aber mit Typsicherheit (nicht mehr global deklariert -> für Sichtbarkeit von außen: ```extern const```)
- ```extern "C"```: für korrekte Übersetzung der Funktionsnamen zwischen C und C++

## Erweiterungen für Funktionen

- Defaultwerte für Funktion
	- Defaultwerte können Konstanten oder Globale Variablen sein
	- Parameter mit Defaultwerten müssen am Ende des Funktionsaufrufes stehen
```C++
void drawLine(int width = 80, char c = '=') { ... }
```
- Überladen von Funktionen
	- beliebig viele Funktionen mit gleichem Namen möglich
	- eindeutige Unterscheidung durch Parameter-Typen
	- Compiler sucht passende Funktionen in zwei Durchläufen: erst mit genauen Typen, dann mit impliziten Typkonvertierungen
-  Referenzen
	- Normal: Call by value wie in C
	- Call by reference im Funktionskopf mit ```&``` statt ```*```
	- Arrays werden weiterhin immer per Pointer übergeben
```C++
bool delete(int key, double &val);
```
	- Referenzen können nie ```NULL``` sein
	- Referenzen sind immer konstante Pointer
	- keine Pointer auf Referenzen, Arrays von Referenzen oder Referenzen von Referenzen
	- Referenzen sind auch als Return-Wert möglich (nicht const, keine lokalen Variablen!)
```C++
*(func(...)) = ...;
```
	- Der Wert auf der rechten Seite der Zuweisung wird in jenes Objekt gespeichert, auf das die Referenz zeigt, die als Returnwert von der Funktion zurückkommt

## I/O und File-I/O

### Ein-/Ausgabe auf die Konsole

```C++
#include <iostream> //statt <stdio.h>
using namespace std;
// ===== Ausgabe =====
// Einfach Ausgabe von Rechnungen/Variablen/Text
cout << 2+5; cout << "Hello World";
// Ausgabe mehrerer Variablen (Typ wird automatisch erkannt; kein automatisches Leerzeichen)
cout << 21*2 << "= " << 84/2;
// Zeilenvorschub mit endl:
cout << "..." << endl;

// ===== Eingabe =====
cin >> variable;
// Der Typ der Variabe wird erkannt und die Umwandlung erfolgt automatisch
// Leerziechen und Leerzeilen werden übersprungen, es wird genau ein Wort gelesen
// Zeichenweises Lesen ebenfalls ohne Whitespace
```

### Lesen und Schreiben von Dateien

- relevante Klassen: ```ifstream``` (Lesen), ```ofstream``` (Schreiben), ```fstream``` (Beides)

```C++
#include <iostream>
using namespace std;

ifstream inFile(argv[1]);
ofstream outFile(argv[2]);

if (!inFile); // Fehlerüberprüfung

// ===== Lesen =====
inFile.get(c); // Zeichenweise Lesen
inFile >> input; // "wortweises" lesen (ohne whitspace)
// Zeileinweises Lesen (ohne newline!!!)
char zeile[81];
inFile.getline(zeile, 81);
string zeile;
getline(inFile, zeile);

// ===== Schreiben =====
outFile.put(c); // Zeichenweises Schreiben
outFile << zeile; // Zeilenweise Schreiben

// ===== Fehlerbehandlung =====
inFile.eof(); // Fileende wurde erreicht
inFile.fail(); // Konvertierungsfehler o. weiteres Lesen trotz EOF
inFile.bad(); // echter I/O-Fehler
inFile.good(); // kein Fehler

// ===== Beispiele =====

while (inFile) {}
while (inFile.getline(zeile, 81)) {}
while (inFile >> txt) {}
```

## Objektorientierte Software-Entwicklung

- Bisher (C): Ablauforientiert = Schritt für Schritt = am Code orientiert
- Jetzt (C++): Datenorientiert -> Daten statt Algorithmus im Mittelpunkt
- Aufspaltung von Code in Objekte mit Eigenschaften und Funktionalitäten
	- Neue Denkweise: Daten sind aktiv, d.h. können Operationen auf sich selbst ausführen und werden für ein bestimmtes Objekt aufgerufen (in jeder Funktion gibt es einen "ich selbst"-wert)

### Konzepte und Terminologien

**Klasse**
- vgl. ```struct```-Typ erweitert um Funktionen und einiges mehr
- enthält keine Werte oder Daten, sondern dien als Schablone für diese

**Objekt**
- Instanz einer Klasse

**Methode**
- Einer Klasse zugehörige Funktion

**Member-Variable**
- Einer Klasse zugehöriges Datenelement (Primitives oder andere Objekte)
