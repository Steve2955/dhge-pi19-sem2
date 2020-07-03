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
	- Umrechnung innerhalb: mul. / div. mit $2^3$ (Exponent steigt / fällt um 3)
- **IEC-Präfixe:** 2er- Potenz als Basis (KiB, MiB, GiB, TiB, PiB, ... -> $=2^x$ Byte)
	- Umrechnung innerhalb: mul. / div. mit $2^{10}$ (Exponent steigt / fällt um 10)

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

- Betriebssystem verwaltet eine Prozesstabelle (ein Block/Prozess)
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
- **Kernel-Thread:** dem Betriebssystem bekannt, erhält vom Betriebssystem Rechenzeit

> User-Thread muss einem einem konkreten Kernel-Thread zugeteilt werden, damit er real Ausgeführt wird

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

- Für jeden Prozess exisitert eine Flag
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
- Verbraucher: verbraucht Datenpakete (schläf und wird geweckt, wenn neue Daten vorhanden sind)

**Problemfall**

- Verbraucher wird geweckt, bevor er sich bereits komplett pausieren konnte (Prozessunterbrechung im kritischen Abschnitt Erkennung der Bedingung von Sleep und Aufruf von Sleep)
- Idee: Speicherung der Anzahl der Weckrufe in neuer Variablenart(**Semaphor**)

##### Semaphore

- "Ampel", die immer nur einem Prozess die Benutzung erlaubt und allen anderen verweigert
- Alle Prozesse sind dazu verpflichtet bestimmten Code nur auszuführen, wenn es die Semaphore erlaubt
- Prozesse synchronisieren sich über die Semaphore (Setzen/Rücksetzen der Semaphore bei Betretten/Verlassen kritischer Bereiche)
- Zur Manipulation und Abfrage der Semaphoren exisitieren zwei unteilbare Operationen
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
	- Kurzzeit-(CPU)Scheduler = zuständig für die bereits im Speicher befindlichen rechenbereiten Prozesse
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
- **vektorisiert:** Interruptquelle legt Adresse der ISR auf den Datenbus und verzweigt direkt zum Mikroprogramm
- **nichtvektorisiert:** Interruptquelle legt eine Vektornummer auf den Datenbus, mit der due Adresse der ISR aus einer Vektortabelle ermittelt wird

#### Software-Interrupts

- Aufruf mit speziellen Maschinenbefehlen (nur Nummer für den Interrupt notwendig)
- Mit Nummer in der Interrupt-Vektor-Tabelle wird die Adresse des Interrupt-Unterprogrammes referenziert

#### Traps

- Art automatische Prozeduraufrufe, welche durch eine vom Programm verursachte Bedingung eingeleitet werden (z.B. Gleitkommaüberlauf)
- Bei Auftretten der Bedingung stoppt die Ablaufsteuerung die Ausführung und überschreibt den Programmcounter mit der Adresse des Trap-Handlers
- Wesentliches Merkmal: Auslösung bei Ausnahmebedingungen (durch HW oder Mikroprogramme)

#### Ablauf der Interrupt-Verarbeitung

- Sperren weiterer Unterbrechungen mit gleicher oder geringerer Priorität
- Rettung wichtiger Register-Informationen (Prozessorstatus)
- Bestimmen der Interruptquelle (durch Hardware realisiert)
- Laden des zugehörigen Interruptvektors
- Abarbeitung der Interruptroutine
- Rückkehr zur unterbrochenen Aufgabe

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
- Kunde bekommt die Ressource, falls der Banker danach noch genügend Ressourcen hat, um mindestens einem der Kunden sein komplettes Limit zuteilen zu können
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
- Problem: benötigte Ressourcen meist nicht im Voraus bekannt
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

# Ein- und Ausgaben

## Grundlegende Hardware

- Ein-/Ausgabegeräte als wichtigste Hardwarekomponenten und Kommunikationsschnittstelle
- Varianten mit der Außenwelt zu kommunizieren:
	- Zeichen- vs. block-orientiert
	- Sequentieller vs. wahlfreier Zugriff
	- gemeinsame vs. exklusive Kanäle
	- Geschwindigkeit: Abhängig vom Gerät oder Kommunikationspartner
	- read/write, read only, write only

### Ein-/Ausgabegeräte

- **blockorientierte Geräte:** Informationen in adressierbaren Blöcken fester Größe; Blöcke können unabhängig voneinander gelesen und geschrieben werden
- **zeichenorientierte Geräte:** Zeichenströme ohne Blockstruktur, nicht adressierbar
- jedes Gerät besitzt einen **Controller**
	- verwaltet, steuert ein/mehrere Geräte
	- einfach Schnittstelle zum Betriebssystem
	- besitzen Register und Datenpuffer für die Kommunikation

| Benutzerprozess    |
|--------------------|
| Kernel-Verteiler   |
| Auftragsverwaltung |
| Pufferung          |
| Treiber            |
| Controller         |
| Gerät              |

- idealisierte Struktur einer I/O-Verwaltung
- jede Schicht Kommuniziert nur mit ihren direkten Nachbarn

### Kommunikation mit Controller

Zwei Alternativen:
- Jedem Kontrollregister wird eine **Ein-/Ausgabe-Port-Nummer** zugewiesen
	- Spezielle Ein-/Ausgabebefehle notwendig (Assembler)
- **Memory Mapped Ein-/Ausgabe:** Jedem Kontrollregister wird eine Hauptspeicheradresse zugewiesen
	- Kontrollregister sind Variable im Speicher und können von C aus direkt angesprochen werden

#### Direkter Speicherzugriff

- **Direct Memory Access** (DMA) erlaubt Geräten direkt mit dem Arbeitsspeicher zu kommunizieren (ohne Umweg über die CPU)
- Vorteile: Entlastung des Prozessor und Steigerung der Datenübertragung
- DMA-Controller überträgt Daten zwangsläuﬁg über die gleichen Bussysteme, wie die CPU -> Abstimmung notwendig
	- DMA-Controller fordert die Kontrolle über das Bussystem von der CPU
	- CPU übergibt Kontrolle
	- DMA-Controller führt Datenübertragung aus und gibt Kontrolle an CPU zurück.
- **Transparentes DMA:** DMA-Controller wartet dass CPU keinen Zugriff zum Hauptspeicher durchführt (Nutzung freier Bus-Zyklen)
- **Einzeltranfer:** Gerätecontroller übernimmt kurzzeitig Buszyklus von der CPU zur Übertragung *eines Wort* (kleine Datenrate; auch cycle-steal mode)
- **Blocktransfer:** *Alle Daten* werden unmittelbar hintereinander übertragen, CPU wird eine Zeit lang blockiert  (burstmode)

**DMA-Betriebsphasen**

- Initialisierung: DMA-Controller wird programmiert (Quell und Zieladresse, Anzahl Byte, ...)
- DMA-Betrieb: Controller übernimmt je nach Betriebsart (Einzel- oder Blocktransfer) teilweise oder dauerhaft den Bus
- Abschluss: Die CPU wird mittels Interrupt darüber informiert, dass alle Daten transferiert wurden

## Grundlagen Software

**Ziele**

