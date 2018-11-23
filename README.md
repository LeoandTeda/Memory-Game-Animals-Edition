# Informatik Projekt Nr.1: Memory Game (Animals Edition)
*von Teda und Leonard, 12e*

## Inhaltsverzeichnis
* [Programm](#Programm)
* [Spielidee](#Spielidee)
* [Aufbau](#Aufbau)
  * [Grundprinzip](#Grundprinzip)
  * [Karten sortieren](#Sortieren)
  * [Karten umdrehen](#Umdrehen)
 * [Extras](#Extras)
  * [Variablen](#Variablen)
  * [Punktesystem](#Punktesystem)
  * [Begleitende Figuren](#Figuren)
  * [Startbildschirm](#Startbildschirm)
  * [Endbildschirm](#Endbildschirm)


## Das Programm <a name="Programm"></a>

![image](https://user-images.githubusercontent.com/42579285/48960806-160b1200-ef70-11e8-82f8-a4498ecd9050.png)


Um unser Projekt zu programmieren haben wir das Programm snap! genutzt, da dies besonders für Anfänger gut geeignet ist, da keine Kenntnisse in einer Programmiersprache für die Verwendung vorausgesetzt werden. Snap vereinfacht dabei den Quellcode in Blöcke, welche je nach belieben zusammengeheftet werden können. Dabei werden Fehler anders als beim normalen programmieren schnell erkannt und es werden zudem viele Tipps sowie Anleitungen gegeben. Snap beruht dabei auf einer sehr visuellen Programmiersprache.


## Die Spielidee <a name="Spielidee"></a>

Der Spieleklassiker Memory lässt sich, mit einigem Zeitaufwand und logischen Denken in ein online game umwandeln. Wir haben uns dazu entschieden ein Sologame zu programmieren, dass für jede Altersgruppe geeignet ist.

Dafür muss man, je nach gewünschter Kartenanzahl entsprechend viele Sprites anlegen. Spirtes sind in diesem Fall einzelne Grafikdateien, welche unterschiedliche Symbole oder Icons enthalten.

![unbenannt](https://user-images.githubusercontent.com/42579285/48960973-6cc51b80-ef71-11e8-9005-e67377dd267e.png)

In unserem Fall haben wir uns für 20 Karten, also 10 Paaren, entschieden. Nun können beliebige Motive für eine einheitliche Rückseite und 10 unterschiedliche Motive, möglicherweise mit einem gemeinsamen Thema wie beim klassischen Original, für die Vorderseite ausgewählt werden. Diese Bilder werden in den Bereich Costumes eingefügt und wenn nötig umbenannt. Anschließend wird der erste Block hinzugefügt um die Größe der Motive anzupassen. Der Befehl set size to …% muss nur noch durch die gewünschte Größe vervollständigt werden.

![unbenannt](https://user-images.githubusercontent.com/42579285/48961170-b9f5bd00-ef72-11e8-97e4-339291633b87.png)
![unbenannt](https://user-images.githubusercontent.com/42579285/48961086-3d62de80-ef72-11e8-9ee7-3127360d4dee.png)


## Der Aufbau <a name="Aufbau"></a>

### Das Grundprinzip <a name="Grundprinzip"></a>

#### Karten sortieren <a name="Sortieren"></a>

Der nächste Schritt ist es die mittlerweile als Karten erkennbaren Sprites einer bestimmten Position zuzuordnen, so dass eine einheitliche Anordnung entsteht. Falls die Größe der Motive verändert werden soll kann man den Befehl set to size nutzen und sie auf eine einheitliche Größe bringen. Dies soll wie einige weitere Punkte direkt bei Spielbeginn passieren, also wird es unter den Operator when (grüne Flagge) clicked gesetzt. Übergangsweise können die Karten manuell an eine geeignete Stelle gezogen werden, da es nicht sinnvoll ist den Karten eine konkrete Position zuzuordnen, wenn man im weiteren Verlauf die Kartenanordnung mischen möchte nach einem vollendeten Spiel.

![unbenannt](https://user-images.githubusercontent.com/42579285/48961040-f248cb80-ef71-11e8-97b4-4d8729ba9c2f.png)

#### Karten umdrehen <a name="Umdrehen"></a>

Der Operator switch to costume … wird hinzugefügt und das Motiv der Rückseite ausgewählt, damit zu Beginn alle Karten das selbe Motiv zeigen. 
Als nächstes soll eine Karte beim Anklicken das Motiv wechseln, sich also optisch “umdrehen”. Dies wird durch den Operatoren Block when I am (clicked) -> next costume ermöglicht. Eine weitere Möglichkeit wäre es statt next costume , switch to costume … zu verwenden. Dies hat in diesem Fall den selben Effekt.
Damit sichergestellt ist, dass nur zwei Karten aufeinmal umgedreht werden können, wird die Variable AufgedeckteKarte wie die meisten anderen auch am Anfang unter Script der Bühne auf null gesetzt. Daraufhin wird bei jeder einzelnen Karte unter dem Operator when I am clicked and if AufgedeckteKarte < 2 das bereits bestehende next costume und das neu hinzuzufügende change AufgedeckteKarte by 1 eingefügt.


### Extras  <a name="Extras"></a>

Nachdem das Grundprinzip des Spiels komplett funktioniert, können jetzt weitere Funktionen hinzugefügt werden, die den Spielverlauf interessanter gestalten sollen.
Zu diesen gehören unter anderem eine Figur, die den Spieler durch das ganze Spiel begleitet, ein Punktesystem und einen Timer um einen gewissen Anreiz zu schaffen sich zu verbessern, da es keinen Gegenspieler gibt. Weitergehend lassen sich Start und Endbildschirme programmieren.


#### Variablen <a name="Variablen"></a>

Beim programmieren dieses Spiels ist es sinnvoll verschiedenste Variablen zu nutzen. Die Namensgebung ist dabei individuell anpassbar und keinesfalls eine Vorgabe.

![unbenannt](https://user-images.githubusercontent.com/42579285/48961234-43a58a80-ef73-11e8-9106-cdb801df174f.png)

#### Punktesystem <a name="Punktesystem"></a>

Die Variable Punkte ist essenziell für ein funktionierende Punktesystem. Zu Spielbeginn soll bereits ein Spielstand von (15) Punkten vorhanden sei, damit der Spieler bei nicht direkt eintretenden Glück nicht mit einem negativen Spielstand startet. Also wird der Befehl set Punkte to (15) unter Scripts der Bühne, später gefolgt von weiteren Variablen, unter when (grüne Flagge) clicked gesetzt. Um den Punktestand bei finden eines Paares zu erhöhen wird unter den Bedingungsschaffenden Block der Befehl change Punkte by (3) hinzugefügt. Das selbe muss für den Fall, dass kein Paar gefunden wird geschehen, mit der Abweichung, dass statt einer positiven Zahl eine negativen Zahl, wenn möglich kleiner als eins, um den Endstand ins Positive zu bringen, eingesetzt wird.


#### Begleitende Figur <a name="Figuren"></a>

Um die begleitende Figur lebendiger zu gestalten ist es sinnvoll mehrere neue Sprites anzulegen, die verschiedene Emotionen dieser Figur zeigen. Hierfür werden wie zuvor bei den Karten die gewünschten Motive einzufügen. Es besteht die Möglichkeit für die zwei verschiedenen Ausgänge (Paar/ kein Paar) verschiedene Motive passend dazu passend auszuwählen. Diese sollen nicht dauerhaft sichtbar sein, also wird unter den Operatoren Block when (grüne Flagge) clicked nach der Einstellung der Größe, set to size, der Befehl hide eingefügt. Wann sie sich zeigen sollen wird bei den einzelnen Karten durch den Befehl tell (begleitender Figur)… to 
1. show
2. say … (je nach Emotion etwas positives zu dem Spieler) vor … sechs (hier ist es sinnvoll die Zeit, die die Figur sichtbar ist auf eine Sekunde zu beschränken, wenn ein Paar gefunden wurde und bei zwei unterschiedlichen Karten dem Spieler genug Zeit zu geben, um sich die Position der Motive einzuprägen)
3. hide

Eine “wartende” Figur kann zusätzlich angelegt werden, diese hat allerdings außer dem ersten Block, der über die Größe und Sichtbarkeit entscheidet einen weiteren Block, der sich anders als bei den beiden vorherigen Figuren noch im selben Script befindet. Diese Figur soll den Spieler dazu anregen etwas schneller zu spielen und die eigene Bestzeit zu schlagen. In den Operator when [ ] wird Time mit 75 gleichgesetzt und eingesetzt. Daraufhin folgen die Befehle 1. show
2. say … for … sechs 
3. hide
Somit ist diese Figur nur einmalig für ein paar Sekunden sichtbar im gesamten Spiel.


#### Startbildschirm <a name="Startbildschirm"></a>

![unbenannt](https://user-images.githubusercontent.com/42579285/48960865-89ad1f00-ef70-11e8-9988-c1d890fe1fdb.png)

Ein simpler Startbildschirm mit nur einer Funktion, dem Start Button, lässt sich verwirklichen, indem ein einfacher Hintergrund, der den Titel des Spiels zeigt unter costumes der Bühne eingefügt wird, der bei Anklicken der grünen Flagge sichtbar wird. Ein neuer Sprites wird mit dem Bild eines Startbuttons versehen und wie bei allen anderen Sprites wird die Größe angepasst. Beim Anklicken des Buttons soll das vorher programmierte Spielfeld sichtbar werden. Deswegen werden die Variablen der einzelnen Karten jeweils in den Befehl tell (...) to show, unter der Vorraussetzung when I am clicked eingefügt.
Der Button selbst und der Hintergrund sollen logischerweise nicht mehr angezeigt werden. Dies wird durch tell Bühne to switch costume to Turtle und hide möglich, die ebenfalls zum selben Block hinzugefügt werden.


#### Endbildschirm <a name="Endbildschirm"></a>

Das Spielende, also wenn alle Paaren aufgedeckt wurden, soll einen Endbildschirm mit verschiedenen Fortfahrmöglichkeiten hervorrufen. Zuerst wird ein passendes Bild gebraucht, dass entweder im Internet gefunden oder selbst gestaltet werden kann, dass Anweisungen für den Fall, dass der Spieler weiterspielen oder zurück zum Menü möchte anzeigt. Dieses wird bei costumes eingefügt. Um ein eindeutiges Spielende festzustellen wird die Variable Victory angelegt, die sich bei jeder einzelnen Karten im Befehl change Victory by 1 unter der Bedingung des gefundenen Paares befindet. Somit ergibt sich bei Vollendung der Runde ein Wert von 20 für Victory. Im Script der Bühne muss nun ein neuer Block zusammengefügt werden, bestehend aus 
when Victory = 20
switch to costume Endbildschirm 
show Variable Score 
set Score to Punkte
hide Variable Punkte

Die Variable Score unterscheidet sich nicht von Punkte und ist jegendlich für den Endbildschirm von Bedeutung, da die Punktzahl dort mittig im Bild erscheinen soll und nicht wie im vorhergehenden Spiel am oberen Rand.

Um die oben angesprochenen Möglichkeiten durchzuführen können beliebige Tasten festgelegt werden, die das darüber geschilderte Szenario verwirklichen. 
Um zurück zum Startbildschirm zu kommen wird die ausgewählte Taste in den Operator when … key pressed eingefügt, gefolgt von switch to costume Home (Menü) und tell (beliebiger Variabel (für  jede einzelnene Karte muss ein eigener Befehl eingefügt werden)) to hide. So werden die “versteckten” Karten erst wieder sichtbar, wenn der Startbutton angeklickt wird.


