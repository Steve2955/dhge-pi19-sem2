Informationsverarbeitung - Zusammenfassung
==========================================

# Programmiersprachen

- Sprachen zur Beschreibung von Daten und zur Formulierung von Verarbeitungsvorschriften (Schnittstelle zwischen Nutzer und Maschine)
- Maschinenorientierte Sprachen: Orientierung am Befehlssatz der Hardware (komplex, effizient, hw-spezifisch)
- Problemorientierte Sprachen: Orientierung an Problemstellungen (einfach, weniger effizient, plattformunabhängig)

## Maschinenorientierte Programmierung

- Orientierung am Befehlssatz des Zentralprozessors
- **Befehl:** kleinste nicht zerlegbare Einheit -> beschreibt einzelnen Arbeitsschritt (Operation + Adresse)

**Adressierungsarten**

- **unmittelbar:** Operand im Adressteil
- **absolut/direkt:** Adresse des Operanden im Adressteil
- **indirekt:** Adresse der Speicherzelle der Adresse des Operanden im Adressteil
- **symbolisch:** Zuordnung von Speicherzellen zu Namen (während Linken durch absolute Adressen ersetzt)
- **indiziert:** Adressteil + Indexregister = Adresse des Operanden
- **relativ:** vgl. indiziert (Basis- statt Indexregister)
- **PC-relativ:** relativ zur aktuell Bearbeiten Adresse
- **virtuell:** Speicherbereich außerhalb des Hauptspeichers

## Problemorientierte Programmierung

- **Imperative Programmierung:** Folge von Anweisungen (Weg der Verarbeitung im Vordergrund)
- **Funktionale Programmierung:** Funktionen (Ausdrücke aus Operationen) die Eingaben in Ausgaben abbilden
- **Prädikative Programmierung:** Beweis aus einem System aus Tatsachen und Regeln
- **Objektorientierte Programmierung:** Zusammenfassung von Teilproblemen in Objekten (Daten, Operationen)

# Sprachen

- **Alphabet:** nicht leere, eventuell unendliche Menge von unterscheidbaren Zeichen ($A = {a_1,a_2,\dots ,a_n}$)
- **Buchstaben:** Zeichen eines Alphabets; innerhalb des Alphabet besteht zwischen den Zeichen eine Ordnungsrelation ($a_1<a_2< \dots < a_n$)
- **Zeichenvorrat:** Buchstaben ohne Ordnungsrelation
- **Wort:** Aneinanderreihung von Zeichen eines Alphabets ($A*$ Menge aller Worte eines Alphabets $A$)
- **Natürliche Sprachen:** Kommunikation zw. Menschen
	- Worte bilden nach Regeln (Grammatik) Sätze, die Bedeutung (Semantik) besitzen
	- unterliegen ständiger Veränderung -> für maschinelle Verarbeitung unbrauchbar
- **Künstliche Sprachen:** einheitliche, klare und eindeutige
	- fester, begrenzter Wortschatz und feste, endliche Grammatik (eindeutige, vollständige Beschreibung der Sprachen)

## Grammatiken

- Regelwerk zur Zuordnung von Zeichen und Zeichenreihen zu einer Sprache

$$G = {T,V,S,P}$$

- **Terminalsymbole** $T$: unveränderliche, unteilbare Bestandteile der Sprache
- **Nichtterminalsymbolen** $V$: Zeichen/Zeichenfolgen, die nach den Regeln der Grammatik gebildet werden können
- **Grammatikregeln** $P$: Regeln, die festlegen wie aus Terminalsymbolen und/oder Nichtterminalsymbolen neue Konstrukte gebildet werden können
- **Startsymbol** $S$: Nichtterminalsymbol, aus dem alle Worte der Sprache abgeleitet werden

### Backus-Naur-Form

- Metasprache zur Beschreibung der Syntax einer Programmiersprache
```abnf
<Zeichen> ::= <Buchstabe> | <Sonderzeichen> | <Ziffer>
<Buchstabe> ::= A | B | C | ... | Z
```
- Erweiterungen:
	- Optionale Symbole in eckigen Klammern (```<Zeichenkette> ::= <Zeichen> [<Zeichenkette>]```)
	- Alternativen in geschweiften Klammern (```<Ausdruck> ::= <Operand> {+|-|*|/} <Operand>```)

### Einfache Syntaxdiagramme

- vgl. grafische Darstellung der BNF
- Terminalsymbole = Kreise; Nichtterminalsymbole = Rechtecke
- Ersetzungswege durch Pfeile dargestellt

### Reguläre Ausdrücke

- beschreiben reguläre Mengen

**Definition einer regulären Menge**

- $\emptyset \in R$; die leere Menge ist regulär
- $\{\epsilon\}\in R$; die Menge, die das leere Wort enthält ist regulär
- $\{a\}\in R \;\forall\; a \in A$
- Vereinigungen und Konkatenation von regulären Mengen sind ebenfalls regulär
	- $(p)^{\ast}$: Konkatenation von $p$ mit sich selbst
	- $(pq)$: Konkatenation von $p$ und $q$
	- $p \lor q$: Vereinigungsmenge von $p$ und $q$
