# Hunter Macros

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