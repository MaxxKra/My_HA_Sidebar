# Meine Dashboard Seitenleiste (Sidebar)
Hier findest du alle Informationen um meine Sidebar nachzubauen.

<br>

Beispiel:
![Beispiel](https://raw.githubusercontent.com/MaxxKra/README_images/master/Sidebar/Sidebar.gif)

<br>

### <p align="center">Wenn du Interesse daran hast, mich, meinen Kanal oder meine kreative Arbeit zu unterstützen,<br>freue ich mich über jeglichen Support:
</p>
<p align="center">
  <a href="https://www.buymeacoffee.com/bastler">
    <img src="https://www.buymeacoffee.com/assets/img/custom_images/orange_img.png" alt="Buy Me A Coffee">
  </a>
  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
  <a href="https://www.paypal.me/kramlmaxx">
    <img src="https://www.paypalobjects.com/en_US/i/btn/btn_donateCC_LG.gif" alt="PayPal Donate">
  </a>
</p>

### <p align="center">Danke</p>

<br>


## Verwendete HACS Integrationen:

| **TYPE** | **LINK** | **HACS PFAD** |
| --- | --- | --- |
| Sidbar Card | https://github.com/DBuit/sidebar-card.git | /hacs/repository/241825574 |
| Kiosk Mode | https://github.com/NemesisRE/kiosk-mode.git | /hacs/repository/497319128 |
| Swipe Navigaton | https://github.com/zanna-37/hass-swipe-navigation.git | /hacs/repository/5017254 |
| Button Cartd | https://github.com/custom-cards/button-card.git | /hacs/repository/146194325 |
| Card Mod | https://github.com/thomasloven/lovelace-card-mod.git | /hacs/repository/190927524 |
| Clock Weather Card | https://github.com/pkissling/clock-weather-card.git | /hacs/repository/522634019 |
| Vertical Stack in Card | https://github.com/ofekashery/vertical-stack-in-card.git | /hacs/repository/142051833 |
| Caule Themes | https://github.com/MaxxKra/caule-themes-pack-1.git | /hacs/repository/797533022 |


<br>


## Erstellung in Schritten:

### Schritt :one: - Dashboards erstellen


Erstelle dein Dashboard in Home Assistant mit mehreren Seiten und stelle dabei sicher, dass jede Seite eine eigene URL hat.
Das Layout (Grid, Panel, Horizontal, Vertical, usw...) spielt dabei keine Rolle.

<br>

![Beispiel](https://raw.githubusercontent.com/MaxxKra/README_images/master/Sidebar/Dashboard_Seiten.jpg)

<br>

In meinem Fall sind die Seiten meines `dashboard-Sidebar` auf folgende Namen und URL´s aufgeteilt:

| **NAME** | **URL** | **ANSICHTSART** |
| --- | --- | --- |
| Floorplan | /dashboard-sidebar/floorplan | Panel (1 Karte) |
| Übersicht | /dashboard-sidebar/ubersicht | Abschnitte (experimentell) |
| Alles Müll | /dashboard-sidebar/alles-mull | Panel (1 Karte) |
| Geburtstage | /dashboard-sidebar/geburtstage | Grid (layout-card) |


### Schritt :two: - Vollbildmodus einrichten


Für den Vollbildmodus verwende ich gerne den Kiosk Mode, auch wenn das Ausblenden der Seiten- und Titel- Leiste ebenso mit der Sidebar Card funktionieren würde.
Durch den Kiosk Mode und dem dazu angelegten Helfer habe ich die Möglichkeit, einen Schalter am Dashboard zu positionieren, mit welchem ich das Vollbild ein bzw. ausschalten kann.

<br>

<img src="https://raw.githubusercontent.com/MaxxKra/README_images/master/Sidebar/Vollbild_Schalter.gif" alt="Example" width="600"/>

<br>

Den Kiosk-Mode habe ich in HACS installiert und mit folgendem Code im RAW Konfigurationseditor eingerichtet:


```yaml
kiosk_mode:
  entity_settings:
    - entity:
        switch.vollbild_touch_pc: 'on'
      hide_sidebar: true
      hide_header: true
```


### Schritt :three: - Swipe Navigation einrichten


Eine super Custom Integration ist die Home Assistant Swipe Navigation.

Mit dieser hat man die Möglichkeit am Dashboard mit "wischen" zwischen den Seiten zu navigieren.
Auch diese Integration ist in HACS zu installieren und ich habe sie mit folgendem Code im RAW Konfigurationseditor eingerichtet:


```yaml
swipe_nav:
  wrap: true # mit 'true' wird von der letzten zur ersten Seite geswiped
  enable_mouse_swipe: true # true, um mit der Maus zu navigieren
  animate: fade # Alternative Animationen sind: swipe und flip
  animate_duration: 300 # Dauer der Animation
  prevent_default: false # Verhindert mit 'true' die sstandardmäßigen horizontalen Wischaktionen
  swipe_amount: 10 # Länge des Wischens in % um die Seite zu wechseln
```


Es gibt jede Menge Einstellungsmöglichkeiten, welche in der Dokumentation nachzulesen sind. 



### Schritt :four: - Sidebar erstellen


Im nächsten Schritt wird die Sidebar erstellt. Dazu kannst du dir aus der Datei [`Sidebar-RAW-Code.yaml`](https://github.com/MaxxKra/My_HA_Sidebar/blob/aa810088ae622b1fb6ef183465423d6402f6f69e/Sidebar-RAW-Code.yaml) den Code kopieren und in deinen RAW Konfigurationseditor ganz oben einfügen.

Code Erklärung:

1. **Grundeinstellungen**
    - verstecken der Titelleiste
    - verstecken der Seitenleiste
    - Breite der Sidebar


2. **Digitale Uhr**
    - Auswählen ob die digitale Uhr verwendet wird
    - Digitale Uhr mit oder ohne Sekunden


3. **Analoge Uhr**
    - Auswählen ob die analoge Uhr verwendet wird


4. **Datum**
   - Auswählen ob das Datum angezeigt werden soll
   - Eingabe des Dastumsformat (z.B. dddd, DD. MMMM YYYY = Montag, 31.Dezember 2024)


5. **Sidebar Menü**
    - Je Dashboard-Seite ein Eintrag
    - Den Pfad (URL) der Dashboard Seite angeben
    - der am Button dargestellte Name
    - angeben ob der Button als aktiv gekennzeichnet sein soll
    - ein Icon für die Seite am Button auswählen


6. **Sensor Werte Anzeige**<br>
Dies ist die Template Sektion, in welcher eine Begrüßung sowie Sensor Werte angezeigt werden können.
In meinem Fall:
   - Begrüßung Tageszeitabhängig
   - Anzahl der aktiven Lampen
   - Anzahl der aktiven Schalter

Wie ich die Templates für die aktiven Lampen und Schalte in Home Assistant angelegt habe, kann man unter `SENSOR_ENTITY_COUNTER.md` nachlesen und sich den Code kopieren.


7. **Untere Karte**<br>
Hier kann eine bzw. mehrere Karten ganz unten in der Sidebar angezeigt werden und ist somit immer sichtbar.
Ich habe mich für einen vertikalen Stapel mit Hilfe der `custom:vertical-stack-in-card` Integration entschieden.
In diesen vertikalen Stapel habe ich eine Wetterkarte und den Schalter für den Vollbildmodus eingefügt.


8. **Einstellungen Farben, Schriften, Hintergründe**<br>
Nun folgen die Anaben für das Design bzw. die Darstellungen.<br><br>
Am Besten findet man sich damit zurecht, wenn man mit den diversen Einstellungen herumspiet um die Aufgabe der jeweiligen Angaben besser kennen zu lernen.<br><br>
- Im Einzelnen sind die Abschnitte:
    - :host = die Grundeinstellungen der Sidebar im Allgemeinen
    - #customSidebar = der Z Index welcher sicherstellt, dass die Sidebar ganz vorne dargestellt wird
    - .sidebarMenu li = Zeilenhöhe und Farbe der Navigation Buttons
    - .bottom = die Breite der unteren Karten im Bezug zur Sidebar
    - .sidebarMenu li.active = die Darstellung der Navigation Buttons wenn ausgewählt
    - .sidebarMenu li.active ha-icon = die Darstellung des Icons wenn der Button ausgewählt ist
    - .clock = Position und Größe der analogen Uhr
    - .digitalClock = Position, Größe und Schrift der digitalen Uhr
    - .date = Position, Größe und Schrift des Datum
    - .template li = Darstellung der Template Sektion allgemein
    - .template li.one-light = Farbe und Schrift des Lampen Templates bei 1 aktiven Lampe
    - .template li.multiple-lights = Farbe und Schrift des Lampen Templates bei mehreren aktiven Lampen
    - .template li.one-switch = Farbe und Schrift des Lampen Templates bei 1 aktiven Schalter
    - .template li.multiple-switches = Farbe und Schrift des Lampen Templates bei mehreren aktiven Schaltern
    - .status = Position und Farbe der Status Anzeige


9. **Anmerkungen**<br>
Ein kleines Manko ist, dass die Sidebar leider nicht das Theme der jeweiligen Seite übernimmt, sondern nur das der allgemeinen Einstellung aus dem Profil. Ich habe das mit einem Auswahl-Helfer und einer Automatisierung gelöst, in dem ich das Theme je nach Eintrag des Helfers in HA komplett einstelle.