- Geräteunabhängigkeit
- Abstraktion von den technischen Gerätedetails (Schichtenmodell)
- einheitliche Namensgebung
- Fehlerbehandlung
- Pufferung (z.B. Druckerausgabe)
- Gerätevergabe und Prioritätssteuerung

**Ansätze**

- Programmgesteuert
- Interruptgesteuert
- DMA-Betrieb

### Programmgesteuerte Ein-/Ausgabe

- dauernde Kontrolle über den E/A-Vorgang durch den Prozessor
- Prozessor fragt ständig Ein-/Ausgabegerät ab, ob es für das nächste Zeichen bereit ist (Polling oder busy waiting)
- Vorteil: Einfachheit
- Nachteil: Verschwendung von Rechenzeit durch viele Busy-Waits

### Interruptgesteuerte Ein-/Ausgabe

- Bessere Ausnutzung der Wartezeiten für andere Aufgaben durch Unterbrechungen
- Vorteil: CPU kann bis zum einem Interrupt ungestört Programmcode abarbeiten und nach Behandlung fortsetzen
- Nachteil: Interrupts kosten Zeit

## Gerätetreiber

- **Gerätetreiber:** geräteabhängige Steuersoftware
- für jedes Betriebssystem unterschiedlich
- steuern meist eine Klasse ähnlicher Geräte
- greifen auf die Register des Controllers (HW-Zugriff notwendig)
- vom Hardwarehersteller geschrieben -> erfordert klares Modell und klare Schnittstellen
- Unterteilung in Treiber für Block- und zeichenorientierte Geräte (jeweils mit Standardschnittstelle)

### Aufgaben

- definiert das Gerät und sich selbst gegenüber dem Betriebssystem
- initialisiert den Controller und das Gerät beim Systemstart (Aktiviert das Gerät)
- wandelt allgemeine E/A-Anforderungen in gerätespeziﬁsche Befehle um
- antwortet auf Hardwaresignale (Interrupts)
- meldet Geräte- und Controllerbefehle
- bearbeitet Schreib-und Lesebefehle
- Ereignisverwaltung
- puffert Daten bei der Ein- und Ausgabe

### Struktur

Abhängig vom Betriebssystem...

- müssen alle Treiber in der Systemkonfiguration eingebunden werden (neuer Treiber -> OS neu übersetzen)
- müssen Treiber beim Systemstart bekannt sein
- können Treiber dynamisch während des Betriebs installiert, gestartet/gestoppt werden

Sonderfälle müssen beachtet werden

- Treiber muss Entfernen eines Gerätes umgehen können
	- I/O abbrechen, wartende Anfragen entfernen, Aufrufer informieren
- neue Geräte können dazukommen

## Geräteunabhängige Software

- Teile der Ein-/Ausgabe-Software ist geräteunabhängig durchführbar

**Typische Funktionen**

- Einheitliches Interface
- Pufferung
- Fehlerbericht
- Anforderung/Freigabe von Geräten
- Geräteunabhängige Blockgröße

### Schnittstellen

- Hauptaufgabe: einheitliche Darstellung unterschiedlicher I/O-Geräte und Treiber
- Einheitliches Schnittstellen -> Treiber leichter einbindbar
- Abbildung von Symbolischer Gerätenamen auf eigentliche Treiber

### Pufferung

- Strategie 1: ein Zeichen anfordern Blockieren
	- pro Zeichen einmal Prozess starten viele Kontextwechsel -> Inefﬁzient
- Strategie 2: Prozess stellt Puffer (n Zeichen) zur Verfügung -> Lesebefehl für n Zeichen -> wenn Puffer voll, Prozess aufwecken und Zeichen anfordern
	- Effizienter, aber Pufferspeicher darf nicht ausgelagert werden
- Strategie 3: Puffer im Kernelspace -> Wenn gefüllt, ev. Seite einlagern und Daten in Userspace kopieren
	- Problem: Was tun, wenn Daten ankommen, während kopiert wird
- Strategie 4: zweiter Puffer im Kernel - doppelte Pufferung;
	- Benutzerprozess und Peripheriegerät können parallel arbeiten

### Kommunikation

| Benutzerprozess      | I/O-Aufruf; Formatierung der I/O; Spooling   |
|----------------------|----------------------------------------------|
| Geräteunabhängige SW | Benennung, Schutz, Sperren, Puffern, Belegen |
| Gerätetreiber        | Initialisiere Geräteregister, prüfe Status   |
| Interrupthandling    | Aktiviere Treiber, wenn I/O beendet          |
| Hardware             | Führe I/O-Operationen durch                  |

## Physikalische Geräte

### Plattenspeicher

**Bauelemente einer Festplatte**

- eine/mehrere drehbar gelagerte Scheiben (Platters)
- bewegliche Schreib-/Leseköpfe (Heads)
- jeweils Lager für Platter und Heads
- Steuerelektronik für Antrieb- und Kopfsteuerung
- Hochleistungs-DSP (Digital Signal Processor) für die Schreib/Leseköpfe
- Schnittstelle zur Verbindung mit dem Festplattencontroller
- Festplattencache (meist zw. 2 bis 32 MB Größe)

**Plattengeometrie**

- Festplatte aufgeteilt in Zylinder
- Zylinder aufgeteilt in Spuren
- Spuren aufgeteilt in Sektoren (Datenblöcke zu je 512 Byte)

Lokalisierung eines Datenblocks bzw. Sektors über die CHS bzw. LBA

#### CHS-Adressierung

- CHS (Cylinder-Head-Sector) war eine frühe Methode zum Ansprechen von Festplatten
- Sektoren können bis 8 GByte durch CHS Koordinaten adressiert werden:
	- C: Cylinder, gültiger Bereich: 0-1023 cylinders
	- H: Head, gültiger Bereich 0-254 heads
	- S: Sector, gültiger Bereich 1-63 sectors
- heute in der Regel nicht mehr verwendet

#### LBA-Adressierung

- Logical Block Addressing (LBA)
- Blöcke werden unabhängig von der Geometrie adressiert (Blöcke fortlaufen durchnummeriert -> linearer Adressraum)
- Lokalisierung eines Datenblocks über logische Blockadress
- LBA unterscheidet zwischen Adressen mit 28 (max. 128 GByte) und 48 Bit (max. 128 PByte)
- höheres Abstraktionsniveau: physische Organisation hat für OS keine Bedeutung, physische Beschränkungen aufgehoben
- Aus Gründen der Kompatibilität unterstützen Festplatten jedoch weiterhin beide Adressierungsverfahre
- Festplatten-Controller kann defekte Blöcke ausblenden und Block aus Reserve-Bereich einblenden

#### Fehlerbehandlung durch Controller

Logische Ersetzung defekter Sektoren/Blöcke durch intakte Ersatzsektoren

- in der Produktion:
	- Liste fehlerhafter Sektoren auf Festplatte schreiben und durch Reservesektoren ersetzen (Sector slipping)
- im Betrieb:
	- transiente Fehler verursacht durch feine Staubpartikel – erneutes Lesen funktioniert
	- Sektor wird kaputt -> auf Reservesektor ausweichen (Sector sparing)
	- Verwaltung durch Betriebssystem

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

