Betriebssysteme
===============

# Grundlagen

## Prinzipieller Aufbau eines Rechnensystems

- Anwendersoftware
- Compiler, Datenbanken, Dienstprogramme
- Betriebssystem
- Maschinensprache
- Mikroarchitektur/Gerätetreiber/Hardware-Software Interface (HSI)
- Physische Geräte

## Systemsoftware

- Betriebssystem und seine Hilfsprogramme
- Unterteilung in:
	- Systemsprogramme/Betriebssystem (Steuerprogramme, Übersetzer, Dienstprogramme, ...)
	- Anwendersoftware (eigene Programme, Bibliotheken, Softwarepakete, ...)

## Betriebssystem als erweiterte Maschine

- Betriebssystem macht die Nutzung eines Computers möglich
- Betriebssystem = Software $\neq$ Betriebssystem
- OS dient als erweiterte Maschine (Abstraktion der Hardware) und Ressourcenmanager
	- Abstraktion der konkreten Instruktionssatzarchitektur, Eigenschaften Zentraler Hardware, Ein-/Ausgabeschnittstellen und Peripheriegeräte
- Anwendersicht:
	- Reale Maschine = Zentraleinheit + Hardware
	- Abstrakte Maschine = Reale Maschine + OS
	- Benutzermaschine = Abstrakte Maschine + Anwendungen

**Das Betriebssystem ist eine virtuelle Maschine, die von der Hardware abstrahiert**

## Betriebssystem als Ressourcenmanager

- aktive Ressourcen (Prozessor [Tastatur, Monitor, Netwerk]) verarbeiten passive Ressourcen (Hauptspeicher [Platte, Bänder, CD])
- Alle Ressourcen eines Computersystems (CPU, RAM, Festspeicher) = Betriebsmittel
- Betriebsmitteln = abstrakte Ressource -> verfügt über ID, Adressbereich, Wertebereich und Funktion
- Klassen von Betriebsmitteln:
	- Entziehbarkeit: entziehbar (z.B. Prozessor) oder nicht (z.B. Dateideskriptor)
	- Zuteilbarkeit: gleichzeitig (z.B. Speicher) oder exklusiv (z.B. Prozessor)
	- Wiederverwendbarkeit: einmalig nutzbar (z.B. Interrupt) oder mehrfach (z.B. CPU, Speicher)
	- Hardware/Software: physikalisches/logisches Betriebsmittel

## Das Betriebssystem in der Definition

**DIN 44300:** __Die Programme__ eines digitalen Rechnersystems __, die zusammen__ mit den Eigenschaften dieser Rechenanlage die Basis der möglichen Betriebsarten des digitalen Rechnersystems bilden und die insbesondere __die Abwicklung von Programmen steuern und überwachen__

## Betriebssystem als Schalen-/Schichtenmodell

**Schichtenmodell**
- Benutzer -> Programm -> Betriebssystem -> Hardware
- Jeder der Schichten wird durch eine Menge an Operationen definiert, die sie bereitstellt (Schnittstelle)

**Schalenmodell**
- HW-spezifische Funktionen auf der untersten Ebene -> aufbauende, elementare Betriebssystemfunktionen -> Schichten für Kommunikation/Dateisysteme/...

| Vorteile | Nachteile |
|----------|-----------|
| - Reduzierte Komplexität (nur Betrachtung der Schnittstellen) | - erhöhte Komplexität der vertikalen Kommunikation (nur durch einzelne Schichten möglich)|
| - Austausch einzelner Schichten durch definierte Schnittstellen möglich (Gesamtsystem bleibt erhalten)| - Effizienz-, Reibungsverluste und lange Pfade |

## Aufgaben eines Betriebssystems

- Verstecken technischer Details/Automatisierung von Vorgängen
	- Abstraktion der HW
	- Definition von Konzepten (Prozess, Datei, Speicher, ...)
	- Vereinfachung der Nutzung (HW), Vermeidung von Fehlern
- Steuern von Abläufen/ Kontrollieren von Ressourcennutzung
	- Blockaden von Prozessen verhindern, CPU-Leistung zuweisen
	- effiziente, zuverlässige, sichere Verwaltung
- Dienste für Anwender/Anwendungsprogramme
	- Prozessverwaltung, E/A-Operationen, Interprozesskommunikation
	- Über APIs realisiert
	- Privilegiensystem zum Schutz der Anwendungen untereinander (inkl. OS)

## Arten von Betriebssystemen

**Mainframe-Betriebssysteme**

- Hohe I/O-Bandbreite, Einsatz als Webserver o. Server für B2B-Anwendungen
- Typische Prozessverwaltungsarten: Batchverfahren (sukzessive Abarbeitung), Transaktionsverfahren (Buchungen), Zeitaufeilungsverfahren (Anfragen an DB)

**Sever-Betriebssysteme**

- viele Nutzer über Netzwerk, Verteilung der Ressourcen an Nutzer (z.B. ISPs, Google)
- Typische Vertretter: UNIX, Linux, (Windows Server)

**Multiprozessor-Betriebssysteme**

- Zusammenschalten mehrerer Prozessoren (höhere Kapazität)
- enge Kopplung (gemeinsamer Speicher), lose Kopplung (Kommunikation über Nahrichten) oder Verteilte Systeme (Netzwerk)

**Betriebssysteme für den PC**

- vernünftige Schnittstelle für Benutzer (Office, Internet, ...)

**Echtzeitbetriebssysteme**

- Zeit als wichtigster Parameter für Ressourcenvergabe
- z.B. Überwachung maschineller Fertigung, Audio/Multimedia-Systeme

**Betriebssysteme für eingebettete Systeme**

- kontrollieren andere Geräte
- kleine Größe, Speicher, Verbrauch

**Betriebssysteme für Chipkarten**

- Smart Cards besitzen eigenen Prozessor (nur einzelne Funktionen)
- Applikationen stark unterschiedlich (bei mehreren Ressourcenverwaltung und Schutzmechanismen sehr wichtig)

## Bits und Bytes

- **Bit:** kleinstmögliche Speichereinheit
- **Byte:** 8 Bits
- **Si-Präfixe:** 10er- Potenz als Basis (kb, MB, GB, TB, PB, ... -> $=10^x$ Byte)
- **IEC-Präfixe:** 2er- Potenz als Basis (KiB, MiB, GiB, TiB, PiB, ... -> $=2^x$ Byte)

# Grundlegende Strukturen

## Aufgaben

**Bedienschnittstelle (UI)**

- Betriebssysteme und alle Programme müssen mit Nutzer kommunizieren und nach dessen Wünschen verfahren (CLI/UI)

**Programmierschnittstelle (API)**

- Bereitstellung einfacher Schnittstellen zur HW (Prinzip der virtuellen (abstrakten) Maschine)
- Schutz der HW vor direktem Zugriff (Stabilität)

**Verwalten von Ressourcen**

