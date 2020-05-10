Versuch 1: Rechneraufbau
========================

# Vorbereitung

## 3.1 Welche grundlegenden Komponenten, außer dem Gehäuse, gehören zu einem Desktop-Rechner (Innereien und Außen rum)?

Intern:
- Netzteil
- Mainboard
- CPU
- RAM
- Festspeicher (HDD/SSD)
- Soundkarte
- DVD-Laufwerk
- Netzwerkkarte
- Kühlung (CPU-Lüfter)

Extern:
- Bildschirm
- Lautsprecher
- Tastatur und Maus
- Netzwerkanbindung (Switch, Router, ...)

## 3.2 Welche Erweiterungssteckplätze sind auf aktuellen Mainboards zu finden (für Steckkarten, Massenspeicher, nicht USB, RAM etc.)?

- PCI
- PCI-Express (x16,8,4,1)
- SATA 3
- M.2

## 3.3 Wodurch zeichnet sich das Funktionsprinzip eines DDR-SDRAM gegenüber SDRAM aus? Was heißt in diesem Fall DDR?

- SDRAM = Synchronous Dynamic Random Access Memory (nur steigend)
- DDR SDRAM = Double Data Rate SDRAM
	- Daten werden bei steigenden und fallenden Flanken transferiert (bis zu doppelte Datenübertragung bei gleicher Taktung)

[Elektronik Kompendium](https://www.elektronik-kompendium.de/sites/com/1312291.htm)

## 3.4 Welche drei Takte spezifizieren die Leistung des Arbeitsspeichers? Erklären Sie diese und wie sie miteinander zusammenhängen!  

- Speichertakt
- I/O-Takt
- effektive Taktfrequenz = Speichertakt * I/O (bei DDR: zweimal eigentliche Taktfrequenz))

