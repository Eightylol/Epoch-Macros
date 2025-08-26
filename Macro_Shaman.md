# Shaman Macros

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
/cast [target=mouseover, exists] Chain Heal; Chain Heal
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
/cast Earth Shock
```

### Earth Shield
>Cast on mouseover if present, then on focus if present, otherwise on target or self.
```
#showtooltip Earth Shield
/cast [target=mouseover, exists] Earth Shield; [target=focus,exists,noharm] Earth Shield; Earth Shield
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
/cast [target=mouseover, exists] Healing Wave; Healing Wave
```

### Healing Wave - NS
>Cast on mouseover if present, otherwise on target or self.
```
#showtooltip
/stopcasting
/cast Nature's Swiftness
/use 13
/use 14
/cast [target=mouseover, exists] Healing Wave; Healing Wave
```

### Lesser Healing Wave
>Cast on mouseover if present, otherwise on target or self.
```
#showtooltip Lesser Healing Wave
/cast [target=mouseover, exists] Lesser Healing Wave; Lesser Healing Wave
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
/cast [@mouseover,nodead] Purge; [@target] Purge
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