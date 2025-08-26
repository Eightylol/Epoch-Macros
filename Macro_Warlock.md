# Warlock Macros

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

### DoT Mouseover Example
> "Corruption" can be replaced with any DoT.
```
#showtooltip Corruption
/use [@mouseover,harm] [harm] Corruption
```

### Drain Life
```
#showtooltip Drain Life
/cast [nochanneling:Drain Life] Drain Life
```

### Fear
```
#showtooltip Fear
/stopcasting
/cast Fear
```

### Fel Domination + Pet
```
#showtooltip Summon <pet of choice>
/use Fel Domination
/use Summon <pet of choice>
```

### Incinerate
```
#showtooltip Incinerate
/cast Demonic Empowerment
/cast Incinerate
```

### Rain of Fire
> Cast at cursor.
```
#showtooltip Rain of Fire
/cast [@cursor] Rain of Fire
```

### Ritual of Souls
```
#showtooltip Ritual of Souls
/s Click Please!
/cast Ritual of Souls
```

### Shadow Bolt Rank 1 
```
#showtooltip
/cast [@mouseover,harm,nodead] [] Shadow Bolt(Rank 1)
```