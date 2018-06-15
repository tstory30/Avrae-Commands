# Action Surge

*By Toothless#7854.*

<p align="center">
  
<img src="https://i.imgur.com/HUkBwGF.png"/>

</p>



Subtracts 1 from "Action Surge" counter. 



### Usage



``!action``



### Setup


Run the command in the **Code** section. It will automatically setup counters and cvars.



### Code
```GN


!servalias action embed
{{set_cvar_nx("embedimage", "true")}}
{{set_cvar("embedimage", "false") if str(embedimage) != "true" else ""}}
{{set_cvar_nx("showpage", "true")}}
{{set_cvar("showpage", "false") if str(showpage) != "true" else ""}}
{{set("pgSubject", "Fighter")}}
{{set("pgNum", "PHB 72")}}
{{set("counter", "Action Surge")}}
{{set("lvl", int(FighterLevel if exists("FighterLevel") else level))}}
{{create_cc_nx(counter, 0, 1 if lvl < 17 else 2, "short", "bubble")}}
{{set("valid", 1 if get_cc(counter) > 0 else 0)}}
{{mod_cc(counter, -1) if valid else ""}}
-title "<name> {{"uses" if valid else "attempted to use"}} {{counter}}!"
-desc "{{"On your turn, you can take one additional action on top of your regular action and a possible bonus action.\n\nOnce you use this feature, you must finish a short or long rest before you can use it again. Starting at 17th level, you can use it twice before a rest, but only once on the same turn." if valid else "Once you use this feature, you must finish a short or long rest before you can use it again. Starting at 17th level, you can use it twice before a rest, but only once on the same turn. (``!g sr``)"}}"
-f "{{counter}} | {{'?'*get_cc(counter) + '?'*(get_cc_max(counter)-get_cc(counter))}}"
{{"-footer \"" + pgSubject + " | " + pgNum + "\"" if str(showpage) == "true" else ""}}
{{"-thumb " + str(image) if str(embedimage) == "true" and valid else ""}} 
-color <color>