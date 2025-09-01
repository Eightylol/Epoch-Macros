
---

# 📜 Priest Macros

---
<br>

### Binding Heal
>Cast on mouseover if present, otherwise on target or self.
```
#showtooltip Binding Heal
/cast [@mouseover, exists] Binding Heal; Binding Heal
```

### Dispel 
>Dispel self without losing target
```
#showtooltip
/cast [target=player] Dispel Magic(Rank 2)
```

### Flash Heal
>Cast on mouseover if present, otherwise on target or self.
```
#showtooltip Flash Heal
/cast [@mouseover, exists] Flash Heal; Flash Heal
```

### Greater Heal
>Cast on mouseover if present, otherwise on target or self.
```
#showtooltip Greater Heal
/cast [@mouseover, exists] Greater Heal; Greater Heal
```

### Mass Dispel
```
#showtooltip
/cast !Mass Dispel
```

### Mind Blast
```
#showtooltip Mind Blast
/use 13
/use 14
/cast Inner Focus
/cast Mind Blast
```

### Mind Flay
>Cast Mind Flay, unless already channeling
```
#showtooltip
/cast [nochanneling:Mind Flay] Mind Flay
```

### Pain Suppression
>Cast on mouseover if present, then on focus if present, otherwise on target or self.
```
#showtooltip Pain Suppression
/cast [@mouseover, exists] Pain Suppression; [@focus, exists, noharm] Pain Suppression; Pain Suppression
```

### Power Word: Shield
>Cast on mouseover if present, otherwise on target or self.
```
#showtooltip Power Word: Shield
/cast [@mouseover, exists] Power Word: Shield; Power Word: Shield
```

### Powerr Infusion
>Cast on mouseover if present, otherwise on target or self.
```
#showtooltip Power Infusion
/cast [@mouseover, exists, noharm] Power Infusion; Power Infusion
```

### Prayer of Healing
```
#showtooltip Prayer of Healing
/cast [target=mouseover,help][help][] Prayer of Healing; Prayer of Healing
```

### Prayer of Mending
>Cast on mouseover if present, then on focus if present, otherwise on target or self.
```
#showtooltip Prayer of Mending
/cast [@mouseover, exists, noharm] Prayer of Mending; [@focus, exists, noharm] Prayer of Mending; Prayer of Mending
```


### Psychic Horror 
> Mouseover -> target prioritization
```
#Showtooltip Psychic Horror
/cast [target=mouseover, harm][harm] Psychic Horror
```

### Psychic Horror
> Focustarget
```
#Showtooltip Psychic Horror
/cast [target=focus] Psychic Horror
```

### Renew
>Cast on mouseover if present, otherwise on target or self.
```
#showtooltip Renew
/cast [@mouseover, exists] Renew; Renew
```

### Shadowform
> Spammable - it won't drop you out of form after you're in shadowform.
```
#showtooltip
/cast !Shadowform
```

### Shadow Word: Death
```
#showtooltip Shadow Word: Death
/stopcasting
/cast Inner Focus
/cast Shadow Word: Death
```

### Shadow Word: Pain
```
#showtooltip Shadow Word: Pain
/use 13
/use 14
/cast [@mouseover,harm,nodead] Shadow Word: Pain; Shadow Word: Pain
```

### Silence
> Mouseover -> target prioritization
```
#showtooltip
/cast [target=mouseover, harm][harm] Silence
```

### Silence
> Focustarget
```
#showtooltip
/cast [target=focus] Silence
```


### Silence
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
