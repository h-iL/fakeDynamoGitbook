# Verwendung von Blöcken

Dynamo 2.0 stellt eine Reihe von Wörterbuch-Blöcken für die Verwendung bereit. Dies umfasst die Blöcke _create, action und query_.

![BILD](../.gitbook/assets/9-2\_dictionaryNodes.png)

* `Dictionary.ByKeysValues` erstellt ein Wörterbuch mit den bereitgestellten Werten und Schlüsseln. _(Die Anzahl der Einträge entspricht der Länge der kürzesten Liste.)_
* `Dictionary.Components` erstellt die Komponenten des Eingabe-Wörterbuchs. _(Dieser Vorgang ist die Umkehrung der Block-Erstellung.)_
* `Dictionary.RemoveKeys` erzeugt ein neues Wörterbuch-Objekt und entfernt die Eingabe-Schlüssel.
* `Dictionary.SetValueAtKeys` erzeugt ein neues Wörterbuch anhand der eingegebenen Schlüssel und Werte und ersetzt den aktuellen Wert in den entsprechenden Schlüsseln.
* `Dictionary.ValueAtKey` gibt den Wert am Eingabeschlüssel zurück.
* `Dictionary.Count` gibt an, wie viele Schlüssel-Wert-Paare sich im Wörterbuch befinden.
* `Dictionary.Keys` gibt auch zurück, welche Schlüssel derzeit im Wörterbuch gespeichert sind.
* `Dictionary.Values` gibt zurück, welche Werte derzeit im Wörterbuch gespeichert sind.

**Die Möglichkeit, Daten allgemein mit Wörterbücher in Beziehung zu setzen, ist eine großartige Alternative zur vorherigen Verwendung von Indizen und Listen.**
