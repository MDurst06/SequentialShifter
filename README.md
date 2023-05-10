# Sim Racing Squential Shifter mit Arduino

Verfasser: **Manuel Durst 3CHIT**

Datum: **14.03.2023**

## 1.  Einführung

Equipment für einen Renn Simulator ist oft teuer, deswegen habe ich mich entschieden, selber eine Gangschaltung mit 3D Druck Komponenten, Schrauben, Arduino usw zu bauen. Hierfür habe ich inspiration an einer anderen Gangschaltung genommen, jedoch mehrere Dinge umgeändert und verbessert, damit er billiger, effizienter und robuster ist.

## 2.  Projektbeschreibung

Das Ziel des Projektes ist, eine sequentielle Gangschaltung zu bauen, die ermöglicht, den Hebel nach vorne und nach hinten zu drücken. Dabei werden Inputs an den Computer weitergeleitet und in Spielen umgesetzt.

## 3.  Komponenten

Für den Bau wurden folgende Komponenten eingesetzt:

1x Mainbody
1x Schaltwelle
1x unterblatte
4x Switch Spacers
1x Schaltknauf

1x M12 Schraube 75mm lang mit 2x M12 Nylock-Mutter
2x Switches
1x Arduino Pro Micro
1x Micro USB cable
4x M3 (Sechskantkopf) Schrauben 70mm lang
4x M3 Unterlegscheiben
4x M3 Nylock-Mutter
1x M10x1.5 Schraube ~65mm long
2x M10x1.5 (Sechskantkopf) 30-35mm lange Schraube
Drähte für das verlöten der Switches
Lötmaterial
2x Federn (1.4mm14mm Durchmesser, Länge: 40mm )
2x M12x1.75 Kugelstößel

## 4.   Arbeitsschritte

### Zusammenbau

Als erstes habe ich bereits vorhandene 3D-Modelle einer solche Gangschaltung genommen und so umgeändert, dass weniger Material beim Drucken verwendet wird und er am Ende robuster ist. Nach mehreren Stunden war alles fertig gedruckt und ich habe das Support-Material entfernt und die Teile geschliffen. Als nächstes habe ich alle Schrauben eingebaut und die Switches mit dem GND und GPIO Ports verbunden. Nachdem alle Teile eingebaut waren und die Teile verlötet wurden, konnte ich den Arduiono mit meinem PC verbinden und den Code hinaufspielen. Nachdem dieser ausgeführt wurde, wurden die Switches als Input eines Joystick erkannt und war somit für Spiele erkennbar.

### Code

Um den "Controller" zu realisieren wird die Joystick Library benötigt. Nachdem diese importiert wurde, werden die Pins deklariert und in einem Loop wird zugewießen, welche Inputs dem Computer weitergeleitet werden sollen.

    #include <Joystick.h>

    int upPin = 8;
    int downPin = 5;

    int Up = 0;
    int Down = 0;

    void setup() {
    pinMode(upPin, INPUT_PULLUP);
    pinMode(downPin, INPUT_PULLUP);

    Joystick.begin();
    }

    void loop( ){

    Up = digitalRead(upPin);
    Down = digitalRead(downPin);

    Joystick.setButton(0,!Up);
    Joystick.setButton(1,!Down);

    delay(50);
    }

## 5. Zusammenfassung

Der Controller hat direkt nach dem ersten Start funktionert und wurde in bisher jedem Spiel, welches ich testete, ohne Probleme erkannt.
