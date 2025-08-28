# Druid Macros

### Bash
```
#showtooltip Bash
/cast [noform:1] Bear Form(Shapeshift)
/cast Bash
```

### Cat
```
#showtooltip
/cast !Cat Form
/startattack
```

### Cyclone
```
#showtooltip Cyclone
/stopcasting
/cast [@focus] Cyclone
```

### Challenging Roar
```
#showtooltip Challenging Roar
/cast !Bear Form
/cast Challenging Roar
```

### Dash
```
#showtooltip Dash
/cancelform [noform:3]
/cast [noform:3] Cat Form
/cast Dash
```

### Faerie Fire
```
#showtooltip
/cast [nomod,stance:1] Faerie Fire (Feral)
/cast [nomod,stance:3] Faerie Fire (Feral)
/cast Faerie Fire
```

### Feral Charge (Castsequence)
> spam to charge
```
#showtooltip Feral Charge
/castsequence reset=5 bear form, feral charge
```

### Feral Charge (Not working atm)
```
#showtooltip Feral Charge
/cancelform [noform:1]
/cast [noform:1] Dire Bear Form
/cast Feral Charge
```

### Growl
```
#showtooltip Growl
/cast [@mouseover, harm, form:1][@target, harm, form:1] Growl
```

### Hibernate
```
#showtooltip Hibernate
/cast [@mouseover,harm]Hibernate
```

### Pounce / Rake
```
#showtooltip
/cast [nostealth] Rake; [stealth] Pounce
```

### Powershift
```
#showtooltip
/cast !Cat Form
/startattack [form:3,harm,nodead]
```

### Prowl
> needs doubleclicking - spammable
```
#showtooltip Prowl
/cancelform [noform:3]
/cast [noform:3] Cat Form
/cast !Prowl
```

### Ravage / Shred
```
#showtooltip
/cast [stealth] Ravage; [nostealth] Shred
```

### Travel Form
```
#showtooltip
/cast [swimming] !Aquatic Form;[outdoors] !Travel Form; !Cat Form
```

<br>
<br>
<br>
<br>

# Needs testing - will edit based on results

### Bear Heal
> Double-tap - uses enrage and then cancels enrage at the end to cancel armor reduction
```
#showtooltip Dire Bear Form
/use Enrage
/cast [noform:1] !Dire Bear Form
/cast Frenzied Regeneration
/use Major Healing Potion
/cancelaura Enrage
```

### Innervate
```
#showtooltip Innervate
/cast [help] Innervate
/script SendChatMessage("innervated.", "WHISPER", nil, UnitName("target"))
```

### Rebirth / Revive
```
#showtooltip Rebirth(Rank 7)
/stopmacro [nohelp,nodead]
/run c="Resurrecting %t"if UnitInRaid("player")then SendChatMessage(c, "RAID")elseif GetNumPartyMembers()>0 then SendChatMessage(c, "PARTY")end
/cast [combat] Rebirth ; Revive
```