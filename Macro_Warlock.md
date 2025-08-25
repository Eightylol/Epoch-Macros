# Warlock Macros

### Unending Resolve + Healthstone
```
#showtooltip Unending Resolve
/use Healthstone
/cast Unending Resolve
```

### Fel Domination + Pet
```
#showtooltip Summon <pet of choice>
/use Fel Domination
/use Summon <pet of choice>
```

### DoT Mouseover Example
> "Corruption" can be replaced with any DoT spell.
```
#showtooltip Corruption
/use [@mouseover,harm] [harm] Corruption
```

### Banish Focus
```
#showtooltip Banish
/use [@focus] [] Banish
```

### Demonic Circle
```
#showtooltip
/stopcasting
/cast Demonic Circle
```

### Moral Coil or Howl of Terror
> Bind the two spells to the same key, depending on what you have talented. Makes temporary spec changes simpler.
```
#showtooltip
/use [talent:5/2,@mouseover,exists] Mortal Coil; [talent:5/2] Mortal Coil; [talent:5/3] Howl of Terror
```

### Grimire: Felguard
```
#showtooltip Grimoire: Felguard
/petattack
/use 13
/use 14
/cast Blood Fury
/cast Grimoire: Felguard
```

### Summon Demonic Tyrant
```
#showtooltip Summon Demonic Tyrant
/petattack
/use 13
/use 14
/cast Blood Fury
/cast Summon Demonic Tyrant
```

### Demonbolt
> Can be used with any spell to start pet attack
```
#showtooltip Demonbolt
/petattack
/cast Demonbolt
```

### Havoc
> Cast on Mouseover target, or current target.
```
#showtooltip Havoc
/cast [@mouseover,harm] Havoc; [harm] Havoc
```

### Rain of Fire
> Case at cursor to avoiding circle and click.
```
#showtooltip Rain of Fire
/cast [@cursor] Rain of Fire
```

### Rain of Fire
> Case at cursor to avoiding circle and click.
```
#showtooltip Summon Infernal
/use 13
/use 14
/cast Blood Fury
/cast [@cursor] Summon Infernal
```