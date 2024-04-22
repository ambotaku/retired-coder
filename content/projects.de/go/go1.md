+++
weight=2
title = 'Nebenläufigkeit mit Goroutinen'
date = 2024-04-18T16:08:00+02:00
draft = false
+++

## Goroutinen sind einfach

Jede Prozedur, also Funktion, die kein Ergebnis zurückgibt, kann als Goroutine gestartet werden,
indem man vor den Aufruf das Schlüsselwort **Go** schreibt:

{{< highlight go >}}
go render("das ist eine Goroutine")
{{< /highlight >}}

Eine Goroutine sollte mit **return** verlassen werden können, denn sie kann
auch weiter laufen, wenn das Hauptprogramm schon beendet wurde. Meist macht
eine Goroutine, die nicht mit dem Hauptprogramm oder anderen Goroutinen
kommuniziert, auch wenig Sinn. Zur Kommunikation zwischen Hauptprogramm und
Goroutinen dienen Channels (Schlüsselwort **chan**). Wie Kollektionen
(slices, structs, maps, etc.) werden channels mit der Funktion **make**
erstellt:

{{< highlight go >}}
senke := make(chan int) // ein Kanal, der eine Ganzzahl transportiert
senke <- 42 // sendet die Zahl 42 in den Kanal "senke"

// eine andere routine
func DoAnything(senke chan int) {
    // eine Routine wartet, bis der Kanal senke eine Zahl sendet
    gotAnything:= <- senke // danach läuft die Routine weiter
    ...
}
{{< /highlight >}}

Auf diese Weise lassen sich Goroutinen und Hauptprogramm synchronisieren und
werden angehalten, bis für sie benötigte Daten über einen Channel bereit
gestellt werden können, ohne dass Rechenzeit verschwendet wird. Das Konzept
erinnert an Message-Loops bei anderen Architekturen, ist aber flexibler,
weil man noch mehr damit anfangen kann. Auch können Goroutinen auch
wirklich nebenläufig ausgeführt werden, und die im Kanal transportierten
Daten benötigen keinen Mutex, weil simultaner Zugriff auf sie verhindert
ist. Sollte man dennoch simultan auf Variablen zugreifen müssen,
verwendet man natürlich auch bei Go Mutexe.

Jedenfalls kann man auch mit Goroutinen und Channels gut Anwendungsschichten
modellieren, die sich über Channels austauschen. Anwendungsserver empfangen
etwa Aufrufe via HTTP Befehlszeile und filtern in mehreren Middleware-Schichten
Parameter heraus, erledigen Authentifizierung, suchen Daten in Datenbanken und
bauen schliesslich eine aus allen angeforderten Daten eine Webseite zusammen
und liefern diese an den Absender des Requests aus.

So etwas kann man mit Goroutinen und Channels gut lösen. Das folgende
Beispiel zeigt einen Client, der zwei Goroutinen-Schichten
besitzt, um in einer Schicht Daten von einem JSON-Webservice zu holen, um
sie mit einer anderen Goroutine stückweise verzögert  auf der Konsole
auszugeben.

{{< highlight go >}}
package main

import (
    "encoding/json"
    "fmt"
    "io"
    "net/http"
    "time"
)

// ein freier Zitate-Webserver
const Api = "https://type.fit/api/quotes"

// Datenmodell für JSON Zitat
type Quote struct {
    Text  string `json:"text"`
    Autor string `json:"author"`
}

// der JSON Server liefert ein Array aus Zitaten
type Quotes []Quote

// Service Zugriffs Goroutine
// api: die URL des Zitate-Servers
// ch: Go-Channel für Quelle
//
func request(api string, ch chan Quote) {
    var quotes Quotes

    // Zitate per HTTP GET abholen
    resp, err := http.Get(api)
    if err != nil {
        fmt.Println("Failed to fetch quote:", err)
        ch <- Quote{"", ""} // signalisiere Abbruch
        return
    }

    // beendet nach Verlassen der Funktion die Server-Verbindung
    // das ist auch eine Nebeneffekt der Go - Channel-Architektur
    defer resp.Body.Close()

    // liest den Body des Get-Requests ein
    body, err := io.ReadAll(resp.Body)
    if err != nil {
        fmt.Print("Failed to read response body:", err)
        ch <- Quote{"", ""}
        return
    }

    // dekodiert die JSON Daten in das Go Datenmodell (Datentyp Quote)
    err = json.Unmarshal([]byte(body), &quotes) // call by reference
    if err != nil {
        fmt.Println("Failed to parse response body:", err)
        ch <- Quote{"", ""}
        return
    }

    // sende die Zitate einzeln in den Quellen-Kanal
    for _, q := range quotes {
        ch <- q
    }

    // melde Daten-Ende
    ch <- Quote{"", ""}
}

// Ausgabe - Goroutine
// ch: Go-Channel für Senke
//
func render(ch chan Quote) {
    count := 1 // Zitate - Zähler

    // Schleife wird durch leeres Zitat beendet
    for {
        q := <-ch // empfangen eines Zitats

        // wenn kein weiteres Zitat -> beende Goroutine
        if len(q.Text) == 0 {
            fmt.Println("no more quotes today")
            break
        }

        // gib Zitat aus
        fmt.Printf("%d: %s - %s\n", count, q.Text, q.Autor)
        count++
        // warte 2 Sekunden
        time.Sleep(2 * time.Second)
    }
}

func main() {
    // öffne Quell-Kanal
    quelle := make(chan Quote)
    // starte Server-Abfrage
    go request(Api, quelle)

    // öffne Senken-Kanal
    senke := make(chan Quote)
    // starte Ausgabeschleife
    go render(senke)

    for {
        // übergib Zitat an Ausgabeschleife
        q := <-quelle
        // wenn keine weiteren Zitate, stoppe Ausgabe
        if len(q.Text) == 0 {
            senke <- q
            break
        }

        // sende Zitat an Ausgabe
        senke <- q
    }
}
{{< /highlight >}}
