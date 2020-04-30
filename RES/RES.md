# Betriebssysteme

## Grundlagen

### Prinzipieller Aufbau eines Rechnensystems

- Anwendersoftware
- Compiler, Datenbanken, Dienstprogramme
- Betriebssystem
- Maschinensprache
- Mikroarchitektur/Gerätetreiber/Hardware-Software Interface (HSI)
- Physische Geräte

### Systemsoftware

- Betriebssystem und seine Hilfsprogramme
- Unterteilung in:
	- Systemsprogramme/Betriebssystem (Steuerprogramme, Übersetzer, Dienstprogramme, ...)
	- Anwendersoftware (eigene Programme, Bibliotheken, Softwarepakete, ...)

### Betriebssystem als erweiterte Maschine

- Betriebssystem macht die Nutzung eines Computers möglich
- Betriebssystem = Software $\neq$ Betriebssystem
- OS dient als erweiterte Maschine (Abstraktion der Hardware) und Ressourcenmanager
	- Abstraktion der konkreten Instruktionssatzarchitektur, Eigenschaften Zentraler Hardware, Ein-/Ausgabeschnittstellen und Peripheriegeräte
- Anwendersicht:
	- Reale Maschine = Zentraleinheit + Hardware
	- Abstrakte Maschine = Reale Maschine + OS
	- Benutzermaschine = Abstrakte Maschine + Anwendungen

**Das Betriebssystem ist eine virtuelle Maschine, die von der Hardware abstrahiert**

### Betriebssystem als Ressourcenmanager

- aktive Ressourcen (Prozessor [Tastatur, Monitor, Netwerk]) verarbeiten passive Ressourcen (Hauptspeicher [Platte, Bänder, CD])
- Alle Ressourcen eines Computersystems (CPU, RAM, Festspeicher) = Betriebsmittel
- Betriebsmitteln = abstrakte Ressource -> verfügt über ID, Adressbereich, Wertebereich und Funktion
- Klassen von Betriebsmitteln:
	- Entziehbarkeit: entziehbar (z.B. Prozessor) oder nicht (z.B. Dateideskriptor)
	- Zuteilbarkeit: gleichzeitig (z.B. Speicher) oder exklusiv (z.B. Prozessor)
	- Wiederverwendbarkeit: einmalig nutzbar (z.B. Interrupt) oder mehrfach (z.B. CPU, Speicher)
	- Hardware/Software: physikalisches/logisches Betriebsmittel

### Das Betriebssystem in der Definition

**DIN 44300:** __Die Programme__ eines digitalen Rechnersystems __, die zusammen__ mit den Eigenschaften dieser Rechenanlage die Basis der möglichen Betriebsarten des digitalen Rechnersystems bilden und die insbesondere __die Abwicklung von Programmen steuern und überwachen__

### Betriebssystem als Schalen-/Schichtenmodell

**Schichtenmodell**
- Benutzer -> Programm -> Betriebssystem -> Hardware
- Jeder der Schichten wird durch eine Menge an Operationen definiert, die sie bereitstellt (Schnittstelle)

**Schalenmodell**
- HW-spezifische Funktionen auf der untersten Ebene -> aufbauende, elementare Betriebssystemfunktionen -> Schichten für Kommunikation/Dateisysteme/...

| Vorteile | Nachteile |
|----------|-----------|
| - Reduzierte Komplexität (nur Betrachtung der Schnittstellen) | - erhöhte Komplexität der vertikalen Kommunikation (nur durch einzelne Schichten möglich)|
| - Austausch einzelner Schichten durch definierte Schnittstellen möglich (Gesamtsystem bleibt erhalten)| - Effizienz-, Reibungsverluste und lange Pfade |

### Aufgaben eines Betriebssystems

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

### Arten von Betriebssystemen

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

### Bits und Bytes

- **Bit:** kleinstmögliche Speichereinheit
- **Byte:** 8 Bits
- **Si-Präfixe:** 10er- Potenz als Basis (kb, MB, GB, TB, PB, ... -> $=10^x$ Byte) 
- **IEC-Präfixe:** 2er- Potenz als Basis (KiB, MiB, GiB, TiB, PiB, ... -> $=2^x$ Byte)
