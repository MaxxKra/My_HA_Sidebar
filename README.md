# Meine Dashboard Seitenleiste (Sidebar)
Hier findest du alle Informationen um meine Sidebar nachzubauen.

<br>

Beispiel:
![Beispiel](https://raw.githubusercontent.com/MaxxKra/README_images/master/Sidebar/Sidebar.gif)

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

In meinem Fall sind die Seiten meines `dashboard-Sidebar` auf folgende Namen und URL´s aufgeteilt:

| **NAME** | **URL** | **ANSICHTSART** |
| --- | --- | --- |
| Floorplan | /dashboard-sidebar/floorplan | Panel (1 Karte) |
| Übersicht | /dashboard-sidebar/ubersicht | Abschnitte (experimentell) |
| Alles Müll | /dashboard-sidebar/alles-mull | Panel (1 Karte) |
| Geburtstage | /dashboard-sidebar/geburtstage | Grid (layout-card) |


### Schritt :two: - Vollbildmodus einrichten


Für den Vollbildmodus verwende ich gerne den Kiosk Mode, auch wenn das Ausblenden der Seiten- und Titel- Leiste auch mit der Sidebar Card funktionieren würde.
Durch den Kiosk Mode und dem dazu angelegten Helfer habe ich die Möglichkeit, einen Schalter am Dashboard zu positionieren, mit welchem ich das Vollbild ein bzw. ausschalten kann.

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