- quasiparallele Ausführung mehrere Prozesse; Zugang mehrere Benutzer
- sichere Trennung von einzelnen Nutzern oder Prozessen (Adressraum, Rechenzeit, Speicherzugriff, Zuteilung E/A-Geräte)
- keine allgemeine perfekte Strategie
	- Zerlegung der Zugriffe in kurze Zeitscheiben
	- Effiziente Verwaltung von Datenpuffern (langsame Zugriffe)
	- korrekte Zuteilung (z.B. E/A-Geräte)
	- Spooling (für Geräte mit langsamer Verarbeitung)

**Dienste von Betriebssystemen**

- Bereitstellung von Diensten
	- Prozessmanagement
	- Speichermanagement
	- Dateiverwaltung
	- Steuerung und Abstraktion der HW, Geräteverwaltung, E/A-Steuerung
	- Bereitstellung der Benutzeroberfläche
- Kommunikation mit Diensten über APIs

**Privilegiensystem**

- Verhinderung von negativen Auswirkungen auf das OS bei Programmfehlfunktionen (insbesondere bei Multitask/-user Anwendungen/Systemen)
- Ermöglichen unterschiedlicher Betriebsarten
	- **Kern-Modus**: alle Rechte für Betriebssystem-Code
	- **Benutzer-Modus**: eingeschränkte Rechte für Anwendungs-Code

|                                 | Benutzer-Modus      | Kern-Modus      |
|---------------------------------|---------------------|-----------------|
| Ausführbare Maschinenbefehle    | begrenzte Auswahl   | alle            |
| HW-Zugriff                      | Nein (nur durch OS) | Ja, Vollzugriff |
| Zugriff auf System-Code/Dateien | keiner/read-only    | exklusiv        |

- Schnittstelle zwischen Usermode und Kernel = Traps (Einstiegspunkte; vgl. Software-Interrupt)

## Klassifizierung von Betriebssystemen

**Nach Betriebsart**
- Netzwerk-Betriebssysteme
	- Einbindung von Computern in Netze, Teilen von Ressourcen
	- Client-Server-Betrieb oder Peer2Peer-Netze
- Realzeit-Betriebssysteme
	- Verarbeitungszeit als wichtigster Faktor
- Universelle Betriebssysteme
	- erfüllen mehrere der zuvor genannten Kriterien

**Nach Anzahl der gleichzeitig laufenden Programme**

- Einzelprogrammbetrieb (singletasking)
	- Zu jedem Zeitpunkt nur ein Programm ausgeführt, Ausführung mehrerer nacheinander
- Mehrprogrammbetrieb (multitasking)
	- gleichzeitige Ausführung mehrere Programme (mehrere CPUs) oder zeitlich verschachtelt (quasi-parallel)

**Nach Anzahl der gleichzeitigen Nutzer**

- Einzelbenutzerbetrieb (singleuser mode)
- Mehrbenutzerbetrieb (multiuser mode): Ressourcen werden aufgeteilt

**Nach Anzahl der Verwalteten Prozessoren bzw. Rechner**

- Ein-Prozessor-Betriebssystem
	- Von-Neumann-Architektur besitzt meist nur einen Universalprozessor
- Mehr-Prozessor-Betriebssystem
	- jedem Prozessor wird eine Aufgabe zugeteilt (Aufgabenverarbeitung abhängig von Prozessorzahl -> Koordinationsprobleme) oder
	- Aufgaben werden auf alle Prozessoren verteilt (aber sind nicht an die Beendigung einer Aufgabe gebunden -> quasiparallele Verarbeitung mehrerer Aufgaben durch einen Prozessor)
- Die Verteilung des OS auf mehrere Prozessoren ist möglich (verteilte Betriebssysteme)

## Programmausführung und Hardware

### Grundmodell eines Rechners

- Ausführung von Programmen = Aufgabe von Prozessorhardware + OS
- Basis meister Rechner: Von-Neumann-Architektur

**Steuerwerk**

Laden der Steuerbefehle aus dem Speicher -> Interpretation -> Steuerung der Instruktionsausführung (Steueralgorithmen wie z.B. Rechenoperationen, logische Operationen, ...)

**Rechenwerk**

Laden der Operanden aus dem Speicher -> Verarbeitung (logische/arithmetische Operationen) -> Ablage des Ergebnis im Speicher

**Speicher**

Enthält Maschinenbefehle und Daten in gemeinsamen Adressraum

**Ein-/Ausgabe**

Verbindung von Peripheriegeräten (Tastatur, Monitor, ...) mit Rechenwerk (Schnittstelle zur Umwelt)

### Von-Neumann-Rechner

- Rechenwerk und Steuerwerk häufig als CPU zusammengefasst
- Verbindung einzelner Komponenten über BUS-System
- Prozessor-Speicher-Anbindung = "Von-Neumann-Flaschenhals" (Daten und Befehle über gemeinsamen BUS)

### Befehlsausführung

Pipeline:

- Befehl holen (FETCH)
- Befehl dekodieren (DECODE)
- Befehl ausführen (EXECUTE)
- Speicher-/Registerwerte einlesen und zurückschreiben

Durchsatzerhöhung durch "Prefetching" (während Anweisung n ausgeführt wird, wird n+1 dekodiert und n+2 geholt) -> Latenzzeit (5 Takte), Durchsatz (ein Befehl/Takt)

## Strukturen

### Monolithischer Kern

- Betriebssystem als Menge von Programmen (können sich gegenseitig aufrufen)
- meist evolutionär gewachsen (Anfangs keine deutliche Abgrenzung von Teilfunktionen über Schnittstellen)
- Struktur: keine/unklar (z.B. MS-DOS, UNIX, ...)
	- Linux gilt trotz modularisierten Kernel als monolithisch (alle Module laufen im Kernel-Modus)
- Privilegierter Zugriff aller Komponenten auf die Hardware im Kernel-Modus
- für kleine, statische Betriebssysteme geeignet

**Vorteile:**

- Minimaler Zeitaufwand beim Wechsel zwischen Kernel- und Benutzer-Modus
- Zuverlässigkeit wichtiger Betriebssystemfunktionen nicht direkt vom Verhalten der User-Programme abhängig
- Aufwändige Kommunikation zwischen Teilen des Betriebssystems entfällt

**Nachteile:**

- mangelnde Robustheit: Fehler können nicht abgefangen werden
- mangelnde Modularität: schwere Instandhaltung
- mangelnde Flexibilität(keine abstrakten Schnittstellen): Erweiterungen an Implementierungsdetails gebunden, keine austauschbaren Komponenten (Treiber nicht zur Laufzeit ladbar)

### Mikrokern

- Nur zentralster Funktionen in einem Kernteil zusammengefasst
- Weitere Funktionen durch Serverdienste realisiert (z.B. Datei- o. Verzeichnisdienste)
- Basisdienste:
	- Nachrichtenübermittlung (message passing)
	- Speicherverwaltung (virtual memory)
	- Prozessorverwaltung (scheduling)
- Optimal für verteilte Betriebssysteme (z.B. Amoeba, L4Linux)