#### Plattencache

- Plattenspeicher ist langsam (Mechanik der Positionierung) -> Plattencache zur Leistungssteigerung

**Strategien**

- Read cache: Zugriffswahrscheinlichkeit auf folgenden Block ca. 50%
- Write through cache: Vor dem Schreiben prüfen, ob sich Blockinhalt geändert hat
- Write back cache: Schreiboperationen werden nicht sofort ausgeführt, sondern gesammelt (lazy write)

**Typen**

- Buffer cache: Orientierung an logischen Sektoren
- File cache: Orientierung an konkreter Speicherung der Datei (Vorteil bei fragmentierter Datenspeicherung)

#### Interleaving

- Problem: Bis ein Datenblock komplett übertragen war rotierten die nächsten Blöcke unter dem Schreib-Lesekopf hindurch -> Zugriff auf nachfolgenden Block erst nach einer kompletten Umdrehung
- Lösung: Änderung der Nummerierung der Blöcke durch Auslassung (interleaving)
- logische Sektornumerierung stimmt mit der physikalischen Numerierung nicht überein
- Verhältnis zwischen den beiden Numerierungen wird als Interleave-Faktor bezeichnet
	- 1:1 - fortlaufende Nummerierung
	- 1:2 - übernächster Sektor hat die folgende Sektornummer
	- 1:3 - zwei Sektoren werden übersprungen
- hat an Bedeutung verloren

# Speicherverwaltung

- Speicher als wichtigste Ressource ist begrenzt und muss sorgfältig verwaltet werden
- Programme wachsen schneller als der verfügbare Speicher -> Speicherhierarchie

## Speicherhierarchie

- Speicherverwaltung = Teil des Betriebssystems, dass die Speicherhierarchie verwaltet
- Überwacht belegten Speicher, teilt Prozessen Speicher zu und gibt ihn wieder frei
- Außerdem: Auslagern von Speicher (Swapping), wenn der Hauptspeicher zu klein ist

**Speicherverwaltungssysteme**

- Prozesse werden zwischen Hauptspeicher und Platte hin- und hergeschoben (Swapping und Paging)
- Direkte Speicherverwaltung ohne Auslagerungen (Ein- und Mehrprogrammbetrieb)

**Anforderungen nach Lister/Eager**

- Relokation
- Schutz
- Gemeinsame Nutzung
- Logische Organisation
- Physikalische Organisation

### Relokation - Verlagerbarkeit

- Auslagern und Wiedereinlagern ganzer Prozesse aus dem Hauptspeicher
- Ort der Einlagerung zum Zeitpunkt der Programmübersetzung unbekannt
- Problem: Speicherrefernzen innerhalb des Programmes
	- Absolute Sprungbefehle
	- Datenzugriffsbefehle
- Übersetzung der Speicherreferenzen im Programmcode in tatsächliche Speicheradressen durch Prozessorhardware und Betriebssystemsoftware

### Schutz

- Schutz von Prozessen gegen Störungen durch andere Prozesse
	- Überprüfung aller Speicherzugriffe nötig
	- nicht zur Übersetzungszeit prüfbar (dynamische Adressen, Relokation)
- Nicht ausschließlich durch Software lösbar (für effektiven Schutz mit Hardwareunterstützung)

### Gemeinsame Nutzung

-  kontrollierter Zugriff mehrerer Prozesse auf gemeinsam genutzte Bereiche des Speichers

**Beispiele**

- Ausführung des gleichen Programms durch eine Reihe von Prozessen -> Code nur einmal im Speicher
- Benuztung gemeinsamer Module (dynamisch gelinkte Bibliotheken)
- Kooperation von Prozessen über gemeinsam genutzten Datenspeicher (shared memory)

### Logische Organisation

- Hauptspeicher ist lineares Feld von Bytes
- Logischer Aufbau großer Programme besteht hingegen aus verschiedenen, evtl. gemeinsam genutzen Modulen, die unabhängig übersetzt wurden
- Betriebsystem muss mit Modulen umgehen können

### Physische Organisation

- Zwei Ebenen
	- Hauptspeicher (schnell, teuer, flüchtig)
	- Hintergrundspeicher (langsam, billig, nicht flüchtig)
- Grundproblem: Organisation des Informationsﬂusses zwischen Haupt- und Sekundärspeicher

## Freispeicherverwaltung

- Betriebssystem verwaltet diesen Speicherbereich als eine Kette von freien Speicherblöcken
- Jeder dieser Blöcke enthält Informationen (Gesamtlänge, nächster freie Block, ...)
- Wird Speicherplatz angefordert kann dieser mit verschiedenen Strategien durchlaufen werden

**Strategien**

- **First-Fit-Verfahren:** Durchlaufen des Speicherbereiches, Allokation des erstbesten freien Bereiches
- **Next-Fit-Verfahren:** Wie First-Fit, aber aufeinanderfolgende Suchen werden bei zuletzt gefundenem Speicherplatz begonnen
- **Best-Fit-Verfahren:** Durchsuchen der gesamten Speicherliste, Allokation des kleinsten Bereichs (optimale Ausnutzung)
- **Worst-Fit-Verfahren:** Allokation des größten freien Bereichs
- **Quick-Fit-Verfahren:** unterhält getrennte Listen für freie Bereiche gebräuchlicher Größe
- **Buddy-Verfahren:** für jede Speichergröße eine eigene Liste (nur Blöcke von Zweierpotenzen verwendet)
	- ist kein gewünschter Block frei, wird ein Block in zwei gleich große Blöcke aufgeteilt

## Direkte Speicherverwaltung

### Monoprogrammierung

- Betriebssystem belegt feste Speicherbereiche
- freier Speicher wird einem Benutzerprogramm zur Verfügung gestellt
- Programm organisiert seinen Speicherbedarf selbst
- Solche Struktur nur für einen laufenden Prozess möglich

### Multiprogrammierung

- Mehrere Prozesse werden vollständig im Hauptspeicher gehalten
- Aufteilung des Hauptspeichers in feste Partitionen (gleiche oder unterschiedliche Größe)
- Getrennte Warteschlangen für jede Partition
	- Auftrag wird der kleinsten Partition, die groß genug für ihn ist, angehängt
	- Nachteil: Schlange für große Partitionen leer, für kleine voll
- gemeinsame Warteschlang für alle Partitionen
	- First Fit: In eine freie Partition wird der erste passende Auftrag geladen
	- Next Fit: Wie First Fit, Suche ab aktueller Position
	- Best Fit: Ist eine Partition frei, wird die ganze Schlange durchsucht und der größte passende Auftrag geladen

#### Partitionierung

**Statische Partitionierung**

- Programm zu groß für Partition -> aufwändige Programmerstellung durch Overlays nötig
- Interne Fragmentierung (Platzverschwendung)
- Fest vorgegebene Anzahl von Prozessen im Speicher
- Laden von Prozessen in Speicher: evtl. Auslagern von anderen Prozessen
- Zuweisung von Partitionen an Prozesse
	- Bereiche gleicher Länge: trivial
	- Bereiche variabler Länge: kleinste verfügbare ausreichend große Partition

