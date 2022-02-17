# Dokumentation

Die Bearbeitung von Parametern für die Dokumentation schließt sich an die in den vorigen Abschnitten behandelten Aufgaben an. In diesem Abschnitt bearbeiten Sie Parameter, mit deren Hilfe Sie nicht die geometrischen Eigenschaften von Elementen steuern, sondern eine Revit-Datei für die Konstruktionsunterlagen erstellen können.

### Abweichung

In der folgenden Übung verwenden Sie einen einfachen Block für die Abweichung von der Ebene, um einen Revit-Plan für die Dokumentation zu erstellen. Die einzelnen Elemente der parametrisch definierten Dachkonstruktion weisen unterschiedliche Abweichungswerte auf. Die Werte innerhalb dieses Bereichs sollen mithilfe von Farben gekennzeichnet und die adaptiven Punkte in einer Bauteilliste ausgegeben werden, sodass die Daten an einen Fassadenspezialisten, Bauingenieur oder Subunternehmer weitergegeben werden können.

![deviation](../.gitbook/assets/deviation.jpg)

> Der Block für die Abweichung von der Ebene berechnet, in welchem Grad die Gruppe aus vier Punkten von der optimalen Ebene zwischen ihnen abweicht. Dies ist eine schnelle und einfache Möglichkeit zur Untersuchung der Realisierbarkeit.

## Übungslektion

> Laden Sie die zu dieser Übungslektion gehörigen Beispieldateien herunter (durch Rechtsklicken und Wahl der Option "Save Link As"). Eine vollständige Liste der Beispieldateien finden Sie im Anhang.

