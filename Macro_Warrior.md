# Warrior Macros
<br>

#### Mortal Strike
```
#showtooltip
/startattack
/cast Mortal Strike
```

### Sunder Armor
```
#showtooltip
/startattack
/cast Sunder Armor
```

### Bloodthirst
```
#showtooltip
/startattack
/cast Bloodthirst
```

### Heroic Strike
```
#showtooltip
/cast Heroic Strike
/startattack
```

### Cleave
```
#showtooltip
/cast Cleave
/startattack
```

### Disarm
```
#showtooltip Disarm
/startattack
/cast Defensive Stance
/cast Disarm
```

### Intercept
```
#showtooltip Intercept
/startattack
/cast Berserker Stance
/cast Intercept
```

### Charge
```
#showtooltip
/startattack
/cast Battle Stance
/cast Charge
```

### Overpower/Charge
```
#showtooltip Overpower
/startattack
/cast Battle Stance
/cast Charge
/cast Overpower
```

### Overpower/Charge (mouseover)
```
#showtooltip Overpower
/startattack
/cast Battle Stance
/cast Charge
/cast [@mouseover,harm,nodead][] Overpower
```

### Hamstring (dps/PvP)
```
#showtooltip Hamstring
/startattack
/cast [form:2] Berserker Stance
/cast Hamstring
```



### Rend (dps/PvP)
```
#showtooltip Rend
/startattack
/cast [form:3] Battle Stance
/cast Rend
```

### Equip Shield+Defensive Stance
```
/equipslot 17 Aegis of the Scarlet Commander
/equipslot 16 Vanquisher's Sword
/cast Defensive Stance
```

### Equip Shield
```
/equipslot 17 Aegis of the Scarlet Commander
/equipslot 16 Vanquisher's Sword
```

### Equip 2-hand
```
/stopcasting [noworn:Two-Handed Axes]
/equip Whirlwind Axe
```

### Shield Block
```
#showtooltip Shield Block
/startattack [combat,harm,nodead]
/stopcasting [noworn:Shields]
/equipslot 17 Aegis of the Scarlet Commander
/equipslot 16 Vanquisher's Sword
/cast Shield Block
/cast Defensive Stance
```

### Shield Wall
```
#showtooltip Shield Wall
/startattack [combat,harm,nodead]
/stopcasting [noworn:Shields]
/equipslot 17 Aegis of the Scarlet Commander
/equipslot 16 Vanquisher's Sword
/cast Defensive Stance
/cast Shield Wall
```

### Shield Bash
```
#showtooltip Shield Bash
/startattack
/stopcasting [noworn:Shields]
/equipslot 17 Aegis of the Scarlet Commander
/equipslot 16 Vanquisher's Sword
/cast [form:3,worn:Shields] Battle Stance
/cast Shield Bash
```

### Shield Bash (mouseover)
```
#showtooltip Shield Bash
/startattack
/stopcasting [noworn:Shields]
/cast [form:3,worn:Shields] Battle Stance
/cast [@mouseover,harm,nodead][] Shield Bash
```

### Revenge
```
#showtooltip Revenge
/startattack
/cast Revenge
/cast Defensive Stance
```

### Pummel
```
#showtooltip Pummel
/startattack
/cast Berserker Stance
/cast Pummel
```

### Double Interupt
```
#showtooltip Pummel
/startattack
/cast [form:1/2,worn:Shields] Shield Bash
/cast [noworn:Shields] Berserker Stance
/cast [form:3] Pummel
```

### Double Interupt (mouseover)
```
#showtooltip Pummel
/startattack
/cast [form:1/2,worn:Shields,@mouseover,harm,nodead][form:1/2,worn:Shields] Shield Bash
/stopcasting [form:1/2,noworn:Shields]
/cast [noworn:Shields] Berserker Stance
/cast [form:3,@mouseover,harm,nodead][form:3] Pummel
```

### Whirlwind
```
#showtooltip Whirlwind
/startattack
/stopcasting [form:1/2]
/cast Berserker Stance
/cast Whirlwind
```

### Execute
```
#showtooltip Execute
/startattack
/stopcasting
/cast [form:2] Berserker Stance
/cast Execute
```

### Sweeping Strikes
```
#showtooltip Sweeping Strikes
/startattack
/stopcasting [form:2/3]
/cast Battle Stance
/cast Sweeping Strikes
```

### Sweeping Strikes+Bloodrage
```
#showtooltip Sweeping Strikes
/startattack
/stopcasting [form:2/3]
/cast Battle Stance
/cast [form:1,combat] Bloodrage
/cast Sweeping Strikes
```

### Blood Fury
```
#showtooltip Blood Fury
/cast Blood Fury
/startattack
```
<br>
<br>


## Shouts

### Demoralizing Shout
```
#showtooltip
/startattack
/cast Demoralizing Shout
```

### Challenging Shout
```
#showtooltip
/startattack
/cast Challenging Shout
```

### Battle Shout
```
#showtooltip
/startattack
/cast Battle Shout
```

### Bloodrage
```
#showtooltip
/startattack
/cast Bloodrage
```

### Berserker Rage
```
#showtooltip Berserker Rage
/startattack
/cast Berserker Rage
/cast Berserker Stance
```

### One-button ranged
```
#showtooltip
/cast [worn:Thrown] Throw; [worn:Bows] Shoot Bow; [worn:Guns] Shoot Gun; [worn:Crossbows] Shoot Crossbow
```

### Intimidating Shout
```
#showtooltip
/cleartarget [dead][help]
/targetenemy [noexists]
/stopattack
/cast Intimidating Shout
```

### Taunt (mouseover)
```
#showtooltip Taunt
/startattack [harm,nodead]
/cast Defensive Stance
/cast [@mouseover,harm,nodead][] Taunt
```

### Mocking Blow (mouseover)
```
#showtooltip Mocking Blow
/startattack
/cast Battle Stance
/cast [@mouseover,harm,nodead][] Mocking Blow
```

### Thunder Clap
```
#showtooltip Thunder Clap
/startattack
/cast Battle Stance
/cast Thunder Clap
```

### Retaliation
```
#showtooltip Retaliation
/startattack
/cast Battle Stance
/cast Retaliation
```

### Bloodthirst
```
#showtooltip
/startattack
/cast Bloodthirst
/cancelaura Arcane Intellect
/cancelaura Arcane Brilliance
```


# Tank Macros


### Sunder (Tank)
```
#showtooltip Sunder Armor
/startattack
/cast Defensive Stance
/cast Sunder Armor
/cancelaura Blessing of Salvation
/cancelaura Greater Blessing of Salvation
```

### Revenge (Tank)
```
#showtooltip Revenge
/startattack
/cast Defensive Stance
/cast Revenge
/cancelaura Blessing of Salvation
/cancelaura Greater Blessing of Salvation
```

### Shield Bash (Tank)
```
#showtooltip Shield Bash
/startattack
/stopcasting [noworn:Shields]
/equipslot 17 Aegis of the Scarlet Commander
/equipslot 16 Vanquisher's Sword
/cast Defensive Stance
/cast Shield Bash
```

### OH SHIT button
```
/use 13
/use 14
/cast Defensive Stance
/cast Shield Wall
```

### Hamstring (Tank)
```
#showtooltip Hamstring
/startattack
/cast [form:2] Battle Stance
/cast Hamstring
```

### Rend (Tank)
```
#showtooltip Rend
/startattack
/cast [form:3] Defensive Stance
/cast Rend
```