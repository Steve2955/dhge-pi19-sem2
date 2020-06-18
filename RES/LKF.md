# Lernkontrollfragen - RES

## Architektur

### Welche der folgenden Befehle sollte nur im Kernmodus erlaubt sein?

| Sperren aller Unterbrechungen           | Kernel |
|-----------------------------------------|--------|
| Lesen der aktuellen Uhrzeit             | User   |
| Setzen der aktuellen Uhrzeit            | Kernel |
| Änderung der Speicherzuordnungstabellen | Kernel |

### Zählen Sie einige Unterschiede zwischen einem Betriebssystem für einen Personalcomputer und für einen Mainframe auf

| Mainframe                            | Personalcomputer                  |
|--------------------------------------|-----------------------------------|
| - Primär Batchverarbeitungsverfahren | - Universelle Betriebssysteme     |
| - Mehrprogrammbetrieb?               | - meist Einzelprogrammbetrieb?    |
| - Mehr-Prozessor-Betriebssystem?     | - Ein-Prozessor-Betriebssystem?   |
| - Fokus auf Sicherheitsaspekten      |                                   |

### Was verstehen Sie unter Multiprogramming?

Mehrere Programme werden (quasi)-gleichzeitig auf einem System aufgeführt.

### Das Client-Server-Modell ist bei verteilten Systemen sehr verbreitet. Kann es auch in einem Einzelplatz-Computer Anwendung finden?

Ja, typische Beispiele sind Samba, X11 und BS-Emulation auf einem Rechner.

### Was verstehen Sie unter der Von-Neumann-Architektur? Was ist der so genannte Von-Neumann-Flaschenhals?

- Grundmodell für den Aufbau eines Rechners
- Aufteilung eines Rechners in verschiedene Werke mit verschiedenen Aufgaben (Rechen-, Speicher-, Steuerwerk; Ein-/Ausgabe, ...)
- Verbindung einzelner Komponenten über BUS-System (= Flaschenhals, weil Daten und Befehle über gleichen BUS)

### Nennen Sie mindestens vier Betriebsmittel, welche das Betriebssystem verwaltet. Welche davon sind hardware- und welche softwaretechnische Betriebsmittel?

Hardwaretechnische Betriebsmittel:

- Prozessor
- Speicher
- E/A-Geräte

Softwaretechnische Betriebsmittel:

- Datei
- Nachricht
- Prozess

## Strukturen

### Erläutern Sie Vor- und Nachteile von Schalen- bzw. Schichtenmodellen.

Vorteile:
- Abstraktion komplexer Funktionen in Schichten mit klar definierten Schnittstellen
- Logikanpassungen innerhalb einer Schicht ohne Änderung der Schnittstelle einfach realisierbar
- Einzelne Schichten bei unveränderter Schnittstelle austauschbar

Nachteile:
- Hoher Kommunikationsaufwand durch Schnittstelle (besonders zwischen Oberen und unteren Schichten)
- Nur Kommunikation mit benachbarten Schichten möglich -> Nachrichten müssen weitergereicht werden

### Erläutern sie kurz die Begriffe „virtuelle Maschine“ und „Schnittstelle“

Eine Virtuelle Maschine ist eine Maschine mit Zugriff auf virtuelle Hardware, die entweder von einer weiteren Virtuellen Maschine oder der Maschine die die physischen Hardware verwaltet, bereitgestellt wird.

Schnittstelle = Berührungspunkt zwischen den virtuellen Maschine. Stellen Methoden für den Hardwarezugriff und Datenaustausch bereit. Diese Kommunikation erfolgt nach festen Regeln (Protokoll).

### Ein Grund für die langsame Einführung grafischer Benutzeroberflächen war, dass die nötige Hardware anfangs noch sehr teuer war.

Wieviel Videospeicher braucht man für die Darstellung von:

a) 25 Zeilen a 80 Zeichen pro Zeile im Textmodus (Monochrom - 1 Byte pro Zeichen)?
b) 1024 * 768 Bildpunkten mit 24 Bit Farbtiefe?

Was hat der Speicher 1980 gekostet, als ein KByte etwa 5 DM kostete? Und wieviel kostet er heute?

$$25*80=2000 \quad\rightarrow\quad 2000\text{Byte}* \frac{5 \text{DM}}{1000\text{Byte}} = 10\text{DM}$$

$$1024*768*\frac{24}{8}=‭2.359.296‬ \quad\rightarrow\quad ‭2.359.296‬\text{Byte}* \frac{5 \text{DM}}{1000\text{Byte}} = ‭11.796,48‬\text{DM}$$

Heutzutage 16GB Speicher ab $3,556 \frac{€}{GB} = 6,95\frac{DM}{GB} = 6,95 * 10^{-6} \frac{DM}{Kbyte}$

### In folgender Tabelle sieht man auszugsweise einige Systemaufrufe in UNIX, für die keine entsprechende Funktion in der Win64 API existiert.

| UNIX  | Win64             | Beschreibung                     |
|-------|-------------------|----------------------------------|
| fork  | CreateProcess     | Neuen Prozess erzeugen           |
| exit  | ExitProcess       | Ausführung beenden               |
| mkdir | CreateDirectory   | Neue Datei erzeugen              |
| link  | Verweis auf Datei | Win64 unterstützt nur NTFS       |
| mount | [none]            | Win64 unterstützt kein Einhängen |
| kill  | [none]            | Win64 unterstützt keine Signale  |
| time  | GetLocalTime      | Aktuelle Zeit erfragen           |

