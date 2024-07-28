# Meine Entitäten - Zähler

Um alle aktiven Entitäten zählen zu können, habe ich bei meinen Templates zwei Sensoren angelegt, welche mir alle aktiven Lampen also `light` Entitäten und Schalter also `switch` Entitäten anzeigt.



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