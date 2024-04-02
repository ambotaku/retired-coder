+++
weight = 20
title = 'Keine Nachhaltigkeit wegen Verdongelung'
date = 2024-04-01T19:03:39+02:00
draft = false
+++
# Verdongelung kontra Nachhaltigkeit

Der Leitartikel in c't 18/2021 machte auf ein Problem aufmerksam, das
sich zunehmend stellt: Elektroschrott entsteht durch nicht mehr von
Software unterstützte, aber noch gut verwendbare Hardware. Man kauft
sich ein neues, "digitalisiertes" Haushaltsgerät, eBike, Auto oder
Computerperipherie wie einen Drucker, welches sich per "App" über einen
Computer oder Smartphone konfigurieren oder verwenden lässt, aber kaum
eigene Bedienelemente - außer vielleicht noch einen Power-Schalter hat.

Eine Verbindung entsteht auch nicht mehr über Kabel, sondern eine
Funkverbindung wie Bluetooth oder WLAN - allein schon weil eine
Kabelverbindung zum Smartphone nicht möglich ist. Nach dem Einschalten
kommt dann entweder sofort - oder nach einem Update des angeschlossenen
Geräts oder Rechners die Enttäuschung: Die bislang tadellos zusammen
arbeitenden Komponenten kennen sich nicht mehr. Ein Update oder neues
Smartphones behebt das Problem vielleicht, aber dafür werden durch die
Aktualisierung des Smartphones andere Geräte unerreichbar. Manchmal wird
auch ein Dienst einfach abgeschaltet und die auf diesen angewiesene
Hardware mag nicht mehr.

Das kennt man ja schon von Fernsehern. Der Fernseher könnte sicher noch
DVB T1 empfangen, aber nicht mehr DVB T2 und wird ohne eine Settop-Box
zu unbrauchbarem Elektroschrott - aber zurück zum Internet bzw.
"Cloud"-Systemen.

## Im Namen der Sicherheit

Jedes Gerät, dass eine Verbindung mit der "Außenwelt" aufnimmt - sei es
über Kabel, Funkverbindung oder Datenträger (USB-Stick oder Diskette)
ist angreifbar und hat bereits entdeckte oder noch unbekannte
Software-Schwachstellen, ist also Viren, Trojanern oder anderen "Hacks"
ausgesetzt, sobald eine Verbindung hergestellt wird - von oder zu (fast)
jedem anderen Gerät oder Dienst. Deshalb muss es regelmäßige Updates vom
Hersteller geben - vor allem bei älteren Geräten scheitert das aber
schon an einer Möglichkeit der Hardware.

Bei jedem Update muss aber sichergestellt sein, dass der Update auch
wirklich vom Hersteller stammt. Dazu dienen heute digitale Zertifikate,
mit welchen alle Veröffentlichungen des Herstellers "signiert" werden,
damit nicht Schadsoftware als Update getarnt das Gerät oder Nutzerdaten
schädigen kann. Zertifikate haben stets eine Gültigkeitsdauer, meist nur
ein oder zwei Jahre. Sie verwenden eine Zertifikatskette, die bei einer
Prüfung über verschiedene Herausgeber bis zu einem Stammzertifikat
zurückverfolgt werden kann. Die Prüfung geschieht über öffentliche
Schlüssel (public keys), weshalb Browser oder Betriebssysteme zumindest
die public keys aller bedeutenden Stammzertifikate kennen müssen.

Ein Ablaufen oder Sperren kompromittierter Stammzertifikate kann wie das
Abschalten eines Update-Dienstes weitere Updates unmöglich machen,
wodurch zwangsläufig Elektroschrott entsteht, wenn ein Hersteller ein
Produkt nicht mehr "supported".