**Dynamische Partitionierung**

- Einteilung des Speichers in Partitionen mit variabler Länge und Anzahl
- Prozesse erhalten exakt passende Speicherbereiche
- Ein- und Auslagern führt zu externer Fragmentierung (Defragmentierung erforderlich)

#### Modellierung der Multiprogrammierung

- Betrachtung der CPU von einem probabilistischen Standpunkt
- Ein Prozess wartete einen Anteil $p$ auf das Ende von I/O-Operationen (I/O wait)
- Bei $n$ Prozessen im Speicher ist die Wahrscheinlichkeit, das alle gleichzeitig auf I/O-Operationen warten $p^n$ (CPU wird nicht genutzt)
- Ausnutzung $A$ aus dem Grad der Multiprogrammierung $n$:

$$A=1-p^n$$

**Grenzen des Modells**

- probalistisches Modell ist nur eine Annährung, weil es annimmt, dass die Prozesse unabhängig voneinander sind
- in einem realen System kann die CPU nur einen gleichzeitig Prozess ausführen -> andere müssen warten (nicht unabhängig)
- Dennoch: Multiprogrammierung verbessert die Ausnutzung der CPU

### Probleme der direkten Speicherverwaltung

- Speicherfragmentierung
- Programme größer als verfügbarer Speicher
- Relokation von Programmcode (absolute Speicheradressen müssen umgeschrieben werden)
- Prozess muss in einem Stück im Speicher liegen
- Verwendung von absoluten Adressen kann zu Speicherschutzverletzungen führen
- Lösung: **Virtueller Speicher**

## Virtueller Speicher

- mehrere Fragmente müssen für das Programm so dargestellt werden, als ob sie aus einem kontinuierlichen Bereich stammen
- Verlangt ein Programm mehr Speicher als vorhanden, wird der inaktive Teil ausgelagert (geswappt)
- Umsetzung der virtuellen in eine physische Adresse durch die Memory Management Unit (MMU)

### Implementierung

- Jeder Prozess besitzt eigenen virtuellen Adressraum
- virtueller Adressraum besteht aus gleich großen Seiten (page)
- Arbeitspeicher unterteilt in gleich große Kacheln (page frame)
- i.d.R.: $\text{page} = \text{page frame} \quad \text{oder} \quad \text{page} * n = \text{page frame}$
- Hintergrundspeicher aufgeteilt in zusammenhängende Blöcke gleicher Größe
- nur Blöcke des Hintergrundspeicher adressierbar
- Verwaltung der Adresse und des Zustand jeder Seite in einer Seitentabelle
- Typische Größe eines Seitentabelleneintrags: 32 Bit (Zugriffsrechte, Informationsbits für Speicherverwaltung, Seitenrahmennummer)

### Paging

- Abbildung logischer Adressen auf physikalische durch Zerlegung
- Virtuelle Seite wird gegeben durch $v=(s,w)$ mit Seitennummer $s$ und Offset in der Seite $w$
- Abgebildet wird $v$ auf die reale Adresse $p=(k,w)$ mit der Kachelnummer $k$
- Wortbreite von 64 Bit -> Seitentabelle hat $2^{52} = 4∗10^{15}$ Einträge -> Grenzen des Systems erreicht
- Extrem große Seitentabelle für jeden Prozess lässt schnelle Adressumrechnung nicht mehr zu
- Lösungsansätze:
	- Adressbegrenzung: Begrenzung des Adressraums (Speicher) pro Prozess
	- Mehrstufige Seitentabellen: Reduktion des Verwaltungsaufwandes mit Untertabellen
	- Invertierte Seitentabellen: Statt Seitentabelle für Prozess -> Seitentabelle für physikalisch vorhandene Seiten (Abbildung aufwendiger)
	- Assoziativer Tabellencache: Hardware, die virtuelle Adressen ohne Umweg auf physische abbildet (auch TLB - Translation Lookaside Buffer; heutiger Standard)
		- wird eine virtuelle Seite im TLB gefunden (TLB Hit), kann die Adressumrechnung direkt erfolgen ($> 99\%$)
		- war die Suche im TLB erfolglos (TLB Miss), muss auf die Seitentabellen im Arbeitsspeicher zurückgegriffen werden

#### Seitenersetzungsstrategien

- wird es versucht auf eine Seite zuzugreifen, die nicht im physischen Speicher liegt, wird ein  Systemaufruf mit einem Seitenfehler (page fault) ausgelöst
	- wenig genutzter Speicherrahmen wird ausgelagert, angeforderte Seite wird in den freien Rahmen geladen
	- Anpassung der Seitentabelle, Wiederholung des Befehls
- richtiges Auslagern ist eines der größten Probleme virtueller Speichersysteme (extreme Auswirkungen auf Gesamtleistung)
- Worst case: ausgelagerte Seite wird sofort wieder benötigt -> Seitenflattern (trashing)

**Optimale Seitenersetzungsstrategie**

- lagere die Seite aus, für die der nächste Zugriff am weitesten in der Zukunft liegt (theoretisch beste Strategie)
- jedoch unmöglich, herauszufinden, welche Seite wann als nächstes gebraucht wird (praktisch nicht umsetzbar)
- Auch bekannt als **Belady-Theorem der optimalen Verdrängung**
- Dient als Referenz für andere Strategien:
	- **NRU:** teilt Seiten anhand ihrer R- und M-Bits in vier Klassen ein und entfernt zufällig eine Seite aus der niedrigsten, nicht-leeren Klasse
	- **FIFO:** Auslagern der Seite, die sich am längsten im Hauptspeicher befunden hat (älteste Seite)
	- **Second-Chance:** FIFO mit R-Bit Überprüfung (verhindert auslagern häufig genutzer Seiten)
	- **LRU:** Auslagern der Seite, auf die am längsten nicht mehr zugegriffen wurde (aufwändig, Umsetzung über Hardware)
	- **NFU:** Seite, die am seltensten benutzt wird, soll ausgelagert werden (mit Zähler realisiert; Problem: anfangs viel genutzte Seiten werden nicht augelagert)
	- **Aging:** Software-Simulation von LRU (alle Zähler 1 Bit nach rechts, R-Bit addiert)
	- **Clock:** analog Second-Chance -> Uhrzeiger wandert so lange um die Elemente, bis eine Seite mit einem zurückgesetzten R-Bit gefunden wird
	- **WSClock:** Kombination aus Working-Set (Menge von Seiten eines Prozesses) und Clock

#### Belady’s Anomalie

> Eine Erhöhung der Anzahl der Kacheln verbessert für eine gegebene Seitenersetzungsstrategie nicht immer die Page Fault Rate

#### Aufwand von Seitenwechseln

- Paging ist zeitaufwendig -> Prozessor muss warten
- Mittlere Speicherzugriffszeit bei Wahrscheinlichkeit $p$ für einen Seitenfehler

$$t_Z=t_{HS}+p*t_{SF}$$

- um Leistungsverluste zu minimieren sollte $p$ sehr klein sein (z.B. durch Vergrößern des Arbeitsspeichers)
- Paging ist für Echtzeitsysteme ungeeignet

### Segmentierung