**Vorteile:**

- Modulare Struktur: klare Schnittstellen, separierte Komponenten (beliebig austauschbar)
- Gerätetreiber zusammen mit Anwendungsprogramm im Benutzer-Modus
- kleiner sicherheitskritischer Teil des Systems (Kern)

**Nachteile:**

- hoher Kommunikationsaufwand zwischen Prozessen mit eng begrenzten Aufgaben
- Synchronisation vieler Nutzer-Prozesse schwer optimierbar
- Betriebssystemaufrufe (physischer I/O-Zugriff) ohne Kernel-Modus schwer zu realisieren: Aufweichen des Konzeptes

### Makrokern

- Kompromiss zwischen Monolith und Mikrokern
- üblicherweise modulare Architektur (keine Standardstruktur)
- Nutzung von Diensten erfolgt von oben nach unter
- Module höherer Schichten nutzen Funktionen niederer Schichten (nicht umgekehrt)
- Änderungen innerhalb von Schichten problemlos möglich (bei unveränderter Schnittstelle)
- Schichtänderungen haben auf benachbarte Schichten große Auswirkungen (schwer nachverfolgbar)
- Z.B. MAC OS X, Solaris, Win 10

**Moderne Lösung**

- stark modularisiert (alle Module mit sauberen Schnittstellen)
- Module werden am Anfang und zur Laufzeit dynamisch geladen
- einen zentralen Kern (core kernel) und verschiedene ladbare Module
- Zentraler Kern kann mit allen Modulen effizient kommunizieren (ohne Nachrichten)
- Höhere Schichten können Klassen tieferer Schichten erweitern (objektorientierter Ansatz)


### Virtuelle Maschine

- Umstellung auf Client-Server-Architektur -> extrem steigende Zahl von Servern
- Konsolidierung der Serverlandschaften mittels Virtualisierungskonzepten
- ausführen mehrerer logischer Betriebssysteme auf gemeinsamer Hardware
- Virtualisierung auf Hardware-Ebene oder durch Virtualisierungssoftware

**Virtualisierung durch Hardware**

- Ressourcen über Firmware des Rechners verwaltet
- Gastbetriebssystem werden nur Teilbereiche der physischen Hardware als virtuelle Hardware zur Verfügung gestellt
- jede virtuelle Maschine besitzt eigenen Hardware-Satz

**Virtualisierung durch Software**

- Kern ist Monitor (Hypervisor, VMM) der Mehrprogrammbetrieb für mehrere Betriebssysteme ermöglicht
- Monitor vermeidet Zugriffsüberschreitungen von nebenläufigen Programmen
- Alle virtuellen Maschinen haben exakte Kopien der Hardware (gleiche Eigenschaften der realen Maschine)

**Vorteile**

- Konsolidierung der Serverlandschaften
- Kostenreduzierung
- Geringerer administrativer Aufwand
- Bessere Skalierbarkeit und hohe Verfügbarkeit

**Nachteile**

- nicht jede Hardware ansprechbar oder emulierbar
- Host-Ausfall: Ausfall mehrerer virtueller Server (Ausfallkonzepte und Redundanzen)
- Virtualisierung ist komplex
- Leistungsverluste (5-10%)

## Entwurf von Betriebssystemen

- Aufwändiger Schnittstellenentwurf: Austausch von Informationen zwischen vielen Programmen
- Prinzip Einfachheit: Perfektion ist nicht einfach -> KISS: Keep It Simple, Stupid.
- Prinzip Vollständigkeit: alle benötigten Programme sollten verfügbar sein, keines darüber hinaus
- Ausführungsparadigma: algorithmisches Paradigma vs. ereignisbasierte Paradigma
- Prinzip Effizienz: steigende Effizienz = sinkende Komplexität (Effizienz und Lesbarkeit als Kompromiss)
- Datenparadigmen: Band (FORTAN), Datei (UNIX) oder Objekt (Windows)
- Minimum an Mechanismen: Nur notwendige Implementationen


## Beispiel: UNIX

- Enstand aus der Notwendigkeit für die Programmerstellung ein Rechnerbetriebssystem zu entwickeln
- Portierbarkeit von UNIX beruht auf der Entwicklung der Programmiersprache C
- Kompaktheit und strukturelle Einfachheit des Systems (ermuntert Nutzer zu eigener Aktivität und Weiterentwicklung)
- heute: hoher Reifegrad und vielfache UNIX-Derivate
- Kernel um die Hardware aufgebaut (verwaltet Ressourcen)
- Über Kernel werden alle Interrupts und I/O-Operationen abgewickelt
- Kommunikationsschnittstelle mit dem Benutzer: Shell
- Aufgaben des Kernel:
	- Prozess-Scheduling
	- Prozess-Umschaltung
	- Prozess-Kommunikation
	- Dateisystem verwalten
	- Ein-/Ausgabesteuerung
	- Gerätesteuerung
	- Zugangskontrolle und Abrechnung

# Schnittstellen

## Computergestützte Benutzerschnittstellen

- Benutzer kann nicht sehen, was sich im Rechner abspielt: Ein-/Ausgabe wichtig
- Benutzeroberfläche: Art und Weise der Gestaltung der Aktion zwischen Rechner und Benutzer
- Erste Benutzerschnittstellen: Lochkarten und -streifen (Ein- und Ausgabemedium, nicht interaktiv)
- Terminal: Tastatur als Eingabe, Bildschirm als Ausgabe (Terminal mit alphanumerischen Zeichen)
- heute: Grafische Benutzeroberflächen

**Arten**

- Kommandozeilen: Eingabe von Befehlen per Tastatur
- Zeichenorientierte Schnittstellen: Menüs, die durch Tastatur oder Maus bedient werden
- Grafische Benutzeroberflächen: komplexe Oberflächen mit Maus bedient
- Sprachbasierte Schnittstellen: Kommunikation mit gesprochenem Wort
- Anfassbare Schnittstellen: Systemfunktionalität wird durch angepasste Eingabegeräte verkörpert (z.B. Handy)

### Kommandozeile

- auch Konsole/Terminal
- Kommandozeile = Eingabebereich für Steuerung einer Software
- Eingabe von Kommandos/Befehlen als Worte (Steuerung durch zusätzliche Parameter)

**Shell**

- ein Kommandozeileninterpreter (Shell) ist ein Programm, welches eine Zeile Text in der Kommandozeile einließt, interpretiert und ausführt
- eventuelle Ausgaben werden direkt auf den Bildschirm ausgegeben
- Vertreter: bash, sh, PowerShell, cmd

**Vorteile**

- schnelle, direkte Kontrolle und Erreichbarkeit aller Funktionen für erfahrene Nutzer
- Automatisierung durch Makros, Stapeldateien oder Skripte möglich

**Probleme**

- Länderspezifische Textdarstellung und Eingabe (viele Zeichensätze)
- Datenaustausch erfordert Nutzung der ursprünglichen Zeichenkodierung (Standardisierungsansatz: Unicode)

