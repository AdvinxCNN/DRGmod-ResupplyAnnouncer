# ResupplyAnnouncer

Deep Rock Galactic mod that announces resupply pickups to the team with a fully editable, English / Simplified Chinese message template.

深岩银河模组：按一句可以完整编辑的中英文模板，向全队播报领取补给的情况。

**Download / 下载：** full version, this repo / 满血版（本仓库）：[GitHub Releases](https://github.com/AdvinxCNN/DRGmod-ResupplyAnnouncer/releases/latest) · pak-only Lite version / 纯 pak 的 Lite 版：[mod.io](https://mod.io/g/drg/m/resupplyannouncer)

Install the full version's zip with [mintcat](https://github.com/iris-cat-dev/mintcat) (UE4SS-Lite loader enabled); the game's built-in Modding Menu alone cannot load it. The Lite version on mod.io is subscribed to in the Modding Menu.

满血版请用 [mintcat](https://github.com/iris-cat-dev/mintcat)（开启 UE4SS-Lite 加载器）安装 zip，仅靠游戏内置 Modding Menu 无法加载；mod.io 上的 Lite 版在 Modding Menu 里订阅即可。

---

## English

Announce resupply pickups to the team with a fully editable message template. Includes English and Simplified Chinese settings, switched with the two language buttons at the top of the ModHub settings page.

### Requirements and installation

- Deep Rock Galactic, Windows 64-bit.
- **mintcat with its UE4SS-Lite / UE4SSL native-mod loader enabled.** This archive contains both `ResupplyAnnouncer.pak` and `main.dll` at the root. Download the zip from GitHub Releases and add the complete zip in mintcat; do not extract just the pak. The mod.io page is the separate Lite version (see below), not this one.
- **ModHub** for the settings page.
- Only the host needs to install this mod; teammates receive normal in-game chat messages.
- This is a native-loader mod, not a pak-only mod for the game's built-in Modding Menu. Subscribing through that menu alone does not load `main.dll`, so the announcements will not work.
- Disable earlier copies of ResupplyAnnouncer and other resupply announcement mods to avoid duplicate messages. An older ResupplyAnnouncer and this release must not be enabled together.

Open **ModHub → ResupplyAnnouncer → Template**.

### Features

- Announces pickups from normal supply pods and abandoned resupply pods.
- Shows a player's pickup count, the team total, and that player's percentage of the total.
- Fully editable template with live preview, Save, Restore default, and Send test message.
- English / Simplified Chinese interface, including button labels, help, tooltips, preview text and status messages. Language is remembered across restarts.
- Event-driven pickup detection: no periodic polling or per-frame update loop.

### Template placeholders

- `\c`: class name, following the **game's language**, independently of the interface language.
- `\p`: player name.
- `\m`: this player's pickup count in the current mission or stage, including the current pickup.
- `\M`: the team's total pickup count in the current mission or stage, including the current pickup.
- `\r`: this player's share of the team total, up to one decimal place (`25%`, `33.3%`).
- `\\`: one literal backslash.

Reorder, repeat, or omit placeholders freely. Unknown escapes remain unchanged. Save an empty template to count pickups without sending announcements.

Switching interface language **does not translate, replace or save your template draft**. To use the English or Chinese default message, select that language and click **Restore default**; this replaces and saves the template. Copy any custom template you want to keep before restoring defaults. Fresh installations start in English. Existing configurations from the Chinese-only version keep their template and start in Simplified Chinese.

### Counting and test behavior

Counts reset for each mission or Deep Dive stage. Pickups from players who leave remain in the team total. Players with identical names share a count. Repairing an abandoned pod does not itself count as a pickup.

Send test message uses sample values (Engineer Karl, 2 personal pickups out of 8 team pickups). It sends the current draft to the team's chat without saving it or increasing the counters.

Settings are stored locally in `FSD/Saved/SaveGames/Mods/ResupplyAnnouncer/ResupplyAnnouncer.ini`.

### Lite version on mod.io

ResupplyAnnouncer Lite is a pak-only version without the DLL: subscribe to it in the game's Modding Menu, no mintcat or UE4SS needed. It finds supply pods with a periodic scan and keeps its own settings. If both versions are installed, Lite stays silent and this version announces.

### Links

- mintcat (mod manager with the native-mod loader): https://github.com/iris-cat-dev/mintcat
- ResupplyAnnouncer Lite (pak-only, mod.io): https://mod.io/g/drg/m/resupplyannouncer

---

## 简体中文

按一句可以完整编辑的模板，向全队播报领取补给的情况。ModHub 页面提供 **简中** / **En** 按钮切换中英文。

### 依赖与安装

- 深岩银河 Windows 64 位版。
- **mintcat，并启用其 UE4SS-Lite / UE4SSL 原生模组加载器。** 安装包根目录包含 `ResupplyAnnouncer.pak` 和 `main.dll`，请从 GitHub Releases 下载 zip，在 mintcat 中添加整个 zip，不要只取 pak。mod.io 页面是另一个 Lite 版（见下文），不是本版本。
- **ModHub**，用于显示设置页。
- 只需要主机安装；队友通过游戏聊天收到播报。
- 本模组包含原生 DLL，不是游戏内置 Modding Menu 可独立加载的纯 pak 模组；仅通过该菜单订阅不会加载 `main.dll`，播报功能不会生效。
- 请禁用旧版 ResupplyAnnouncer 和其他吃补播报模组，避免重复播报。新旧版本不要同时启用。

进入 **ModHub → ResupplyAnnouncer → Template** 即可设置。

### 功能

- 普通补给舱和废弃补给舱均可检测。
- 支持个人领取份数、全队总份数、个人占比。
- 整句模板自由编辑，支持实时预览、保存、恢复默认和发送测试消息。
- 标题、说明、按钮、悬浮提示、预览及操作状态均支持中英文，语言选择会保存。
- 事件触发，没有定时轮询或逐帧更新。

### 模板占位符

- `\c`：职业名，跟随**游戏语言**，不随本页面的语言按钮改变。
- `\p`：玩家名。
- `\m`：该玩家本关已领取的份数，包含这次。
- `\M`：全队本关总领取份数，包含这次。
- `\r`：该玩家占全队总数的比例，最多一位小数，例如 `25%`、`33.3%`。
- `\\`：输出一个反斜杠。

占位符可任意排序、重复或省略，未知转义原样保留。留空并保存可以只计数、不播报。

切换语言**不会翻译、覆盖或保存正在编辑的模板**。需要对应语言的默认播报时，先选语言，再点“恢复默认”；该按钮会替换并保存模板；需要保留原模板时，请先复制到别处备份。全新安装默认英文；从旧中文版本升级时保留原模板并使用简中界面。

默认中文模板：`\c\p刚刚吃了1份补给，一共吃了\m份（全队共吃\M份），占全队总数的\r`。

### 计数与测试说明

每个任务、深潜的每一层重新计数。离队玩家的领取份数仍包含在全队总数内，同名玩家合并计数。修复废弃补给舱本身不计为领取。

“发送测试消息”使用示例数据（工程师 Karl，本人 2 份、全队 8 份），把输入框中的模板发到全队聊天；不会保存模板，也不会增加真实计数。

配置位于 `FSD/Saved/SaveGames/Mods/ResupplyAnnouncer/ResupplyAnnouncer.ini`。

### mod.io 上的 Lite 版

ResupplyAnnouncer Lite 是不带 DLL 的纯 pak 版：在游戏内 Modding Menu 订阅即可使用，不需要 mintcat 或 UE4SS。它靠定时扫描发现补给舱，设置与本版本互不相通。两版同时安装时 Lite 自动不播报，由本版本播报。

### 链接

- mintcat（带原生模组加载器的模组管理器）：https://github.com/iris-cat-dev/mintcat
- ResupplyAnnouncer Lite（纯 pak，mod.io）：https://mod.io/g/drg/m/resupplyannouncer
