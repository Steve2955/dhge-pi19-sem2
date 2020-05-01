# Algorithmen und Datenstrukturen

## Listen

- Liste = Datentyp bestehend aus Elementen und Operationen
- Eigenschaften einer Liste unterscheiden sich je nach Sprache -> Typsystem
	- Listen mit Elementen gleichen Typs
	- Listen mit Elementen unterschiedlichen Typs (verallgemeinerte Listen; wenn Listen weitere Listen enthalten entsehen Bäume)
- eindimensionale Datenstruktur (nur ein Nachfolger/Vorgänger) -> __Lineare Liste__
- Anordnung der Elemente sortiert oder unsortiert
- Zugriff auf Elemente erfolgt:
	- Nach Positionsangabe (Pointer/Index)
	- Nur am Ende (Stack)
	- Nur am Anfang (Queue)
- Liste ist rekursiver Datentyp
	- die Liste leer
	- die besteht aus einem (Kopf-) Element und einer (Rest-) Liste
- Denkbare Operationen: Liste erzeugen, durchlaufen, sortieren, verketten, umkehren; Element hinzufügen, entfernen

### Implementierung von Listen

- Um Listen zu Implementieren wird ein Element mit seinen entsprechenden Daten und einem Pointer (Verkettung) auf ein nächstes und oder vorheriges Element deklariert
	- einfach Verkettete Liste: jedes Element besitzt einen Pointer auf seinen Nachfolger
	- doppeltverkettete Liste: jedes Element besitzt einen Pointer auf seinen Vorgänger und seinen Nachfolger
- Pointer auf den Beginn der Liste zeigt auf des Erste Element
- Ende der Liste ist durch NULL-Pointer markiert (bei ringförmigen Listen Pointer auf erstes Element)

### Organisationsformen von Listen
- Pointer auf erstes Element; letztes Element durch NULL markiert
- Pointer auf erstes und letztes Element; letztes Element zusätzlich durch NULL markiert
- Pointer auf Dummy am Anfang und am Ende der Liste (letzter Dummy durch NULL markiert)
- Pointer auf Dummy am Anfang und am Ende der Liste (letzter Dummy zeigt auf letztes richtiges Element)
- Ringförmige Verkettung: Pointer auf Erstes Element; Letztes Element zeigt auf Erstes

### Keller (Stack) und Stapel (Queue)

- Keller: nur am Ende der Liste wird ein- und ausgespeichert (LIFO)
	- push/pop zum Ein-/Auspeichern
	- top als oberstes Element
- Schlange: an einem Ende der Liste wird eingespeichert, am anderen wird ausgespeichert (LILO)
	- enqueue zum Anstellen
	- dequeue zum Drankommen

## Graphen

### Definition

Ein **Graph** G ist ein Tupel $(V,E)$, wobei $V$ eine endliche Menge von **Knoten**(vertices) und $E$ eine Menge von **Kanten**(edges) bezeichnet. Eine Kate $\{a,b\}$ verbindet die zwei benachbarten Knoten $a,b$. Man sagt auch $a$ und $b$ sind adjazent. Diese Knoten heißen **Endkoten** der Kante. Als Vereinfachte Schreibweise wird oft lediglich $ab$ verwendet. Ein **Teilgraph** entsteht, wenn Knoten oder Kanten eines gegebenen Graphen entfernt werden. Es gibt keine spezielle geometrische Anordnung der Knoten und Kanten.

### Grundbegriffe

#### Knoten und Kanten**
Ein Graph kann zwischen $0$ und $V(V-1)/2$ Kanten haben. Er heißt **vollständig**, wenn alle Knoten untereinander mit Kanten verbunden sind. Fehlen wenige der möglichen Kanten, so wird er als **dicht** bezeichnet und sind nur wenige Kanten ($< V log V$) vorhanden, wird er **licht** genannt.

