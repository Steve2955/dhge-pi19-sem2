Vertiefung Programmierung/Objektorientierte Programmierung
==========================================================


# Unterschiede C/C++

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

# Erweiterungen für Funktionen

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

# I/O und File-I/O

## Ein-/Ausgabe auf die Konsole

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

## Lesen und Schreiben von Dateien

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

# Objektorientierte Software-Entwicklung

- Bisher (C): Ablauforientiert = Schritt für Schritt = am Code orientiert
- Jetzt (C++): Datenorientiert -> Daten statt Algorithmus im Mittelpunkt
- Aufspaltung von Code in Objekte mit Eigenschaften und Funktionalitäten
	- Neue Denkweise: Daten sind aktiv, d.h. können Operationen auf sich selbst ausführen und werden für ein bestimmtes Objekt aufgerufen (in jeder Funktion gibt es einen "ich selbst"-wert)

## Konzepte und Terminologien

**Klasse**
- vgl. ```struct```-Typ erweitert um Funktionen und einiges mehr
- enthält keine Werte oder Daten, sondern dien als Schablone für diese

**Objekt**
- Instanz einer Klasse

**Methode**
- Einer Klasse zugehörige Funktion

**Member-Variable**
- Einer Klasse zugehöriges Datenelement (Primitives oder andere Objekte)

# Klassen und Objekte in C++

## Deklaration einer Klasse
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

## Objekte deklarieren/anlegen

- Klassenname ist zugleich Typ (vgl. ```struct``` mit ```typedef```)
- Initialisierung mit Standard-Konstruktor, Copy-Konstruktor (Kopie eines vorhandenen Objektes) oder Typumwandlungs-Konstruktor
- Zur Übergabe von Argumenten kann der Standard-Konstruktor überschrieben werden
- temporäre, anonyme Objekte: ```myFunc(myClass(x, 42), ...);```
- dynamisches anlegen mit ```new``` statt ```malloc```

## Definition des Codes von Methoden

- entweder direkt in der Klasse (nur kurze Methoden) oder danach (dann mit Klassennamen ```double myClass::myMeth(double *data, int size) { ...```)
- auch Definition von Konstruktoren außerhalb der Klasse möglich

## Konstruktoren

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

## Arten von Konstruktoren

- Standard-Konstruktor: Ohne Parameter, tut nichts (nur angelegt, wenn kein expliziter Konstruktor vorhanden)
- Copy-Konstruktor: erhält const-Referenz auf das Original, legt standardmäßig eine bitweise Kopie an (kann überschrieben werden)
- Typumwandlungs-Konstruktor: Parameter eines anderen Typs (meist const, Objektparameter als const Referenz)
	- wird ein Typumwandlungs-Konstruktor als ```explicit``` deklariert, wird er nicht für implizite Typumwandlungen verwendet

## "Verhinderte" Konstruktoren

- man kann Konstruktoren als ```private``` oder ```protected``` definieren (verhindert Zugriff von außerhalb der Klasse -> z.B. für Singelton-Klassen)
- Bei ausschließlicher Deklarierung von Konstruktoren (ohne Code) wird der Aufruf verhindert (Fehler beim Linken)
	- Ab C++-11: mit ```= delete```
- Häufige Anwendung: Copy-Konstruktor verhindern (z.B. statische Klassen -> Konstantensammlung)

## Destruktoren

- Metodenname mit Tilde: ```~myClass```; kein Paramter, kein Return (nur einer pro Klasse)
- Aufruf bei:
	- Verlassen des Blockes (lokale Objekte)
	- Ende des Programmes
	- Aufruf von ```delete```
	- Destruktor des Übergeordneten Objektes
- Pointer werden nicht automatisch freigegeben!

## Initialisierungsliste


```C++
Point(const Color &color, int x, int y) : mRGB(color), mX(x), mY(y) { ... }
```
- in der Reihenfolge der Deklaration
- Werte können beliebige Ausdrücke, Konstanten, globale Variablen oder Parameter des Konstruktors sein
- Notwendig für ```const```-Member und Member, die Objekte sind (damit explizit ein Konstruktor aufgerufen werden kann) und später bei Vererbung

