# Funktionen

Funktionen können in einem Codeblock erstellt und an anderer Stelle in einer Dynamo-Definition erneut aufgerufen werden. Dadurch erhalten Sie eine weitere Steuerungsmöglichkeit in parametrischen Dateien. Sie stellt eine Textversion eines benutzerdefinierten Blocks dar. In diesem Fall ist der übergeordnete Block problemlos verfügbar und kann sich an beliebiger Stelle im Diagramm befinden. Hierfür sind keine Verbindungen erforderlich.

## Übergeordneter Block

Die erste Zeile besteht aus dem Schlüsselwort "def" und dem Namen der Funktion mit den Namen der Eingaben in Klammern. Der Hauptteil der Funktion wird in geschweiften Klammern angegeben. Verwenden Sie zum Ausgeben eines Werts "return =". In Codeblöcken, die eine Funktion definieren, sind keine Eingabe- oder Ausgabeverbindungen vorhanden, da sie über andere Codeblöcke aufgerufen werden. ![Parents](../.gitbook/assets/21.png)

```
/*This is a multi-line comment,
which continues for
multiple lines*/
def FunctionName(in1,in2)
{
//This is a comment
sum = in1+in2;
return sum;
};
```

## Untergeordnete Blöcke

Sie können die Funktion in einem anderen Codeblock in derselben Datei aufrufen, indem Sie ihren Namen und dieselbe Anzahl von Argumenten angeben. Dies funktioniert auf dieselbe Weise wie die vordefinierten Blöcke aus der Bibliothek.

![Children](../.gitbook/assets/20.png)

```
FunctionName(in1,in2);
```

## Übungslektion

