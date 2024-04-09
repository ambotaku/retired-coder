+++
weight = 1
title = 'Die nächste Programmiersprachen-Generation'
date = 2024-04-08T11:57:44+02:00
draft = false
+++

[Gemini](https://gemini.google.com/app/3b52c1970102fa8f)
sagt mir, das es derzeit 350 aktiv genutzte Programmiersprachen gibt -
und immer noch kommen neue dazu, die allerdings
etliche Jahre brauchen, um sich zu etablieren - oder was
wahrscheinlicher ist - wieder vergessen zu werden.

Das zeigt eindrucksvoll die Popularität der Sprachen von 1965 bis heute in diesem Zeitraffer- Video:

{{< youtube qQXXI5QFUfw >}}

Dabei wechselten als populärste Sprachen Fortran, Pascal, C, Java
bis heute Python die Führungsrolle - dicht gefolgt von
Javascript, einer Sprache, die viele Jahre nur für nervige Webseiten-
Gimmicks geeignet schien. Das in den frühen 1990ern (wie zuvor mal
der einstige Favorit Pascal) für die Lehre
entwickelte Python taucht in der Popularitätsliste erst 2000 auf,
um erst ab 2011 rasant durchzustarten, um heute auch schon nicht
mehr als "modern" zu gelten.

Neue Sprachen wie Kotlin, Swift, Go, Rust und Dart gehören noch nicht
zu den Favoriten und man kann nicht erahnen, welche davon sich
durchsetzen, gerade weil sie viele Ähnlichkeiten besitzen.

Aber was fehlt Programmiersprachen, damit sie unpopulär werden?
Neue Anforderungen erfordern andere
[Paradigmen](https://de.wikipedia.org/wiki/Programmierparadigma) -
das zeigen die Schwächen der einstigen Favoriten.

### von imperativer zu modularer Programmierung

**Fortran** und **Cobol** waren noch **imperativ**; Programme wahren schlicht
Befehlsfolgen, Daten (Variablen) spielten eine Nebenrolle, die
Programmlogik liess kaum Struktur erkennen und große Programme
waren nicht mehr durchschaubar (Spaghetti-Code).

Besser wurde es mit **Algol** bzw. dem nächsten Favoriten **Pascal**.
**Prozedurale** und später **modulare Programmierung** erlaubten einen
höheren Abstraktionsgrad für Code und Daten und überschaubare Gliederung
von sehr großen Projekten, was wegen immer größerer Hardwareleistung
und dadurch möglichen größeren Programmen auch notwendig wurde.

Die Sprache **C** brachte hinsichtlich Modularisierung (verglichen mit den
Pascal-Nachfolgern **Modula-2** und **Ada**) nichts neues, war
aber hardwarenah genug, um Assembler (imperativen Maschinencode) weitgehend
auch aus den Betriebssystemen zu verdrängen.

### objektorientierte Programmierung und Entwurfsmuster

Dann kam mit graphischen Bedienoberflächen bei dem Entwicklungssystem
 **Smalltalk** das objektorientierte Paradigma und führte zum Durchbruch von
  **Java** und **C++**. Die Grundideen waren die Kapselung von Verhalten
(Funktionen) und Eigenschaften (Attributen) in **Klassen** genannten Vorlagen
die sich in Vererbungshierarchien strukturieren lassen, um **polymorphe**
Objekte zu erzeugen, so wie in dem [Duck Test](https://en.wikipedia.org/wiki/Duck_test)
genannten Zitat:

If it looks like a duck, swims like a duck, and quacks like a duck,
then it probably is a duck.

Das bedeutet, Objekte auch unterschiedlicher Klassen sind austauschbar,
 wenn sie sich gleich verhalten

So erlauben halbwegs moderne Sprachen wie **Python**, **Groovy** und **Ruby** mit
[Duck-Typing](https://de.wikipedia.org/wiki/Duck-Typing) Polymorphie über das 
Klassenkonzept hinaus.

Die Objektorientierung ermöglichte als noch höhere Abstraktion eine Definition von
[Entwurfsmustern und Pattern Languages](https://de.wikipedia.org/wiki/Entwurfsmuster)

### von funktionaler zu reaktiver Programmierung

[Funktionale Programmierung](https://de.wikipedia.org/wiki/Funktionale_Programmierung)
kennt nicht nur - wie bereits die prozedurale Programmierung - Funktionen per se, sondern
ermöglicht Funktionen auch Funktionen als Funktionsparameter oder Ergebnis
(Funktionen als "first class objects").

Vor allem
aber muss eine Funktion bei Aufruf mit gleichen Parametern auch **immer** das gleiche Ergebnis liefern.
Das verbietet ein Kapseln von Attributen über einen Aufruf hinaus - was ja gerade bei
der Objektorientierung ausdrücklich erwünscht ist.

Interessant ist, dass die zweitälteste
Programmiersprache **Lisp** bereits funktionales Coding erlaubte, aber nicht sehr populär
wurde - bis sich mit dem durch eine **Java** ähnliche Syntax verbogenem **Javascript** funktionale
Programmierung auch auf breiter Basis durchsetzte.

Rein funktionale Sprachen kennen wegen der Zustands-Problematik keine Variablen,
sondern nur Konstanten.
Dies Problem mit klassischer Objektorientierung wurde mit immer stärkeren Prozessoren durch
mehrere Rechenkerne, Vernetzung und Cloud-Computing zu einem großem Problem. Sobald mehrere
nebenläufige Funktionen sich Variablen teilen, benötigt man Synchronisations-Maßnahmen
wie **Locks** bzw. [Mutexe](https://de.wikipedia.org/wiki/Mutex), die unerwünscht veränderte Daten
verhindern. Python (wie auch Ruby) hatte bis vor kurzem nur einen *global interpreter lock* ,
der stabilen nebenläufigen Code sehr ineffizient machte.

Bei sauberer funktionaler Programmierung treten solche Probleme aber gar nicht erst auf, weshalb
Sprachen des Internet-Zeitalters zunehmend darauf aufsetzen. Heute haben gerade Mobilgeräte Prozessoren
mit vielen eher leistungsschwachen Rechenkernen, um aufwändige Apps effektiv auszuführen.
Das würde ohne ein funktionales Vorgehen leicht zu sehr vielen Performance kostenden Locks oder
gar die Stabilität gefährdenden [Deadlocks](https://de.wikipedia.org/wiki/Deadlock_(Informatik)) führen.

Auch erwartet man gerade von mobilen Apps ein [reaktives](https://de.wikipedia.org/wiki/Reaktive_Programmierung)
Verhalten, d.h. jeder Klick und
jede Eingabe soll möglichst automatisch alles sonst noch angezeigte aktualisieren. Das führt
zu sehr komplexen Datenströmen und hoch dynamischen Abläufen, bei denen Kapselung objektorientierter
Art eher im Weg steht - vor allem wenn bei Netzverbindungen die Verfügbarkeit externer Daten kaum bestimmbar ist.

Solche Datenströme lassen sich aber gut durch verkettete und verschachtelte
Funktionen modellieren. Dabei hat zuerst Javascript mit Frameworks wie
[React](https://react.dev/learn) und [RxJS](https://rxjs.dev/) viel Popularität eingebracht.

Und damit kommen wir schlussendlich bei den eingangs erwähnten reaktiven Programmiersprachen an.
Diese sind multiparadigmatisch und unterstützen alle bisher hier aufgeführten Paradigmen
in ihrem Sprachumfang, weil sie die Entwicklung moderner, reaktiver Apps zum Ziel haben.
Sprachen, die sich kaum an das reaktive Umfeld anpassen, landen also irgendwann in einer Nische,
obwohl sicher auch alte COBOL und FORTRAN Programme gepflegt werden müssen.

### deklarative Programmierung

Bei der deklarativen Programmierung definiert der Entwickler eine gewünschte Regel oder
Gleichung und die Herleitung oder Ergebnisbildung geschieht durch die Software.

Das populärste Beispiel sind wohl Datenbank-Abfragesprachen wie SQL. Auch Expertensysteme und
die Programmiersprache **Prolog** können hier genannt werden.

Sofern man das als Programmierung versteht, kann man auch alle Auszeichnungssprachen
wie HTML, XML, XAML, SGML, LaTeX, JSON, Yaml, ... als deklarative Programmierung betrachten.

Letztlich schließt sich hier der Kreis weil sich mit funktionaler Programmierung auch gut
deklarativ formuliert werden kann. Die an SQL angelehnte Abfragesprache LINQ als Bestandteil
der Sprache **C#** nutzt auch bereits Techniken funktionaler Programmierung:

{{< highlight csharp >}}
int[] numbers = [ 5, 10, 8, 3, 6, 12 ];

//Query syntax:
IEnumerable<int> numQuery1 =
    from num in numbers
    where num % 2 == 0
    orderby num
    select num;
{{< /highlight >}}

Wie funktionale Programmierung in Javascript durch eine reaktive Library wie RxJS
aussehen kann, zeigt dieses Beispiel:

{{< highlight javascript >}}
const observable = Rx.from([1, 2, 3, 4, 5]);

// Verdopplung jedes Werts
observable
  .pipe(
    // map: Funktion auf jeden Wert anwenden
    Rx.operators.map((x) => x * 2),
    // filter: Nur gerade Werte durchlassen
    Rx.operators.filter((x) => x % 2 === 0),
    // toArray: Observable in Array konvertieren
    Rx.operators.toArray(),
  )
  .subscribe((result) => {
    console.log(result); // Ausgabe: [2, 4, 6, 8, 10]
  });
  {{< /highlight >}}

In diesem Beispiel:

- Rx.from([1, 2, 3, 4, 5]) erstellt ein Observable aus einem Array.
- pipe verkettet mehrere Operatoren zu einer Sequenz.
- map wendet eine Funktion auf jeden Wert im Observable an. In diesem Fall wird jeder Wert verdoppelt.
- filter lässt nur Werte durch, die einer bestimmten Bedingung entsprechen. In diesem Fall werden
  nur gerade Werte durchgelassen.
- toArray konvertiert das Observable in ein Array.
- subscribe abonniert das Observable und führt die angegebene Funktion für jedes Ergebnis aus.

RxJS Datenströme können auch verzweigen oder mit anderen Strömen verknüpft werden, sodass
ein Ereignis wie ein Tastendruck alle Filter und Berechnungen durchläuft, die zur
Aktualisierung von Anzeigen oder externen Dateien führt.

### Ausblick

Diesen Rundgang durch für App-Entwicklung wichtige Paradigmen habe ich
vor meine Beiträge zu Flutter und vor allem der Sprache **Dart** geschaltet,
weil das zum Verständnis der Sprache und der damit zu lösenden Probleme helfen kann.

Bemerkenswert bei Dart ist, dass zum Coding der Flutter Bedienoberflächen
keine Auszeichnungssprache (.NET braucht dazu XAML) nötig ist, weil Dart wegen
seinem pur funktionalem Paradigma (wie konstante Klassen) auch vollständig
deklarativ sein kann. Verwendet man dagegen eine Auszeichnungssprache, die
noch nicht einmal Turing-vollständig ist (z.B. keine Fallunterscheidungen
und Schleifen kennt), verkompliziert sich auch das Design.

So etwa sieht das detaillierte Design eines Button-Widgets in Dart/Flutter als
konstante Klasse aus:

Eine ```onPressed``` - Funktion und die Beschriftung ```text``` werden als Parameter
übergeben, die ```fontSize``` ist optional. Alles andere ist für einen solchen
Button-Typ festgelegtes Design.

{{< highlight dart>}}
class CalculatorButton extends StatelessWidget {
  const CalculatorButton(
      {super.key,
      required this.onPressed,
      required this.text,
      this.fontSize = 32});

  final void Function() onPressed;
  final String text;
  final double fontSize;

  @override
  Widget build(BuildContext context) {
    return TextButton(
      onPressed: onPressed,
      style: ButtonStyle(
        alignment: Alignment.center,
        shape: MaterialStateProperty.all<RoundedRectangleBorder>(
          RoundedRectangleBorder(
            borderRadius: BorderRadius.circular(24.0),
            side: const BorderSide(color: Colors.red),
          ),
        ),
        backgroundColor: MaterialStateProperty.resolveWith<MaterialColor>(
            (Set<MaterialState> states) {
          if (states.contains(MaterialState.hovered)) return Colors.teal;
          return Colors.indigo;
        }),
      ),
      child: Text(
        text,
        style: TextStyle(
            fontSize: fontSize,
            fontWeight: FontWeight.bold,
            color: Colors.amber),
      ),
    );
  }
}
{{< /highlight>}}
