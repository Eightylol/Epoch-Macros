
---

# 📜 Hunter Macros

---
<br>

### Aimed Shot
```
#showtooltip Aimed Shot
/use 13
/use 14
/petattack
/cast Aimed Shot
```

### Arcane Shot
```
#showtooltip Arcane Shot
/startattack
/cast !Auto Shot
/cast Arcane Shot
```

#### Auto Shot
```
#showtooltip Auto Shot
/startattack
/cast !Auto Shot
```

### Bestial Wrath
```
#showtooltip Bestial Wrath
/use 14
/startattack
/cast !Auto Shot
/cast Bestial Wrath
```

### Feed Pet
```
#showtooltip Roasted Quail
/cast [pet, nodead] Feed Pet
/use FOOD OF CHOICE
```

### Feign Death
```
#showtooltip Feign Death
/stopattack
/petpassive
/cast Feign Death
```

### Hunter's Mark /w Pet attack
```
#showtooltip Hunter's Mark
/petattack
/cast Hunter's Mark
```

### Hunter's Mark /w Skull
```
#showtooltip Hunter's Mark
/script SetRaidTarget("target",8);
/cast Hunter's Mark
```

### Kill Command
```
#showtooltip Kill Command
/use 13
/use 14
/cast Kill Command
```

### Melee
```
#showtooltip
/stopcasting
/cast Raptor Strike
/startattack
/cast Mongoose Bite
```

### Mend Pet
```
#showtooltip Mend Pet
/cast [@pet,dead] Revive Pet
/cast [nopet] Call Pet
/cast [@pet,nodead] Mend Pet
```

### Misdirection
```
#showtooltip Misdirection
/cast [@focus,exists][@pet] Misdirection
```

### Rapid Fire
```
#showtooltip Rapid Fire
/use 13
/use 14
/petattack
/cast Rapid Fire
```

### Scatter Shot
```
#showtooltip Scatter Shot
/petpassive
/cast Scatter Shot
```

### Serpent Sting
```
#showtooltip Serpent Sting
/startattack
/cast !Auto Shot
/cast Serpent Sting
```

### Steady Shot
```
#showtooltip Steady Shot
/cast Kill Command
/cast Steady Shot
```