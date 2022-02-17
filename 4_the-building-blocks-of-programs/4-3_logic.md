# Logik

**Logik**, genauer **Bedingungslogik** ermöglicht die Angabe einer Aktion oder einer Gruppe von Aktionen unter Verwendung einer Prüfung. Die Auswertung der Prüfung ergibt einen booleschen Wert für `True` oder `False`, der zur Steuerung des Programmablaufs verwendet werden kann.

## Boolesche Werte

Numerische Variablen können für eine Vielzahl unterschiedlicher Zahlen stehen. Boolesche Variablen hingegen können nur zwei Werte annehmen, die als True oder False, Ja oder Nein, 1 oder 0 wiedergegeben werden. Booleschen Operationen werden wegen ihrer begrenzten Möglichkeiten nur selten zum Durchführen von Berechnungen verwendet.

## Bedingungsanweisungen

Die "If"-Anweisung ist ein wichtiges Konzept in der Programmierung: "Wenn _dies_ zutrifft (True), dann geschieht _das_, andernfalls geschieht _etwas anderes_. Die aus der Anweisung resultierende Aktion wird durch einen booleschen Wert gesteuert. In Dynamo stehen mehrere Möglichkeiten zum Definieren von If-Anweisungen zur Verfügung:

| Symbol                                                            | Name      | Syntax      | Eingaben          | Ausgaben |
| ----------------------------------------------------------------- | --------- | ----------- | ----------------- | -------- |
| ![](../.gitbook/assets/DSCoreNodesUI-Logic-If-Large.jpg)          | Wenn      | If          | test, true, false | result   |
| ![](../.gitbook/assets/DSCoreNodesUI-Formula-Large.jpg)           | Formel    | if (x, y,z) | x, y, z           | result   |
| ![](../.gitbook/assets/Dynamo-Nodes-CodeBlockNodeModel-Large.jpg) | Codeblock | (x?y:z)     | x, y, z           | result   |

Die folgenden kurzen Beispiele zeigen die Funktionsweise dieser drei Blöcke in der If-Bedingungsanweisung.

![](../.gitbook/assets/IFs.jpg)

> In dieser Abbildung wurde im _Boolean_ die Option _True_, eingestellt, d. h., das Ergebnis ist die Zeichenfolge: _"this is the result if true"._ Die drei möglichen Blöcke, mit deren Hilfe die _If_-Anweisung erstellt werden kann, funktionieren hier auf dieselbe Weise.

![](../.gitbook/assets/IFs2.jpg)

> Auch in diesem Fall funktionieren die Blöcke auf dieselbe Weise. Wenn Sie den _Boolean_-Wert in _False_ ändern, wird als Ergebnis die Zahl _Pi_ ausgegeben, wie in der ursprünglichen _If_-Anweisung festgelegt.

## Filtern einer Liste

> Laden Sie die Beispieldatei für diese Übungslektion herunter (durch Rechtsklicken und Wahl von Save Link As...): \[Building Blocks of Programs - Logic.dyn]\(datasets/4-3/Building Blocks of Programs - Logic.dyn). Eine vollständige Liste der Beispieldateien finden Sie im Anhang.

In diesem Beispiel teilen Sie eine Liste von Zahlen in eine Liste mit geraden und eine Liste ungeraden Zahlen auf.

![](<../.gitbook/assets/01 (12).jpg>)

> 1. **Range**: Definieren Sie im Ansichtsbereich einen Zahlenbereich.

1. **Number**-Blöcke: Fügen Sie im Ansichtsbereich drei Number-Blöcke ein. Legen Sie in diesen Blöcken die folgenden Werte fest: _0.0_ für _start_, _10.0_ für _end_ und _1.0_ für _step_.
2. **Ausgabe**: Die Ausgabe zeigt eine Liste mit 11 Zahlen von 0-10.
3. **Modulus (%)**: Verbinden Sie _Range_ mit _x_ und _2.0_ mit _y_. Mit dieser Funktion wird für jede Zahl aus der Liste der Rest bei Division durch 2 berechnet. Die Ausgabe für diese Liste ist eine Liste, die abwechselnd die Werte 0 und 1 enthält.
4. **Gleichheitsprüfung (==)**: Fügen Sie im Ansichtsbereich einen Block für die Gleichheitsprüfung hinzu. Verbinden Sie die Ausgabe des _Modulus_-Blocks mit der _x_-Eingabe und _0.0_ mit der _y_-Eingabe.
5. **Watch**: Die Gleichheitsprüfung gibt eine Liste aus, die abwechselnd die Werte true und false enthält. Mithilfe dieser Werte werden die Einträge aus der Zahlenliste eingeordnet. Dabei steht _0_ (bzw. _true_) für gerade und (_1_ bzw. _false_) für ungerade Zahlen.
6. **List.FilterByBoolMask**: Dieser Block filtert die Werte anhand der eingegebenen Booleschen Operation in zwei Listen. Verbinden Sie den ursprünglichen _number range_ mit der _list_-Eingabe und die Ausgabe der _Gleichheitsprüfung_ mit der _mask_-Eingabe. Die _in_-Ausgabe enthält die true-Werte, die _out_-Ausgabe die false-Werte.
7. **Watch**: Als Ergebnis erhalten Sie eine Liste mit geraden und eine Liste mit ungeraden Zahlen. Damit haben Sie mithilfe logischer Operatoren Listen anhand eines Musters aufgeteilt.

