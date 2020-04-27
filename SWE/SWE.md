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