- Jedes Programm ist aus vielen Teilen zusammengesetzt (Prozeduren, Module, Klassen, Bibliotheken,...)
- Jedes Teil verdient einen eigenen Adressraum (Unterteilung in Segmente unterschiedlicher Länge)
	- wenige große Segmente (Programmcode, Daten, Stack)
	- mehrere mittelgroße Segmente (Prozeduren, Module, Bibliotheken)
	- extrem viele kleine Segmente (Objekte, Verbunde)
- Hilfreich für mehrfache Ausführung des gleichen Programmes, Kommunikation über gemeinsame Segmente und shared libraries

#### Prinzip

- oft auch Prinzip der gestreuten Speicherung (einzelne Seiten liegen nicht sequentiell im Speicher)
- Definition eines Segmentes durch: Segmentbasis (Erste Adresse im Segment) und Segmentlänge (Zahl der aufeinanderfolgenden Adressen des Segmentes)
- direkte Segmentierung des physischen Adressraum oder eines virtuellen linearen Adressraum, der auf den physischen abbildet
- Segmentierung bildet einen logischen Adressraum:
	- Segmentselektor $s$: direkt oder indirekte (durch Segmentverwaltungstabelle) Bestimmung des adressierten Segments
	- Offset $d$: Speicherstelle relativ zum Segmentanfang
- Jedem Programm ist eine Segmenttabelle zugeordnet: physische Anfangsadresse $b$ und Länge $l$ aller logischen Segmente $s$
- physikalische Adresse ergibt sich aus $b + d$

#### Segmentierung mit Paging

- Segmentierung: Einteilung des virtuellen Speichers in verschiedene feste Bereiche für jeden Prozess
- Paging: Einteilung von virtuellem und physischem Speicher in Bereiche (unabhängig von den einzelnen Prozessgrenzen)
- Paging ist im Gegensatz zu Segmentierung nie vom Programmierer zu beeinflussen ("transparente Operation")
- Häufig werden aber Segmentierung und Paging kombiniert, so dass eine zweistufige Adressierung entsteht

#### Segmentierung vs. Paging

- Segmente dienen zur Aufteilung des Adressraumes nach semantischen Kriterien
- Paging ist ein technisches Hilfsmittel zur Vereinfachung der Speicherverwaltung und Implementierung eines virtuellen Speichers
- Segmente sind die bessere Abstraktion zur Verwaltung von Teilhaberschaften (shared libraries/text/memory), aber problematisch in Bezug auf die Speicherverwaltung (externe Fragmentierung, ...)
- Segmentierung kann problemlos auf Paging aufgesetzt werden
	- Anfang und Größe der Segmente auf ein Vielfaches der Größe von Seitenrahmen beschränkt
	- impliziert interne Fragmentierung (i.d.R. unproblematisch)
- Fast alle modernen Betriebssysteme verwalten Adressräume auf logischer Ebene als eine Menge von Segmenten

### Flat Memory Model

- wurden erst mit 32 Bit Prozessoren möglich
- keine Segmente zur Adressierung des Speichers mehr nötig
- linearer Adressraum beinhaltet Programmcode und Daten (-> direkte Adressierung aller Speicherzelle)
- Befehlszeiger (EIP) kann jeden Maschinenbefehl innerhalb der 4 GB ansprechen
- Segmentregister (CS, DS, SS, ES) speichern nun die Adresse des 4 GB Flat Segment im virtuellen Speicher -> fester Bestandteil des Betriebssystems, nicht veränderbar
- ESI, EDI und EBX sind 32 Bit Allzweckregister und referenzieren auf Daten die im Speicher abgelegt sind

# Dateisysteme

- Daten müssen in einen nicht flüchtigen Speicher geschrieben werden können
- Anforderungen:
	- Möglichkeit große Mengen an Informationen zu sammeln
	- Informationen müssen die Terminierung des auf sie zugreifenden Prozesses überdauern (Persistenz)
	- mehrere Prozesse müssen gleichzeitig auf die Informationen zugreifen können
- Dateien werden durch Dateisystem verwaltet (= Teil des Betriebssystem)
- Dateisystem vermittelt zwischen der logischen Sicht von Dateien und Verzeichnissen und der physikalischen Sicht von Blöcken, Spuren, Sektoren, Geräten, Netzlaufwerken
- Abstraktion des Betriebssystems zur geräteunabhängigen Verwaltung von Dateien

## Dateien

- Dateien besitzen fast immer einen **Dateinamen** sowie **Attribute** (**=Metadaten**)
- Dateinamen sind in speziellen Dateien, den **Verzeichnissen**, abgelegt
- **Dateisystem** bildet einen **Namensraum**
- Alle Dateien sind so über eine eindeutige Adresse (Dateiname inkl. Pfad) innerhalb des Dateisystems aufrufbar

**Namenskonventionen**

- Regeln zur Benennung von Dateien variieren von System zu System
	- Unterschiedliche Längen und Zeichen (Buchstaben, Zahlen, Sonderzeichen) erlaubt
	- Unterscheidung zwischen Groß- und Kleinschreibung
- Üblich: zweiteilige Dateinamen bestehend aus Dateiname und Dateinamenserweiterung (durch Punkt getrennt)

### Dateistruktur

- eine Datei besteht aus einer Folge von Worten/Bytes
- Durch Einfügen spezieller Kontrollzeichen können kompliziertere Strukturen dargestellt werden:
	- Einfach Verbund-Struktur (Record): Zeilenstruktur, Datensätze fester/variabler Länge
	- Komplexe Strukturen: formatiertes Dokument oder ausführbares Programm

### Zugriff

- **sequentieller Zugriff:** Datensätze einer Datei werden vom Anfang der Reihe nach gelesen (kein Überspringen)
- **Direktzugriff:** Datensätze können in beliebiger Reihenfolge gelesen werden (random access)

### Attribute

- Dateiattribute = spezifizierende Eigenschaften (abhängig vom OS)

**Beispiele**	 

- Dateirechte
- Besitzer
- Ersteller
- Zeitpunkt der Erstellung/letzten Änderung/letzten Zugriffs
- aktuelle Größe
- ...

### Dateioperationen

Zugriff auf Dateien erfolgt durch Systemaufrufe die das Betriebssystem zur Verfügung stellt

- open, close: Öffnen und Schließen einer Datei
- read, write: Lesen und Schreiben
- create, delete: Erzeugen und Löschen
- seek: Neupositionierung des Schreib/Lese-Zeigers
- get/set attributes: Auslesen und Setzen der Dateiattribute
- rename: Dateinam ändern

## Verzeichnisse

- heute allgemein übliche Methode von Betriebssystemen, den Zugriff auf Dateien zu organisieren
- Verzeichnisse sind selbst Dateien, erkennbar am Typ "Verzeichnis"
- enthalten Dateinamen: entweder weitere Dateiverzeichnisse oder andere Dateien (-> Baumstruktur)
- globales Wurzelverzeichnis (root-Directory) oder mehrere Wurzelverzeichnisse, die logischen Laufwerken zugeordnet sind
- Weg durch das Dateisystem = Pfad
	- absolute Pfadnamen (relativ zur root-Directory)
	- relative Pfadnamen (relativ zum aktuellen Verzeichnis)

