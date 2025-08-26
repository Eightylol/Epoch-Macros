# Rogue Macros

### Adrenaline Rush
```
#showtooltip Adrenaline Rush
/use 14
/startattack
/cast Adrenaline Rush
```

### Apply Poison
> Left + Right mouse button click
```
#showtooltip Deadly Poison IX
/use Deadly Poison IX;
/use [button:1] 16; [button:2] 17;
/click StaticPopup1Button1
```

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

### Blade Flurry
```
#showtooltip Blade Flurry
/startattack
/cast Cold Blood
/cast Blade Flurry
/cast Adrenaline Rush
```

### Blind
```
#showtooltip Blind
/cast [@mouseover] Blind
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
>Dismount, stealth if not in stealth, Sap if player has a target <br>
>Spam for success
```
#showtooltip Stealth
/dismount
/cast !stealth
/cast [target=target] Sap
```

### In-Combat Sap (Shadowstep)
>Shadowstep, stealth if not in stealth, Sap if player has a target <br>
>Spam for success
```
#showtooltip Shadowstep
/cast !stealth
/cast [@target] Shadowstep
/cast [@target] Sap
```

### Kick
```
#showtooltip Kick
/startattack
/cast [target=mouseover, exists] Kick); [target=focus, exists] Kick; Kick
```

### Pickpocket
```
#showtooltip Pick Pocket
/targetenemy [no harm][dead]
/cast Pick Pocket
/cleartarget
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

### Riposte / Sinister Strike
```
#showtooltip
/startattack
/cast [mod:shift] Riposte; Sinister Strike

```

### Sap closest enemy
```
#showtooltip Sap
/cleartarget
/targetenemyplayer
/cast Sap
```


### Sinister Strike
```
/startattack
/cast Sinister Strike
```

