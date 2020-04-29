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
- sog. Quellprogramme werden mit Übersetzungswerkzeugen in Maschinensprache des Rechners übersetzt

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
- relative Adressierung: ähnlich indizierte Adressierung, Basisregister statt Indexregister
- PC-relative Adressierung: Berechnung der nächsten Adresse relativ zur aktuell bearbeiteten Adresse (Sonderform der relativen Addressierung)
- virtuelle Adressierung: Ansprechen von Speicherbereichen außerhalb des Hauptspeichers (Ein-/Auslagern der Daten)

## Sprachen

### Syntax einer Programmiersprache

- Die Syntax einer Sprache bezeichnet die durch die Zeichen und Regeln einer Sprache entstehenden Konstrukte
- Für eine Überprüfung auf Korrektheit der Syntax muss diese durch Automaten oder Grammatiken formal beschrieben werden
- Bei der Programmierung wird diese Überprüfung durch den Compiler durchgeführt
- Sollte der Programmcode nicht der Syntax (den Regeln der Programmiersprache) entsprechen, kann dieser nicht compiliert werden

#### Grundlegende Begriffe

- **Alphabet:** nicht leere, eventuell unendliche Menge von unterscheidbaren Zeichen ($A = {a_1,a_2,\dots,a_n}$)
- **Buchstaben:** Zeichen eines Alphabets; innerhalb des Alphabet besteht zwischen den Zeichen eine Ordnungsrelation ($a_1<a_2<\dots<a_n$)
	- liegt keine Ordnungsrelation vor, spricht man von einem Zeichenvorrat
- **Wort:** Aneinanderreihung von Zeichen eines Alphabets
	- Ein Wort das aus keinem Zeichen besteht wird als leeres Wort bezeichnet und als $\epsilon$ dargestellt
	- $A*$ bezeichnet die Menge aller Worte, die mit einem Alphabet $A$ gebildet werden können
	- Die Länge eines Wortes $w$ (Anzahl der Zeichen) wird als $\left|w\right|$ dargestellt
- **Sprache**
	- Unterteilung in natürliche und künstliche Sprachen
	- Natürliche Sprachen dienen der Kommunikation zwischen Menschen
		- bestehen aus einer Menge von Worten (Wortschatz) und Regeln (Grammatik)
		- Worte werden zu Sätzen zusammengefügt, welche eine bestimmte Bedeutung (Semantik) besitzen
		- Wortschatz, Grammatik und Semantik unterliegen ständiger Veränderung -> für maschinelle Verarbeitung unbrauchbar
	- Künstliche Sprachen streben eine möglichst einheitliche, klare und eindeutige Beschreibung an (meist fachspezifisch)
		- Beispiel: Programmiersprachen -> Kommunikation zwischen Maschinensprache und problemorientierter Fachsprache, die einer natürlichen Sprache deutlich näher kommt
		- fester, begrenzter Wortschatz und feste, endliche Grammatik (eindeutige, vollständige Beschreibung der Sprachen)

### Darstellungsmöglichkeiten zur Sprachbeschreibung

#### Grammatiken

- Regelwerk, das festlegt, welche Zeichen und Zeichenreihen zu einer Sprache gehören.
- Definierung von Programmiersprachen erfolgt über präzise Grammatiken

**Bestandteile einer Grammatik**

$$G = {T,V,S,P}$$

- Menge $T$ von **Terminalsymbolen**: unveränderliche und unteilbare Bestandteile der Sprache
- Menge $V$ von **Nichtterminalsymbolen**: Zeichen und Zeichenfolgen, die nach den Regeln der Grammatik gebildet werden können
- Menge $P$ von **Grammatikregeln**: Regeln, die festlegen wie aus Terminalsymbolen und/oder Nichtterminalsymbolen neue Konstrukte (Nichtterminalsymbole) gebildet werden können
- Das **Startsymbol** $S$: Nichtterminalsymbol, aus dem alle Worte der Sprache abgeleitet werden

#### Backus-Naur-Form

- Metasprache zur Beschreibung der Syntax einer Programmiersprache
- Eine Grammatikregel in der Backus-Naur-Form besitzt eine linke und eine rechte Seite
	- Linke Seite: Nichtterminalsymbol, das durch die Regel definiert werden soll (Nichtterminalsymbole werden durch ```<...>``` dargestellt)
	- Rechte Seite: Regel zur Bildung des Nichtterminalsymbols (Alternative Bildungen werden durch ```|``` getrennt)
