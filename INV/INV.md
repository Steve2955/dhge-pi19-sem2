Informationsverarbeitung
========================

# Grundlagen der Programmierung

## Einteilung der Programmiersprachen

- Sprachen zur Beschreibung von Daten und zur Formulierung von Verarbeitungsvorschriften
- Schnittstelle zwischen Benutzer und Maschine

| Maschinenorientierte Sprachen                                                   | Problemorientierte Sprachen                                             |
|---------------------------------------------------------------------------------|-------------------------------------------------------------------------|
| - Orientieren sich am Befehlssatz der zugrundeliegenden Hardware                | - Sprache orientiert sich an den zu lösenden Problemstellungen          |
| - Programmierung für einen spezifischen Prozessor (nicht Plattformübergreifend) | - Bsp.: imperative, funktionale, logische o. deskriptive Programmierung |
| - sehr einfache Befehle -> Komplexe Programmierung                              | - auch "höhere Programmiersprachen"                                     |
| - Assembler-Programmierung = Vereinfachung durch mnemonische Ersetzungen        | - plattformunabhängige Entwicklung durch Verwendung von Compilern       |
| - hohe Effizienz                                                                | - einfachere Programmierung                                             |

### Problemorientierte Programmiersprachen

- zu sehr großen Teil von der zugrundeliegenden Maschine unabhängig
- definierter Kern: Wesen der Sprachen überall gleich
- eventuell maschinen-/plattformspezifische Erweiterungen
- sog. Quellprogramme werden mit Übersetzungswerkzeugen in Maschinensprache des Rechners übersetzt

#### Imperative Programmiersprachen

- Folge von Anweisungen
- Weg der Verarbeitung im Vordergrund
- Bsp.: C, Pascal, Fortan, Cobol, Basic

#### Funktionale Programmiersprachen

- Funktionen die Eingabegrößen in Ausgabegrößen abbilden
- Funktionen bestehen aus Audrücken, die sich aus Operationen zusammen setzen
- Bsp.: Lisp

#### Deskriptive Programmiersprachen

- Ergebnis selbst im Vordergrund -> Sprache beschreibt Eigenschaften des gewünschten Ergebnis
- Programm liefert alle Eingabewerte, die diese Bedingungen erfüllen
- keine Manipulation der Eingabegrößen
- oft Abfragesprachen für Datenbanken -> Bsp.: SQL

#### Prädikative Programmiersprachen

- Beweis in einem System aus Tatsachen und Regeln im Vordergrund (= Wissensbasis)
- Benutzer formuliert Anfrage an das System, die dieses versucht mit "richtig" oder "falsch" zu beantworten
- Bsp.: Prolog

#### Objektorientierte Programmiersprachen

- Zusammenfassen der zur Lösung von Teilproblemen notwendigen Daten und Operationen zu Objekten
- Objekte kommunizieren über Signale und Botschaften miteinander
- Einige imperative Vertretter sind durch objektorientierte Programmierung erweitert wurden
- Bsp.: C++, Java, Smalltalk

### Maschinenorientierte Programmiersprachen

- Orientierung an der vorliegenden Hardware (Befehlssatz des Zentralprozessors)
- Typische Vertretter: Assemblersprachen

**Befehl**

- kleinste, nicht weiter zerlegbare Einheit einer Programmiersprache
- bezeichnen einzelne Arbeitsschritte
- bei problemorientierten Sprachen: Anweisung (oft keine einzelnen Schritte, sondern komplexere Abläufe)
- nicht weiter zerlegbare Anweisung = elementare Answeisung
- Befehl = Operationsteil + Adressteil

#### Adressierungsarten

- unmittelbare Adressierung: Operand direkt im Adressteil des Befehls (kein Speicherzugriff nötig)
- absolute/direkte Adressierung: die im Adressteil angegebene Adresse gibt den Aufenthaltsort de Operanden an
- indirekte Adressierung: Adressteil gibt Adresse der Speicherzelle an, in der sich die Adresse des Operanden befindet
- symbolische Adressierung: Zuordnung einer Speicherzelle zu frei wählbarem Namen (wird während des Linkens durch absolute Adresse ersetzt)
- indizierte Adressierung: Summe des Adressteils und dem Wert eines Indexregisters gibt die Adresse des Operanden an
- relative Adressierung: ähnlich indizierte Adressierung, Basisregister statt Indexregister
- PC-relative Adressierung: Berechnung der nächsten Adresse relativ zur aktuell bearbeiteten Adresse (Sonderform der relativen Addressierung)
- virtuelle Adressierung: Ansprechen von Speicherbereichen außerhalb des Hauptspeichers (Ein-/Auslagern der Daten)

