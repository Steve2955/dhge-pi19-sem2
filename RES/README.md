Betriebssysteme - Zusammenfassung
=================================

# Grundlage

## Bits und Bytes

- **Bit:** kleinstmögliche Speichereinheit (8 Bit = 1 Byte)
- **Si-Präfixe:** 10er- Potenz als Basis (kb, MB, GB, TB, PB, ... -> $=10^x$ Byte)
	- Umrechnung innerhalb: mul. / div. mit $10^3$ (Exponent steigt / fällt um 3)
- **IEC-Präfixe:** 2er- Potenz als Basis (KiB, MiB, GiB, TiB, PiB, ... -> $=2^x$ Byte)
	- Umrechnung innerhalb: mul. / div. mit $2^{10}$ (Exponent steigt / fällt um 10)

| KB | $10^3$    | KiB | $2^{10}$ |
|----|-----------|-----|----------|
| MB | $10^6$    | MiB | $2^{20}$ |
| GB | $10^9$    | GiB | $2^{30}$ |
| TB | $10^{12}$ | TiB | $2^{40}$ |
| PB | $10^{15}$ | PiB | $2^{50}$ |
| EB | $10^{18}$ | EiB | $2^{60}$ |

### 10er Potenzen von Einheiten

| Yotta | $10^{24}$  |
|-------|------------|
| Zetta | $10^{21}$  |
| Exa   | $10^{18}$  |
| Peta  | $10^{15}$  |
| Tera  | $10^{12}$  |
| Giga  | $10^{9}$   |
| Mega  | $10^{6}$   |
| Kilo  | $10^{3}$   |
| Hekto | $10^{2}$   |
| Deka  | $10^1$     |
| Dezi  | $10^{-1}$  |
| Zenti | $10^{-2}$  |
| Milli | $10^{-3}$  |
| Mikro | $10^{-6}$  |
| Nano  | $10^{-9}$  |
| Piko  | $10^{-12}$ |
| Femto | $10^{-15}$ |
| Atto  | $10^{-18}$ |

## Aufbau eines Rechnersystems

- Hilfsprogramme: System-/Anwendersoftware
- Betriebssystem
- Mikroarchitektur/Gerätetreiber
- Physische Hardware

**Das Betriebssystem ist eine virtuelle Maschine, die von der Hardware abstrahiert**

## Aufgaben des Betriebssystems

- Bedienschnittstelle für Nutzer -> Programme (CLI/UI)
- Verstecken technischer Details/Automatisierung von Vorgängen
	- Abstraktion der HW (einfache Programmierschnittstelle)
	- Definition von Konzepten (Prozess, Datei, Speicher, ...)
	- Vermeidung von Fehlern (Schutz der HW -> Stabilität)
- Steuern von Abläufen/ Kontrollieren von Ressourcennutzung
	- quasiparallele Ausführung mehrere Prozesse (sichere Trennung)
	- Blockaden von Prozessen verhindern, CPU-Leistung zuweisen
	- effiziente, zuverlässige, sichere Verwaltung
- Dienste für Anwender/Anwendungsprogramme
	- Prozess-, Speicher-, Dateiverwaltung, E/A-Operationen, Interprozesskommunikation (über APIs realisiert)
- Privilegiensystem zum Schutz der Anwendungen untereinander (inkl. OS)
	- Kern-Modus: alle Rechte für Betriebssystem-Code
	- Benutzer-Modus: eingeschränkte Rechte für Anwendungs-Code
	- Schnittstelle zwischen Usermode und Kernel = **Traps** (Einstiegspunkte; vgl. Software-Interrupt)

## Das Betriebssystem in der Definition

**DIN 44300:** __Die Programme__ eines digitalen Rechnersystems __, die zusammen__ mit den Eigenschaften dieser Rechenanlage die Basis der möglichen Betriebsarten des digitalen Rechnersystems bilden und die insbesondere __die Abwicklung von Programmen steuern und überwachen__

