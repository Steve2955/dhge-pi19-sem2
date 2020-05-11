Algorithmen und Datenstrukturen
==================================

# Listen

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

## Implementierung von Listen

- Um Listen zu Implementieren wird ein Element mit seinen entsprechenden Daten und einem Pointer (Verkettung) auf ein nächstes und oder vorheriges Element deklariert
	- einfach Verkettete Liste: jedes Element besitzt einen Pointer auf seinen Nachfolger
	- doppeltverkettete Liste: jedes Element besitzt einen Pointer auf seinen Vorgänger und seinen Nachfolger
- Pointer auf den Beginn der Liste zeigt auf des Erste Element
- Ende der Liste ist durch NULL-Pointer markiert (bei ringförmigen Listen Pointer auf erstes Element)

## Organisationsformen von Listen
- Pointer auf erstes Element; letztes Element durch NULL markiert
- Pointer auf erstes und letztes Element; letztes Element zusätzlich durch NULL markiert
- Pointer auf Dummy am Anfang und am Ende der Liste (letzter Dummy durch NULL markiert)
- Pointer auf Dummy am Anfang und am Ende der Liste (letzter Dummy zeigt auf letztes richtiges Element)
- Ringförmige Verkettung: Pointer auf Erstes Element; Letztes Element zeigt auf Erstes

## Keller (Stack) und Stapel (Queue)

- Keller: nur am Ende der Liste wird ein- und ausgespeichert (LIFO)
	- push/pop zum Ein-/Auspeichern
	- top als oberstes Element
- Schlange: an einem Ende der Liste wird eingespeichert, am anderen wird ausgespeichert (LILO)
	- enqueue zum Anstellen
	- dequeue zum Drankommen

# Graphen

## Definition

Ein **Graph** G ist ein Tupel $(V,E)$, wobei $V$ eine endliche Menge von **Knoten**(vertices) und $E$ eine Menge von **Kanten**(edges) bezeichnet. Eine Kate $\{a,b\}$ verbindet die zwei benachbarten Knoten $a,b$. Man sagt auch $a$ und $b$ sind adjazent. Diese Knoten heißen **Endkoten** der Kante. Als Vereinfachte Schreibweise wird oft lediglich $ab$ verwendet. Ein **Teilgraph** entsteht, wenn Knoten oder Kanten eines gegebenen Graphen entfernt werden. Es gibt keine spezielle geometrische Anordnung der Knoten und Kanten.

## Grundbegriffe

### Knoten und Kanten

Ein Graph kann zwischen $0$ und $V(V-1)/2$ Kanten haben. Er heißt **vollständig**, wenn alle Knoten untereinander mit Kanten verbunden sind. Fehlen wenige der möglichen Kanten, so wird er als **dicht** bezeichnet und sind nur wenige Kanten ($< V log V$) vorhanden, wird er **licht** genannt.

Ein Knoten $v$ und eine Kante $e$ heißen **inzident**, wenn $e$ den Knoten $v$ mit einem anderen Knoten verbindet. Der **Grad** eines Knoten entspricht der Anzahl der Kanten, die inzident mit dem Knoten sind. Ein Knoten heißt **isoliert**, wenn sein Grad gleich Null ist. In jedem Graphen ist die Anzahl der Knoten mit ungeradem Grad gerade. Die Summe über alle Grade der Knoten ist gleich 2-mal die Anzahl der Kanten.

### Äquivalente Graphen

Zwei Graphen $G_1=(V_1,E_1)$ und $G_2=(V_2,E_2)$ heißen **äquivalent**, falls sie bis auf Benennung der Knoten gleich sind. Es gibt eine bijektive Abbildung $F: G_1 \rightarrow G_2$, sodass $a,b \in E_1$, genau dann, wenn $f(a),f(b) \in E_2$

**Reihenfolge zur Bestimmung der Äquivalenz zweier Graphen**

- Anzahl der Knoten und Kanten vergleichen
- Anzahl der Knoten mit entsprechendem Grad vergleichen
- bijektive Abbildung finden

### Wege und Kreise

- **Kantenzug:** Folge von inzidenten Kanten
- **Weg/Pfad:** Kantenzug, bei dem alle vorkommenden Knoten unterschiedliche sind
- **Kreis/Zyklus:** geschlossener Weg
- **Hamilton-Kreis:** Kreis, der jeden Knoten genau einmal enthält
- **Euler-Zug:** geschlossener Kantenzug, der jede Kante des Graphen genau einmal enthält
- **Baum:** Graph ohne Zyklen
- **Wald:** Gruppe nicht zusammenhängender Bäume
- **Spannbaum:** Teilgraph eines Graphen, der alle Knoten enthält, aber die Kanten so reduziert, dass ein Baum entsteht

### Zusammenhängende Graphen

- **zusammenhängender Graph:** jeder Knoten kann durch ein Weg mit jedem verbunden werden
- ein ungerichteter Graphe ist zusammenhängend, wenn er einen Spannbaum enthält
- ein Graph mit mehr als $\frac{(n-1)(n-2)}{2}$ Kanten ist zusammenhängend
- ein Graph, der nicht zusammenhängend ist, setzt sich aus zusammenhängenden Komponenten zusammen

### Gerichtete Graphen

- **gerichteter Graph**: Tupel $(V,E)$ (auch Digraph), wobei $V$ eine endliche Menge von __Knoten__ und $E$ die Menge von __Kanten__

$$G=(V,E); E=\{a,b\} \text{mit} a,b \in V$$

- bei gerichteten Graphen gilt $ab \neq ba$ (eignen sich daher besonders zur Darstellung zweiseitiger Relationen)

### Gewichtete Graphen

- **gewichteter Graph:** Tripel $(V,E,w)$, wobei $w$ eine Gewichtsfunktion der Form $w:E\rightarrow R \quad w:V\rightarrow R$ darstellt
- **Kantengewicht:** Gewicht einer Kante $e \in E$, dass mit $w(e)$ oder $w_e$ bezeichnet wird
- **Knotengewicht:** Gewicht eines Knoten $v \in V$, dass mit $w(v)$ oder $w_v$ bezeichnet wird

## Computerdarstellung

- Mengen sind keine geeigneten Datenstrukturen zur Darstellung von Graphen
- Geeignete Strukturen: Adjazenzmatrizen für dichte, vollständige Graphen oder Adjazenzlisten für lichte Graphen

### Adjazenzmatrix

