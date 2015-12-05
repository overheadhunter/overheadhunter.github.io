---
layout: post
title:  "LaTeX: Verhalten von \\ac bei erster Benutzung"
date:   2012-10-17
tags: [LaTeX, ac, acl, acronym]
---
Ich schreibe zur Zeit an meiner Bachelorarbeit und habe die Vorgabe von der FH, dass Abkürzungen bei erster Verwendung wie folgt aussehen müssen:

> FH (Fachhochschule)

Das Problem ist nur, dass die Standardimplementierung des Befehls \ac beim Einführen einer Abkürzung (also bei erster Benutzung des Befehls im Dokument) folgendes generiert:

> Fachhochschule (FH)

Man kann sich nun sicher streiten, welche der beiden Wege richtig ist. Fakt ist, ich muss den zuerst genannten Weg nutzen. [Orders is Orders](http://www.imdb.com/title/tt0425210/quotes?qt=qt0441421).

Wie kriegt man jetzt also LaTeX dazu, das zu tun, was ich will? Eine Nähere Betrachtung des Acronym-Packages hat ergeben, dass bei erster Benutzung des `\ac`-Befehls `\acf` aufgerufen wird. Und diesen kann man sich ganz einfach umdefinieren. Der Vollständigkeit halber sollte man das auch für die Plural-Version der Abkürzung machen.

Fügt man zu Beginn seines Dokuments also die folgenden zwei Zeilen ein, werden die Befehle `\acf` und `\acfp` umdefiniert, um erst die Kurzform und dann die ausgeschriebene Form der Abkürzung in Klammern auszugeben. Wichtig ist desweiteren, die Abkürzungen danach als genutzt zu markieren. Dies geschieht mit dem Befehl `\acused`.

```tex
\renewcommand{\acf}[1]{\acs{#1} (\acl{#1})\acused{#1}}
\renewcommand{\acfp}[1]{\acsp{#1} (\aclp{#1})\acused{#1}}
```
