+++
weight = 25
title = 'Chrome OS als Windows Alternative'
date = 2024-04-02T21:09:12+02:00
draft = false
+++
Im ersten Teil dieser kleinen Artikelreihe ([Verdongelung]({{< ref "verdongelung.md" >}}))
habe ich beschrieben, welche Motive mich zur weitest gehenden Loslösung
von Microsoft Windows- und Apple-Computern gebracht haben. ChromeOS und
das auf den meisten PCs installierbare ChromeOS Flex nutzen vorhandene
Leistung von Computern am effektivsten aus
und machen auch ältere oder sehr preiswerte Computer sicher und
brauchbar für Alltagsaufgaben. Hier zeige ich auch, wie ein Premium
Chromebook durchaus auch als Arbeitsgerät etwa für professionelle
Software-Entwicklung einsetzbar ist.

{{< notice info>}}
Diese Artikelserie entstand auf einem Acer Spin 713 teilweise auf einem
Clone meines DokuWiki-Servers und einem Apache2+PHP-LAMP-Server, der
auch auf dem Chromebook lief, wenn ich unterwegs mal keine Online
Verbindung hatte.
{{< /notice >}}

Wer heute einen Computer oder Mobilgerät kauft, erwartet darauf ein
vorinstalliertes Betriebssystem. Bei fast allen Desktop-Computern und
Notebooks ist das meist Windows 10 bzw. ab Oktober Windows 11 oder bei
Apple-Geräten macOS. Bei Tablets und Smartphones ist kommt meist Android
oder iOS für Apple Geräte zum Einsatz. Hierzulande noch wenig verbreitet
sind ChromeBooks mit dem Betriebssystem ChromeOS von Google, dieses hat
aber seit Februar 2021 immerhin eine größere Verbreitung als
macOS.
Besonders im
[Bildungsbereich](https://www.computerbase.de/2019-01/bildungsbereich-chromebooks-30-millionen/)
konnten ChromeBooks andere Computer aus den folgenden Gründen
verdrängen:

- Chromebooks sind ähnlich preiswert wie die hierfür angedachten
    Netbooks mit Windows-Betriebssystem, deren Leistung aber noch völlig
    unzureichend war, der Leistungshunger von Windows 10 machte auch
    Tablets und Convertibles mit Chromebook-ähnlicher Ausstattung
    faktisch unbrauchbar
- Chromebooks verursachen kaum Administrationsaufwand, aktualisieren
    sich im Hintergrund automatisch und sind durch Virtualisierung
    schwerer durch Schadsoftware angreifbar
- für Schulen und Bildungseinrichtungen gibt es für Computerlaien
    (Lehrer) sehr einfach bedienbare und auf Schulanforderungen
    zugeschnittene Administrationssoftware
- 
   es wird überwiegend Cloud-Software eingesetzt, das lokale
    Dateisystem spielt je nach Konfiguration kaum eine Rolle, die Geräte
    sind somit leicht austauschbar und nicht personalisiert

Waren bis vor einigen Jahren auf den Rechnern installierte Anwendungen -
deren Installation, Einrichtung und zentrale Administration gerade für
Bildungseinrichtungen ohne IT-Fachpersonal recht schwierig war - noch
alternativlos, haben sich inzwischen auf Cloud-Servern laufende
Web-Anwendungen für immer weitere Anwendungsbereiche etabliert. Gerade
weit verbreitete Software wie Microsoft Office, Grafikanwendungen von
Adobe und Autodesk und Streaming von Musik, Videos und sogar viel
Rechenleistung erfordernde Computerspiele können auch mit
leistungsschwachen Chromebooks genutzt werden (etwa per Google's Stadia
Dienst). Während Webanwendungen anfangs nicht offline nutzbar waren,
können moderne Single-Page Webanwendungen auch Dokumente lokal
speichern, um sich bei Netzverfügbarkeit automatisch zu
resynchronisieren.

Für einige Anwendungen und Arbeitsweisen gibt es aber auch Gründe die
gegen Einsatz eines Chromebooks sprechen, die ich hier zuerst nennen
möchte, damit Leser eher erkennen können, ob der ganze Artikel für sie
lesenswert ist.

## Mögliche Argumente gegen ChromeOS und ChromiumOS

### schlechte oder teure Netzanbindung

ChromeOS ist primär ein Frontend-Betriebssystem für Cloud-Anwendungen.
Auch wenn man inzwischen vieles auch Offline erledigen kann, benötigt
man - je nach Anwendung - erheblich viel Download-Volumen. Das gilt
inzwischen zwar auch - schon wegen immer größerer Updates - für Windows
und macOS, aber ChromeOS ist sicher das am ehesten Cloud-zentrische
Betriebssystem.

### Kosten für Cloud-Dienste

Auch darf der niedrige Preis für die Anschaffung eines Chromebooks und
viel kostenlose Software nicht darüber hinweg täuschen, dass einige
Dienste hohe laufende Kosten verursachen. Spieler brauchen wegen Stadia
vielleicht keine teuren Computer oder Grafikkarten, zahlen aber ca. 10€
monatlich nur fürs Streaming - die laufenden Kosten für Online-Spiele
kommen noch dazu.

### Mehr Werbung

Wie man es von den Bezahlschranken der Tageszeitungen kennt, hat man die
Wahl zwischen kostenloser oder preiswerter Cloud-Software oder
werbefreie Angebote gegen höhere Gebühren.

### Benutzerkonto bei Google

Wie inzwischen auch bei Apple und Microsoft benötigt man zur vollen
Nutzung der ChromeOS Anwendungen ein Google-Mail Konto verbunden mit der
Preisgabe persönlicher Daten - gegebenenfalls auch (freiwillig für
Google-Pay) mit Kontodaten. Für Chrome OS Flex gibt es alternative
Möglichkeiten und für ein "bisschen" Surfen geht vieles auch ohne
Account.

### Hardware Ausstattung

Es gibt noch ganz billige, veraltete Chromebooks so ab 200€, die nur 2
Gigabyte Arbeitsspeicher und 32 oder gar nur 16 GB lahmen eMMC Speicher
haben. Da funktionieren dann nur einfache Webseiten. Ein Chromebook
(oder ein alter Rechner für ChromiumOS) sollte schon mindestens 4GB
Arbeitsspeicher und mindestens 128GB SSD Festspeicher (oder Festplatte)
haben. Premium Chromebooks können auch 16GB Hauptspeicher haben und bis
1 TB Festspeicher erweitert werden. Ab 4GB können virtuelle Maschinen
für die Android und Debian-Linux Subsysteme laufen. Wer sehr viele
multimediale Linux-Anwendungen nutzen oder gar Software entwickeln will,
sollte besser ein Premium-Chromebook kaufen und ab 700€ für dessen
Anschaffung einplanen.

### große Unterschiede bei Verarbeitung

Chromebooks sind von sehr gut bis ganz miserabel verarbeitet und
ausgestattet. Während Premium-Chromebooks überwiegend stabile
Alu/Magnesium - Gehäuse und IPS-Displays mit mindestens Full HD
Auflösung, Speicherkarten-Slots und reichlich USB-Ports haben, gibt es
bei Einstiegs-Modellen ähnlich knarzende Dünnplastik-Konstruktionen und
weniger als 1024 x 768 Pixel Display-Auflösung wie seinerzeit bei
Netbooks. Bekannte Marken wie Acer, Asus, HP oder Lenovo haben aber nur
noch sehr gut verarbeitete Chromebooks im Programm.

### Leistungsverlust durch Virtualisierung

Zwar schützt die Virtualisierung der Android- und Linux- Subsysteme ein
Chromebook recht zuverlässig gegen Schadsoftware, kostet aber auch
Leistung und begrenzt gegenüber "echtem" Android oder Linux den Zugang
zu Hardware-Ressourcen, persönlichen Daten, USB-Anschlüssen und
Aufenthaltsort. Vieles lässt sich für ausgesuchte Anwendungen freigeben,
aber etwa Grafik-Beschleunigung, Drucker und Scanner mit USB-Anschluss
und alles, was spezielle Treiber braucht, bleibt außen vor.
Standard-Peripherie wie HIDs (Tastaturen, Mäuse und Gamecontroller) und
USB-Sticks funktionieren aber auch mit Android und Linux - wenn man
diese dafür frei schaltet.

### nicht alle Android- oder Linux- Anwendungen sind unter ChromeOS lauffähig

Wie oben bereits genannt, schränkt die Virtualisierung den Zugang zur
Hardware stark ein und kostet auch Performance. Das dient zwar auch der
Sicherheit, denn unsichere, fehlerhafte oder korrumpierte Treiber sind
ja etwa bei Windows eine Hauptproblemquelle. Dadurch können viele
Programme oder Apps nicht einfach vom Smartphone oder der gewohnten
Linux-Distribution auf ein Chromebook übertragen werden. Aber ich
verwende etwa gerade einen Apache2 Webserver samt PHP auf dem
Chromebook, um dieses Wiki auch offline bearbeiten zu können sowie
mehrere Entwicklungsumgebungen sowie ein lokales Git-Repository zur
Versionsverwaltung und Synchronisation all meiner Arbeit. Selbst
Software-Entwickler können also fast alle Arbeiten auch unterwegs mit
einem (Premium-) Chromebook wie meinem Acer Spin 713 machen - auch ohne
Cloud-Zugang.

### Betriebssystemwechsel bei Chromebooks schwierig

Google's offizieller Weg zu Linux auf Chromebooks ist die mit dem
Linux-Hypervisor KVM realisierte virtuelle Maschine *chrostini* mit den
oben beschriebenen Nachteilen. Da Chromebooks recht unterschiedliche
Hardware (sowohl Intel als auch ARM-Prozessoren mit 32- oder 64-Bit
Architektur) haben, ist die Auswahl eines für Dual-Boot geeigneten
Linux-Betriebssystems nicht immer möglich. Statt über *chrostini* kann
man eine *echte* Linux-Distribution mittels der Drittsoftware *crouton*
installieren - wenn die Hardware passt. Das ist aber mit *rooten*, also
Abschaltung aller Schutzmechanismen und Garantieverlust verbunden leider
eine Möglichkeit, ein sonst recht unverwüstliches Chromebook zu
*bricken* - also nicht mehr bootbar zu machen, denn das UEFI (BIOS)
eines Chromebooks hat faktisch keine Einstellmöglichkeiten und bootet
nur ChromeOS.

### Chromebook Kaltstart Mysterien

Überhaupt ist alles, was mit dem UEFI (BIOS) der Chromebooks zu tun hat
durch kryptische Tastenkombinationen (wie ESC-Refresh Powerschalter) und
allerlei Hindernisse (schlimmer als bei vielen Windows-Notebooks)
erschwert. Man sollte sich unbedingt einen Wiederherstellungs USB-Stick
erstellen, bevor man die Hardware - etwa auch Upgrade einer SSD -
antastet. Jeder Kaltstart über solch eine "geheime" Tastenkombination
löscht alle lokal abgespeicherten Daten - inklusive des gesamten
*crostini* Linux-Subsystems, dass man vorher unbedingt extern (USB oder
SD-Karte) speichern sollte. Das schützt bei Geräte-Diebstahl oder
Manipulation seitens Dritter vor Datenlecks, kann aber bei
Nachlässigkeit auch zu Datenverlust führen.

### ungewöhnliche Tastaturbelegung

Wie auch bei Apple-Tastaturen fehlen Chromebooks Tasten, die man von
PC-Tastaturen kennt, insbesondere Eing, Entf, Pos1, Ende, Bild\*,
Feststelltaste und alle Funktionstasten. Über nicht auf der Tastatur
aufgedruckte Kombinationen - etwa Alt-Backspace für Entf - erreicht man
zwar (fast) alle, aber es gibt sehr viele solcher Kombinationen, die man
erst mal in der Online-Doku suchen muss - aber das ist nur eine der
vielen Ähnlichkeiten zu Apple. Installiert man ChromeOS Flex auf einem
alten Notebook, ist die Beschriftung von dessen PC-Tastatur vollends
irreführend.

### Panels von Linux Desktops erscheinen nicht auf Linux Desktop

So genial es ist, graphische Linux-Anwendungen auf dem ChromeOS Desktops
zu sehen, werden Panels (Menüsysteme) von Linux auf einem Extra-
ChromeOS Desktop dargestellt, was verwirrend, aber prinzipiell auch
nicht zu ändern ist. Wenigstens erscheinen alle installierten
Linux-Anwendungen und Android Apps auf den ChromeOS Anwendungsmenüs. Für
den *lxpanel* des Linux LXDE-Desktops gibt es aber einen guten
[Kompromiss](https://linuxiumcomau.blogspot.com/2020/02/using-lxpanel-as-ui-for-crostini.html),
den ich auch deshalb nutze, weil *lxde-core* ein sehr schlanker
Linux-Desktop ohne Doppelinstallation von in ChromiumOS bereits
vorhandenen Anwendungen ist.

## Chromebooks - so schön und Anwender-freundlich wie Apple früher mal war

Gratulation an alle, die bis hier gelesen haben !

Für wen keine der oben genannten Einschränkungen ein No-Go ist, der kann
jetzt die Pluspunkte von Chromebooks und ChromeOS (-Flex) erfahren.
Chromebooks sind einfach einfach. Hat man gar schon einen Google-Mail
Account, nutzt Chrome oder Chromium, speichert schon
Rechner-übergreifend Browser-Einstellungen, Lesezeichen, und Passworte
ab und nutzt bereits Android Apps, ist man mit dem ersten Einschalten
schon fast fertig mit Installation und Konfiguration:

1. Chromebook erstmalig einschalten
2. optional noch Sprache ändern
3. WLAN Verbindung auswählen
4. mit Googlemail Account anmelden
5. Updates abwarten
6. optional noch Datensicherheits- Einstellungen ändern
7. optional mit vorhandenem Android Smartphone verbinden
8. optional Android Apps auswählen, die man bereits auf dem Handy hat
    und nun auch auf dem Chromebook nutzen möchte
    optional "Entwickler"-Modus einschalten, wenn man auch Linux
    Anwendungen installieren möchte
9. FERTIG klicken und zuschauen, wie sich das Menüsystem mit den
    ausgewählten Anwendungen füllt
10. anfangen mit dem System zu arbeiten

Das war's dann auch mit Administration, viel Einzustellen gibt es auch
nicht - vielleicht noch die wichtigsten Apps und Links auf die Taskbar
ziehen, aktualisieren aller Apps und des Systems geschieht automatisch
im Hintergrund, Neustarts sind dabei sehr selten nötig. Man schaltet
nichts ab, klappt nach der Arbeit das Chromebook zu und klappt es zum
Weiterarbeiten wieder auf, um sofort da weiter zu machen, wo man
aufgehört hat. Über wichtige Ereignisse oder rein kommende Mails - auch
vom per WLAN oder Bluetooth verbundenen Handy informieren kleine Popups,
geht mal was schief, solche in roter Schrift mit Links zur möglichen
Fehlerbehebung. Keine Bluescreens, keine unverständlichen 0xDEADBEEF-
Fehlermeldungen und Belehrungen, was man falsch gemacht hat - ohne
Hinweis, wie denn es richtig geht. Kurzum - das richtige System für Oma
& Opa und die Enkel, die nicht ständig Hilfs-Admins sein wollen. Nehmt
dem Opa seinen schrottigen Windows PC weg und schenkt ihm ein
Chromebook - das schont Eure und auch seine Freizeit und Nerven.

Manche der oben aufgeführten Nachteile und Einschränkungen sind
Nebeneffekte eines sehr resilienten Systems. Deshalb konnte sich
ChromeOS wohl auch so gut an Schulen durchsetzen, denn auch Lehrer haben
mit den Schüler-Geräten keinen Stress mehr oder werden mit technischen
Details überfordert, wenn ein Schüler mal "Hacker" gespielt hat und mit
einem Chromebook komische Sachen macht. Mit dem Chrome Remote-Desktop
trennt ihn der Lehrer vom Schulnetz und stößt schlimmstenfalls die
Systemwiederherstellung an. Nach einem Neustart ist alles wieder wie
neu.

Wie beim macOS sind die "gefährlichen" Sachen - etwa die *Shell*
(Befehlszeilen-Interpreter) tief unter der Motorhaube versteckt. Die
ganz gefährlichen, die eigentliche Installation bzw. das Host-Linux
betreffenden Befehle erzwingen eine komplette Systemwiederherstellung -
ein Durchschnitts-Hacker kommt also nicht an die lokalen Daten, weil
diese gelöscht werden, bevor er ein Chromebook überhaupt "rooten" kann -
und dabei komplett neu aufsetzen muss - weil nichts mehr da ist. Das ist
sicher lästig, aber macht Unbefugten den Datenklau schwer.

Ohne den zum Gerät passenden Wiederherstellungs - USB-Stick kommt man
also überhaupt nicht weiter. Diesen sollte man für Notfälle also
vorsorglich (über eine Chrome-Browser-Erweiterung) erstellen und gut
aufheben - besonders wenn man an Chromebooks herum basteln will. Ein
normaler Anwender kommt mit all dem aber ohnehin nicht in Berührung und
kann auch mit maroden Linux- oder Android- Anwendungen kaum Schaden
anrichten. Die "Lock" Taste rechts auf der Funktionstasten-Leiste
beendet auch bei "eingefrorenen" Fullscreen-Anwendungen die Sitzung und
man landet sofort auf dem Anmelde-Bildschirm, weil dabei auch die
korrumpierten virtuellen Subsysteme (VMs) terminiert wurden und beim
Anmelden neu gestartet werden. Der stabile Zustand von ChromeOS - Host
wird auch durch einen schweren Fehler in einem Subsystem nicht
korrumpiert.

## ChromeOS Flex vs. ChromeOS

Der chinesische ChromeOS-Fork FydeOS sieht
leider noch ziemlich nach Baustelle aus. Priorität hat da wohl erst mal
die Übersetzung ins chinesische für den chinesischen Markt. Die
verzweifelte US-Sanktionierungspolitik beschert und aber wohl bald mehr
OpenSource-basierte Computer.

Bisher war hauptsächlich vom proprietären Google ChromeOS die Rede,
welches nur auf Chromebook- oder Chromebox- genannten Rechnern läuft und
auch Android Apps aus Googles Playstore ausführen kann. ChromeOS Flex
erreicht nur Google's Webstore oder "freie" Stores, die Web-Anwendungen
ausbreiten und natürlich alle im Web zugänglichen Webseiten und
Dienste - so wie jeder aktuelle Browser. Darüber hinaus ist aber auch
bei ChromeOS Flex eine virtuelle Maschine mit einer Debian GNU Linux
Distribution vorhanden (wenn der Rechner mindestens 4GB Arbeitsspeicher
hat), womit man per APT-Tool auch die riesige Welt der Debian-Linux
Distribution nutzen kann.

So konnte ich recht umfangreiche *chrostini*- Linux-VMs vom Chromebook
auch auf ein einfaches, für Windows 10 sehr schwaches
Einsteiger-Notebook (Pentium Silver 5000, 4GB Ram, 256GB SSD) kopieren
und der Linux LXDE-Desktop mit aller installierten Linux-Software lief
ohne Einschränkungen auf Anhieb. Die Linux-Images können sehr kompakt
sein, weil für Debian-Pakete wohl nur Links abgespeichert werden, die
dann vom Paketmanager geladen und installiert werden. Das erleichtert
auch den Wechsel zwischen verschiedenen Images oder eine Neuinstallation
eines Images, dessen VM instabil oder korrumpiert wurde.

Etwas lästig mag erscheinen, dass man sowohl bei ChromeOS als auch
ChromeOS Flex bei Änderungen der Installation alle lokalen Daten verliert,
die man nicht extern gesichert hat. Das gilt besonders für Linux-Images.
Schaltet man die Linux-Option ab oder lädt ein anderes Linux-Image, sind
alle Daten und Einstellungen, die im Vorgänger-Image angelegt wurden
weg. Hier ist es - wie bei Linux oft üblich - eigene Daten außerhalb der
Linux Installation in für Linux frei gegebenen Verzeichnissen
abzulegen - dann reicht auch schon ein kleinerer Bereich für die Linux
VM und die Linux-Images sind auch kleiner und schneller
wiederhergestellt.

Für so gesicherte Daten kann natürlich auch das Google-Drive oder ein
anderer Cloud Store wie Microsoft's One Drive für Backups verwendet
werden. Besonders mit ChromiumOS kann man so auch von Google relativ
unabhängig bleiben.

Was manche vielleicht auch bei ChromiumOS stört, ist die schlechte
Unterstützung für Dual-Boot Installationen. Wie die Chrome-Installation
überschreibt auch die Chromium-Installation die komplette primäre
Festplatte. Dort werden von ChromeOs und ChromiumOs - wegen der
Subsysteme bzw. VMs so viele Partitionen angelegt, dass die meisten
anderen Betriebssysteme damit wohl ein Problem bekämen. Dafür bleibt das
System einfach und der Anwender braucht über Partitionen nichts zu
wissen. Bei Chromebooks kann man das als gegeben hinnehmen, bei
Windows-Notebooks oder macBooks ist der Verzicht auf die Nutzung der
originalen Software aber sicher schwerer zu akzeptieren - höchstens bei
Altgeräten, die sonst Elektroschrott wären, weil keine sicheren Updates
mehr erhältlich sind. Mit der Community-Lösung
[crouton](https://github.com/dnschneid/crouton) lässt sich zwar auch ein
Dual-Boot mit nativ laufenden Linux-Distributionen realisieren, aber
dazu muss der unsichere Developer-Mode von ChromeOs aktiviert werden.
Dieses "rooten" löscht wiederum auch eine zuvor genutzte ChromeOS
Installation vollständig.

Da durch die Konflikte zwischen USA und China Android und Windows vom
größten IT-Markt der Welt (China) verschwinden, setzt China ja stark auf
eigene Linux und ChromiumOS-Varianten. Kaum jemand im Westen kennt etwa
FydeOS, eine chinesische Variante des freien ChromiumOS, das vielleicht
auch bald auf in China produzierten Tablets oder "Chromebooks" auch
hierzulande auftaucht - so wie das Linux HarmonyOS bei Huawei Geräten.

## Fazit

Nicht sehr Computer-affine Anwender finden sich in ChromeOS sehr gut
zurecht - grundlegende Browser-Kenntnisse reichen völlig aus. Sie müssen
aber auf eventuell zuvor verwendete macOS- oder Windows-Software
verzichten, wenn es für diese keine Cloud- oder
Android-Implementierungen gibt und sie mit den Einschränkungen gegenüber
den Desktop-Versionen auskommen können. Recht populär sind hier
natürlich Microsoft's Office 365 Cloud- und Android Varianten und Adobes
Lightroom Photosoftware.

Von der Masse der Android Apps funktionieren nicht viele wirklich
vollständig und performant unter ChromeOS, weil Android wie Linux nur in
einer restriktiv gehandhabten virtuellen Maschine läuft.

Wer mit "echten" Linux-Distributionen und ihren zwar aufwändigen aber
auch oft unübersichtlichen Desktops nicht zurecht kommt, dem bieten
ChromeOS und ChromiumOS vereinfachte, aber auch wegen der virtuellen
Maschine *chrostini* eingeschränkte Alternative, die Linux-Anwendungen
auch ohne viel Linux Kenntnisse zugänglicher macht.

Aber auch Linux Profis können von den ausgefeilten
Sicherheitsmechanismen und den recht geringen Hardware-Anforderungen für
des ebenfalls Linux-basierten Chromium-Hosts bzw. -Hypervisors
profitieren. Aber hier operiert man dann wirklich ohne Netz und
doppelten Boden und eine Gewährleistung seitens Hersteller von Rechner
und Betriebssystem. Solange man aber das UEFI nicht verändert, kommt man
per Hardboot und Wiederherstellungs- USB-Stick stets wieder zu einem
"sauberen" ChromeOS.
