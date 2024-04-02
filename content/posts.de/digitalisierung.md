+++
weight = 30
title = 'Was bedeutet "Digitalisierung" ?'
date = 2024-04-01T18:49:18+02:00
draft = false
+++
# Was bedeutet Digitalisierung ?

Ein Bingo-Buzzword des Jahres ist *Digitalisierung*. Vor allem Politiker
und Journalisten täuschen damit gerne Halbwissen vor, um die Wichtigkeit
dieser Thematik zu unterstreichen, scheinen davon aber nicht mehr zu
wissen als Helmut Kohl schon vor Jahrzehnten von seiner "Datenautobahn".

## Grundlegende Schichten

Was erfordert Digitalisierung denn eigentlich ?

1.  Erfassen von Messwerten und Einstellen anderer Werte (Sensoren und
    Aktoren)
2.  Kodieren solcher Werte in sehr klar definierten, standardisierten
    Datenformaten (Datenstukturen und Codecs)
3.  Sammeln, Übertragen und Synchronisieren dieser Daten in Datenbanken
    (Protokolle, Telemetrie)
4.  Verknüpfen und Verarbeiten von Daten aus den Datenbanken
    (Algorithmen, Anwendungen)
5.  Benutzerschnittstellen (Softwarenutzung, Konfiguration, Alarme,
    Statusberichte etc.)

Der momentan kritischste und oft noch unzureichende Teilbereich sind die
Telemetrie und die dafür verwendeten Protokolle. Sie machen die
Interoperabilität der vielen Bestandteile einer Vernetzung von Geräten
in einem globalen "Internet" erst aus.