### Grafikschnittstelle

- Lösten ab ca. 1980 die Bedienung per Kommandozeile ab
- Durch Entwicklung der Computermaus ermöglicht: grafischer Mauszeiger auf Bildschirm
- Eine GUI macht eine Software mittels grafischer Elemente bedienbar
- Gesamtbild wird aus einer Vielzahl aus Bildpunkten erzeugt (erhebliche Datenmengen)
- **Fokus:** GUI-Element, das für die nächste Benutzer-Aktion relevant ist besitzt den Fokus

**Anforderungen**

- Benutzer soll Aufgabe direkt zeigen können (Maus)
- Anwendung soll Auswahlloste an Kommandos als Menü anbieten (Hierarchie)
- Zuordnung von Universalkommandos zu Funktionstasten
- Aussehen der Dokumente soll realem Ausdruck entsprechen (WYSIWYG)
- **Benutzerkontrolle:** Benutzer muss immer Kontrolle über den Rechner haben
- **Rückkopplung:** Reaktion auf Benutzereingabe (Vermeidung von Frustration)
- **Visualisierung:** Verwendung von Metaphern für bestimmte Programmfunktionen (z.B. Papierkorb)
- **Konsistenz:** Benutzeroberflächen sollen ähnlich sein (bekannte Situation darstellen)
- **Einfachheit:** Kompromiss zwischen zu viel und zu wenig Informationen
- **Ästhetik:** Gestaltung der Oberfläche nicht nur nach funktionalen Erfordernissen (Aufmerksamkeit auf wichtige Funktionen lenken)

#### Funktionale Struktur

- Nicht jedes Programm besitzt eigene individuelle GUI -> Betriebssystem stellt einheitliche GUI zur Verfügung (einheitliche Funktionen)

**Rastergrafik**

- Problem: großer Speicherbedarf bei 24 Bit Farbe pro Pixel
- Lösung: Color Lookup Table (3 Bit Farbindex pro Pixel, je Farbe 8 Bit Farbinfo)
- schnelle Übertragung großer Datenmengen
- Speicherungen von Texturen geometrischer Körper

|          | Pixelgrafik               | Vektorgrafik                                           |
|----------|---------------------------|--------------------------------------------------------|
| Vorteil  | Zeichnen, Input einfacher | beliebige Größe und Formstauchung, stark komprimierbar |
| Nachteil | nicht skalierbar          | Zeichnen dauert mit jedem Vektor länger                |

- Vektorgrafik als internes Format
- Pixelgrafik extern für Bildschirm/Drucker

#### Fenstersysteme

- **Fenster:** rechteckiger Bildschirmausschnitt zum Anzeigen aller Daten eines Programmes
- Ausgabe eines Prozesses auf einen bestimmten Teil des Bildschirms
- Früher: ASCII Ein-/Ausgabe, Grafikbibliothek beim Programm
- Heute: Grafikbibliothek beim OS -> Fenstermanager (Virtuelle Fenster, Menüs, Clipboard)

**Vorteile**

- Zentral einheitliches Fenstermanagement
- Gemeinsame parallele Darstellung unabhängiger Ereignisse (parallele Präsentation mehrerer Programme)
- Dezentrale Grafik zentral zusammenfassen
- Ereignisbearbeitung auf Subsystem verlagern -> Entlastung des Prozessors für Anwendung

**Nachteile**

- kein Multi-User-System (kein Displayserver)
- fest im Betriebssystem integriert

**Alternative: X Window System (X11)**

- netzwerkfähiges Fenstersystem (Client-Server-Prinzip)
- einheitlicher Desktop durch Toolkits (Windowmanger, KDE, ...)

__Stärken__

- konzipiert für effizienten Netzwerkbetrieb
- Server-Client-Kommunikation über Standardisiertes Protokoll
- kein Betriebssystembestandteil

__Schwächen__

- Verschiedene Toolkits mit verschiedenen Eigenschaften -> unterschiedliches Verhalten
- hohe Übertragungsrate und geringe Latenz als Voraussetzung


### API

- Systemfunktionen werden durch APIs von Betriebssystemen für Anwendungen bereitgestellt
- Programmiersprache der API ist im allgemeinen die Implementierungssprache des OS
- Bereitstellung weiterer APIs durch Zusatzbibliotheken (zwingend erforderlich für andere Programmiersprachen)

**Standard APIs**

- in Programmiersprachen: Standard-Bibliothek
- implementieren Funktionen unabhängig von Hardware und Betriebssystem:
	- Ein-/Ausgabe
	- Dateizugriffe
	- dynamische Speicherverwaltung
	- mathematische Berechnungen
- Standartisierung der API trägt zur Portabilität von Programmen bei (Kompilierung auf neuer Hardware genügt)

**Proprietär APIs**

- stellen Funktionsumfang über die Standartbibliothek hinaus bereit (grafische Bedienoberfläche, Multi-Threading, ...)
- Programm, das Funktionen aus solchen speziellen APIs verwendet ist nicht mehr beliebig portabel
	- Abhängigkeit vom Compiler, Betriebssystem oder Zusatzbibliothek
	- Ständige Veränderung von Bibliotheken: Kompatibilitätsprobleme
- Beispiel: POSIX (Ziel: Kompatibilität der UNIX-Derivate)

# Prozesse

**Definition**

> eine Abstraktion eines laufenden Programms
> - Tanenbaum, 2003

- Prozesse sind aktive Komponenten, befinden sich in Ausführung und können voneinander abhängen
- Prozesskommunikation ermöglicht Synchronisation von Prozessen (Konfliktsituationen möglich)
- Prozesse verwenden Ressourcen und besitzen stets einen Zustand

**Abgrenzung**

- Programm: statische Beschreibung eines sequentiellen Algorithmus
- Prozess: Programm in der Ausführung
- Thread: sequentieller Abarbeitungsablauf innerhalb eines Prozesses
- Task: Synonym für Prozess, aber auch Thread

**Parallelität**

- Prozesse sind die wichtigste Eigenschaft für die parallele Ausführung von Aufgaben
- bei nur einem Prozessor: Parallelität simuliert (Zeitscheibe-Verfahren)

**Prozess-Umschaltung**

- Scheduler entscheidet, wann welcher Prozess ausgeführt werden soll
- Füher: Stapelbetrieb (ein Prozess nach dem anderen - nicht-präemtives Scheduling)
- Heute: Multitasking (Scheduler entscheidet über die Unterbrechung laufender Prozesse - präemtives Scheduling)

**Eigenschaften**

- alle ausführbare Programme sind sequentielle Prozesse
- jeder Prozess besitzt eigenen virtuellen Prozessor (Scheduler schaltet zwischen virtuell und real um)
- jeder Prozess hat eigenen Kontrollfluss
- zu jedem Zeitpunkt nur ein Prozess aktiv

## Prozesserzeuung/-terminierung

**Prozesserzeugung**