Die Adjazenzmatrix für den Graphen $G=(V,E)$ mit $V=\{v_1,\dots,v_n\}$ ist eine $n \times n$ Matrix, die an der Stelle $[i,j]$ eine $1$ enthält, wenn die Knoten $v_i$ und $v_j$ adjazent sind. Die Adjazenzmatrix eines ungerichteten Graphen ist stets symmetrisch.

### Adjazenzliste

Die Adjazenzliste für den Graphen $G= (V,E)$ ordnet jedem Knoten $v$ die List der zu ihm adjazenten Knoten zu. (z.B. Knotenindiziertes Array mit dynamischen Listen)

## Elementare Algorithmen

### Tiefensuche

- depth first search: DFS
- bietet sich oft für Zusammenhangsprobleme an

**Algorithmus**

- Wahl eines Startknoten $v$
- Markieren des Knoten $v$ (durch Einfärben oder Verwalten eines Hilfsfeldes)
- rekursiver Aufruf für alle nicht markierten Nachbarknoten $w$ von $v$

Rekursion kann durch Verwendung eines Stapels beseitigt werden

### Breitensuche

- breadth ﬁrst search: BFS
- gut geeignet für Distanzprobleme

**Algorithmus**

- Wahl eines Startknoten $v$
- Betrachtung jeder Kante $v,w$ mit der Überprüfung, ob $w$ schon besucht wurde
- Speicherung alles nicht besuchten Knoten $w$ in einer Warteschlange
- Rekursiver Aufruf mit erstem Knoten aus der Warteschlange

### Zusammenhangskomponenten

Eine Tiefensuche kann in einem nicht zusammenhängenden Graph nur die Knoten markieren, die vom Startknoten aus erreichbar sind. Diese Knoten bilden eine Zusammenhangskomponente des Graphen. Damit die nächste Zusammenhangskomponente gefunden werden kann, muss aus den restlichen Knoten ein neuer Startknoten gewählt und das Verfahren wiederholt werden.

**Algorithmus zur Nummerierung der Knoten einer Zusammenhangskomponente**

- markiere alle Knoten mit $0$
- setze $c=0$
- durchlaufe alle Knoten $v$, wenn $v$ mit $0$ markiert ist, setze $c=c+1$ und führe eine Tiefensuche beginnend bei $v$ durch

### Transitive Hülle

Die transitive Hülle einer (zweistelligen) Relation ist eine Erweiterung dieser Relation, die zusätzliche alle indirekt erreichbaren Paare enthält. Sie kann mit dem Warshall-Algorithmus berechnet werden.

**Warshall-Algorithmus**

Für alle Knoten $k = \{0,\dots,n-1\}$ des Graphen $G$ mit $V = \{0,\dots,n-1\}$ und alle Paare von Knoten $[i,j]$ erzeuge eine neue Kante $[i,j]$, wenn $[i,k]$ und $[k,j]$ Kanten sind.

### Alle kürzesten Pfade

**Floyd-Algorithmus**

Für alle Knoten $k = \{0,\dots,n-1\}$ des Graphen $G$ mit $V = \{0,\dots,n-1\}$ und alle Paare von Knoten $[i,j]$ setzte die Entfernung zwischen auf die kleinere Entfernung aus [i,j] oder der Summe der Pfade $[i,k]$ und $[k,j]$.

### Minimaler Spannbaum

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

### Fluss in einem Netzwerk

#### Definition

- Ein **Netzwerk** ist ein zusammenhängender Graph, indem jede Kante $[i,j]$ mit einem Gewicht $w_{ij}$ (**Kapazität**) versehen ist und in dem es zwei (verschiedene) ausgezeichnete Knoten gibt: Die Quelle $q$ und die Senke $s$
- $f_{ij}$ wird **Fluss** genannt, falls der Fluss $f_{ij}$ entlang der Kante $[i,j]$ eine nichtnegative Zahl ist und die Kapazität der Kante nicht überschritten wird ($0 \leq f_{ij} \leq w_{ij}$)
- Kirchhoff'sches Gesetz: An jedem Knoten (außer Senke, Quelle) gilt: Fluss in den Knoten = Fluss aus dem Knoten
- Das zu transportierende Gut fließt von der Quelle über das Leitungsnetz zur Senke
- Jede Kante stellt einen Abschnitt dar; Knoten = Verbindung zwischen Abschnitten; Gewicht einer Kante = Kapazität/Zeiteinheit
- **innerer Knoten:** Knoten der weder Senke noch Quelle ist
- Aus der Quelle fließt netto ein Fluss $f$; innere Knoten können sich betragsmäßig nicht ändern; $f$ ist der **(Gesamt-)Fluss** durch das Netzwerk
- Neben einem Gewicht, besitzt jede Kante einen Fluss (An einem Knoten ist die Summe der Flüsse gleich)
- Ziel: Maximierung des Flusses durch das Netzwerk (Frage: Entspricht die Kapazität im Netzwerk der Kapazität an der Quelle/Senke?)
- **Ungerichteter Weg:** Weg bei dem Kanten in ihrer Richtung (**Vorwärtskante**) oder entgegengesetzt durchlaufen werden (**Rückwärtskante**)
- **Zunehmender Weg:** ungerichteter Weg von der Quelle zur Senke, bei dem keine Vorwärtskante ausgelastet ist ($f_{iv} < c_{ij}$) und durch alle Rückwärtskanten ein Fluss existiert ($f_{iv} > 0$)

### Vergrößerung des Flusses

- zur Maximierung des Flusses gilt es einen (ungerichteten) Weg zu finde, dessen sämtliche Kanten nicht ausgelastet sind (nur durch diese kann der Durchsatz erhöht werden)
- Der Fluss entlang eines zunehmenden Weges kann um $\Delta$ Einheiten vergrößert werden indem:
	- der Fluss entlang einer Vorwärtskante um $\Delta$ vergrößert und
	- entlang einer Rückwärtskante um $\Delta$ verkleinert wird
- Größtmögliche Zunahme ist das Minimum folgender Zahlen für alle Kanten $[i,j]$ eines Weges:

$$\Delta_{ij} = \begin{cases} c_{ij}-f_{ij}, & \text{Vorwärtskante}\\f_{ij}, & \text{Rückwärtskante}\end{cases}$$

- Der maximale Fluss ist genau dann erreicht wenn es keinen zunehmenden Weg von der Quelle zur Senke gibt

#### Ford-Fulkerson-Algorithmus