## this

- Zeiger auf das eigene Objekt
- Verwendung innerhalb von Methoden

## Zugriff auf Member

- bei eigenen Membern: wie normale Variablen
- In der Namenssuch-Reihenfolge zwischen lokalen und globalen Variablen
- Member fremder Objekte: ```obj.member``` oder ```obPtr->member```
- ```private``` gilt auf Klassenebene -> Objekte gleicher Klasse können gegenseitig auf ```private```-Member zugreifen

## const-Methoden

- nach den Parametern steht const: ```(...)const```
- ändert ```this```: keine Zuweisung auf Member-Variablen, ruft intern nur const-Methoden auf
- Objekte, die als const deklariert sind, dürfen nur const-Methoden beinhalten

## Übliche Methoden get... und set...

Üblicherweise Member-Variablen nicht public -> Zugriff über Getter/Setter-Funktionen

## Aufruf von Methoden

- eigenes Objekt: wie normale Funktion oder ```this->meth()```
- fremdes Objekt: ```obj.meth()``` oder ```objPrt->meth()```

## Statische Member und Methoden

- einmal pro Klasse existent: Alle Objekte der Klasse greifen auf gleichen Wert zu
- Speicher wird bei Programmstart agelegt
- Müssen in der Klasse nicht nur deklariert, sondern auch definiert werden:
```C++
static int myCounter = 1; // in der Klasse
static int myClass::myCounter = 1; // außerhalb der Klasse
```
- Wenn statische Member public sind, kann auf diese auch ohne Objekt zugegriffen werden: ```myClass::myCounter = -1;```
- in statischen Methoden ist ```this``` nicht definiert

## const-Member

- normale const-Member-Variablen: existieren ein mal pro Objekt, Initialisierung durch Initialisierungsliste
- echte Konstanten: belegen keinen Speicher (nur Primitives)
- echte konstante Klassenvariablen: einmal im Speicher angelegt, bei Programmstart initialisiert (Initialisierung muss separat von der Deklaration stehen)

## Pointer auf Methoden

- dürfen nicht auf ```void*``` konvertiert werden
- Static Methoden sind normale Funktionspointer, keine Methoden-Pointer

## Objekte als Parameter und Returnwert

- wie bei Strukturen: Übergabe __by value__ möglich, normalerweise aber stets __by reference__

## Friend

- ```friend``` teilt den Zugriff auf alle Member und Methoden der eigenen Klasse
- Häufig eingesetzt bei eigenen Ausgabe-Operatoren

```C++
friend class xxx;
friend prototyp;
```

## Aufteilung in Dateien

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

## Enumeration innerhalb einer class

- werden innerhalb einer Klasse Enumerations-Typen nicht als ```public``` deklariert, kann dieser nur innerhalb der Klasse verwendet werden
- Zugriff auf ```public```-Enums: ```myClass::myEnumType; myClass::myEnumVal1```

## Dynamische Speicherverwaltung: new und delete

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

# Vererbung

- Eine Klasse kann als Erweiterung einer bestehenden Klasse deklariert werden (sie "erbt" **alle** Member und Methoden dieser Klasse)
	- Member werden unverändert übernommen, können nicht geändert werden
	- Methoden werden unverändert übernommen, können aber überschrieben werden (gleicher Prototyp, anderer Code)
	- Konstruktoren und Destruktoren existieren für jede Klasse separat
	- Neue Member und Methoden können die bestehende Klasse nach Belieben erweitern
```C++
// Button "erbt" alle Member und Methoden von DialogElement
class Button: public DialogElement {...};
// durch public werden die Rechte der Basis-Klasse unverändert übernommen (meist üblich)
```

## protected

- ```protected``` ist eine Mischung aus ```public``` und ```private```
- von außen sind ```protected```-Member unsichtbar (```private```)
- innerhalb der Klasse verhält sich ```protected``` wie ```public```

