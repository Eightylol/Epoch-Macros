
---

# 📜 Shaman Macros

---
<br>

### Call of the Ancestors
```
#showtooltip Call of the Ancestors
/dismount
/startattack
/cast Call of the Ancestors
```

### Call of the Elements
```
#showtooltip Call of the Elements
/dismount
/startattack
/cast Call of the Elements
```

### Chain Heal
>Cast on mouseover if present, otherwise on target or self.
```
#showtooltip Chain Heal
/cast [@mouseover,nodead,help][] Chain Heal
```

### Chain Lightning
```
#showtooltip Chain Lightning
/use 13
/use 14
/cast Chain Lightning
```

### Earth Shock
```
#showtooltip Earth Shock
/use 13
/use 14
/cast [@mouseover,nodead,harm][@target,nodead,harm][] Earth Shock
```

### Earth Shield
>Cast on mouseover if present, then on focus if present, otherwise on target or self.
```
#showtooltip Earth Shield
/cast [@mouseover,nodead,help][@focus,nodead,help][] Earth Shield; 
```

### Elemental Mastery
```
#showtooltip Elemental Mastery
/use 14
/cast Elemental Mastery
```

### Flame Shock
```
#showtooltip Flame Shock
/use 13
/use 14
/cast Flame Shock
```

### Healing Wave
>Cast on mouseover if present, otherwise on target or self.
```
#showtooltip Healing Wave
/cast [@mouseover,nodead,help][] Healing Wave
```

### Healing Wave - NS
>Cast on mouseover if present, otherwise on target or self.
```
#showtooltip
/stopcasting
/cast Nature's Swiftness
/use 13
/use 14
/cast [@mouseover,nodead,help][] Healing Wave
```

### Lesser Healing Wave
>Cast on mouseover if present, otherwise on target or self.
```
#showtooltip Lesser Healing Wave
/cast [@mouseover,nodead,help][] Lesser Healing Wave
```

### Lightning Bolt
```
#showtooltip Lightning Bolt
/use 13
/use 14
/cast Lightning Bolt
```

### Purge
```
#showtooltip
/stopcasting
/cast [@mouseover,nodead][@target,nodead][] Purge
```

### Stormstrike
```
#showtooltip Stormstrike
/dismount
/startattack
/use 13
/use 14
/cast Stormstrike
```