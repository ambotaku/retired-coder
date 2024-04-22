+++
weight=1
title = 'Where Should We Go ?'
date = 2024-04-18T16:07:42+02:00
draft = false
+++

## Programmiersprachen - Punk

Im Artikel [Die nächste Programmiersprachen-Generation]({{< ref "/projects.de/flutter/next_generation_languages.md" >}})
habe ich den Wandel der populärsten Programmiersprachen beschrieben,
der durch Paradigmenwechsel ausgelöst wurde. Programmiersprachen "altern", wenn der
Code zu groß, unübersichtlich oder unsicher wird oder schlecht performed.
Das wird auch durch ein nachträgliches "draufsatteln" neuer Features
selten besser.

So verdrängte hinsichtlich Popularität zuerst Pascal Fortran, dann C Pascal, dann
Java C/C++ und momentan noch Python Java - doch was kommt nun ?

Natürlich werden alle oben genannten Sprachen noch gebraucht, werden aber
 wegen zunehmenden Schwierigkeiten mit aktuellem Code unbeliebter.

 Was heute an Bedeutung gewinnt, ist eine  einfache und sicher erreichbare
 Reaktivität und Nebenläufigkeit im Umfeld
 immer komplexerer Daten-Kommunikation von immer mehr Cloud-Rechnern und
 Endgeräten mit immer mehr Rechenkernen. Selbst Einstiegs-Smartphones
 haben heute schon 4 Kerne, um dutzende von Prozessen und Threads zu
 synchronisieren, während sie mit Rechnern in aller Welt kommunizieren.

Sicher kann man das alles noch mit C/C++ machen, aber wie viele hoch qualifizierte
Entwickler sollen in vertretbaren Zeiträumen sicher funktionierende und sehr
komplexe Programm schreiben? C++ ist zwar über die Jahre zwar sehr stark
erweitert worden um multi-paradigmatisch zu erscheinen, aber immer noch nicht
leichter zu beherrschen als der Urahn C vor mehr als 50 Jahren.

So wie in der Musikszene immer imposanterer Rock & Roll von Glamour-Rock und dieser
vom Punk und der vom Rap verdrängt wurde - manchmal sollte man alte Zöpfe
 abschneiden und nach schlechten Erfahrungen neu anfangen.
Wegen solcher Vorbedingungen entstand bei Google wohl die neue
Programmiersprache Go - klein und auf das wirklich Nötige begrenzt.

## Informatiker - Urgestein schafft Synergie

