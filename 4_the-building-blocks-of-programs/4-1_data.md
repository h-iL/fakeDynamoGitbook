# Daten

Daten sind das Material unserer Programme. Sie fließen als Eingaben durch "Drähte" in Blöcke, wo sie verarbeitet und in eine neue Form von Ausgabedaten umgewandelt werden. Hier sollen zunächst die Definition und Struktur von Daten betrachtet werden, bevor Sie damit beginnen, sie in Dynamo zu verwenden.

## Was sind Daten?

Unter Daten versteht man eine Gruppe von Werten für qualitative oder quantitative Variable. Die einfachste Form von Daten sind Zahlen wie z. B. `0`, `3.14` oder `17`. Es gibt jedoch eine Reihe unterschiedlicher Datentypen: Variable, die für veränderliche Zahlen stehen (`Höhe`); Zeichen (`meinName`); Geometrie (`Kreis`) oder eine Liste von Datenelementen (`1,2,3,5,8,13,...`). Daten müssen in die Eingabeanschlüsse der Blöcke in Dynamo eingegeben werden: Daten können ohne Aktionen existieren, aber die Aktionen, die durch die Blöcke dargestellt werden, können nur durchgeführt werden, wenn Daten vorhanden sind. Wenn Sie im Arbeitsbereich einen Block hinzufügen, ohne Eingaben bereitzustellen, ist das Ergebnis eine Funktion, nicht das Ergebnis der eigentlichen Aktion.

![Daten und Aktionen](../.gitbook/assets/00-DataAndActions.png)

> 1. Einfache Daten

1. Daten und Aktion (Block): erfolgreiche Ausführung
2. Aktion (Block) ohne Daten gibt eine allgemeine Funktion zurück

## Vermeiden Sie Nullen

Der Typ `'null'` steht für das Fehlen von Daten. Dies ist zwar ein abstraktes Konzept, dem Sie jedoch bei der Arbeit mit visueller Programmierung sehr wahrscheinlich begegnen werden. Wenn eine Aktion kein gültiges Ergebnis erstellt, gibt der Block Null zurück. Das Ermitteln und Entfernen von Nullwerten aus Datenstrukturen ist ein entscheidender Schritt zum Erstellen stabiler Programme.

| Symbol                                                 | Name/Syntax   | Eingaben | Ausgaben |
| ------------------------------------------------------ | ------------- | -------- | -------- |
| ![](../.gitbook/assets/DSCore-Object-IsNull-Large.jpg) | Object.IsNull | obj      | bool     |

## Datenstrukturen

Bei der visuellen Programmierung können sehr schnell große Datenmengen generiert werden. Aus diesem Grund benötigen Sie ein Verfahren zur Verwaltung von deren Hierarchie. Dies ist die Funktion der Datenstrukturen, der organisatorischen Schemata, in denen Daten gespeichert werden. Die Charakteristika der Datenstrukturen und ihrer Verwendung sind von Programmiersprache zu Programmiersprache unterschiedlich. in Dynamo werden Daten mithilfe von Listen hierarchisch geordnet. Dies wird in den weiteren Kapiteln ausführlich erläutert. Am Anfang sollen einige einfache Beispiele stehen:

Eine Liste für eine Sammlung von Elementen, die in einer Struktur von Daten abgelegt wurden:

* Sie haben fünf Finger (_Elemente_) an einer Hand (_Liste_).
* Zehn Häuser (_Elemente_) stehen entlang einer Straße (_Liste_).

![Übersicht zu Listen](../.gitbook/assets/01-ListBreakdown.png)

> 1. Ein **Number Sequence**-Block definiert eine Liste von Zahlen mithilfe der Eingaben _start_, _amount_ und _step_. Mithilfe dieser beiden Blöcke wurden zwei separate Listen mit je zehn Zahlen – _100–109_ und _0–9_ erstellt.

1. Mithilfe des Blocks **List.GetItemAtIndex** wird das Element an einer bestimmten Indexposition ausgewählt. Wenn Sie _0_ wählen, wird das erste Element in der Liste (in diesem Fall_100_) abgerufen.
2. In der zweiten Liste erhalten Sie mit demselben Verfahren den Wert _0_, das erste Element in der Liste.
3. Als Nächstes führen Sie die beiden Listen mithilfe eines **List.Create**-Blocks zu einer zusammen. Mit diesem Block wird eine _Liste von Listen erstellt._ Dies verändert die Struktur der Daten.
4. Wenn Sie **List.GetItemAtIndex** erneut mit dem Index _0_ verwenden, erhalten Sie die erste der in der übergeordneten Liste enthaltenen Listen. Dieses Beispiel verdeutlicht, wie Listen behandelt werden: Sie gelten – anders als in anderen Skriptsprachen – als Objekte. Listenbearbeitung und Datenstruktur werden in den später folgenden Kapiteln genauer beschrieben.

