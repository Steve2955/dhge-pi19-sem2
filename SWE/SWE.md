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

## Klassen und Objekte in C++

### Deklaration einer Klasse
```C++
class Color{
	public: // Öffentliche Schnittstelle der Klasse -> Zugriff von außen (immer zuerst -> Lesbarkeit)
		// Konstruktor
     Color(int r = 0, int g = 0, int b = 0){
       mR = r; mG = g; mB = b;
     }
		 // Methode
     int getR() const { return mR; }   // ist dasselbe wie { return this->mR; }

   private:   // Kein Zugriff von klassenfremdem Code auf mR, mG, mB
     int mR, mG, mB;
}
```

### Objekte deklarieren/anlegen

- Klassenname ist zugleich Typ (vgl. ```struct``` mit ```typedef```)
- Initialisierung mit Standard-Konstruktor, Copy-Konstruktor (Kopie eines vorhandenen Objektes) oder Typumwandlungs-Konstruktor
- Zur Übergabe von Argumenten kann der Standard-Konstruktor überschrieben werden
- temporäre, anonyme Objekte: ```myFunc(myClass(x, 42), ...);```
- dynamisches anlegen mit ```new``` statt ```malloc```

### Definition des Codes von Methoden

- entweder direkt in der Klasse (nur kurze Methoden) oder danach (dann mit Klassennamen ```double myClass::myMeth(double *data, int size) { ...```)
- auch Definition von Konstruktoren außerhalb der Klasse möglich

### Konstruktoren

- Name der Klasse, kein Returntyp
- Mehrere Konstruktoren möglich (Überladen)
- Automatischer Aufruf bei:
	- Betreten des Blockes für lokale Objekt-Variablen
	- Aufruf einer Funktion mit __by value__ Objekt-Parametern
	- Start das Programmes (vor ```main()```) für statische und globale Objekte
	- Anlegen von dynamischen Objekten mit ```new```
	- Aufruf des Konstruktors eines übergeordneten Objektes (vor übergeordnetem Konstruktor)
	- explizitem Aufruf (temporäres/anonymes Objekt)
	- **Nicht** beim Anlegen eines Pointers
- Konstruktoren dienen der Initialisierung (Objekte sollten gleich mit gültigem Inhalt "geboren" werden)

### Arten von Konstruktoren

- Standard-Konstruktor: Ohne Parameter, tut nichts (nur angelegt, wenn kein expliziter Konstruktor vorhanden)
- Copy-Konstruktor: erhält const-Referenz auf das Original, legt standardmäßig eine bitweise Kopie an (kann überschrieben werden)
- Typumwandlungs-Konstruktor: Parameter eines anderen Typs (meist const, Objektparameter als const Referenz)
	- wird ein Typumwandlungs-Konstruktor als ```explicit``` deklariert, wird er nicht für implizite Typumwandlungen verwendet

### "Verhinderte" Konstruktoren

- man kann Konstruktoren als ```private``` oder ```protected``` definieren (verhindert Zugriff von außerhalb der Klasse -> z.B. für Singelton-Klassen)
- Bei ausschließlicher Deklarierung von Konstruktoren (ohne Code) wird der Aufruf verhindert (Fehler beim Linken)
	- Ab C++-11: mit ```= delete```
- Häufige Anwendung: Copy-Konstruktor verhindern (z.B. statische Klassen -> Konstantensammlung)

### Destruktoren

- Metodenname mit Tilde: ```~myClass```; kein Paramter, kein Return (nur einer pro Klasse)
- Aufruf bei:
	- Verlassen des Blockes (lokale Objekte)
	- Ende des Programmes
	- Aufruf von ```delete```
	- Destruktor des Übergeordneten Objektes
- Pointer werden nicht automatisch freigegeben!

### Initialisierungsliste


```C++
Point(const Color &color, int x, int y) : mRGB(color), mX(x), mY(y) { ... }
```
- in der Reihenfolge der Deklaration
- Werte können beliebige Ausdrücke, Konstanten, globale Variablen oder Parameter des Konstruktors sein
- Notwendig für ```const```-Member und Member, die Objekte sind (damit explizit ein Konstruktor aufgerufen werden kann) und später bei Vererbung

### this

- Zeiger auf das eigene Objekt
- Verwendung innerhalb von Methoden

### Zugriff auf Member

- bei eigenen Membern: wie normale Variablen
- In der Namenssuch-Reihenfolge zwischen lokalen und globalen Variablen
- Member fremder Objekte: ```obj.member``` oder ```obPtr->member```
- ```private``` gilt auf Klassenebene -> Objekte gleicher Klasse können gegenseitig auf ```private```-Member zugreifen

### const-Methoden