- Initialisierung durch das System (Betriebssystem-Dienste) oder Benutzer (Programme)
- durch Systemaufruf eines bestehenden Prozesses (fork -> Prozesshierarchie)
- Initiierung eines Batch-Jobs

**Prozessterminierung**

- Freiwillig durch Aufruf von ```exit``` (normal oder aufgrund Fehler)
- Unfreiwillig durch Betriebssystem
	- schwerwiegender Fehler (Speicherüberschreitung, E/A-Fehler, ...)
	- durch anderen Prozess
	- Reaktion des Prozesses Teilweise noch möglich

## Erweitertes Prozessmodell

Ein Prozess beﬁndet sich in genau einem der folgenden Zustände:
- rechnend (Befehle werden in diesem Moment ausgeführt)
- rechenbereit (anderer Prozess rechnet gerade)
- blockiert (warten auf externes Ereignis)

## Implementierung von Prozessen

- Betriebsystem verwaltet eine Prozesstabelle (ein Block/Prozess)
- Prozesskontrollblock enthält Informationen über den Zustand des Prozesses
	- Prozessidentifikation
	- Befehlszähler, Kellerzeiger, ...
	- Zustand seiner geöffneten Dateinen
	- Verwaltungs- und Schedulinginformationen
- Prozess wird nach Zustandsänderung ohne Auswirkungen fortgesetzt

## Prozessverwaltung

### Prozesserzeuung

- Zuweisung einer eindeutigen Prozesskennung (Eintrag in Prozesstablle)
- Zuteilung von Speicherplatz (für Programmcode, Daten und Keller)
- Initialisierung des Prozesskontrollblock (Prozess bereit)
	- PC und SP
	- Ressourcen evtl. von Elternprozessen geerbt
- Einhängen des Prozesses in Warteschlange

### Prozesswechsel

**Urachen**

- bei Systemaufruf (Prozess gibt Kontrolle freiwillig ab)
	- Sichern des Prozessorstatus
	- Zustand des Prozess auf bereit zurücksetzen
	- Ausführung des Aufrages (evtl. Prozess auf blockiert setzen)
	- Sprung zum Scheduler
- bei Ausnahme (z.B. unzulässiger Befehl -> Beendigung oder Behandlung durch OS)
	- Sichern des Prozessorstatus
	- Beenden/Blockieren des Prozesses oder Behebung der Ursache für die Ausnahme (je nach Art der Ausnahme)
	- Sprung zum Scheduler
- bei Interrupt (Behandlung des Interupts im Betriebssystem)
	- Sichern des Prozessorstatus
	- Zustand des Prozess auf bereit zurücksetzen
	- Ursache der Unterbrechung ermitteln
	- Ereignis entsprechend behandeln
	- evtl. blockierte Prozesse auf bereit setzen
	- Sprung zum Scheduler

## Threads

- Aspekte klassischer Prozesse
	- Einheit des Ressourcenbesitzes: eigener Adressraum, Kontrolle von Ressourcen (z.B. E/A-Geräte)
	- Einheit der Ablaufplanung/Ausführung

> Prozesswechsel sind aufwändige Aktionen des Betriebssystems

- Lösung: Trennung der Aspekte
	- **Prozess:** Einheit des Ressourcenbesitzes und Schutzes
	- **Thread:** Einheit der Ausführung (Prozessorzuteilung)
- Ziel: Strukturierung unabhängiger Programmkomponenten, Leistungssteigerung durch effiziente Parallelarbeit

### Aufbau von Prozessen und Threads

| Elemente pro Prozess         | Elemente pro Thread |
|------------------------------|---------------------|
| - Adressraum                 | - Befehlszähler     |
| - Globale Variablen          | - Register          |
| - Geöffnete Dateien          | - Stack             |
| - Kindeprozesse              | - Zustand           |
| - Zu behandelnde Signale     |                     |
| - Signale und Signalroutinen |                     |
| - Accounting Informationen   |                     |

> Ein Thread hat Zugriff auf alle Ressourcen des Prozesses in dem er abläuft

**Vorteile**

- schnellere Umschaltung zwischen Threads als Prozessen
- Einfache Nutzung von gemeinsamen Prozessressourcen (Parallelität innerhalb einer Anwendung)
- Bessere Nutzung der verfügbaren Rechenzeit

### Typische Anwendungen

- Textverarbeitung
	- Texteingabe, Rechtschreibprüfung, Zwischenspeichern auf verschiedenen Threads
- Webserver
	- Dispatcher-Thread: nimmt ankommende Anfrage entgegen
	- Worker-Thread: wird vom Dispatcher geweckt und erhält die Anfrage

### Implementierung

- **User-Thread:** für Programmierer sichtbar, **logische Realisierung** der gewünschten Parallelität
- **Kernel-Thread:** dem Betriebsystem bekannt, erhält vom Betriebssystem Rechenzeit

> User-Thread muss einem einem konkreten Kernel-Thread zugeteilt werden, dmit er real Ausgeführt wird

**Realisierungsformen:**
- $m:1$-Zuordnung: Alle zu einem Prozessgehörenden User-Threads werden einem einzigen Kernel-Thread zugeteilt (Multithreading außerhalb des Systemkerns)
- $1:1$-Zuordnung: Jedem User-Thread wird ein Kernel-Thread zugeteilt (Multithreading auf Systemebene)
- $m:n$-Zuordnung: Einem Kernel-Thread sind mehrere User-Threads zugeordnet, mehrere Kernel-Threads pro Prozess (Hybridlösung)

## Interprozesskommunikation

### Parallelität und Nebenläufigkeit

- **Mehrprogrammbetrieb:** Verwaltung mehrerer Prozesse in einem Einprozessorsystem
- **Mehrprozessorbetrieb:** Verwaltung mehrerer Prozesse in einem Mehrprozessorsystem
- **Verteilte Verarbeitung:** Verwaltung mehrerer Prozesse auf mehreren Verteilten Computersystemen (Cluster)

Grundlegender Bedeutung: Kommunikation, Synchronisation zwischen Prozessen; Nutzung von Ressourcen und Prozessorzeit

- **Parallelität:** Die Anweisungen zweier Prozesse werden gleichtzeitig unabhängig voneinander ausgeführt (echte Parallelität -> nur auf Multiprozessor-Systemen)
- **Nebenläufigkeit:** Die Anweisungen zweier Prozesse werden  unabhängig voneinander sequentiell ausgeführt (pseudo Parallelität -> auf Monoprozessor-Systemen)

#### Probleme bei der Ausführung

- **Blockieren:** ein Prozess belegt Betriebsmittel, die ebenfalls von einem anderen benötigt werden
- **Verhungern:** ein Prozess erhält keine Rechenzeit (anderer hat höherer Priorität)
- **Verklemmung:** Zustand bei dem ein oder mehrere Prozesse auf eine bereits zugeteilt Betriebsmittel warten

### Notwendigkeit der Interprozesskommunikation

