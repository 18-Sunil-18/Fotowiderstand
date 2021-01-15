# Fotowiderstand 
Helligkeitssensor auslesen – Wenn es dunkel wird, geht ein Licht an

Aufgabe: Eine LED soll leuchten, wenn es dunkel wird bzw. wenn ein Fotowiderstand abgedeckt wird.

Jetzt wird’s etwas komplizierter! Erst durchatmen, neues Getränk holen!

Material: Arduino / eine LED / ein Widerstand mit 200 Ohm / ein Widerstand mit 10K Ohm / Breadboard / Kabel  / Fotowiderstand


Lerninhalt: Spannungen auslesen und ausgelesene Werte per „serial monitor“ darstellen.

6.1 Spannungen auslesen

Der Mikrokontroller soll über einen Fotowiderstand auslesen, wie hell es ist. Dazu nutzt man ein einfaches physikalisches Prinzip. Wenn in einem Stromkreis zwei Verbraucher hintereinander angeschlossen sind (Reihenschaltung), dann „teilt“ sie sich auch die gemeinsam anliegende Spannung. Ein Beispiel: Zwei gleiche Lampen sind in Reihe geschaltet und es wird eine Spannung von 6 Volt angelegt. Dann kann man mit einem Spannungsmessgerät feststellen, dass an den Lampen jeweils nur 3 Volt anliegen. Wenn zwei ungleiche Lampen angeschlossen werden (Eine hat einen geringeren Widerstand), dann kann man zwei unterschiedliche Spannungen an den beiden Lampen messen, bspw. 1,5 Volt und 4,5 Volt.

Ein Fotowiderstand ändert seinen Widerstand in Abhängigkeit der Lichtstärke. Diesen Effekt nutzt man, um anhand der an ihr anliegenden Spannung einen Wert für Helligkeit bzw. Dunkelheit in Form von verschiedenen Spannungen abzulesen. Damit man hier überhaupt eine Spannungsteilung erzeugen kann, schließt man den Fotowiderstand und einen Widerstand (1 – 10 K Ohm, je nach verwendetem Fotowiderstand. Der Widerstand sollte einen ähnlichen Widerstandswert wie der Fotowiderstand haben) in Reihe an und verbindet sie mit 5 Volt und der „Erdung“ (Ground / GND) – siehe Aufbau.

Das Mikrocontroller-Board ist in der Lage, analoge Signale (Spannung) zu messen und diese zu verarbeiten. Dies geschieht mit den analogen Eingängen auf dem Board. Dieser wandelt den gemessenen Spannungswert in eine Zahl um, die dann weiter verarbeitet werden kann. 0 Volt entspricht dabei der Zahl 0 und der höchste Messwert 5 Volt entspricht der Zahl 1023 (0 bis 1023 entspricht 1024 Zahlen = 10 Bit). Beispiel: Es wird eine Spannung von 2,5 Volt gemessen, dann liefert der Mikrokontroller den Wert 512 (1024 : 2).

6.2 Der „serial monitor“

Der „serial monitor“ ist ein wichtiger Bestandteil der Arduino-Software. Mit diesem „serial monitor“ kann man sich am PC Daten anzeigen lassen, die das Mikrocontroller-Board an den PC sendet (Zahlen oder Texte). Das ist sehr sinnvoll, da man nicht immer ein LCD Display am Mikrocontroller angeschlossen hat, auf dem man bestimmte Werte ablesen könnte.

In diesem Sketch wird der „serial monitor“ verwendet, um die Werte anzeigen zu lassen, die das Board von dem Fotowiderstand einliest.

Wozu ist das sinnvoll? Mal angenommen, die LED soll erst bei beginnender Dunkelheit anfangen zu leuchten. Dann muss es im Sketch einen Bereich geben, der die Funktion hat: „Wenn der Wert des Fotowiderstandes den Wert x unterschreitet, dann soll die LED leuchten“. Dazu müsste man wissen wie groß der Wert x bei beginnender Dämmerung ist.

Lösung: Ich sende den ausgelesenen Wert „x“ der Spannung an dem Fotowiderstand bei entsprechender Helligkeit (bspw. Dämmerung) an den „serial monitor“ und lasse ihn mir dort anzeigen. Mit diesem Wissen kann ich später das Programm in der folgenden Form abändern. „Wenn der Spannungsausgabewert des Fotowiderstandes einen Wert von „x“ unterschreitet, dann schalte die LED an.“


Weitere Infos unter: https://funduino.de/
