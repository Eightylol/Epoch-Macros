
---

# 📜 WoW 3.3.5 Macro Compendium (Project Epoch)

This is a comprehensive guide to the **macro and communication system** in the **3.3.5 client**. <br>
Project Epoch inherits all of these features.

---

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

### 🔹 Communication Examples (All Classes)

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




---

# 📜 WoW 3.3.5 Class Macros

---

Provided below is **working macros** for each class in the **Wrath 3.3.5 client**.<br>
Most examples are annotated so you can understand and adapt it.

<br>



## 🔹 Universal Macros


### Focus set/clear

```
/focus [@mouseover,exists][] 
/clearfocus [mod:shift]
```

* Sets focus to mouseover or target.
* Hold Shift to clear.

### Focus interrupt

```
/cast [@focus,harm,nodead] Kick
```

* Works for Kick, Pummel, Counterspell, etc.

### Mouseover heal (generic)

```
/cast [@mouseover,help,nodead][] Flash Heal
```

### Announce CC

```
/cast [@focus,harm,nodead] Polymorph
/run if UnitExists("focus") then SendChatMessage("Polymorph on "..UnitName("focus").." — do NOT break!", "PARTY") end
```

---
<br>
<br>

## 🔹 Warrior Macros


### Charge + Intercept + Intervene (stance dance)

```
/cast [stance:1/2] Charge; [stance:3] Intercept; [help] Intervene
```
* Uses correct ability depending on stance and target.


### Shield Bash (focus interrupt)
```
/cast [@focus,harm,nodead] Shield Bash
```

### Equip shield + Shield Block
```
/equip [noequipped:Shields] Shield of Impenetrable Darkness
/cast Shield Block
```

### Shattering Throw (announce)
```
/cast Shattering Throw
/run SendChatMessage("Casting Shattering Throw on "..UnitName("target").."!","RAID_WARNING")
```

---

<br>
<br>

## 🔹 Paladin Macros

### Mouseover Cleanse

```
/cast [@mouseover,help,nodead] Cleanse
```

### Hand of Protection on focus

```
/cast [@focus,help,nodead] Hand of Protection
```

### Bubble + cancel

```
/cast Divine Shield
/cancelaura Divine Shield
```

* First press bubbles, second press cancels.

### PvP Hammer of Justice (focus)

```
/cast [@focus,harm,nodead][] Hammer of Justice
```

---

<br>
<br>

## 🔹 Hunter Macros

### Misdirection macro
```
/cast [@focus,help][@pet,exists] Misdirection
```

* Casts on focus if friendly, else on pet.

### Scatter + trap
```
/cast Scatter Shot
/cast [@focus] Freezing Trap
```

### Pet attack / follow toggle
```
/petattack [@target,harm]
/petfollow [@target,noexists]
```

---

<br>
<br>

## 🔹 Rogue Macros

### Focus Sap

```
/cast [@focus,harm,nodead][] Sap
```

### Stealth toggle

```
/cast [nostealth] Stealth
/cancelaura [stealth] Stealth
```

### Kick (focus interrupt)

```
/cast [@focus,harm,nodead][] Kick
```

### Vanish + announce

```
/cast Vanish
/run SendChatMessage("VANISHED — reset fight!", "PARTY")
```

---

<br>
<br>

## 🔹 Priest Macros

### Mouseover Heal
```
/cast [@mouseover,help,nodead][] Flash Heal
```

### Dispel Magic on focus
```
/cast [@focus,exists] Dispel Magic
```

### Shadow Word: Death self-break
```
/cast [@player] Shadow Word: Death
```
* Useful to break CC.

### Mass Dispel with cursor
```
/cast !Mass Dispel
```
* Places targeting circle at cursor for quick use.

---

<br>
<br>

## 🔹 Mage Macros

### Focus Counterspell**

```
/cast [@focus,harm,nodead] Counterspell
```

### Sheep focus + announce**

```
/cast [@focus,harm,nodead] Polymorph
/run if UnitExists("focus") then SendChatMessage("Sheeping "..UnitName("focus").." — do NOT break!","PARTY") end
```

### Ice Block toggle**

```
/cast !Ice Block
/cancelaura Ice Block
```

### Evocation self-cancel**

```
/cast Evocation
/stopcasting
```

---

<br>
<br>

## 🔹 Warlock Macros

### Focus Fear
```
/cast [@focus,harm,nodead] Fear
```

### Mouseover Banish
```
/cast [@mouseover,harm][] Banish
```

### Pet Spell Lock (focus)
```
/cast [@focus,harm,nodead][] Spell Lock
```

### Soulstone announce
```
/cast [@mouseover,help,nodead] Soulstone
/run if UnitExists("mouseover") then SendChatMessage("Soulstoned "..UnitName("mouseover").."!", "RAID") end
```

---

<br>
<br>

## 🔹 Shaman Macros

### Focus Wind Shear
```
/cast [@focus,harm,nodead] Wind Shear
```

### Grounding Totem destroy (anti-spell)
```
/castsequence reset=10 Grounding Totem, Totemic Call
```

### Mouseover purge
```
/cast [@mouseover,harm,nodead][] Purge
```

### Bloodlust announce
```
/cast Bloodlust
/run SendChatMessage("BLOODLUST ACTIVATED!", "RAID_WARNING")
```

---

<br>
<br>

## 🔹 Druid Macros

### Focus Cyclone

```
/cast [@focus,harm,nodead] Cyclone
```

### Travel form auto-switch

```
/cast [swimming] Aquatic Form; [flyable] Swift Flight Form; Travel Form
```

### Bear Frenzied Regeneration + Barkskin

```
/cast Barkskin
/cast Frenzied Regeneration
```

### Rebirth with raid announce

```
/cast [@mouseover,help,dead] Rebirth
/run if UnitExists("mouseover") then SendChatMessage("Battle-ressing "..UnitName("mouseover").."!", "RAID_WARNING") end
```


---
