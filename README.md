<div align="center">

## ⚔️ Clan Claims • Upgradable Cores • Wars • Flags • Bank • GUI ⭐

![RelishClans](https://github.com/iM5LB/RelishClans/raw/master/docs/assets/RelishClansBanner.png)
[![M5LB Store Banner](https://github.com/iM5LB/RelishClans/raw/master/docs/assets/M5LBStore.png)](https://m5lb.run.place/)
[![Discord](https://img.shields.io/badge/Discord-Support-7289da?style=for-the-badge&logo=discord)](https://discord.gg/jDr2KZcGXk)
[![Documentation](https://img.shields.io/badge/Docs-Read-bf1029?style=for-the-badge&logo=gitbook)](https://im5lb.github.io/RelishClans)
[![Issues](https://img.shields.io/badge/🐛%20Issues-Report-orange?style=for-the-badge)](https://github.com/iM5LB/RelishClans/issues)
[![Store](https://img.shields.io/badge/Store-License%20Keys-gold?style=for-the-badge)](https://m5lb.run.place/)
[![Donate](https://img.shields.io/badge/💖%20Donate-Love-ff69b4?style=for-the-badge)](https://creators.sa/m5lb)

</div>

---

## 🌟 **Why Choose RelishClans?**

RelishClans is a modern clan plugin for Paper — chunk claims, territory protection, upgradable clan cores, wars, flags, shared bank and chest, clan identity, and PlaceholderAPI. Built for 1.21+ with YAML, SQLite, or MySQL storage.

### ✨ **Key Highlights**

🗺️ **Chunk Claims** - Claim, unclaim, autoclaim, radius claim, contiguous mode, and chat map  
🏰 **Upgradable Core** - Beacon clan core with war-defense tiers  
⚔️ **War System** - Declare war, capture cores, protection drop (Premium)  
🚩 **Flags & Upgrades** - Economy-backed unlocks and per-clan tiers  
🎨 **Clan Identity** - Color + icon tag across holograms, titles, chat, and GUI  
🔌 **Integrations** - Vault, WorldGuard, PlaceholderAPI, Floodgate (Bedrock forms)  

---

## 📋 **Requirements**

| Component | Requirement |
|-----------|-------------|
| **Minecraft** | 1.21+ |
| **Server** | Paper, Purpur, or Paper-based forks |
| **Java** | 21+ |
| **Soft Dependencies** | Vault (economy), WorldGuard (regions), PlaceholderAPI (optional), Floodgate (Bedrock forms) |

---

## 🚀 **Features Overview**

### 🆓 **Free Version**
- ✅ Clan create / disband / rename / description / leave / transfer
- ✅ Roster: invite, join, kick, promote, demote, roster GUI
- ✅ Claim, unclaim, autoclaim, radius claim, contiguous mode, `/clan map`
- ✅ Clan core on first claim + teleport home (tier 1)
- ✅ Clan bank deposit / withdraw (Vault)
- ✅ Shared clan chest (base tier)
- ✅ Allies and free identity (colors / free tags)
- ✅ Basic protection flags and visual toggles
- ✅ YAML, SQLite, and MySQL storage
- ✅ PlaceholderAPI expansion (`%relishclans_*%`)
- ✅ Full chest GUI (Bedrock forms when Floodgate is present)

### ⭐ **Premium Version**
- ⭐ Wars — declare, surrender, capture, war GUI
- ⭐ Clan fly in claims
- ⭐ Core upgrades (tier 2+) and core relocator
- ⭐ Expansion boosts (claim / member limits)
- ⭐ Claim effects (heal zone, XP boost, and similar)
- ⭐ Claim activity logs and movement replay
- ⭐ Advanced / paid flag unlocks
- ⭐ Premium identity tags

---

## 📦 **Installation**

1. **Download** the plugin JAR file
2. **Place** it in your server's `plugins` folder
3. **Start/Restart** your server
4. **(Optional)** For premium features, buy a license key from [M5LB Store](https://m5lb.run.place/)
5. **Place license key** in `config.yml` (`license-key`)
6. **Reload** the plugin

```bash
/clan help       # View commands
/clan license    # License status (admin)
/clan reload     # Reload configuration
```

Full guide: [docs/Installation.md](docs/Installation.md)

---

## 🎮 **Commands & Usage**

**Aliases:** `/clan`, `/clans`, `/c`

### 👤 **Player / Clan Commands**

| Command | Description |
|---------|-------------|
| `/clan create <name>` | Create a clan |
| `/clan disband` | Disband (confirm twice) |
| `/clan invite <player>` | Invite a player |
| `/clan join <clan>` | Accept an invite |
| `/clan leave` | Leave your clan |
| `/clan claim [radius]` | Claim chunk or area |
| `/clan unclaim [radius\|all]` | Unclaim chunk, radius, or all |
| `/clan autoclaim` | Toggle walk-to-claim |
| `/clan map` | Chat claim map + borders |
| `/clan gui` | Open clan GUI |
| `/clan bank` | Clan bank GUI |
| `/clan chest` | Shared storage |
| `/clan teleport` | Teleport to core |
| `/clan color [name]` | Set clan color |
| `/clan tag [symbol]` | Set icon tag |
| `/clan identity` | Color & tag picker GUI |
| `/clan ally <clan>` | Request / accept alliance |
| `/clan info [clan]` | Clan details |
| `/clan fly` | Toggle clan fly (Premium) |
| `/clan war <clan>` | Declare war (Premium) |
| `/clan surrender <clan>` | End war (Premium) |
| `/clan movecore` | Move clan core (Premium) |
| `/clan toggle <option>` | Particles / titles / bossbars / fly |

### 👑 **Admin Commands**

| Command | Description |
|---------|-------------|
| `/clan admin clans` | Browse and manage all clans |
| `/clan admin wars` | View / force-end wars |
| `/clan admin endwar <a> <b>` | Force-end a war |
| `/clan license` | License status |
| `/clan reload` | Reload config and language |

Complete reference: [docs/Commands.md](docs/Commands.md)

---

## 🔐 **Permissions**

| Permission | Default | Description |
|------------|---------|-------------|
| `relishclans.command` | `true` | Use `/clan` |
| `relishclans.admin` | `op` | Admin bypass, reload, `/clan admin` |
| `relishclans.cooldown.bypass` | `op` | Bypass action cooldowns |

Clan **roles** (Member → Officer → Admin → Leader) gate in-game actions such as claim, war, bank withdraw, and identity.

See [docs/Permissions.md](docs/Permissions.md)

---

## 🔧 **Configuration**

### ⚙️ **Basics**
```yaml
settings:
  max-members: 25
  max-claims: 50
  contiguous-claims: false
  max-claim-radius: 2
  claim-buffer: 1

storage:
  type: YAML   # YAML | SQLITE | MYSQL

language: "en"

license-key: ""
check-for-updates: true

cooldowns:
  teleport: 30
  claim: 3
  war: 60
```

### 🎨 **Clan identity & core**
```yaml
clan-identity:
  default-color: red
  default-tag: "⚔"
  colors: [red, dark_red, gold, yellow, green, aqua, blue, light_purple, white, gray]

core:
  levels:
    1: { icon: IRON_BLOCK, upgrade-cost: 0, extra-capture-seconds: 0, radius-bonus: 0 }
    4: { icon: NETHERITE_BLOCK, upgrade-cost: 40000, extra-capture-seconds: 120, radius-bonus: 3 }

war:
  capture-seconds: 120
  auto-end-seconds: 300
```

Full guide: [docs/Configuration.md](docs/Configuration.md)

---

## 📊 **PlaceholderAPI**

Identifier: `relishclans`

```text
%relishclans_name%
%relishclans_tag%
%relishclans_display_name%
%relishclans_displayname_legacy%
%relishclans_bank%
%relishclans_claims%
%relishclans_members%
%relishclans_role%
%relishclans_at_war%
%relishclans_power%
%relishclans_rank%
```

See [docs/PlaceholderAPI.md](docs/PlaceholderAPI.md)

---

## 🌍 **Language**

Bundled: 🇺🇸 **English** (`lang/en.yml`).

Copy to `lang/<code>.yml`, set `language: "<code>"` in `config.yml`, then `/clan reload`.

---

## 📚 **Documentation**

Browse the docs site: [im5lb.github.io/RelishClans](https://im5lb.github.io/RelishClans)

---

## 💬 **Support**

<div align="center">

[![Discord](https://img.shields.io/badge/Discord-Support-7289da?style=for-the-badge&logo=discord)](https://discord.gg/jDr2KZcGXk)
[![Store](https://img.shields.io/badge/Store-License%20Keys-gold?style=for-the-badge)](https://m5lb.run.place/)
[![Donate](https://img.shields.io/badge/💖%20Donate-Love-ff69b4?style=for-the-badge)](https://creators.sa/m5lb)

</div>

---

<div align="center">

**Made with ❤️ by M5LB**

</div>
