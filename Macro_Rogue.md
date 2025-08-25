# Rogue Macros
### Backstab
```
#showtooltip
/startattack
/cast Backstab
```
```
#showtooltip
/cast Backstab
```

### Blind
```
#showtooltip Blind
/cast [@mouseover] Blind
```

### Sap closest enemy
```
#showtooltip Sap
/cleartarget
/targetenemyplayer
/cast Sap
```

### Poison Application
```
#showtooltip
/use Crippling Poison II
/use 16
```
```
#showtooltip
/use Instant Poison VI
/use 16
```

### Sinister Strike
```
/startattack
/cast Sinister Strike
```

### Riposte
```
#showtooltip
/startattack
/cast Riposte
/cast Sinister Strike
```

### In-Combat Cheap Shot
>ShotDismount, stealth if not in stealth, Cheap Shot if player has a target <br>
>Spam for success
```
#showtooltip Stealth
/dismount
/cast !stealth
/cast [target=target] Cheap Shot
```

### In-Combat Cheap Shot - trinket
>Trinket, Shadowstep, Cheap Shot. Great when being opened on
```
/use 13
/use 14
/cast Vanish
/cast Shadowstep
/cast [target=target] Cheap Shot
```



### In-Combat Sap
>Dismount, stealth if not in stealth, Sap if player has a target
<br>
>Spam for success
```
#showtooltip Stealth
/dismount
/cast !stealth
/cast [target=target] Sap
```

### In-Combat Sap (Shadowstep)
>Shadowstep, stealth if not in stealth, Sap if player has a target
<br>
>Spam for success
```
#showtooltip Shadowstep
/cast !stealth
/cast [@target] Shadowstep
/cast [@target] Sap
```