## Aus Logik wird Geometrie

In diesem Schritt wenden Sie die in der ersten Übung erstellte Logik auf einen Modellierungsvorgang an.

![](<../.gitbook/assets/02 (1).png>) Beginnen Sie mit den Blöcken aus der letzten Übung. Die einzigen Ausnahmen (zusätzlich zum Ändern des Formats) sind:

> 1. Die Eingabewerte wurden geändert.

1. Die in-Listeneingabe für _List.FilterByBoolMask_ wurde entfernt. Diese Blöcke werden momentan nicht benötigt, kommen aber weiter unten in dieser Übung zum Einsatz.

![](../.gitbook/assets/03.png)

> Beginnen Sie, indem Sie die Blöcke wie in der Abbildung oben gezeigt miteinander verbinden. Diese Gruppe von Blöcken stellt eine parametrische Gleichung zum Definieren einer Sinuskurve dar. Einige Hinweise:

> 1. Im **ersten Schieberegler** müssen als Mindestwert 1, als Höchstwert 4 und als Schritt 0.01 angegeben werden.

1. Im **zweiten Schieberegler** müssen als Mindestwert 0, als Höchstwert 1 und als Schritt 0.01 angegeben werden.
2. **PolyCurve.ByPoints**: Indem Sie das oben gezeigte Blockdiagramm kopieren, erhalten im Ansichtsfenster der Dynamo-Vorschau eine Sinuskurve.

Für die Eingaben gilt hier folgende Regel: Verwenden Sie Zahlenblöcke für statische und Schieberegler für veränderliche Eigenschaften. Der anfangs definierte ursprüngliche Zahlenbereich soll erhalten bleiben. Für die Sinuskurve, die hier erstellt werden soll, wird jedoch mehr Flexibilität benötigt. Mithilfe dieser Schieberegler können Sie die Frequenz und Amplitude der Kurve ändern.

![](../.gitbook/assets/04.png)

> Die Schritte dieser Definition werden hier nicht nacheinander beschrieben. Hier wird zunächst das Endergebnis gezeigt, um eine Vorstellung der fertigen Geometrie zu vermitteln. Die ersten beiden Schritte wurden separat durchgeführt und müssen jetzt zusammengeführt werden. Die Position der reißverschlussähnlichen Bauteile soll durch die zugrunde liegende Sinuskurve gesteuert werden, wobei mithilfe der True/False-Logik abwechselnd große und kleine Quader eingefügt werden.

![](<../.gitbook/assets/05 (1).png>)

> 1. **Math.RemapRange**: Erstellen Sie aus der in Schritt 01 erstellten Zahlenfolge eine neue Zahlenfolge, indem Sie den Bereich neu zuordnen. In Schritt 01 wurden Zahlen von 0 – 100 festgelegt. Diese Zahlen liegen zwischen 0 und 1, wie mithilfe der Eingaben _newMin_ und _newMax_ festgelegt.

![](../.gitbook/assets/06.png)

> 1. **Curve.PointAtParameter**: Verbinden Sie _Polycurve.ByPoints_ (aus Schritt 2) mit _curve_ und _Math.RemapRange_ mit _param_. Mithilfe dieses Schritts erstellen Sie Punkte entlang der Kurve. Die Zahlen mussten dem Bereich 0 bis 1 neu zugeordnet werden, da als Eingabe für _param_ Werte in diesem Bereich verlangt werden. Der Wert _0_ steht für den Startpunkt, der Wert _1_ für die Endpunkte. Die Auswertung aller dazwischen liegenden Zahlen ergibt Werte im Bereich _\[0,1]_.

![](../.gitbook/assets/07.png)

> 1. \*\*List.FilterByBoolMask - \*\* Verbinden Sie _Curve.PointAtParameter_ aus dem vorigen Schritt mit der _list_-Eingabe.

1. **Watch**: Die Watch-Blöcke für _in_ und _out_ zeigen, dass zwei Listen für gerade bzw. ungerade Indizes erstellt wurden. Diese Punkte sind auf dieselbe Weise entlang der Kurve angeordnet, wie im folgenden Schritt gezeigt.

![](../.gitbook/assets/08.png)

> 1. **Cuboid.ByLengths**: Stellen Sie die in der Abbildung oben gezeigten Verbindungen wieder her, um eine reißverschlussähnliche Struktur entlang der Kurve zu erhalten. Sie erstellen hier einfache Quader, deren Größe jeweils durch ihren auf der Kurve liegenden Mittelpunkt definiert wird. Die Logik der Aufteilung in gerade und ungerade Werte wird damit im Modell deutlich.

![](../.gitbook/assets/matrix.png)

> 1. **Number Slider**: Wenn Sie zum Anfang dieser Definition zurückkehren, können Sie mit den Werten im Schieberegler experimentieren und beobachten, wie sich der "Reißverschluss" verändert. Die obere Reihe der Abbildungen zeigt den Wertebereich für den oberen Zahlen-Schieberegler. Er steuert die Frequenz der Welle.

1. **Number Slider**: Die untere Reihe der Abbildungen zeigt den Wertebereich für den unteren Zahlen-Schieberegler. Er steuert die Amplitude der Welle.