# Sprachen

## Syntax einer Programmiersprache

- Die Syntax einer Sprache bezeichnet die durch die Zeichen und Regeln einer Sprache entstehenden Konstrukte
- Für eine Überprüfung auf Korrektheit der Syntax muss diese durch Automaten oder Grammatiken formal beschrieben werden
- Bei der Programmierung wird diese Überprüfung durch den Compiler durchgeführt
- Sollte der Programmcode nicht der Syntax (den Regeln der Programmiersprache) entsprechen, kann dieser nicht compiliert werden

### Grundlegende Begriffe

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

## Darstellungsmöglichkeiten zur Sprachbeschreibung

### Grammatiken

- Regelwerk, das festlegt, welche Zeichen und Zeichenreihen zu einer Sprache gehören.
- Definierung von Programmiersprachen erfolgt über präzise Grammatiken

**Bestandteile einer Grammatik**

$$G = {T,V,S,P}$$

- Menge $T$ von **Terminalsymbolen**: unveränderliche und unteilbare Bestandteile der Sprache
- Menge $V$ von **Nichtterminalsymbolen**: Zeichen und Zeichenfolgen, die nach den Regeln der Grammatik gebildet werden können
- Menge $P$ von **Grammatikregeln**: Regeln, die festlegen wie aus Terminalsymbolen und/oder Nichtterminalsymbolen neue Konstrukte (Nichtterminalsymbole) gebildet werden können
- Das **Startsymbol** $S$: Nichtterminalsymbol, aus dem alle Worte der Sprache abgeleitet werden

### Backus-Naur-Form

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

### Einfache Syntaxdiagramme

- die BNF kann leicht in Diagramme übertragen werden
- Terminalsymbole werden in Kreise eingeschlossen
- Nichtterminalsymbole werden in Rechtecke eingeschlossen
- Ersetzungswege werde durch Pfeile dargestellt

