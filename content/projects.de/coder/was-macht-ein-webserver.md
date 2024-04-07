+++
weight= 2
title = 'Was macht eigentlich ein Webserver ?'
date = 2024-04-05T13:11:17+02:00
draft = false
+++
## Rudimentäre Webserver

Ein Webserver muss mindestens eine Sache können:

1. per [Transmission Control Protocol (TCP)](https://de.wikipedia.org/wiki/Transmission_Control_Protocol)
 einen Port öffnen 80 für
das [Hypertext Transfer Protokoll HTTP](https://de.wikipedia.org/wiki/Hypertext_Transfer_Protocol)
2. warten bis ein Paket ankommt, das eine Zeile enthält, die den Befehl GET gefolgt
von einem [URL-Pfadnamen](https://de.wikipedia.org/wiki/Uniform_Resource_Locator)
 wie <http://server.de/index.html> enthält
3. die so angeforderte Datei in einem Dateisystem suchen
4. ein Header-Päckchen schicken, welches mindestens die HTTP-Version und einen Status
enthält (z.B. **HTTP/1.1 200 OK** wenn Datei gefunden wurde oder **HTTP/1.1 404
 not found**
 wenn nicht).
Wichtig für den Browser sind noch der Content-Type (MIME)und Content-Size (Byte-Anzahl),
 damit der Browser weiß, welche und wie viele Bytes vom Server kommen
5. wenn Datei gefunden wurde, deren Inhalt in handlichen TCP Päckchen zum Absender
 des GET-Befehls
schicken.
6. die TCP Verbindung beenden

"Richtige" Webserver wie NGINX oder Apache erkennen noch Befehle wie HEAD, POST,
 PUT oder vielleicht sogar DELETE, aber um eine statische Webseite wie diese auf
 einem Browser darzustellen, reicht GET völlig aus. Webserver im Internet sollten
  auch mehrere Anfragen
zur gleichen Zeit ausführen können, also einen weiteren Prozess oder Thread
 beginnen, der bei Punkt 2 (listen) neu anfängt.

Wer einen Python-Interpreter auf seinem Rechner hat, kann mal in einem
Verzeichnis, welches eine HTML Datei namens index.html enthält den folgenden
Konsolen-Befehl eingeben:
{{< highlight bash >}}
$ python3 -m http.server
Serving HTTP on 0.0.0.0 port 8000 [](http://0.0.0.0:8000/) ...
{{< /highlight >}}
Wenn man nun in einem Browser die angezeigte URL ins Suchfeld eingibt (ja -
die IP4-Addresse 0.0.0.0 funktioniert tatsächlich),
zeigt der Browser die Seite index.html korrekt an.

Gibt es für Python keine als HTML-Hauptseite erkennbare Datei, wird wie bei den
 meisten Servern das Inhaltverzeichnis angezeigt (bei produktiv genutzten Servern
  sollte man so ein Feature aus Sicherheitsgründen abschalten).

Nutzt man diesen Befehl in einem von Hugo erstelltem HTLML-Wurzelverzeichnis
 */public*, wird der gesamte Webauftritt sogar funktionieren, obwohl Pythons
 primitiver Webserver von  HTML, CSS, Javascript usw. überhaupt nichts versteht.
  Das ist ja auch nicht Sache eines Webservers, sondern eines Browsers.

Statt Python zu bemühen, wenn man schon Hugo hat ist auch überflüssig, denn
 auch Hugo hat einen eingebauten Webserver. Der lädt dazu noch alle Seiten neu,
  die man bearbeitet hat. Diesen Server öffnet man aber im Projekt-
  Wurzelverzeichnis, weil er auf Änderungen im */content* Verzeichnis,
  also den Markdown-Texten achtet. Findet er dort Fehler, werden sie auch
   direkt im Webbrowser angezeigt - was sehr, sehr nützlich ist.

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
Web Server is available at <http://localhost:1313/> (bind address 127.0.0.1)
Press Ctrl+C to stope
{{< /highlight >}}

Die in der Befehlszeile angegebene Option D rendert auch "Draft"-
Texte, die noch nicht zur Veröffentlichung freigegeben sind.
Das ist während der Arbeit an neuen Texten sehr nützlich. Derart spezialisierte
 Test-Webserver findet man wohl in jedem modernen Web-Entwicklungs-System.

## Webserver auf Kleinstrechnern

Ich habe es noch nicht ausprobiert, aber eigentlich sollten sogar *Bastelrechner*
 wie [Raspberry Pi Zero 2 W](https://www.raspberrypi.com/products/raspberry-pi-zero-2-w/)
  sich als einfache Hugo Entwicklungsumgebung eignen - mit 2 Watt Stromverbrauch
   zum Preis von 15$ für diesen Computer - denn sogar darauf läuft schon ein
    aktuelles Debian-Linux (ist das nicht nachhaltig?). Das reicht
sogar schon für einen Apache-Webserver mit Modulen wie der Programmiersprache
 PHP - also einen sogenannten LAMP-Server (Linux + Apache-Webserver + MySQL-
 Datenbank + PHP).

Bei nur 512 MB Arbeitsspeicher sollte man auf eine graphische Bedienoberfläche
 besser verzichten, aber so etwas braucht weder **ein echter Server** noch ein
  **echter DevOp** (versteht ihr das nicht, Micro$oft ?). Das Aufbauen und
   Anzeigen von Webseiten macht jedenfalls der Browser und der läuft im
   Normalfall ja auf einem anderen Rechner als der Server. Da es aber MicroSD
   Speicherkarten inzwischen bis 1 TB Größe gibt, kann sogar ein
   **Raspberry Pi Zero** wohl bald eine gesamte Wikipedia an (statischen)
   Webseiten speichern.

![Pi Zero W](/images/pi_zero_w.jpg)

Dieser kleine Rechner hat sogar einen HDMI Anschluss, was aber
bei nur 512 MB Arbeitsspeicher auch mit Linux knapp ist. Spätestens einen der
*großen* Browser wie Firefox oder Chrome sollte man auf so einem Ding weg lassen.

## Aber es geht noch kleiner

Wie wär es denn mit Webservern auf einem Chip ?

Wie oben beschrieben, braucht ein Webserver mindestens ein funktionierendes
 Dateisystem und einen kompletten TCP/IP Protokollstack. Damit sind zumindest
  8-Bit Lösungen wie ein [Arduino UNO](https://store.arduino.cc/collections/boards-modules)
   raus - wären da nicht diese ESP32-Chips des chinesischen
Hersteller [Espressif](https://www.espressif.com/).

{{< notice info >}}
Gemini behauptet:

- Minimaler Stack: Ein TCP/IP-Stack mit grundlegenden Funktionen wie DHCP-Client
 und Ping kann mit 32 KB RAM auskommen.
- Erweiterter Stack: Erweiterte Stacks mit Funktionen wie Firewall, NAT, VPN und
 komplexeren Protokollen benötigen bis zu 96 KB RAM.

Da ist aber noch nicht der Speicher berücksichtigt, der für Puffer
etc. benötigt wird.
{{< /notice >}}

Die Espressif Chips ESP8266 und ESP32 sind 32 Bit Microcontroller, die sich dem
 8-Bit Controller [ATmega328](https://ww1.microchip.com/downloads/en/DeviceDoc/Atmel-7810-Automotive-Microcontrollers-ATmega328P_Datasheet.pdf)
  der populären, älteren Arduinos gegenüber als Modem mit serieller Schnittstelle
   ausgeben - mit den selben alten AT-Sequenzen wie Hayes Modems aus den späten
    1980ern. Diese Chips implementieren auf Ihrer Seite aber diverse WLAN und
     Bluetooth Standards und machen so auch veraltete 8-Bit- Technik "smart"-
      wie dämlich auch immer die Grundfunktion eines Geräts bleibt. Damit kann
       man dann Küchengeräte, Heizungen, Waagen, Lampen oder Steckdosenleisten
        via WLAN oder Bluetooth über einen Web-Browser steuern - über
         Webseiten, die ein Webserver aus solch einem Chip ausliefert.
Als Goodie (für den Hersteller solcher Geräte) liefert man dann seine persönlichen
 Daten nach China, wo der Server des
Herstellers steht - diese Chinesen sind wohl das wahrlich *smarte* an der Chose.

![ESP32 D1 mini](/images/D1_mini_ESP32_pinout.jpg)

Ich gehe hier nicht näher auf den Anschlussplan des ESP32 Boards
oben ein, das sollte aber klar machen, das so ein Ding mehr machen
kann als nebenbei noch einen simplen Webserver.

Inzwischen setzt auch Arduino selbst 32-bittige ESP32 auf
 [eigenen Boards](https://docs.arduino.cc/hardware/nano-esp32/) ein.

 Die Espressif-Chips haben inzwischen Konkurrenz von preiswerten Chips mit
 kleineren ARM-Prozessorkernen bekommen.
Dazu gehört der [Raspberry Pi Pico W](https://www.raspberrypi.com/documentation/microcontrollers/raspberry-pi-pico.html),
 der den Pi Pico noch um ein WLAN erweitert und als Board-Kit in Preisen um 7€
  gehandelt wird.

  ![Pico-W Pinout](/images/picow-pinout.svg)

Da ESP32 und Raspberry Pi Pico W Chips allein auch schon recht gut
 [MicroPython](https://micropython.org/) können,
reicht ganz allein solch ein Chip für einen Webserver schon aus, wenn der
 vorhandene Massenspeicher (Flashdrive) ausreicht. Die Daten sollten sich aber
  nicht zu häufig ändern, denn diese Chips halten nur einige tausend
   Schreibzyklen aus. Ansonsten nutzt man eine ihrer beim ESP32 doppelt
vorhandenen [SPI-Schnittstellen](https://de.wikipedia.org/wiki/Serial_Peripheral_Interface)
 (im Bild oben orange markiert), um direkt eine SD-Karte anzusteuern.

Manch ein Webserver soll auch keine langen Texte ausgeben, sondern nur kleine Dialoge,
mit denen man Hardware-Einstellungen vornimmt. Ihr kennt das vielleicht von Eurem
Internet-Router oder anderer vernetzter Hardware.

Mit Micropython lassen sich solch einfachen Webserver mit wenig Code erreichen, wie
dies kleine [Github-Projekt](https://github.com/troublegum/micropyserver) mit
einem ESP8266 zeigt.

Ich verwende auch einen WLAN Router, der nur aus einem ESP32 Chip besteht, der
über [dies Projekt](https://github.com/martin-ger/esp32_nat_router) konfiguriert
 wird:

![nat-router](/images/nat_router.jpg)

Über den Webserver dieses Routers wird der folgenden Dialog gesendet, dem man
den WLAN-Zugang zu diesem Router (Access Point Settings) und den WLAN-Zugang
des Routers einträgt, welcher die Verbindung zum Internet herstellt, wobei noch eine
feste IP-Adresse möglich ist, falls für diese Verbindung kein DHCP verwendet
werden soll. Über einen Reboot-Button lässt sich der Router neu starten.
Diese Anwendung wurde allerdings in C geschrieben.

![ESP32_NAT.png](/images/ESP32_NAT.png)

## Wie kann man Dateneingaben zurück an den Webserver schicken ?

Seitengeneratoren wie Hugo sind für statische Webseiten ausgelegt
und die werden vom Server nur ausgeliefert und der Server braucht
keine Methode, um in Formulare von Seiten eingegebene Daten anzunehmen.

Mit dem Html ```<form>``` Tag umgebene Textteile des Markdown werden bei
der Seitengenerierung deshalb sogar ausgelassen. Ohne händisch erstellten
 HTML-Code geht da nichts und der Server braucht auch Code, um in einem
 zusätzlichem Request per GET oder POST Formulardaten anzunehmen.

Hugo's Markdown kann aber mittels Shortcodes erweitert werden, die
wiederum HTML enthalten können:

{{< highlight html >}}
<form accept-charset="UTF-8" action="???" method="GET">
    <input type="email" name="email" placeholder="Ihre Email">
    <input type="text" name="name" placeholder="Ihr Name">
    <input type="text" name="message" placeholder="Wie kann ich Ihnen helfen">
    <button type="submit">Send</button>
</form>
{{< /highlight >}}

Wird solch ein Formular im Hugo Projektverzeichnis ```/layout/shortcodes/contact.html```
abgelegt, kann es mit dem Shortcode ```contact``` im Markdown eingebaut werden.

Aber wo geht dann die ```action``` hin? Statt der drei Fragezeichen sollte
dort als *Endpoint* eine Serveradresse stehen, welche diese Daten verarbeiten kann.
Als *method* könnte auch ```POST``` verwendet werden, wenn da ein Server ist,
der Posts annehmen kann.