Ein Knoten $v$ und eine Kante $e$ heißen **inzident**, wenn $e$ den Knoten $v$ mit einem anderen Knoten verbindet. Der **Grad** eines Knoten entspricht der Anzahl der Kanten, die inzident mit dem Knoten sind. Ein Knoten heißt **isoliert**, wenn sein Grad gleich Null ist. In jedem Graphen ist die Anzahl der Knoten mit ungeradem Grad gerade. Die Summe über alle Grade der Knoten ist gleich 2-mal die Anzahl der Kanten.

#### Äquivalente Graphen

Zwei Graphen $G_1=(V_1,E_1)$ und $G_2=(V_2,E_2)$ heißen **äquivalent**, falls sie bis auf Benennung der Knoten gleich sind. Es gibt eine bijektive Abbildung $F: G_1 \rightarrow G_2$, sodass $a,b \in E_1$, genau dann, wenn $f(a),f(b) \in E_2$

**Reihenfolge zur Bestimmung der Äquivalenz zweier Graphen**
- Anzahl der Knoten und Kanten vergleichen
- Anzahl der Knoten mit entsprechendem Grad vergleichen
- bijektive Abbildung finden

#### Wege und Kreise

- **Kantenzug:** Folge von inzidenten Kanten
- **Weg/Pfad:** Kantenzug, bei dem alle vorkommenden Knoten unterschiedliche sind
- **Kreis/Zyklus:** geschlossener Weg
- **Hamilton-Kreis:** Kreis, der jeden Knoten genau einmal enthält
- **Euler-Zug:** geschlossener Kantenzug, der jede Kante des Graphen genau einmal enthält
- **Baum:** Graph ohne Zyklen
- **Wald:** Gruppe nicht zusammenhängender Bäume
- **Spannbaum:** Teilgraph eines Graphen, der alle Knoten enthält, aber die Kanten so reduziert, dass ein Baum entsteht

#### Zusammenhängende Graphen

- **zusammenhängender Graph:** jeder Knoten kann durch ein Weg mit jedem verbunden werden
- ein ungerichteter Graphe ist zusammenhängend, wenn er einen Spannbaum enthält
- ein Graph mit mehr als $\frac{(n-1)(n-2)}{2}$ Kanten ist zusammenhängend
- ein Graph, der nicht zusammenhängend ist, setzt sich aus zusammenhängenden Komponenten zusammen

#### Gerichtete Graphen

- **gerichteter Graph**: Tupel $(V,E)$ (auch Digraph), wobei $V$ eine endliche Menge von __Knoten__ und $E$ die Menge von __Kanten__

$G=(V,E)|E=\{a,b\}$ mit $a,b \in V$

- bei gerichteten Graphen gilt $ab \neq ba$ (eignen sich daher besonders zur Darstellung zweiseitiger Relationen)

#### Gewichtete Graphen

- **gewichteter Graph:** Tripel $(V,E,w)$, wobei $w$ eine Gewichtsfunktion  der Form $w:E\rightarrow R \quad w:V\rightarrow R$ darstellt
- **Kantengewicht:** Gewicht einer Kante $e \in E$, dass mit $w(e)$ oder $w_e$ bezeichnet wird
- **Knotengewicht:** Gewicht eines Knoten $v \in V$, dass mit $w(v)$ oder $w_v$ bezeichnet wird

### Computerdarstellung

- Mengen sind keine geeigneten Datenstrukturen zur Darstellung von Graphen
- Geeignete Strukturen: Adjazenzmatrizen für dichte, vollständige Graphen oder Adjazenzlisten für lichte Graphen

#### Adjazenzmatrix

Die Adjazenzmatrix für den Graphen $G=(V,E)$ mit $V=\{v_1,\dots,v_n\}$ ist eine $n \times n$ Matrix, die an der Stelle $[i,j]$ eine $1$ enthält, wenn die Knoten $v_i$ und $v_j$ adjazent sind. Die Adjazenzmatrix eines ungerichteten Graphen ist stets symmetrisch.

#### Adjazenzliste