## Design-Hilfe

- __"X ist (auch) ein Y"__: X wird wahrscheinlich von Y abgeleitet
- __"X hat (auch) ein Y"__: Y ist wahrscheinlich ein Member von X

## Erben und Überschreiben von Methoden

- Überschreiben von Code einer Funktion, die bereits in der Vaterklasse deklariert ist
- Beim Aufruf wird stets der "zutreffenste" Code einer Methode ausgeführt (erst eigene, dann Vaterklasse)

## Virtuelle Methoden

- Ein Pointer der auf ein Objekt der Klasse x zeigt, kann entweder auf ein Objekt der Klasse x oder auf ein Objekt einer davon direkt oder indirekt abgeleiteten Klasse zeigen
- Man darf somit einen Pointer der Klasse X auch auf ein Objekt einer davon abgeleiteten Klasse zuweisen (__nicht umgekehrt__)

```C++
myBaseClass *p;
p = new mySubClass(...);
```

- Der Pointer kann nur jene Methoden und Member aufrufen, die bereits in der Vaterklasse deklariert sind
- Ob der Pointer eine Methode der Vaterklasse oder eine überschriebene Methode aufruft, hängt davon ab, ob diese als ```virtual``` deklariert ist
- die Methode muss bereits in der Vaterklasse als ```virtual``` deklariert sein

```C++
virtual void myFunc(); // Funktion der abgeleiteten Klasse wird aufgerufen
void myFunc(); // Funktion der Vaterklasse wird aufgerufen
```

## Typumwandlungen zwischen abgeleiteten Klassen

- Wie kann man feststellen, ob ein Pointer auf eine Vaterklasse oder abgeleitete Klasse zeigt?
	- Deklaration eines Members in der Vaterklasse, der diese Information beinhaltet
	- Deklaration einer Funktion, die den Typ angibt und von abgeleiteten Klassen überschrieben wird
- Wie kann auf Member und Methoden der abgeleiteten Klasse zugegriffen werden?
	- ```static_cast``` auf eine abgeleitete Klasse möglich (aber unsicher, __nur umgekehrt verwenden__)
	- ```dynamic_cast``` für den speziellen Fall deklarieren (Sicher durch Laufzeitüberprüfung -> bei falscher Klasse ```NULL```-Pointer; funktioniert nur wenn mindestens eine virtuelle Methode deklariert ist)

## Konstruktoren und Destruktoren in abgeleiteten Klassen

**Reihenfolge**

- Beim Anlegen eines Objektes werden automatisch die Konstruktoren aller seiner Klassen aufgerufen (in Ableitungsreihenfolge)
- Der Aufruf der Destruktoren erfolgt in umgekehrter Reihenfolge

**Welcher Konstruktor der Basisklasse wir aufgerufen?**

- Normalerweise Standard-Konstruktor
- Besitzt die Vaterklasse keinen Standard-Konstruktor oder soll ein anderer Konstruktor aufgerufen werden, muss dies an die erste Stelle der Initialisierungsliste geschrieben werden
- Bei automatischen Copy-Konstruktoren, wird der der Basisklasse verwendet
- Ein expliziter Copy-Konstruktor ruft den Standard-Konstruktor der Basisklasse (Member der Basisklasse werden nicht automatisch deklariert -> uninitialisiert)
	- Sollen Member der Basisklasse kopiert werden, muss in der Initialisierungsliste der abgeleiteten Klasse als erstes explizit der Copy-Konstruktor der Basisklasse aufgerufen werden

**virtual**

- Konstruktoren können nicht virtuell sein
- Destruktoren können als virtuell deklariert werden (z.B. wenn es eine übergeordnete Klasse mit Pointer o.ä. auf die Basisklasse hat)
	- wird ein Destruktor nicht als ```virtual``` deklariert, wird nur der Destruktor der abgeleiteten Klasse aufgerufen
	- Faustregel: **Immer wenn eine Klasse eine virtuelle Methode enthält, muss man den Destruktor virtuell machen**

