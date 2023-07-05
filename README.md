Repo: MAS\_IIoT\_ShowCase\_ESP32\_AIoTK

Einführung

Dieses Repo enthält den Azure FreeRTOS middleware und sample Code für die Verbindung eines ESPRESSIF ESP32-Azure IoT Kit mit IoT Central.

Der Code ist bereits mit den WiFi Login-Daten sowie den Azure-Device Daten für den MAS ShowCase konfiguriert (s. Auszug Menükonfiguration unter `Build und Test` weiter unten). 

Die Übermittlung der Telemetriedaten von verschiedenen Sensoren am ESP32 und die Anzeige dieser Daten (Temperatur, Helligkeit, Feuchtigkeit, Druck, Bewegung) in IoT Central kann hiermit demonstriert werden.

Erste Schritte

Für eine neue Anwendung:	

Projekt-Ordner für Repo anlegen (am besten direkt auf C:/), dann in ESP-IDF PowerShell dort hin navigieren (Hinweise zur Installation unter `Build und Test` weiter unten) und Repo klonen: 

*cd C:\<Projekt-Ordner>*

*git clone --recursive https://github.com/Azure-Samples/iot-middleware-freertos-samples*

Zu Ordner des Demo-Projekts navigieren:

*C:\<Projekt-Ordner>\iot-middleware-freertos-samples\demos\projects\ESPRESSIF\aziotkit*

Über den Befehl *idf.py menuconfig* zunächst die Einstellungen für den zu nutzenden Wifi-Zugang und das in IoTC angelegte Azure-Device (Details zu Menükonfiguration unter `Build und Test` weiter unten) modifizieren und speichern.

Extra Build-Ordner im Projektordner anlegen, da die ESP-IDF ein Problem mit langen Build-Pfaden hat, und folgende Befehle ausführen: 

*idf.py --no-ccache -B "C:\<Projekt-Ordner>\<Build-Ordner>" build*

ESP32-Azure IoT Kit über Micro USB Port an PC anschließen und COM Port über Geräte-Manager ermitteln.

*idf.py --no-ccache -B "C:\<Projekt-Ordner>\<Build-Ordner>" -p <Your-COM-port> flash*

*idf.py -B "C:\<Projekt-Ordner>\<Build-Ordner>" -p <Your-COM-port> monitor*

Die Telemetriedaten der Sensoren am ESP32-Modul werden nun in Azure IoT Central in der Geräte-Overview angezeigt.

Build und Test

Folgende Anleitung von Microsoft wurde für die Erstellung des ShowCase herangezogen:

[**https://docs.microsoft.com/en-us/azure/iot-develop/quickstart-devkit-espressif-esp32-freertos**](https://docs.microsoft.com/en-us/azure/iot-develop/quickstart-devkit-espressif-esp32-freertos)

Für die Bearbeitung des sample Codes wird das Entwicklungs-Framework ESP-IDF verwendet. 

Über folgenden [ESP-IDF Tool Installer](https://dl.espressif.com/dl/esp-idf-tools-setup-2.3.exe) kann das Framework installiert werden. 

Eine lauffähige und fehlerfreie Version ist die v4.4.x (release version).

Über die Eingabe *idf.py menuconfig* in der ESP-IDF PowerShell öffnet sich das Konfigurations-Menü,

dort sind folgende Eingaben notwendig:

1. Wifi SSID und Passwort des für das ESP32-Modul bereitgestellten WLAN-Zugangs

![Ein Bild, das Text, Software, Webseite, Screenshot enthält.

Automatisch generierte Beschreibung](Aspose.Words.e1eb0883-57e7-4a56-934a-dc451c859a43.001.png)

1. Azure-Device Daten (primary key, ID scope, Device ID)

![Ein Bild, das Text, Schrift, Software, Screenshot enthält.

Automatisch generierte Beschreibung](Aspose.Words.e1eb0883-57e7-4a56-934a-dc451c859a43.002.png)

1. TLS-Server Einstellungen (bei Fehlermeldung zu peer-certificate validation im *idf.py … monitor* Befehl, was aufgrund eines veralteten Azure root-certificate im sample Code der Fall sein kann)

![Ein Bild, das Text, Software, Screenshot, Webseite enthält.

Automatisch generierte Beschreibung](Aspose.Words.e1eb0883-57e7-4a56-934a-dc451c859a43.003.png)