Meine Frau hat ein Apple MacBook, dass nur bis zur Betriebssystemversion
OSX 10.10 updatebar ist und konnte es mit Google Chrome aber bis vor ein
paar Wochen noch verwenden (**WARNUNG: man sollte eigentlich nicht mit
so einem alten Betriebssystem noch ins Internet gehen und persönliche
Daten hinterlassen**). Das finale Problem entstand aber erst, als Google
Chrome sich für das alte Betriebssystem nicht mehr updaten ließ und in
der Folge abgelaufene Stammzertifikate in Chrome keine sichere
HTTPS-Verbindung mehr ermöglichten. Damit wurde dies von der Hardware
noch durchaus brauchbare Notebook nun Elektroschrott, denn ohne HTTPS
funktionieren die meisten Websites nicht mehr korrekt.

Leider ist aber für die Hersteller und Dienstanbieter Sicherheit ein
guter Vorwand, die Nutzbarkeit und Nutzungsdauer von Geräten künstlich
zu begrenzen oder nur Originalbauteile und im eigenen Shop verbreitete
Software zuzulassen. Das kennt man ja schon länger von den Smartphones,
wird aber auch bei Computern unter Mac OS-X, Windows 10S, Windows 11 und
ChromeOS üblich. Bei Apple-Computern haben bereits Ersatzteile
Zertifikate und so können nur Original-Ersatzteile nur von
Apple-ernannte Service-Zentren eingebaut werden. Eine Reparatur durch
freie Werkstätten ist bei neuerer Apple Hardware unmöglich. So kann
Apple kann für seine Produkte und Dienstleitungen auch weiter überzogene
Preise verlangen - egal welche Qualität dafür geboten wird. Diesem
Beispiel folgen leider auch andere große Anbieter und die Nutzer
verlieren immer mehr Einfluss darauf, welche Produkte sie noch wie lange
verwenden "dürfen" - vorgeblich zu ihrer "Sicherheit" - in Wahrheit um
die Marktmacht von Monopolisten zu festigen.

## Ausweg "freie Software" ?

Das Problem dieser unethischen Kundenbindung und proprietärer statt
freier Software ist so alt wie Software selbst. Bereits IBM baute eine
Monopolstellung bei Computern auf, die erst durch die US- Kartellbehörde
(teilweise) aufgehoben wurde. Lange konnten sich nur Großunternehmen
IBM-Rechner leisten, erst neue Marktnischen wie Prozessrechner,
Minicomputer und schließlich die von IBM "Personal Computer" genannten
Microcomputer-Systeme ließen eine Konkurrenz entstehen, die aber auch
wieder nur zu neuen Monopolen führte.

Schon bei dem von AT&T entwickeltem und anfänglich frei verfügbarem
Minicomputer-Betriebssystem UNIX führte dessen Kommerzialisierung zu
einem Monopol. Da zwischenzeitlich aber Universitäten wie Berkeley und
MIT sehr viel UNIX-Software unentgeltlich beitragen konnten, da der
ursprüngliche Quellcode frei verfügbar war, entstanden Initiativen wie
die Berkeley Software Distribution (BSD), Gnu is not Unix (GNU) seitens
Mitarbeitern des Massachusetts Institute of Technology (MIT) und später
noch Minix von der Universität Amsterdam. Alle modernen Betriebssysteme
außer Microsoft Windows und einigen alten IBM-Betriebssystemen basieren
auf diesen offenen Quellen, denn "offen" heißt dabei die Ausbreitung des
kompletten Quellcodes, um eine Weiterentwicklung auch durch Dritte zu
fördern. Ein Minix-Derivat ist sogar in jedem aktuellen Intel-Prozessor
zur Hardware - Konfiguration integriert.

Die BSD Lizenz erlaubt eine Entwicklung ohne den Zwang zur Offenlegung
des hinzu gefügten oder veränderten Quellcodes, wodurch Apples
proprietäres Betriebssystem OS-X (macOS) und Sun's Solaris erst möglich
wurden, es gibt aber auch freie und kostenlose BSD-Varianten wie FreeBSD
und NetBSD. Auch große Teile des Internet Netzwerk-Stacks von Microsoft
Windows basieren auf BSD- Code