## Betriebssystem als Schichten-/Schalenmodell

- Benutzer -> Programm -> Betriebssystem -> Hardware
- Jede Schicht wird durch die Menge an Operationen definiert, die sie bereitstellt (Schnittstelle)

| Vorteile | Nachteile |
|----------|-----------|
| - Reduzierte Komplexität (nur Betrachtung der Schnittstellen) | - erhöhte Komplexität der vertikalen Kommunikation (nur durch einzelne Schichten möglich)|
| - Austausch einzelner Schichten durch definierte Schnittstellen möglich (Gesamtsystem bleibt erhalten)| - Effizienz-, Reibungsverluste und lange Pfade |

## Arten von Betriebssystemen

- **Mainframe-Betriebssysteme:** Webserver/B2B-Anwendungen (hohe I/O-Bandbreite, meist Batchverfahren)
- **Sever-Betriebssysteme:** viele Nutzer über Netzwerk, Verteilung der Ressourcen
- **Multiprozessor-Betriebssysteme:** bündeln der Kapazität mehrerer Prozessoren (eng, lose o. Verteilte Systeme)
- **Betriebssysteme für den PC:** vernünftige Schnittstelle für Benutzer (Office, Internet, ...)
- **Echtzeitbetriebssysteme:** zeitkritische Anwendungen (z.B. Überwachung maschineller Fertigung)
- **Betriebssysteme für eingebettete Systeme:** minimale Systeme zur Überwachung/Steuerung anderer Geräte
- **Betriebssysteme für Chipkarten:** unterschiedliche Applikationen (Sicherheit wichtig)

## Klassifizierung von Betriebssystemen

- **Nach Betriebsart:** Netzwerk-, Realzeit- oder universale Betriebssysteme
- **Nach Anzahl der gleichzeitig laufenden Programme:** Einzel- (singletask) oder Mehrprogrammbetrieb (multitask)
- **Nach Anzahl der gleichzeitigen Nutzer:** Einzel- oder Mehrbenutzerbetrieb
- **Nach Anzahl der verwalteten Prozessoren:** Ein- oder Mehr-Prozessor-Betriebssystem

## Programmausführung und Hardware

### Grundmodell eines Rechners

- Basis: Von-Neumann-Architektur
- Unterteilung in einzelne Werke (Kommunikation über BUS-System)
- Prozessor-Speicher-Anbindung = "Von-Neumann-Flaschenhals" (Daten und Befehle über gemeinsamen BUS)
- **Steuerwerk:** Laden, Interpretieren und Steuerung der Ausführung von Befehlen aus dem Speicher
- **Rechenwerk:** Laden der Operanden aus dem Speicher -> Verarbeitung -> Ablage des Ergebnis im Speicher (Rechen- + Steuerwerk = CPU)
- **Speicher:** Maschinenbefehle und Daten in gemeinsamen Adressraum
- **Ein-/Ausgabe:** Verbindung mit Peripheriegeräten (Schnittstelle zur Umwelt)

### Befehlsausführung

- erfolgt in mehreren Schritten (FETCH -> DECODE -> EXECUTE) -> Pipeline
- Durchsatzerhöhung durch **Prefetching** (versetzte Verarbeitung mehrerer Befehle)
- $\text{Durchsatz}=\frac{1\text{Sekunde}}{\text{Bearbeitungszeit einer Stufe}}$

## Strukturen

- **Monolithischer Kern:** Menge von Programmen die sich gegenseitig aufrufen (meist evolutionär gewachsen; unklare Struktur; keine Abgrenzungen über Schnittstellen)
	- Vorteile: schneller Wechsel zwischen kernel- und usermode; aufwändige Kommunikation entfällt
	- Nachteile: mangelnde Robustheit, Modularität, Flexibilität
