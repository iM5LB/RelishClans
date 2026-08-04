# Changelog

All notable changes to RelishClans.

## [1.0.1] - 2026-08-03

### Added
- **Entry Denial** flag (`entry_deny`) — block non-members from walking/teleporting into claims (settings for neutrals, allies, war enemies)
- **Clan fly braking** — `fly.brake` + per-tier `brake` on `clan_fly`
- **Global flag disable** — `flags.disabled: [...]` or per-flag `enabled: false`
- PlaceholderAPI: location (`in_claim`, `claim_owner_display`, …), role checks, ratios, `bank_short`, smart ally/enemy display lists
- Companion configs: **`identity.yml`** (colors + tags) and **`flags.yml`** (flag definitions)

### Fixed
- Territory boss bar / fly / visuals update correctly on teleport, world change, and respawn
- `%relishclans_at_war%` returns `"false"` (not `"0"`) when not in a clan

## [1.0.0] - 2026-07-27

### Added
- Chunk claiming with radius claim/unclaim, autoclaim, optional contiguous mode, and `/clan map`
- Upgradable clan core (beacon) — tiers improve war capture time / radius
- War system with core capture, protection drop, auto-end, and admin war tools
- Free / Premium licensing (`license-key`) with gated features and `/clan license`
- Update checker (`check-for-updates`) via GitHub releases — console banner + admin join notify
- Clan identity: color + icon tag (`/clan color`, `/clan tag`, `/clan identity`)
- Flags & upgrades (chest, fly, locks, war shield, claim/member boosts, and more)
- Clan bank, shared chest, allies, roles (Member → Leader)
- Configurable action cooldowns with `relishclans.cooldown.bypass`
- Storage backends: YAML, SQLite, MySQL
- Soft-depends: Vault, WorldGuard, PlaceholderAPI (`%relishclans_*%`), PacketEvents (claim replay playback)
- Full MiniMessage language file (`lang/en.yml`)
- Clan GUI for roster, claims, bank, flags, war, identity, and visuals
- Clan mail (`/clan mail`) and claim activity logs with optional movement replay (`/clan logs`)
- Documentation under `docs/`

## Next Steps

- [Installation](Installation.md)
- [Configuration](Configuration.md)
- [Commands](Commands.md)
