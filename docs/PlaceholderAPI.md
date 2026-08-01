# PlaceholderAPI Integration

RelishClans registers the expansion **`relishclans`** automatically when PlaceholderAPI is installed.

## Installation

1. Install [PlaceholderAPI](https://www.spigotmc.org/resources/placeholderapi.6245/)
2. Install RelishClans
3. Restart (or ensure RelishClans loads after PlaceholderAPI)
4. Check console for PlaceholderAPI expansion registration

## Identifier

```text
%relishclans_<placeholder>%
```

All placeholders are relative to the **viewing player's clan**. If the player is not in a clan, most string fields return empty and numeric fields return `0`.

---

## Clan Identity

| Placeholder | Description |
|-------------|-------------|
| `%relishclans_name%` | Plain clan name (no color) |
| `%relishclans_name_colored%` | Name with `§` colors |
| `%relishclans_name_minimessage%` | Name as MiniMessage |
| `%relishclans_tag%` | Tag as MiniMessage — **sprite icons** use `<sprite:…>`, unicode tags are tinted |
| `%relishclans_tag_plain%` | Unicode tag only (empty when the tag is a sprite) |
| `%relishclans_tag_legacy%` | Unicode tag with `§` color (empty for sprites) |
| `%relishclans_color%` | Color id (`red`, `#ff55aa`, …) |
| `%relishclans_color_code%` | Color as `§` / hex prefix |
| `%relishclans_color_minimessage%` | Color for MiniMessage (`red` / `#rrggbb`) |
| `%relishclans_displayname%` / `%relishclans_display_name%` | **Sprite/unicode tag + colored name** (MiniMessage — preferred for chat / holograms / Adventure TAB) |
| `%relishclans_displayname_legacy%` | `§`-colored name (no sprite objects — for scoreboards) |
| `%relishclans_displayname_plain%` | Tag + name, no formatting |
| `%relishclans_description%` | Description text |

> **Sprites:** `%relishclans_tag%` and `%relishclans_display_name%` emit MiniMessage `<sprite:"atlas":path>` tags so Java clients show the real item/icon. Plugins must parse MiniMessage (RelishChat, DecentHolograms MM, modern TAB, etc.). Scoreboards should use `%relishclans_displayname_legacy%`.

---

## Stats

| Placeholder | Description |
|-------------|-------------|
| `%relishclans_bank%` | Bank balance (2 decimals) |
| `%relishclans_claims%` | Claim count |
| `%relishclans_max_claims%` | Claim limit (with boosts) |
| `%relishclans_members%` | Member count |
| `%relishclans_max_members%` | Member limit (with boosts) |
| `%relishclans_core_level%` | Core upgrade tier |
| `%relishclans_power%` | Clan power score (0–10) |
| `%relishclans_rank%` | Rank among all clans by power (`1` = strongest) |
| `%relishclans_online_members%` | Online members |
| `%relishclans_has_core%` | `true` / `false` |
| `%relishclans_in_clan%` | `true` / `false` |

---

## Role & Leadership

| Placeholder | Description |
|-------------|-------------|
| `%relishclans_role%` | Player's role display name |
| `%relishclans_leader%` | Leader's last known name |

---

## Diplomacy & War

| Placeholder | Description |
|-------------|-------------|
| `%relishclans_allies%` | Ally names (comma-separated) |
| `%relishclans_allies_colored%` | Ally names with `§` colors |
| `%relishclans_allies_count%` | Ally count |
| `%relishclans_wars%` | Number of active wars |
| `%relishclans_at_war%` | `true` / `false` |
| `%relishclans_enemies%` | Enemy clan names |
| `%relishclans_enemies_colored%` | Enemy names with `§` colors |

---

## Usage Examples

**Chat / holograms (MiniMessage):**
```text
%relishclans_display_name%
```

**Scoreboard / classic TAB (`§` only):**
```text
Clan: %relishclans_displayname_legacy%
Claims: %relishclans_claims%/%relishclans_max_claims%
```

**Test:**
```text
/papi parse me %relishclans_display_name%
/papi parse me %relishclans_tag%
```

## Troubleshooting

**Seeing `diamond` / item alias text instead of an icon?**
- You are using a consumer that does not parse MiniMessage sprites. Switch to `%relishclans_displayname_legacy%` for scoreboards, or use a MiniMessage-capable chat/TAB plugin for `%relishclans_display_name%`.

**No color?**
- Prefer `%relishclans_display_name%` (MiniMessage) or `%relishclans_displayname_legacy%` (`§`). Plain `%relishclans_name%` is intentionally uncolored.

## Next Steps

- [Commands](Commands.md)
- [Configuration](Configuration.md)
