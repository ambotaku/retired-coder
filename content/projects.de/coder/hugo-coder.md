+++
weight = 1
draft = false
title = 'Webseiten generieren mit Hugo & Coder'
date = 2024-04-03T21:32:15+02:00
+++

Blogs und persönliche Webseiten werden häufig mit Content Management
Systemen ([CMS](https://de.wikipedia.org/wiki/Content-Management-System)) wie z.B. [WordPress](https://de.wikipedia.org/wiki/WordPress) erstellt. Ich verwendete dafür bisher gern [DokuWiki](https://de.wikipedia.org/wiki/DokuWiki).

CMS-Anwendungen erlauben Bearbeitung der Seiten direkt mit der Anwendung, die auf dem Webserver läuft. Das erstellt höhere
Anforderungen an Server, als nur Seiten auszuliefern, denn zur Speicherung der Inhalte und Auslieferung der Seiten reicht ein Webserver allein nicht, denn der Server muss den Anwendungscode der Seiten ausführen, Benutzer und Sitzungen verwalten und benötigt dazu meist noch eine Datenbank (DokuWiki kommt ohne aus).

## Sicherheitsprobleme mit CMS

Das eigentliche Problem dabei ist aber die Sicherheit gegenüber Angriffen, Spam und Datendiebstahl, gerade wenn Benutzerkonten benötigt werden - denn diese sind meist Ziel von automatisierten Angriffen, welche dann schnell den gesamten Server lahm legen können.

Mein bei Strato gemieteter VServer erhält derzeit täglich über 10.000 Anmeldeversuche mit Zufalls- Anmeldedaten, was bis vor kurzem alle 2-3 Tage den Server abstürzen ließ. Das die Server-Firewall steuernde Bann-Programm [fail2ban](https://de.wikipedia.org/wiki/Fail2ban) verhindert inzwischen zwar die Abstürze, aber nicht die Zahl der Angriffsversuche und den Aufwand zur
Administration des Servers.

## Ein schlanker Webserver wie nginx reicht mir

Ich verwende für diesen Webauftritt nur noch den bekannten und kompakten  Webserver [nginx](https://de.wikipedia.org/wiki/Nginx) zur Auslieferung von mit dem Seitengenerator [Hugo](https://gohugo.io/) auf meinem Entwicklungs-Rechner aufgebauten Seiten. Das hat eine Reihe von Vorteilen, aber auch Nachteilen, die mir die Google's Gemini KI recht passend aufzählte:

### Vorteile von Webseitengeneratoren wie Hugo

- Geschwindigkeit: Statische Websites, die mit Generatoren wie Hugo erstellt werden, sind extrem schnell, da die Seiten bereits vollständig generiert und im HTML-Format vorliegen. Dies führt zu kurzen Ladezeiten und einer besseren Benutzererfahrung.

- Sicherheit: Da statische Websites keine dynamischen Inhalte oder Datenbanken benötigen, sind sie deutlich weniger anfällig für Sicherheitslücken. Es gibt keine laufenden Updates oder Patches, die installiert werden müssen.

- Skalierbarkeit: Statische Websites können einfach skaliert werden, da sie keine komplexen Serverumgebungen benötigen. Sie können von jedem Webserver bereitgestellt werden, auch auf kostengünstigen  Shared-Hosting-Plattformen.

- Wartung: Statische Websites sind im Vergleich zu dynamischen Websites deutlich wartungsarmer. Es gibt keine Datenbanken, die gepflegt werden müssen, und keine Plugins oder Themes, die aktualisiert werden müssen.

- Flexibilität: Hugo bietet eine Vielzahl von Themes und Plugins, die die Erstellung von individuellen Websites ermöglichen. Es gibt auch die Möglichkeit, eigene Themes und Plugins zu entwickeln.

- Einfachheit: Hugo ist einfach zu erlernen und zu verwenden. Die Bedienung ist intuitiv und es gibt eine große Community, die mit Rat und Tat zur Seite steht. *Anmerkung: Wie als Nachteil unten
auf geführt ist, kann die Umsetzung spezifischer Merkmale aber auch recht aufwändig und kompliziert werden.*

### Nachteile von Webseitengeneratoren wie Hugo

- Dynamische Inhalte: Statische Websites können keine dynamischen Inhalte wie Formulare, Kommentare oder Benutzeranmeldungen generieren. Für solche Funktionen ist ein Content-Management-System (CMS) erforderlich.
*Man kann aber soziale Medien wie [Disqus](https://disqus.com/) oder [Discord](https://www.rudderstack.com/integration/discord/integrate-your-hugo-site-with-discord/) in die eigenen Hugo-Seiten integrieren*

- Komplexität: Die Erstellung komplexer Websites mit Hugo kann fortgeschrittene Kenntnisse in HTML, CSS und JavaScript erfordern.
*Oder man sucht nach einem besser geeigneten Theme*.

- Einschränkungen: Hugo ist ein statischer Website-Generator und bietet daher nicht die gleichen Funktionen wie ein CMS. Es gibt beispielsweise keine Möglichkeit, Inhalte direkt im Webbrowser zu bearbeiten. *Das ist richtig - aber eine gut eingerichtete Entwicklungsumgebung bietet mehr Möglichkeiten als der dagegen meist recht primitive Editor eines CMS.*

- Fehlerbehebung: Fehler in der Konfiguration oder im Code von Hugo können zu schwerwiegenden Problemen führen. Die Fehlerbehebung kann schwierig sein, insbesondere für unerfahrene Benutzer. *Ein CMS ist schon in sich komplexer und kann Anwender mit auftretenden Problemen auch leicht überfordern. Ich denke mit Schrecken an meine Erfahrungen mit Typo3 vor einigen Jahren.*

## Wer oder was sind *Hugo \& Coder* ?

[Hugo](https://de.wikipedia.org/wiki/Hugo_(Software)) ist ein freier Webseitengenerator ([Apache Lizenz](https://de.wikipedia.org/wiki/Apache-Lizenz)) und wurde 2013 von Steve Francia mittels [Google Go](https://de.wikipedia.org/wiki/Go_(Programmiersprache)) entwickelt.

Anwender können Texte für Webseiten in der simplen Auszeichnungssprache [Markdown](https://de.wikipedia.org/wiki/Markdown) schreiben, darüber hinaus erlaubt Hugo in Texten aber auch
HTML-Code, *Templates* und *Shortcuts*. *Templates* bilden eine Art
Programmiersprache, mit der HTML-Layouts programmiert werden können, die dann z.B. als *Shortcuts* die Möglichkeiten von Markdown erweitern. *Templates* richten sich eher an erfahrene Web-Designer, die
fertige *Themes* ausbreiten, welche für andere Hugo-Nutzer das Erstellen eigener Webauftritte einfacher machen.

So bietet das für diese Webpage genutzte Theme [coder](https://github.com/luizdepra/hugo-coder/) etwa den Shortcut *notice*:

\{\{< notice example >\}\} Beispieltext \{\{< /notice >\}\}

der auf der Seite dann wie folgt gerendert wird:

{{< notice example >}} Beispieltext {{< /notice >}}

Aber Themes können als *Module* auch Go-Code enthalten und damit
die Möglichkeiten von Hugo noch stark erweitern.

Man sollte also bei der Auswahl eines Themes nicht nur auf dessen
Darstellungen achten, sondern schauen, ob es auch die gewünschte Funktionalität bietet.

Nicht viele Themes können mathematische Formeln wie ...
$$ % \f is defined as #1f(#2) using the macro
f\relax{x} = \int_{-\infty}^\infty
    f\hat\xi\,e^{2 \pi i \xi x}
    \,d\xi $$

... rendern. Dazu benötigt es eine Javascript-Bibliothek [KaTex](https://katex.org/). Katex ist ein Subset von [LaTeX](https://de.wikipedia.org/wiki/LaTeX), einem  Textsatzsystem, das der bekannte Informatiker Donald Knuth entwickelte. Nun, so etwas brauchen wohl vor allem Mathematiker und Physiker.

Informatiker schätzen da eher die Javascript-Bibliothek [mermaid](https://mermaid.js.org/#/) um Diagramme zu zeichnen:

{{< mermaid >}}
erDiagram
    CUSTOMER ||--o{ ORDER : places
    ORDER ||--|{ LINE-ITEM : contains
    CUSTOMER }|..|{ DELIVERY-ADDRESS : uses
{{< /mermaid >}}

Die Möglichkeiten von Hugo sind schier unbegrenzt. Sicher erfordert
Hugo und auch jedes Theme einigen oder sogar erheblichen
Einarbeitungs-Aufwand, denn die verwendete Syntax ist nicht immer aus einem Guß. Aber es braucht ja auch nicht jeder alles.

[Alle Themes](https://themes.gohugo.io/) haben eigene Schwerpunkte und Coder richtet sich schon an echte **Coder**, also Autoren mit einem Informatik-Hintergrund. Andre Themes haben social Media, Bildgalerien oder Videosammlungen als Schwerpunkt und sind für
populäre Zielgruppen geeigneter.

## Versionsverwaltung

Hugo besitzt selbst keine Verwaltung für damit erstellte Dokumentation. Aber Markdown-Quellcode kann wie jeder Programm-
Quellcode behandelt werden und Quellcode-Dokumentation geschieht deshalb schon länger in Markdown-Notation.

Das Versionsverwaltungs-Programm mit der größten Verbreitung ist heute das vom Linux-Entwickler Linus Torwalds ursprünglich für die Quellcode-Verwaltung von Linux entwickelte Programm [Git](https://de.wikipedia.org/wiki/Git). Deshalb wird Git auch gerne zur Speicherung von kompletten Webseiten-Quellen benutzt, auch wenn nur Textseiten bzw. Webseitentext gespeichert wird.

Gerade weil Webseiten aus vielen ganz unterschiedlichen Quelltexten bestehen (HTML, XML, Javascript, SQL, Java, Python, Perl, ...) die in versionierten Releases exakt zusammenpassen müssen, geht es ohne eine Versionsverwaltung wie Git kaum.

Auch eine gute Entwicklungsumgebung, die nicht nur Editoren, sondern auch Tests, Syntax- und Rechtschreibprüfung enthält,
ist von Vorteil. So eine Entwicklungsumgebung sollte recht modular und erweiterbar gestaltet sein - gerade im Umgang mit heterogenen
Umgebungen wie Hugo mit all seinen Erweiterungen. Auch Git
sollte da eine zentrale Rolle spielen.

Sehr verbreitet ist deshalb Microsoft's sehr flexible integrierte
Entwicklungsumgebung [VisualStudio Code](https://code.visualstudio.com/). Für VSCode, wie es meist abgekürzt genannt wird, gibt es
Extensions für nahezu alle Programmiersprachen, sonstige Quelltextformate (wie Markdown, Json, Yaml, ...), Editoren, Tests, und natürlich auch Git quasi als den Kitt, der alles zueinander passend zusammenhält.

Microsoft betreibt auch mit [GitHub](https://github.com/) die wohl größte Sammlung (Repository) von quelloffener Software, in der auch die meisten
bekannten Softwarehersteller öffentlich zugänglichen Code verwalten. Zu Github gehört auch die Seite [pages.github.com](https://pages.github.com/), die Webseiten wie die mittels Hugo erstellten bereitstellt.

## Kosten
Alle hier erstellten Werkzeuge und auch Repositories sind für nicht kommerzielle Nutzung kostenlos. Dabei hat der Nutzer eine Wahl zwischen unterschiedlichen OpenSource Lizenzen. Für kommerzielle Nutzung und nicht öffentliche Repositorien fallen allerdings Gebühren an und die Urheberrechts-Bestimmung der
eingesetzten Werkzeuge und aller Quellen müssen natürlich beachtet werden - aber das gilt für Webseiten Inhalte ja
immer.

## Wie geht es hier weiter ?
Ich habe diesem Projekt erst einmal die originale Dokumentation von Coder angehängt,
damit jede(r) entscheiden kann, ob er/sie dies Theme für eigene Web-Projekte brauchen kann.