### Verzeichnisoperationen

- erlaubten Systemaufrufe für die Verwaltung von Verzeichnissen sind stark Systemabhängig
- analog zu Systemaufrufen für Dateioperationen:
	- Anlegen, Löschen,
	- Umbenennen,
	- ...
	- Linken und Unlinken

## Dateiverwaltung

- Dateien sind logisch Folgen von Elementen
	- Bytes: einfachte Sicht
	- Blöcken: folgt physischen Begebenheiten
	- Datensätze: logische Sicht (heute kaum noch vertretten)
- Betriebsystem sieht eine Datei als Folge von Blöcken
- logischen Blöcken müssen physische Blöcke zugewiesen werden (nicht notwendig zusammenhängend)

### Zusammenhängende Belegung

- jede Datei wird in einer kontinuierlichen Folge von Blöcken abgespeichert
- Zugriff auf Datei über Startblock und Anzahl belegter Blöcke
- einfache Implementation, hohe Lesegeschwindigkeit
- nachträgliche Änderung der Dateigröße problematisch (-> externe Fragmentierung)

### Verkettete Blockliste

- zu Beginn jedes Blockes wird ein Zeiger auf den nächsten Block gespeichert (Rest des Blockes = Daten)
- Zugriff erfolgt nur noch über Startblock
- keine externe Fragmentierung, aber sehr langsamer wahlfreier Zugriff

### Zentrale Indexstruktur

- zentrale Tabelle (File Allocation Table, FAT) verwaltet alle Blöcke des Dateisystems, Blocknummer ist Index
- für jeden Block einer Datei wird in der FAT der Index des Folgeblocks gespeichert (physisch beliebig verteilt)
- FAT ist auf Datenträger gespeichert (wird vollständig oder partitiell in den Hauptspeicher geladen)
- bei Verlust oder Zerstörung der FAT ist das zugehörige Dateisystem nicht mehr nutzbar
- Zugriff auf eine Datei über Index des Startblocks im Verzeichnis-Block
- für heutige Speicherkapazitäten zu groß
- aktuell genutzt als universelles Austauschformat über Betriebssystemgrenzen hinweg

### Verteilte Indexstruktur

- für jede Datei existiert eine eigene Indexliste mit den Nummern aller benutzten Blöcke (I-Node)
- Indexliste einer Datei wird in separatem Indexblock im Dateisystem gespeichert; bei langen Dateien  mehrere Indexblöcke
- Indexblöcke können zudem Attribute der Datei beinhalten
- i-node muss sich nur im Hauptspeicher befinden, wenn die Datei geöffnet ist
- Dateisystemkonzept von Unix/Linux, Windows

## Implementierung

- Dateisysteme werden auf externe Speicher geschrieben, die in eine oder mehrere Partitionen unterteilt werden können
- Sektor 1 wird als MBR (Master Boot Record) bezeichnet und enthält:
	- Code, der vom BIOS beim Starten des Rechners ausgeführt wird (Bootloader)
	- Partitionstabelle mit Anfangs- und Endadresse jeder Partition
	- Markierung einer aktiven Systempartition, von der gebootet wird
- erster Block in jeder Partition ist ein Bootblock (Bootsektor): Programm zum Start des Betriebssystems
- Aufbau einer Partition ist vom jeweiligen Dateisystem abhängig

### FAT Partition

- FAT-Dateisystem Eintrag enthält:
	- Alle Informationen über die Datei
	- Verweis auf den Anfang der Liste von Blöcken
- Achtung: verschiedene Versionen

### Unix Partition

- Superblock enthält Verwaltungsinformationen des Dateisystems
- UNIX-Dateisystem Eintrag enthält:
	- Dateiname
	- Verweis auf I-Node-Datenstruktur
- I-Node beinhaltet:
	- Dateityp
	- Eigentümer
	- Gruppe des Eigentümers
	- Zugriffsschutzbits
	- Datumseinträge
	- Anzahl der Links für diesen I-Node
	- Zeiger auf den Dateiinhalt

## Verwaltung physischer Blöcke

- Jedes Betriebssystem verwaltet pro Dateisystem eine Menge von physikalischen Blöcken (in Teilmengen Unterteilt)
- **Bad-Block-Liste:** Defekte Blöcke, die nicht mehr verwendet werden können
- **Liste benutzter Blöcke:** Blöcke, die derzeit von Dateien genutzt werden
- **Liste freier Blöcke:** Blöcke, die derzeit nicht genutzt werden
- **Papierkorb-Liste:** Blöcke, die kürzlich genutzt und dann gelöscht wurden (Reaktivieren möglich)

### Blockgröße

- Laufwerke verwalten auf der untersten Ebene meist Sektoren zu 512 Byte (sehr große Anzahl von Blöcken)
- Zusammenfassung von mehreren Sektoren zu einer Zuordnungseinheit (Cluster)
- wenige Sektoren/Zuordnungseinheit: Verwaltung träge (Datenstrukturen umfangreich)
- viele Sektoren/Zuordnungseinheit: Verwaltung verschwenderisch (kleine Datei muss mindestens einen Block belegen)

## Verwaltung freier Blöcke

- **Verkettete Liste** von Plattenblöcken, in der jeder Block so viele Blocknummern wie möglich hat
- **Bitmap:** Platte mit n Blöcken benötiget eine Bitmap mit n Bits; freie/belegte Blöcke durch 0/1 dargestellt

## Eigenschaften guter Dateisysteme

- Möglichst wenige E/A-Transporte
	- Puffertechniken mit Buchführung, welche Blöcke sich zur Zeit in Puffern des Arbeitsspeichers befinden
	- Vorausschauende Lese-/Schreibstrategien im E/A-System
- Unabhängigkeit von Satz-/Blocklänge flexible Wahl von Blockanzahl und -länge durch Programmierer vermeidet Speicherplatzvergeudung durch bessere Anpassung von Satz- und Blocklänge
- Automatische Lagebestimmung von Dateien
	- Verwaltung der Zuordnung "Dateiname <-> physikalische Blocknummer" ist Aufgabe des Dateisystems, nicht des Programmierers
	- Verwendung von "frei"-Einträgen im Dateiverzeichnis
- Dynamische Speicherplatzzuweisung
- Flexible Benennung von Dateien

# Sicherheit

## Anforderungen

- **Vertraulichkeit:** Nur berechtigte Personen haben Zugriff auf das System
- **Integrität:** Nur berechtigte Personen dürfen Änderungen am System vornehmen
- **Verfügbarkeit:** Niemand darf das System stören, sodass es unbenutztbar wird
- **Authentizität:** System kann die Identität des Nutzers feststellen

## Bedrohungen

- **Unterbrechung:** Angriff auf die Verfügbarkeit (Zerstörung der Hardware)
- **Abhören:** Angriff auf die Vertraulichkeit (Unerlaubtes Kopieren von Dateien)
- **Veränderung:** Angriff auf die Integrität (Ändern des Inhalts einer Nachricht)
- **Fälschung:** Angriff auf die Authentizität (Einschleusen von Datensätzen in eine Datenbank)