- Zuordnung eines Anfangsfluss $f_{ij} = 0$ für alle Kanten, Berechnung des Gesamtfluss $f$ des Netz
- Markieren der Quelle $q$ (alle anderen Knoten unmarkiert)
- Wähle einen Knoten $i$ mit der ältesten Markierung der noch nicht betrachtet wurde:
	- Wenn die Kante eine unausgelastete Vorwärtskante ist ($f_{ij} < c_{ij}$), berechne die mögliche Flusszunahme entlang der Kante $\Delta_{ij} = c_{ij} - f_{ij}$ und berechne damit: $$\Delta_j = \begin{cases} \Delta_{ij}, & \text{falls}\ i=q \\ \text{min}(\Delta_i,\Delta_{ij}), & \text{ansonsten}\end{cases}$$ und markiere den Knoten $j$ mit einem "Vorwärtslabel" ($i^+,\Delta_j$)
	- Wenn die Kante eine Rückwärtskante ist und $f_{ij}>0$, so berechne $$\Delta_j=\text{min}(\Delta_i,f_{ij})$$ und markiere den Knoten $j$ mit einem "Rückwärtslabel" ($i^-,\Delta_j$)
	- Wenn es keinen solche zu $i$ benachbarten Knoten $j$ gibt, dann kann der Durchlauf abgebrochen werden ($f$ ist der maximale Fluss)
- Wiederhole den vorherigen Schritt, bis die Senke s erreicht und $\Delta_s$ berechnet ist (zunehmender Weg von der Quelle zur Senke). Wird die Senke nicht erreicht, kann der Durchlauf abgebrochen werden ($f$ ist der maximale Fluss)
- Backtracking: Rekonstruiere den zunehmenden Weg mit Hilfe der Knotenmarkierungen ausgehend von der Senke; Vergrößere den Fluss entlang des zunehmenden Weges um $\Delta_s$ (neuer Gesamtfluss $f+=\Delta_s$); Wiederhole das Vorgehen ausgehend von der Quelle

### Systeme mit mehreren Quellen/Senken

- Darstellung eines neuen "fiktiven" Knoten $q_2$, der durch eine Kante mit unendlicher Kapazität mit $q_1$ verbunden ist ($q$ bleibt einzige richtige Quelle)
- Analoges Vorgehen bei mehreren Senken

### Kapazitätseinschränkung eines inneren Knoten

- Wenn der Knoten $x$ höchstens $c$ Einheiten weiterleiten kann, ersetzt man ihn durch zwei Knoten $x,x'$, die durch eine Kante der Kapazität $c$ verbunden sind
- In $x$ hineinführende Kanten werden weiterhin mit $x$ verbunden, herausführende mit $x'$

### Kapazitätseinschränkung von Quelle/Senke

- Wenn die Quelle $q$ höchstens einen Fluss $c$ in das System einbringen kann, fügt man einen "fiktiven" Knoten $q'$ hinzu, der durch eine Kante der Kapazität $c$ mit $q$ verbunden sind
- Analoges Vorgehen wenn die Senke nur eine bestimmte Kapazität aufnehmen kann

## Travelling-Salesman-Problem

- Besuchen aller Knoten mit minimalem Weg und Rückkehr zum ursprünglichen Knoten (Hamiltonkreis)
- Es gibt $(n-1)!$ mögliche Rundwege -> zu viele Möglichkeiten für brute-force Ansatz (Komplexität $O(n^3)$)
- TSP ist NP-vollständig: lässt sich nichtdeterministisch in Polynomialzeit lösen -> wahrscheinlich kein Algorithmus mit $O(N^k)$ möglich (polynomielle Komplexität)
- Folgender Ansatz: Minimum-Spanning-Tree-Verfahren ($O(n^2 log(n))$)

### Metrisches TSP

- Spezialfall des TSP (Kantengewichte in metrischen Größen): Annäherungsverfahren möglich, dessen Strecke höchstens doppelt so lang ist, wie optimal
- Eigenschaften einer metrischen Kantengewichtung $w$:
$$\begin{matrix}
w(i,j)=0 \leftrightarrow i=j \\
w(i,j)= w(j,i) \\
w(i,j)+w(j,k) \geq w(i,k)\\
\end{matrix}$$
- Alle Kantengewichte sind positiv und der Graph ist ungerichtet

### Minimum-Spanning-Tree

- Idee: optimale Tour = Hamilton-Kreis; durch Weglassen einer Kante wird ein Baum aufgespannt

**Verfahren**

- minimalen Spannbaum $M$ konstruieren
- Verdoppeln aller Kanten in $M$, finden eines Euler-Zuges
- Konstruieren eines Hamilton-Kreises: Entlanggehen am Euler-Zug (bereits durchlaufen Kanten überspringen)

**Praktische Grenzen der Berechenbarkeit**

- exakte Lösung nur durch Betrachtung aller Möglichkeiten
- Aufwand der Berechnung wächst exponentiell mit der Anzahl der Knoten(18 Knoten = 17 Billionen Möglichkeiten)

# Bäume

Bäume dienen der Beschreibung von Hierarchien

Beispiele:
- Stammbaum
- Verzeichnisstruktur
- Organigramm
- Inhaltsverzeichnisse

## Terminologie

- **Baum:** hierarchische Datenstruktur bestehend aus Kanten und Knoten
- **Kante:** Verbindung zweier Knoten
- **Knoten:** eingeteilt in innere und äußere Knoten
- **Innere Knoten:** Knoten mit Nachfolgerknoten, eventuell Vorgänger
- **Wurzel:** innerer Knoten ohne Vorgänger
- **Äußerer Knoten:** Knoten ohne Nachfolger (auch Blatt)
- **Pfad:** Kantenanzahl oder Knotenanzahl zwischen zwei Knoten (Richtung Blatt oder Wurzel)
- **(Baum-)Ebene:** Knoten einer Ebene besitzen die gleiche Pfadlänge zur Wurzel
- **Tiefe eines Knoten:** Pfadlänge zur Wurzel (oder Ebenen-Nummer)
- **Arboreszenz:** Kanten des Baum gerichtet -> Wurzel eindeutig identifizierbar (bei ungerichtetem Baum: jeder Knoten mögliche Wurzel)
- **Vorgänger:** benachbarter Knoten einer oberen Ebene
- **Nachfolger:** benachbarter Knoten einer unteren Ebene
- **Geschwister:** Knoten der gleichen Ebene mit gemeinsamem Vorgänger
- **Relation:** __direkt__ über eine Kante oder __indirekt__ durch Verbindung mit Vorgängern
- **Grad/Ordnung/Rang eines Knoten:** Anzahl der Nachfolger
- **Grad/Ordnung/Rang eines Baumes:** maximaler Grad im Baum (auch Verzweigungsgrad)
- **geordneter Baum:** feste Reihenfolge unter den Nachfolgern eines Knoten (linker, rechter Teilbaum)
- **Binärer Baum:** Baumgrad entspricht 2
- **Allgemeiner Baum:** Baumgrad > 2
- **Teilbaum:** alle Nachfahren eines Vaterknoten (direkt und indirekt)
- **Baumarten:**
	- **Statisch:** unveränderlicher Baum
	- **Dynamisch:** veränderlicher Baum
	- __Aussehen:__
		- **schief, degeneriert**
		- **voll/vollständig**
	- **Natürlich:** Baum mit beliebiger Schlüsselreihenfolge
