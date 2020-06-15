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