- nach den Parametern steht const: ```(...)const```
- ändert ```this```: keine Zuweisung auf Member-Variablen, ruft intern nur const-Methoden auf
- Objekte, die als const deklariert sind, dürfen nur const-Methoden beinhalten

### Übliche Methoden get... und set...

Üblicherweise Member-Variablen nicht public -> Zugriff über Getter/Setter-Funktionen

### Aufruf von Methoden

- eigenes Objekt: wie normale Funktion oder ```this->meth()```
- fremdes Objekt: ```obj.meth()``` oder ```objPrt->meth()```

### Statische Member und Methoden

- einmal pro Klasse existent: Alle Objekte der Klasse greifen auf gleichen Wert zu
- Speicher wird bei Programmstart agelegt
- Müssen in der Klasse nicht nur deklariert, sondern auch definiert werden:
```C++
static int myCounter = 1; // in der Klasse
static int myClass::myCounter = 1; // außerhalb der Klasse
```
- Wenn statische Member public sind, kann auf diese auch ohne Objekt zugegriffen werden: ```myClass::myCounter = -1;```
- in statischen Methoden ist ```this``` nicht definiert

### const-Member

- normale const-Member-Variablen: existieren ein mal pro Objekt, Initialisierung durch Initialisierungsliste
- echte Konstanten: belegen keinen Speicher (nur Primitives)
- echte konstante Klassenvariablen: einmal im Speicher angelegt, bei Programmstart initialisiert (Initialisierung muss separat von der Deklaration stehen)

### Pointer auf Methoden

- dürfen nicht auf ```void*``` konvertiert werden
- Static Methoden sind normale Funktionspointer, keine Methoden-Pointer

### Objekte als Parameter und Returnwert

- wie bei Strukturen: Übergabe __by value__ möglich, normalerweise aber stets __by reference__

### Friend

- ```friend``` teilt den Zugriff auf alle Member und Methoden der eigenen Klasse
- Häufig eingesetzt bei eigenen Ausgabe-Operatoren

```C++
friend class xxx;
friend prototyp;
```

### Aufteilung in Dateien

- Ein .h-File und ein .cpp-File pro Klasse
- weitere .cpp/.h-Files für nicht-Klassen-Code (z.B. main)

Idee:

- Alles, was alle von der Klasse wissen bzw. verwenden sollen gehört in den .h-File (öffentliche Schnittstelle)
- Die Implementierung (Methoden, Deklarationen, ...) gehören in den .cpp-File

Technisch:

- .h-File darf nur Deklarationen enthalten, die weder Code erzeugen, noch globalen/statischen Speicher anlegen (sonst Namenskollisionen)
- Inline-Code wird nur im Kontext der aufrufenden Funktion erzeugt (wird somit mehrfach kompiliert -> keine Namenskollisionen)

Includes:

- Jeder File (.cpp + .h) inkludiert alle Header jener Klassen, die er direkt verwendet
- Jeder .cpp-File inkludiert den .h-File der eigenen Klasse
- Fehler bei mehrfachen Includes vermeiden: ```#ifndef /
#define / #endif```

### Enumeration innerhalb einer class

- werden innerhalb einer Klasse Enumerations-Typen nicht als ```public``` deklariert, kann dieser nur innerhalb der Klasse verwendet werden
- Zugriff auf ```public```-Enums: ```myClass::myEnumType; myClass::myEnumVal1```

### Dynamische Speicherverwaltung: new und delete

- `new` legt dynamischen Speicher an (vgl. ```malloc```), ruft den Konstruktor auf und liefert einen Pointer auf das Objekt/Array
- Primitives sind mit Standard-Konstruktor uninitialisiert (zufällige Bits)
- früher: gibt im Fehlerfall ```NULL```-Pointer zurück
	- altes mit neuem Standard: ```new (nothrow) myClass[10];``` (sonst wird Exception geworfen)

```C++
int *p = new int; // legt einen int dynamisch an
myClass *p = new myClass; // legt ein myClass-Objekt dynamisch an (Standardkonstruktor)
myClass *p = new myClass[size]; // legt ein Array der Größe size von myClass-Objekten an (nicht mit explizitem Konstruktor möglich)
// kein new für variable, mehrdimensionale Arrays (nur erste Dimension darf variabel sein)
myClass *p = new myClass(10, 30); // legt ein myClass-Objekt mit den übergebenen Argumenten an
double **data = new double * [size]; // zusammengesetzte Typen möglich
```

- `delete` ruft den Destruktor auf und gibt den Speicher frei (vgl. ```free```)
- darf auch mit ```NULL```-Pointer aufgerufen werden (keine Auswirkung)
```C++
delete p; // Gibt ein Objekt frei (p = Pointer auf Objekt)
delete [] p;  // Gibt ein Array von Objekten frei (p = Pointer auf Array)
```
