# Configuration

Main file: `plugins/RelishClans/config.yml`  
Messages: `plugins/RelishClans/lang/en.yml`

After edits, run `/clan reload` (or restart).

---

## Settings

```yaml
settings:
  max-members: 25
  max-claims: 50
  auto-save-minutes: 5
  claim-indicators: true
  contiguous-claims: false      # new claims must touch existing territory
  claim-buffer: 1               # min chunk gap vs other clans (0 = allow next door; allies ignored)
  max-claim-radius: 2           # /clan claim <radius> max (0–5)
  invite-expire-minutes: 60
  bypass-permission: "relishclans.admin"
```

---

## Cooldowns

Seconds per action. `0` disables that cooldown.

```yaml
cooldowns:
  teleport: 30
  move_core: 120
  claim: 3
  unclaim: 3
  war: 60
  create: 60
  invite: 10
  ally: 15
  rename: 30
  core_upgrade: 10
  bank_withdraw: 5
```

Bypass: `relishclans.cooldown.bypass` or admin bypass permission.

---

## Storage

```yaml
storage:
  type: YAML    # YAML | SQLITE | MYSQL

  mysql:
    host: "localhost"
    port: 3306
    database: "relishclans"
    username: "root"
    password: "password"
    use-ssl: false
```

| Type | Notes |
|------|--------|
| **YAML** | `clans.yml` / `wars.yml` — simplest |
| **SQLITE** | Local `clans.db` — drivers shaded in the JAR |
| **MYSQL** | Remote DB — drivers shaded; DB created if missing |

---

## Language

```yaml
language: "en"
```

Copy `lang/en.yml` to `lang/<code>.yml` and set `language` to that code. MiniMessage format; placeholders use `<name>` style.

---

## Economy

Paid unlocks/upgrades always require Vault when cost &gt; 0 (hardcoded).  
If Vault is missing, those actions fail with a clear message.

---

## Visuals

```yaml
visuals:
  titles: true
  boss-bars: true
  particles:
    enabled: true
    step: 1
    vertical-rings: true
    refresh-ticks: 20
    join-preview-seconds: 6
  holograms:
    enabled: true
    height: 2.2
    update-seconds: 10
    proximity-seconds: 1
```

Claim border particles already use per-player `spawnParticle` (client-bound). Titles, boss bars, and action bars are Adventure packets. Holograms remain real TextDisplays with proximity culling.

Players can toggle personal prefs via `/clan toggle` or the Visuals GUI.

---

## Fly

```yaml
fly:
  enabled: true
  allow-in-allied-claims: false
  speed: 0.08
  disable-on-damage: true
```

Requires the clan `clan_fly` flag unlocked and active. Speed can scale with flag tier.

---

## Mail

```yaml
mail:
  enabled: true
  max-messages: 100
```

Clan mailbox stored in `mail.yml`. Use `/clan mail`.

---

## Claim logs & replay

```yaml
logs:
  enabled: true
  max-entries: 500
  record-break: true
  record-place: true
  record-interact: true
  record-kill: true

replay:
  enabled: true
  sample-hz: 10
  max-seconds: 120
  outsiders-only: true
  min-frames: 20
  auto-save: true          # false = only /clan logs save replay adds clips to Claim Logs
  retain-hours: 12         # how long unsaved clips stay available for manual save
```

Recording requires the **Claim Replay** flag upgrade. Activity rows go to `claim-logs.yml`. Movement clips (with skin textures) are sampled into `replays/<clanId>/*.rcl`.

Playback works **without PacketEvents** via Paper `Mannequin` entities (full body + skin, viewer-only). If PacketEvents is installed, a client-side fake player is used instead. Watch with `/clan logs replay <player>` (sneak to cancel). Manual save: `/clan logs save replay 12h ago [player]`.

---

## WorldGuard

When WorldGuard is installed, RelishClans registers these hardcoded state flags:

