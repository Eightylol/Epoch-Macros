
---

# 📜 Mage Macros

---
<br>

### Arcane Blast
> Can also be used with [nochanneling : Arcane Missiles]
```
#showtooltip Arcane Blast
/cast Arcane Blast
```

### Blizzard
```
#showtooltip Blizzard
/cast Blizzard
```

### Counterspell
```
#showtooltip Counterspell
/stopcasting
/cast [target=mouseover,exist,harm] Counterspell;Counterspell
```

### Frostbolt
```
#showtooltip Frostbolt
/cast Frostbolt
```

### Ice Block
```
#showtooltip Ice Block
/stopcasting
/cast Ice Block
/cancelaura Ice Block
```

### Polymorph
```
#showtooltip Polymorph
/cast [@focus, exists] Polymorph;  [@mouseover, exists] Polymorph; Polymorph
```

### Ritual of Refreshment(Rank 1)
```
#showtooltip Ritual of Refreshment(Rank 1)
/cast Ritual of Refreshment(Rank 1)
```