- **Mikrokern:** Nur zentralste Funktionen im Kernel (Nachrichten, Speicher-, Prozessorverwaltung), weitere durch Serverdienste realisiert (Filesystem, ...)
	- Vorteile: modulare Struktur, Gerätetreiber im usermode,  kleiner sicherheitskritischer Kern
	- Nachteile: hoher Kommunikationsaufwand, Synchronisation vieler Nutzer-Prozesse schwer optimierbar, Betriebssystemaufrufe ohne kernelmode schwer realisierbar
- **Makrokern:** Kompromiss, üblicherweise modular -> Module höherer Schichten nutzen Funktionen niederer Schichten
- **Virtuelle Maschine:** mehrerer logische Betriebssysteme auf gemeinsamer Hardware
	- durch Hardware: Ressourcen über Firmware des Rechners verwaltet; Gastbetriebssysteme erhalten Teile der physischen als virtuelle Hardware
	- durch Software: Kern ist Monitor für mehrere Betriebssysteme; virtuellen Maschinen erhalten exakte Kopien der Hardware
	- Vorteile: Reduzierung von Kosten+Aufwand; bessere Skalierbar- und Verfügbarkeit
	- Nachteile: komplex; Leistungsverluste; nicht jede Hardware emulierbar; Host-Ausfall = Ausfall mehrerer virtueller Server

# Schnittstellen

## Computergestützte Benutzerschnittstellen

### Kommandozeile

- Eingabe von Befehlen (Worte) zur Steuerung einer Software
- Kommandozeileninterpreter (Shell) ließt eine Zeile Text ein, interpretiert sie und führt sie aus
- **Vorteile:** schnelle, direkte Kontrolle; Erreichbarkeit; einfache Automatisierung
- **Probleme:** länderspezifische Textdarstellung und Eingabe
- Baudrate: Zeit für die Übertragung eines Zeichens
- Für Übung: beim Scrollen bleit immer eine Zeile stehen (+ es muss gescrollt werden)

### Grafikschnittstelle

- Bedienung von Software mittels grafischer Elemente
- wichtige Kriterien: Benutzerkontrolle, Rückkopplung, Visualisierung, Konsistenz, Einfachheit, Ästhetik
- **Vorteile:** leichter für weniger erfahrene Nutzer; ermöglicht WYSIWYG
- **Probleme:** Erfordert Verarbeitung großer Datenmengen; Einschränkung von Kontrolle und Erreichbarkeit

#### Color Lookup Table (CLUT)

- **Speicherbedarf ohne CLUT:** $\text{Speicherbedarf}=\text{Auflösung/Anzahl der Pixel} * \text{Speicherbedarf einer Farbe}$
- Farbtiefe: In der Regel werden RGB-Farben mit 8 Bit pro Farbanteil verwendet -> $3 * 8 \text{Bit}= 24 \text{Bit}$
- **Größe der CLUT:** $\text{Speicherbedarf der CLUT}=\text{Anzahl Einträge/versch. Farben} * \text{Speicherbedarf einer Farbe}$
- **Speicherbedarf mit CLUT:** $\text{Speicherbedarf}=\text{Auflösung/Anzahl der Pixel} * \text{Speicherbedarf für den Index der CLUT}$
- Wenn die CLUT z.B. $65538=2^{16}$ Einträge beinhaltet, bedarf die Speicherung eines Index $16 \text{Bit} = 2 \text{Byte}$

### API

- Kommunikation mit dem Betriebssystem (Systemfunktionen) und anderen Programmen/Bibliotheken
- Standard API stellt grundlegende Funktionen einer Programmiersprache bereit (I/O, Speicher, Math -> standardisiert -> Portable)
- Proprietär APIs (GUI, Multi-Threading, ... -> nicht standardisiert -> Kompatibilitätsprobleme)

# Prozess

- = Abstraktion eines laufenden Programms (Zustand + Ressourcen)

## Abgrenzungen