[Wiki: DDR-SDRAM](https://de.wikipedia.org/wiki/DDR-SDRAM#Arbeitsweise)

## 3.5 Wie wird die Erhöhung der Datenrate von DDR-SDRAM zu DDR2- und DDR3-Speicher maßgeblich realisiert (zwei sich bedingende Maßnahmen)?

- Erhöhung des I/O Takts -> Erhöhung des effektiven Takts + Übertragungsrate
- Reduktion der Spannung -> gesenkter Stromverbrauch
- Prefetchbuffer Erhöhung -> I/O Takt Erhöhung

[Wiki: DDR-SDRAM](https://de.wikipedia.org/wiki/DDR-SDRAM#Arbeitsweise)

## 3.6 Welche technischen Unterschiede gibt es zwischen DDR3 und DDR4? Stellen Sie diese in einer Tabelle gegenüber!

| DDR3                | DDR4                                                |
|---------------------|-----------------------------------------------------|
| - 240 Kontakte      | - 288 Kontakte (schneller, mechanisch inkompatibel) |
| - geringerer Takt   | - höherer Takt (schneller)                          |
| - geringere Timings | - höhere Timings (langsamer)                        |
|                     | - direkte Anbindung an den CPU-Controller           |
|                     | - verbesserte Signalqualität und Fehlerkorrektur    |
|                     | - niedrigere Spannung                               |

[turn-on Ratgeber](https://www.turn-on.de/tech/ratgeber/ddr3-vs-ddr4-so-unterscheiden-sich-die-ram-typen-463825)

## 3.7 Was sind die Schaltzeiten im RAM? Welche gibt es? Woher rühren diese bzw. was bedeuten sie?  

- CAS (column access strobe) - latency (CL)
	- Anzahl der für die Bereitstellung der Daten notwendigen Taktzyklen
- RAS to CAS Delay (tRCD)
	- Dauer bis zur Bearbeitung einer bestimmten Speicherzelle
	- tRC = Minimalzeit zum Aufbau einer Speicherzelle
- RAS (row access strobe) – precharge delay (tRP)
	- Zeit um den Speicherinhalt einer Zelle auszulesen
- Row-Active-Time (tRAS)
	- Erlaubte Neuzugriffe nach festgelegten Taktzyklen (CAS + tRP + Sicherheit)
- Command Rate (Befehlsrate)
	- Latenz bei der Auswahl einzelner Speicherchips (vor Ansteuerung der Zeilen/Spalten)

[Wiki: Arbeitsspeicher](https://de.wikipedia.org/wiki/Arbeitsspeicher#Leistung_von_Speichermodulen)

## 3.8 Wenn Sie mit einer Software die Latenz des Arbeitsspeichers messen, welche Schaltzeiten müssen Sie dann berücksichtigen wenn das Programm a) eine zufällig bestimmte Speicheradresse anfordert und b) sequenziell auf den Speicher zugreift?

Prefetch greift nicht

a) CL + tRCD + (tRP) + (tRC) + tRAS
b) CL + (tRCD pro Zeile) + tRP + tRAS **+ Befehlsrate**

[Wiki: Arbeitsspeicher](https://de.wikipedia.org/wiki/Arbeitsspeicher#Leistung_von_Speichermodulen)

## 3.9 Was bedeuten Dual- und Singlechannel in Bezug auf die Speicherkonfiguration? Wie funktioniert der Dualchanel-Modus? Wie hoch ist die Speicherbusbreite im jeweiligen Modus?

- Singlechannel: Verwendung eines Arbeitsspeicher-Moduls
- Dualchannel: Verwendung mehrerer identischer Arbeitsspeicher-Module parallel an einer CPU
	- Verwendung getrennter Datenbusse des Prozessors
	- Vervielfachung der Speicherbusbreite

## 3.10 Wie hoch ist die Bandbreite bei einem DDR4 Speichermodul das mit 2133 MHz Nenntakt betrieben wird im Singlechanel-Modus und wie welchen Wert sollte sie folglich im Dualchanel besitzen? Schreiben Sie Ihren Rechenweg auf!

$$\frac{\text{Nenntakt in (MHz)} \times \text{Busbreite}}{8\ \text{Bit}}= \text{Bandbreite in MByte/s}$$

$$\frac{2.133\ \text{MHz} \times 64\ \text{Bit}}{8\ \text{Bit}} = 17.064\;‬ \text{MByte/s} \approx 17\ \text{GByte/s}$$

Dual-Channel-Modus = Verdopplung der Busbreite = Verdopplung der Bandbreite

$$\frac{2.133\ \text{MHz} \times 128\ \text{Bit}}{8\ \text{Bit}} = 34.128\ \text{MByte/s} \approx 34‬ \text{GByte/s}$$

[Wiki: DDR-SDRAM](https://de.wikipedia.org/wiki/DDR-SDRAM#Berechnung_Speichertransferrate)


Versuch 2: Speicher und Raid
============================

# Versuchsvorbereitung

## 3.1 Welche aktuellen Schnittstellen für Speichermedien gibt es (intern / extern)? Wie sind deren Spezifikationen (max. Bandbreite, max. Anzahl anschließbarer Geräte, max. Kabellänge, Anzahl Adern / Kontakte)?

- SATA
	- SATA: max. 6 Gbit/s; SATA Express: 16 Gbit/s
	- Kabel mit 7 Adern, max. 1m lang
	- (1 Gerät/Anschluss?)
- USB
	- 2.0: max. 480 MBit/s; 3.0: max. 5 Gbit/s; 3.1: max. 10 Gbit/s ; 3.2: max. 20 Gbit/s
	- maximal 127 USB-Geräte (USB 3.0)
	- 9 Adern (USB 3.0), 4 Adern (USB 2.0)
	- Maximale Kabellänge im Standard nicht genau definiert (Empfehlung: max 3m)
- NVM Express
	- Anbindung über PCIe 3.0/3.1: 7,88‬‬ Gbit/s; 4.0: 15.75 Gbit/s; 5.0: 60.23 Gbit/s (jeweils pro Lane)
	- (1 Gerät/Anschluss?)

[Wiki: SATA](https://de.wikipedia.org/wiki/Serial_ATA)
[Elektronik Kompendium](https://www.elektronik-kompendium.de/sites/com/0310281.htm)
[Wiki: USB 3.0](https://en.wikipedia.org/wiki/USB_3.0)
[Wiki: PCIE](https://de.wikipedia.org/wiki/PCI_Express)
[Wiki: NVME](https://de.wikipedia.org/wiki/NVM_Express)

## 3.2 Welche Vor- und Nachteile bieten die folgenden Speichermedien hinsichtlich ihrer Kosten absolut und pro GiB, Geschwindigkeit sowie Datensicherheit und Portabilität? Erstellen Sie eine entsprechende Tabelle!  USB-Stick (3.0), (Micro)SD-Karte, Festplatte, SSD, DVD

|                   | USB-Stick                                                      | (Micro) SD-Karte                                                                      | Festplatte      | SSD          | DVD                                    |
| ----------------- | -------------------------------------------------------------- | ------------------------------------------------------------------------------------- | --------------- | ------------ | -------------------------------------- |
| absolute Kosten\* | gering                                                         | gering                                                                                | hoch            | hoch         | gering                                 |
| Kosten/GiB\*      | hoch                                                           | hoch                                                                                  | gering          | hoch         | hoch                                   |
| Geschwindigkeit   | USB 2.0: 480 Mbit/s<br>USB 3.0: 5 Gbit/s<br>USB 3.1: 10 Gbit/s | Class 2: 16 Mbit/s<br>Class 4: 32 Mbit/s<br>Class 6: 48 Mbit/s<br>Class 10: 80 Mbit/s | etwa 1.6 Gbit/s | bis 4 Gbit/s | 1x: 11,08 Mbit/s<br>24x: 265.92 Mbit/s |
| Datensicherheit\* | gering                                                         | gering                                                                                | mittel          | mittel       | mittel                                 |
| Portabilität\*    | hoch                                                           | hoch                                                                                  | gering          | gering       | mittel                                 |

\* = persönliche Einschätzung

[Wiki: USB](https://de.wikipedia.org/wiki/Universal_Serial_Bus#USB_2.0)
[Wiki: MicroSD](https://de.wikipedia.org/wiki/MicroSD#Geschwindigkeitsklassen_und_Anwendung_bei_Mobiltelefonen)
[Wiki: Festplattenlaufwerk](https://de.wikipedia.org/wiki/Festplattenlaufwerk#Geschwindigkeit)
[Wiki: DVD](https://de.wikipedia.org/wiki/DVD#Geschwindigkeit)

## 3.3 Erstellen Sie ein Balkendiagramm in dem Sie aktuelle GB-Preise für folgende Speichermedien eintragen: HDD – SATA, SSD – SATA, HDD – SAS, USB-Stick 2.0, USB-Stick 3.0. Suchen Sie nach dem jeweils günstigsten Angebot und geben Sie Ihre Bezugsquelle (Händler) sowie die Gesamtspeichergröße und den Gesamtpreis in einer Tabelle an!

```
Hier fehlt ein Balkendiagramm!
```


| Speicher      | Preis/GB | Preis    | Kapazität | Händler     | URL                                                                                                           |
|---------------|----------|----------|-----------|-------------|---------------------------------------------------------------------------------------------------------------|
| HDD-SATA      | 0,019475 | 78,71 €  | 4 TB      | Mindfactory | [Geizhals](https://geizhals.de/toshiba-p300-high-performance-4tb-hdwd240uzsva-a2189648.html?hloc=at&hloc=de)  |
| SSD-SATA      | 0,095    | 95,00 €  | 1 TB      | Saturn      | [Geizhals](https://geizhals.de/crucial-bx500-1tb-ct1000bx500ssd1-a2168439.html?hloc=at&hloc=de)               |
| HDD-SAS       | 0,024988 | 199,90 € | 8 TB      | Technix     | [Geizhals](https://geizhals.de/seagate-exos-x-x10-8tb-st8000nm0156-a1762008.html?hloc=at&hloc=de)             |
| USB-Flash 2.0 | 0,086    | 10,98 €  | 128 GB    | OTTO        | [Geizhals](https://geizhals.de/hama-flashpen-rotate-128gb-108071-a985312.html?hloc=at&hloc=de)                |
| USB-Flash 3.0 | 0,085    | 45,53 €  | 512 GB    | Mindfactory | [Geizhals](https://geizhals.de/pny-attach-4-3-1-schwarz-512gb-fd512att431kk-ef-a2128176.html?hloc=at&hloc=de) |

## 3.4 Was ist ein RAID? Welchen Zweck erfüllt der Einsatz eines RAID-Systems?

- RAID = Redundant Array of independent disks
- Ziel: Speicherung redundanter Informationen zur Sicherung der Integrität von Daten **und/oder** Steigerung der Verfügbarkeit der Daten

[Wiki: RAID](https://de.wikipedia.org/wiki/RAID)

## 3.5 Wie funktionieren RAID 0, 1, 10, 5 und 6? Welche Anforderungen hat jedes dieser RAID-Level bezüglich der Anzahl an HDDs? Wieviel des Speichers steht tatsächlich zur Verfügung (relativ im Bezug zum Gesamtspeicher aller beteiligten Platten)?

- RAID 0:
	- min. 2 Festplatten
	- keine Redundanz
	- gesteigerte Transferrate (Speicherung zusammenhängender Blöcke auf unterschiedlichen Speichern)
	- volle Kapazität
	- erhöhte Fehler- und Ausfallwahrscheinlichkeit
- RAID 1:
	- min. 2 Festplatten
	- volle Redundanz durch Mirroring
	- effektives Halbieren der Kapazität
- RAID 10: RAID 0 über mehrere RAID 1
	- min. 4 Festplatten
	- gesteigerte Transferrate (Speicherung zusammenhängender Blöcke auf unterschiedlichen Speichern)
	- volle Redundanz durch Mirroring
	- effektives Halbieren der Kapazität
- RAID 5:
	- min. 3, max. 5 Festplatten
	- gesteigerte Transferrate (Speicherung zusammenhängender Blöcke auf unterschiedlichen Speichern)
	- Speicherung von Paritätsinformationen (keine Redundanz, aber für Wiederherstellung verwendbar)
- RAID 6:
	- gesteigerte Transferrate (Speicherung zusammenhängender Blöcke auf unterschiedlichen Speichern)
	- zweifache Speicherung von Paritätsinformationen (keine Redundanz, aber für Wiederherstellung verwendbar)
	- hohe Fehler- und Ausfalltoleranz

[Wiki: RAID](https://de.wikipedia.org/wiki/RAID)
[Storage Insider](https://www.storage-insider.de/was-ist-raid-alles-ueber-level-1-bis-5-und-mehr-a-517806/)
