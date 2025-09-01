
---

# 📜 WoW 3.3.5 Macro Reference (Project Epoch)

---

## 🔹 1. Macro Commands (Slash Commands)

These are the most common ones you’ll use inside a macro:

| Command                                                                                  | Description                                                                         |
| ---------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- |
| `/cast`                                                                                  | Cast a spell                                                                        |
| `/use`                                                                                   | Use an item, trinket, or ability                                                    |
| `/castsequence`                                                                          | Cast spells in sequence (can reset)                                                 |
| `/target`                                                                                | Target a unit (by name, or conditionally)                                           |
| `/assist`                                                                                | Assist a unit (target their target)                                                 |
| `/focus`                                                                                 | Set focus target                                                                    |
| `/clearfocus`                                                                            | Clear your focus                                                                    |
| `/petattack`, `/petfollow`, `/petstay`, `/petpassive`, `/petdefensive`, `/petaggressive` | Pet controls                                                                        |
| `/stopcasting`                                                                           | Cancel your current spellcast                                                       |
| `/stopattack`                                                                            | Stop auto-attacking                                                                 |
| `/startattack`                                                                           | Start auto-attacking                                                                |
| `/cancelaura`                                                                            | Remove a buff/debuff                                                                |
| `/cancelqueuedspell`                                                                     | Cancel a queued spell (like Heroic Strike)                                          |
| `/equip` / `/equipslot`                                                                  | Equip an item (optionally in a slot)                                                |
| `/swapactionbar`                                                                         | Swap between action bars (1–6)                                                      |
| `/click`                                                                                 | Click another action bar button (chain macros)                                      |
| `/run` or `/script`                                                                      | Run Lua code (disabled on some servers, but usually works on 3.3.5 private servers) |

---

## 🔹 2. Targeting & Substitutions

### `@unit` / `[target=unit]`

Specifies who to act on:

* `@target` → current target
* `@focus` → focus target
* `@mouseover` → unit your mouse is over
* `@player` → yourself
* `@pettarget` → your pet’s target
* `@party1` … `@party4` → party members
* `@raid1` … `@raid40` → raid members
* `@arena1` … `@arena5` → arena enemies
* `@boss1` … `@boss4` → boss units

💡 `@unit` is shorthand for `[target=unit]`. Both work.

---

### `% substitutions` (chat/emotes only)

* `%t` → name of your target
* `%f` → name of your focus
* `%m` → name of your mouseover target

Example:

```
/y Focusing %t — kill it fast!
```

---

## 🔹 3. Conditionals

Conditionals go inside `[ ]`. You can chain them:

* Commas (`,`) = AND logic
* Semicolons (`;`) = OR logic (priority order)

Example:

```
/cast [mod:shift,@focus,harm][] Polymorph
```

→ Polymorphs focus if Shift held, else casts on target.

---

### Target Conditionals

| Conditional | Meaning                        |
| ----------- | ------------------------------ |
| `exists`    | Target exists                  |
| `help`      | Target is friendly             |
| `harm`      | Target is hostile              |
| `dead`      | Target is dead                 |
| `nodead`    | Target is alive                |
| `party`     | Target is in your party        |
| `raid`      | Target is in your raid         |
| `group`     | You’re in a group (party/raid) |
| `nogroup`   | You’re solo                    |

---

### Self/Player State

| Conditional     | Meaning                                                                |
| --------------- | ---------------------------------------------------------------------- |
| `combat`        | You are in combat                                                      |
| `nocombat`      | You are not in combat                                                  |
| `mounted`       | You are mounted                                                        |
| `nomounted`     | You are not mounted                                                    |
| `stealth`       | You are stealthed                                                      |
| `stance:X`      | You are in stance/form X (see below)                                   |
| `form:X`        | Same as stance                                                         |
| `swimming`      | You are swimming                                                       |
| `flying`        | You are flying                                                         |
| `indoors`       | You are indoors                                                        |
| `outdoors`      | You are outdoors                                                       |
| `equipped:slot` | You have something equipped in slot (or type, e.g. `equipped:Shields`) |

---

### Pet Conditionals

| Conditional | Meaning                                |
| ----------- | -------------------------------------- |
| `pet`       | You have a pet                         |
| `nopet`     | You do not have a pet                  |
| `pet:NAME`  | Your pet is that type (e.g. `pet:Imp`) |

---

### Modifiers (keyboard)

| Conditional | Meaning                 |
| ----------- | ----------------------- |
| `mod:shift` | Shift is pressed        |
| `mod:ctrl`  | Control is pressed      |
| `mod:alt`   | Alt is pressed          |
| `nomod`     | No modifier key pressed |
| `mod`       | Any modifier pressed    |

---

### Stances / Forms

Depends on class:

* **Warrior**: `stance:1` Battle, `stance:2` Defensive, `stance:3` Berserker
* **Druid**: `form:1` Bear, `form:2` Aquatic, `form:3` Cat, `form:4` Travel, `form:5` Moonkin/Tree, `form:6` Flight
* **Rogue**: `stance:0` Unstealthed, `stance:1` Stealth
* **Priest**: `stance:1` Shadowform

---

### Action Bar / Bonus Bars

* `[bar:1]` → if action bar 1 is active
* `[bonusbar:X]` → if bonus bar X is active (used for stance/stealth shifting)

---

### Special Conditionals

* `channeling:SpellName` → You are channeling that spell
* `equipped:ItemType` → You have that type equipped (e.g. `equipped:Shields`)
* `worn:ItemType` → Same as equipped
* `flyable` → You are in a zone where flying mounts can be used
* `mounted` → You’re mounted
* `indoors` / `outdoors` → Self-explanatory

---

## 🔹 4. Practical Examples

**Mouseover heal with fallback:**

```
/cast [@mouseover,help,nodead][] Flash Heal
```

**Focus CC with modifier:**

```
/cast [mod:shift,@focus,harm,nodead][] Polymorph
```

**Mount macro (ground if no flying available):**

```
/cast [flyable] Swift Flight Form; Swift Zulian Tiger
```

**Weapon swap + ability:**

```
/equip [equipped:Shields] Staff of Domination
/equip [noequipped:Shields] Shield of Impenetrable Darkness
/cast Shield Block
```

---

## 🔹 5. Special Notes

* You can’t **condition on health/mana values** in 3.3.5 macros (protected functions).
* `[target=]` and `@` are **fully interchangeable**.
* `%t`, `%f`, `%m` only expand in **chat/emote macros**, never in `/cast`.
* Most macros can only execute **one GCD ability per press** — no automation beyond that.

---