Als wichtigstes Prinzip zum Verständnis der Datenhierarchie in Dynamo gilt: **Innerhalb der Datenstruktur gelten Listen als Elemente.** In anderen Worten: In Dynamo kommt ein hierarchisch von oben nach unten geordneter Prozess für Datenstrukturen zum Einsatz. Was bedeutet das? Das folgende Beispiel soll dies verdeutlichen:

## Erstellen einer Kette von Zylindern mithilfe von Daten

> Laden Sie die Beispieldatei für diese Übungslektion herunter (durch Rechtsklicken und Wahl von "Save Link As..."): \[Building Blocks of Programs - Data.dyn]\(datasets/4-1/Building Blocks of Programs - Data.dyn). Eine vollständige Liste der Beispieldateien finden Sie im Anhang.

In diesem ersten Beispiel erstellen Sie zur Demonstration der in diesem Abschnitt behandelten Geometriehierarchie einen Zylinder und geben seine Wandstärke an. ![](../.gitbook/assets/1.png)

> 1. **Point.ByCoordinates**: Nachdem Sie diesen Block im Ansichtsbereich hinzugefügt haben, wird ein Punkt am Ursprung des Rasters in der Dynamo-Vorschau angezeigt. Die Vorgabewerte der Eingaben für _x, y_ und _z_ sind _0.0_, wodurch ein Punkt an dieser Position definiert wird.

![](../.gitbook/assets/2.png)

> 1. **Plane.ByOriginNormal**: Die nächste Stufe in der Geometriehierarchie ist eine Ebene. Es gibt mehrere Möglichkeiten für die Konstruktion einer Ebene: Hier werden ein Ursprung und eine Normale als Eingaben verwendet. Der Ursprung ist der Punkt, den Sie mithilfe des Blocks im vorigen Schritt erstellt haben.

1. **Vector.ZAxis**: Dies ist ein Vektor mit Einheiten in z-Richtung. Hier sind keine Eingaben, sondern nur ein Vektor mit dem Wert \[0,0,1] vorhanden. Dieser wird für die _normal_-Eingabe des _Plane.ByOriginNormal_-Blocks verwendet. In der Dynamo-Vorschau wird daraufhin eine rechteckige Ebene angezeigt.

![](../.gitbook/assets/3.png)

> 1. **Circle.ByPlaneRadius**: Eine Stufe höher in der Hierarchie erstellen Sie aus der Ebene, die Sie im letzten Schritt erstellt haben, eine Kurve. Nachdem Sie den Block verbunden haben, erhalten Sie einen Kreis um den Ursprungspunkt. Als Radius ist in diesem Block der Wert _1_ vorgegeben.

![](../.gitbook/assets/4.png)

> 1. **Curve.Extrude**: In diesem Schritt wandeln Sie dieses Objekt in einen 3D-Körper um. Dieser Block erstellt durch Extrusion eine Oberfläche aus einer Kurve. Der vorgegebene Abstand im Block beträgt _1_ und im Ansichtsfenster ist jetzt ein Zylinder zu sehen.

![](../.gitbook/assets/5.png)

> 1. **Surface.Thicken**: Mit diesem Block erhalten Sie einen geschlossenen Körper, indem die Oberfläche um den angegebenen Wert versetzt und die entstehende Form geschlossen wird. Der Vorgabewert für die Verdickung ist _1_. Im Ansichtsfenster wird ein Zylinder mit der entsprechenden Wandstärke angezeigt.

![](../.gitbook/assets/6.png)

> 1. **Number Slider**: Anstatt die Vorgabewerte für alle diese Eingaben zu verwenden, können Sie dem Modell auch Funktionen zur parametrischen Steuerung hinzufügen.

1. **Domänenbearbeitung**: Nachdem Sie den Zahlen-Schieberegler im Ansichtsbereich hinzugefügt haben, klicken Sie auf die Pfeilspitze oben links, um die Domänenoptionen anzuzeigen.
2. **Min/Max/Step**: Ändern Sie die Werte für _min_, _max_ und _step_ in _0_,_2_ und _0.01_. Mit diesen Angaben steuern Sie die Gesamtgröße der Geometrie.