**Virtuelle Aufrufe**

Im Code von Konstruktoren und Destruktoren ist der Aufruf virtueller Methoden nicht möglich, es wird immer die Methode unmittelbar aus der Klasse des Konstruktor aufgerufen.

## Aufruf der Methode einer Vaterklasse

Um explizit die Methode einer Vaterklasse aufzurufen, muss der Scope-Operator verwendet werden.

```C++
myBaseClass::myFunc(...); // Aufruf für das eigene Objekt
someObj.myBaseClass::myFunc(...); // Für andere Objekte
ptr->myBaseClass::myFunc(...); // ^^
```

## Rein virtuelle Methoden, abstrakte Klassen

- Häufig soll eine Methoden in einer Basisklasse deklariert (Prototyp), aber nicht Implementiert werden (Code)
- = rein virtuelle Methoden
- Basisklassen von denen keine Objekte direkt angelegt werden sollen, heißen "abstrakte" Klassen (werden eigens gekennzeichnet, ist automatisch ab einer rein virtuellen Methode abstrakt -> diese Eigenschaft wird vererbt)

```C++
virtual void draw() = 0; // Rein virtuelle Methode
```

- rein virtuelle Destruktoren werden durch ```{}``` markiert

## Mehrfachvererbung

```C++
class myClass : public Base1, public Base2 { ... };
```

- bei identischen Member/Methoden-Bezeichnungen muss der Scope-Operator verwendet werden (```Base1::xyz```)
- Besitzen die Vaterklassen indirekt selbst eine geteilte Vaterklasse, so werden zwei Instanzen dieser Großvaterklasse erzeugt (Großvaterklasse muss in Vaterklasse als ```virtual``` geerbt werden)
- solche Konstrukte sollten vermieden werden

## ```clone```-Trick

- Pointer auf Objekt der Basisklasse kann entweder auf Basisklasse oder auf abgeleitete Klassen zeigen
- Copy-Konstruktor reicht der Basisklasse nicht, um die Member der abgeleiteten Klasse zu kopieren

```C++
// Deklaration von clone() in der Basisklasse, kann auch definiert werden
virtual Base* clone() const;

// Implementierung von clone() in der abgeleiteten Klasse
virtual Child* clone() const {
 return new Child(*this);
}
// Korrekte Klasse wird nun automatisch Kopiert (mit allen Membern)
copyPtr = origPtr->clone();
```

# Operator Overloading

- Overloading ermöglicht das überschreiben völlig getrennter unabhängiger Funktionen
- diese Funktionalität lässt sich auch für Operatoren wie ```+,-,=,->,&&,==, ...``` realisieren

```C++
T& T::operator =(const T& b); // Basic assignment
bool T::operator >(const T& b) const; // Greater than
T T::operator ~() const; // Bitwise not
R& T::operator [](const T2& b); // Array subscript
// ...
```

- Gleiche Operationen mit unterschiedlichen Operanden lassen sich mit verschiedenen Parameter-Typen überschreiben
- Können global oder als Methode einer Klasse definiert werden
	- soll der Operator als Methode aufgerufen werden, muss der linke Operator die entsprechende Klasse sein (das eigene Objekt wird mit ```this``` übergeben)
	- Kann der Operand in einer Klasse (Basistyp oder fremd) nicht überschrieben werden, muss der Operator global überschrieben werden
	- für I/O-Zwecke werden immer als globale Funktionen definiert
- Anzahl der Operanden, Bindungsrichtung Priorität sind nicht überschreibbar
- Operator-Funktionen (speziell ```<<, >>```) werden oft als ```friend``` definiert, damit auch auf die ```private``` Member der Klassen zugegriffen werden kann
- Operanden werden normalerweise als ```const```-Referenz übergeben (Ausnahme: Zuweisungen; das ```const``` für ```this``` steht im Prototypen)

## Returnwert