- Programm: statische Beschreibung eines sequentiellen Algorithmus
- Prozess: Programm in der Ausführung
- Thread: sequentieller Abarbeitungsablauf innerhalb eines Prozesses

## Eigenschaften

- parallele Ausführung mehrerer Prozesse (bei einem Prozessor simuliert -> Scheduler)
- jeder Prozess besitzt eigenen virtuelle Prozessor + Speicher (eigener Kontrollfluss)
- Prozesserzeugung: durch System/Nutzer oder bestehende Prozesse (fork -> Kennung, Speicherplatz, Rechenzeit)
- Prozessterminierung: freiwillig oder durch OS (bei Fehler/durch anderen Prozess)

## Prozessmodell

- Zustände: rechnend, rechenbereit (keine RZ zugeteilt), blockiert (warten auf externes Ergebnis)
- OS verwaltet Prozesstabelle (Infos+Zustand aller Prozesse)
- Prozesswechsel (durch Systemaufruf, Ausnahme oder Interrupt)
	- Zustand sichern, beenden/bereit setzen, Systemaufruf/Interrupt behandeln, Scheduler

## Threads

- Prozesswechsel = aufwändig -> Trennung der Aspekte
	- **Prozess:** Einheit des Ressourcenbesitzes und Schutzes
	- **Thread:** Einheit der Ausführung (Prozessorzuteilung)
- Thread hat Zugriff auf alle Ressourcen des Prozesses in dem er abläuft -> schnellerer Threadwechsel
- User-Thread (logische Realisierung) -> Kernel-Thread (Zuteiltung von Rechenzeit - $m:1\;1:1\;m:n$)

## Interprozesskommunikation

- Austausch von Informationen -> Koordination mehrere Prozesse (Threads bis Netzwerk)
- **Parallelität:** gleichzeitige Verarbeitung mehrerer Prozesse (echte Parallelität -> Multiprozessor-Systeme)
- **Nebenläufigkeit:** sequentielle Verarbeitung mehrerer Prozesse (pseudo Parallelität -> Monoprozessor-Systeme)
- **Probleme:** Blockieren, Verhungern, Verklemmung

### Race Conditions

- Nebenläufige Prozesse geraten in Konflikt, wenn sie um die gleichen Ressourcen wetteifern -> Wechselseitiger Ausschluss notwendig! (Mutual Exclusion)
- **kritischer Abschnitt:** Teil eines Programms, das auf gemeinsame Ressourcen zugreift
- Vermeidung: nur ein Prozess gleichzeitig für endliche Zeit in kritischem Bereich (Prozess außerhalb darf diesen nicht blockieren)

### Prozess-Synchronisation

- Abschalten von Unterbrechungen
- gemeinsame Sperrvariable (Spinlock) -> Race-Condition auf Sperrvariable möglich
- Decker-Algortihmus: jeder Prozess besitzt Flag -> ```turn```-Variable entscheidet, wer als nächstes kritischen Bereich betreten darf
- Pertersons Lösung
- Test and Set Lock: nichtunterbrechbarer Test-And-Set Maschinenbefehl (Hardwareunterstützung)
- Sleep and Wackup: Erzeuger + Verbrauch + Warteschlange (je nach Füllung der Schlange automatisch schlafen/wecken -> Problem: Wecken, bevor Verbraucher komplett pausiert)
	- Lösung: Semaphore = Variable, die einem Prozess erlaubt und anderen verbietet
	- Manipulation der Semaphore über zwei unteilbare Operationen (reservieren = *P(sema)*; freigeben = *V(sema)*)

## Prozess-Kommunikation

- Pipes: unidirektionale Datenkanäle zwischen zwei Prozessen (nur innerhalb Prozessgruppen)
- Named Pipes: keine Prozess fest zugeordnet -> flexible Kommunikationsschnittstelle
- Sockets: Verbindung zweier Sockets zur bidirektionalen Pipe (über Rechneradresse identifizierbar -> Netzwerkdienste)

