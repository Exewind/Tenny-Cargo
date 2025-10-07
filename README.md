# 🚚 Tenny-Cargo

<div align="center">

![Version](https://img.shields.io/badge/version-1.0.0-blue.svg)
![Framework](https://img.shields.io/badge/framework-ESX%20%7C%20QB--Core-green.svg)
![License](https://img.shields.io/badge/license-Custom-red.svg)
![Language](https://img.shields.io/badge/language-Lua-orange.svg)

**Modern FiveM Cargo Delivery System**

*ESX/QB-Core Compatible • Multi-Language Support • Modern NUI Interface*

[📖 Documentation](#-features) • [🛠️ Installation](#️-installation) • [⚙️ Configuration](#️-configuration) • [🎮 Usage](#-usage)

</div>

---

## 📋 Table of Contents

- [✨ Features](#-features)
- [🛠️ Installation](#️-installation)
- [⚙️ Configuration](#️-configuration)
- [🎮 Usage](#-usage)
- [🌍 Language Support](#-language-support)
- [🔧 Advanced Features](#-advanced-features)
- [🐛 Troubleshooting](#-troubleshooting)
- [📋 Changelog](#-changelog)
- [📄 License](#-license)

---

## ✨ Features

### 🎯 **Main Features**

| Feature | Description |
|---------|-------------|
| 🔄 **Framework Compatibility** | ESX & QB-Core automatic detection |
| 🎨 **Modern NUI** | Responsive and user-friendly design |
| 🌍 **Multi-Language** | Turkish and English language options |
| 🚛 **Realistic Experience** | Package carrying, vehicle driving, delivery |
| 🗺️ **GPS Navigation** | Automatic route drawing and guidance |
| 📍 **Customizable** | 10+ different delivery points |
| 💰 **Reward System** | Total reward after completing all deliveries |

### 🚛 **Cargo System**

- **🏢 Job Start** - Start job from cargo center
- **🚗 Vehicle Spawn** - Automatic cargo vehicle delivery
- **📦 Package Management** - Inventory system with package control
- **📍 Sequential Delivery** - Deliver in specific order
- **🗺️ GPS Guidance** - Automatic route for each delivery
- **💰 Reward System** - Total reward after completing all deliveries

### 🎮 **User Interface**

- **🎨 Modern Design** - Emoji and icon supported interface
- **📱 Responsive Menu** - Compatible with all screen sizes
- **⚡ Real-time** - Job status tracking
- **🖱️ Easy to Use** - One-click operations

---

## 🛠️ Installation

### 📋 **Requirements**

- ✅ **ESX** or **QB-Core** framework
- ✅ **FiveM Server** (v1.0+)
- ✅ **MySQL** database (optional)

### 📥 **Installation Steps**

#### 1️⃣ **Download Files**
```bash
git clone https://github.com/Exewind/Tenny-Cargo.git
```

#### 2️⃣ **Install to Server**
1. Copy `tenny-cargo` folder to `resources` directory
2. Add to your `server.cfg`:
```cfg
ensure tenny-cargo
```

#### 3️⃣ **Database Settings** *(Optional)*
- Script works automatically
- No additional database tables required

#### 4️⃣ **Restart Server**
```bash
restart tenny-cargo
```

---

## ⚙️ Configuration

### 🔧 **Basic Settings** (`config.lua`)

```lua
-- Framework setting
Config.Framework = 'auto' -- 'esx', 'qb', 'auto'

-- Language setting
Config.Locale = 'en' -- 'tr' or 'en'

-- Debug mode
Config.Debug = false

-- Key system
Config.UseKeys = false -- Give vehicle keys
```

### 👥 **NPC Settings**

```lua
-- NPC models
Config.NPCModel = 'a_m_m_business_01'
Config.DeliveryNPCModel = 'a_m_m_business_01'

-- Job start NPC
Config.JobStartNPC = {
    vector4(78.8895, 112.5281, 81.1682, 163.7160) -- Los Santos Post Office
}
```

### 📍 **Delivery Points**

```lua
Config.DeliveryLocations = {
    {name = "1", npc = vector4(17.9662, -12.6672, 70.1161, 343.0002)},
    {name = "2", npc = vector4(-333.2365, 101.2704, 71.2182, 274.5316)},
    {name = "3", npc = vector4(3.4313, 36.9017, 71.5305, 167.6731)},
    -- Add more locations...
}
```

### 🚗 **Vehicle Settings**

```lua
-- Cargo vehicle
Config.VehicleModel = 'boxville'
Config.VehicleSpawn = vector4(84.0409, 105.8925, 79.1686, 252.9563)

-- Blip settings
Config.BlipSprite = 478
Config.BlipColor = 2
Config.BlipScale = 0.8
```

### 💰 **Reward System**

```lua
-- Payment per delivery (for total calculation)
Config.PaymentPerDelivery = 5000

-- Total reward = PaymentPerDelivery × Number of Delivery Points
-- Example: 5000 × 10 = 50,000$ (for 10 delivery points)

-- Package settings
Config.PackageModel = 'prop_cs_cardbox_01'
Config.PackageWeight = 1.0
```

---

## 🎮 Usage

### 👤 **For Players**

| Step | Description |
|------|-------------|
| 1️⃣ | **Go to Cargo Center** - Find "Cargo Center" blip on map |
| 2️⃣ | **Interact with NPC** - Press [E] to open menu |
| 3️⃣ | **Start Job** - Click "Start Job" button |
| 4️⃣ | **Get Vehicle** - Enter spawned cargo vehicle |
| 5️⃣ | **Make Delivery** - Go to delivery points according to GPS |
| 6️⃣ | **Deliver Package** - Press [E] to deliver package |
| 7️⃣ | **Complete All Deliveries** - Deliver all packages |
| 8️⃣ | **Get Total Reward** - Receive total money after all deliveries |

### 👨‍💼 **For Admins**

- **📍 Add Locations**: Add new delivery points from `config.lua`
- **💰 Adjust Rewards**: Change `Config.PaymentPerDelivery` value
- **🐛 Debug Mode**: Set `Config.Debug = true` for debugging

---

## 🌍 Language Support

### 🌐 **Available Languages**

| Language | File | Status |
|----------|------|--------|
| 🇺🇸 **English** | `en.lua` | ✅ Default |
| 🇹🇷 **Turkish** | `tr.lua` | ✅ Full support |

### ➕ **Adding New Language**

1. Add new language file to `locales/` folder (e.g., `de.lua`)
2. Set `Config.Locale = 'de'` in `config.lua`
3. Fill language file with following format:

```lua
Locales = Locales or {}
Locales['de'] = {
    blip_cargo_center = "Frachtzentrum",
    blip_delivery_point = "Lieferpunkt",
    hint_open_menu = "[E] Frachtmenü",
    -- Other translations...
}
```

---

## 🔧 Advanced Features

### 🔑 **Key System Integration**

```lua
-- Supported key systems
Config.UseKeys = true -- To activate

-- Supported systems:
-- ✅ qbx_vehiclekeys
-- ✅ qb-vehiclekeys  
-- ✅ wasabi_carlock
```

### 🚗 **Custom Vehicle Models**

```lua
-- You can use different cargo vehicles
Config.VehicleModel = 'mule'      -- Small cargo vehicle
Config.VehicleModel = 'boxville'  -- Medium cargo vehicle
Config.VehicleModel = 'pounder'   -- Large cargo vehicle
```

### 🗺️ **Blip Customization**

```lua
-- Different blip types
Config.BlipSprite = 478 -- Cargo icon
Config.BlipColor = 2    -- Green color
Config.BlipScale = 0.8  -- Size
```

---

## 🐛 Troubleshooting

### ❓ **Common Issues**

| Issue | Solution |
|-------|----------|
| **Script Not Loading** | Make sure `fxmanifest.lua` is correct |
| **NPC Not Visible** | Ensure `Config.NPCModel` value is valid |
| **Vehicle Not Spawning** | Ensure `Config.VehicleModel` value is valid |
| **No Money Given** | Check framework integration |

### 🔍 **Debug Mode**

```lua
Config.Debug = true -- To see debug messages
```

---

## 📋 Changelog

### 🆕 **v1.0.0** - *Initial Release*

- ✅ Initial version released
- ✅ ESX/QB-Core compatibility
- ✅ Modern NUI interface
- ✅ Multi-language support
- ✅ GPS navigation system
- ✅ Customizable locations

---

## 📄 License

This software is free to use, but the following restrictions apply:

❌ **May not be modified**  
❌ **May not be sold**  
❌ **Derivative works are not allowed**  
❌ **Commercial use is strictly prohibited**  
✅ **May only be used in its original form, free of charge**

Any use that violates these restrictions is strictly prohibited.

---

**TR**

Bu yazılım ücretsizdir ancak aşağıdaki kısıtlamalar geçerlidir:

❌ **Değiştirilemez**  
❌ **Satılamaz**  
❌ **Türev çalışma yapılamaz**  
❌ **Ticari kullanım yasak**  
✅ **Sadece orijinal haliyle ücretsiz kullanılabilir**

Bu kısıtlamalara uymayan kullanım yasaktır.

---

## 👨‍💻 Developer

**Tenny-Cargo** - Modern FiveM cargo system

## 📞 Support

- **🐛 GitHub Issues**: Bug reports and feature requests
- **💬 Discord**: https://discord.gg/ZBuNKA6ZxQ

---

<div align="center">

### ⭐ Don't Forget to Star if You Liked It!

This script is developed for free for the FiveM community.  
If you liked it, you can support us by giving a star on GitHub! 🚀

</div>
