# EnchantShop

An enchant shop plugin for **PaperMC 26.3** by **SquidNetwork**. The menu a player gets depends on the item they are holding: hold a sword and you see sword enchants, hold a pickaxe and you see pickaxe enchants. Java players get a chest GUI, Bedrock players get a native form.

## Features

- **Hold-to-open menus**: the shop only opens when the held item matches a category (sword, axe, pickaxe, shovel, hoe, helmet, chestplate, leggings, boots, bow, crossbow, trident, fishing rod, mace). Holding anything else, like an anvil, does not open the menu.
- **Java GUI**: a 3-row chest menu showing the held item, 7 enchants per page, and arrow buttons for previous/next page.
- **Bedrock forms** (via Floodgate): buttons with icons, colored text, and fully customizable names and format.
- **Vault economy**: works with any Vault-compatible economy plugin.
- **Upgrade by level**: each purchase raises the enchant by one level, up to a configurable max level.
- **Smart filtering**: only enchants that fit the held item are shown, and conflicting enchants (e.g. Sharpness and Smite) can be blocked.
- **Fully configurable**: categories, enchants, prices, GUI, form, and messages.
- **Multi-language messages**: Indonesian and English included.

## Requirements

| Requirement | Notes |
|---|---|
| Paper 26.3 | Java 25 |
| [Vault](https://www.spigotmc.org/resources/vault.34315/) | Required |
| An economy plugin | Any plugin that provides a Vault economy |
| [Floodgate](https://geysermc.org/download#floodgate) | Optional, needed for Bedrock forms. Without it, everyone uses the GUI. |

## Installation

1. Download `EnchantShop-1.0.jar` from the Releases page.
2. Put it in your server's `plugins/` folder.
3. Make sure Vault and an economy plugin are installed.
4. Start the server. The config files are generated in `plugins/EnchantShop/`.

## Commands and permissions

| Command | Description | Permission |
|---|---|---|
| `/eshop` (alias `/enchantshop`) | Open the shop for the item in your hand | `enchantshop.use` (default: everyone) |
| `/eshop reload` | Reload all config files | `enchantshop.reload` (default: op) |

## Configuration

| File | Purpose |
|---|---|
| `config.yml` | Language, price mode, number format, GUI layout and texts, sounds |
| `eshop.yml` | Item categories and the enchant list (prices, max levels, categories) |
| `form.yml` | Bedrock form title, button format, icons, and custom enchant names |
| `messages/messages_id.yml` | Indonesian messages |
| `messages/messages_en.yml` | English messages |

### Pricing

Set `price-mode` in `config.yml`:

- `LEVEL_MULTIPLIER` (default): price multiplied by the target level. With a base price of 100,000, level 1 costs 100,000 and level 2 costs 200,000.
- `FLAT`: the same price for every level.

### Adding or changing enchants

Edit `eshop.yml`:

```yaml
enchants:
  sharpness:
    enchantment: "minecraft:sharpness"
    display-name: "Sharpness"
    icon: ENCHANTED_BOOK
    price: 100000
    max-level: 5
    categories: ["sword", "axe"]
```

Use `categories: ["*"]` for enchants available on every category. The enchant id (`sharpness` above) is also the key used in `form.yml`.

### Bedrock form

In `form.yml`, the button format supports `{name}`, `{price}`, `{current}`, `{next}` and `{max}`:

```yaml
default-icon: "textures/items/book_enchanted"
button-format: "&d{name}\n&aHarga: &eRp{price}"
max-button-format: "&d{name}\n&cMAX LEVEL"
```

### Language

Set `language: en` or `language: id` in `config.yml`, then run `/eshop reload`.

## Building from source

Requires JDK 25 and Maven.

```
mvn clean package
```

The jar is created at `target/EnchantShop-1.0.jar`.

## Author

SquidNetwork