Überlegen Sie sich für jede dieser Funktionen, welche Folgen das für einen Programmierer hat, der ein UNIX-Programm nach Windows portieren will.

Bei Portieren auf Windows treten genau dann Probleme auf, wenn Funktionen unter Linux verwendet werden, die unter Windows nicht existieren (z.B. mount, kill). Dies führt dazu, dass das Programm nicht einfach übersetzt werden kann, sondern für die unterschiedlichen Betriebssysteme angepasst werden muss. Weitere Unterschiede zwischen den Plattformen sind bespielweise die Verwendung von Mount-Points oder Laufwerken unter Windows und damit verbunden auch der unterschiedliche Aufbau von Pfadangaben.

### Ein Computer hat zur Befehlsabarbeitung eine vierstufige Pipeline eingebaut. Jede Stufe benötigt für die Bearbeitung dieselbe Zeit von 1 ns. Wie viele Befehle kann dieser Rechner pro Sekunde abarbeiten? Wie sieht das bei einer zehnstufigen Pipeline aus?

$10^{9}$ Befehle werden pro Sekunde bei einer vierstufigen abgearbeitet. Durch die parallele Verarbeitung mehrere Befehle in jeweils unterschiedlichen Pipeline-Stufen, hat die Veränderung der Anzahl der Stufen einer Pipeline keinen Einfluss auf den Befehlsdurchsatz. Daher werden bei einer zehnstufigen Pipeline ebenfalls $10^{9}$ Befehle in pro Sekunde verarbeitet.

### Was verstehen Sie unter einem Mikrokern?

Ein Mikrokern implementiert nur die wichtigsten Funktionen im Kern (z.B. Prozess-, Speicherverwaltung und Kommunikationsschnittstellen). Alles Weiter wird von Betriebssystemdiensten verwaltet (z.B. Dateisystem, Gerätetreibe). Diese werden im User-Mode ausgeführt.

## Schnittstellen

### Angenommen wir beschreiben für eine anspruchsvolle Grafik die Farbe eines Pixels direkt ohne CLUT mit 24 Bit Genauigkeit (Farbtiefe). Wie groß muss der Bildwiederholspeicher für eine 1024x768 großes Bild mindestens sein? Wie groß, wenn er drei Ebenen davon abspeichern soll?

$$1024*768*\frac{24}{8} * 3 = ‭‭7.077.888‬‬ \text{Byte} = ‭‭7,078 \text{MByte}‬$$

### Wie groß muss der Bildwiederholspeicher für das Bild mindestens sein, wenn gleichzeitig 65536 = 16 Bit Farben sichtbar sein sollen und eine einstufige Umsetzung mit CLUT möglich ist. Wieviel Platz benötigt diese CLUT?

$65.536=2^{16}$ -> 16 Bit

$65.536*(3*16)=‭12.745.728‬$

### Ein SLIM-Terminal (thin client, "dummes Terminal") wird zur Ausgabe einer Webseite verwendet, die ein animiertes Bild mit 400 mal 160 Punkten und einer Bildwiederholrate von 10 Bildern pro Sekunde besitzt (24 Bit Farbtiefe). Welcher Anteil eines 100 Mbps Fast Ethernet wird durch die Darstellung der Animation verbraucht.

$$400*160*\frac{24}{8}=‭192.000‬$$

$$\frac{‭192.000‬ * 10^{-6} \text{Bytes} * 10s}{100 \text{Mbps}} = 0,0192$$

### Ein Bitmap-Terminal enthält 1280 mal 960 Bildpunkte. Um ein Fenster zu scrollen, muss die CPU (oder der Controller) alle Zeilen des monochromen Textes nach oben schieben, indem sie die entsprechenden Bits innerhalb des Videospeichers kopiert. Wenn ein spezielles Fenster 60 Zeilen hoch und 80 Zeichen breit ist und ein Zeichen 16 Pixel hoch und 8 Pixel breit ist,

#### a) wie lange dauert es dann, das gesamte Fenster bei einer Geschwindigkeit von 50 ns pro Byte zu scrollen?

$$(60*80) * (16*8*1\text{Bit}) = ‭614.400‬ \text{Bit} = 76.800 \text{Byte}$$

$$76.800 \text{Byte} * \frac{50 ns}{1 \text{Byte}} = 3.840.000‬ ns = 3,84 ms$$

#### b) Wenn alle Zeilen 80 Zeichen lang sind, was ist dann die gleichwertige Baudrate (Ausgabe einer Zeile) des Terminals? Das Ausgeben eines Zeichens dauert 5 µs.

$$80 * (16*8*1\text{Bit}) = 10.240‬ \text{Bit} = 1.280‬ \text{Byte}$$

#### c) Wieviel Zeilen pro Sekunde können angezeigt werden?

### Bewerten Sie den Einsatz des lokalen Desktop-Konzeptes von Windows NT gegenüber dem verteilten X-Window-System? Denken Sie dabei an Applikationen wie die Prozesssteuerung eines Stahlwerks mit einem Rechnernetz, die Datenauswertung der Abteilungen über das Intranet eines Betriebs, die Softwareinstallation und Wartung für einen vernetzten Rechnerpool usw.
