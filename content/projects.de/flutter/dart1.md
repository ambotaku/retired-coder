+++
weight = 2
title = 'Wie und warum Dart entstand'
date = 2024-04-09T10:32:20+02:00
draft = false
+++

In den 2000ern entdeckte man das Potential von Javascript
als sehr flexible funktionale und objektorientierte Sprache,
die in jedem modernen Browser vorhanden war - leider noch als einzige
Möglichkeit zur Client-Programmierung. Statt nerviger Effekthascherei
geriet nun [Ajax](https://de.wikipedia.org/wiki/Ajax_(Programmierung))
in den Focus der Entwickler und Webanwendungen verteilten sich in
[Frontend und Backend](https://de.wikipedia.org/wiki/Frontend_und_Backend)
und immer leistungsfähigere Javascript-Bibliotheken realisierten auch
Client-seitig objektorientierte Entwurfsmuster wie etwa
[Model-View-Presenter](https://de.wikipedia.org/wiki/Model_View_Presenter),
um im Browser reaktive Web-Anwendungen zu ermöglichen.

Da mit dem wachsenden Umfang solcher Bibliotheken Javascript immer
unübersichtlicher, schlecht wartbar und damit fehleranfällig wurde,
entstanden Compiler für [statisch typisierte](https://de.wikipedia.org/wiki/Statische_Typisierung)
Sprachen, vor allem weil Javascript Datentypen eher schlampig behandelt,
was dann leider erst bei Programmausführung z.B. durch fehlschlagende
automatische Typumwandlungen auffällt. Besonders bei Kommunikation mit
einem sauber typisierten Backend wirkt das fatal.

So entwickelte Microsoft 2012 die Sprache [TypeScript](https://de.wikipedia.org/wiki/TypeScript).
welche syntaktisch stark an Microsoft's [VisualJ++](https://de.wikipedia.org/wiki/Visual_J%2B%2B) -
Nachfolger C# erinnert.
(Federführung hatte bei beidem [Anders Hejlsberg](https://de.wikipedia.org/wiki/Anders_Hejlsberg),
der zu Beginn seiner Karriere auch der Entwickler von Turbo-Pascal war).

Ab 2011 entwickelte ein Google-Team um [Lars Bak](https://de.wikipedia.org/wiki/Lars_Bak_(Informatiker))
 dann Dart.

{{< notice info>}}
Lars Bak ist ebenso wie Hejlsberg Däne und auch Designer Google's V8- Javascript-Engine,
die neben dem Chrome Browser auch alle NodeJS Server antreibt.
{{< /notice >}}

Dart entfernte sich weiter von JavaScript und sollte (?) dessen Nachfolge
als Browser-Programmiersprache werden. Durch Einflüsse von C# wie auch TypeScript ähnelt
 Dart syntaktisch TypeScript und C# so stark, das C# Entwickler sich gut einarbeiten können.

So wurde Dart auch die Sprache von Google's Webfrontend-Framework [Angular](https://angulardart.xyz/),
das aber wohl in seiner [TypeScript-Variante](https://angular.io/) populärer ist, denn TypeScript
ist 100% kompatibel zu dem heute in Browsern implementierten JavaScript.

Um Dart-Anwendungen ins Web zu bringen, musste der Dart-Transpiler also für Browser brauchbares
Javascript kompilieren, das reichte für einen Erfolg von Dart aber noch nicht.

Für Mobilanwender sind Web-Anwendungen zweite Wahl, sie bleiben nicht installiert wie Apps
und müssen neu geladen werden, sobald der Cache bereinigt wurde. Die Entwicklung von Apps sowohl
für iOS als auch Android zusätzlich zu einer Web Client-Server Anwendung ist aber sehr aufwändig,
weil die Plattformen so unterschiedlich sind - schon was die Programmiersprachen angeht.
Das erfordert meist sogar unterschiedliche Entwicklerteams.

iOs Apps müssen in Apple's Programmiersprache [Swift](https://developer.apple.com/swift/)
 geschrieben werden (zuvor noch Objective C), Android Anwendungen entstehen in
[Kotlin](https://kotlinlang.org/) (vormals Java). Möchte man dann noch MS-Windows Apps haben, landet man
schließlich auch noch bei [Visual C++](https://de.wikipedia.org/wiki/Visual_C%2B%2B).

Der Anspruch von Flutter ist nun, den zu jeder dieser Plattform passenden Code aus einem gemeinsamen
Dart-Quellcode zu transpilieren, in den Maschinencode des Ziels zu kompilieren und darauf auszubreiten.

Für die Benutzerschnittstellen verwendet Flutter [Google Material Design](https://m3.material.io/) oder
```Cupertino``` bei Apple-Geräten (iOs / macOS). Flutters Widgets liegen alle als Dart-Quellcode vor,
sodass sie eine gute Grundlage für ein eigenes Design bilden.

Flutter und Dart kommen als gut ausgestattete Entwicklungsumgebung, zusätzlich empfiehlt sich noch Git
und VisualStudio Code als IDE. Zur Erstellung von Apps für Android, iOS, macOS und Windows werden
allerdings noch die Entwicklungstools der jeweiligen Platform gebraucht, um binären Code für diese
erstellen zu können.

Im nächsten Artikel geht es dann endlich um die Sprachelemente von Dart.