![Beispiel eines BNF-Diagramms](https://steve2955.github.io/dhge-pi19-sem2/INV/IMG/BNF-Diagramm.JPG)

### Übung BNF

Grammatik für die Definition eines Funktionsprototypen (ähnlich der Definition von Funktionsprototypen)

```
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
```

### Sprachbeschreibung mittels Regulärer Ausdrücke

- Reguläre Ausdrücke können reguläre Mengen beschrieben

**Definition einer regulären Menge**

- $\emptyset \in R$; die leere Menge ist regulär
- $\{\epsilon\}\in R$; die Menge, die das leere Wort enthält ist regulär
- $\{a\}\in R \forall a \in A$
- Vereinigungen und Konkatenation von regulären Mengen sind ebenfalls regulär
- Eine Menge ist genau dann regulär, wenn sie in endlich vielen Schritten aus diesen Regeln gewonnen werden kann

**Konkatenation**
- $(p)^{\ast}$: Konkatenation von $p$ mit sich selbst
- $(pq)$: Konkatenation von $P$ und $Q$

**Vereinigung**
- $p \lor q$: Vereinigungsmenge von $P$ und $Q$

**Beispiel**
Alphabet $A=\{a,b\}$, dessen Worte weder **aa** noch **bb** enthalten

$$L \subset A^{\ast}=(ab)^{\ast}\lor(ba)^{\ast}\lor a(ba)^{\ast} \lor b(ab)^{\ast}$$

### Sprachbeschreibung mittels deterministischer Automaten

- Beschreibung von Sprachen mittels deterministischer Automaten ist sehr aufwendig
- Bestandteile:
	- I,O: Ein- und Ausgabealphabet
	- Q: endliche Menge an Zuständen, in denen sich der Automat befinden kann
	- $\partial$: Überführungsfunktion, die in Abhängigkeit von einem gelesenen Zeichen und dem aktuellen Zustand in einem anderen Zustand überführt
	- $q_0 \in Q$: Startzustand des Automaten
	- $F \subset Q$: Teilmenge aller Endzustände, bei deren Erreichen der Automat eine erfolgreich abgearbeitete Aufgabe anzeigt

**Beispiel**
Automat, der nur dessen Worte akzeptiert, die weder **aa** noch **bb** enthalten

![Beispiel eines Deterministischen Automaten](https://steve2955.github.io/dhge-pi19-sem2/INV/IMG/Deterministischer-Automat.JPG)

# Automaten

## Allgemeines

- keine technischen Geräte in der Informatik -> mathematische Modelle zur Umformung von Eingaben
- erkennende Automaten (Akzeptoren): Beschreibung von Sprachen
- Übersetzende Automaten (Tranduktoren): Umwandlung von Ein- in Ausgaben
- Automatentheorie definiert Lösbarkeit von Problemen mit Rechnern (Registermaschine/Turingmaschine)

## Funktionen

- Abbildung von Elementen einer Menge $A$ in eine Menge $B$ ($f: A\rightarrow B$)
- $A$ = Urbildbereich (Nicht jedem Element von A muss ein Element in B zugeordnet werden -> Definitionslücke)
- $B$ = Bildbereich
- Eine Funktion ist __injektiv__, wenn zwei unterschiedliche Werte aus A auch zwei unterschiedlichen Werte aus B zugeordnet werden
- Wenn jedes $b$ auch als Bild vorkommt, bezeichnet man die Funktion als __surjektiv__
- Ist eine Funktion sowohl __injektiv__ als auch __surjektiv__, so ist sie eindeutig umkehrbar und wird als __bijektiv__ bezeichnet

## Registermaschinen

- Registermaschine = Modell eines Automaten
- vereinfachtes Modell realer Rechner (Vorbild: Von-Neumann-Architektur)
- beinhaltet Befehlszähler, Akkumulator, Programm und endliche Anzahl von Registern
- jedes Register kann eine beliebig große natürliche Zahl aufnehmen und unterstützt folgende Operationen:
	- Inkrement: Erhöhen des Wertes um 1
	- Dekrement: Vermindern des Wertes um 1
	- Test des Wertes im Register auf 0
- eine Registermaschine besitzt $m$ Register und berechnet die Funktionen $f:N^r_0 \rightarrow N^s_0 \text{mit} r,s \leq m$
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

### Definition einer Registermaschine

$$R_m=(F,T,P,\delta)$$

- Menge der Inkrement/Dekrement-Operationen $F$

$$\begin{matrix}
F= \{A_1,\dots,A_m,S_1,\dots,S_m\} \\
i \in \{1,\dots,m\}
A_i: N^m_0 \rightarrow N^m_0 \qquad Ai(x_1,\dots,x_m)=x_1,\dots,x_{i-1},x_i\ +1,x_{i+1},\dots,x_m) \text{und} \\
S_i: N^m_0 \rightarrow N^m_0 \qquad Si(x_1,\dots,x_m)=x_1,\dots,x_{i-1},x_i\ -1,x_{i+1},\dots,x_m) \text{mit} \\
x-1 = \begin{cases} x-1 & \text{falls} x \geq 0 \\0 & \text{sonst.}\end{cases}
\end{matrix}$$

- Menge der Booleschen Funktionen $T$: Testen ob der Wert eines Registers 0 ist

$$\begin{matrix}
T= \{T_1,\dots,T_m\} \\
i \in \{1,\dots,m\}\\
T_i: N^m_0 \rightarrow \{true,false\};\\
T_i(x_1,\dots,x_m) = \begin{cases} true & \text{falls}\ x_i = 0 \\false & \text{sonst.}\end{cases}
\end{matrix}$$

- Menge der Anweisungen $P$: Programm

$$\begin{matrix}
P \subset & N_0 \times F \times N_0 & \cup & N_0 \times F \times N_0\\
& (i,f,j) & & (i,t,j,k)
\end{matrix}$$

- Überführungsfunktion $\delta$: Beschreibt die Arbeit der Registermaschine (Steuerwerk)