**Der Operator berechnet ein neues Ergebnis**

- Returnwert ist keine Referenz, Operanden sind als ```const``` definiert
- neues, lokales Objekt anlegen und zurückgeben (__by value__)

**Der Operator ändert einen der Operanden**

- Returnwert muss eine Referenz sein (verweist auf geänderten Operanden, keine Kopie)
- Bei Funktion: ein Operand muss Referenz sein, kein ```const``` (diese Referenz muss zurückgegeben werden)
- Bei Methode: gibt Referenz auf das eigene Objekt zurück (```return *this;```)


## Zuweisungsoperator

- kann nur als Methode definiert werden
- immer erst Prüfung auf Selbst-Zuweisung (```if (this == &value) return *this;```)
- Zuweisungs-Operator einer abgeleiteten Klasse: Aufruf der Basisklasse (```this->myBaseClass::operator=(val);```)
- ```return *this;``` (Referenz auf Objekt der eigenen Klasse)
- Verwendung: Aufräumen, Pointer auf dynamische Daten

## Index-Operator

- kann nur als Methode definiert werden
- bei Zuweisung Rückgabe einer Referenz auf das ausgewählte Element, sonst *by value*

```C++
elemClass &operator[] (int index); // Lesen und Schreiben (Zuweisung)
elemClass const &operator[] (int index) const; // Lesen
```

## <</>>-Operator

```C++
ostream &operator<<(ostream &outFile, const myClass &val);
istream &operator>>(istream &inFile, myClass &var);
// für Reihung mehrere Ein-/Ausgabe Operationen:
return outFile;
```

## Der Typ-Cast-Operator

- kann nur als Methode definiert werden (Umwandlung des ```this```)
- Operator-Name = Typ-Name (z.B.```operator double()```); kein expliziter Return-Typ
- Verwandelt Klasse in fremden Typ

## Increment- und Decrement-Operator

- Prefix: Returnwert = Referenz auf das eigene Objekt
- Postfix: Returnwert = neuer Wert *by value*
- Unterscheidung über zusätzlichen funktionslosen int-Parameter (mit = suffix)

## Probleme von virtuellen Funktionen und Operatoren

Vorrausetzung für das Überschreiben:
- Return-Typ muss exakt ident sein (oder voneinander abgeleitete Klassen)
- Parameter müssen exakt ident sein (keine abgeleitete Klassen! -> viele Probleme)
In der Realität kaum überschriebene Operatoren

# Strings und Stringstreams

- Header: ```<string>``` (alte C-Strings: ```<cstring>```)
- Umwandlung von C-Strings in C++-Strings sehr angenehm (Verwendung von C-Strings mit C++ Funktionen)

**Operationen auf String-Objekte**

- ```s.clear();``` - setze ```s``` auf Leerstring
- ```s.length();``` oder ```s.size();``` - Tatsächliche Länge von ```s```
- ```s.empty();``` - ist ```s``` leer?
- Zugriff auf einzelne Zeichen: ```s[];``` (ohne Längenprüfung!)
- Zusammenhängen mit ```+``` Operator (mindestens ein Operand muss ```string``` sein)
- Anhängen mit ```+=``` ```s.append()```: für String, C-String oder char
- Teilstring extrahieren mit ```s.substr(pos,n)```
- Vergleich über Normale Operatoren ```== != < > <= >``` oder ```s1.compare(s2)```
- Weitere Funktionen: ```find, insert, erase, replace```

**String-Streams**

- Header: ```<sstream>```
- Ein- oder Ausgabe wie bei ```cin, cout``` mit ```<<, >>``` (in einen String schreiben oder lesen)

```C++
stringstream s;
s << "Hello " << name << "!\n";
return s.str(); // Liefert internen String
```

# Objekte mit Pointer

- Hast du Objekte mit Pointern oder dynamischen Arrays, muss du dich für Konstruktor, Copy-Konstruktor, Dekonstruktor, ... selbst um die Speicherverwaltung kümmern (default: bitweise Kopie)