### Passive Bedrohungen

- Aufdecken von Nachrichteninhalten (Zugriff auf sensible Daten während der Kommunikation)
- Datenflussanalyse
	- Angreifer kann Standort und Identität der kommunizierenden Hosts feststellen (+ Häufigkeit/Dauer der Kommunikation)

> Passive Angriffe lassen sich nur schwer erkennen, da keine Daten verändert werden

### Aktive Bedrohungen

- Maskerade (Vorgabe falsche Identität)
- Replay-Angriff (Senden zuvor aufgezeichneter Daten)
- Ändern von Inhalten (verändern, verzögern, neu strukturieren)
	- Austausch von Namen -> Angreifer erhält Zugriff auf vertrauliche Daten
- Denial-of-Service-Angriff (Server im Netzwerk stilllegen)
	- Server mit einer Flut von Anfragen überfordern

## Schutz

### Schutz durch das Betriebssystem

- **Kein Schutz:** Nur eigene Prozesse laufen
- **Isolation:** Jeder Prozess verfügt über eigenen Adressraum, Dateien und andere Objekte
- **Alles oder nichts freigeben:** Besitzer entscheidet ob öffentlich oder privat
- **Freigabe über Zugriffsbeschränkungen:** Betriebssystem prüft Berechtigung des Zugriffs
- **Freigabe über dynamische Zugriffsbeschränkungen:** Erzeugung von Zugriffsrechten zur Laufzeit
- **Eingeschränkte Nutzung:** Einschränkung nicht nur das Zugriffs sondern auch der Nutzung

#### Benutzerauthentiﬁkation durch das Betriebssystem

- Etwas das der Nutzer **weiß** (Name, Passwort) **besitzt** (Schlüssel, Chipkarte) oder **ist** (biometrische Daten)
- Verbreitetste Lösung: Nutzername und Passwort
	- Computergenerierte Passwörter sind am sichersten, lassen sich schlecht merken
	- Reaktive Passwortprüfung: System versucht Passwort zu knacken
	- Vorbeugende Passwortprüfung: System prüft Passworteingabe des Nutzers auf Sicherheit
	- Mögliche Kombinationen in Abhängigkeit von der Passwort Länge: $C_{max}=n_C^l$ (Länge ist größter Einfluss auf Sicherheit)

##### Passwortsicherheit und UNIX

- durch Salt-Hashverfahren
- Salt-Wert erfüllt drei Funktionen
	- verhindert Passwort-Duplikate in der Passwortdatei
	- verlängert Passwort, ohne dass sich Nutzer mehr merken muss
	- Wörterbuchangriffe werden erschwert, da sich der Hash aus dem Salt-Wert und dem Passwort besteht

##### Passwortsicherheit und Regenbogentabellen

- **Rainbow Table:** Datenstruktur für eine schnelle, speichereffiziente Such nach der ursprünglichen Zeichenfolge eines Hashwert
- Regenbogentabellen sind wesentlich schneller als Brute-Force oder Wörterbuch-Angriffe
- Vorausgesetzt wird eine Hashfunktion ohne Salt

## Angreifer

- **Ziele:** Zugriff auf das System erlangen und/oder Rechte im System erweitern
- **Voraussetzung:** Besitz einer Zugangsberechtigung (meist Name + Passwort)

### Wer?

- Herumschnüffeln von nichttechnischen Benutzern (Mensch ist ein neugieriges Wesen)
- Herumschnüffeln durch Insider (Programmierer, Administratoren und technisches Personal) -> betrachten Sicherheit des Systems zu knacken als persönliche Herausforderung
- Gezielte Versuche mit wirtschaftlicher Motivation
- Militärische- oder Wirtschaftsspionage -> Versuch fremder Länder oder Wettbewerber geheime Informationen zu stehlen

### Wie?

- Ausprobieren von Default-Passwörtern und kurzen Passwörtern
- Ausprobieren mit Hilfe eines Wörterbuches
- Sammeln von Informationen über Nutzer (Familie, Wohnort, Hobbys, ...)
- Ausprobieren von Telefonnummern, Kennzeichennummern, ...
- Umgehung der Zugriffsbeschränkung mit Hilfe eines Trojaners
- Anzapfen der Leitung zwischen Server und Client

> Sicherheitsproblem: Viele Nutzer verwenden leicht zu erratende Passwörter

## Angriffe von Innen

- Ist der Angreifer im System, kann er beginnen Schaden anzurichten
	- Kompromittiert ist die komplette Umgebung des Nutzers, dessen Kennung gebrochen wurde
	- Kompromittierter Zugang kann benutzt werden, um später in weitere Accounts einzubrechen

> Angreifer kann auch ein legitimer Nutzer sein

### Möglichkeiten nach dem Login

- **Trojanisches Pferd:** Schadprogramm, das als nützliche Software getarnt ist
- **Login-Spoofing:** Nutzer wird ein optisch identischer Login präsentiert -> Angaben Angreifer zugänglich
- **Logische Bombe:** Einbau von Code, der nach einer Bedingung schädliche Aktionen auslöst
- **Versteckte Hintertüren:** Teil einer Software ermöglicht umgehen der normalen Zugriffsicherung
- **Pufferüberläufe:** Betriebssysteme werden in C implementiert -> prüft nicht die Einhaltung von Arraygrenzen (Puffer)
	- Große Datenmengen werden in einen dafür zu kleinen reservierten Speicherbereich geschrieben, wodurch nach dem Ziel-Speicherbereich liegende Speicherstellen überschrieben werden (Verfälschung von Daten oder Beschädigung von Datenstrukturen der Laufzeitumgebung)
- **Generische Angriffe:** Basierend auf Ergebnissen von Penetrationstests
	- Anfordern von Datenträgern -> Suche nach Informationen
	- Aufrufen ungültiger Systemaufrufe bzw. Systemaufrufe mit ungültigen Parametern (Systemstörungen)
	- Unterbrechung des Login –> Login erfolgreich
	- Systemprogrammierer überreden eine Hintertür einzufügen
	- Sekretärin des Systemverantwortlichen aufsuchen (bestechen) –> Herausgabe des Passwortes

## Angriffe von Außen

### Voraussetzungen

- Netzwerkinfrastruktur
- Zugang zum Netzwerk
- Schadprogramm, welches sich im Netz verbreiten kann
	- Virus: Code, der sich repliziert indem er sich anderen Programmen anhängt
	- Wurm: Programm, das sich selbst repliziert, nachdem es ausgeführt wurde

### Viren

**Phasen**

- **Schlafphase:** Virus ist inaktiv (Wartet auf Ereignis)
- **Verbreitungsphase:** Virus setzt identische Kopien in andere Programme oder bestimmte Systembereiche
- **Auslösephase:** Virus wird durch eine Reihe von Systemereignissen aktiviert
- **Ausführungsphase:** Schadfunktion wird ausgeführt

**Arten**