- **voller Binärbaum:** Binärbaum, der alle möglichen Knoten besitzt
- **vollständiger Binärbaum:** Binärbaum, der bis zur vorletzten Ebene voll ist und dessen unterste Ebene auf einer Seite lückenlos mit Knoten besetzt ist (je nach Seite auch links-/rechtsvollständig)

## Definition

Ein Baum ist eine Menge von Knoten, von denen einer die Wurzel ist und die restlichen Knoten, aufgeteilt in $n \geq 0$ disjunkte Mengen, wobei jede dieser Mengen ein Teilbaum ist.

Ein Binärer Suchbaum hat entweder keine Knoten (leerer Binärbaum) oder besteht aus einem Tripel (linker binärer Teilbaum, Wurzeln, rechter binärer Teilbaum)

Schlüssel können innerhalb eines Baumes in inneren Knoten (Suchbaum), in Blättern (Blattsuchbaum) oder beidem gespeichert werden.

## Binäre Bäume

- Ein binärer Suchbaum ist geordnet
- Suche beginnt in der Wurzel: Betrag entscheidet, ob die Suche im linken oder rechten Teilbaum weitergeführt werden muss (erfolglose Suche endet in Blatt)

**Implementierungsmöglichkeiten**

- Reihung und Verbund (nicht für Suchbaum)
	- Baum: Knoten ebenenweise numeriert -> Index
	- Knoten in Reihung lückenlos gespeichert $$\begin{matrix}\text{Vorgänger von i}: i \text{DIV} 2 \\ \text{Nachfolger von}: 2*i, 2*i+1\end{matrix}$$
- Zeiger und Verbund
	- innerer Knoten als Verbund
	- Kante als Zeiger (Blatt mit NULL-Pointer)

## Baum durchlaufen (traversieren)

- systematische Betrachtung jedes Knoten eines Baumes (Ausgeben, Vergleichen, ...)
- Tiefendurchläufe (rekursiv oder iterativ)
	- Hauptreihenfolge (preorder - WLR)
	- Nebenreihenfolge (postorder - LRW)
	- Symmetrischer Reihenfolge (inorder - LWR -> sortiert)
- Breitendurchläufe: ebenenweise

**Euler-Tour** (Nichtrekursiver Tiefendurchlauf)

 Umlaufe Baum, halte Baum mit linker Hand, steige links ab

- Hauptreihenfolge: Merken eines Knoten bei erstem Besuch
- Nebenreihenfolge: Merken eines Knoten bei drittem Besuch
- Symmetrische Reihenfolge: Merken eines Knoten bei zweiten Besuch

## Arithmetische Ausdrücke als Baum

- Innere Knoten enthalten Operationen
- Blätter enthalten Operanden
- Übersetzungsprogramm erzeugt Baum und durchläuft diesen in NR bei Code-Erzeugung (Keller-Automat kann mit NR sofort rechnen)

## Analytische Betrachtung

### Vollständige Binärbaume

Ein Binärbaum heißt voll, wenn seine Höhe und sein kürzester Pfad (zwischen Wurzel und Blatt) gleich sind. Die Anzahl von Knoten auf einer Ebene ist $2^i,i \geq 0$, auf vorletzter Ebene $2∗2^{k−1}=2^k$ Kanten aus, an denen Knoten hängen.


| Höhe                  |             | h  | $h$               |
|-----------------------|-------------|----|-------------------|
| Blattzahl             | $2^h$       | ba | $h=log_2(ba)$     |
| Anzahl innerer Knoten | $2^h-1$     | ik | $h=log_2(ik+1)$   |
| Gesamtknotenzahl      | $2^{h+1}-1$ | gk | $h=log_2(gk+1)-1$ |

