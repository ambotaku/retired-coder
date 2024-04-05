+++
weight= 2
title = 'Was macht eigentlich ein Webserver ?'
date = 2024-04-05T13:11:17+02:00
draft = false
+++
## Rudimentäre Webserver

Ein Webserver muss mindestens eine Sache können:

- per [Transmission Control Protocol (TCP)](https://de.wikipedia.org/wiki/Transmission_Control_Protocol) einen Port öffnen 80 für das [Hypertext Transfer Protokoll HTTP](https://de.wikipedia.org/wiki/Hypertext_Transfer_Protocol)
- warten bis ein Paket ankommt, das eine Zeile enthält, die den Befehl GET gefolgt von einem [URL-Pfadnamen](https://de.wikipedia.org/wiki/Uniform_Resource_Locator) wie http://server.de/index.html enthält
- die angeforderte Datei in einem Dateisystem suchen
- ein Header-Päckchen schicken, welches mindestens die HTTP-Version und einen Status enthält (z.B. **HTTP/1.1 200 OK** wenn Datei gefunden wurde oder **HTTP/1.1 404 not found** wenn nicht)
- wenn Datei gefunden wurde, deren Inhalt in handlichen TCP Päckchen zum Absender des GET-Befehls schicken.
- die TCP Verbindung beenden

"Hauptamtliche" Webserver wie NGINX oder Apache erkennen noch Befehle wie HEAD, POST, PUT oder vielleicht sogar DELETE, aber um eine statische Webseite wie diese auf einem Browser darzustellen reicht GET völlig aus.

Wer einen Python-Interpreter auf seinem Rechner hat, kann mal in einem Verzeichnis, welches eine HTML Datei namens index.html enthält den folgenden Konsolen-Befehl eingeben:
{{< highlight bash >}}
$ python3 -m http.server
Serving HTTP on 0.0.0.0 port 8000 (http://0.0.0.0:8000/) ...
{{< /highlight >}}
Wenn man nun in einem Browser die angezeigte URL http://0.0.0.0:8000/ ins Suchfeld eingibt (ja - die IP4-Addresse 0.0.0.0 funktioniert tatsächlich), zeigt der Browser die Seite index.html korrekt an.

Gibt es für Python keine als HTML-Hauptseite erkennbare Datei, wird wie bei den meisten Servern das Inhaltverzeichnis angezeigt (bei produktiv genutzten Servern sollte man so ein Feature aus Sicherheitsgründen tunlichst abschalten).

Nutzt man diesen Befehl in einem HTLML-Wurzelverzeichnis */public*, das Hugo erstellt hat, wird die Seite sogar vollständig funktionieren, obwohl Pythons primitiver Webserver von  HTML, CSS, Javascript usw. überhaupt nichts versteht. Das ist ja auch nicht Sache eines Webservers, sondern eines Browsers.

Statt Python zu bemühen, wenn man schon Hugo hat, ist auch überflüssig, denn auch Hugo hat einen eingebauten Webserver. Der lädt dazu noch alle Seiten neu, die man bearbeitet hat. Diesen Server öffnet man aber im Projekt-Wurzelverzeichnis, weil er auf Änderungen im */content* Verzeichnis, also den Markdown-Texten achtet. Findet er dort Fehler, werden sie auch direkt im Webbrowser angezeigt - was sehr, sehr nützlich ist.

{{< highlight bash >}}
$ hugo server -D
Watching for changes in /home/kzerbe/projects/hugo/scratch/retired-coder/{archetypes,content,i18n,static,themes}
Watching for config changes in /home/kzerbe/projects/hugo/scratch/retired-coder/hugo.toml, /home/kzerbe/projects/hugo/scratch/retired-coder/themes/hugo-coder/config.toml
Start building sites …
hugo v0.124.1-db083b05f16c945fec04f745f0ca8640560cf1ec+extended linux/amd64 BuildDate=2024-03-20T11:40:10Z VendorInfo=gohugoio

                   | DE
-------------------+-----
  Pages            | 82
  Paginator pages  |  7
  Non-page files   |  0
  Static files     | 23
  Processed images |  0
  Aliases          | 28
  Cleaned          |  0

Built in 440 ms
Environment: "development"
Serving pages from disk
Running in Fast Render Mode. For full rebuilds on change: hugo server --disableFastRender
Web Server is available at http://localhost:1313/ (bind address 127.0.0.1)
Press Ctrl+C to stop
{{< /highlight >}}

Derart spezialisierte Test-Webserver findet man wohl in jedem modernen Web-Entwicklungs-System. Es geht aber noch primitiver - und das kann sogar recht nützlich sein.

# Webserver auf Kleinstrechnern

Ich habe es noch nicht getestet, aber eigentlich sollten sogar *Bastelrechner* wie [Raspberry Pi Zero 2 W](https://www.raspberrypi.com/products/raspberry-pi-zero-2-w/) sich als einfache Hugo Entwicklungsumgebung eignen - mit 2 Watt Stromverbrauch zum Preis von 15$ für diesen Computer, denn sogar darauf läuft ein aktuelles Debian-Linux (ist das nicht nachhaltig?).

Bei nur 512 MB Arbeitsspeicher sollte man auf eine graphische Bedienoberfläche besser verzichten, aber so etwas braucht weder **ein echter Server** noch ein **echter DevOp** (versteht ihr das nicht, Micro$oft ?). Das Aufbauen und Anzeigen von Webseiten macht jedenfalls der Browser und der läuft im Normalfall ja auf einem anderen Rechner als der Server. Da es aber MicroSD Speicherkarten inzwischen bis 1 TB Größe gibt, kann sogar ein **Raspberry Pi Zero** wohl bald eine gesamte Wikipedia an (statischen) Webseiten speichern.

![Pi Zero W](/images/pi_zero_w.jpg)

Dieser kleine Rechner hat sogar einen HDMI Anschluss, was aber
bei nur 512 MB Arbeitsspeicher auch mit Linux knapp ist.

## Aber es geht noch kleiner

Wie wär es denn mit Webservern auf einem Chip:

Wie oben beschrieben, braucht ein Webserver mindestens ein funktionierendes Dateisystem und einen kompletten TCP/IP Protokollstack. Damit sind zumindest 8-Bit Lösungen wie ein [Arduino UNO](https://store.arduino.cc/collections/boards-modules) raus - wären da nicht diese ESP32-Chips des chinesischen
Hersteller [Espressif](https://www.espressif.com/).

Das sind 32 Bit Microcontroller, die sich aber dem 8-Bit Controller [ATmega328](https://ww1.microchip.com/downloads/en/DeviceDoc/Atmel-7810-Automotive-Microcontrollers-ATmega328P_Datasheet.pdf) der populären, älteren Arduinos gegenüber als Modem mit serieller Schnittstelle ausgeben - mit den selben alten AT-Sequenzen wie Hayes Modems aus den späten 1980ern. Diese Chips realisieren auf
der anderen Seite aber diverse WLAN und Bluetooth Standards und machen so auch veraltete 8-Bit- Technik "smart"- wie dämlich auch immer die Grundfunktion eines Geräts bleibt. So kann man dann
Küchengeräte, Heizungen, Waagen, Lampen oder Steckdosenleisten via WLAN oder Bluetooth mit dem Smartphone steuern - über Webseiten, die ein Webserver in solch einem Chip aufbaut. Als Goodie liefert
man dann seine persönlichen Daten nach China, wo der Server des
Geräte-Herstellers steht - diese Chinesen sind wohl das wahrlich *smarte* an der Chose.

![ESP32 D1 mini](/images/D1_mini_ESP32_pinout.jpg)

Ich gehe hier nicht näher auf den Anschlußplan des ESP32 Boards
oben ein, das sollte aber klar machen, das so ein Ding mehr machen
kann als nebenbei noch einen simplen Webserver.

Inzwischen setzt Arduino selbst sogar 32-bittige ESP32 auf [eigenen Boards](https://docs.arduino.cc/hardware/nano-esp32/) ein.

Da die ESP32 Chips allein auch schon recht gut MicroPython können,
reicht ganz allein so ein Chip für einen Webserver schon aus, wenn der vorhandene Massenspeicher (Flashdrive) ausreicht. Die Daten sollten sich aber nicht häufig ändern, denn diese Chips halten nur ein paar tausend Schreibzyklen aus. Ansonsten nutzt man ihre bereits vorhandene SPI-Schnittstelle, um direkt eine SD-Karte anzusteuern.

Aber die Espressif-Chips haben inzwischen Konkurrenz von preiswerten Chips mit kleineren ARM-Prozessorkernen bekommen.
Den Durchbruch schaffte hier der [Raspberry Pi Pico W](https://www.raspberrypi.com/documentation/microcontrollers/raspberry-pi-pico.html), der den Pi Pico noch um eine WLAN-Schnittstelle erweitert und als Board-Kit um 7€ gehandelt wird.

![Pico-W Pinout](/images/picow-pinout.svg)
