# Lichtsignalanlage-für-Scheibenschiessen-Pistole-25m
Lichtsignalanlage für die Pistolendisziplinen mit 10s, 20s und 7s+3s Zeitlimits

Im Wesentlichen geht es um die "Shot - don't Shot" Signalisierung auf einer Schiessanlage für das Pistolenschiessen 25m in den Zeitdisziplinen auf Basis von WS2812 8x8 Matrizen und ESP8266  Modulen. 

Voraussetzung ist natürlich Wifi-Empfang dort wo die Lichtsignalanlagen später hängen sollen. Auf unserer Schiessanlage ist glücklicherweise durch unsere Scheibenbeobachtungskameras die Voraussetzung geschaffen worden. 

Der Aufbau ist eigentlich simpel. Man nehme 3 mal:

![61yslnrIXHL _AC_SX679_](https://user-images.githubusercontent.com/55184135/228845679-b304f9ec-1f6e-494a-8403-c07c6895bfc9.jpg)


und 3 mal:

![71b9yM7dFlL _SX466_](https://user-images.githubusercontent.com/55184135/228845776-24f1171e-391e-4980-8c2d-bed19e2b098e.jpg)


und gesteuert werden mit der folgenden Software:

![wled_logo_akemi](https://user-images.githubusercontent.com/55184135/228845879-2eab03f3-c0b2-4ce9-9be2-73b232b241f3.png)

und dann stellt man fest das es so einfach dann doch nicht ist. Erst mal müssen der ESP8266 und die LED-Module sinvoll verbunden werden wozu ein Levelshifter empfohlen wird. Es geht aber auch einfacher, da nicht bidirektional, über einen Widerstand als PullUp und eine Entkoppelungsdiode.

Wenn das schon mal funktioniert, also die Demos die LEDs in sinnvoller Weise ansteuern, dann kommt der Moment wo man feststellt das es leider nicht reicht nur jedem LED-Modul einen ESP8266 zu spendieren weil die WLED Software, jedenfalls so wie ich sie betreibe, die eigenen LEDs bevorzugt und dann erst die Kommandos an die anderen ESP8266 absetzt. Also noch einen 4. ESP8266 als Master dazu geholt und schwups ist alles synchron.

Das war aber leider nicht komfortabel genug da die Weboberfläche von WLed genügend Möglichkeiten der Fehlbedienung bietet. Zum Glück bin ich "zufällig" über eine Software gestolpert mit der man Konsolenspiele verwalten und starten kann. Diese ist so weit konfigurierbar das man per CURL unter Windows die Kommandos an den Master absetzen kann, der diese weiterleitet an die Slaves und das ganz komfortabel mit Oberfläche und so.