- Eine Menge ist genau dann regulär, wenn sie in endlich vielen Schritten aus diesen Regeln gewonnen werden kann

**Beispiel:** Alphabet $A=\{a,b\}$, dessen Worte weder **aa** noch **bb** enthalten

$$L \subset A^{\ast}=(ab)^{\ast}\lor(ba)^{\ast}\lor a(ba)^{\ast} \lor b(ab)^{\ast}$$

### Deterministische Automaten

- $I,O$: Ein- und Ausgabealphabet
- $Q$: endliche Menge an Zuständen, in denen sich der Automat befinden kann
- $\partial$: Überführungsfunktion, die in Abhängigkeit von einem gelesenen Zeichen und dem aktuellen Zustand in einem anderen Zustand überführt
- $q_0 \in Q$: Startzustand des Automaten
- $F \subset Q$: Teilmenge aller Endzustände, bei deren Erreichen der Automat eine erfolgreich abgearbeitete Aufgabe anzeigt

**Beispiel** Automat, der nur Worte akzeptiert, die weder **aa** noch **bb** enthalten

![Beispiel eines Deterministischen Automaten](https://steve2955.github.io/dhge-pi19-sem2/INV/IMG/Deterministischer-Automat.JPG)

# Automaten

- keine technischen Geräte in der Informatik -> mathematische Modelle zur Umformung von Eingaben (definieren Lösbarkeit von Problemen mit Rechnern)
- Unterscheidung zw. erkennende und übersetzenden Automaten (Akzeptoren/Transduktoren)
- $f: A\rightarrow B$: Abbildung von Elementen einer Menge $A$ (Urbildbereich) in eine Menge $B$ (Bildbereich)
	- **injektiv:** zwei unterschiedliche Werte aus A werden zwei unterschiedlichen Werte aus B zugeordnet
	- **surjektiv:** jedes $b$ kommt auch als Bild vor
	- **bijektiv:** Funktion ist _injektiv_ und _surjektiv_ (eindeutig umkehrbar)

## Registermaschinen

- Registermaschine = vereinfachtes Modell realer Rechner (Vorbild: Von-Neumann-Architektur)
- beinhaltet Befehlszähler, Akkumulator, Programm und endliche Anzahl von Registern
- jedes Register kann eine beliebig große natürliche Zahl aufnehmen und unterstützt folgende Operationen:
	- Inkrement: Erhöhen des Wertes um 1
	- Dekrement: Vermindern des Wertes um 1
	- Test des Wertes im Register auf 0
- eine Registermaschine besitzt $m$ Register und berechnet die Funktionen $f:N^r_0 \rightarrow N^s_0 \;\text{mit}\; r,s \leq m$
- Eingabe in den ersten Registern $r$, Ausgabe beginnend im ersten Register $s$

### Programm

- einzelne Befehle des Programmes sind nummeriert
- Programm verarbeitet natürliche Zahlen aus den Eingaberegistern in natürliche Zahlen in den Ausgaberegistern
- Eingabe wird in den Erste $r$ Registern gespeichert (restliche Register mit 0 belegt)
- Programm beginnt bei der mit 0 gekennzeichneten Anweisung, stoppt, wenn zu einer Marke verzweigt werden soll, die nicht im Programm enthalten ist

```Javascript
i:DO f ; GOTO j // Ausführung einer Registeroperation und Sprung nach j
i:IF t THEN GOTO j ELSE GOTO k // Test, ob der Registerinhalt 0 ist,
                               // wenn ja Sprung nach j, sonst nach k
```
- Tupelschreibweise: $(i,f,j)$ und $(i,t,j,k)$

### Technische Umsetzung

- Durchführung von bestimmte Registeroperationen in speziellen Registern: Akkumulatoren (+ Befehlszähler)
- Zum Ausführen einer Operation: in Akkumulator laden, dann zurückspeichern
- Erweiterung mit wahlfreiem Zugriff auf Speicherzellen = Random Access Machine (RAM)

# Turing-Maschinen

- universelles Automatenmodell (unendliches Band, Lese-/Schreibkopf, Befehlszähler, Programm)
- Konfiguration = Momentaufnahme des Zustands einer Turing-Maschine

$$T=(I,B,Q,\delta,q_0,F)$$

- Eingabealphabet: $I \subset B$
- Bandalphabet: $B$
- endliche Menge an Zuständen: $Q$
- Startzustand: $q_0$
- Menge der möglichen Endzustände: $F \subset Q$
- Zustandsüberführungsfunktion: $\delta$

## Mehrspurmaschine

- Erweiterung der Turing-Maschine ($B \rightarrow I \cup B^k$ mit $k$ = Anzahl der Spuren)
- Verwendung für mehrere Operanden (Addition, oder für Zwischenrechnungen)

## Nichtdeterministische Turing-Maschine

- formelle Definition identisch zu deterministischen Turingmaschinen
- Übergang von einem Zustand und einem Zeichen in mehrere Zustände möglich -> **"Orakel"** sorgt für Wahl des kürzesten Weges
- Wort wird akzeptiert, wenn es mindestens einen akzeptierten Rechen weg gibt
- technisch nicht realisierbar

## Churchesche-These

**Die durch formale Definition der Turing-Berechenbarkeit erfasste Klasse von Funktionen stimmt mit der Klasse der intuitiv berechenbaren Funktionen überein.**

- bisher nicht beweisbar
- z.B. kein automatisches Verfahren für die Überprüfung der Korrektheit beliebiger Programme (Halte-Problem)

# Endliche Automaten

## Schaltwerke und endliche deterministische Automaten

- Hardware aus festverdrahteten Schaltkreise
- jeder Befehl benötigt bestimmte Schaltungen (Miniaturisierung nicht möglich)
- ein Schaltkreis $S$ wird durch eine externe Eingabe $x_1,\dots,x_l$ und $k$ interne Steuersignale gespeist($s_1\dots,s_k$)
- daraus entstehende externe Ausgaben $y_1,\dots,y_m$ und neue Steuersignale $s_1',\dots,s_k'$ werden zunächst in einem Block aus Flip-Flops zwischengespeichert und im nächsten Takt ausgegeben
- Ausgabe des nächsten Verarbeitungsschrittes in Abhängigkeit von Eingaben und zuvor erzeugten Steuersignalen

### Mealy-Automat

$$M=(Q,I,O,q_0,\delta,\gamma,F)$$

- endliche Menge an Zuständen $Q = \{0,1\}^k$
- Eingabealphabet $I = \{0,1\}^l$
- Ausgabeaphabet $O = \{0,1\}^m$
- Anfangszustand $q_0 \in Q$
- Zustandsüberführungsfunktion: $\delta:Q\times I \rightarrow Q$
- Ausgabefunktion: $\gamma:Q\times I \rightarrow O$
- Menge akzeptierter Endzustände $F \subset Q$

Ein Eingabewort $w$ wird von einem Mealy-Automaten genau dann akzeptiert, wenn sich der Automat nach dem vollständigen Lesen der Eingabe in einem der Finalzustände befindet. Die durch diese Einschränkung entstehenden Automaten der Form $M = (Q, I, q_0, \delta, F)$ heißen endliche deterministische Automaten. (deterministisch: gleiche Eingabe = gleiche Ausgabe)

**Arbeitsweise**

- Wort $w$ wird von links nach rechts gelesen (bei jedem Schritt: Verarbeitung eines Zeichen -> Zustandswechsel)
- Befindet sich der Automat nach der Bearbeitung aller Zeichen in einem Finalzustand, wurde $w$ akzeptiert

## Endliche nichtdeterministische Automaten

- mehrere/keine Kanten für ein Zeichen, Kanten für Zeichenketten -> einfachere Problembeschreibung
- jeder nichtdeterministischer Automat kann komplexer als deterministischer Automat realisiert werden
- akzeptieren eine Eingabe, wenn mindestens ein Weg vom Anfangszustand in den Endzustand existiert
- hat ein Zustand keine Kante, die das Zeichen verarbeitet, wird das Wort nicht akzeptiert

## Überführung nichtdeterministischer Automaten in deterministische Automaten

- **Schritt 1:** Aufspalten von Kanten mit Zeichenketten
- **Schritt 2:** Zusammenführen von Kanten und Zuständen mit gleichem Zeichen und Ausgangszustand (jeder Knoten, der einen Finalzustand enthält ist selbst Finalzustand; Fehlende Kanten führen zu einem Fehlerzustand)

# Grammatiken der Chomsky Hierarchie

- Chomsky-0: Grammatiken ohne Einschränkungen
- Chomsky-1: Alle Regeln der Form $u\rightarrow v$ mit $u \in V^+$ mit $v \in ((V \cup T) - {S})^+$ und $|u| \leq |v|$ oder $S \rightarrow \varepsilon$(kontextsensitive Grammatiken)
- Chomsky-2: Alle Regeln der Form $A\rightarrow v$ mit $A \in V$ und $v \in (V \cup T)^* $(kontextfreie Grammatiken)
- Chomsky-3: Alle Regeln der Form $A\rightarrow v$ mit $A \in V$ und $v = \varepsilon$ oder $v = aB$ mit $a \in T$ und $B \in V$ (rechtslinear, reguläre Grammatiken)

# Deterministische Kellerautomaten

- um einen Keller erweiterte endliche Automaten (LIFO)
- Kellerband ermöglicht Merken bestimmter Zeichen und Zustandsübergänge in Abhängigkeit vom zuletzt gemerkten Zeichen
- Bsp: Grammatik zum Erkennen von paarigen Klammern
