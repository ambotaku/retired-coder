+++
weight = 3
title = 'Dart Spracheigenschaften'
date = 2024-04-09T14:21:00+02:00
draft = false
+++

{{< notice note>}}
In dieser Artikelreihe setze ich etwas Grundwissen in einer Programmiersprache
 mit C-ähnlicher Syntax (C/C++, Java, C#, Go, TypeScript) voraus und konzentriere
 mich vor allem auf die Besonderheiten von Dart. Es ist hilfreich sich als Einsteiger
 zuerst mit einer dieser Sprachen zu beschäftigen, denn Dart hat sonst eine
 recht steile Lernkurve.

 Problemerfahrung mit ähnlichen Sprachen hilft beim Verständnis
 jener Konstrukte von Dart, die geschaffen wurden,
  um solche Probleme zu vermeiden. :nerd_face:
{{< /notice>}}

## Daten in Dart Programmen

Die Auswahl an skalaren Datentypen ist bei Dart gegenüber anderen C-ähnlichen
Sprachen begrenzt.

Es gibt nur drei numerische Datentypen:

### int : Ganzzahlen mit max. 64 Bits

Die genaue Bitlänge hängt von der Zielumgebung ab. Javascript als Zielumgebung
etwa kennt nur 56 Bit lange Ganzzahlen. Die Dart VM (bei Ausführung ohne
Transpilierung verwendet aber immer 64-Bit Zahlen).

Ansonsten gibt es auch
 keine kürzeren Zahlentypen mit 8, 16 oder 32 Bit und keine Unterscheidung
von Zahlen mit oder ohne Vorzeichen (signed / unsigned).

Beispiel:
{{< highlight dart >}}
int x;          // Deklaration
int y = 100;    // Deklaration und Definition
z = 3           // Typinferenz (Dart bestimmt den Typ nach dem Wert)
red = 0xff000;  // Hexadezimalzahlen wie bei C/C++
{{< /highlight >}}

### double : Fließpunktzahlen mit 64 Bits

Fließpunktzahlen entsprechen dem ISO Standard 754. Für Typinferenz muß ein
Dezimalpunkt angegeben werden:

{{< highlight dart >}}
pi = 3.1415927;
plankLength = 1.616e-35; // Plancklänge in Meter
{{< /highlight >}}

### BigInt : beliebig genaue Ganzzahlen

{{< highlight dart >}}
import 'dart:math';     // math library enthält Potenzierfunktion pow()

ten = BigInt.from(10);
gogol = ten.pow(100);   // die Zahl namens Gogol hat 101 Stellen
{{< /highlight >}}

BigInts sind eigentlich kein integraler Bestandteil der Dart-Sprache,
sondern nur wie eine Library - etwas umständlich - nutzbar.
Es gibt also keine BigInt- Literale und nur die nötigsten überladene Operatoren.

### Zeichenketten (strings)

Es gibt auch keinen char-Typ wie in C/C++ sondern nur immutable Strings.
Stringkonstanten können aber auch mehrzeilig sein.
Als String Quotes können Apostrophe und Anführungszeichen verwendet werden.
Strings können mit den Operatoren '+' oder ',' konkateniert werden,
performanter geht das aber mit einer Stringbuffer-Klasse.

{{< highlight dart >}}
one = '1';           // es gibt keinen char-Typ
roman = '''Das Schweigen im Walde
Ein Roman in zwei Bänden von
"Ludwig Ganghofer"

Kapitel 1 ...''';
greeting = 'hello', ' world' + '!'; // Konkatenierung
{{< /highlight >}}

Die Möglichkeiten zur Stringverarbeitung sind ansonsten mit Sprachen wie Python,
Java oder JavaScript vergleichbar, auch reguläre Ausdrücke (regex) sind gut unterstützt.

### Logic (bool Werte)

Hinsichtlich logischer Werte ist mit der Klasse **bool** welche die Werte **true** und
 **false** kennt, alles wie bei anderen Sprachen der großen C-Familie, aber es gibt auch
 noch den Wert **null**, der seine eigene Klasse mit nur diesem Wert bildet.

### Der Wert **null**

Der Wert **null** steht für undefinierte (also nicht initialisierte) Variablen
 oder fehlende Ergebnisse.

{{< notice warning >}}
Eine Besonderheit des Dart-Compilers ist die Prüfung auf nicht initialisierte Variablen.

Bei deren Verwendung bricht die Übersetzung mit einem Fehler ab, denn der Wert **null** ist
zu keiner anderen Klasse als **Null** kompatibel und eine nicht zugewiesene Variable
hat immer den Wert **null** und ist somit ein Fehler.
Deshalb sollte man Variablen stets initialisieren, wenn das möglich ist.

Andernfalls hängt man dem Typnamen ein Fragezeichen an, um temporär **null**-Werte
zuzulassen. Das verpflichtet dann natürlich zu eigenen Prüfungen auf **null**.

Seit Dart 2.0 müssen Programme vollständig [null safe](https://dart.dev/null-safety/understanding-nul-safety) sein. Ältere Code-Beispielen lassen sich deshalb manchmal
nicht übersetzen.
{{< /notice >}}

### Konstanten und Speicherort

Ungewöhnlich bei Dart ist die Unterscheidung von **final**- und **const**- Konstanten.

{{< highlight dart >}}
final pi = 3.1415927     // dies ist eine Variable,
                         //deren Wert nicht mehr verändert werden darf

const yellow = 0xffff00; // der Compiler ersetzt **yellow** überall
                         // durch den Wert 0xffff00
{{< /highlight >}}

Die häufige Verwendung von **const** zieht sich durch die gesamte Architektur
von Dart und Flutter. Flutter-Widgets, die keine veränderlichen Werte enthalten,
werden mit **const**-Klassen definiert. Das folgende Beispiel definiert eine
simple Textbox mit einer überladenen build-Methode, welche die Textbox neu rendert,
wenn sich der Inhalt ändert (den Code muss man im Detail hier noch nicht zu verstehen).

{{< highlight dart >}}
import 'package:flutter/material.dart';

// ein StatelessWidget ist **const** und kann keine
// darin dargestellten Werte mehr ändern und muss bei
// Änderungen neu gezeichnet werden.
//
// die dem Konstruktor beim Aufruf übergebenen Werte number und size müssen **final**
// sein, um innerhalb einer Instanz der Klasse keine Änderung mehr zuzulassen
//
class EntryLine extends StatelessWidget {
  // bei einem const Konstruktor darf die Instanz keine veränderlichen Werte besitzen
  const EntryLine({super.key, required this.number, required this.size});

  final String number; // angezeigter Text
  final Size size;     // Schriftgröße

  @override
  Widget build(BuildContext context) {
    // auch beim Aufbau des Widgets werden möglichst Konstanten
    // für alle enthaltene Elemente benutzt (siehe EdgeInsets und TextStyle)
    return Container(
      alignment: Alignment.centerRight,
      width: size.width,
      height: 50,
      padding: const EdgeInsets.symmetric(horizontal: 20, vertical: 10),
      decoration: BoxDecoration(
        color: Colors.teal[400],
        border: Border.all(color: Colors.black),
      ),
      child: Text(
        number,
        textAlign: TextAlign.end,
        style: const TextStyle(
            fontSize: 24, fontWeight: FontWeight.bold, color: Colors.white),
      ),
    );
  }
}
{{< /highlight >}}

Das Beispiel zeigt die funktionale Architektur von Dart. Es wird schon beim
kompilieren sicher gestellt, das sich dieses Widget zur Laufzeit ändert,
denn es wird bei neuen Werten auch neu gerendert. Wegen der const Konstanten
kann der Dart-Compiler das Widget auch vorübersetzen, sodass die Laufzeit-
Performance und der Speicherbedarf minimiert wird.

Das Letztere  ist gerade für Mobilgeräte wichtig, denn vorübersetzter Code kann
im nur lesbaren Speicher (flash rom) liegen. Nur veränderliche bzw finale
Variablen liegen im oft knappen Hauptspeicher. Das führt zu einer
reaktiven App mit geringerer Leistungsaufnahme.

C/C++ Entwickler können sich const-Daten als DATA Speichersegment
vorstellen, BSS sollte gemieden werden und finals und variable Daten liegen
auf dem HEAP.