| Flag | Use |
|------|-----|
| `relish-clans-claim` | Allow/deny claiming in a region |
| `relish-clans-fly` | Allow/deny clan fly |
| `relish-clans-war` | Allow/deny war actions |

Set a region flag to `deny` to block that action inside the region.

---

## War

```yaml
war:
  capture-radius: 10.0   # unused for presence (compat only)
  capture-seconds: 120
  autosave-seconds: 60
  auto-end-seconds: 300
```

Capture requires attackers to stand on the **core chunk** (same chunk as the clan core).  
Actual capture time = `capture-seconds` + `war_shield` extras + **core tier** `extra-capture-seconds`.  
The core **cannot be moved** while the clan is at war. Both clans are notified when capture starts and at 25%/50%/75%.

---

## Clan Identity

```yaml
clan-identity:
  colors:
    - red
    - dark_red
    - gold
    - "#FF5500"             # custom hex
  default-color: red
  default-tag: "⚔"
  # default-description is in lang (clan.default-description)
  tags:
    "⚔": 0                  # default free unicode
    diamond: 0              # free sprite alias (from sprites.properties)
    netherite_sword: 2500
    "★": 1500
```

Admins pick colors freely — named vanilla colors and/or `#RRGGBB` hex. Hex applies to clan name, holograms, claim particles, core beam, and overlays.
Tags with cost `> 0` must be unlocked once per clan before they can be selected.

**Sprite tags:** use a Mojang sprite alias (same mapping as RelishChat `sprites.properties`). Java clients render the real atlas icon via Adventure sprite objects. Unknown ASCII aliases are skipped on load with a warning. Unicode symbols remain supported.

The identity GUI paginates colors and tags separately.

---

## Core Upgrades

```yaml
core:
  levels:
    1:
      icon: IRON_BLOCK
      upgrade-cost: 0
      extra-capture-seconds: 0
      radius-bonus: 0
    2:
      icon: GOLD_BLOCK
      upgrade-cost: 5000
      extra-capture-seconds: 30
      radius-bonus: 1
    # ...
```

The physical core is always a **beacon**. Tiers only change upgrade cost, war capture time, and radius bonus — not the world block. GUI icons use `icon` (Iron → Netherite).

---

## Clan Chest

Default **3** rows, max **6** (hardcoded). Flag tiers under `clan_chest` can still raise rows within that max.

---

## Companion configs

| File | Contents |
|------|----------|
| `config.yml` | Core settings (license, storage, fly, war, …) |
| **`identity.yml`** | Clan colors, icon tags + unlock costs, defaults |
| **`flags.yml`** | Flag definitions, `default-unlocked`, `disabled` |
| `lang/en.yml` | All player-facing messages |

## Flags

Edit **`flags.yml`** (not `config.yml`). Under `flags.definitions` each flag has gameplay settings only:

- `icon`, `unlock-cost`
- `default-unlocked` / `default-active`
- `enabled: false` — **server-wide kill** for that flag (optional; default `true`)
- `levels` with `upgrade-cost` and typed `settings`

**Names and lore** live in `lang/en.yml` under `messages.flag.<id>.name` and `messages.flag.<id>.lore.<tier>`.

Default unlocked at clan create: `flags.default-unlocked` in `flags.yml`.

### Globally disable flags (admin)

Hide a flag from every clan’s Upgrades / Chunk Flags GUIs and stop all of its gameplay (even if a clan already unlocked it):

```yaml
# flags.yml
flags:
  disabled:
    - entry_deny
    - clan_fly
```

Or on a single definition:

```yaml
flags:
  definitions:
    entry_deny:
      enabled: false
      # ...
```

Reload with `/clan reload` (or restart) after editing.

### Tags & colors

Edit **`identity.yml`**:

```yaml
default-color: red
default-tag: "⚔"

colors:
  - red
  - "#FF5500"

tags:
  "⚔": 0
  diamond: 0
  emerald: 1500
```

### Flag reference

| Flag ID | Purpose |
|---------|---------|
| `clan_chest` | Shared clan storage (rows per tier) |
| `clan_fly` | Fly in owned claims (speed per tier) |
| `beacon_relocator` | Allow moving the clan core |
| `claim_boost` | Extra claim slots |
| `member_boost` | Extra member slots |
| `pvp_mode` | Friendly fire between members |
| `no_pvp` | Block all PvP in claims |
| `visitor_greeting` | Notify members when non-members enter |
| `alarm_bell` | Alert on enemy entry |
| `heal_zone` | Regen HP in claims |
| `xp_boost` | XP multiplier in claims |
| `war_shield` | Extra war capture seconds |
| `build_lock` | Block outsider building |
| `container_lock` | Lock chests / furnaces / etc. |
| `use_lock` | Lock doors, buttons, utilities |
| `entity_interact` | Block outsider entity interact (frames, stands, boats…) |
| `villager_lock` | Block outsider villager trade / harm |
| `spawner_lock` | Block outsider spawner break/place (even if build unlocked) |
| `ally_access` | Enable ally tiers on lock flags |
| `explosion_shield` | Block explosion damage |
| `fire_control` | Stop fire spread / burn |
| `leaf_decay` | Prevent leaf decay |
| `snow_melt` | Preserve snow |
| `ice_melt` | Preserve ice |
| `mob_spawn_control` | Block monster (and animal) spawns |
| `enderpearl_guard` | Block outsider ender pearls |
| `entry_deny` | Block non-members from entering claims (walk/teleport) |
| `animal_guard` | Protect animals from outsiders |
| `crop_trample_guard` | Prevent farmland trampling |
| `entry_titles` | Territory enter/leave titles |
| `particle_markers` | Claim border particles |
| `war_room` | Placeholder only — not implemented (hidden from GUI) |

### Still intentional / leftover

These are expected by design, not bugs:

| Item | Notes |
|------|--------|
| **`war_room`** | Placeholder only — defined in config and hidden from Upgrades; **not implemented** in code. Reserved for a future war feature. |
| **Simple flags** | `fire_control`, `leaf_decay`, `snow_melt`, `ice_melt`, `enderpearl_guard`, `animal_guard`, `crop_trample_guard`, `xp_boost`, `claim_boost`, `member_boost`, `war_shield`, `beacon_relocator`, `clan_fly`, `ally_access`, `entry_titles`, `particle_markers` — left-click unlock/upgrade; right-click enable/disable. No detail settings screen. |
| **Detail flags** | `mob_spawn_control`, `pvp_mode`, `no_pvp`, `heal_zone`, `alarm_bell`, `visitor_greeting`, `entry_deny`, `explosion_shield`, `build_lock`, `container_lock`, `use_lock`, `entity_interact`, `villager_lock`, `spawner_lock` — same clicks, plus shift-click opens the settings screen. |

---

## Debug

```yaml
# Detailed [Debug] logs: core place/despawn, claims, wars, saves, shutdown steps.
# Keep false on production; enable only while diagnosing.
debug-mode: false
config-version: 1   # do not edit — used by config updater
```

When `debug-mode` is `true`, the enable banner shows `Debug: ON`, and the console logs lifecycle details that are silent otherwise (including clan core restore/despawn).

## Update checks

```yaml
check-for-updates: true
```

When enabled (default), RelishClans checks GitHub releases ~10 seconds after startup and every 6 hours. If a newer version is found:

- Console logs the latest version and download URL
- Online players with `relishclans.admin` get a clickable chat notice (24h cooldown)
- Admins also get the notice a few seconds after joining

URLs are baked in `plugin.yml` (`update.github-api`, `update.github-releases`). Set `check-for-updates: false` to disable. `/clan reload` applies the toggle.

## Next Steps

- [Commands](Commands.md)
- [PlaceholderAPI](PlaceholderAPI.md)
- [Troubleshooting](Troubleshooting.md)