$$\delta: N_0 \times N^m_0 \rightarrow N_0 \times N^m_0$$

**Beispiel**

Programm, dass zwei Zahlen subtrahiert:

```Javascript
0: IF T2 THEN GOTO 3 ELSE GOTO 1
1: DO S1 ; GOTO 2
2: DO S2 ; GOTO 0
```

### Technische Umsetzung

- bisher: Jedes Register implementiert alle Rechenoperationen (-> sehr aufwendig)
- Einführung von speziellen Registern für bestimmte Registeroperationen: Akkumulatoren (+ Befehlszähler)
- Für das Ausführen einer Operation wird der Wert eines Register zunächst in einen Akkumulator geladen und Anschließen wieder zurückgespeichert
- Register, Befehlszähler und Akkumulator können jeweils beliebig große natürliche Zahl aufnehmen
- Programm = endliche Folge von Befehlen einer festgelegten Befehlsliste
- Solche Erweiterung einer Registermaschine mit wahlfreiem Zugriff auf Speicherzellen = Random Access Machine (RAM)

**Beispielbefehle:**

- Operationen mit Registern/Konstanten/indirekt adressierten Operanden
- Sprungbefehl
- Halt-Befehl


- Befehlssatz ähnelt einem abstrakten Assembler
- Unterschiedliche Programme und Algorithmen realisierbar
- Zeichen nach einer bestimmten Vorschrift als Zahlen codiert werden -> RAMs können auch Alphabete verarbeiten

# Turing-Maschinen

## Deterministische Turing-Maschinen

- Turingmaschine = universelles Automatenmodell
- Bestandteile:
	- unendliches Band (= Speicher): einzelne Zellen enthalten Symbole aus einem endlichen Bandalphabet **B**
	- Lese/Schreibkopf: Liest/Schreibt den Inhalt einer Speicherzelle
	- Befehlszähler: endliche Menge von Zuständen **Q**
	- Programm: Zustandsüberführungsfunktion

$$T=(I,B,Q,\delta,q_0,F)$$

- Eingabealphabet: $I \subset B$
- Bandalphabet: $B$
- endliche Menge an Zuständen: $Q$
- Startzustand: $q_0$
- Menge der möglichen Endzustände: $F \subset Q$
- Zustandsüberführungsfunktion: $\delta$

Turing-Maschinen können entweder Funktionen berechnen oder entscheiden, ob bestimmte Eingabeworte als Worte einer Sprache akzeptiert werden. Dabei gelten die folgenden Definitionen:

- Funktion $f:I^*\rightarrow I^*$ heißt total rekursiv (berechenbar), wenn eine Turing-Maschine existiert, die aus einer Eingabe $x$ den Funktionswert $f(x)$ berechnet

- Funktion $f:N^k\rightarrow N$ heißt total rekursiv, wenn eine Turing-Maschine existiert, die für Eingaben vom Typ $bin(i_1), bin(i_2), \dots, bin(i_k)$ mit einem Ergebnis $bin(m)$ stoppt, wenn $m = ƒ( i_1, \dots , i_k)$

- Eine Sprache $L \subset I^*$ heißt rekursiv (entscheidbar), wenn eine Turing-Maschine existiert, die für alle Eingaben stoppt und das Eingabewort $w$ akzeptiert, wenn $w \in L$

- Eine Sprache $L \subset I^*$ heißt rekursiv aufzählbar (semientscheidbar), wenn eine Turing-Maschine existiert, die genau die Eingaben $w$ akzeptiert, die aus $L$ sind

Für rekursiv aufzählbare Sprachen muss die Turing-Maschine nicht in jedem Fall stoppen (sie darf aber keine fehlerhaften Worte der Sprache zuordnen)

Die Überprüfung der Funktionsweise einer Turing-Maschine kann durch Konfigurationen erfolgen. Eine Konfiguration ist die Momentaufnahme der Arbeit einer Turing-Maschine.

Bsp.: ``` #q0abbaba# |-- #aq0bbaba# |-- #abq1baba# |-- #abbq2aba# ... ```

Zeichen für endlich viele Rechenschritte: ``` |--* ```


### Beispiel

Turing-Maschine, die nur Worte akzeptiert, bei denen maximal zwei aufeinanderfolgende b vorkommen dürfen