Die GNU Lizenzen (General public License, GPL) außer LGPL verlangen
ausdrücklich die komplette Quellcode-Ausbreitung aller auf GNU-Code
basierender Software. Das bekannteste Produkt mit GNU-Lizenzen ist der
Betriebssystemkern Linux, auf dem wegen einiger Lizenz-Erleichterungen
wie LGPL etliche Linux-Distributionen unter Einbeziehung von weiterer
offenen Software - etwa Teilen von BSD - aufbauen. Einige dieser
Betriebssysteme sind sogar wieder mehr oder weniger proprietär; etwa
Google's Betriebssysteme Android und ChromeOS und die
Linux-Distributionen von Oracle, SuSE oder Redhat.

Linux ist - mit Abstand - das am Weiten verbreitetste Betriebssystem.
Durch Android, ChromeOS und allerlei Netz-Infrastruktur (Router,
Switches, Drucker, Settop-Boxen, Sony Spielkonsolen) ist das selten
"oberflächlich" sichtbar, auch weil nahezu alle Internet-Software
letztlich auf BSD basiert - mit den "Berkeley Sockets" als grundlegender
Programmierschnittstelle.

Der durch Quelloffenheit gigantische Softwarepool skaliert vor allem den
Linux-Kernel von einfachen Armbanduhren und Smartphones bis hin zum
Betriebssystem von Supercomputern und Serverclustern. Die GNU Compiler
Collection erleichtert die Software-Entwicklung für neue Hardware jeder
Dimension von simplen Microcontrollern (Arduino Software) bis zu
kompletten Prozessor-Neuentwicklungen.

Leider liefern aber häufig unklar definierte Buzzwords wie Datenschutz,
Software-Stabilität und IT-Sicherheit gute Vorwände für Hersteller
proprietärer Software, ihre Kunden immer weiter in kostspielige und
unfreie Abhängigkeit zu zwingen - auch mit dem oben beschriebenen
Profit-orientiertem Zertifikatsmißbrauch. Die Politik sollte
IT-Hersteller zumindest zu längerer Update-Unterstützung verpflichten.

## Nichts geht mehr ohne Cloud

Als Bill Gates seine Vision vom *Computer für Jedermann* mit DOS,
Windows und PC-Desktop erfolgreich umsetzen konnte, verlagerte sich die
Verfügbarkeit von Computern von Büro-Arbeitsplätzen auch in den
Privatbereich und dabei entstanden ganz neue Anwendungsmöglichkeiten wie
Spiele, Text-, Bild- und Videobearbeitung sowie Chat und Mailboxen. Das
funktionierte noch ohne zentrale Kontrolle, Serverfarmen und
Dienstanbieter. Erst mit dem - von Gates zu spät erkanntem Internet -
und darauf zugeschnittenen Webservern verlagerte sich die "Datenhoheit"
wieder zunehmend in zentrale Server und schließlich wurde der "Browser"
zur wichtigsten Schnittstelle für Daten, Medien und Kommunikation. Diese
"Datenhoheit" wechselte so von Microsoft vor allem an Google, die mit
ihrer namensgebenden "Suchmaschine" die beherrschende Schnittstelle zu
den meisten im Netz verfügbaren Daten wurde.

Microsoft konnte Google's Vorsprung nie mehr aufholen und Google machte
mit ChromeOS Browser und Suchmaschine zum zentralen Bestandteil dieses
Endbenutzer-Betriebssystems. Dennoch dauert es recht lange, den durch
Hardware-Bündelung verbreiteten Windows-Desktop durch geeignetere
Betriebssysteme zu ersetzen. Bei allen anderen Plattformen außer dem PC
ist das aber wohl gelungen, weil Microsoft nicht nur das Internet,
sondern vor allem den Trend zur Mobilität verschlafen hat und mit
Windows-Phones viel zu spät kam. Linux verzettelte sich mit zu vielen
Distributionen für Desktops, konnte aber mit Android den Mobilbereich
erobern. Da Windows groß, schwerfällig und im Vergleich zu modernen
Alternativen wenig Benutzer-freundlich ist, gewinnt mit der wachsenden
Verbreitung von Cloud-Diensten ChromeOS zunehmend an Bedeutung, auch
weil es viel weniger Rechenleistung benötigt und wie auch Android mit
eher preiswerter Hardware auskommt.