- Knotenanzahlen $gk, ik, ba$ lassen sich ineinander umrechnen
- Maximale Höhe eines Binärbaumes (wenn zur "Liste" entartet: $h=ik$
- Binärbaum minimaler Höhe muss ein vollständiger Binärbaum sein:  $h=\lceil ld(gk+1)\rceil −1$

### Interne Pfadlänge (Binärer Suchbaum)

- wie viele Vergleiche sind nötig, um jeden Schlüssel einmal zu finden: **Interne Pfadlänge**

$$ipl(b)=\sum_i k_E(i) * (i+1)$$

- $k_E(i)$ - Anzahl der inneren Knoten einer Ebene

### Interne Pfadlänge (Binärer Suchbaum)

Durchschnittliche Suchpfadlänge $dpl$ misst, wieviel Knoten bei erfolgreicher Suche besucht worden sind

$$dpl(b)=\frac{ipl(b)}{ik(b)}$$

### Maximale Anzahl von Suchschritten

Wie viele Vergleiche sind im ungünstigsten Fall notwendig um einen Schlüssel zu finden (Annahme: ausbalancierter Suchbaum)

$$S_{max}(n) = \lfloor ld n \rfloor +1$$

Suchaufwand: $O(log(n))$

## Ausgeglichene Binärbäume

- Zweck: Suchen, Einfügen und Entfernen in einem zufällig erzeugten binärem Suchbaum mit $n$ Schlüsseln stets in $O(log(n))$ Schritten ausführbar
- Zusätzliche Bedingung an die Struktur des Baums: Verhinderung von Degenerieren bei Einfügen/Entfernen

**AVL-Baum**

- Ein binärer Suchbaum heißt AVL-ausgeglichen (höhenbalanciert), wenn für jeden Knoten gilt, dass sich die Höhen seiner Teilbäume um 1 unterscheidet
- Balancierungsfaktor: $bal(k) = \text{Höhe des rechten TB} - \text{Höhe des linken TB}; bal(k)\in \{-1,0,1\}$

### Rebalancierungsoperationen  

- Rebalancierungsoperationen werden notwendig, wenn durch Einfügen/Entfernen die Rebalancierungsbedingung verletzt wird
- Rebalancieren = Umhängen von Teilbäumen (Suchbaum bleibt erhalten)
	- (Einfach)Rotation: Ein Teilbaum muss "umgehangen" werden
	- Doppelrotation: Zwei Teilbäume muss "umgehangen" werden (an neuen inneren Knoten)

## Bruder-Baum

- **Bruder-Baum:** Binärbaum, bei dem unäre Knoten zugelassen sind
- **Unäre Knoten:** Innerer Knoten mit nur einem Nachfolger
- Ziel: Alle Blätter auf einer Ebene (zu viele unäre Knoten entarten Baum -> Einführung weiterer Bedingungen)

## Rot-Schwarz-Baum

Ein Binärbaum heißt **Rot-Schwarz-Baum**, wen für alle Knoten gilt:

- jeder Knoten ist schwarz oder weiß
- Wurzel und Blätter sind schwarz
- Ist ein Knoten rot, sind seine Nachfolger schwarz
- der Pfad eines Knoten zu jedem seiner Blattknoten enthält die gleiche Anzahl schwarzer Knoten (Schwarzhöhe/-tiefe)

## Vielwegsuchbaum

- Suchaufwand abhängig von Baumhöhe -> Suchbäume sollten möglichst flach sein
- Erreichbar, indem Grad > 2 (Bäume wachsen in die Breite)
- Vielwegsuchbaum verallgemeinert das Konstruktionsprinzip des binären Suchbaums: Invariante des Baumes

**B-Baum**

- spezielle Form des Vielwegsuchbaumes (auch ausgeglichener Mehrweg-Suchbaum)
- Problem: große Bäume können nicht komplett in den Hauptspeicher abgelegt werden (Ziel: Reduktion der Zugriffe auf Festspeicher)
- Definition:
	- Alle Blätter besitzen gleiche Tiefe
	- Jeder Knoten (außer Wurzel, Blätter) hat wenigstens $\lceil m/2 \rceil$ Nachfolger
	- Wurzel hat wenigstens 2 Nachfolger
	- Jeder Knoten hat höchstens $m$ Nachfolger
	- Jeder Knoten mit $i$ Nachfolgern besitzt $i-1$ Schlüssel

	$$sa = ba-1 \qquad sa \text{ - Schlüsselanzahl}; ba \text{ - Blattanzahl}$$

Minimale/Maximale Blätterzahl eines B-Baum der Ordnung $h$

$$N_{min}=2\left\lceil\frac{m}{2}\right\rceil^{h-1} \qquad N_{max}=m^h$$

-> Bei Überlauf muss Knoten geteilt werden


**Variationen**

- B-Baum der Ordnung $k$: Jeder Knoten hat höchstens $2k+1$ Nachfolger, jeder innere Knoten(außer Wurzeln) hat mindestens $k+1$ Nachfolger
- $B*$-Baum: Jeder Knoten (außer Wurzel) hat mindestens $(2m-1)/3$ Nachfolger

- $B^+$-Baum: Jeder innere Knoten besteht aus $m$ Suchschlüsseln und $m+1$ Pointern (zusätzlich auf Nachbarknoten)

**Zusammenfassung**

- Suchpfade kurz, aber sequentielle Suche in Knoten (trotzdem Nutzung Plattenspeicher)
- Linux nutzt $B^+$-Baum für ```btrfs```
	- direkt zugreifbarer Block wird Knoten (Innere Knoten = Index)
	- Blattknoten enthalten Dateien

## Breitendurchlauf

**Mit Hilfe einer Schlange**
- Teilbäume stellen sich an (beginnend bei Wurzel):
- Noch nicht besuchte Nachfolger stellen sich in der Schlange an
- Besuch des ersten Knoten aus der Schlange (entfernen aus dieser) + wiederholen
- Nach Durchlauf des gesamten Baumes ist die Schlange leer

## Blattsuchbäume

- innere Knoten enthalten "Wegweiser"
	- größter Schlüssel des linken Teilbaum oder
	- kleinster Schlüssel des rechen Teilbaum
- Suche analog zu Binärbäumen

# Sortieren

- zentrales Problem der Computeranwendung (grundlegende Voraussetzung für effizientes Suchen)
- Anwendung:
	- statistische Auswertung großer Datenmengen
	- Präsentation von Daten
	- Datenbankanwendungen (erfordern effiziente Zugriffe)
	- Teilschritt in anderen Algorithmen
- **internes Sortieren:** Datensatz vollständig im Hauptspeicher
- **externes Sortieren:** Datensatz zu groß für Hauptspeicher (Rückführung auf internes Sortieren -> Zerlegung in Teilschritte)
- Reihenfolge der Sortierung: aufsteigend
- Reihenfolge bei Mehrfachsortierung: Ergebnisse vorhergehender Sortierläufe bleiben erhalten (stabile Sortierung)
- Aufwand der Sortierarbeit steigt mit der Anzahl $N
 Elemente ($N$ = Problemgröße; Aufwand des Algorithmus steigt mit $N$)

## Ressourcenverbrauch

- Aufwandsabschätzung:
	- **worst case:** maximaler Aufwand für schlechtesten Fall
	- **best case:** minimaler Aufwand im günstigsten Fall
	- **average case:** mittlerer Aufwand (meist schwer berechenbar)
- Größenordnung des Aufwandes in Abhängigkeit von $N$ Schlüsseln

$$O(fkt(N))=O(N^2)$$

- Abstraktion durch konstanten Faktor: $O$-Kalkül

**Erreichbarer Minimalaufwand**

- Informationen über die Anordnung der Schlüssel werden allein aus Vergleichsoperationen bezogen
- Die für die Sortierung notwendige Anzahl der Vergleiche $v(N)$ beträgt mindestens $O(N log N)$
- Es gibt $N!$ mögliche Lösungen entsprechende der $N!$ Blätter eines Baumes bei $N$ Schlüsseln ($N!$ Permutationen)
- Höhe des Baumes entspricht Anzahl der Vergleiche
- Stirlingsche Formel für erreichbaren minimalen Aufwand:

$$N! \approx \sqrt{2N N}(\frac{N}{e})^N \rightarrow V(N) \approx N ld N \rightarrow O(N log N)$$

- wichtige Operation für Zeiteffizienz: __Vergleiche__
- bei Sortierung in Arrays: Austausche von Datensätzen (Listen: nur vertauschen der Referenzen)

## Klassifizierungskriterien für Sortieralgorithmen

**Abhängigkeit von der Größe des Arbeitsspeichers:** interne/externe Sortierung
**Methodische Unterschiede:** Vertauschen/Einfügen/Auswählen/mit o. ohne Vorsortieren/Rekursion/...
**nach Effizienz:** Laufzeitverhalten (O-Notation)/Speicherbedarf
**Stabilität der Sortierverfahren:** stabil: gleichrangige Schlüssel werden nicht vertauscht

## Problemspezifikation beim Sortieren von Datensätzen

- Behälter $R$ enthält $n$ Elemente der Form $r=\text{key}+w$
- Sortieren durch Ändern der Reihenfolge oder Angabe der Reihenfolge
- Sortierfunktion: $\text{sort}: R \rightarrow R'$
- Menge $M = \{\text{key}_1,\dots,\text{key}_n\}$; Reihenfolge in $R': r_i < r_j$


## Einfache Sortierverfahren

### Selection-Sort

- Idee: entferne jeweils das kleinste Element aus der Ausgangsfolge und füge es am Ende der Ergebnisfolge ein
- Selection-Sort ist terminiert (unsortierter Bereich verringert sich jeden Durchlauf)

**Algorithmus**

- setze $i = li$
- solange $i < re$
	- suche kleinsten key in [Ri.key ... Rre.key]; seine Position sei $i_{min}$
	- vertausche Ri mit $R_{i_{min}}$
	- erhöhe i um 1

**Diskussion**

- $N-1$ Durchläufe (in jedem Durchlauf $i$ $N-i$ Vergleiche)
- $N-1$ Swaps
- kein stabiles Verfahren ($3_1$ hinter $3_2$)
- Aufwandsabschätzung: $T_{worst}(n)=T_{best}(N)\rightarrow O(N^2)$

### Insertion-Sort

- Idee: Entnimm der Ausgangsfolge ein beliebiges Element und sortiere es in die (bereits sortierte) Ergebnisfolge
- Insertion-Sort ist terminiert (Ausgangsfolge wird bei jedem Durchlauf um ein Element verringert)

**Algorithmus**

- setze i = li + 1
- solange i <= re
	- speichere einzufügendes Element Ri in v
	- suche die Einfügeposition für v.key und verschiebe alle dazwischenliegenden Elemente um eine Position nach rechts
	- füge v an der frei geschobenen Position ein
	- erhöhe i um 1

**Diskussion**

- $N-1$ Durchläufe (in jedem Durchlauf $i$ $N-i$ Vergleiche)
- pro Durchlauf von Vorsortierung abhängige Anzahl von Vergleichen und Verschiebungen ($T_{worst}(n)\neq T_{best})
- stabiles Verfahren
- Aufwandsabschätzung: $T_{worst}(n)\rightarrow O(N^2); T_{best}(N)\rightarrow O(N); T_{avg}\rightarrow(N^2)$

### Bubble-Sort

- Idee: Vertausche benachbarte Schlüssel, wenn diese nicht in der gewünschten Reihenfolge sind
- Bubble-Sort ist terminiert (Sortierter Bereich wird in jedem Durchlauf vergrößert)

**Algorithmus**

- solange swap durchgeführt wurde
	- paarweises swap, wenn rechtes Element < linkes Element ist
	- m merkt sich Index des letzten swap, damit nächster Durchlauf bei m-1 endet

**Diskussion**

- In jedem Durchlauf wandert das größte Element an die richtige Stelle
- stabiles Suchverfahren, bei fast Vorsortierung trotzdem $n-1$ Durchläufe
- Aufwandsabschätzung: $T_{worst}(n)\rightarrow O(N^2); T_{best}(N)\rightarrow O(N); T_{avg}\rightarrow(N^2)$

### Vergleich

| Selection-Sort                                       | Insertion-Sort                                            | Bubble-Sort                                              |
|------------------------------------------------------|-----------------------------------------------------------|----------------------------------------------------------|
| - $\frac{N^2}{2}$ Vergleiche, aber nur $O(N)$ swaps  | - $\frac{N^2}{4}$ Vergleiche, aber auch $O(N^2)$ swaps    | - $T_{worst}\approx T_{avg}\rightarrow \frac{N^2}{2}N^2$ |
| - niedriger Austauschaufwand                         | - lineares Verfahren bei fast sortierten Dateien ($O(n)$) | - Vorsortierung sinnvoll                                 |
| - Vorsortierung nie sinnvoll                         | - Vorsortierung wird am Besten honoriert                  |                                                          |


## Sortierverfahren mit Vorsortierung

- Insertion-Sort und Bubble-Sort belohnen Vorsortierung

**Shell-Sort**

- Basis: Insertion-Sort

__Algorithmus__

- setze h auf Anfangswert der Distanzfolge
- repeat Schleife für aktuelles h
	- berechne ein neues h der Distanzfolge
	- while: damit k>=li bleibt, muss wegen k=k-h jetzt k>h sein
	- füge v an der frei geschobenen Position ein
	- erhöhe i um 1
- verkleinere h bis h=1 abgearbeitet ist

__Diskussion__

- Werte der Distanzfolge bestimmen Güter der Vorsortierung
- Laufzeitverhalten theoretisch schwer feststellbar (prinzipiell: $O(N^{1+e})$, experimentell: $O(N^{1.25})$)
- Shell-Sort ist terminiert (vgl. Insertion-Sort)
- kein stabiles Verfahren (swaps über weite Distanz)

## Effiziente Sortierverfahren

### Divide and conquer

- Teile und herrsche
- Vertreter:
	- Quick-Sort: Aufwendiger Divide-Schritt, trivialer Füge-Schritt
	- Merge-Sort: Trivialer Divide-Schritt, aufwendiger Füge-Schritt
- Laufzeitverhalten: $T_{worst}(n)\rightarrow O(N^2); T_{avg}\rightarrow(N log N)$

**Grundprinzip**

```
Divide: Zerlege Menge in zwei gleich große Teilmengen
Conquer: Sortiere jede Teilmenge
Fügen: Füge Teillösungen geordnet zusammen
```

### Quick-Sort

- Idee: wähle ein beliebiges Element x aus der Folge (= Pivotelement)
	- teile die Restfolge in zwei Teilmengen (LTM und RTM)
	- sortiere beide Teilmengen mit Quick-Sort (Rekursion)
- Auswahl des Pivot-Elements
	- für höchste Effizienz teilen in zwei gleichgroße Teilmengen
	- Verschiedene Strategien: R[li].key, R[re].key, R[(li+re) div 2].key, ...
- Termination: bei Partitionierung entstehende Teilmengen sind immer kleiner als die Ausgangsmenge bis zur einelementigen Liste
- kein stabiles Verfahren

**Algorithmus**

- Abbruch bei einelementiger bzw. leerer Menge
- setze Partitionierungsindizes L, R
- Wähle Pivot-Element (Index p)
- partitioniere:
	- prüfe Partitionierungsbed. linke Teilmenge
	- prüfe Partitionierungsbed. rechte Teilmenge
	- tausche Elemente, wenn notwendig
- $L>R$: Partitionierung fertig, 2 Teilmengen
- rekursiver Aufruf mit den beiden Teilmengen

**Aufwandsabschätzung**

- worst case: Conquer zerlegt eine Folge von $N$ Elementen rekursiv in 2 Folgen der Länge $1$ und $N-1$ ($T_{worst}\rightarrow O(N^2)$)
- best case: Conquer zerlegt eine Folge von $N$ Elementen rekursiv in 2 Folgen gleicher Länge ($T_{best}\rightarrow O(N log N)$)

### Merge-Sort

- Idee:
	- Zerlege die Ausgangsmenge rekursiv in 2 gleichgroße Teilmengen (bis einelementige Mengen)
	- Mische jeweils 2 benachbarte Teilmengen, sortiere dabei die Elemente
- Gut geeignet für Sortierung von Daten auf externen Medien
- Termination: durch sukzessive Teilung der Folge bis zu einelementiger Folge gesichert
- stabiles Verfahren
**Algorithmus**
- Abbruch bei einelementiger bzw. leerer Menge
- teile R[li]...R[re] in der Mitte m;
- sortiere rekursiv (linke, rechte Teilmenge)
- füge 2 Teilmengen zusammen

**Aufwandsabschätzung**

- worst case: $O(N log N)$
- worst = optimal (immer optimale Teilung)

### Heap-Sort

- Idee: Sortierung mittels eines spez. Binärbaums
- Grundprinzip: partielle Ordnung eines Baumes mit N Knoten (Schlüsseln)
$$k_i \geq \begin{cases} k_{2i} & 2i \leq N \\k_{2i+1} & 2i+1 \leq N \end{cases}$$
- Die sukzessive Entnahme des Wurzelknotens mit anschließendem Wiederherstellen der partiellen Ordnung erzeugt eine geordnete Folge
- Termination: unsortierte Menge nimmt kontinuierlich ab
- nicht stabil

**Algorithmus**

- solange R_Unsort nicht leer
	- entnimm R_Unsort Wurzelschlüssel und hänge ihn in R_Sort sukzessive am Ende an
	- Stelle danach wieder die Heap-Bedingung für R_Unsort her

**Diskussion**

- Baumstruktur: $j = ld(N+1)$ Ebenen -> garantiertes $O(N log N)$-Verfahren
- Durchschnittliche Zahl der Vergleiche: $2*N log N + O(N)$
- Laufzeitverhalten: $T_{worst}(n)\rightarrow O(N log N);$

### Radix-Sort

- Idee: Ausnutzen digitaler Darstellungs-Eigenschaften der Schlüssel (Schlüssel als Zahl zur Basis M) -> Betrachtung der einzelnen Ziffern
- Stabilität: bitweise Zerlegung -> Schlüssel mit i-ten Bit 0 vor Schlüsseln mit i-ten Bit 1 stabil angeordnet

***Diskussion***

- für N verschiedene Schlüssel werden im Dualsystem $b=ld(N)$ Bits benötigt
- Komplexität: $T=O(N log N)$ ($b*N$ Vergleiche)
- gut bei Zeichenketten fester Länge
- stabil und terminiert , weil Anz. von Bits und Keys begrenzt ist
- Effizienzproblem bei Vorsortierung
- Zusätzlicher Speicherplatz notwendig (exsitu)
- Umfangreiche innere Schleife des Verfahrens (deshalb kaum schneller als Quicksort)

# Suchen

- Suchen von einem Schlüssel (oder Vergleiche zwischen Schlüsseln) in einer Sequenz (Reihung/Liste)
- Elementare Suchverfahren, oder Suchverfahren, die:
	- spezielle Datenstrukturen verwenden (z.B. Bäume)
	- Schlüssel transformieren (z.B. Hashing)
	- mehrere Schlüssel verwenden

## Auswahlproblem

- Suche nach *i-kleinsten* oder *i-größten* Schlüsseln einer Sequenz (z.B. drittgrößter Schlüssel)
- **Verfahren:** Suche wiederholt nach dem kleinsten/größten Schlüssel der Liste, entferne den Schlüssel solange die gesuchte Tiefe nicht erreicht ist
- $N-1$ Vergleiche für jede Iteration nötig ($O(i*N)$)

## Sequentielle Suche

- **Voraussetzung:** Länge der Sequenz bekannt (keine Sortierung)
- **Algorithmus:** Durchlaufen der Sequenz, jeweils Vergleich mit Suchschlüssel (bis Fund oder Ende)
- **Aufwand:** max. $N+1$ Vergleiche

### Binäre Suche

- **Voraussetzung:** Länge der Sequenz bekannt, Sortierung
- **Algorithmus:** Suchbereich wird halbiert, mittlerer Schlüssel entscheidet welche Hälfte weiter rekutsiv durchsucht werden soll (= Suche im Binärbaum)
- **Aufwand:** $O(N log N)$

### Fibonacci-Suche

- Unterteilung des Suchbereiches entsprechend der Fibonacci-Zahlen
- **Algorithmus:** Suchbereich wird anhand der Fibonacci-Folge geteilt, Schlüssel entscheidet ob die Folge fortgesetzt oder zurückgesetzt wird
- **Aufwand:** $O(N log N)$

### Exponentielle Suche

- Verwendung bei sehr langen sortierten Sequenzen
- **Algorithmus:** Suchbereich wird an einer Grenze $i$ geteilt, Suche des Schlüssels, Verdopplung der Teilgrenze
- **Aufwand:** $O(N log N)$

### Interpolationssuche

- vgl. binäre Suche, aber verkleinern/vergrößern der "Hälften" mit Schätzfaktor
- z.B. Suche in alphabetischem Wörterbuch (Buchstabe "A" am Anfang)

## Selbstanordnende Listen

- Wird auf die Elemente einer Liste unterschiedlich häufig zugegriffen, sollten die am häufigsten genutzten am anfang stehen
- **Methoden:**
	- **Move to front:** gerade zugegriffenes Element an den Anfang
	- **Transpose:** gerade zugegriffenes Element wird mit vorhergehendem getauscht
	- **Frequency count:** Elemente mit Zugriffszähler, absteigende Sortierung

## Nichtelementare Suchverfahren

### Suchen mit Hash-Verfahren

- Finden eines Schlüssels in einer Datenstruktur mit möglichst wenig Vergleichen
- **Überlegungen:**
	- bei Kenntnis des Index: sofortiger Zugriff auf Element des Arrays (ohne Suche)
	- einzutragende Schlüssel meist kleiner als aufstellbare Schlüssel (-> Schlüsseltranformation)
- Bereich der Schlüsseltransformation: $0 \text{bis} m-1$ (= **Abbildung** Ganze Zahlen -> Index)
- Hash-Verfahren rechnet Schlüssel in ganze Zahlen um (Adresskollision muss behandelt werden)
- **Hash-Funktion:** bildet einen Schlüssel $k$ auf eine **Hash-Adresse** ab
- **Hash-Tabelle:** bezeichnung eines solchen Array mit dem Indexbereich $0 \text{bis} m-1$
- sind effizient, wenn zunächst viel eingefügt und dann viel gesucht wird (kein Entfernen)
- ist die Anzahl der möglichen Schlüssel gleich der Anzahl der Abbilder, kann eine eindeutige (bijektiv) Hash-Funktion aufgestellt werden
- Verschiedene Hash-Verfahren unterscheiden sich nach Hash-Funktion und Adresskollisionsbehandlung

**Problem**

- Hash-Funktion kann für verschiedene Schlüssel gleiche Hash-Adressen liefern (**= Synonyme**)
- Eine solche **Adresskollision** muss behandelt werden (für Unterscheidung muss Orignial-Schlüssel im Datensatz gespeichert werden)
- Hash-Funktion soll schnell berechenbar sein und Hash-Adressen gleichmäßig verteilen (Grundlegende Verfahren: Divisions-Rest-Methode, Multiplikative Methode)

**Belegungsfaktor**

Der **Füllfaktor** $\alpha=\frac{n}{m}$ beschreibt die Anzahl die in einer Hash-Tabelle belegten Adressen

#### Hash-Verfahren mit direkter Verkettung

- $C_n^+$: **Erwartungswert** für betrachtete Schlüssel bei **erfolgreicher Suche**
- $C_n^-$: **Erwartungswert** für betrachtete Schlüssel bei **erfolgslose Suche**
- Dem **Eintragen** eines Schlüssels geht eine erfolglose Suche voraus (alle Schlüssel werden betrachtet: $C_n^-=\alpha$)
- Dem **Entfernen** eines Schlüssels geht eine erfolgreiche Suche voraus (Durchschnittliche $C_n^+\approx 1+ \frac{\alpha}{2}$)

#### Offene Hashverfahren

- Prinzip: Finden der noch nciht besetzten Array-Elemente in der Hash-Tabelle nach festgelegter **Sondierungsfolge** $s(j,k)$ (ein Platz muss immer frei bleiben!)
- Lineares Sondieren: $s(j,k)=j$
- Quadratisches Sondieren: $s(j,k)=(\lceil\frac{j}{2}\rceil)^2 \times (-1)^j$
- Double Hashing: $s(j,k)= j \times h^'(k)$ (h' = 2. Hashfunktion)

