# PlaceholderAPI Integration

RelishClans registers the expansion **`relishclans`** when PlaceholderAPI is installed.

## Setup

1. Install [PlaceholderAPI](https://www.spigotmc.org/resources/placeholderapi.6245/)
2. Install RelishClans and restart
3. Test: `/papi parse me %relishclans_display_name%`

```text
%relishclans_<placeholder>%
```

Values are for the **viewing player**. Not in a clan → empty / `0` / `false` (see each group).

---

## Use this one for full clan label

| Placeholder | What you get |
|-------------|--------------|
| **`%relishclans_display_name%`** | **Smart full label:** sprite icon if the clan tag is a sprite, unicode symbol if it is a symbol, plus the **clan-colored name** |

Same key: `%relishclans_displayname%`.

| Clan tag type | Example result (MiniMessage) |
|---------------|------------------------------|
| Sprite (`diamond`) | `<sprite:"minecraft:items":item/diamond> <red>Relish</red>` |
| Symbol (`⚔`) | `<red>⚔ Relish</red>` |

Your chat / TAB / hologram plugin must parse **MiniMessage** (and sprite tags on Paper 1.21.9+).

---

## Identity

| Placeholder | Description |
|-------------|-------------|
| `%relishclans_name%` | Plain name (no color, no tag) |
| `%relishclans_name_colored%` | Name with `§` colors |
| `%relishclans_tag%` | Smart tag only (sprite **or** tinted symbol) |
| `%relishclans_color%` | Color id (`red`, `#ff55aa`, …) |
| `%relishclans_color_code%` | Color as `§` / hex prefix |
| `%relishclans_color_hex%` | `#rrggbb` |
| `%relishclans_displayname_legacy%` | `§` label for scoreboards (unicode tag + name; sprites skipped) |
| `%relishclans_displayname_plain%` | Tag + name, no color |
| `%relishclans_description%` | Description |

---

## Stats

| Placeholder | Description |
|-------------|-------------|
| `%relishclans_bank%` | Bank (2 decimals) |
| `%relishclans_bank_short%` | Compact bank (`1.2K`, `3.5M`) |
| `%relishclans_claims%` / `%relishclans_max_claims%` | Claims |
| `%relishclans_claims_ratio%` | `claims/max` (e.g. `3/10`) |
| `%relishclans_members%` / `%relishclans_max_members%` | Members |
| `%relishclans_members_ratio%` | `members/max` |
| `%relishclans_core_level%` | Core tier |
| `%relishclans_power%` / `%relishclans_rank%` | Power & rank |
| `%relishclans_online_members%` | Online count |
| `%relishclans_has_core%` / `%relishclans_in_clan%` | `true` / `false` |

---

## Role

| Placeholder | Description |
|-------------|-------------|
| `%relishclans_role%` | Your role (`§` colored) |
| `%relishclans_role_plain%` | Your role (no color) |
| `%relishclans_leader%` | Leader name |
| `%relishclans_is_leader%` | `true` if you are leader |
| `%relishclans_is_admin%` | `true` if admin or leader |
| `%relishclans_is_officer%` | `true` if officer+ |

---

## Diplomacy

| Placeholder | Description |
|-------------|-------------|
| `%relishclans_allies%` | Ally names (plain, comma-separated) |
| `%relishclans_allies_colored%` | Allies as `§` labels |
| `%relishclans_allies_display%` | Allies as smart MiniMessage labels |
| `%relishclans_allies_count%` | Ally count |
| `%relishclans_wars%` / `%relishclans_enemies_count%` | Active war count |
| `%relishclans_at_war%` | `true` / `false` |
| `%relishclans_enemies%` | Enemy names (plain) |
| `%relishclans_enemies_colored%` | Enemies as `§` labels |
| `%relishclans_enemies_display%` | Enemies as smart MiniMessage labels |

---

## Location (works without a clan)

| Placeholder | Description |
|-------------|-------------|
| `%relishclans_in_claim%` | Standing in any claim |
| `%relishclans_in_own_claim%` | Standing in your clan’s claim |
| `%relishclans_claim_owner%` | Plain name of claim owner (empty if wilderness) |
| `%relishclans_claim_owner_display%` | Smart MiniMessage owner label |
| `%relishclans_claim_owner_legacy%` | `§` owner label |

Offline players → `false` / empty for these.

---

## Examples

**Chat / TAB / holograms:**
```text
%relishclans_display_name%
```

**Scoreboard:**
```text
%relishclans_displayname_legacy%
%relishclans_claims_ratio%
%relishclans_bank_short%
```

**Territory HUD:**
```text
%relishclans_claim_owner_display%
```

## Troubleshooting

- **No icon, only name?** Chat plugin may not support MiniMessage sprites — use a MiniMessage-capable plugin, or `%relishclans_displayname_legacy%` on scoreboards.
- **Still a unicode symbol?** That clan’s tag *is* a symbol (e.g. `⚔`). Equip a sprite tag (e.g. `diamond`) in Identity for an item icon.

## Next

- [Commands](Commands.md)
- [Configuration](Configuration.md)