> 1. [Documenting.dyn](https://github.com/h-iL/ForkedDynamoPrimerReorganized/blob/de/08\_Dynamo-for-Revit/datasets/8-6/Documenting.dyn)

1. [ARCH-Documenting-BaseFile.rvt](https://github.com/h-iL/ForkedDynamoPrimerReorganized/blob/de/08\_Dynamo-for-Revit/datasets/8-6/ARCH-Documenting-BaseFile.rvt)

Beginnen Sie mit der Revit-Datei für diesen Abschnitt (oder verwenden Sie weiterhin die Datei aus dem vorigen Abschnitt). Diese Datei zeigt eine Gruppe von EFTE-Elementen auf dem Dach. Diese Elemente werden in dieser Übung referenziert.

![Exercise](<../.gitbook/assets/17 (1).jpg>)

> 1. Fügen Sie einen _Family Types_-Block in den Ansichtsbereich ein und wählen Sie _"ROOF-PANEL-4PT"_.

1. Verbinden Sie diesen Block mit einem _All Elements of Family Type_-Block, um alle diese Elemente auszuwählen und aus Revit in Dynamo zu übernehmen.

![Exercise](<../.gitbook/assets/16 (1).jpg>)

> 1. Rufen Sie die Positionen der adaptiven Punkte für die einzelnen Elemente mithilfe eines _AdaptiveComponent.Locations_-Blocks ab.

1. Erstellen Sie mithilfe eines _Polygon.ByPoints_-Blocks Polygone jeweils aus den vier Eckpunkten. Dadurch erhalten Sie eine abstrakte Version des aus Einzelelementen bestehenden Systems in Dynamo, ohne dass die vollständige Geometrie des Revit-Elements importiert werden muss.
2. Berechnen Sie die planare Abweichung mithilfe des _Polygon.PlaneDeviation_-Blocks.

![Exercise](../.gitbook/assets/15.jpg)

> In der folgenden kurzen Zusatzübung legen Sie den _Öffnungsgrad_ der einzelnen Elemente anhand ihrer planaren Abweichung fest.

> 1. Fügen Sie im Ansichtsbereich einen _Element.SetParameterByName_-Block hinzu und verbinden Sie die adaptiven Bauteile mit der _element_-Eingabe. Verbinden Sie einen _Code Block_ mit der Angabe _"Aperture Ratio"_ mit der _parameterName_-Eingabe.

1. Die Ergebnisse der Abweichungsberechnung können nicht direkt mit der value-Eingabe verbunden werden, da die Werte zunächst dem Parameterbereich neu zugeordnet werden müssen.

![Exercise](../.gitbook/assets/14.jpg)

> 1. Ordnen Sie mithilfe von _Math.RemapRange_ die Abweichungswerte einer Domäne zwischen _.15_ und _.45_ zu.

1. Verbinden Sie diese Ergebnisse mit der value-Eingabe von _Element.SetParameterByName_.

![Exercise](../.gitbook/assets/13.jpg)

> In Revit ist die Veränderung der Öffnungen in der Oberfläche _ungefähr_ zu erkennen.

![Exercise](../.gitbook/assets/13a.jpg)

> Die vergrößerte Darstellung zeigt deutlicher, dass die weniger weit geöffneten Elemente sich näher an den Ecken befinden. Die weit geöffneten Elemente befinden sich hingegen ganz oben. Die Eckbereiche weisen stärkere Abweichungen, der Scheitel der Wölbung dagegen die geringste Krümmung auf. Das Ergebnis ist daher überzeugend.

## Farben und Dokumentation

Durch Festlegen des Öffnungsgrads wird die Abweichung der Elemente des Dachs nicht präzise dargestellt. Zudem kommt es zu Änderungen an der Geometrie des Elements selbst. Angenommen, Sie möchten lediglich die Abweichung unter dem Gesichtspunkt der Realisierbarkeit analysieren. In diesem Fall wäre es hilfreich, für die Dokumentation die Elemente in Abhängigkeit von Abweichungsbereichen farbig zu kennzeichnen. Dies ist mithilfe der folgenden Schritte möglich, wobei der Vorgang dem oben beschriebenen sehr ähnlich ist.

![Exercise](<../.gitbook/assets/11 (1).jpg>)

> 1. Entfernen Sie _Element.SetParameterByName_ und die dazugehörigen Blöcke und fügen Sie _Element.OverrideColorInView_ hinzu.

1. Fügen Sie im Ansichtsbereich einen _Color Range_-Block hinzu und verbinden Sie ihn mit der color-Eingabe von _Element.OverrideColorInView_. Um den Farbverlauf zu erstellen, müssen Sie noch die Abweichungswerte mit dem Farbbereich verbinden.
2. Wenn Sie den Mauszeiger auf die _value_-Eingabe setzen, wird angezeigt, dass Werte zwischen _0_ und _1_ für die Zuordnung von Farben zu Werten erforderlich sind. Sie müssen daher die Abweichungswerte für diesen Bereich neu zuordnen.

![Exercise](<../.gitbook/assets/10 (1).jpg>)

> 1. Ordnen Sie mithilfe von _Math.RemapRange_ die Werte für die planare Abweichung dem Bereich zwischen _0_ und _1_ zu. (Anmerkung: Sie können die Quelldomäne auch mithilfe eines _MapTo_-Blocks definieren.)

1. Verbinden Sie die Ergebnisse mit einem _Color Range_-Block.
2. Dadurch erhalten Sie als Ausgabe einen Bereich von Farben anstelle eines Bereichs von Zahlen.
3. Falls Manuell eingestellt ist, klicken Sie auf _Ausführen_. Für den Rest dieses Vorgangs können Sie die Einstellung Automatisch verwenden.

![Exercise](<../.gitbook/assets/09 (1).jpg>)

> In Revit ist jetzt eine wesentlich übersichtlichere Darstellung mit einem Farbverlauf zu sehen, der die planare Abweichung unter Verwendung des Farbbereichs zeigt. Die Farben müssen jedoch möglicherweise angepasst werden. Momentan werden die Werte für die kleinste Abweichung in Rot angezeigt: Dies scheint das Gegenteil des erwarteten Resultats zu sein. Stattdessen soll der Höchstwert der Abweichung in Rot dargestellt werden, während für die kleinste Abweichung eine ruhigere Farbe verwendet wird. Kehren Sie zu Dynamo zurück, um dies zu korrigieren.

![Exercise](../.gitbook/assets/08.jpg)

> 1. Geben Sie in einem _Code Block_ zwei Zahlen in zwei getrennten Zeilen ein: `0;` und `255;`.

1. Erstellen Sie die Farben Rot und Blau, indem Sie die entsprechenden Werte mit zwei _Color.ByARGB_-Blöcken verbinden.
2. Erstellen Sie eine Liste aus diesen beiden Farben.
3. Verbinden Sie diese Liste mit der _colors_-Eingabe des _Color Range_ und beobachten Sie die Aktualisierung dieses benutzerdefinierten Farbbereichs.

![Exercise](<../.gitbook/assets/07 (7).jpg>)

> In Revit ist die Darstellung der Bereiche mit maximaler Abweichung in den Ecken jetzt besser verständlich. Mithilfe dieses Blocks werden Farben in einer Ansicht überschrieben. Aus diesem Grund kann es sehr hilfreich sein, wenn unter den Zeichnungen ein bestimmter Plan für einen bestimmten Analysetyp vorhanden ist.

## Bauteillisten

![Exercise](../.gitbook/assets/06.jpg)

> 1. Wenn Sie eines der ETFE-Elemente in Revit auswählen, werden vier Exemplarparameter angezeigt: _XYZ1, XYZ2, XYZ3_ und _XYZ4_. Diese sind nach der Erstellung leer. Diese Parameter sind textbasiert und benötigen Werte. Sie schreiben mithilfe von Dynamo die Positionen der adaptiven Punkte in die einzelnen Parameter. Dies verbessert die Interoperabilität, falls die Geometrie an einen Bauingenieur oder Fassadenspezialisten weitergegeben werden soll.

![Exercise](<../.gitbook/assets/03 (11).jpg>)

> Der Beispielplan zeigt eine große, leere Bauteilliste. Die XYZ-Parameter sind gemeinsam genutzte Parameter in der Revit-Datei und können daher in die Bauteilliste aufgenommen werden.

![Exercise](<../.gitbook/assets/02 (4).jpg>)

> Die vergrößerte Darstellung zeigt, dass die XYZ-Parameter noch ausgefüllt werden müssen. Die ersten beiden Parameter werden von Revit vorgegeben.

![Exercise](<../.gitbook/assets/05 (8).jpg>)

> Um diese Werte zu schreiben, ist eine komplexe Listenoperation erforderlich. Das Diagramm selbst ist recht einfach, nutzt jedoch in großem Umfang die Listenzuordnung wie im Kapitel zu Listen beschrieben.

> 1. Wählen Sie mithilfe der oben gezeigten Blöcke alle adaptiven Bauteile aus.

1. Extrahieren Sie die Positionen der einzelnen Punkte mithilfe von _AdaptiveComponent.Locations_.
2. Konvertieren Sie diese Punkte in Zeichenfolgen. Beachten Sie, dass Sie hier textbasierte Parameter verwenden, und achten Sie darauf, den richtigen Datentyp einzugeben.
3. Erstellen Sie eine Liste mit den vier Zeichenfolgen, die die zu ändernden Parameter definieren: _XYZ1, XYZ2, XYZ3_ und _XYZ4_.
4. Verbinden Sie diese Liste mit der _parameterName_-Eingabe von _Element.SetParameterByName_.
5. Verbinden Sie _Element.SetParameterByName_ mit der _combinator_-Eingabe von _List.Combine_.
6. Verbinden Sie die _adaptiven Bauteile_ mit _list1_.
7. Verbinden Sie _String from Object_ mit _list2_.
8. In diesem Vorgang werden Listen zugeordnet: Für jedes Element werden vier Werte geschrieben, wodurch eine komplexe Datenstruktur entsteht. Der _List.Combine_-Block definiert eine Operation, die eine Stufe tiefer in der Datenhierarchie abläuft. Aus diesem Grund wurden die Eingaben für Element und Wert leer gelassen. _List.Combine_ verbindet die Unterlisten aus seinen Eingaben mit den leeren Eingaben von _List.SetParameterByName_ in der Reihenfolge, in der sie verbunden wurden.

![Exercise](<../.gitbook/assets/04 (3).jpg>)

> Wenn Sie jetzt ein Element in Revit auswählen, werden die Werte der einzelnen Parameter als Zeichenfolgen angezeigt. In der Praxis würden Sie ein einfacheres Format zum Schreiben von Punkten (x, y, z) erstellen. Sie könnten dies mithilfe von Zeichenfolgenoperationen in Dynamo erreichen. Da dies jedoch den Rahmen dieses Kapitels sprengen würde, wird dieses Verfahren hier nicht behandelt.

![Exercise](<../.gitbook/assets/01 (16).jpg>)

> Ansicht der Bauteilliste mit ausgefüllten Parametern

![Exercise](<../.gitbook/assets/00 (8).jpg>)

> Für jedes EFTE-Element sind jetzt die xyz-Koordinaten der adaptiven Punkte an seinen Ecken angegeben und können für die Fertigung der Elemente verwendet werden.