## Scheduling

- mehrere Prozesse konkurrieren um die CPU -> Konfliktsituation
- Langzeit-(Job)Scheduler für Prozesse, die in den Speicher geladen werden
- Kurzzeit-(CPU)Scheduler für die bereits im Speicher befindlichen rechenbereiten Prozesse

- Ziele: max Auslastung/Durchsatz, Fairness, min Ausführungs-/Wart-/Antwortzeit
- Non-präemptive: FIFO, SJF, HRN, PS
- Präemptive: Dynamic Priority Round-Robin, Shortest Remaining Time First

## Interruptverarbeitung

- Interrupt = kurzfristige Unterbrechung eines Programms durch eine von der CPU abzuarbeitende Befehlssequenz (Interrupt Service Routine -> schnelle Reaktion auf I/O o. Zeitgeber)
- intern/extern -> synchron/asynchron zu ausgeführtem Prozess

### Hardware-Interrupts

- durch HW ausgelöst: maskierbar oder nicht maskierbar
- wird ein nicht-maskierter Interrupt ausgelöst, arbeitet der Prozessor den gerade ausgeübten Befehl ab und führt unmittelbar anschließend den Interrupt durch
- Verarbeitung der Anforderungen durch Interruptcontroller -> Weitergabe nach Priorität an Prozessor
- vektorisiert/nichtvektorisiert -> Addresse direkt auf BUS/Vektortabelle


### Software-Interrupts

- Aufruf mit speziellen Maschinenbefehlen (nur Nummer für den Interrupt notwendig)
- Nummer -> Interrupt-Vektor-Tabelle -> Adresse des Interrupt-Unterprogrammes

### Traps

- Art automatischer Prozeduraufruf bei bestimmten Bedingungen (z.B. Gleitkommaüberlauf) -> Programmcounter wird mit Adresse des Trap-Handlers überschrieben

### Ablauf der Interrupt-Verarbeitung

- Sperren weiterer Unterbrechungen mit gleicher oder geringerer Priorität
- Rettung wichtiger Register-Informationen (total/partitiell)
- Bestimmen der Interruptquelle (durch Hardware realisiert)
- Laden des zugehörigen Interruptvektors
- Abarbeitung der Interruptroutine
- Rückkehr zur unterbrochenen Aufgabe

## Polling

- zyklische Abfragen von E/A-Devices -> Status ohne Interrupts abfragen
- **Vorteile:** einfach, Kommunikationsanforderungen parallel zum Programm
- **Nachteile:** hoher Overhead (Anfragen meist unnötig), höhere Reaktionszeit, Priorisierung erfordert zusätzlichen Aufwand

# Deadlocks

> Eine Menge von Prozessen beﬁndet sich in einem Deadlock-Zustand, wenn jeder Prozess aus der Menge auf ein Ereignis wartet, das nur ein anderer Prozess aus der Menge auslösen kann.

Ein System ist Deadlock-frei, wenn die Anzahl der Ressourcen mindestens $p(m-1)+1$ entspricht. Wobei $p$ die Anzahl der Prozesse und $m$ die maximale Zahl reservierter Ressourcen pro Prozess ist.

## Notwendige Bedingungen für Deadlocks

- Mutual Exclusion
- Belegungs- und Wartebedingung
- Ununterbrechbarkeit
- Zyklische Wartebedingung

## Verhinderung

- Eine der vier Voraussetzungen eliminieren

- **Mutual Exclusion:** Spooling -> Dienst verwaltet Ressource (kann von mehreren Prozessen angefordert werden) -> Aber:nicht bei allen Ressourcen möglich
- **Belegungs- und Wartebedingung:** Jeder Prozess fordert seine Ressourcen im Voraus an (Ausführung nur, wenn alle verfügbar) -> benötigte Ressourcen meist nicht im Voraus bekannt
	- Alternative: Prozess gibt vor Anforderung alle Ressourcen kurzzeitig frei und reserviert dann alles auf einmal