Neben dem proprietären ChromeOS, dass neben Web-Anwendungen virtuelle
Maschinen für Android und die Linux-Distribution Debian mitbringt, gibt
es noch das quelloffene und freie ChromiumOS, das sogar auf recht alten
PCs und Apple Macs noch gut läuft - lediglich Android fehlt ChromiumOS.

Auch ChromiumOS bleibt durch automatisierte und den Nutzer nicht - wie
Windows - behindernde Sicherheits-Updates ständig aktuell und ermöglicht
so auch die weitere recht komfortable Nutzung des 10 Jahre alten
MacBooks meiner Frau.

## Welche Cloud hätten Sie den gern ?

Mit der zunehmenden "Digitalisierung" - oder besser gesagt Vernetzung -
der meisten elektronischen Geräte kommt man um eine Abhängigkeit von
mehreren Netzanbietern oder Betriebssystem - bzw. Rechner-Herstellern
kaum herum, wenn man Zugriff auf aktuelle Dienste und
Kommunikationsmedien braucht. Man kann sich eigentlich nur den für sich
selbst persönlich noch vertretbaren Monopolisten entscheiden.

Das fängt mit der Auswahl der Endgeräte an. Gibt es hier einen Druck
oder gar Zwang, alle Geräte von einem Hersteller (wie Apple) zu kaufen,
damit diese zusammen funktionieren können, oder kann ein Smartphone oder
Tablett von einem anderen Hersteller als neuer Desktop-Rechner oder
Laptop gekauft werden ? Letzeres kann leicht zu allerlei Ungemach,
aufwändiges Gefrickel und temporären oder endgültigen Ausfällen führen.
Gerade Windows-Anwender kennen das vielleicht seit seligen DOS-Zeiten
nur zu gut.

Leider wird es aber immer schwerer, überhaupt noch ein anderes
Betriebssystem als das vorinstallierte auf ein Gerät zu bringen, wenn
die Restriktionen des Originals, etwa beschränkte Software-Auswahl im
Shop oder Nutzung dort nicht mehr angebotener Anwendungen, das nicht
erlauben. Apple-Nutzer hatten hier schon öfter das Nachsehen und auch ab
Windows 10S, Windows 11 und Android muss man mit Überraschungen wie
Support-Einstellungen rechnen. Wenn dann selbst die Hardware keine
Alternativen bietet, weil noch nicht mal mehr von einem
Installationsmedium (etwa USB-Disk oder DVD) gestartet werden kann, hat
man unweigerlich Elektroschrott. Ähnliches gilt für
Hardware-Erweiterungen, Zubehör-Nutzung etc. - etwa die bange Frage:
Funktioniert mein Drucker, Scanner oder die Grafikkarte noch nach dem
nächsten Software-Update ?

All diese Fragen lassen sich oft mit der Frage: "Kriege ich noch Linux
oder BSD auf dem Rechner installiert?" reduzieren - das reduziert die
Abhängigkeit auf wenige benötigte Cloud-Dienste. Auch ChromiumOS ist
hier eine gute Alternative, denn die meisten Cloud-Dienste lassen sich
auch noch ohne ein Googlemail-Konto nutzen, Android bzw. Googles
PlayStore wird bei ChromeOS (im Gegensatz zu ChromeOS) ohnehin nicht
unterstützt, Linux ist aber noch möglich. Mit der kostenlosen ChromiumOS
Distribution *CloudReady* von *Neverware* lassen sich viele alte
Rechner - wie MacBooks oder Windows-Notebooks auch im Internet sicher
und erstaunlich performant weiter nutzen.

Da über Apple und Microsoft in allen Medien viel geschrieben wird,
stelle ich bald in einem
[Folgeartikel](/hardware/chromeos_als_alternative_zu_macos_und_microsoft_windows)
die gerade für weniger Computer-affine Nutzer geeignete und auch auf
preiswerteren "Chromebooks" oder alten Rechnern gut funktionierende
Betriebssystem ChromiumOS / ChromeOS vor.