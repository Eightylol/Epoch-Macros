
---

# 📜 Paladin Macros

---
<br>

### Avenging Wrath
> Popping all cooldowns
```
#showtooltip Avenging Wrath
/use 13
/use 14
/cast Avenging Wrath
```

### Blessing of Freedom
> Mouseover
```
#showtooltip Blessing of Freedom
/cast [@mouseover,help,exists,nodead][@target,help,exists,nodead][@player] Blessing of Freedom; Blessing of Freedom
```

### Blessing of Protection
> Mouseover
```
#showtooltip Blessing of Protection 
/cast [target=mouseover,help] Blessing of Protection; Blessing of Protection
```

### Cleanse
> Cleanse self, Cleanse mouseover 
```
#showtooltip
/cast [@target,help,nodead,exists][@mouseover,exists,help,nodead][@player] Cleanse; Cleanse
```

### Crusader Strike
```
#showtooltip Crusader Strike
/cast Crusader Strike
/startattack
```

### Divine Shield
```
#showtooltip
/cancelaura Divine Shield
/cast Divine Shield
```

### Hammer Of Justice
```
#showtooltip Hammer of Justice
/stopcasting
/cast Hammer of Justice
```

### Holy Light
> Mouseover
```
#showtooltip
/cast [@mouseover, help, nodead] Holy Light
```

### Holy Shock
> Mouseover
```
#showtooltip Holy Shock
/cast [@mouseover, help, nodead] [help, nodead] Holy Shock;
[harm, nodead] Holy Shock
```

### Judgement
```
#showtooltip Judgement
/startattack
/use 14
/cast Judgement
/cast Seal of Command(Rank 1)
```

### Righteous Defense
> Attempts to taunt, in order, target -> mouseover friendly -> targets target
```
#showtooltip
/cast [exists,help,nodead][@mouseover,exists,help,nodead][exists,harm,nodead,target=targettarget] Righteous Defense; Righteous Defense
```

### Seal of Command
```
#showtooltip Seal of Command
/cast Seal of Command
/startattack
```

### Seal of Command
> With popping cooldowns. Change/remove trinkets based on equipped items.
```
#showtooltip Seal of Command
/cast Avenging Wrath
/use 13
/use 14
/cast Seal of Command
/startattack
```