- **Ununterbrechbarkeit:** Prozessen Ressourcen zu entziehen ist schwierig oder unmöglich (z.B. gerade genutzter Drucker)
- **Zyklische Wartebedingung:** Ressourcen durchnummerieren -> Alle Prozesse dürfen nur in aufsteigender Reihenfolge reservieren (Belegungs-Anforderungs-Graph immer zyklenfrei)

# Ein- und Ausgabe

## Grundlegende Hardware

- Zeichen- vs. block-orientiert
- Sequentieller vs. wahlfreier Zugriff
- gemeinsame vs. exklusive Kanäle
- Geschwindigkeit: Abhängig vom Gerät oder Kommunikationspartner
- read/write, read only, write only

> jedes Gerät durch **Controller** verwaltet (einfache Schnittstelle zum OS, Datenpuffer)

- Benutzerprozess <-> Kernel-Verteiler <-> Auftragsverwaltung <-> Pufferung <-> Treiber <-> Controller <-> Gerät
- Kommunikation mit Controller mit **Ein-/Ausgabe-Port-Nummer** oder **Memory Mapped**

## Grundlagen Software

- Ziele: Geräteunabhängigkeit, Abstraktion, einheitliche Benennung, Fehlerbehandlung, Pufferung, ...
- **Programmgesteuertes I/O:** dauernde Kontrolle über den E/A-Vorgang durch den Prozessor (Polling/busy wait) -> Einfach, aber Verschwendung von Rechenzeit (wait)
- **Interruptgesteuertes I/O:** Bessere Ausnutzung der Wartezeiten, aber Interrupts kosten Zeit

## Gerätetreiber

- geräteabhängige Steuersoftware (meist für Geräteklasse)
- initialisiert den Controller und das Gerät beim Systemstart (Aktiviert das Gerät)
- wandelt allgemeine E/A-Anforderungen in gerätespeziﬁsche Befehle um
- meldet Geräte- und Controllerbefehle
- bearbeitet und puffert Schreib-und Lesebefehle

## Physikalische Geräte

### Plattenspeicher

#### Zugriffszeiten

- mittlere Suchzeit $t_S$
- Rotationsverzögerung $t_D$ - bis Sektor unter Kopf erscheint
- Dauer der Datenübertragung $t_T$
- Gesamtzugriffszeit mit $t_d=\frac{t_R}{2}$
$$T=t_S+t_d+t_T=t_s+\frac{t_R}{2}+\frac{k}{m}t_R$$
- Zugriffszeit dominiert durch Suchzeit
	- Dateien möglichst in aufeinanderfolgenden Sektoren
	- geeignetes Scheduling der Plattenzugriffe

#### Schedulingstrategien für Plattenzugriffe

- FCFS: Zugriff in Reihenfolge der Aufträge -> viele unnötige Bewegungen des Plattenarms
- Priority: Zugriff prioritätsgesteuert -> „Verhungern“ möglich
- SSTF: (Shortest Seek Time First) kürzesten Bewegungen zuerst
- SCAN: möglichst wenig Richtungswechsel: erst in eine Richtung, bis es in dieser Richtung keine Anfragen mehr gibt, dann Richtung wechseln (Fahrstuhlalgorithmus)
- read-ahead (Vorauslesen): große Wahrscheinlichkeit, das nachfolgende Sektoren benötigt werden
- lazy write (verzögertes Schreiben): Daten werden nicht sofort geschrieben sondern zwischengepuffert

# Speicherverwaltung

