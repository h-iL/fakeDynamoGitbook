# Veröffentlichen von Paketen

In den vorigen Abschnitten wurde gezeigt, wie das _MapToSurface_-Paket sich aus benutzerdefinierten Blöcken und Beispieldateien zusammensetzt. Aber wie veröffentlichen Sie ein Paket, das lokal entwickelt wurde? Diese Fallstudie zeigt, wie Sie ein Paket aus einer Gruppe Dateien in einem lokalen Ordner veröffentlichen können. !\[]\(images/11-4/Creating/Packages - 12.jpg) Es gibt viele Möglichkeiten zum Publizieren eines Pakets. Im Folgenden wird der von uns empfohlene Prozess beschrieben: **Sie veröffentlichen lokal, entwickeln lokal und veröffentlichen schließlich online.** Sie beginnen mit einem Ordner, der sämtliche Dateien im Paket enthält.

## Deinstallieren eines Pakets

Bevor Sie mit der Veröffentlichung des MapToSurface-Pakets beginnen, deinstallieren Sie das Paket aus der vorigen Lektion, falls Sie es installiert haben. Dadurch vermeiden Sie, mit identischen Paketen zu arbeiten.

!\[]\(images/11-4/Publishing/Packages - 01.jpg)

> Beginnen Sie, indem Sie _Pakete > Pakete verwalten_ wählen.

![](../.gitbook/assets/uninstall.jpg)

> Wählen Sie die Schaltfläche für _MapToSurface_ und wählen Sie _Deinstallieren_. Starten Sie dann Dynamo erneut. Wenn Sie beim erneuten Öffnen das Fenster _Pakete verwalten_ überprüfen, darf _MapToSurface_ dort nicht mehr vorhanden sein. Jetzt können Sie den Vorgang von Anfang an durchführen.

## Lokale Veröffentlichung von Paketen

_Anmerkung: Zu dem Zeitpunkt, als dieses Dokument verfasst wurde, war die Veröffentlichung von Dynamo-Paketen nur in Dynamo for Revit und Dynamo for Civil 3D aktiviert. Dynamo Sandbox verfügte nicht über Veröffentlichungsfunktionen._

