# Algorithmen und Datenstrukturen

## Listen

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

### Implementierung von Listen

- Um Listen zu Implementieren wird ein Element mit seinen entsprechenden Daten und einem Pointer (Verkettung) auf ein nächstes und oder vorheriges Element deklariert
	- einfach Verkettete Liste: jedes Element besitzt einen Pointer auf seinen Nachfolger
	- doppeltverkettete Liste: jedes Element besitzt einen Pointer auf seinen Vorgänger und seinen Nachfolger
- Pointer auf den Beginn der Liste zeigt auf des Erste Element
- Ende der Liste ist durch NULL-Pointer markiert (bei ringförmigen Listen Pointer auf erstes Element)

### Organisationsformen von Listen
- Pointer auf erstes Element; letztes Element durch NULL markiert
- Pointer auf erstes und letztes Element; letztes Element zusätzlich durch NULL markiert
- Pointer auf Dummy am Anfang und am Ende der Liste (letzter Dummy durch NULL markiert)
- Pointer auf Dummy am Anfang und am Ende der Liste (letzter Dummy zeigt auf letztes richtiges Element)
- Ringförmige Verkettung: Pointer auf Erstes Element; Letztes Element zeigt auf Erstes

### Keller (Stack) und Stapel (Queue)

- Keller: nur am Ende der Liste wird ein- und ausgespeichert (LIFO)
	- push/pop zum Ein-/Auspeichern
	- top als oberstes Element
- Schlange: an einem Ende der Liste wird eingespeichert, am anderen wird ausgespeichert (LILO)
	- enqueue zum Anstellen
	- dequeue zum Drankommen