- Austausch von Informationen = wichtiges Mittel für die Koordination mehrere Prozesse
- im engeren Sinne: Kommunikation zwischen Prozessen auf einem Computer mit getrennten Speicherbereichen
- im weiteren Sinne: Datenaustausch in Verteilten Systemen (Threads bis Netzwerk verschiedener Computer)

### Race Conditions

- Nebenläufige Prozesse (oder Threads) geraten in Konflikt, wenn sie um die gleichen Ressourcen wetteifern
- Endergebnisse hängen von der zeitlichen Reihenfolge ab

> Wechselseitiger Ausschluss notwendig! (Mutual Exclusion)

- **kritischer Abschnitt:** Teil eines Programms, das auf gemeinsame Ressourcen zugreift
- Bedingungen zur Vermeidung von Race-Conditions
	- keine zwei Prozesse dürfen sich gleichzeitig in einem kritischen Abschnitt befinden
	- keine Annahmen über Geschwindigkeit oder Anzahl der CPUs
	- kein Prozess außerhalb einer kritischen Region darf einen anderen blockieren
	- Alle Prozesse müssen in endlicher Zeit den kritischen Abschnitt betretten können

### Prozess-Synchronisation

#### Unterbrechungen ausschalten

- unattraktiver Ansatz
- Benutzerprozess schaltet Unterbrechung ab und nie wieder ein -> CPU kann nie wieder zu anderem Prozess wechseln (keine Unterbrechung durch Systemuhr möglich)

#### Variablen sperren

- gemeinsam genutzte Sperrvariable (Spinlock) zeigt die Möglichkeit über den Eintritt in einen kritischen Bereich an
- Setzen des Spinlock bei Betretten eines kritischen Abschnittes, Rücksetzen bei Verlassen
- Race-Condition auf Sperrvariable möglich (Unterbrechung nach Auslesen)

#### Decker-Algorithmus

- Für jeden Prozess exisiter eine Flag
- eine gesetzte Flag signalisiert, dass sich der Prozess in einem kritischen Abschnitt befindet
- Variable ```turn``` entscheidet, wer als nächstes einen kritischen Abschnitt betretten kann
- Problem: Prozess kann nicht in kritische Region, solange anderer Prozess ```turn``` besitzt und einen nichtkritischen Bereich bearbeitet

#### Petersons Lösung

- Prozess bekundet sein Interesse indem er sein Feldelement setzt und setzt ```turn```
- Nach Verlassen des kritischen Bereiches wird das Feldelement zurückgesetzt
- weitere Prozesse warten, bis der laufende Prozess sein Interesse zurückzieht

#### Test and Set Lock (TSL)

- Problem: Testen und Schreiben auf Sperrvariablen sind zwei unterbrechbare Aktionen
- Lösung: nichtunterbrechbarer Test-And-Set Maschinenbefehl (Hardwareunterstützung)

#### Sleep and Wakeup

Klassisches Beispiel: Erzeuger-Verbraucher-Problem

- Erzeuger: erzeugt Datenpakete, bis zur vollen Warteschlange (schäft und wird geweckt, wenn Platz in der Warteschlange ist)
- VerbraucherL verbraucht Datenpakete (schläf und wird geweckt, wenn neue Daten vorhanden sind)


**Problemfall**

- Verbraucher wird geweckt, bevor er sich bereits komplett pausieren konnte (Prozessunterbrechung im kritischen Abschnitt Erkennung der Bedingung von Sleep und Aufruf von Sleep)
- Idee: Speicherung der Anzahl der Weckrufe in neuer Variablenart(**Semaphor**)

##### Semaphore

- "Ampel", die immer nur einem Prozess die Benutzung erlaubt und allen anderen verweigert
- Alle Prozesse sind dazu verpflichtet bestimmten Code nur auszuführen, wenn es die Semaphore erlaubt
- Prozesse synchronisieren sich über die Semaphore (Setzen/Rücksetzen der Semaphore bei Betretten/Verlassen kritischer Bereiche)
- Zur Manipulation und Abfrage der Senaphoren exisitieren zwei unteilbare Operationen
- Notation nach Dijkstra:
	- **P(sema)** Semaphore reservieren (auch down-Operation)
	- **V(sema)** Semaphore freigeben (auch up-Operation)
- Eine Semaphore regelt durch Zählen Wechselwirkungsituationen von Prozessen und realisiert ein passives Warten der Prozesse
- binären Semaphore auch "Mutexe", Integer auch "Zähl-Semaphore"

**Implementierung**

- Zähler (Ganzzahl) beim Start mit Zahl maximal verfügbarer Ressourcen initialisiert
- Herunterzählen bei einer Reservierung, Inkrementieren bei einer Freigabe
- Fällt der Zähler unter 0, muss der reservierende Prozess warten

##### Erzeuger-Verbraucher-Problem mit Semaphoren

- Semaphor mutex verhindert, dass gleichzeitig Verbraucher und Erzeuger im kritischen Abschnitt sind
- Um zu verhindern, dass eine leere/volle Liste gelesen/geschrieben wird, werden zwei Weitere Semaphoren verwendet (empty/full)  

#### Monitore

- Monitor besteht aus einigen Prozeduren, Variablen und Darenstrukturen
- verkapselt Semaphore und Operationen auf diese Semaphore
- zu jedem Zeitpunkt kann nur ein Prozess einen Monitor benutzen, aber für alle Prozesse zugänglich
- Häufig für Verwaltung von Puffern, Geräten

## Prozess-Kommunikation

### Pipes

- unidirektionale Datenkanäle zwischen zwei Prozessen (ein Prozess schreibt, der andere liest)
- Realisierung im Speicher oder als Datei
- Lebensdauer entspricht der der beiden Prozesse
- Nur innerhalb von Prozessgruppen (UNIX) oder zwischen Threads verwendbar, da diese nur dort eindeutig identifizierbar sind
- Erweiterung: Named Pipes

#### Named Pipes

- keinem Prozess fest zugeordnet
- Lesen/Schreiben wie Dateien (über Systemaufrufe)
- existieren als Objekte mit Namen im Dateisystem
- flexible Kommunikationsschnittstelle, Teil aller modernen Betriebssysteme

### Sockets

- Erweiterung von Pipes für Internet und Netzdienste
- zwei Sockets werden zu einer bidirektionalen Pipe verbunden
- über Rechneradresse identifizierbar (ermöglichen Client-Server-Kommunikation)
- Serverprozess erstellt Socket (create) und wartet auf Verbindungswünsche (listen)

## Prozessscheduling

- mehrere Prozesse konkurrieren zur gleichen Zeit um die CPU -> Konfliktsituation
- Koordination des Zugriffes auf die CPU notwendig, wenn Nachfrage zu hoch
	- Langzeit-(Job)Scheduler = zuständig für Prozesse, die in den Speicher geladen werden
	- Kurzzeit-(CPU)Scheduler = zuständig für die bereits im Speicher befindlichen, rechenbereiten Prozesse