- Teil des Betriebssystems, dass die Speicherhierarchie verwaltet
- Überwacht belegten Speicher, teilt Prozessen Speicher zu und gibt ihn wieder frei
- Außerdem: Auslagern von Speicher (Swapping/Paging), wenn der Hauptspeicher zu klein ist
- Anforderungen: Relokation, Schutz (vor anderen Prozessen), Gemeinsame Nutzung, Logische und Physisikalische Organisation
- Grundproblem: Organisation des Informationsﬂusses zwischen Haupt- (schnell, teuer, flüchtig) und Sekundärspeicher (langsam, billig, nicht flüchtig)

## Freispeicherverwaltung

- OS verwaltet Speicherbereiche als eine Kette von freien Speicherblöcken
- **First-Fit-Verfahren:** Durchlaufen des Speicherbereiches, Allokation des erstbesten freien Bereiches
- **Next-Fit-Verfahren:** Wie First-Fit, aber aufeinanderfolgende Suchen werden bei zuletzt gefundenem Speicherplatz begonnen
- **Best-Fit-Verfahren:** Durchsuchen der gesamten Speicherliste, Allokation des kleinsten Bereichs (optimale Ausnutzung)
- **Worst-Fit-Verfahren:** Allokation des größten freien Bereichs
- **Quick-Fit-Verfahren:** unterhält getrennte Listen für freie Bereiche gebräuchlicher Größe
- **Buddy-Verfahren:** für jede Speichergröße eine eigene Liste (nur Blöcke von Zweierpotenzen verwendet)
	- ist kein gewünschter Block frei, wird ein Block in zwei gleich große Blöcke aufgeteilt

### Partitionierung

- **Statische Partitionierung:** Bereiche gleicher Länge -> Interne Fragmentierung (Platzverschwendung)
- **Dynamische Partitionierung:** exakt passende Speicherbereiche -> externer Fragmentierung durch Ein-/Auslagern

### Probleme der direkten Speicherverwaltung

- Speicherfragmentierung
- Prozess muss on einem Stück im Speicher liegen
- Relokation von Programmcode (absolute Speicheradressen müssen umgeschrieben werden)

## Virtueller Speicher

- mehrere Fragmente müssen für das Programm so dargestellt werden, als ob sie aus einem kontinuierlichen Bereich stammen
- Verlangt ein Programm mehr Speicher als vorhanden, wird der inaktive Teil ausgelagert (geswappt)
- Umsetzung der virtuellen in eine physische Adresse durch die Memory Management Unit (MMU)

### Paging

- Abbildung logischer Adressen auf physikalische durch Zerlegung
- Virtuelle Seite wird gegeben durch $v=(s,w)$ mit Seitennummer $s$ und Offset in der Seite $w$
- Abgebildet wird $v$ auf die reale Adresse $p=(k,w)$ mit der Kachelnummer $k$
- Wortbreite von 64 Bit -> Seitentabelle hat $2^{52} = 4∗10^{15}$ Einträge -> Grenzen des Systems erreicht
- Extrem große Seitentabelle für jeden Prozess lässt schnelle Adressumrechnung nicht mehr zu
	- Lösung: Adressbegrenzung, Mehrstufige/invertierte Seitentabelle, Assoziativer Tabellencache

### Seitenersetzungsstrategien

- wird es versucht auf eine Seite zuzugreifen, die nicht im physischen Speicher liegt, wird ein  Systemaufruf mit einem Seitenfehler (page fault) ausgelöst
- richtiges Auslagern ist eines der größten Probleme virtueller Speichersysteme (extreme Auswirkungen auf Gesamtleistung)
- Worst case: ausgelagerte Seite wird sofort wieder benötigt -> Seitenflattern (trashing)

