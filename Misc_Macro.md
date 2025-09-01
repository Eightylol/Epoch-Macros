
---

# 📜 Misc Macros

---

<br>

### Attack
```
#showtooltip
/dismount
/startattack
```

### Universal ranged attack
```
#showtooltip
/cast [equipped:bow] Shoot Bow;[equipped:gun] Shoot Gun; [equipped: crossbow] Shoot Crossbow; [equipped: thrown] Throw
```

### Bandage
>Apply Bandage on self without losing target
```
#showtooltip
/use [target=player] Heavy Runecloth Bandage
```

### Herb/Mineral tracking
>Alternate between Herb/Mineral tracking
```
#showtooltip
/castsequence Find Herbs, Find Minerals
```

### Consumable heal
```
#showtooltip Major Healing Potion
/use Whipper Root Tuber
/use Major Healing Potion
```

### Fishing - needs testing
```
#showtooltip Fishing
/equip [noequipped:FishingPole] Big Iron Fishing Pole
/use Big-mouth Clam
/use Bright Baubles
/use 16
/click StaticPopup1Button2
/stopspelltarget
/cast fishing
```