> Laden Sie die zu dieser Übungslektion gehörige Beispieldatei herunter (durch Rechtsklicken und Wahl der Option "Save Link As..."). Eine vollständige Liste der Beispieldateien finden Sie im Anhang. [Functions\_SphereByZ.dyn](https://github.com/h-iL/ForkedDynamoPrimerReorganized/blob/de/07\_Code-Block/datasets/7-4/Functions\_SphereByZ.dyn)

In dieser Übung erstellen Sie eine allgemeine Definition zum Erstellen von Kugeln aus einer eingegebenen Liste von Punkten. Der Radius dieser Kugeln wird durch die z-Eigenschaft des jeweiligen Punkts gesteuert.

![Exercise](../.gitbook/assets/11.jpg)

> Sie beginnen mit einem Zahlenbereich, der zehn Werte von 0 bis 100 umfasst. Verbinden Sie diesen mit einem _Point.ByCoordinates_-Block, um eine diagonale Linie zu erhalten.

![Exercise](<../.gitbook/assets/10 (5).jpg>)

> 1. Erstellen Sie einen _Code Block_ und geben Sie mithilfe der folgenden Codezeile die Definition ein:

```
def sphereByZ(inputPt){
};
```

Dabei ist _inputPt_ der Name, den Sie für die Punkte zuweisen, über die die Funktion gesteuert werden soll. Bis hierher hat die Funktion keine Wirkung. Dies entwickeln Sie jedoch in den folgenden Schritten.

![Exercise](../.gitbook/assets/09.jpg)

> 1. Fügen Sie der _Code Block_-Funktion einen Kommentar und die Variable _sphereRadius_ hinzu, die die _Z_-Position der einzelnen Punkte abfragt. Beachten Sie, dass die Methode _inputPt.Z_ keine Klammern benötigt. Da es sich um eine _Abfrage_ von Eigenschaften eines bestehenden Elements handelt, sind keine Eingaben erforderlich.

```
def sphereByZ(inputPt,radiusRatio)
{
//get Z Value, use it to drive radius of sphere
sphereRadius=inputPt.Z;
};
```

![Exercise](<../.gitbook/assets/08 (7).jpg>)

> 1. Als Nächstes rufen Sie die eben erstellte Funktion in einem anderen _Code Block_ auf. Wenn Sie im Ansichtsbereich doppelklicken, um einen neuen _Code Block_ zu erstellen, und _sphereB_ eingeben, schlägt Dynamo die eben definierte _sphereByZ_-Funktion vor: Die Funktion wurde der IntelliSense-Bibliothek hinzugefügt. Dieser Mechanismus ist sehr hilfreich.

![Exercise](<../.gitbook/assets/07 (8).jpg>)

> 1. Als Nächstes erstellen Sie eine Variable mit dem Namen _Pt_, um die Verbindung zu den Punkten herzustellen, die Sie in den vorherigen Schritten erstellt haben:

```
sphereByZ(Pt)
```

1. Die Ausgabe zeigt lediglich Nullwerte. Dies geschieht aus dem folgenden Grund: Beim Definieren der Funktion wurde festgelegt, dass die Variable _sphereRadius_ berechnet werden soll, Sie haben jedoch noch nicht definiert, was die Funktion als _Ausgabe_ _zurückgeben_ soll. Dies beheben Sie im nächsten Schritt.

![Exercise](<../.gitbook/assets/06 (5).jpg>)

> 1. In diesem wichtigen Schritt müssen Sie die Ausgabe der Funktion definieren. Fügen Sie die Zeile `return = sphereRadius;` in die _sphereByZ_-Funktion ein.

1. Jetzt zeigt die Ausgabe im _Code Block_ die z-Koordinaten der einzelnen Punkte an.

![Exercise](<../.gitbook/assets/05 (6).jpg>)

> Als Nächstes erstellen Sie die Kugeln, indem Sie die _übergeordnete_ Funktion bearbeiten.

> 1. Definieren Sie zunächst eine Kugel mit der folgenden Codezeile: `sphere=Sphere.ByCenterPointRadius(inputPt,sphereRadius);`

1. Ändern Sie dann den return-Wert in _sphere_ anstelle von _sphereRadius_: `return = sphere;`. Als Ergebnis erhalten Sie einige sehr große Kugeln in der Dynamo-Vorschau.

![Exercise](<../.gitbook/assets/04 (12).jpg>)

> 1. Um Kugeln von angemessenerer Größe zu erhalten, aktualisieren Sie den Wert von _sphereRadius_, indem Sie ihn dividieren: `sphereRadius = inputPt.Z/20;`. Jetzt sind die einzelnen Kugeln getrennt sichtbar und die Beziehung zwischen dem Radius und dem z-Wert wird erkennbar.

![Exercise](<../.gitbook/assets/03 (7).jpg>)

> 1. Indem Sie im _Point.ByCoordinates_-Block die Vergitterung von _Kürzeste_ in _Kartesisches Produkt_ ändern, erstellen Sie ein Raster aus Punkten. Die _sphereByZ_-Funktion ist weiterhin uneingeschränkt wirksam, d. h., für alle Punkte werden Kugeln mit von ihren z-Werten abhängigen Radien erstellt.

![Exercise](<../.gitbook/assets/02 (10).jpg>)

> 1. Verbinden Sie jetzt als weiteren Test die ursprüngliche Zahlenliste mit der x-Eingabe von _Point.ByCoordinates_. Dadurch entsteht ein Würfel aus Kugeln.

1. Anmerkung: Wenn diese Berechnung auf Ihrem Computer viel Zeit in Anspruch nimmt, ändern Sie den Wert _#10_ in einen kleineren Wert, z. B. _#5_.

![Exercise](<../.gitbook/assets/01 (10).jpg>)

> 1. Beachten Sie, dass die von Ihnen erstellte Funktion _sphereByZ_ eine allgemeine Funktion ist. Sie können daher die Helix aus einer der vorigen Lektionen erneut öffnen und die Funktion darauf anwenden.

![Exercise](../.gitbook/assets/20.jpg)

> In einem letzten Schritt steuern Sie das Radienverhältnis über einen benutzerdefinierten Parameter. Zu diesem Zweck müssen Sie eine neue Eingabe für die Funktion erstellen und den Teiler _20_ durch einen Parameter ersetzen.

> 1. Aktualisieren Sie die Definition von _sphereByZ_ wie folgt:

```
def sphereByZ(inputPt,radiusRatio)
{
//get Z Value, use it to drive radius of sphere
sphereRadius=inputPt.Z/radiusRatio;
//Define Sphere Geometry
sphere=Sphere.ByCenterPointRadius(inputPt,sphereRadius);
//Define output for function
return sphere;
};
```

1. Aktualisieren Sie die untergeordneten Codeblöcke, indem Sie der Eingabe die Variable _ratio_ hinzufügen: `sphereByZ(Pt,ratio);`. Verbinden Sie einen Schieberegler mit der neu erstellten Codeblock-Eingabe und ändern Sie die Größe der Radien anhand des Radienverhältnisses.