![](../.gitbook/assets/7.png)

> 1. **Number Slider**-Blöcke: Erstellen Sie mehrere Kopien dieses Number Slider-Blocks (indem Sie ihn auswählen und anschließend zuerst Strg+C und dann Strg+V drücken), bis für alle Eingaben anstelle der bisherigen Vorgaben Verbindungen zu den Number Sliders verwendet werden. Manche Werte für diese Schieberegler müssen größer als Null sein, damit die Definition verwendbar ist. So wird beispielsweise eine Tiefe für die Extrusion benötigt, damit eine Oberfläche entsteht, die verdickt werden kann.

Sie haben jetzt mithilfe dieser Regler einen parametrischen Zylinder mit Angabe einer Wandstärke erstellt. Experimentieren Sie mit einigen dieser Parameter und beobachten Sie die dynamische Veränderung der Geometrie im Dynamo-Ansichtsfenster.

![](../.gitbook/assets/8.png)

> 1. **Number Sliders**-Blöcke: In einem weiteren Schritt wurden etliche weitere Schieberegler im Ansichtsbereich hinzugefügt und die Benutzeroberfläche des neu erstellten Werkzeugs muss übersichtlicher gestaltet werden. Klicken Sie mit der rechten Maustaste nacheinander auf die einzelnen Schieberegler, wählen Sie Umbenennen und ändern Sie den Namen jedes Schiebereglers in den Namen des dazugehörigen Parameters. Die Namen können Sie der Abbildung oben entnehmen.

Damit haben Sie einen perfekten verdickten Zylinder erstellt. Dies ist jedoch nur ein einzelnes Objekt. Im nächsten Schritt wird gezeigt, wie Sie ein Array von Zylindern erstellen, die dynamisch miteinander verbunden bleiben. Zu diesem Zweck arbeiten Sie nicht mit einem einzelnen Element, sondern erstellen eine Liste von Zylindern.

![](../.gitbook/assets/9.png)

> 1. **Addition (+)**: Neben dem eben erstellten Zylinder soll eine Reihe weiterer Zylinder hinzugefügt werden. Um einen Zylinder direkt neben dem vorhandenen hinzuzufügen, müssen Sie sowohl dessen Radius als auch die Stärke seiner Wand berücksichtigen. Diesen Wert erhalten Sie durch Addition der Werte aus den beiden Schiebereglern.

![](../.gitbook/assets/10.png)

> Dieser Schritt ist etwas komplexer und wird daher im Einzelnen erläutert: Erstellt werden soll eine Liste mit Zahlen, die die Positionen der einzelnen Zylinder in einer Reihe definieren.

> 1. **Multiplikation**: Als Erstes müssen Sie den Wert aus dem vorigen Schritt mit 2 multiplizieren. Der Wert aus dem vorherigen Schritt gibt den Radius an, der Zylinder muss jedoch um den vollständigen Durchmesser verschoben werden.

1. **Sequence**: Mithilfe dieses Blocks erstellen Sie ein Array von Zahlen. Die erste Eingabe ist der Wert des _Multiplikation_-Blocks aus dem vorigen Schritt in den _step_-Wert. Als _start_-Wert können Sie _0.0_ festlegen. Verwenden Sie hierfür einen _number_-Block.
2. **Integer Slider**: Verbinden Sie für den _amount_-Wert einen Integer-Schieber. Diese Funktion definiert, wie viele Zylinder erstellt werden.
3. **Ausgabe**: Diese Liste zeigt den Abstand, um den die einzelnen Zylinder im Array versetzt werden. Sie wird parametrisch durch die ursprünglichen Schieberegler gesteuert.

![](<../.gitbook/assets/11 (1).png>)

> 1. Dieser Schritt ist einfach: Verbinden Sie die im letzten Schritt erstellte Sequenz mit der _x_-Eingabe des ursprünglichen _Point.ByCoordinates_. Dies ersetzt den Schieberegler _pointX_, den Sie löschen können. Im Ansichtsfenster wird jetzt ein Array von Zylindern angezeigt (achten Sie darauf, dass im Integer Slider ein Wert größer als Null angegeben ist).

![](../.gitbook/assets/12.png)

> Die Kette der Zylinder ist weiterhin dynamisch mit allen Schiebereglern verknüpft. Experimentieren Sie mit den Schiebereglern, und beobachten Sie, wie die Definition aktualisiert wird.