- **Parasitäres Virus:** hängt sich ausführbaren Dateien an
- **Speicherresidentes Virus:** infiziert als Teil eines speicherresidenten Systemprogramms jedes ausgeführte Programm
- **Boot-Sektor-Virus:** infiziert MBR, verbreitet sich bei Systemstart
- **Tarnkappen-Virus:** spezieller Virus, der von Antivirensoftware nicht erkannt werden kann
- **Polymorphes Virus:** ändert sich mit jeder Infizierung (kein Erkennen durch Signatur möglich)
- **Makro-Virus:** Virus, der in ein Textverarbeitungsdokument oder ähnliches eingebettet ist

### Würmer

- gleiche Eigenschaften wie Virus
- kann erkennen, ob eine System bereits infiziert ist
- kann Anwesenheit verschleiern, indem er sich wie ein Systemprozess nennt
- benutzt Netzwerkdienste zur Verbreitung (z.B. E-Mail)

### Antivirenprogramme

- ideale Lösung für das Virenproblem ist die **Vermeidung**
- in Realität nicht erreichbar -> Antivirensoftware
- **Problem:** ständiges Wettrüsten zwischen Virenschreibern und Antivirenprogrammierern

## Verdeckte Kanäle

- **Verdeckter Kanal:** parasitärer Kommunikationskanal, welcher Bandbreite eines legitimierten Informationskanals nutzt, um Informationen zu übermitteln
- **Speicherkanal:** Kommunikation über gespeicherte Daten
- **Zeitkanal:** Information werden über die zeitliche Abfolge informationstechnischer Verarbeitungen übertragen
- verdeckte Kanäle in einem Computersystem können weder ausgeschlossen, noch sinnvoll verhindert werden

### Speicherkanal

- Beispiel: Steganographie (verstecktes Schreiben)
	- verändern weniger Details in einem Bild, um weiter Informationen einzubringen
- komprimierten Daten werden verschlüsselt in die niederwertigen Bits jedes Farbwertes (RGB) eingebunden -> Auge kann nicht unterscheiden
- Bei Auflösung von 1024 x 768 Pixel können ca. 295 kByte geheime Informationen gespeichert werden

### Zeitkanal

- Beispiel: Öffnen und Schließen einer Datei oder Setzen von Dateiattributen nach vereinbartem Muster
- Ein Programm manipuliert Datei, ein anderes überwacht diese Datei und interpretiert die sich die Abfolge der Zustände
- kaum möglich, ein solches Verhalten zu erkennen

## Einbruchserkennung

- Schnelle Einbruchserkennung kann Angreifer identifizieren und Schaden begrenzen
- Wirkt abschreckend und kann Angriffe verhindern
- Sammeln von Informationen über Angriffstechniken zur Verbesserung der Einbruchsvermeidung

### Grundlage

- Beruht auf der Annahme, dass sich das Verhalten eines Angreifers von dem eines berechtigten Benutzers so unterscheidet, dass es in Zahlen ausgedrückt werden kann
- Verhaltensprofile von Angreifern und berechtigten Benutzern

### Ansätze

- Statische Anomalieerkennung definiert normales bzw. erwartetes Verhalten
	- Schwellwerterkennung oder profilbasierte Erkennung
- Regelbasierte Erkennung definiert richtigen Verhaltens
	- Suche nach verdächtigem Verhalten oder Abweichungen von normalem Verhalten
- Audit-Protokolle, hier werden alle laufenden Aktivitäten aufgezeichnet
	- Erfassung nativ durch das Betriebssystem oder durch spezielle Software

## Vertrauenswürdige Systeme

- fast alle Computersysteme weisen Sicherheitslücken auf -> Existiert ein sicheres System?
- einzige Möglichkeit Sicheres System zu entwickeln besteht darin es einfach zu halten
- mehr Features = mehr Komplexität, Code, Bugs, **sicherheitskritische Fehler**
- Beispiel: E-Mail mit ASCII-Text sicher -> diverse Probleme bei HTML-Mail
- Um ein sicheres System zu entwickeln braucht man:
	- ein Sicherheitsmodell im Kern des Betriebssystems, das einfach genug ist um wirklich verstanden zu werden
	- Stehvermögen um das Modell nicht durch neue Features aufzuweichen

> Vertrauenswürdige Systeme sind Systeme, die Sicherheitsanforderungen formal festgelegt haben und diesen Anforderungen genügen.

- **Trusted Computing Base:** Kernstück des Systems (Durchsetzung der Sicherheitsregeln)
- **Referenzmonitor:** wichtigster Teil (Verarbeitung aller sicherheitskritischen Systemaufrufe, kann nicht umgangen werden)

### Formale Modelle

- Schutzsysteme auf der Basis dynamischer Zugriffsmatrizen
- Autorisierung ist ein Managementproblem
	- Matrix bestimmt zu jedem Zeitpunkt, nur was jeder Prozess tun kann, nicht ob er wirklich autorisiert ist

### Multilevel Sicherheit

- Benutzerbestimmte Zugriffskontrollstrategie: Benutzer bestimmt, wer seine Dateien und ihre anderen Objekte lesen, schreiben und ausführen darf
- Systembestimmte Zugriffskontrollstrategie: Umgebungen mit Organisation die zusätzliche Regeln und Berechtigungen festgelegt
- weitest verbreitetes Multilevel-Sicherheitsmodell: **Bell-La Padula-Modell**
	- Schützt Vertraulichkeit von Daten durch Kontrolle des Informationsflusses
	- Weitergabe von vertraulichen Informationen an nicht vertrauenswürdige Personen verhindern
	- Regeln:
		- niedriger eingestufte Personen dürfen nicht auf Informationen höher eingestufter Personen zugreifen
		- höher eingestufte Personen dürfen nicht in Informationen von niedriger eingestuften schreiben (keine Weitergabe nach unten)
		- Frei definierbare Zugriffsmatrix, um den Zugriff von Personen auf Objekte anzugeben

#### Biba-Modell

- Schützt Integrität der Daten durch Kontrolle von Lese- und Schreibzugriffen anhand exsitierender Benutzerrechte
- No-Read-Down: Es darf einer höher eingestuften Ebene nicht möglich sein, Informationen einer tieferen Sicherheitsebene zu lesen
- No-Write-Up: auf höhere Schichten kann von tieferen Sichten nicht geschrieben werden

### Orange Book

- teilt Betriebssysteme aufgrund ihrer Sicherheitseigenschaften in sieben Kategorien
- Europäischer Standard: ITSEC -> Neuer allgemeiner Standard: Common Criteria

**Common Criteria**

- Der Evaluation Assurance Level eines Systems ist eine Bewertung nach Abschluss der "Common Criteria" Sicherheitsprüfung
- ansteigenden EAL-Werte spiegeln steigenden Anforderungen wieder
- Übertreffen Systeme die minimalen Anforderungen einer EAL-Stufe so wird dies durch EAL-Wert gefolgt von einem Plus "+" notiert
- Die Zertifizierung EAL4-Standard gehört zu den anspruchsvollsten und teuersten Zertifizierungstests
- Windows und Linux Betriebssysteme sind EAL4+ zertifiziert

## Fazit

- kein System ist absolut sicher
- es tauchen immer wieder Sicherheitslücken auf
- Computersicherheit ist und bleibt ein aktuelles Thema
- Schwerpunkte: Netzwerksicherheit, Benutzerauthentifikation, Kryptographie
