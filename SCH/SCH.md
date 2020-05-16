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

- PCI/PCI-Express (x16,8,4,1)
- SATA 3
- M.2

## 3.3 Wodurch zeichnet sich das Funktionsprinzip eines DDR-SDRAM gegenüber SDRAM aus? Was heißt in diesem Fall DDR?

- SDRAM = Synchronous Dynamic Random Access Memory (nur steigend)
- DDR SDRAM = Double Data Rate SDRAM
	- Daten werden bei steigenden und fallenden Flanken transferiert (bis zu doppelte Datenübertragung bei gleicher Taktung)

[Elektronik Kompendium](https://www.elektronik-kompendium.de/sites/com/1312291.htm)

## 3.4 Welche drei Takte spezifizieren die Leistung des Arbeitsspeichers? Erklären Sie diese und wie sie miteinander zusammenhängen!  

- Speichertakt
- I/O-Takt (Speichertakt\*2 bei DDR: zweimal eigentliche Taktfrequenz))
- effektive Taktfrequenz = Speichertakt * Prefetch (bei SDRAM kein Prefetch)

[Wiki: DDR-SDRAM](https://de.wikipedia.org/wiki/DDR-SDRAM#Arbeitsweise)

## 3.5 Wie wird die Erhöhung der Datenrate von DDR-SDRAM zu DDR2- und DDR3-Speicher maßgeblich realisiert (zwei sich bedingende Maßnahmen)?

- Erhöhung Prefetchbuffer -> I/O Takt Erhöhung -> Erhöhung des effektiven Takts + Übertragungsrate
- (Reduktion der Spannung -> gesenkter Stromverbrauch)

|       | Prefetch | Speichertakt | I/O-Takt |
|-------|----------|--------------|----------|
| DDR-1 | 2x       | 100 MHz      | 100 MHz  |
| DDR-2 | 4x       | 100 MHz      | 200 MHz  |
| DDR-3 | 8x       | 100 MHz      | 400 MHz  |

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

Max:
```
a)Zeile aktivieren -> Spalte auswählen -> Zeile deaktivieren(CL) # CL, trcd, tras, evtl. trp, trc  ->  abh. v. d.angeforderten Bank
b)Zeile aktivieren -> prefetching buffer (tRCD pro Zeile, jedes mal CL)
```

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
- Thunderbolt 3

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
	- volle Redundanz durch Mirroring (ein Ausfall möglich)
	- effektives Halbieren der Kapazität
	- gesteigerte Lese-Performance
- RAID 10: RAID 0 über mehrere RAID 1
	- min. 4 Festplatten
	- gesteigerte Transferrate (Speicherung zusammenhängender Blöcke auf unterschiedlichen Speichern)
	- volle Redundanz durch Mirroring (ein Ausfall möglich)
	- effektives Halbieren der Kapazität
- RAID 5:
	- min. 3, max. 5 Festplatten
	- gesteigerte Transferrate (Speicherung zusammenhängender Blöcke auf unterschiedlichen Speichern)
	- Speicherung von Paritätsinformationen (keine Redundanz, aber für Wiederherstellung verwendbar)
	- Kapazitätsausnutzung: 67% - 94% (bei 16 HDDs)
- RAID 6:
	- gesteigerte Transferrate (Speicherung zusammenhängender Blöcke auf unterschiedlichen Speichern)
	- zweifache Speicherung von Paritätsinformationen (keine Redundanz, aber für Wiederherstellung verwendbar)
	- hohe Fehler- und Ausfalltoleranz
	- Kapazitätsausnutzung: 50% - 88% (bei 16 HDDs)
	- kein Datenverlust beim Ausfall zweier Festplatten

[ThomasKrennWiki: RAID](https://www.thomas-krenn.com/de/wiki/RAID)
[Wiki: RAID](https://de.wikipedia.org/wiki/RAID)
[Storage Insider](https://www.storage-insider.de/was-ist-raid-alles-ueber-level-1-bis-5-und-mehr-a-517806/)

Versuch 3: System-Tuning und Sicherheit
=======================================

# Vorbereitung

## 3.1 Notieren Sie Bezeichnungen und Grundmerkmale (Taktfrequenz, Kerne Sockel, Cache, Strukturgröße, Verlustleistung) aktueller INTEL sowie adäquater AMD Desktop-Prozessoren! (jeweils 2 konkret am Markt verfügbare CPUs)

|                 | Intel Core i9-10980XE Extreme Edition | AMD Ryzen Threadripper 3960X |
|-----------------|---------------------------------------|------------------------------|
| Taktfrequenz    | 3,00 GHz (max. 4,60 GHz)              | 3.80 GHz (max. 4,50 GHz)     |
| Kerne           | 18                                    | 24                           |
| Sockel          | FCLGA2066                             | sTRX4                        |
| Cache           | 24.75 MB                              | 128 MB                       |
| Strukturgröße   | 14nm                                  | 7nm                          |
| Verlustleistung | 165 W                                 | 280 W                        |

[Intel](https://www.intel.de/content/www/de/de/products/processors/core/x-series/i9-10980xe.html)
[AMD](https://www.amd.com/de/products/cpu/amd-ryzen-threadripper-3960x)

## 3.2 Es gibt prinzipiell 2 Optionen im BIOS/UEFI um eine CPU in einem Desktoprechner zu übertakten. Welche sind das? Welche Vor- und Nachteile hat die jeweilige Option? Welche Vor- und Nachteile birgt das Übertakten im Allgemeinen?

**Möglichkeiten für das Übertakten**

- Übertakten
- Untervolten

**Vorteile**

- gesteigerte Leistungs des Systems(begrenzt)

**Nachteile**

- gesteigerter Stromverbrauch
- aufwendigere Kühlung notwendig
- Reduktion der Lebensdauer des Prozessors
- zu starkes Übertakten führt zu Instabilität des Systems

## 3.3 Welche grundlegenden Aufgaben besitzt das BIOS (UEFI)! Nenne Sie gängige Hersteller! Nennen Sie mindestens drei Möglichkeiten ein BIOS-Passwort zu löschen bzw. zu umgehen.

- BIOS-Batterie entfernen
- CMOS Clear (Jumper)
- Master Passwort

## 3.4 Was ist UEFI? Welche Vorteile bietet es gegenüber einem BIOS?

- Industrieller Standard (s.a [http://www.uefi.org](http://www.uefi.org/about/))
- Aufgrund der Entwicklung in C leichter programmier- und erweiterbar
- Architektur unabhängig (für aktuelle 32/64 Bit Systeme ausgelegt)
- Graphische User Interfaces in der der Pre-Boot-Umgebung anbieten (z.B. durch einen pre-Boot Netzwerk-Stack)
- Remote Upgrade von Firmware-Komponenten oder der ganzen Firmware durchführen
- Auf beliebigen Plattformen eingesetzt werden
- Parallel-Installation von mehreren Betriebssystemen ohne OS-spezifische Bootmanager (wie z.B. Grub2)
- Limitierung der Festplattenkapazität auf 2,2 TByte (im eigentlichen Sinne eine Einschränkung des Master Boot Records (MBR), die durch die Einführung der GPT-Partitionierung aufgehoben wurde)
- Netzwerkfähigkeiten auch ohne OS (z.B. zum Aktualisieren der Firmware)
- Pre-Boot-Applikationen (z.B. für Recovery-Funktionen, Diagnose-Werkzeuge)

[ThomasKrennWiki: UEFI](https://www.thomas-krenn.com/de/wiki/UEFI_Einf%C3%BChrung)

## 3.5 Es wird erwartet, dass Sie grundlegend mit einem Linux System umgehen können (Laufwerke einbinden, Dateien kopieren, umbenennen, erzeugen). Listen Sie die entsprechenden Kommandos auf und fügen Sie ein Beispiel an!

```bash
lsblk
mount sda /mnt/sda
umount /mnt/sda
mkdir folder
touch file
fallocate -l 1G file
cp src dest
mv src dest
rm file
```

[Linux Command Line Cheat Sheet](https://cheatography.com/davechild/cheat-sheets/linux-command-line/)

## 3.6 Was ist das Kommandozeilentool Winsat? Welche Möglichkeiten bietet es bezüglich CPU- und Arbeitsspeicherbewertung?

WinSAT ist das "Windows System Assessment Tool", es zuständig für die Systembewertung, es misst die Leistung und Funktionsfähigkeit eines Systems.

```XML
<CPUMetrics>
	<CompressionMetric units="MB/s">387.27909</CompressionMetric>
	<EncryptionMetric units="MB/s">4679.87043</EncryptionMetric>
	<CPUCompression2Metric units="MB/s">881.78483</CPUCompression2Metric>
	<Encryption2Metric units="MB/s">1781.61980</Encryption2Metric>
	<CompressionMetricUP units="MB/s">77.84197</CompressionMetricUP>
	<EncryptionMetricUP units="MB/s">696.70586</EncryptionMetricUP>
	<CPUCompression2MetricUP units="MB/s">198.94126</CPUCompression2MetricUP>
	<Encryption2MetricUP units="MB/s">522.49450</Encryption2MetricUP>
	<DshowEncodeTime units="s">0.00000</DshowEncodeTime>
</CPUMetrics>
<MemoryMetrics>
	<Bandwidth units="MB/s">24011.42845</Bandwidth>
</MemoryMetrics>
```

[win-tipps-tweaks](https://www.win-tipps-tweaks.de/cms/windows-7-tipps/tricks/winsat-windows-system-assessment-tool.html)


Versuch 4: Netzwerk
====================

# Vorbereitung

## 3.1 Wie ist die Steckerbelegung und Farbcodierung eines paarigen Netzwerkkabels nach DIN EN 50173 mit RJ45 Stecker?

```
1 - orange/weiß ──┐
2 - orange ───────┘
3 - grün-weiß ────┐
4 - blau ──────┐  │
5 - blau-weiß ─┘  │
6 - grün ─────────┘
7 - braun-weiß ───┐
8 - braun ────────┘
```

[Netzmafia](http://www.netzmafia.de/skripten/netze/twisted.html)

## 3.2 Welche Schirmungsarten für Twisted-Pair-Kabel gibt es (Bezeichnung/Aufbau)?

- Ziel: Erhalt der Übertragungsqualität bei Einstrahlung der Störungen von außen
- Gesamtschirmung
	- Drahtgeflecht: S/UTP, S/FTP, SF/FTP
	- Folie: F/FTP, SF/FTP
- Adernpaarschirmung
	- Drahtgeflecht: -
	- Folie: U/FTP, S/FTP, F/FTP, SF/FTP

[Wiki: Twisted-Pair-Kabel](https://de.wikipedia.org/wiki/Twisted-Pair-Kabel#Schirmung)

## 3.3 Ab welcher Kategorie ist ein Netzwerkkabel geeignet, um in einem GBit-Netz eingesetzt zu werden?

- Netzwerkkabel der Kategorie 5/5e

[Wiki: Twisted-Pair-Kabel](https://de.wikipedia.org/wiki/Twisted-Pair-Kabel#Schirmung)

## 3.4 Was ist PowerLAN, wie ist die maximale Reichweite, wie funktioniert es? Welche Bandbreiten können realisiert werden?  

- Technik, die vorhandene elektrische Leitungen im Niederspannungsnetz zum Aufbau eines lokalen Netzwerks zur Datenübertragung nutzt, so dass keine zusätzliche Verkabelung notwendig ist
- IEEE-1901-FFT-Standard: maximal 2000 Mbit/s bei bis zu 300 m Reichweite
- ITU-G.hn-Standard: maximal 2400 MBit/s brutto mit bis zu 500 m Reichweite

[Wiki: PowerLAN](https://de.wikipedia.org/wiki/PowerLAN)

## 3.5 Welche Einflüsse können eine PowerLan-Verbindung stören? Welche Besonderheiten hinsichtlich der Sicherheit sind zu beachten?

- Stromkabel sind nicht abgeschirmt: PowerLAN kann Störungen im Kurzwellenbereich verursachen
- Verschiedene Haushaltsgeräte (z.B. Waschmaschinen, Spülmaschinen) können PowerLAN-Signale stören
- FI-Schutzschalter können die Übertragung im Hochfrequenzbereich stören (Phasenkoppler durch Elektriker installieren lassen)
- Für die Sicherheit der Daten-Verbindung sollte diese verschlüsselt sein

[PowerLine Tests](https://powerline-tests.de/powerline-stoerungen-beseitigen/)

## 3.6 Notieren Sie entscheidende Merkmale des Industriestandards IEEE 802.11! Erklären Sie insbesondere Unterschiede zwischen IEEE 802.11a/b/g/n (max. Datenrate, Frequenzband, Modulation)! Welche Neuerungen brachte der ac-Standard?

- Standart für die Kommunikation in Funknetzen (WLAN)

- IEEE 802.11a: 5 GHz-Band mit bis zu 54 Mbit/s (Modulation: OFDM)
- IEEE 802.11b: 2.4 GHz-Band mit bis zu 11 Mbit/s (Modulation: DSSS mit CCK)
- IEEE 802.11g: 2.4 GHz-Band mit bis zu 54 Mbit/s (Modulation: OFDM)
- IEEE 802.11n: 2.4/5 GHz-Band mit bis zu 600 Mbit/s (Modulation: OFDM)

- IEEE 802.11ac: Erweiterung zu 802.11n (nur 5 Ghz)
	- breitere Kanäle möglich (80 MHz, 160 MHz Kanalbreite optional) -> bis 867 Mbit/s
	- mehrere MIMO-Verbindungen (bis zu acht) -> höhere Übertragungsgeschwindigkeit
	- Downstream Multi-User MIMO (muss vom Accesspoint und Client unterstützt werden)
	- Höhere Modulationsstufen bei sehr gutem Empfangssignal
	- Standardisiertes Beamforming

[Wiki: IEEE_802.11](https://de.wikipedia.org/wiki/IEEE_802.11#Standard_802.11)
[Wiki: IEEE_802.11ac](https://de.wikipedia.org/wiki/IEEE_802.11ac)
[Wiki: IEEE_802.11n](https://de.wikipedia.org/wiki/IEEE_802.11n)

## 3.7 Erklären Sie Unterschiede zwischen dem 2,4 und dem 5 GHz Übertragungsband! Nennen Sie jeweils die Vor- und Nachteile!

| Band                | 2.4 GHz                            | 5 GHz                        |
|---------------------|------------------------------------|------------------------------|
| Kanal               | Drei (3) nicht überlappende Kanäle | 23 nicht überlappende Kanäle |
| Standard            | Wireless-B, G, und N               | Wireless-A, N, und AC        |
| Netzwerk Reichweite | Weite Reichweite                   | Kürzere Reichweite           |
| Interferenzen       | Höher                              | Geringer                     |

[linksys](https://www.linksys.com/ch/support-article?articleNum=134478)

## 3.8 Geben Sie für folgende Fragestellungen die Kommandos mit entsprechenden Parametern an:

Wie ermitteln Sie die physikalische Adresse Ihres Netzwerkadapters auf der Kommandozeile?

```cmd
ip config /all
```

Wie prüfen Sie mit Hilfe eines Terminal-Kommandos die Netzwerkverbindung zu einer dedizierten Gegenstelle?

```cmd
ping 1.2.3.4
```

Wie kopieren Sie über die Kommandozeile eine Datei aus dem Netzwerk auf Ihren lokalen Rechner und messen dabei die für den Kopiervorgang nötige Zeit? Schreiben Sie die entsprechende Kommandofolge, wie sie in einer Batch-Datei stehen könnte, auf!

```cmd
@echo Started: %date% %time%
robocopy src dest
@echo Completed: %date% %time%
```