- Trennung der beiden Seiten erfolgt durch ```::=```
- Terminalsymbole sind nicht durch Regeln erzeugbar
- Beispiel:
```
<Zeichen> ::= <Buchstabe> | <Sonderzeichen> | <Ziffer>
<Buchstabe> ::= A | B | C | ... | Z
```
- Erweiterungen:
	- Optionale Symbole oder Symbolfolge in eckigen Klammern (```<Zeichenkette> ::= <Zeichen> [<Zeichenkette>]```)
	- Darstellung von Alternative in geschweiften Klammern (```<Ausdruck> ::= <Operand> {+|-|*|/} <Operand>```)

#### Einfache Syntaxdiagramme

- die BNF kann leicht in Diagramme übertragen werden
- Terminalsymbole werden in Kreise eingeschlossen
- Nichtterminalsymbole werden in Rechtecke eingeschlossen
- Ersetzungswege werde durch Pfeile dargestellt

![Beispiel eines BNF-Diagramms](https://steve2955.github.io/dhge-pi19-sem2/INF/IMG/BNF-Diagramm.JPG)

#### Übung BNF

Grammatik für die Definition eines Funktionsprototypen (ähnlich der Definition von Funktionsprototypen)

<S> ::= <Datentyp> <Bezeichner>(<Parameterliste>);

<Datentyp> ::= int | float | char

<Bezeichner> ::= <Buchstabe> | _ <Zeichenfolge> | <Buchstabe><Zeichenfolge>
<Zeichenfolge> ::= <Zeichen> | <Zeichen><Zeichenfolge>
<Zeichen> ::= <Buchstabe> | <Ziffer> | <Sonderzeichen>
<Buchstabe> ::= a..Z
<Ziffer> ::= 0..9
<Sonderzeichen> ::= $ | _ | ? | #

<Parameterliste> ::= ∊ | <Parameterfolge>
<Parameterfolge> ::= <Datentyp> | <Datentyp>,<Parameterfolge>

#### Sprachbeschreibung mittels Regulärer Ausdrücke

- Reguläre Ausdrücke können reguläre Mengen beschrieben

**Definition einer regulären Menge**

- $\emptyset \in R$; die leere Menge ist regulär
- $\left{\epsilon\right}\in R$; die Menge, die das leere Wort enthält ist regulär
- $\left{ a \right}\in R \forall a \in A$
- Vereinigungen und Konkatenation von regulären Mengen sind ebenfalls regulär
- Eine Menge ist genau dann regulär, wenn sie in endlich vielen Schritten aus diesen Regeln gewonnen werden kann

**Konkatenation**
- $(p)^*$****: Konkatenation von $p$ mit sich selbst
- $(pq)$: Konkatenation von $P$ und %Q%

**Vereinigung**
- $p \lor q$: Vereinigungsmenge von $P$ und $Q$

**Beispiel**
Alphabet $A=\left{a,b\right}$, dessen Worte weder **aa** noch **bb** enthalten

$$L \subset A^*=(ab)^*\lor(ba)^*\lor a(ba)^* \lor b(ab)^*$$****

#### Sprachbeschreibung mittels deterministischer Automaten

- Beschreibung von Sprachen mittels deterministischer Automaten ist sehr aufwendig
- Bestandteile:
	- I,O: Ein- und Ausgabealphabet
	- Q: endliche Menge an Zuständen, in denen sich der Automat befinden kann
	- $\partial$: Überführungsfunktion, die in Abhängigkeit von einem gelesenen Zeichen und dem aktuellen Zustand in einem anderen Zustand überführt
	- $q_0 \in Q$: Startzustand des Automaten
	- $F \subset Q$: Teilmenge aller Endzustände, bei deren Erreichen der Automat eine erfolgreich abgearbeitete Aufgabe anzeigt

**Beispiel**
Automat, der nur dessen Worte akzeptiert, die weder **aa** noch **bb** enthalten

![Beispiel eines Deterministischen Automaten](https://steve2955.github.io/dhge-pi19-sem2/INF/IMG/Deterministischer-Automat.JPG)
