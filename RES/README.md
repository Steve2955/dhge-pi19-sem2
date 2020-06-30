Betriebssysteme - Zusammenfassung
=================================

# Grundlage

## Bits und Bytes

- **Bit:** kleinstmögliche Speichereinheit (8 Bit = 1 Byte)
- **Si-Präfixe:** 10er- Potenz als Basis (kb, MB, GB, TB, PB, ... -> $=10^x$ Byte)
	- Umrechnung innerhalb: mul. / div. mit $10^3$ (Exponent steigt / fällt um 3)
- **IEC-Präfixe:** 2er- Potenz als Basis (KiB, MiB, GiB, TiB, PiB, ... -> $=2^x$ Byte)
	- Umrechnung innerhalb: mul. / div. mit $2^{10}$ (Exponent steigt / fällt um 10)

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

### Grafikschnittstelle

- Bedienung von Software mittels grafischer Elemente
- wichtige Kriterien: Benutzerkontrolle, Rückkopplung, Visualisierung, Konsistenz, Einfachheit, Ästhetik
- **Vorteile:** leichter für weniger erfahrene Nutzer; ermöglicht WYSIWYG
- **Probleme:** Erfordert Verarbeitung großer Datenmengen; Einschränkung von Kontrolle und Erreichbarkeit

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

#### Hardware-Interrupts

- durch HW ausgelöst: maskierbar oder nicht maskierbar
- wird ein nicht-maskierter Interrupt ausgelöst, arbeitet der Prozessor den gerade ausgeübten Befehl ab und führt unmittelbar anschließend den Interrupt durch

#### Software-Interrupts

- Aufruf mit speziellen Maschinenbefehlen (nur Nummer für den Interrupt notwendig)
- Nummer -> Interrupt-Vektor-Tabelle -> Adresse des Interrupt-Unterprogrammes

#### Traps

- Art automatischer Prozeduraufruf bei bestimmten Bedingungen (z.B. Gleitkommaüberlauf) -> Programmcounter wird mit Adresse des Trap-Handlers überschrieben