Die Go Entwickler [Robert Griesemer](https://de.wikipedia.org/wiki/Robert_Griesemer),
[Rob Pike](https://de.wikipedia.org/wiki/Rob_Pike) und
[Ken Thompson](https://de.wikipedia.org/wiki/Ken_Thompson) brachten sehr viel
Erfahrung mit Betriebssystemen und System - nahen Sprachen mit.

Ken Thompson und Rob Pike gehören zu den Vätern
 von Unix, dem Vorläufer aller unixoiden wie Linux, BSD und macOS. Die beiden entwarfen
 bei Bell Labs (das spätere AT&T) auch das experimentelle Betriebssystem Plan 9, mit dessen
 Tools Ken Thompson dann die erste Go-Version entwickeln konnte.

Der Schweizer Robert Griesemer kam von der ETH Zürich zu diesem Team, nachdem
 er bei Niklaus Wirth promovierte. [Wirth](https://people.inf.ethz.ch/wirth/Articles/LeanSoftware.pdf)
wurde bekannt als ein Gegner von seiner Meinung nach unnötig komplexer Software -
 besonders im C- und Unix-Umfeld.

Deshalb entstand in Zürich das [Oberon System](https://www.golem.de/news/oberon-eth-das-schweizer-system-2301-170754.html)
basierend auf der Sprache Oberon als schlankere Weiterentwicklung von Modula-2,
das wiederum eine Weiterentwicklung von Pascal war, jener lange sehr populären
Sprache von  Wirth, die ihn berühmt machte und auch zu Sprachen wie
[Ada](https://de.wikipedia.org/wiki/Ada_(Programmiersprache)) oder gar der Chip-Design-Sprache
[VHDL](https://de.wikipedia.org/wiki/Very_High_Speed_Integrated_Circuit_Hardware_Description_Language)
anregte.
Die Synergie dieser drei erfahrenen Systemarchitekten führte bei Go zu einer
sehr schlanken aber mächtigen Sprache mit gerade 25 keywords. Go wirkt wie eine
Kreuzung aus C und Oberon, was beim ersten Eindruck sowohl gestandene C/C++
Entwickler als auch Kenner von Wirth- beeinflussten Sprachen wie Modula-2, Ada
und Oberon verwirren kann.

Wohl deshalb breitet sich Go bislang recht langsam aus - ähnlich wie mal bei Python,
dessen Syntax auch sehr vom C-Gewohnten abwich, was Python's Ausbreitung trotz
sehr viel einfacherer Syntax verzögerte.

## C meets Oberon

Als erstes Go - Codebeispiel zuerst dieser kleine Primzahl-Rechner von Edsger Dijkstra:

{{< highlight go >}}
// Funktionsdefinition erinnert mehr an Pascal als an C
// Parametertyp nach Name, Resultat am Ende des Funktionskopfs
// Pointer wie bei C
func dijkstraPrimes(last int) *[]int {
    // Variablen-Definition wie bei Pascal (mit Typ-Inferenz)
    // "Slices" kennt man von Python als Listen, referenzieren bei Go aber Arrays
    primes := []int{2} // erste Primzahl ist 2
    pool := []int{4}   // pool-Werte beginnen mit dem Quadrat der zugehörigen Primzahl

    // for Schleife wie bei C, Klammern sind aber überflüssig
    for test := 3; test <= last; test++ { // Blöcke wie bei C
        isPrim := true
        for index := 0; index < len(pool); index++ {
            if pool[index] == test {
                pool[index] += primes[index] // alle Operatoren wie bei C
                isPrim = false // einfache Zuweisung wie bei C
            }
        }
        // nächste Primzahl gefunden -> eintragen
        if isPrim { // keine Klammern, aber C-Blöcke
            // die den Slices hinterlegten Arrays vergrößern
            primes = append(primes, test)
            pool = append(pool, test*test)
        }
    }
    return &primes // Rückgabe einer Pointer Adresse wie bei C
} // ... und nirgendwo die völlig überflüssigen Semikolons von C
{{< /highlight >}}

## Wieso ist Go nicht "objektorientiert" ?

Den Vereinfachungen scheint auch die Objektorientierung zum Opfer gefallen zu sein,
denn Go kennt ja keine Klassen und deren Vererbung. Das ist aber eine
erwünschte Vereinfachung, denn Objektorientierung geht auch
ganz ohne Klassen, wie ja auch Javascript zeigt.

Vererbung vererbt nämlich nicht nur, sondern spezialisiert, was zu unflexibleren
Objekten und unnötig aufgeblähtem Code führen kann, wie man es gerade bei
größeren Java Programmen häufig vorfindet. [Objekt-Komposition ist also meist einer Spezialisierung
überlegen](https://en.wikipedia.org/wiki/Composition_over_inheritance) und hilft dabei,
aufgeblähte Codebasen zu vermeiden.

Polymorphie als Hauptvorteil der Objektorientierung lässt sich auch gut mit
Interfaces und Mixins erreichen - dass kennt man ja von erfolgreichen Skriptsprachen
wie Ruby, Javascript und Python schon länger.

Bei Go werden Verbunde (struct/record) mit Methoden und Konstruktoren verknüpft, Methoden-Deklarationen
werden per Interface propagiert und ein Objekt definiert letztlich durch die unterstützten Interfaces
in sein Verhalten.

Dazu ein weiteres Beispiel mit Koordinatensystemen:

{{< highlight go>}}
package main

import (
    "fmt"
    "math"
)

// eine Dimension - eine Gerade
// auch Grundtypen wie float-Zahlen können unterschiedliche Typen darstellen
type line float64

// metrische Länge
type meter float64

// imperiale Länge
type foot float64

// wegen statischer Typisierung ist foot zu meter inkompatibel.
// Hätte man die Software der Ariane 5 in Go statt Ada programmiert, wäre
// sie nicht durch solch eine "Verwechslung" explodiert ...

// 2D Vektor Typ
type Vec2d struct {
    x, y float64
}

// 3D Vektor Typ
type Vec3d struct {
    x, y, z float64
}

// jedes Objekt, welches die Funktionen eines "Distancer" implementiert
// kann Abstände berechnen - Klasse ? braucht keiner.  Duck-Typing ist Polymorphie !
type Distancer interface {
    // Berechnung des Abstands zwischen zwei Punkten
    Distance() float64
}

// Abstand zwischen Punkten einer Linie
func (l line) Distance(l2 line) float64 {
    return math.Abs(float64(l2 - l))
}

// Punkt-Abstand auf Fläche
func (v Vec2d) Distance(v2 Vec2d) float64 {
    return math.Sqrt((v2.x-v.x)*(v2.x-v.x) + (v2.y-v2.y)*(v2.y-v.y))
}

// Punkt-Abstand im Raum
func (v Vec3d) Distance(v2 Vec3d) float64 {
    return math.Sqrt((v2.x-v.x)*(v2.x-v.x) + (v2.y-v2.y)*(v2.y-v.y) + (v2.z-v.z)*(v2.z-v.z))
}

// Implementierung des Stringer interfaces für Koordinaten im Raum
// (um  Koordinaten auszugeben)
//
//  type Stringer interface {
//      String() string
//  }
//
func (v Vec3d) String() string {
    return fmt.Sprintf("{%f, %f, %f}", v.x, v.y, v.z)
}

// Konstruktor für Koordinate (eigentlich unnötig, weil auch Literal möglich ist)
func NewVec3d(x, y, z float64) Vec3d {
    return Vec3d{x: x, y: y, z: z} // benutze Literal
}

// 3D Vektor Addition
func (v Vec3d) AddVec3d(v2 Vec3d) Vec3d {
    return Vec3d{x: v.x + v2.x, y: v.y + v2.y, z: v.z + v2.z}
}

func main() {
    v1 := NewVec3d(1.0, 2.0, 3.0)
    v2 := NewVec3d(2.0, 2.0, 2.0)

    // Operator-Überladung gibt es bei Go (absichtlich) nicht
    // denn als Obfuskation ist das oft eine Fehlerquelle
    v3 := v1.AddVec3d(v2)

    // printf kennt man von C
    fmt.Printf("v1+v2 = %f\n, Distanz: %f\n", v3, v1.Distance(v2))

    v4 := Vec2d{2.0, -1.0} // literale Vektor Definition ersetzt Konstruktor
    v5 := Vec2d{-1.0, 3.0}
    fmt.Printf("v4 v5 Abstand: %f\n", v4.Distance(v5))

    l1 := line(3.0)
    l2 := line(5.0)
    fmt.Printf("l1 l2 Abstand: %f\n", l1.Distance(l2))
}
{{< /highlight >}}

## Keine C/C++ Header-File Hölle mehr

Da ich in den 1980ern von meinem geliebten Turbo-Pascal auf Logitech's Modula-2
umgestiegen bin, war danach Borland's Turbo-C++ für mich eine Header File Hölle,
denn der Modula-Compiler erzeugte für Bibliotheken bzw. Module neben dem Code
auch eine zum Code passende Modul-Definitionsdatei für den Linker.

Das ging wegen des "Prä-Prozessors" und später auch Templates bei C/C++ nicht mehr.
Die Entwicklungsumgebung brauchte neben Compiler und Linker stets auch Make-Tools,
die immer komplizierter wurden und jeden Build zu einem Abenteuer machten -
spätestens wenn irgend eine Bibliothek aktualisiert werden musste.

Das wurde auch durch Automake und aktuell CMake nicht wirklich besser und hat
mir C/C++ - gerade auch im OpenSource Umfeld endgültig verleidet.

Bei Go ist man da zum Glück Wirth's Vereinfachungs-Philosophie gefolgt bzw. nutzt
eine simple Modul-Liste für die verwendeten Module, ähnlich wie man das auch
von NodeJS oder Flutter/Dart kennt.

Module exportieren alle groß geschriebenen Bezeichner und verbergen klein Geschriebenes,
Zugriffs-Spezifikationen wie **private, public** oder gar **protected** braucht es so nicht.

Auch um die um die im Kopf der Module genannten Importe braucht man sich nicht zu kümmern,
Modulnamen stehen ja als Prefix vor den verwendeten Symbolen (wie **math** und **fmt** im
Beispiel oben). Das veranlasst den Editor bzw das Tool **gofmt** nicht nur dazu den Quellcode
einheitlich zu formatieren, sondern generiert auch die Importe des bearbeiteten Moduls.

Überhaupt wird der gesamte Lebenszyklus von Modul-Generierung, über Build bis Test von
einem Befehlszeilen-Tool **go** gesteuert. Builds können dabei auch für
andere Plattformen (Prozessor-Architekturen und Betriebssysteme) cross-compiliert
werden, so wie es auch bei Flutter / Dart möglich ist.

Es gibt also wenig, was von dem Content ablenkt, den man mit Go erstellen möchte -
das ist wohl der wichtigste Unterschied zu Umgebungen wie C/C++ oder Java, wo
Entwickler oft mehr mit administrativem Drumherum als der zu bewältigenden Aufgabe
beschäftigt sind.

## Worin unterscheiden sich Dart und Go ?

In dieser Artikelserie beschäftige ich mich ja mit den beiden neuen Programmiersprachen,
die Google propagiert und auch intern viel nutzt. Bei ähnlich vereinfachtem
administrativem Handling empfehlen sich die Sprachen aufgrund ihrer Architektur
für unterschiedliche Anwendungsgebiete.

Dart ist klar klassisch objektorientiert angelegt, weil moderne Benutzerschnittstellen
sehr komplexe Widget-Taxonomien mit sich bringen. Man denke alleine, was und wie viele
Arten von Buttons, Textgestaltungen und Einfärbungen es gibt - all diese Items bilden
tiefe Hierarchien. Dart's Nutzung von hochkomplexen konstanten Objekten (wie
alle statischen Widgets) ermöglicht es, sehr aufwändige Bedienoberflächen ohne eine
Auszeichnungssprachen wie XML, HTML oder CSS aufzubauen und dabei von Vererbung zu
profitieren. Die Problematik von States als Bestandteil von Objekten wird durch die
klare Unterscheidung von Zustand-behafteten und zustandslosen Objekten gelöst.

Damit empfiehlt sich Dart zusammen mit Flutter als hervorragendes Toolset für Frontend-
Projekte. Die sehr weit reichenden Cross-Compile Möglichkeiten erlauben dabei eine
gemeinsame Codebasis für alle heute relevanten Frontends.

Go sehe (nicht nur ich) vor allem im Backend. Von kleinen Befehlszeilentools bis hin zu
komplexen Anwendungsservern reicht dabei die Spannweite. In diesen Bereichen wird Go
schon länger eingesetzt.

Nicht zuletzt wird sogar diese Website ja komplett von [Hugo](https://gohugo.io/) -
also auch einer Go Anwendung - gebaut. Es dauert aktuell 0.414 Sekunden, meine
Markdown-Dateien zu dieser Site zusammen zu setzen. Das machte mich letztendlich neugierig
auf diese Sprache, die mir erlaubt, Hugo noch mit besonderen Mods zu erweitern.

Eine Gemini-Anfrage zur Nutzung von Go lieferte folgende Antwort:

## Welche bekannten Anwendungen wurden in Go entwickelt ?

(**WARNING: blatant advertising**)

Go, die Programmiersprache von Google, hat sich in kurzer Zeit zu einer beliebten Wahl für die Entwicklung einer Vielzahl von Anwendungen entwickelt. Hier einige bekannte Beispiele:

### Von Google

- Google Chrome: Der beliebteste Webbrowser der Welt verwendet Go für Teile seines Kerns und seiner DevTools.
- Google Earth: Die beliebte 3D-Globus-Anwendung nutzt Go für die Backend-Infrastruktur.
- YouTube: Die Video-Sharing-Plattform verwendet Go für verschiedene Backend-Dienste und Skalierungstools.
- Google App Engine: Die Platform-as-a-Service (PaaS) von Google nutzt Go als zentrale Programmiersprache.

### Von anderen Unternehmen

- Kubernetes: Das Open-Source-Container-Orchestrierungssystem wird von Google entwickelt und nutzt Go extensiv.
- Docker: Die Containerisierungsplattform verwendet Go für seinen Docker Engine und andere Komponenten.
- Dropbox: Der Cloud-Speicherdienst nutzt Go für seine Backend-Dienste und Synchronisationstools.
- Twitch: Die Live-Streaming-Plattform für Spiele und Unterhaltung verwendet Go für seine Backend-Infrastruktur.
- SoundCloud: Die Audio-Sharing-Plattform nutzt Go für seine APIs und Backend-Dienste.
- Uber: Die Mobilitätsplattform verwendet Go für verschiedene Backend-Dienste und Mikroservices.
- SendGrid: Der E-Mail-Zustelldienst nutzt Go für seine APIs und Skalierungstools.

### Weitere Anwendungsbereiche

- Webserver und APIs: Go eignet sich aufgrund seiner Schnelligkeit, Einfachheit und Konkurrenzfähigkeit hervorragend für die Entwicklung von Webservern und APIs.
- Microservices: Die modulare Architektur von Go macht es ideal für die Entwicklung von Microservices-basierten Anwendungen.
- Kommandozeilentools: Go ist beliebt für die Entwicklung von leistungsstarken und effizienten Kommandozeilentools.
- Netzwerkanwendungen: Aufgrund seiner Netzwerkfunktionen und -leistung eignet sich Go gut für die Entwicklung von Netzwerkanwendungen.

{{< notice note >}}
Im nächsten Kapitel geht um Go-Routinen. Diese stellen wohl eine Weiterentwicklung von
Oberon's bzw. Modula's Coroutinen dar, ermöglichen also sehr unkompliziert
Nebenläufigkeit und Task-Synchronisation.
{{< /notice >}}

## weitere Artikel zu Go

- [Nebenläufigkeit mit Goroutinen]({{< ref "go1.md" >}})