### Fortsetzung

- Was wenn Hash-Tabelle voll ist? (offene Hash-Verfahren bis ca. 80..90% effizient)
- Lösung: **Dynamische Hash-Verfahren** -> Vergrößern der Hash-Tabelle
	- **Vergrößern von m**: Veränderung der Hash-Funktion
	- **Liste von Hash-Tabellen** (je m groß, max 90% gefüllt)
		- Durchsuchen durch sukzessives Suchen in den einzelnen Listen
		- Einfügen in der ersten nicht vollen Liste

## Suchen in Texten

- **Text:** nicht weiter strukturierte Folge von Zeichen eines endlichen Alphabets
- **Problem: Suche im Text**
	- geg.: Text und Muster
	- ges.: ein oder alle Vorkommen des Musters im Text
- **Match:** Übereinstimmung einer Teiltextzeichenkette
- **Mismatch:** Nichtübereinstimmung
- **Gesichtspunkt:**
	- statische oder dynamische Texte (bei statisch: Anlegen eines Index sinnvoll)
	- Suche nach einem oder mehreren Mustern
	- ist Vorverarbeitung sinnvoll

### Naive Suche

- Muster wird an jedem Zeichen des Textes nacheinander angelegt
- Es erfolgt jedes Mal ein Vergleich der Zeichen
- Verbesserung: Muster nur bis zum ersten Mismatch prüfen
- $O(n*m)$ Vergleiche