- zentrale oder dezentrale (Prozess selbst) Verwaltung
	- **Deterministisches Modell:** alle Informationen bekannt
	- **Probalistisches Modell:** offen (Anzahl der Prozesse nicht bekannt) oder geschlossen (Anzahl bekannt, Bedienzeit nicht)

### Deterministisches Modell

- Berechnung der Prozessabläufe vor der Ausführung
- nur in geschlossenen Systemen (feste Prozesszahl, statischer Ablauf)

### Probalistisches Modell

- Zuteilung der CPU zu Prozessen erfolgt dynamisch während der Prozessabarbeitung
- Entscheidung mittels stochastischer Verfahren auf Grundlage der Wahrscheinlichkeitstheorie (z.B. Poisson-Prozesse, Markow-Prozesse)

### Scheduling-Strategien

- Ziele:
	- möglichst hohe CPU-Auslastung, Durchsatz
	- Fairness (ohne Priorisierung alle Prozesse gleich)
	- niedrige Ausführungszeit, Wartezeit und Antwortzeit

#### Non-präemptive Scheduling

- **First come first serve (FCFS/FIFO):** Jobs werden in eine Warteschlange eingefügt
- **Shortest-Job-First (SJF):** Prozess mit geschätzt kürzester Ausführungszeit wird zuerst bedient
- **Highest response ration next (HRN):** verarbeitet Jobs mit maximalem Verhältnis aus Antwortzeit und Bedienzeit
- **Prioritätsscheduling (PS):** Einsortieren von Jobs in eine Wartschlange nach ihrere Priorität

#### Präemptives Scheduling

- einfachste Strategie: alle Prozesse gleichberechtigt, erhalten gleiches Zeitfenster (Round-Robin)
- Implementation: Scheduler muss Liste aller laufenden Prozesse vorhalten
- Antwortzeiten proportional zu Bedienzeit
- Prozess- / Kontextwechsel kostet Prozessorzeit
	- Intervall zu klein: Verwaltung und Wartezeit höher, Durchsatz kleiner
	- Intervall zu groß: geringere Verwaltung, höherer Durchsatz und Antwortzeit
- **Dynamic Priority Round-Robin:** Einteilung der Prozese in Prioritätsklassen
	- höchste Prioritätsklassen erhalten CPU
	- Erhöhen der Priorität in der Vorstufe (verhindert das Prozesse verhungern)
- **Shortest Remaining Time First:** Job mit der kürzesten Restlaufzeit wird vorgezogen

### Interruptverarbeitung

- Interrupt =  kurzfristige Unterbrechung eines Programms durch eine von der CPU abzuarbeitende Befehlssequenz (Interrupt Service Routine)
- Funktion: schnelles reagieren auf Ein-/Ausgabe-Signale oder Zeitgeber
- Reaktion auf zeitkritische Ereignisse
- **interne Interupts:** laufen *synchron* mit dem ausgeführten Programm (erst nach Befehlsausführung erkannt)
- **externe Interrupts:** asynchron, unabhängig vom gerade ausgeführten Programm (Unterbrechung nicht möglich)

#### Hardware-Interrupts

- durch einen Hardware-Baustein oder durch ein Peripheriegerät ausgelöst
- **maskierbare** (sperrbare) oder **nicht maskierbare** Interrupts
- wird ein nicht-maskierbarer Interrupt ausgelöst, arbeitet der Prozessor den gerade ausgeübten Befehl ab und führt unmittelbar anschließend den Interrupt durch
- **Interrupt-Controller** verwaltet mehrere Interrupt-Anforderungen und gibt sie *geordnet nach Priorität* an den Prozessor
- **vektorisiert:** Interruptquelle legt Adress der ISR auf den Datenbus und verzweigt direkt zum Mikroprogramm
- **nichtvektorisiert:** Interruptquelle legt eine Vektornummer auf den Datenbus, mit der due Adresse der ISR aus einer Vektortabelle ermittelt wird

#### Software-Interrupts

- Aufruf mit speziellen Maschinenbefehlen (nur Nummer für den Interrupt notwendig)
- Mit Nummer in der Interrupt-Vektor-Tabelle wird die Adresse des Interrupt-Unterprogrammes referenziert

#### Traps

- Art automatische Prozeduraufrufe, welche durch eine vom Programm verursachte Bedingung eingeleitet werden (z.B. Gleitkommaüberlauf)
- Bei Auftretten der Bedingung stoppt die Ablaufsteuerung die Ausführung und überschreibt den Programmcounter mit der Adresse des Trap-Handlers
- Wesentliches Merkmal: Auslösung bie Ausnahmebedingungen (durch HW oder Mikroprogramme)

#### Ablauf der Interrupt-Verarbeitung

- Sperren weiterer Unterbrechungen mit gleicher oder geringerer Priorität
- Rettung wichtiger Register-Informationen (Prozessorstatus)
- Bestimmen der Interruptquelle (durch Hardware realisiert)
- Laden des zugehörigen Interruptvektors
- Abarbeitung der Interruptroutine
- Rückkehr zur unterbrochenen Aufgabe entweder

#### Zustandssicherungskonzepte

- **totale Sicherung:** Sicherung aller Register (UNIX & Co.)
- **partielle Sicherung:** Sicherung des von Änderungen betroffene Teils (Embedded Systems)

#### Alternative DMA

- Interrupts befreien die Prozessoren vom Warten auf E/A Ereignisse, aber vektorisierte Interrupts benötigen viele Taktzyklen zu ihrer Abarbeitung
- Interrupts werden erst nach der Befehlsabarbeitung erkannt und ausgeführt

->  Problem bei Echtzeitanwendungen

Lösung dieser Probleme wäre ein direkter Speicherzugriff eines Devices, da so der Prozessor komplett umgangen werden kann.

**Implementierung DMA**

- **Zentral:** zentraler DMA-Controller für alle Geräte
- **Dezentral:** jede E/A-Einheit besitzt eigenen DMA-Controller und kann selbst Busmaster werden

**Probleme**

- durch Unabhängigkeit sind Schutzmaßnahmen notwendigen
- DMA-Controller wirkt wie ein weiterer Prozessor am Bus
- DMA-Controller muss eng mit Speichermanagment zusammenarbeiten (Inkonsistenzen im Speicher vermeiden)

#### Polling

- zyklische Abfragen von einen oder mehreren E/A-Devices zur Feststellung der Kommunikationsbereitschaft
- Kann ohne Interrupts den Status von Geräten abfragen

**Vorteile gegenüber Interrupts**

- einfache Implementierung
- Kommunikationsanforderungen erfolgen synchron zum Programmablauf

**Nachteile**

- Hoher Programm-Overhead
- Die meisten Anfragen an die Geräte sind unnötig
- Je mehr Geräte am Bus, um so höher die Reaktionszeit
- Priorisierung zeitgleicher Anfragen erfordern zusätzlichen Zeitaufwand

# Deadlocks

