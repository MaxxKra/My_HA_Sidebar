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
| Swipe Navigaton | https://github.com/zanna-37/hass-swipe-navigation.git | /hacs/repository/5017254 |
| Button Cartd | https://github.com/custom-cards/button-card.git | /hacs/repository/146194325 |
| Card Mod | https://github.com/thomasloven/lovelace-card-mod.git | /hacs/repository/190927524 |
| Clock Weather Card | https://github.com/pkissling/clock-weather-card.git | /hacs/repository/522634019 |
| Vertical Stack in Card | https://github.com/ofekashery/vertical-stack-in-card.git | /hacs/repository/142051833 |
| Caule Themes | https://github.com/MaxxKra/caule-themes-pack-1.git | /hacs/repository/797533022 |


<br>


## Erstellung in Schritten:

### Schritt :one:


Erstelle dein Dashboard in Home Assistant mit mehreren Seiten und stelle dabei sicher, dass jede Seite eine eigene URL hat.
Das Layout (Grid, Panel, Horizontal, Vertical, usw...) spielt dabei keine Rolle.

In meinem Fall sind die Seiten meines `dashboard-Sidebar` auf folgende Namen und URL´s aufgeteilt:

| **NAME** | **URL** | **ANSICHTSART** |
| --- | --- | --- |
| Floorplan | /dashboard-sidebar/floorplan | Panel (1 Karte) |
| Übersicht | /dashboard-sidebar/ubersicht | Abschnitte (experimentell) |
| Alles Müll | /dashboard-sidebar/alles-mull | Panel (1 Karte) |
| Geburtstage | /dashboard-sidebar/geburtstage | Grid (layout-card) |


### Schritt :two: