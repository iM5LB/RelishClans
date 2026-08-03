# Commands

Complete RelishClans command reference.

**Base command:** `/clan`  
**Aliases:** `/clans`, `/c`  
**Permission:** `relishclans.command` (default: true)

---

## Help & Admin

### `/clan help`
Shows the help menu.

### `/clan reload`
**Permission:** `relishclans.admin`

Reload configuration, language, storage hooks, and wars from disk.

### `/clan license`
**Permission:** `relishclans.admin`

Show license verification status and whether Premium features are unlocked. See [Free vs Premium](FreeVsPremium.md).

### `/clan admin <clans|wars|endwar <a> <b>|<clan>>`
**Permission:** `relishclans.admin`

| Usage | Description |
|-------|-------------|
| `/clan admin clans` | Browse all clans in a GUI; click one to manage it |
| `/clan admin wars` | View active wars in a GUI (duration, capture %); click to force-end |
| `/clan admin <clan>` | Open that clan's GUI as admin |
| `/clan admin endwar <clanA> <clanB>` | Force-end a war from chat |

---

## Clan Lifecycle

### `/clan create <name>`
Create a clan. You become Leader. Default color/tag applied.

### `/clan disband`
**Role:** Leader  

First run arms a confirmation; run again within 30s to confirm.

### `/clan rename <name>`
**Role:** Leader  

Rename the clan (cooldown: `rename`).

### `/clan description <text|clear>`
**Role:** Leader  

Set or clear the clan description.

### `/clan leave`
Leave your clan (leaders must transfer or disband).

---

## Members

### `/clan invite <player>`
**Role:** Officer+  

Invite an online player (cooldown: `invite`). Invites expire per `settings.invite-expire-minutes`.

### `/clan invites`
List pending invites you have received.

### `/clan join <clan>`
Accept an invite to that clan.

### `/clan kick <member>`
**Role:** Admin+ (hierarchy enforced)

### `/clan promote <member>` / `/clan demote <member>`
**Role:** Admin+ / Leader as appropriate

### `/clan transfer <member>`
**Role:** Leader  

Transfer leadership.

### `/clan roster`
List members and roles.

---

## Claims

### `/clan claim [radius]`
**Role:** Officer+  

- No args: claim current chunk  
- `radius`: Chebyshev radius (`0` = 1 chunk, `1` = 3×3, …) capped by `settings.max-claim-radius`  

Cooldown: `claim`.

### `/clan unclaim [radius|all]`
**Role:** Officer+ (`all` requires Leader)  

Never unclaims the core chunk. Cooldown: `unclaim`.

### `/clan autoclaim`
**Role:** Officer+  

Toggle walk-to-claim mode.

### `/clan map`
Show an 11×11 chat claim map and particle borders.

Legend: `+` you · `O` own · `A` ally · `W` war · `E` other · `-` wild

---

## Core & Travel

### `/clan teleport` · `/clan home` · `/clan tp`
Teleport on top of your clan core. Cooldown: `teleport`.

### `/clan movecore` · `/clan core move`
**Role:** Admin+  
**Premium:** `core_relocator`  
**Requires:** active `beacon_relocator` (Core Relocator) flag  

Moves the core to your location (claims the chunk first if needed). Cooldown: `move_core`.

### `/clan core`
Show core coordinates.

---
## Identity

### `/clan color [name]`
**Role:** Admin+  

Open identity GUI, or set color (e.g. `gold`, `aqua`).

### `/clan tag [symbol]`
**Role:** Admin+  

Open identity GUI, or set icon tag from the allow-list.

### `/clan identity`
**Role:** Admin+  

GUI color + tag picker.

---

## Economy & Storage

### `/clan bank`
Open deposit / withdraw GUI. Withdraw requires Officer+ (cooldown: `bank_withdraw`).

### `/clan chest`
Open shared clan chest (requires active `clan_chest` flag).

### `/clan flags`
Open upgrades / flags GUI.

---

## Diplomacy & War

### `/clan ally <clan>`
**Role:** Admin+  

Request or accept an alliance. Cooldown: `ally`.

### `/clan neutral <clan>`
**Role:** Admin+  

Break an alliance.

### `/clan war <clan>`
**Role:** Admin+  
**Premium:** required (`wars`)

Declare war. Cooldown: `war`.

### `/clan surrender <clan>`
**Role:** Admin+  
**Premium:** required (`wars`) 

End an active war with that clan.

---

## GUI & Visuals

### `/clan gui`
Open the main clan GUI.

### `/clan info [clan]`
Show clan details (identity, core tier, members, claims, bank, allies, wars).

### `/clan fly`
Toggle clan fly preference (requires `clan_fly` flag in claims).

### `/clan toggle <particles|titles|bossbars|joinpreview|fly|sounds|actionbar|holograms|waralerts|entryalerts|all>`
Toggle personal visual preferences.

### `/clan visuals` · `/clan settings`
Open personal visuals GUI.

### `/clan mail`
List clan mailbox messages (short ids).

| Subcommand | Description |
|------------|-------------|
| `/clan mail send <subject> \| <message>` | Send clan-wide mail |
| `/clan mail send <member> <subject> \| <message>` | Send to one member |
| `/clan mail read <id>` | Read a message |
| `/clan mail delete <id>` | Delete a message |

### `/clan logs`
Show recent claim activity (break/place/interact/kill/enter/replay). Entries marked **▶** have a movement clip.

| Subcommand | Description |
|------------|-------------|
| `/clan logs replay <player>` | Watch that player's latest clip (requires Claim Replay flag; sneak to cancel) |
| `/clan logs save replay <12h\|30m> [ago] [player]` | Link pending clips from that window into Claim Logs (optional player filter) |

---

## Cooldowns

Configured in `config.yml` → `cooldowns`. Set a value to `0` to disable that cooldown.  
Bypass: `relishclans.cooldown.bypass` or `relishclans.admin`.

## Next Steps

- [Permissions](Permissions.md)
- [Configuration](Configuration.md)
- [PlaceholderAPI](PlaceholderAPI.md)
