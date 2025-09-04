
---

# 📜 WoW 3.3.5 Macro Compendium (Project Epoch)

This is a comprehensive guide to the **macro and communication system** in the **3.3.5 client**. <br>
Project Epoch inherits all of these features.

---

## Table of Contents
- [Project Epoch knowledge Sources](#project-epoch-knowledge-sources)
- [Recommended Addons](#recommended-addons)
- [How-to Macro](#-how-to-macro)
    - [Macro Commands](#-1-macro-commands)
    - [Targeting & Substitutions](#-2-targeting--substitutions)
    - [Conditionals](#-3-conditionals)
    - [Communication API Functions](#-4-communication-api-functions)
    - [Combat-Legal Lua](#-5-combat-legal-lua)
    - [Communication Macro Toolkit](#-6-communication-macro-toolkit)
    - [Communication Examples (All Classes)](#-7-communication-examples-all-classes)
    - [Quick Reference](#-8-quick-reference)
    - [Special Notes](#-9-special-notes)
- [Druid Macros](#-druid-macros)
- [Hunter Macros](#-hunter-macros)
- [Mage Macros](#-mage-macros)
- [Paladin Macros](#-paladin-macros)
- [Priest Macros](#-priest-macros)
- [Rogue Macros](#-rogue-macros)
- [Shaman Macros](#-shaman-macros)
- [Warlock Macros](#-warlock-macros)
- [Warrior Macros](#-warrior-macros)
- [Universal Macros](#-universal-macros)
- [**Buy me a Coffee**](#-Buy-me-a-coffee)

<br>
<br>
<br>

## Project Epoch knowledge sources
Official Website - https://www.project-epoch.net/ <br>
Official Discord - https://discord.com/invite/mzCSaZYWuC <br>
Server Status - https://project-epoch-status.com/ <br>
Unofficial Wiki - https://project-epoch-wow.fandom.com/wiki/Project_Epoch_Wiki <br>
Official Github repository - https://github.com/Project-Epoch  <br>

## Recommended Addons
https://project-epoch-wow.fandom.com/wiki/AddOns

<br>
<br>
<br>




# 📜 How-To Macro

## 🔹 1. Macro Commands

Macros are built from **slash commands**, sometimes with **conditionals** (`[ ]`) or **Lua** (`/run` or `/script`).

| Command                                                                                  | Description                                                      |
| ---------------------------------------------------------------------------------------- | ---------------------------------------------------------------- |
| `/cast`                                                                                  | Casts a spell.                                                   |
| `/use`                                                                                   | Uses an item, trinket, or ability.                               |
| `/castsequence`                                                                          | Casts spells in a defined sequence (can reset with time/target). |
| `/target`                                                                                | Selects a target by name or condition.                           |
| `/assist`                                                                                | Targets your target’s target.                                    |
| `/focus`                                                                                 | Sets your focus target.                                          |
| `/clearfocus`                                                                            | Clears your focus target.                                        |
| `/petattack`, `/petfollow`, `/petstay`, `/petpassive`, `/petdefensive`, `/petaggressive` | Pet commands.                                                    |
| `/stopcasting`                                                                           | Stops your current spellcast.                                    |
| `/stopattack`                                                                            | Stops auto-attacking.                                            |
| `/startattack`                                                                           | Starts auto-attacking.                                           |
| `/cancelaura`                                                                            | Removes a buff/debuff.                                           |
| `/cancelqueuedspell`                                                                     | Cancels a queued “on-next-swing” spell (e.g., Heroic Strike).    |
| `/equip` / `/equipslot`                                                                  | Equips an item (optionally in a slot).                           |
| `/swapactionbar`                                                                         | Switches to another action bar (1–6).                            |
| `/click`                                                                                 | Activates another action button (chain macros).                  |
| `/run` or `/script`                                                                      | Executes Lua code. (Protected functions are blocked.)            |

---

## 🔹 2. Targeting & Substitutions

### `@unit` (or `[target=unit]`)

* `@target` → current target
* `@focus` → focus target
* `@mouseover` → unit under mouse (model or frame)
* `@player` → yourself
* `@pettarget` → your pet’s target
* `@party1` … `@party4` → party members
* `@raid1` … `@raid40` → raid members
* `@arena1` … `@arena5` → arena enemies
* `@boss1` … `@boss4` → boss units

💡 `@unit` and `[target=unit]` are **interchangeable** in 3.3.5.

---

### `% substitutions` (chat/emotes only)

* `%t` → name of your target
* `%f` → name of your focus
* `%m` → name of your mouseover

Example:

```
/y Attacking %t next!
```

---

## 🔹 3. Conditionals

Conditionals go inside `[ ]`.

* **Commas (`,`)** = AND logic.
* **Semicolons (`;`)** = OR logic (priority order).

Example:

```
/cast [mod:shift,@focus,harm,nodead][] Polymorph
```

→ Polymorphs focus if Shift held, otherwise your target.

---

### Target Conditionals

* `exists` → Target exists
* `help` → Target is friendly
* `harm` → Target is hostile
* `dead` / `nodead` → Target dead/alive
* `party` → Target in your party
* `raid` → Target in your raid
* `group` → You are in a group
* `nogroup` → You are solo

---

### Player State

* `combat` / `nocombat` → In combat / not in combat
* `mounted` / `nomounted` → Mounted / not mounted
* `stealth` → In stealth
* `swimming` → Swimming
* `flying` → Flying
* `indoors` / `outdoors` → Indoors / outdoors
* `equipped:slot` → Equipped item in slot (or type, e.g. `equipped:Shields`)

---

### Pet

* `pet` → You have a pet
* `nopet` → You don’t have a pet
* `pet:NAME` → Specific pet type (e.g., `pet:Imp`)

---

### Modifiers

* `mod:shift`, `mod:ctrl`, `mod:alt` → Modifier key pressed
* `nomod` → No modifier pressed
* `mod` → Any modifier pressed

---

### Stances & Forms

* **Warrior**: `stance:1` Battle, `stance:2` Defensive, `stance:3` Berserker
* **Druid**: `form:1` Bear, `form:2` Aquatic, `form:3` Cat, `form:4` Travel, `form:5` Moonkin/Tree, `form:6` Flight
* **Rogue**: `stance:0` Unstealthed, `stance:1` Stealth
* **Priest**: `stance:1` Shadowform

---

### Action Bar / Bonus Bars

* `bar:1` … `bar:6` → Which action bar is active
* `bonusbar:X` → Special action bars (stances, stealth, druid forms)

---

### Special Conditionals

* `channeling:SpellName` → If you are channeling that spell
* `equipped:ItemType` → Type equipped (e.g. Shields, Daggers)
* `flyable` → Zone allows flying mounts

---

## 🔹 4. Communication API Functions

These Lua functions can be called inside macros with `/run`.

### `SendChatMessage(message, chatType, language, target)`

* Sends a chat message.
* `chatType` → `"SAY"`, `"YELL"`, `"PARTY"`, `"RAID"`, `"RAID_WARNING"`, `"WHISPER"`, `"CHANNEL"`, `"GUILD"`, `"OFFICER"`, `"EMOTE"`
* `language` → `"Common"`, `"Orcish"`, etc. (or `nil`)
* `target` → player name (for whispers) or channel number (for channels)

---

### `SendAddonMessage(prefix, message, distribution, target)`

* Sends hidden addon messages.
* `distribution` → `"PARTY"`, `"RAID"`, `"GUILD"`, `"BATTLEGROUND"`, `"WHISPER"`
* `prefix` → up to 16 chars
* `target` → player name (for whispers only)

---

### `DoEmote(emote, target, hold)`

* Performs an emote.
* `emote` → string (e.g. `"cheer"`, `"wave"`)
* `target` (optional) → player name
* `hold` (optional) → loop flag

---

### `Emote(emoteToken)`

* Alias for `DoEmote`.

---

### `DEFAULT_CHAT_FRAME:AddMessage(text, r, g, b)`

* Prints text locally in your chat window.
* `r, g, b` → numbers between 0–1 for color.

---

### Supporting Unit Functions

* `UnitName(unit)` → Name of unit
* `UnitClass(unit)` → Class name & token
* `UnitRace(unit)` → Race name
* `UnitLevel(unit)` → Unit level
* `UnitIsPlayer(unit)` → True if player
* `UnitExists(unit)` → True if exists

---

## 🔹 5. Combat-Legal Lua

In combat, **secure functions are blocked** (e.g., auto-targeting, changing action bars),
but you can still use communication and query functions.

✅ Allowed in combat:

* `SendChatMessage`
* `SendAddonMessage`
* `DoEmote` / `Emote`
* `DEFAULT_CHAT_FRAME:AddMessage`
* `Unit*` queries (UnitName, UnitExists, etc.)

❌ Blocked in combat:

* Protected actions (auto-targeting, casting spells via Lua).

---

### Combat-safe Examples

**Announce your target:**

```lua
/run if UnitExists("target") then SendChatMessage("Attacking "..UnitName("target").."!", "SAY") end
```

**Raid warning:**

```lua
/run SendChatMessage("Bloodlust used!", "RAID_WARNING")
```

**Whisper focus:**

```lua
/run if UnitExists("focus") then SendChatMessage("I will CC you — don’t resist!", "WHISPER", nil, UnitName("focus")) end
```

**Emote at target:**

```lua
/run DoEmote("cheer", UnitName("target"))
```

**Debug message (local only):**

```lua
/run DEFAULT_CHAT_FRAME:AddMessage("Macro fired!",0,1,0)
```

---

## 🔹 6. Communication Macro Toolkit

Here are practical templates you can adapt:

**1. Sheep announce (party & raid)**

```
/cast [@focus,harm,nodead] Polymorph
/run if UnitExists("focus") then SendChatMessage("Polymorph on "..UnitName("focus").." — do NOT break!", "PARTY") end
```

**2. Mouseover heal announce**

```
/cast [@mouseover,help,nodead][] Flash Heal
/run if UnitExists("mouseover") then SendChatMessage("Healing "..UnitName("mouseover").."!", "SAY") end
```

**3. Trinket usage announce**

```
/use 13
/run SendChatMessage("Trinket activated!", "RAID")
```

**4. Kill target callout**

```
/run if UnitExists("target") and UnitIsPlayer("target") then SendChatMessage("Kill "..UnitName("target").." NOW!", "RAID_WARNING") end
```

**5. Addon communication (whisper)**

```
/run SendAddonMessage("MYADDON", "hello", "WHISPER", UnitName("party1"))
```

<br>

## 🔹 7. Communication Examples (All Classes)

* **Generic raid warning:**

```lua
/run SendChatMessage("Cooldowns NOW!", "RAID_WARNING")
```

* **Whisper a healer:**

```lua
/run SendChatMessage("I'm low HP, help!", "WHISPER", nil, "HealerName")
```

* **Addon sync (hidden comms):**

```lua
/run SendAddonMessage("MYADDON","readycheck","RAID")
```

* **Custom emote:**

```lua
/run DoEmote("dance", UnitName("target"))
```


<br>
<br>


## 🔹 8. Quick Reference

<br>

### **Slot IDs**

---

| Slot ID | Slot Name      | Slot ID | Slot Name       |
|---------|----------------|---------|-----------------|
| 0       | Ammo           | 10      | Hands           |
| 1       | Head           | 11      | Finger 1        |
| 2       | Neck           | 12      | Finger 2        |
| 3       | Shoulder       | 13      | Trinket 1       |
| 4       | Shirt          | 14      | Trinket 2       |
| 5       | Chest          | 15      | Back            |
| 6       | Waist          | 16      | Main hand       |
| 7       | Legs           | 17      | Off hand        |
| 8       | Feet           | 18      | Ranged / Relic  |
| 9       | Wrist          | 19      | Tabard          |
---
<br>


### **Commands**
---

| Command | Description |
|---------|-------------|
| #show * | Show the icon of a spell, item, or macro condition |
| #showtooltip * | Show the tooltip and icon of a spell, item, or macro condition |
| /assist | Target the same target as a party or raid member |
| /cancelaura | Remove a buff or debuff from yourself |
| /cancelform | Cancel your current stance/form (e.g., Druid forms) |
| /cast | Cast a spell by name |
| /castrandom | Cast a random spell from a list |
| /castsequence | Cast spells in a specific sequence |
| /changeactionbar | Switch action bar pages |
| /clearfocus | Clear your focus target |
| /cleartarget | Clear your current target |
| /click | Simulate clicking a UI button |
| /dismount | Dismount |
| /equip + | Equip an item by name |
| /equipslot + | Equip an item into a specific slot |
| /equipset + | Equip a saved equipment set |
| /focus | Set a focus target |
| /petaggressive | Set your pet to aggressive mode |
| /petattack | Order your pet to attack your target |
| /petautocastoff | Turn off a pet ability autocast |
| /petautocaston | Turn on a pet ability autocast |
| /petdefensive | Set your pet to defensive mode |
| /petfollow | Order your pet to follow you |
| /petpassive | Set your pet to passive mode |
| /petstay | Order your pet to stay in place |
| /startattack | Begin auto-attacking your target |
| /stopattack | Stop auto-attacking |
| /stopcasting | Interrupt your current cast |
| /stopmacro | Stop executing the current macro |
| /swapactionbar | Swap action bars (page switching) |
| /target | Target a specific unit |
| /targetenemy | Target the nearest enemy |
| /targetenemyplayer | Target the nearest enemy player |
| /targetfriend | Target the nearest friendly unit |
| /targetlasttarget | Target your previous target |
| /targetparty | Target a party member |
| /targetraid | Target a raid member |
| /use | Use an item or equipment slot |
| /usetalents + | Activate a talent spec via the in-game talent system |
| /userandom | Use a random spell or item from a list |
---


<br>


### **Conditionals**

--- 

| Conditional | Description |
|-------------|-------------|
| actionbar:1/.../6 or bar:1/.../6 | Given action bar page is selected |
| bonusbar:5 | The possess bar is active (controlling a vehicle or another player) |
| button:1/.../5/<virtual click> or btn:1/.../5/<virtual click> | Macro activated with the given mouse button |
| channeling:<spell name> | Channeling the given spell |
| combat | In combat |
| cursor | What the cursor is currently holding (see API_GetCursorInfo for types) |
| dead | Target is dead |
| equipped:<item type> or worn:<item type> | Item type is equipped (can be an inventory slot, item type, or subtype) |
| exists | Target exists |
| flyable | In a zone where flying is allowed (does not check if you have flying skill) |
| flying | Mounted or in flight form AND in the air |
| group:party/raid | You are in the given type of group |
| harm | Can cast harmful spells on the target |
| help | Can cast helpful spells on the target |
| indoors | Indoors |
| modifier:shift/ctrl/alt or mod:shift/ctrl/alt | Holding the given key |
| mounted | Mounted |
| outdoors | Outdoors |
| party | Target is in your party |
| pet:<pet name or type> | The given pet is out |
| raid | Target is in your raid/party |
| spec:1/2 | Currently active class specialization |
| stance:0/1/2/.../n or form:0/.../n | In a stance or form |
| stealth | Stealthed |
| swimming | Swimming |
| talent:<tier#>/<column#> | Talent from column# of tier# is selected |
| unithasvehicleui | The target of the macro has vehicle UI |
| vehicleui | The player has vehicle UI |
---

<br>
<br>
<br>

## ✅ 9. Special Notes

- Macro system in 3.3.5: /cast, /use, /castsequence, /focus, /click, /run
- You can’t **condition on health/mana values** in 3.3.5 macros (protected functions).
- **[target=]** and **@** are **fully interchangeable**.
Example: /cast [target=mouseover] Heal is the same as /cast [@mouseover] Heal.
- %t, %f, %m only expand in **chat/emote macros**, never in /cast.
- Most macros can only execute **one GCD ability per press** — no automation beyond that.
- Some servers (including private ones like Epoch) may restrict **SendChatMessage** in macros to prevent automation abuse.
- Messages are **rate-limited by the server** (spam throttling).
- You cannot send hidden “programmatic whispers” — the **user must trigger the macro**.
- Protected functions (like automatically picking targets or sending messages without input) are **blocked** by Blizzard’s secure environment.

<br>
<br>
<br>

---

# 📜 Druid Macros

---

### Bash
```
#showtooltip Bash
/cast [noform:1] Bear Form(Shapeshift)
/cast Bash
```

### Bear Frenzied Regeneration + Barkskin
```
/cast Barkskin
/cast Frenzied Regeneration
```

### Cat
```
#showtooltip
/cast !Cat Form
/startattack
```

### Cyclone

```
/cast [@focus,harm,nodead] Cyclone
```
* Focus only

### Cyclone
```
#showtooltip Cyclone
/stopcasting
/cast [@mouseover,harm,nodead][@focus,harm,nodead][] Cyclone
```
* Mouseover > Focus > Target

### Cyclone
```
#showtooltip Cyclone
/stopcasting
/cast War Stomp
/cast [@mouseover,harm,nodead][@focus,harm,nodead][] Cyclone
```
* Mouseover > Focus > Target - With War Stomp

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

### Entangling Roots
```
#showtooltip Entangling Roots
/stopcasting
/cast [@mouseover,harm,nodead][@focus,harm,nodead][] Entangling Roots
```

### Faerie Fire
```
#showtooltip
/cast [nomod,stance:1] Faerie Fire (Feral)
/cast [nomod,stance:3] Faerie Fire (Feral)
/cast Faerie Fire
```

### Feral Charge
```
#showtooltip Feral Charge
/cancelform [noform:1]
/cast [noform:1] Dire Bear Form
/cast Feral Charge
```
* needs doubleclicking

### Growl
```
#showtooltip Growl
/cast [@mouseover,harm,form:1][@target,harm,form:1] Growl
```

### Hibernate
```
#showtooltip Hibernate
/stopcasting
/cast [@mouseover,harm,nodead][@focus,harm,nodead][] Hibernate
```

### Innervate (untested)
```
#showtooltip Innervate
/cast [@mouseover,help,nodead][@target,help,nodead][] Innervate 
```

### Mark of the Wild / Gift of the Wild
```
#showtooltip
/cast [group] Gift of the Wild; Mark of the Wild
```
* Cast Gift of the Wild if you are in a group
* Cast Mark of the Wild if you are solo

### Pounce / Rake
```
#showtooltip
/cast [nostealth] Rake; [stealth] Pounce
```

### Pounce / Maim
```
#showtooltip
/cast [stealth] Pounce; [nostealth] Maim
```

### Powershift
```
#showtooltip
/cast !Cat Form
/startattack [form:3,harm,nodead]
```

### Prowl
```
#showtooltip Prowl
/cancelform [noform:3]
/cast [noform:3] Cat Form
/cast !Prowl
```
* needs doubleclicking - spammable

### Ravage / Shred
```
#showtooltip
/cast [stealth] Ravage; [nostealth] Shred
```

### Rebirth / Revive
```
#showtooltip Rebirth
/stopcasting
/cast [combat] Rebirth ; Revive
```

### Rebirth with raid announce
```
/cast [@mouseover,help,dead] Rebirth
/run if UnitExists("mouseover") then SendChatMessage("Battle-ressing "..UnitName("mouseover").."!", "RAID_WARNING") end
```

### Travel Form
```
#showtooltip
/cast [swimming] !Aquatic Form;[outdoors] !Travel Form; !Cat Form
```

<br>
<br>

## Needs testing - will edit based on results

### Bear Heal
```
#showtooltip Dire Bear Form
/use Enrage
/cast [noform:1] !Dire Bear Form
/cast Frenzied Regeneration
/use Major Healing Potion
/cancelaura Enrage
```
* Double-tap - uses enrage and then cancels enrage at the end to cancel armor reduction

### Feral Charge
```
#showtooltip Feral Charge
/cast [noform:1] !Dire Bear Form
/cast [@mouseover,harm,nodead][@focus,harm,nodead][] Feral Charge
```

### Innervate
```
#showtooltip Innervate
/cast [help] Innervate
/script SendChatMessage("innervated.", "WHISPER", nil, UnitName("target"))
```
* Target with whisper

### Innervate
```
#showtooltip Innervate
/cast [@mouseover,help,nodead][] Innervate 
/script SendChatMessage("innervated.", "WHISPER", nil, UnitName("mouseover"))
```
* Mouseover with whisper

### Rebirth / Revive
```
#showtooltip Rebirth
/stopmacro [nohelp,nodead]
/run c="Resurrecting %t"if UnitInRaid("player")then SendChatMessage(c, "RAID")elseif GetNumPartyMembers()>0 then SendChatMessage(c, "PARTY")end
/cast [combat] Rebirth ; Revive
```

<br>
<br>
<br>

---

# 📜 Hunter Macros

---


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

### Misdirection macro
```
/cast [@focus,help][@pet,exists] Misdirection
```
* Casts on focus if friendly, else on pet.

### Pet attack / follow toggle
```
/petattack [@target,harm]
/petfollow [@target,noexists]
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

### Scatter + trap
```
/cast Scatter Shot
/cast [@focus] Freezing Trap
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

<br>
<br>
<br>
<br>

---

# 📜 Mage Macros

---

### Arcane Blast
```
#showtooltip Arcane Blast
/cast Arcane Blast
```
* Can also be used with [nochanneling : Arcane Missiles]

### Blizzard
```
#showtooltip Blizzard
/cast Blizzard
```

### Counterspell
```
#showtooltip Counterspell
/stopcasting
/cast [@mouseover,harm,nodead][@focus,harm,nodead] Counterspell
```

### Evocation self-cancel

```
/cast Evocation
/stopcasting
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
/cast !Ice Block
/cancelaura Ice Block
```

### Polymorph
```
#showtooltip Polymorph
/cast [@mouseover,harm,nodead][@focus,harm,nodead][] Polymorph
```

### Polymorph focus + announce

```
/cast [@focus,harm,nodead] Polymorph
/run if UnitExists("focus") then SendChatMessage("Sheeping "..UnitName("focus").." — do NOT break!","PARTY") end
```

### Ritual of Refreshment(Rank 1)
```
#showtooltip Ritual of Refreshment(Rank 1)
/cast Ritual of Refreshment(Rank 1)
```

<br>
<br>
<br>
<br>

---

# 📜 Paladin Macros

---

### Avenging Wrath
```
#showtooltip Avenging Wrath
/use 13
/use 14
/cast Avenging Wrath
```
* Popping all cooldowns

### Bubble + cancel
```
/cast Divine Shield
/cancelaura Divine Shield
```
* First press bubbles, second press cancels.

### Cleanse
```
#showtooltip
/cast [@mouseover,help,nodead][@target,help,nodead][@player][] Cleanse
```
* Cleanse mouseover > Target > Self

### Crusader Strike
```
#showtooltip Crusader Strike
/cast Crusader Strike
/startattack
```

### Divine Shield
```
#showtooltip
/cancelaura Divine Shield
/cast Divine Shield
```

### Hand of Freedom
```
#showtooltip Hand of Freedom
/cast [@mouseover,help,nodead][@target,help,nodead][@player][] Hand of Freedom
```
* Mouseover

### Hand of Protection
```
#showtooltip Hand of Protection 
/cast [@mouseover,help,nodead][] Hand of Protection
```
* Mouseover

### Hammer Of Justice
```
#showtooltip Hammer of Justice
/stopcasting
/cast Hammer of Justice
```

### Hammer of Justice (focus)
```
/cast [@focus,harm,nodead][] Hammer of Justice
```

### Holy Light
```
#showtooltip
/cast [@mouseover,help,nodead] Holy Light
```
* Mouseover

### Holy Shock
```
#showtooltip Holy Shock
/cast [@mouseover,help,nodead][help,nodead][harm,nodead] Holy Shock
```
* Mouseover

### Judgement
```
#showtooltip Judgement
/startattack
/use 14
/cast Judgement
/cast Seal of Command(Rank 1)
```

### Righteous Defense
```
#showtooltip
/cast [exists,help,nodead][@mouseover,exists,help,nodead][exists,harm,nodead,target=targettarget] Righteous Defense; Righteous Defense
```
* Attempts to taunt, in order, target -> mouseover friendly -> targets target

### Righteous Defense (Eighty rewrite)
```
#showtooltip
/cast [exists,help,nodead][@mouseover,help,nodead][@targettarget,harm,nodead] Righteous Defense
```
* Attempts to taunt, in order, target -> mouseover friendly -> targets target


### Seal of Command
```
#showtooltip Seal of Command
/cast Seal of Command
/startattack
```

### Seal of Command
```
#showtooltip Seal of Command
/cast Avenging Wrath
/use 13
/use 14
/cast Seal of Command
/startattack
```
* With popping cooldowns. Change/remove trinkets based on equipped items.

<br>
<br>
<br>
<br>


---

# 📜 Priest Macros

---


### Binding Heal
```
#showtooltip Binding Heal
/cast [@mouseover,help,nodead][] Binding Heal
```
* Cast on mouseover if present, otherwise on target or self.

### Dispel 
```
#showtooltip
/cast [@player] Dispel Magic
```
* Dispel self without losing target

### Dispel Magic on focus
```
/cast [@focus,help,nodead][] Dispel Magic
```

### Flash Heal
```
#showtooltip Flash Heal
/cast [@mouseover,help,nodead][] Flash Heal
```
* Cast on mouseover if present, otherwise on target or self.

### Greater Heal
```
#showtooltip Greater Heal
/cast [@mouseover,help,nodead][] Greater Heal
```
* Cast on mouseover if present, otherwise on target or self.

### Mass Dispel
```
#showtooltip
/cast !Mass Dispel
```
* Places targeting circle at cursor for quick use.


### Mind Blast
```
#showtooltip Mind Blast
/use 13
/use 14
/cast Inner Focus
/cast Mind Blast
```

### Mind Flay
```
#showtooltip
/cast [nochanneling:Mind Flay] Mind Flay
```
* Cast Mind Flay, unless already channeling

### Pain Suppression
```
#showtooltip Pain Suppression
/cast [@mouseover,help,nodead][@focus,help,nodead][] Pain Suppression
```
* Cast on mouseover if present, then on focus if present, otherwise on target or self.

### Power Word: Shield
```
#showtooltip Power Word: Shield
/cast [@mouseover,help,nodead][] Power Word: Shield
```
* Cast on mouseover if present, otherwise on target or self.

### Powerr Infusion
```
#showtooltip Power Infusion
/cast [@mouseover,noharm,nodead][] Power Infusion
```
* Cast on mouseover if present, otherwise on target or self.

### Prayer of Healing
```
#showtooltip Prayer of Healing
/stopcasting
/cast Prayer of Healing
```

### Prayer of Mending
```
#showtooltip Prayer of Mending
/cast [@mouseover,help,nodead][@focus,help,nodead][] Prayer of Mending
```
* Cast on mouseover if present, then on focus if present, otherwise on target or self.


### Psychic Horror 
```
#Showtooltip Psychic Horror
/cast [@mouseover,harm][harm] Psychic Horror
```
* Mouseover -> target prioritization

### Psychic Horror
```
#Showtooltip Psychic Horror
/cast [@focus,harm] Psychic Horror
```
* Focustarget

### Renew
```
#showtooltip Renew
/cast [@mouseover,help,nodead][] Renew
```
* Cast on mouseover if present, otherwise on target or self.

### Shadowform
```
#showtooltip
/cast !Shadowform
```
* Spammable - it won't drop you out of form after you're in shadowform.

### Shadow Word: Death
```
#showtooltip Shadow Word: Death
/stopcasting
/cast Inner Focus
/cast Shadow Word: Death
```

### Shadow Word: Death self-break
```
/cast [@player] Shadow Word: Death
```
* Useful to break CC.

### Shadow Word: Pain
```
#showtooltip Shadow Word: Pain
/use 13
/use 14
/cast [@mouseover,harm,nodead][] Shadow Word: Pain
```

### Silence
```
#showtooltip
/cast [@mouseover,harm][harm] Silence
```
* Mouseover -> target prioritization

### Silence
```
#showtooltip
/cast [@focus,harm] Silence
```
* Focustarget

### Wand
```
/cast !Shoot
```
* Spammable

<br>
<br>
<br>
<br>

---

# 📜 Rogue Macros

---


### Adrenaline Rush
```
#showtooltip Adrenaline Rush
/use 14
/startattack
/cast Adrenaline Rush
```

### Apply Poison
```
#showtooltip Deadly Poison IX
/use Deadly Poison IX;
/use [button:1] 16; [button:2] 17;
/click StaticPopup1Button1
```
* Left + Right mouse button click

### Backstab
```
#showtooltip
/startattack
/cast Backstab
```
```
#showtooltip
/cast Backstab
```

### Blade Flurry
```
#showtooltip Blade Flurry
/startattack
/cast Cold Blood
/cast Blade Flurry
/cast Adrenaline Rush
```

### Blind
```
#showtooltip Blind
/cast [@mouseover,harm,nodead][@focus,harm,nodead][] Blind
```

### In-Combat Cheap Shot
```
#showtooltip Stealth
/dismount
/cast !stealth
/cast [@target] Cheap Shot
```
* ShotDismount, stealth if not in stealth, Cheap Shot if player has a target <br>
Spam for success

### In-Combat Cheap Shot - trinket
```
/use 13
/use 14
/cast Vanish
/cast Shadowstep
/cast [@target] Cheap Shot
```
* Trinket, Shadowstep, Cheap Shot. Great when being opened on


### In-Combat Sap
```
#showtooltip Stealth
/dismount
/cast !stealth
/cast [@target] Sap
```
* Dismount, stealth if not in stealth, Sap if player has a target <br>
Spam for success

### In-Combat Sap (Shadowstep)
```
#showtooltip Shadowstep
/cast !stealth
/cast [@target] Shadowstep
/cast [@target] Sap
```
* Shadowstep, stealth if not in stealth, Sap if player has a target <br>
Spam for success

### Kick
```
#showtooltip Kick
/startattack
/cast [@mouseover,exists][@focus,exists][] Kick
```

### Pickpocket
```
#showtooltip Pick Pocket
/targetenemy [noharm][dead]
/cast Pick Pocket
/cleartarget
```

### Poison Application
```
#showtooltip
/use Crippling Poison II
/use 16
```
```
#showtooltip
/use Instant Poison VI
/use 16
```

### Redirect / Kidney Shot
```
#showtooltip
/castsequence [mod:shift][] Redirect, Kidney Shot
```

### Riposte / Sinister Strike
```
#showtooltip
/startattack
/cast [mod:shift] Riposte; Sinister Strike

```

### Sap closest enemy
```
#showtooltip Sap
/cleartarget
/targetenemyplayer
/cast Sap
```

### Sap (focus)
```
/cast [@focus,harm,nodead][] Sap
```

### Stealth toggle
```
/cast [nostealth] Stealth
/cancelaura [stealth] Stealth
```

### Sinister Strike
```
/startattack
/cast Sinister Strike
```

### Vanish + announce
```
/cast Vanish
/run SendChatMessage("VANISHED — reset fight!", "PARTY")
```

<br>
<br>
<br>
<br>


---

# 📜 Shaman Macros

---

### Bloodlust announce
```
/cast Bloodlust
/run SendChatMessage("BLOODLUST ACTIVATED!", "RAID_WARNING")
```

### Call of the Ancestors
```
#showtooltip Call of the Ancestors
/dismount
/startattack
/cast Call of the Ancestors
```

### Call of the Elements
```
#showtooltip Call of the Elements
/dismount
/startattack
/cast Call of the Elements
```

### Chain Heal
```
#showtooltip Chain Heal
/cast [@mouseover,nodead,help][] Chain Heal
```
* Cast on mouseover if present, otherwise on target or self.

### Chain Lightning
```
#showtooltip Chain Lightning
/use 13
/use 14
/cast Chain Lightning
```

### Earth Shock
```
#showtooltip Earth Shock
/use 13
/use 14
/cast [@mouseover,nodead,harm][@target,nodead,harm][] Earth Shock
```

### Earth Shield
```
#showtooltip Earth Shield
/cast [@mouseover,nodead,help][@focus,nodead,help][] Earth Shield; 
```
* Cast on mouseover if present, then on focus if present, otherwise on target or self.

### Elemental Mastery
```
#showtooltip Elemental Mastery
/use 14
/cast Elemental Mastery
```

### Flame Shock
```
#showtooltip Flame Shock
/use 13
/use 14
/cast Flame Shock
```

### Healing Wave
```
#showtooltip Healing Wave
/cast [@mouseover,nodead,help][] Healing Wave
```
* Cast on mouseover if present, otherwise on target or self.

### Healing Wave - NS
```
#showtooltip
/stopcasting
/cast Nature's Swiftness
/use 13
/use 14
/cast [@mouseover,nodead,help][] Healing Wave
```
* Cast on mouseover if present, otherwise on target or self.

### Lesser Healing Wave
```
#showtooltip Lesser Healing Wave
/cast [@mouseover,nodead,help][] Lesser Healing Wave
```
* Cast on mouseover if present, otherwise on target or self.

### Lightning Bolt
```
#showtooltip Lightning Bolt
/use 13
/use 14
/cast Lightning Bolt
```

### Purge
```
#showtooltip
/stopcasting
/cast [@mouseover,nodead][@target,nodead][] Purge
```

### Stormstrike
```
#showtooltip Stormstrike
/dismount
/startattack
/use 13
/use 14
/cast Stormstrike
```

### Wind Shear focus
```
/cast [@focus,harm,nodead] Wind Shear
```

<br>
<br>
<br>
<br>


---

# 📜 Warlock Macros

---


### Banish Focus
```
#showtooltip Banish
/use [@focus][] Banish
```

### Banish mouseover
```
/cast [@mouseover,harm][] Banish
```

### Demonic Circle
```
#showtooltip
/stopcasting
/cast Demonic Circle
```

### DoT Mouseover Example
```
#showtooltip Corruption
/use [@mouseover,harm] [harm] Corruption
```
* "Corruption" can be replaced with any DoT.

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

### Fear Focus
```
/cast [@focus,harm,nodead] Fear
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

### Pet Spell Lock (focus)
```
/cast [@focus,harm,nodead][] Spell Lock
```

### Rain of Fire
```
#showtooltip Rain of Fire
/cast [@cursor] Rain of Fire
```
* Cast at cursor.

### Ritual of Souls
```
#showtooltip Ritual of Souls
/s Click Please!
/cast Ritual of Souls
```

### Shadow Bolt Rank 1 
```
#showtooltip
/cast [@mouseover,harm,nodead][] Shadow Bolt(Rank 1)
```

### Soulstone announce
```
/cast [@mouseover,help,nodead][] Soulstone
/run if UnitExists("mouseover") then SendChatMessage("Soulstoned "..UnitName("mouseover").."!", "RAID") end
```
* Mouseover > Target > Self

<br>
<br>
<br>
<br>


---

# 📜 Warrior Macros

---


### Battle Shout
```
#showtooltip
/startattack
/cast Battle Shout
```

### Berserker Rage
```
#showtooltip Berserker Rage
/startattack
/cast Berserker Rage
/cast Berserker Stance
```
### Blood Fury
```
#showtooltip Blood Fury
/cast Blood Fury
/startattack
```

### Bloodrage
```
#showtooltip
/startattack
/cast Bloodrage
```

### Bloodthirst
```
#showtooltip
/startattack
/cast Bloodthirst
```

### Charge
```
#showtooltip
/startattack
/cast Battle Stance
/cast Charge
```

### Charge + Intercept + Intervene (stance dance) - **untested**
```
/cast [stance:1/2] Charge; [stance:3] Intercept; [help] Intervene
```
* Uses correct ability depending on stance and target.


### Charge/Hamstring
```
#showtooltip
/cast Battle Stance
/cast Charge
/cast Hamstring
/startattack
```


### Charge/Overpower
```
#showtooltip Overpower
/startattack
/cast Battle Stance
/cast Charge
/cast Overpower
```

### Charge/Overpower (mouseover)
```
#showtooltip Overpower
/startattack
/cast Battle Stance
/cast Charge
/cast [@mouseover,harm,nodead][] Overpower
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

### Double Interrupt
```
#showtooltip Pummel
/startattack
/cast [form:1/2,worn:Shields] Shield Bash
/cast [noworn:Shields] Berserker Stance
/cast [form:3] Pummel
```

### Double Interrupt (mouseover)
```
#showtooltip Pummel
/startattack
/cast [form:1/2,worn:Shields,@mouseover,harm,nodead][form:1/2,worn:Shields] Shield Bash
/stopcasting [form:1/2,noworn:Shields]
/cast [noworn:Shields] Berserker Stance
/cast [form:3,@mouseover,harm,nodead][form:3] Pummel
```

### Equip Shield+Defensive form
```
/equipslot 17 Aegis of the Scarlet Commander
/equipslot 16 Vanquisher's Sword
/cast Defensive form
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

### Execute
```
#showtooltip Execute
/startattack
/stopcasting
/cast [form:2] Berserker Stance
/cast Execute
```


### Hamstring
```
#showtooltip Hamstring
/startattack
/cast [form:2] Berserker Stance
/cast Hamstring
```

### Hamstring (Tank)
```
#showtooltip Hamstring
/startattack
/cast [form:2] Battle Stance
/cast Hamstring
```

### Heroic Strike
```
#showtooltip
/cast Heroic Strike
/startattack
```

### Intercept
```
#showtooltip Intercept
/startattack
/cast Berserker Stance
/cast Intercept
```

### Intimidating Shout
```
#showtooltip
/cleartarget [dead][help]
/targetenemy [noexists]
/stopattack
/cast Intimidating Shout
```

### Mocking Blow (mouseover)
```
#showtooltip Mocking Blow
/startattack
/cast Battle Stance
/cast [@mouseover,harm,nodead][] Mocking Blow
```

#### Mortal Strike
```
#showtooltip
/startattack
/cast Mortal Strike
```

### OH SHIT button
```
/use 13
/use 14
/cast Defensive Stance
/cast Shield Wall
```

### Rend
```
#showtooltip Rend
/startattack
/cast [form:3] Battle Stance
/cast Rend
```

### Rend (Tank)
```
#showtooltip Rend
/startattack
/cast [form:3] Defensive Stance
/cast Rend
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

### Sunder Armor
```
#showtooltip
/startattack
/cast Sunder Armor
```

### Victory Rush
```
#showtooltip Victory Rush
/startattack
/cast [form:1] Victory Rush; [form:3] Victory Rush; Berserker Stance
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



### Whirlwind
```
#showtooltip Whirlwind
/startattack
/stopcasting [form:1/2]
/cast Berserker Stance
/cast Whirlwind
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

### Intimidating Shout
```
#showtooltip Intimidating Shout
/cast Intimidating Shout
/stopattack
```



### One-button ranged
```
#showtooltip
/cast [worn:Thrown] Throw; [worn:Bows] Shoot Bow; [worn:Guns] Shoot Gun; [worn:Crossbows] Shoot Crossbow
```



### Taunt (mouseover)
```
#showtooltip Taunt
/startattack [harm,nodead]
/cast Defensive Stance
/cast [@mouseover,harm,nodead] [harm] [@targettarget,harm,nodead] [] Taunt
```
* Enemy mouseover > enemy target > enemy target of target > default

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

### Rend (Tank)
```
#showtooltip Rend
/startattack
/cast [form:3] Defensive Stance
/cast Rend
```


<br>
<br>
<br>
<br>


---

# 📜 Universal Macros

---


### Announce CC
```
/cast [@focus,harm,nodead] Polymorph
/run if UnitExists("focus") then SendChatMessage("Polymorph on "..UnitName("focus").." — do NOT break!", "PARTY") end
```

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
```
#showtooltip
/use [@player] Heavy Runecloth Bandage
```
* Apply Bandage on self without losing target

### Consumable heal
```
#showtooltip Major Healing Potion
/use Whipper Root Tuber
/use Major Healing Potion
```

### Fishing - All-in-one
```
#showtooltip Fishing
/equip [noequipped:FishingPole] Strong Fishing Pole
/use Bright Baubles
/use 16
/click StaticPopup1Button2
/stopspelltarget
/cast fishing
```

### Focus set/clear
```
/focus [@mouseover,exists][] 
/clearfocus [mod:shift]
```
* Sets focus to mouseover or target. <br>
Hold Shift to clear.

### Focus interrupt
```
/cast [@focus,harm,nodead] Kick
```
* Works for Kick, Pummel, Counterspell, etc.

### Herb/Mineral tracking
```
#showtooltip
/castsequence Find Herbs, Find Minerals
```
* Alternate between Herb/Mineral tracking

### Mouseover heal (generic)
```
/cast [@mouseover,help,nodead][] Flash Heal
```

### Multi Racial
```
#showtooltip
/cast Blood Fury
/cast Berserking
/cast Every Man for Himself
/cast Will of the Forsaken
```
* Only the racial you actually have will go off.
* The others silently fail.

### Trinket swap
```
#showtooltip Aspirant's Insignia of the Alliance
/equipslot 13 Emblem of Alacrity
/equipslot 14 Aspirant's Insignia of the Alliance
```
* Create two of these with different trinkets to swap between

### Trinket swap toggle (advanced)
```
#showtooltip 14
/run i=GetInventoryItemID("player",14) if i==61291 then EquipItemByName(61301,13) EquipItemByName(64794,14) else EquipItemByName(61301,13) EquipItemByName(61291,14) end
```
* Checks if current item in slot 14 is ItemID 61291.
* If true, equip ItemID 61301 + 64794
* else equip ItemID 61301 + 61291
* Useful to swap between PvE & PvP , or switch between long CD trinkets

<br>
<br>




<br>
<br>
<br>
<br>

## ☕ Buy me a coffee

If you like my content and would like to show your appreciation, feel free to buy me a coffee.  <br>
https://buymeacoffee.com/eightyfive







---