Die Adjazenzliste für den Graphen $G= (V,E)$ ordnet jedem Knoten $v$ die List der zu ihm adjazenten Knoten zu. (z.B. Knotenindiziertes Array mit dynamischen Listen)

### Elementare Algorithmen

#### Tiefensuche

- depth first search: DFS
- bietet sich oft für Zusammenhangsprobleme an

**Algorithmus**

- Wahl eines Startknoten $v$
- Markieren des Knoten $v$ (durch Einfärben oder Verwalten eines Hilfsfeldes)
- rekursiver Aufruf für alle nicht markierten Nachbarknoten $w$ von $v$

Rekursion kann durch Verwendung eines Stapels beseitigt werden

#### Breitensuche

- breadth ﬁrst search: BFS
- gut geeignet für Distanzprobleme

**Algorithmus**

- Wahl eines Startknoten $v$
- Betrachtung jeder Kante $v,w$ mit der Überprüfung, ob $w$ schon besucht wurde
- Speicherung alles nicht besuchten Knoten $w$ in einer Warteschlange
- Rekursiver Aufruf mit erstem Knoten aus der Warteschlange

#### Zusammenhangskomponenten

Eine Tiefensuche kann in einem nicht zusammenhängenden Graph nur die Knoten markieren, die vom Startknoten aus erreichbar sind. Diese Knoten bilden eine Zusammenhangskomponente des Graphen. Damit die nächste Zusammenhangskomponente gefunden werden kann, muss aus den restlichen Knoten ein neuer Startknoten gewählt und das Verfahren wiederholt werden.

**Algorithmus zur Nummerierung der Knoten einer Zusammenhangskomponente**

- markiere alle Knoten mit $0$
- setze $c=0$
- durchlaufe alle Knoten $v$, wenn $v$ mit $0$ markiert ist, setze $c=c+1$ und führe eine Tiefensuche beginnend bei $v$ durch

#### Transitive Hülle

Die transitive Hülle einer (zweistelligen) Relation ist eine Erweiterung dieser Relation, die zusätzliche alle indirekt erreichbaren Paare enthält. Sie kann mit dem Warshall-Algorithmus berechnet werden.

**Warshall-Algorithmus**

Für alle Knoten $k = \{0,\dots,n-1\}$ des Graphen $G$ mit $V = \{0,\dots,n-1\}$ und alle Paare von Knoten $[i,j]$ erzeuge eine neue Kante $[i,j]$, wenn $[i,k]$ und $[k,j]$ Kanten sind.

#### Alle kürzesten Pfade

**Floyd-Algorithmus**

Für alle Knoten $k = \{0,\dots,n-1\}$ des Graphen $G$ mit $V = \{0,\dots,n-1\}$ und alle Paare von Knoten $[i,j]$ setzte die Entfernung zwischen auf die kleinere Entfernung aus [i,j] oder der Summe der Pfade $[i,k]$ und $[k,j]$.

#### Minimaler Spannbaum

Gesucht wird ein Teilgraph, der ein Baum ist und alle Knoten des Graphen enthält. Ein Spannbaum ist minimal, wenn das Gewicht der in ihm enthaltenen Kanten minimal ist.

**Algorithmus von Prim**

- Schrittweise Aufbau eines Baumes ausgehen von einem beliebigem Startknoten $S$
- Zu jedem Zeitpunkt bestehen drei disjunktive Mengen
	- Menge, der bereits zum Baum gehörenden Knoten
	- Menge, der benachbarten Knoten, die nicht zum Baum gehören
	- Menge, der Knoten, die nicht benachbart sind und kein Teil des Baum sind
- Bei jedem Schritt wird ein benachbarter Knoten $v$ gesucht, der durch eine minimales Gewicht mit dem Baum verbunden werden kann -> Hinzufügen zum Baum, Wiederholung des Schrittes

**Greedy-Strategie**

- zu jedem Zeitpunkt wird die Wahl getroffen, die das beste Ergebnis verspricht (minimales Kantengewicht)
- schnelle, oft aber keine optimale Lösung