$$T=(I,B,Q,\delta,q_0,F)$$
$$I=\{a,b\}; B=\{a,b,\#\}$$
$$Q=\{q_0,q_1,q_2,q_3\}; F=\{q_3\}$$
$\delta:$
| $q$    | $a$      | $\delta(q,a)$ |
|--------|----------|---------------|
| $q_0$  | $a$      | $q_0,R$       |
| $q_0$  | $b$      | $q_1,R$       |
| $q_0$  | $\#$     | $q_3,N$       |
| $q_1$  | $a$      | $q_0,R$       |
| $q_1$  | $b$      | $q_2,R$       |
| $q_1$  | $\#$     | $q_3,N$       |
| $q_2$  | $a$      | $q_0,R$       |
| $q_2$  | $b$      | $q_2,N$       |
| $q_2$  | $\#$     | $q_3,N$       |
| $q_3$  | $a,b,\#$ | $q_3,N$       |

![Beispiel der Turing-Maschine](https://steve2955.github.io/dhge-pi19-sem2/INV/IMG/Turing-Beispiel.JPG)

### Mehrspurmaschine

- Erweiterung der Turing-Maschinen: Ersetzung von $B$ durch $I \cup B^k$ ($k$ = Anzahl der Spuren)
- Verwendung für mehrere Operanden (z.B. Addition: Spur für jeden Summanden, für die Summe, eventuell für Zwischenrechnungen)

## Nichtdeterministische Turing-Maschinen

- formelle Definition identisch zu deterministischen Turingmaschinen
- können ausgehend von einem Zustand und einem Zeichen in mehrere Zustände übergehen (Auswahl willkürlich)
- __"Orakel"__ sorgt für Wahl des kürzesten Weges
- Ein Wort $w$ wird von einer nicht deterministischen Turing-Maschine akzeptiert, wenn es mindestens einen akzeptierten Rechenweg gibt
- Universelle nicht deterministische Turing-Maschinen nicht realisierbar (kein "allgemeines Orakel")

## Churchesche-These

__Die durch formale Definition der Turing-Berechenbarkeit erfasste Klasse von Funktionen stimmt mit der Klasse der intuitiv berechenbaren Funktionen überein.__

Jede berechenbare Funktion kann als Turing-Maschine abgebildet werden. Die These ist derzeit nicht beweisbar (könnte höchstens widerlegt werden).
Es gibt kein automatisches Verfahren für die Überprüfung der Korrektheit beliebiger Programme (Halte-Problem)

## Übung: Inkrementmaschine

|                       | q      | 0/1  | $\delta(q,0/1,a)$ |
|-----------------------|--------|------|-------------------|
| Nach rechts "wandern" | $q_0$  | $0$  | $q_0,0,R$         |
|                       | $q_0$  | $1$  | $q_0,1,R$         |
|                       | $q_0$  | $\#$ | $q_1,\#,L$        |
| Addition              | $q_1$  | $0$  | $q_2,1,L$         |
|                       | $q_1$  | $1$  | $q_1,0,L$         |
|                       | $q_1$  | $\#$ | $q_3,1,N$         |
| Nach links "wandern"  | $q_2$  | $0$  | $q_2,0,L$         |
|                       | $q_2$  | $1$  | $q_2,1,L$         |
|                       | $q_2$  | $\#$ | $q_3,\#,R$        |
| Fertig                | $q_3$  | $*$  | $q_3,*,N$         |


# Endliche Automaten

## Schaltwerke und endliche deterministische Automaten

- Hardware besteht aus festverdrahteten Schaltkreise (realisieren Befehlssatz eines Mikroprozessors)
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

**Beispiel**

Automat, der nur Worte akzeptiert, die weder aa noch bb enthalten.

$$M = (Q, I, q_0, \delta, F)$$

$$Q=\{q_0,q_1,q_2,q_3\}; I=\{a,b\}; F=\{q_0,q_1,q_2\}$$

$$\delta = \{(q_0,a,q_1), (q_0,b,q_2), (q_1,a,q_3), (q_1,b,q_2), (q_2,a,q_1), (q_2b,q_3), (q_3,a,q_3), (q_3,b,q_3)\}$$