Verbindungen müssen zuverlässig, sicher und über viele Verbindungsarten
möglich sein, wegen der daraus entstehenden Komplexität werden Aufgaben
in klar voneinander getrennten Schichten bzw. "Protokoll-Ebenen"
aufgeteilt, die das
[OSI-Modell](https://de.wikipedia.org/wiki/:de:OSI-Modell) abstrakt
definiert:

1.  Bitübertragungsschicht: realisiert ein Übertragungsmedium wie Kabel,
    Glasfaser, DSL- oder Vectoring- Anschluß, Bluetooth, WLAN oder
    Mobilfunk
2.  Sicherungsschicht: verpackt und transportiert zuverlässig
    (Prüfsummen) Frames genannte aber noch nicht Anwendungs-bezogene
    Datenpakete
3.  Vermittlungsschicht: stellt Verbindungen im Netz her (physikalisches
    Routing, Leitungsreservierung), z.B. durch Switches
4.  Transportschicht: unterhält Verbindungen auf logischer Ebene
    (Protokoll-basiertes Routing wie TCP, UDP etc.)
5.  Sitzungschicht: stellt für eine Anwendungssitzung eine stabile
    Verbindung her (Telefonanruf, App-Nutzung)
6.  Darstellungsschicht: Übertragung auf "logischer" Ebene, also in für
    bestimmte Anwendungen relevanten Datenformaten wie HTML-Seiten,
    Bildformaten, Video-Codecs, VOIP-Paketen beim Mobilfunk,
    Fernsehprogramme oder Telemetrie-Daten von Fahrzeugen und Fluggeräten
7.  Anwendungsschicht: Anwendungen wie Browser, Mailprogramme, Messenger
    usw.

Man kann sich leicht vorstellen, dass der Anspruch, zukünftig fast alle
mit dem "Internet" vernetzen zu wollen recht kompliziert wird, wenn das
alles zusammen passen soll. Von verschiedenen Umsetzungen des
ISO-Modells hat sich aber letztlich der Internet-Protokollstapel
(IP-Stack) durchgesetzt, aber für jede Schicht gibt es natürlich eine
ständig wachsende Zahl von Implementierungen.

Stabiler Bezugspunkt sind beim "Internet" besonders Schicht 3
(Internetprotokoll IP) und eine Reihe populärer Protokolle - wie vor
allem TCP und UDP - auf Schicht 4.

Auf Schicht 2 ist das LAN-Protokoll Ethernet Grundlage der meisten
Verbindungsarten - auch bei Funkprotokollen wie dem WLAN oder
DSL-Festnetz. Die darunter liegende physikalische Schicht 1 kann nun
sehr unterschiedlich funktionieren, aber der IP-Stack stellt eine
zuverlässige Kommunikation bis Schicht 4 für alle mit dem IP-Stack
aufgebauten Kommunikationsverbindungen her.

Ab Schicht 5 (Sitzungsschicht) wird es sehr individuell. Für einen
Web-Browser (Schicht 7) braucht es etwa auf Schicht 6 zumindest
Zeichensatzformate und eine Umsetzung für ein HTML- oder XHTML-
Dokumentenformat - sonst kann er keine Seite anzeigen. Auf Schicht 5
muss er das auf TCP (Schicht 4) basierende HTTP- Protokoll umsetzen.
Natürlich reicht das heute für Browser wie Chrome längst nicht mehr aus.

## Das Internet und die Berkeley Software Distribution

Es gab einmal ein Betriebssystem namens UNIX von AT&T. Dessen Quelltexte
waren ursprünglich frei verfügbar und es kostete auch keine
Lizenzgebühren es zu nutzen. Deshalb war es besonders in Universitäten
weit verbreitet und auf seiner Basis entstand viel ebenfalls freie
Software. Als AT&T Unix dann proprietär machte, fühlten sich die Unis
betrogen und 1977 entstand an der Uni Berkeley in Kalifornien eine
weiterhin freie "unixoide" [Berkeley Software Distribution [BSD](https://en.wikipedia.org/wiki/Berkeley_Software_Distribution).
Weitere freie unixoide Betriebssysteme wie Minix oder Linux entstanden
aus dem gleichen Grund erst später und übernahmen vieles von der BSD.

Für BSD entstand die wichtigste freie Implementierung des IP-Stacks,
etwa in Form der *Berkeley Sockets* für Schicht 3 und 4 und eine große
Menge von Hilfsprogrammen, welche den für Betriebssysteme festgelegten
[Portable_Operating_System_Interface
(POSIX)](https://en.wikipedia.org/wiki/:de:Portable_Operating_System_Interface)
Standard ergänzten, womit diese Tools quasi zur Werkzeugkiste des
Internet wurden. Gut für die Teilhabe am Internet geeignete
Betriebssysteme sollten also möglichst POSIX-konform sein. OS-X bzw.
MacOS basiert letztlich auf dem BSD-Fork FreeBSD und schlägt sich da
recht gut. Microsoft baute in Windows NT eine halbherzige
POSIX-Teilimplementierung ein, musste aber in Windows 10 das [Windows
Subsystem for Linux
(WSL)](https://en.wikipedia.org/wiki/:de:Windows-Subsystem_für_Linux)
basierend auf Ubuntu einbauen, damit Cloud-Softwareentwickler sinnvoll
in der Cloud arbeiten konnten. Microsoft schafft es aber - im Gegensatz
zu ChromiumOS / ChromeOS und OS-X - bis heute nicht - auch
Linux-Software mit grafischer Bedienoberfläche nutzbar zu machen.

Monopolisten wie Apple und Microsoft tun sich natürlich Profit-bedingt
schwer mit freier und offener Software und bevorzugen lieber brachiale
Methoden der Kundenbindung wie Hardware-Bundling. Gleich Drogenhändlern
"erweitern" sie offene Standards und Protokolle mit meist gar nicht oder
unvollständig dokumentierten "Verbesserungen", um Kunden von ihren
Produkten abhängig zu machen. Gerne passiert das auch unter dem Vorwand
"Sicherheit" mittlerweile mit digitalen Zertifikaten. Bei Apple gilt das
schon für Ersatz- und Zubehörteile, die ohne den Segen von Apple oder
eines seiner Servicezentren gar nicht mehr eingebaut werden können.
Ansonsten herrscht nur "Security by Obscurity" und eine gewaltige
Geheimniskrämerei. Software kann nur noch vom Shop des Herstellers
bezogen werden und nur solange genutzt werden, bis ein Zertifikat oder
Dienst ausläuft - das gilt natürlich auch für Sicherheits-Updates. Für
Windows 10 ist nach Oktober 2025 Ende Gelände und viele Geräte sind
mangels Sicherheitsupdates für das Internet nicht mehr zu gebrauchen und
werden wohl Elektroschrott.

Das bald erscheinende Windows 11 setzt ein [Trusted Platform Module
(TPM)](https://en.wikipedia.org/wiki/:de:Trusted_Platform_Module)
voraus, das sogar vielen heute noch verkauften Rechnern und noch mehr
Bestandsrechnern fehlt und zu noch mehr Elektroschrott und hohen Kosten
für Neuanschaffung führt. War früher immer größere Bloatware Grund für
neue Hardware-Beschaffung ist es nun die fehlende Sicherheit oder die
Abschaltung von Diensten.

## Ist Google denn besser ?

Ganz klar ist Google ebenfalls ein Monopolist, der mit Android und
ChromeOS Käufer von Smartphones oder Chromebooks ebenfalls bindet. Auch
wurden schon öfter gern genutzte Dienste einfach abgeschaltet, weil sie
nicht mehr in Alphabet's oder Google's Geschäftsmodell passten.

Aber Google setzt zumindest eher auf Quelloffenheit seiner wichtigsten
Produkte. Quellcode-GIT-Repositories finden sich etwa bei Google selbst
<https://chromium.googlesource.com/> und auf GitHub. [Das
Ganze](https://www.chromium.org/chromium-os) ist auch sehr gut und
ausführlich dokumentiert Das führt zu einer Menge "Forks", also von
anderen Nutzern oder Institutionen betriebenen Portierungen und
Weiterentwicklungen. So ist Microsoft's neuer Browser Edge ja auch nur
ein [Chromium](https://github.com/chromium) Fork - und für Linux gibt es
da viele weitere Ports auf allerlei Geräte bis hin zu "Bastelrechnern"
wie dem Raspberry PI.

Auch eine offene Version von ChromeOS ist als ChromiumOS - Quelle
verfügbar und hat bereits einige Forks.

Während ChromeOS nur auf Chromebooks funktioniert, macht
[CloudReady](https://www.computerbase.de/2020-12/google-neverware-cloudready-chrome-os-fork/)
viele alte Rechner, die schon lange keine Sicherheitsupdates und
aktuelle Browser bekommen haben wieder flott. Das können "ehemalige"
MacBooks oder Window-Notebooks sein, 2GB Hauptspeicher und 32GB
Festspeicher reichen aus, ab 4GB geht auch Linux. Lediglich auf Android
Apps muss man verzichten.

Die Offenlegung von ChromeOS führt auch zu einer breiteren Unterstützung
von Plattformen. So gibt es auch einen speziellen Fork für den
vielseitigen Bastelcomputer Raspberry PI, der sich
[CyberryPi](https://www.cyberrypi.de/blogs/raspberry-pi-blog/erste-schritte-mit-chromium-os-auf-raspberry-pi)
nennt und aufzeigt, wie sehr offene Betriebssysteme auch leistungsmäßig
skalierbar sind.

Eine ins chinesische übertragener Fork von ChromeOS ist
[FydeOS](https://fydeos.io/download). Das ist für Europäer sicherlich
nicht sehr interessant, aber die US-amerikanische Embargo-Politik macht
quelloffene und freie Software sehr interessant für chinesische
Hersteller. So ist Huawei mit HarmonyOS ja bereits auf eine eigene Linux
Distribution ausgewichen und da ein Großteil unserer Hardware aus China
kommt, ist es nur eine Frage der Zeit, bis mehr chinesische Hardware
auch mit chinesischer Software ausgebreitet wird - auch weil freie
Software keine Lizenzkosten verursacht und auch Patente umgeht.

## Fazit

Bis heute ist eine zu geringe Interoperabilität eines der Hauptprobleme
der Digitalisierung. Ursache ist zu wenig Offenlegung und Verwässern
oder Nichtbeachten von Standards und freier Software. Google hat das
erkannt und daraus gelernt und macht dennoch genug Profit. Viele andere
große Firmen sind aufgrund mangelhafter Interoperabilität und
Geheimniskrämerei schon zugrunde gegangen und werden die fortschreitende
Digitalisierung nicht überleben. Und das gilt eben nicht mehr nur für
IT-Firmen.
