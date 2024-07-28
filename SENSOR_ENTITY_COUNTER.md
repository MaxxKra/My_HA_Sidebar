# Meine Entitäten - Zähler

Um alle aktiven Entitäten zählen zu können, habe ich bei meinen Templates zwei Sensoren angelegt, welche mir alle aktiven Lampen also `light` Entitäten und Schalter also `switch` Entitäten anzeigt.

![EntityCounter1](https://raw.githubusercontent.com/MaxxKra/README_images/master/Sidebar/Entity_Counter_1.jpg)
![EntityCounter2](https://raw.githubusercontent.com/MaxxKra/README_images/master/Sidebar/Entity_Counter_2.jpg)

Man kann mit `rejectattr` auch Entitäten ausnehmen, wenn diese nicht mitgezählt werden sollen.
In meinem Fall betrifft das meinen Monitor welcher als `light.shb_pc_vivaldi_screen` , sowie den Vollbild-Schalter welcher als `switch.vollbild_touch_pc` angezeigt wird. 


```yaml
#       ######## ##    ## ######## #### ######## ##    ##                       #
#       ##       ###   ##    ##     ##     ##     ##  ##                        #
#       ##       ####  ##    ##     ##     ##      ####                         #
#       ######   ## ## ##    ##     ##     ##       ##                          #
#       ##       ##  ####    ##     ##     ##       ##                          #
#       ##       ##   ###    ##     ##     ##       ##                          #
#       ######## ##    ##    ##    ####    ##       ##                          #
#                                                                               #
#        ######   #######  ##     ## ##    ## ######## ######## ########        #
#       ##    ## ##     ## ##     ## ###   ##    ##    ##       ##     ##       #
#       ##       ##     ## ##     ## ####  ##    ##    ##       ##     ##       #
#       ##       ##     ## ##     ## ## ## ##    ##    ######   ########        #
#       ##       ##     ## ##     ## ##  ####    ##    ##       ##   ##         #
#       ##    ## ##     ## ##     ## ##   ###    ##    ##       ##    ##        #
#        ######   #######   #######  ##    ##    ##    ######## ##     ##       #
#########################################################################################
#---------------------------------------------------------------------------------------#
##------------------------  Zählen diverser aktiver Entitäten -------------------------##
#---------------------------------------------------------------------------------------#
#########################################################################################


sensor:
  #-----------------------------------------------------------
  # Anzahl aktiver LICHT Entitäten
  #-----------------------------------------------------------
  - name: "Zähler Lights gesamt"
    icon: mdi:lightbulb-question-outline
    state: >
      {{ states.light 
         | rejectattr('attributes.entity_id', 'defined') 
         | rejectattr('entity_id', 'in', ['light.shb_pc_vivaldi_screen']) 
         | selectattr('state', 'eq', 'on') 
         | list 
         | count }}

  #-----------------------------------------------------------
  # Anzahl aktiver SCHALTER Entitäten
  #-----------------------------------------------------------
  - name: "Zähler Schalter gesamt"
    icon: mdi:help-network-outline
    state: >
      {{ states.switch 
         | rejectattr('attributes.entity_id', 'defined') 
         | rejectattr('entity_id', 'in', ['switch.vollbild_touch_pc']) 
         | selectattr('state', 'eq', 'on') 
         | list 
         | count }}
```