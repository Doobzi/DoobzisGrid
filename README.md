<p align="center">
  <img src="https://i.ibb.co/XxK0qrFt/2c781d93-d521-478c-a687-6c803eebfed6.png" alt="Doobzi's Grid Logo" width="280" />
</p>

<h1 align="center">Doobzi's Grid</h1>

<p align="center">
  <strong>A feature-rich Bounty Hunting, Economy, Shop & Auction House plugin for Unturned</strong><br/>
  Built for <a href="https://github.com/SmartlyDressedGames/Legally-Distinct-Missile">RocketMod v4</a> &bull; .NET Framework 4.8
</p>

<p align="center">
  <img src="https://img.shields.io/badge/version-2.3.0-blue?style=flat-square" alt="Version" />
  <img src="https://img.shields.io/badge/platform-RocketMod%20v4-green?style=flat-square" alt="Platform" />
  <img src="https://img.shields.io/badge/framework-.NET%204.8-purple?style=flat-square" alt="Framework" />
  <img src="https://img.shields.io/badge/license-MIT-orange?style=flat-square" alt="License" />
</p>

---

## Table of Contents

- [Features](#-features)
- [Installation](#-installation)
- [Building from Source](#-building-from-source)
- [Commands](#-commands)
- [Configuration](#-configuration)
- [Permissions](#-permissions)
- [Achievements](#-achievements)
- [Data Storage](#-data-storage)
- [Discord Integration](#-discord-integration)
- [Pricing Formula](#-pricing-formula)
- [Troubleshooting](#-troubleshooting)
- [License](#-license)

---

## ✨ Features

| Module | Highlights |
|--------|------------|
| **Bounty System** | Place bounties, stack from multiple players, auto-collect on kill, kill streaks, tiered rankings (Bronze → Legendary), self-defense bonuses, most-wanted broadcasts, anonymous bounties, expiry & auto-refund |
| **Economy** | Starting balance, daily login bonus, passive salary, bank interest, transfer tax, full transaction history |
| **Shop** | Auto-generated shop with every Unturned item, rarity-based pricing, stock limits with timed refresh, category browsing, admin price/stock editing |
| **Auction House** | Player-to-player item trading, listing expiry, per-player listing limits, search by keyword |
| **Achievements** | 13 configurable achievements with customizable names, descriptions & thresholds — fully toggleable |
| **MySQL** | Optional MySQL backend — swap from JSON files with a single config toggle. Perfect for multi-server networks |
| **Discord Webhooks** | Optional real-time notifications for bounty & auction events posted directly to your Discord channel |
| **Fully Configurable** | Plugin name, currency symbol, chat prefix, bounty tier names/icons/thresholds, tax rates, and more — all from one XML config |

---

## 📦 Installation

### Quick Install (Recommended)

1. Download the **latest release** from the [Releases](https://github.com/Doobzi/DoobzisGrid/releases) page
2. Copy **`DoobzisGrid.dll`** into your server's `Rocket/Plugins/` folder
3. *(Optional — only if using MySQL)* Copy **`MySql.Data.dll`** into your server's `Rocket/Libraries/` folder
4. Restart your server
5. The plugin will auto-generate its config file at:
   ```
   Rocket/Plugins/DoobzisGrid/DoobzisGrid.configuration.xml
   ```
6. Edit the config to your liking, then run `/bountyreload` in-game

> **Note:** The shop auto-populates with every Unturned item on first load. This is normal and may take a moment.

---

## 🔨 Building from Source

```bash
git clone https://github.com/Doobzi/DoobzisGrid.git
cd DoobzisGrid
dotnet build -c Release
```

The compiled DLL will be at `bin/Release/net48/DoobzisGrid.dll`.

All dependencies (RocketMod, Unturned, MySql.Data) are pulled automatically via NuGet — no manual DLL copying required.

---

## 🎮 Commands

### Bounty System

| Command | Alias | Permission | Description |
|---------|-------|------------|-------------|
| `/bountyadd <player> <amount>` | `/ba` | `bounty.add` | Place a bounty on a player |
| `/bountylist` | `/bl` | `bounty.list` | View all active bounties |
| `/bountytop` | `/bt` | `bounty.top` | See who has the highest bounty |
| `/bountyhunter` | `/bh` | `bounty.hunter` | Top 10 hunters leaderboard |
| `/bountyclear <player>` | `/bc` | `bounty.clear` | Remove all bounties on a player *(admin)* |

### Economy

| Command | Alias | Permission | Description |
|---------|-------|------------|-------------|
| `/balance` | `/bal` | `economy.balance` | Check your current balance |
| `/pay <player> <amount>` | — | `economy.pay` | Send money to another player |
| `/transactions` | `/txn` | `economy.transactions` | View recent transactions |
| `/profile` | — | `economy.profile` | View your full profile & achievements |

### Shop

| Command | Alias | Permission | Description |
|---------|-------|------------|-------------|
| `/shop [page]` | — | `shop.browse` | Browse all shop items |
| `/shopbuy <ID> [qty]` | `/buy` | `shop.buy` | Buy an item by ID |
| `/sell <ID> [qty]` | — | `shop.sell` | Sell an item from your inventory |
| `/shopsearch <keyword>` | `/ss` | `shop.browse` | Search for items by name |
| `/shopcats` | — | `shop.browse` | View all shop categories |
| `/shopcat <category> [page]` | — | `shop.browse` | Browse items in a category |
| `/shopadd <ID> <price>` | — | `shop.admin` | Add an item to the shop *(admin)* |
| `/shoprem <ID>` | — | `shop.admin` | Remove an item from the shop *(admin)* |
| `/shopedit <ID> <price> <stock>` | — | `shop.admin` | Edit item price/stock *(admin)* |

### Auction House

| Command | Alias | Permission | Description |
|---------|-------|------------|-------------|
| `/ahlist [page]` | — | `auction.use` | Browse active auction listings |
| `/ahsell <itemId> <price>` | — | `auction.use` | List an item for sale |
| `/ahbuy <listingId>` | — | `auction.use` | Purchase a listing |
| `/ahcancel <listingId>` | — | `auction.use` | Cancel your own listing |
| `/ahsearch <keyword>` | — | `auction.use` | Search auction listings |
| `/ahmy` | — | `auction.use` | View your active listings |

### Admin & Utility

| Command | Alias | Permission | Description |
|---------|-------|------------|-------------|
| `/ecogive <player> <amount>` | — | `economy.admin` | Give money to a player |
| `/ecotake <player> <amount>` | — | `economy.admin` | Take money from a player |
| `/ecoset <player> <amount>` | — | `economy.admin` | Set a player's balance |
| `/ecoreset <player>` | — | `economy.admin` | Reset a player to starting balance |
| `/bountyreload` | — | `bounty.reload` | Hot-reload plugin configuration |
| `/gridhelp` | — | `grid.help` | Show all available commands |

---

## ⚙️ Configuration

The plugin generates a fully-commented XML config at:  
`Rocket/Plugins/DoobzisGrid/DoobzisGrid.configuration.xml`

All percentage values are **whole numbers** (e.g. `5` = 5%). Use `/bountyreload` in-game to apply changes without restarting.

<details>
<summary><strong>General Settings</strong></summary>

| Setting | Default | Description |
|---------|---------|-------------|
| `PluginName` | `Doobzi's Grid` | Name shown in chat messages (e.g. `[Doobzi's Grid]`) |
| `ChatPrefix` | *(empty)* | Custom chat prefix — auto-generated from PluginName if blank |
| `CurrencySymbol` | `$` | Currency symbol used in all messages |

</details>

<details>
<summary><strong>Economy Settings</strong></summary>

| Setting | Default | Description |
|---------|---------|-------------|
| `StartingBalance` | `1000` | Money new players receive |
| `DailyBonusMin` | `200` | Minimum daily login bonus |
| `DailyBonusMax` | `500` | Maximum daily login bonus |
| `InterestRatePercent` | `1` | Interest rate on bank balance per interval |
| `InterestMaxPayout` | `500` | Maximum interest payout per interval |
| `InterestPayoutMinutes` | `60` | Minutes between interest payouts |
| `SalaryAmount` | `50` | Passive salary per interval while online |
| `SalaryIntervalMinutes` | `10` | Minutes between salary payments |
| `TransferTaxPercent` | `5` | Tax deducted on `/pay` transfers |

</details>

<details>
<summary><strong>Bounty Settings</strong></summary>

| Setting | Default | Description |
|---------|---------|-------------|
| `MinimumAmount` | `100` | Minimum amount for placing a bounty |
| `ExpiryHours` | `48` | Hours before a bounty expires and refunds |
| `AnonymousFeePercent` | `10` | Extra fee for anonymous bounties |
| `SelfDefenseBonusPercent` | `25` | Bonus for killing someone hunting your bounty |
| `StreakBonusPercent` | `10` | Bonus per consecutive kill streak |
| `AnnounceNewBounties` | `true` | Broadcast new bounties server-wide |
| `AnnounceCompletedBounties` | `true` | Broadcast bounty completions server-wide |
| `MostWantedAnnouncementMinutes` | `15` | Minutes between "Most Wanted" broadcasts (0 = off) |

</details>

<details>
<summary><strong>Bounty Tier Settings</strong></summary>

Tiers are evaluated top-down. Any bounty below the Silver threshold is Bronze.

| Setting | Default | Description |
|---------|---------|-------------|
| `LegendaryThreshold` | `15000` | Amount needed for Legendary tier |
| `LegendaryName` | `LEGENDARY` | Display name |
| `LegendaryIcon` | `<<LEGENDARY>>` | Chat icon |
| `GoldThreshold` | `5000` | Amount needed for Gold tier |
| `GoldName` | `GOLD` | Display name |
| `GoldIcon` | `<GOLD>` | Chat icon |
| `SilverThreshold` | `1000` | Amount needed for Silver tier |
| `SilverName` | `SILVER` | Display name |
| `SilverIcon` | `[SILVER]` | Chat icon |
| `BronzeName` | `BRONZE` | Display name |
| `BronzeIcon` | `(BRONZE)` | Chat icon |

</details>

<details>
<summary><strong>Shop Settings</strong></summary>

| Setting | Default | Description |
|---------|---------|-------------|
| `StockRefreshMinutes` | `60` | How often shop stock refreshes |
| `DefaultStockPerItem` | `10` | Default stock per item per cycle |
| `SellPricePercent` | `50` | Percentage of buy price players get when selling |

</details>

<details>
<summary><strong>Auction House Settings</strong></summary>

| Setting | Default | Description |
|---------|---------|-------------|
| `ListingExpiryHours` | `24` | Hours before a listing expires |
| `MaxListingsPerPlayer` | `5` | Maximum active listings per player |

</details>

<details>
<summary><strong>MySQL Settings (Optional)</strong></summary>

When enabled, **all data** is stored in MySQL instead of JSON files. Ideal for multi-server networks.

| Setting | Default | Description |
|---------|---------|-------------|
| `Enabled` | `false` | Toggle MySQL storage |
| `Host` | `localhost` | Server address |
| `Port` | `3306` | Server port |
| `Database` | `doobzis_grid` | Database name (must already exist) |
| `Username` | `root` | MySQL username |
| `Password` | *(empty)* | MySQL password |
| `TablePrefix` | `grid_` | Table name prefix |

> **Important:** When using MySQL, copy `MySql.Data.dll` to your server's `Rocket/Libraries/` folder.

</details>

<details>
<summary><strong>Discord Webhook Settings (Optional)</strong></summary>

Sends real-time event notifications to a Discord channel via webhook.

| Setting | Default | Description |
|---------|---------|-------------|
| `Enabled` | `false` | Toggle Discord notifications |
| `WebhookUrl` | *(empty)* | Webhook URL from Discord channel settings |
| `NotifyAuctionListed` | `true` | Post when a new listing is created |
| `NotifyAuctionSold` | `true` | Post when an item is purchased |
| `NotifyAuctionCancelled` | `true` | Post when a listing is cancelled |
| `NotifyBountyPlaced` | `true` | Post when a bounty is placed |
| `NotifyBountyClaimed` | `true` | Post when a bounty is claimed |

</details>

---

## 🔐 Permissions

Add these to your `Permissions.config.xml` to control access.

### All Permission Nodes

| Permission | Group | Commands |
|------------|-------|----------|
| `economy.balance` | Player | `/balance` |
| `economy.pay` | Player | `/pay` |
| `economy.transactions` | Player | `/transactions` |
| `economy.profile` | Player | `/profile` |
| `shop.browse` | Player | `/shop`, `/shopsearch`, `/shopcats`, `/shopcat` |
| `shop.buy` | Player | `/shopbuy` (alias `/buy`) |
| `shop.sell` | Player | `/sell` |
| `auction.use` | Player | `/ahlist`, `/ahsell`, `/ahbuy`, `/ahcancel`, `/ahsearch`, `/ahmy` |
| `bounty.add` | Player | `/bountyadd` |
| `bounty.list` | Player | `/bountylist` |
| `bounty.top` | Player | `/bountytop` |
| `bounty.hunter` | Player | `/bountyhunter` |
| `grid.help` | Player | `/gridhelp` |
| `shop.admin` | Admin | `/shopadd`, `/shoprem`, `/shopedit` |
| `economy.admin` | Admin | `/ecogive`, `/ecotake`, `/ecoset`, `/ecoreset` |
| `bounty.clear` | Admin | `/bountyclear` |
| `bounty.reload` | Admin | `/bountyreload` |

<details>
<summary><strong>Recommended Player Group</strong></summary>

```xml
<Group>
  <Id>default</Id>
  <DisplayName>Player</DisplayName>
  <Permissions>
    <!-- Economy -->
    <Permission>economy.balance</Permission>
    <Permission>economy.pay</Permission>
    <Permission>economy.transactions</Permission>
    <Permission>economy.profile</Permission>
    <!-- Shop -->
    <Permission>shop.browse</Permission>
    <Permission>shop.buy</Permission>
    <Permission>shop.sell</Permission>
    <!-- Auction House -->
    <Permission>auction.use</Permission>
    <!-- Bounty -->
    <Permission>bounty.add</Permission>
    <Permission>bounty.list</Permission>
    <Permission>bounty.top</Permission>
    <Permission>bounty.hunter</Permission>
    <!-- Utility -->
    <Permission>grid.help</Permission>
  </Permissions>
</Group>
```

</details>

<details>
<summary><strong>Recommended Admin Group</strong></summary>

```xml
<Group>
  <Id>admin</Id>
  <DisplayName>Admin</DisplayName>
  <Permissions>
    <!-- All player permissions -->
    <Permission>economy.balance</Permission>
    <Permission>economy.pay</Permission>
    <Permission>economy.transactions</Permission>
    <Permission>economy.profile</Permission>
    <Permission>shop.browse</Permission>
    <Permission>shop.buy</Permission>
    <Permission>shop.sell</Permission>
    <Permission>auction.use</Permission>
    <Permission>bounty.add</Permission>
    <Permission>bounty.list</Permission>
    <Permission>bounty.top</Permission>
    <Permission>bounty.hunter</Permission>
    <Permission>grid.help</Permission>
    <!-- Admin-only -->
    <Permission>shop.admin</Permission>
    <Permission>economy.admin</Permission>
    <Permission>bounty.clear</Permission>
    <Permission>bounty.reload</Permission>
  </Permissions>
</Group>
```

</details>

---

## 🏆 Achievements

13 achievements are included by default. Each can be renamed, re-described, re-thresholded, or disabled individually. A master toggle can turn off the entire system.

| Achievement | Default Name | Description | Threshold |
|-------------|-------------|-------------|-----------|
| `FIRST_BLOOD` | First Blood | Complete your first bounty kill | 1 |
| `FIVE_BOUNTIES` | Bounty Rookie | Complete 5 bounty kills | 5 |
| `TEN_BOUNTIES` | Seasoned Hunter | Complete 10 bounty kills | 10 |
| `TWENTY_FIVE` | Veteran Hunter | Complete 25 bounty kills | 25 |
| `FIFTY_BOUNTIES` | Master Hunter | Complete 50 bounty kills | 50 |
| `BIG_SPENDER` | Big Spender | Place $50,000+ in total bounties | 50,000 |
| `STREAK_3` | Triple Threat | Get a 3 bounty kill streak | 3 |
| `STREAK_5` | Unstoppable | Get a 5 bounty kill streak | 5 |
| `STREAK_10` | Death Incarnate | Get a 10 bounty kill streak | 10 |
| `LEGENDARY_HUNTER` | Legendary Hunter | Collect a Legendary-tier bounty | 15,000 |
| `SURVIVALIST` | Survivalist | Kill someone hunting your bounty | 1 |
| `SHOPAHOLIC` | Shopaholic | Spend $100,000+ in the shop | 100,000 |
| `AUCTIONEER` | Auctioneer | Sell an item on the auction house | 1 |

---

## 💾 Data Storage

By default, all data is stored as JSON files in `Rocket/Plugins/DoobzisGrid/`:

| File | Contents |
|------|----------|
| `economy.json` | Player balances & transactions |
| `bounties.json` | Active bounties |
| `hunters.json` | Hunter stats, streaks & leaderboard |
| `shop.json` | Shop items, prices & stock |
| `achievements.json` | Player achievement progress |
| `auctions.json` | Auction house listings |

> To switch to **MySQL** storage, set `MySQL > Enabled` to `true` in the config and provide your database credentials. See [MySQL Settings](#-configuration) above.

---

## 🔔 Discord Integration

Send real-time notifications to your Discord server:

1. In your Discord server, go to **Channel Settings → Integrations → Webhooks**
2. Create a new webhook and copy the URL
3. Paste the URL into the config under `Discord > WebhookUrl`
4. Set `Discord > Enabled` to `true`
5. Toggle individual event types on/off as needed

Supported events: **Bounty Placed**, **Bounty Claimed**, **Auction Listed**, **Auction Sold**, **Auction Cancelled**

---

## 💰 Pricing Formula

The shop auto-generates prices for every Unturned item using:

```
Price = BasePrice(type) × RarityMultiplier
```

<details>
<summary><strong>Base Prices by Item Type</strong></summary>

| Type | Base Price | Type | Base Price |
|------|-----------|------|-----------|
| Gun | $750 | Sentry | $500 |
| Melee | $200 | Generator | $300 |
| Throwable | $300 | Backpack | $250 |
| Trap | $250 | Vest | $200 |
| Medical | $75 | Storage | $150 |
| Food | $30 | Sight | $150 |
| Water | $30 | Barrel | $150 |
| Clothing | $100–150 | Magazine | $25 |
| Tool | $100 | Farm | $20 |

</details>

<details>
<summary><strong>Rarity Multipliers</strong></summary>

| Rarity | Multiplier |
|--------|-----------|
| Common | 1.0× |
| Uncommon | 1.5× |
| Rare | 2.5× |
| Epic | 4.0× |
| Legendary | 7.0× |
| Mythical | 12.0× |

</details>

---

## ❓ Troubleshooting

<details>
<summary><strong><code>Assets.find(allItems)</code> doesn't compile</strong></summary>

If your Unturned version doesn't support the generic `Assets.find<T>(List<T>)`, replace the call in `ShopManager.cs` with:

```csharp
var allAssets = Assets.find(EAssetType.ITEM);
var allItems = allAssets?.OfType<ItemAsset>().ToList() ?? new List<ItemAsset>();
```

</details>

<details>
<summary><strong>MySQL errors on load</strong></summary>

- Ensure `MySql.Data.dll` is in your server's `Rocket/Libraries/` folder (not `Plugins/`)
- Verify your database exists and credentials are correct
- Check that your MySQL server allows connections from the game server's IP

</details>

<details>
<summary><strong>Plugin doesn't load</strong></summary>

- Verify `DoobzisGrid.dll` is in the `Rocket/Plugins/` folder
- Check the RocketMod console log for error messages on startup
- Ensure you are running RocketMod v4 with .NET Framework 4.8

</details>

---

## 📄 License

This project is provided as-is for use on Unturned servers. Feel free to modify and distribute.

---

<p align="center">
  Made with ❤️ by <strong>Doobzi</strong>
</p>