- **NRU:** teilt Seiten anhand ihrer R- und M-Bits in vier Klassen ein und entfernt zufällig eine Seite aus der niedrigsten, nicht-leeren Klasse
- **FIFO:** Auslagern der Seite, die sich am längsten im Hauptspeicher befunden hat (älteste Seite)
- **Second-Chance:** FIFO mit R-Bit Überprüfung (verhindert auslagern häufig genutzer Seiten)
- **LRU:** Auslagern der Seite, auf die am längsten nicht mehr zugegriffen wurde (aufwändig, Umsetzung über Hardware)
- **NFU:** Seite, die am seltensten benutzt wird, soll ausgelagert werden (mit Zähler realisiert; Problem: anfangs viel genutzte Seiten werden nicht augelagert)
- **Aging:** Software-Simulation von LRU (alle Zähler 1 Bit nach rechts, R-Bit addiert)
- **Clock:** analog Second-Chance -> Uhrzeiger wandert so lange um die Elemente, bis eine Seite mit einem zurückgesetzten R-Bit gefunden wird
- **WSClock:** Kombination aus Working-Set (Menge von Seiten eines Prozesses) und Clock

### Aufwand von Seitenwechseln

- Paging ist zeitaufwendig -> Prozessor muss warten
- Mittlere Speicherzugriffszeit bei Wahrscheinlichkeit $p$ für einen Seitenfehler

$$t_Z=t_{HS}+p*t_{SF}$$

- um Leistungsverluste zu minimieren sollte $p$ sehr klein sein (z.B. durch Vergrößern des Arbeitsspeichers)

### Segmentierung vs. Paging

- Segmente dienen zur Aufteilung des Adressraumes nach semantischen Kriterien
- Paging ist ein technisches Hilfsmittel zur Vereinfachung der Speicherverwaltung und Implementierung eines virtuellen Speichers
- Segmente sind die bessere Abstraktion zur Verwaltung von Teilhaberschaften (shared libraries/text/memory), aber problematisch in Bezug auf die Speicherverwaltung (externe Fragmentierung, ...)

### Flat Memory Model

- wurden erst mit 32 Bit Prozessoren möglich
- keine Segmente zur Adressierung des Speichers mehr nötig
- linearer Adressraum beinhaltet Programmcode und Daten (-> direkte Adressierung aller Speicherzelle)

# Dateisysteme

- Daten müssen in einen nicht flüchtigen Speicher geschrieben werden können
- Dateisystem vermittelt zwischen der logischen Sicht von Dateien und Verzeichnissen und der physikalischen Sicht von Blöcken, Spuren, Sektoren, Geräten, Netzlaufwerken
- Abstraktion des Betriebssystems zur geräteunabhängigen Verwaltung von Dateien

### Zentrale Indexstruktur

- zentrale Tabelle (File Allocation Table, FAT) verwaltet alle Blöcke des Dateisystems, Blocknummer ist Index
- für jeden Block einer Datei wird in der FAT der Index des Folgeblocks gespeichert (physisch beliebig verteilt) -> bei Verlust oder Zerstörung der FAT ist das zugehörige Dateisystem nicht mehr nutzbar
- FAT ist auf Datenträger gespeichert
- Zugriff auf eine Datei über Index des Startblocks im Verzeichnis-Block
- für heutige Speicherkapazitäten zu groß

### Verteilte Indexstruktur

- für jede Datei existiert eine eigene Indexliste mit den Nummern aller benutzten Blöcke (I-Node)
- Indexliste einer Datei wird in separatem Indexblock im Dateisystem gespeichert; bei langen Dateien  mehrere Indexblöcke
- Indexblöcke können zudem Attribute der Datei beinhalten
- i-node muss sich nur im Hauptspeicher befinden, wenn die Datei geöffnet ist

### Blockgröße

- Laufwerke verwalten auf der untersten Ebene meist Sektoren zu 512 Byte (sehr große Anzahl von Blöcken)
- Zusammenfassung von mehreren Sektoren zu einer Zuordnungseinheit (Cluster)
- wenige Sektoren/Zuordnungseinheit: Verwaltung träge (Datenstrukturen umfangreich)
- viele Sektoren/Zuordnungseinheit: Verwaltung verschwenderisch (kleine Datei muss mindestens einen Block belegen)