### Knuth-Morris-Pratt

- Nutzung der bei der Übereinstimmung von Zeichen gewonnen Informationen
- $O(n)$ Vergleiche
- Vorlauf: Analyse des Musters
	- **Präfix**, **Suffix**
	- **Rand** ($\text{Präfix}=\text{Suffix}\neq\text{Muster}$) und **Breite** des Randes
- Auf Basis dieser Informationen wird eine **Schiebedistanz** berechnet
	- = für jedes Präﬁx das Musters die Länge seines breitesten Randes
- Suche: zeichenweiser Vergleich
	- Bei Mismatch: Verschieben des Musters um die zuvor berechnete Schiebedistanz des entsprechenden Zeichen (bereits verglichene Zeichen müssen nicht erneut geprüft werden)
	- Bei Match: Ausgabe des Treffers

### Boyer-Moore

- Idee: Vergleich des Musters von rechts nach links

**Schlechtes-Zeichen-Strategie**

- Bei Mismatch: Verschieben des Musters
- Bei Zeichen, das nicht im Muster enhalten ist: Verschieben des Musters um $m$ Positionen

**Gutes-Zeichen-Strategie**

- Ableiten der größtmöglichen Schiebedistanz aus der Struktur des Musters (vgl. KMP, aber Suffix)
- schwierig zu verstehen und zu implementieren (wird meist weggelassen)

### Rabin-Karp

- Verfahren ähnelt naivem Algorithmus
- **Aber:** Vergleich der Signatur eines Textfenster mit dem Muster (bei Match: Bruteforce-Vergleich)
- Anforderungen an die Signaturfunktion: Vermeidung von Kollisionen, konstante Berechnungszeit -> Verwendung einer Hash-Funktion
- Inkrementelle Hashwert-Berechnung bei den Teilstrings sinnvoll
