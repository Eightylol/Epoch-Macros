# Priest Macros

### Mind Blast
```
#showtooltip Mind Blast
/use 13
/use 14
/cast Inner Focus
/cast Mind Blast
```

### Dispel 
>Dispel self without losing target
```
#showtooltip
/cast [target=player] Dispel Magic(Rank 2)
```

### Mind Flay
>Cast Mind Flay, unless already channeling
```
#showtooltip
/cast [nochanneling:Mind Flay] Mind Flay
```

### Power Word: Shield
```
#showtooltip
/dismount
/cast Power Word: Shield(Rank 10)
```

### Power Infusion (Mouseover)
```
#showtooltip Power Infusion
/use 14
/cast [@mouseover][] Power Infusion
```

### Prayer of Healing
```
#showtooltip Prayer of Healing
/cast [target=mouseover,help][help][] Prayer of Healing; Prayer of Healing
```

### Shadow Word: Pain
```
#showtooltip Shadow Word: Pain
/use 13
/use 14
/cast [@mouseover,harm,nodead] Shadow Word: Pain; Shadow Word: Pain
```

### Shadow Word: Death
```
#showtooltip Shadow Word: Death
/cast Inner Focus
/cast Shadow Word: Death
```

#### Silence
```
#showtooltip
/stopcasting
/cast Silence
```

### Wand
> Spammable
```
/cast !Shoot
```