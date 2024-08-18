# Meine Theme Einstellungen

Damit ich das Theme nicht immer in meinem Profil ändern muss, habe ich einen Helfer angelegt, in welchen ich alle auszuwählenden Themes aufgelistet habe.

Helfer: Dropdown



Name: Themes


Icon: mdi:format-paint


Optionen:


- Caule Black Rose Glass
- Caule Black Purple Glass
- Caule Black Blue Glass
- Caule Black Aqua Glass
- Caule Black Green Glass
- Caule Black Yellow Glass
- Caule Black Orange Glass
- Caule Black Coral Glass
- Caule Black Pink Glass
- Caule Black Gray Glass
- Caule Black Rose
- Caule Black Purple
- Caule Black Blue
- Caule Black Aqua
- Caule Black Green
- Caule Black Yellow
- Caule Black Orange
- Caule Black Coral
- Caule Black Pink
- Caule Black Gray
- Caule Dark Rose
- Caule Dark Purple
- Caule Dark Blue
- Caule Dark Aqua
- Caule Dark Green
- Caule Dark Yellow
- Caule Dark Orange
- Caule Dark Coral
- Caule Dark Pink
- Caule Dark Gray
- Caule Light Rose
- Caule Light Purple
- Caule Light Blue
- Caule Light Aqua
- Caule Light Green
- Caule Light Yellow
- Caule Light Orange
- Caule Light Coral
- Caule Light Pink
- Caule Light Gray
- Caule Animated Rose Glass
- Caule Animated Purple Glass
- Caule Animated Blue Glass
- Caule Animated Aqua Glass
- Caule Animated Green Glass
- Caule Animated Yellow Glass
- Caule Animated Orange Glass
- Caule Animated Coral Glass
- Caule Animated Pink Glass
- Caule Animated Gray Glass
- default


Danch habe ich noch eine Automatisierung erstellt, welche das Theme auf das im Helfer ausgewählte einstellt.

```yaml
alias: Set Themes
description: ""
trigger:
  - platform: state
    entity_id:
      - input_select.themes
condition: []
action:
  - data:
      name: |
        {{ trigger.to_state.state }}
      mode: dark
    action: frontend.set_theme
mode: single
```