> Laden Sie die zu dieser Übungslektion gehörigen Beispieldateien herunter (durch Rechtsklicken und Wahl der Option "Save Link As..."). Eine vollständige Liste der Beispieldateien finden Sie im Anhang. [MapToSurface.zip](https://github.com/h-iL/ForkedDynamoPrimerReorganized/blob/de/11\_Packages/datasets/11-4/MapToSurface.zip)

!\[]\(images/11-4/Publishing/Packages - 08.jpg)

> Sie übermitteln Ihr Paket zum ersten Mal und alle Beispieldateien und benutzerdefinierten Blöcke befinden sich im selben Ordner. Nachdem dieser Ordner vorbereitet ist, können Sie jetzt auf Dynamo Package Manager hochladen.

1. Der Ordner enthält fünf benutzerdefinierte Blöcke (.dyf).
2. Er enthält außerdem fünf Beispieldateien (.dyn) und eine importierte Vektordatei (.svg). Diese Dateien dienen als einführende Übungen, die dem Benutzer die Arbeit mit den benutzerdefinierten Blöcken erläutern sollen.

!\[]\(images/11-4/Publishing/Packages - 07.jpg)

> Klicken Sie in Dynamo zunächst auf _Pakete > Neues Paket veröffentlichen_.

!\[]\(images/11-4/Publishing/Packages - 03.jpg)

> In Fenster _Paket publizieren_ ist das relevante Formular im linken Bereich bereits ausgefüllt.

1. Durch Klicken auf _Datei hinzufügen_ wurden außerdem die Dateien aus der Ordnerstruktur rechts auf dem Bildschirm hinzugefügt. (Um andere Dateien als DYF-Dateien hinzuzufügen, ändern Sie den Dateityp im Browserfenster in **Alle Dateien (**_**.**_**)"**. Beachten Sie, dass sämtliche Dateien ohne Unterscheidung zwischen benutzerdefinierten Blöcken (.dyf) und Beispieldateien (.dyn) hinzugefügt wurden. Dynamo ordnet diese Objekte beim Veröffentlichen des Pakets in Kategorien ein.
2. Im Feld Gruppe wird definiert, in welcher Gruppe die benutzerdefinierten Blöcke in der Benutzeroberfläche von Dynamo abgelegt werden.
3. Veröffentlichen Sie das Paket, indem Sie auf Lokal publizieren klicken. Achten Sie darauf, auf _Lokal publizieren_ und **nicht** auf _Online publizieren_ zu klicken: Es sollen keine Duplikate im Package Manager erstellt werden.

!\[]\(images/11-4/Publishing/packages - ui.jpg)

> 1. Nach der Veröffentlichung werden die benutzerdefinierten Blöcke in der Gruppe DynamoPrimer oder in Ihrer Dynamo-Bibliothek angezeigt.

!\[]\(images/11-4/Publishing/Packages - 01.jpg)

> Sehen Sie jetzt im Stammverzeichnis nach, wie Dynamo das eben erstellte Paket formatiert hat. Klicken Sie dazu auf _Pakete > Pakete verwalten_.

!\[]\(images/11-4/Publishing/packages - showRoot.jpg)

> Klicken im Fenster zur Verwaltung von Paketen auf die drei senkrechten Punkte rechts neben _MapToSurface_ und wählen Sie _Stammverzeichnis anzeigen._

!\[]\(images/11-4/Publishing/Packages - 02.jpg)

> Das Stammverzeichnis befindet sich am lokalen Speicherort des Pakets (da Sie es lokal veröffentlicht haben). Dynamo greift derzeit zum Lesen benutzerdefinierter Blöcke auf diesen Ordner zu. Aus diesem Grund müssen Sie das Verzeichnis lokal an einem dauerhaften Speicherort ablegen (d. h. nicht auf Ihrem Desktop). Der Ordner mit dem Dynamo-Paket ist wie folgt gegliedert:

1. Im Ordner _bin_ befinden sich DLL-Dateien, die mit C#- oder Zero Touch-Bibliotheken erstellt wurden. Dieses Paket enthält keine solchen Dateien; dieser Ordner ist also in diesem Beispiel leer.
2. Im Ordner _dyf_ befinden sich die benutzerdefinierten Blöcke. Wenn Sie ihn öffnen, werden alle benutzerdefinierten Blöcke (DYF-Dateien) für das Paket angezeigt.
3. Im Ordner extra befinden sich alle zusätzlichen Dateien. Dies sind wahrscheinlich Dynamo-Dateien (.dyn) oder sonstige erforderliche Zusatzdateien (.svg, .xls, .jpeg, .sat usw.).
4. Die Datei pkg ist eine einfache Textdatei, die die Einstellungen des Pakets definiert. Diese Datei wird in Dynamo automatisch erstellt, Sie können Sie jedoch bearbeiten, wenn Sie detaillierte Einstellungen benötigen.

## Online-Veröffentlichung von Paketen

!\[]\(images/11-4/Publishing/Packages - 00.jpg)

> **Anmerkung: Führen Sie diesen Schritt bitte nicht aus, es sei denn, Sie möchten tatsächlich ein eigenes Paket veröffentlichen.**

1. Wenn das Paket zur Veröffentlichung bereit ist, wählen Sie im Fenster Pakete verwalten die Schaltfläche rechts von MapToSurface und wählen Sie _Veröffentlichen_.
2. Um ein bereits veröffentlichtes Paket zu aktualisieren, wählen Sie Version veröffentlichen. Dynamo aktualisiert dann Ihr Paket online mit den neuen Dateien im Stammverzeichnis des Pakets. Dieser einfache Schritt genügt.

## Version veröffentlichen

Wenn Sie die Dateien im Stammverzeichnis des veröffentlichten Pakets aktualisieren, können Sie über _Version veröffentlichen_ im Fenster _Pakete verwalten_ eine neue Version des Pakets veröffentlichen. Auf diese Weise können Sie nahtlos erforderliche Aktualisierungen Ihrer Inhalte vornehmen und sie für die Community bereitstellen. Die Funktion _Version veröffentlichen_ kann nur verwendet werden, wenn Sie der Verwalter des Pakets sind.