- Anwendungen verlangen exklusiven Zugriff auf Ressourcen
- Fordern mehrere Prozesse die gleichen Ressourcen gleichzeitig an, kann es passieren, das keiner der Prozesse Zugriff auf alle benötigten Ressourcen erhält -> die Prozesse blockieren sich gegenseitig (= **Deadlock**/Verklemmung)
- Deadlocks entstehen, wenn Prozessen das alleinige Zugriffsrecht auf Ressourcen erteilt wird
- Unterbrechbare Ressourcen können dem Prozess entzogen werden, ununterbrechbare nicht!
- Benutzung von Ressourcen besteht aus den Schritten: Anfordern, Benutzen, Freigeben (ist eine Ressource besetzt, blockiert der Prozess)

> Eine Menge von Prozessen beﬁndet sich in einem Deadlock-Zustand, wenn jeder Prozess aus der Menge auf ein Ereignis wartet, das nur ein anderer Prozess aus der Menge auslösen kann.

## Notwendige Bedingungen für Deadlocks

- **Mutual Exclusion:** jede Ressource ist entweder verfügbar oder einem Prozess zugeordnet
- **Belegungs- und Wartebedingung:** Prozesse, die bereits Ressourcen reserviert haben, können weitere anfordern
- **Ununterbrechbarkeit:** Ressourcen, die einem Prozess zugeteilt sind, können diesem nicht entzogen werden (Prozess muss sie freigeben)
- **Zyklische Wartebedingung:** Zyklische Kette von Prozessen, die jeweils auf die Freigabe einer Ressource im nächsten Prozess der Kette warten
- alle Bedingungen müssen gleichzeitig erfüllt sein

## Behandlung

- Problem ignorieren (Vogel-Strauß-Algorithmus)
- Erkennen und Beheben
- Dynamische Verhinderung durch Ressourcenmanagement (vor Zuteilung prüfen)
- Vermeidung von Deadlocks (eine der notwendigen Bedingungen eliminieren)

### Vogel-Strauß-Algorithmus

- "Kopf in den Sand stecken und so tun als gäbe es kein Problem"
- Auftrittswahrscheinlichkeit gering
- Vermeidung mit hohen Kosten verbunden
- Abwägen zwischen: Bedienerfreundlichkeit und Korrektheit

### Erkennen und Beheben

- zur Ausführung eines Prozesses nötige Ressourcen müssen vor dem Ausführen bekannt sein (in offenem System nicht möglich)
- Alternative: Deadlocks werden zugelassen und das System versucht diese zu Erkennen und zu Beheben (Unterbrechung, Rollback oder Prozessabbruch)

**Erkennung**

- eine Ressource pro Typ: Konstruktion eines Belegungs-Anforderungs-Graphen
	- bei min. einem Zyklus befindet sich das System in einem Deadlock
- mehrere Ressourcen pro Typ: existierende und verfügbare Ressourcen ($E,A$) werden in einer Belegungs- und einer Anforderungsmatrix($C,R$) dargestellt
	- Summe aller belegten und freien Ressourcen muss der Gesamtzahl der Ressourcen entsprechen
	- **Algorithmus**
		- Suche nach einem unmarkierten Prozess $P_i$, für den die $i$-te Zeile von $R$ kleiner oder gleich $A$ ist
		- Exisitiert ein solcher Prozess, addiere die $i$-te Zeile von $C$ zu $A$, markiere den Prozess und wiederhole
		- Andernfalls beende den Algorithmus; alle nicht markierten Prozesse sind in Deadlock

### Verhinderung

- Ein Zustand heißt **sicher** , wenn kein Deadlock vorliegt, und es eine Scheduling-Reihenfolge gibt die nicht zum Deadlock führt
- Ein **unsicherer Zustand** stellt noch keinen Deadlock dar. Es gibt nur keine Garantie, das alle Prozesse zu Ende laufen können

#### Bankier-Algorithmus

- Bankier hat so viele Ressourcen, dass er das größte vorhandene Limit gerade noch bedienen kann
-  Kunde bekommt die Ressource, falls der Banker danach noch genügend Ressourcen hat, um mindestens einem der Kunden sein komplettes Limit zuteilen zu können
- Algorithmus überprüft bei jedem Kundenantrag, ob die Freigabe zu einem unsicheren Zustand führt (wenn ja ablehnen, sonst freigeben)

**Algorithmus**

- Suche Zeile aus $R$, die kleiner oder gleich $A$ ist. Wenn es keine solche Zeile gibt, kann kein Prozess beendet werden (Deadlock)
- Nimm an, dass der Prozess, der der gewählten Zeile entspricht, alle nötigten Ressourcen reserviert und seine Ausführung beendet. Markiere den Prozess als beendet und addiere seine Ressourcen zu $A$.
- Wiederhole Schritt 1 und 2, bis alle Prozesse markiert sind oder ein Deadlock auftritt. Im ersten Fall ist der Zustand sicher, im Zweiten unsicher.

**Probleme**

- Prozesse wissen nicht im Voraus, wie viele Ressourcen sie brauchen
- Anzahl der Prozesse ist nicht konstant
- Ressourcen können plötzlich verschwinden

> Deadlock-Verhinderung ist im Grunde unmöglich

#### Im realen System

- Eine der vier Voraussetzungen eliminieren

**Mutual Exclusion**

- Spooling-Prinzip: Dienst verwaltet Ressource (kann von mehreren Prozessen angefordert werden)
- z.B. Drucker
- nicht bei allen Ressourcen möglich

**Belegungs- und Wartebedingung**

- Jeder Prozess fordert seine Ressourcen im Voraus an (Ausführung nur, wenn alle verfügbar)
- Problem: benötigte Ressourcen meist icht im Voraus bekannt
- Alternative: Prozess gibt vor Anforderung alle Ressourcen kurzzeitig frei und reserviert dann alles auf einmal

**Ununterbrechbarkeit**

- kein erfolgsversprechender Ansatz
- Prozessen Ressourcen zu entziehen ist schwierig oder unmöglich (z.B. gerade genutzter Drucker)

**Zyklische Wartebedingung**

- Ressourcen durchnummerieren -> Alle Prozesse dürfen nur in aufsteigender Reihenfolge reservieren
- Beleguns-Anforderungs-Graph immer zyklenfrei
- Alternativ: jeder Prozess darf nur Ressourcen mit kleinerer Nummer anfordern, als bereits reservierte

#### Realität und zukünftige Entwicklung

-  Vorherrschaft des sequentiellen Programmiermodells impliziert keine Dringlichkeit Betriebssysteme mit Methoden zur Vermeidung von Verklemmungen auszurüsten
- Verfahren zum Erkennen und Vermeiden von Deadlocks sind praxisuntauglich
- Latente Verklemmungsgefahr durch Virtualisierung und Bereitstellung logischer Geräte abgefangen
- Wachsende Verbreitung des nebenläuﬁgen Programmiermodells (Parallelarbeit - Threads) impliziert steigende Konkurrenz um die Ressourcen
- Deadlocks erfahren zunehmend Bedeutung in der Praxis
