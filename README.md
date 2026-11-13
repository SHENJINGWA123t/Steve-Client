# STEVE CLIENT

版本：2.11.1

一个面向 **Minecraft for Windows（基岩版 / Bedrock Edition）** 的轻量启动器、自动 DLL 注入器与资源安装器。界面参考了桌面客户端的布局，支持一键启动游戏、自动扫描并注入本地 DLL，以及把资源包 / 行为包 / 世界自动解包到对应账号的游戏目录。启动器与应用图标使用新版经典 Steve 头像。

> 本项目不附带任何 DLL、资源包、行为包或地图。你需要使用自己已有的、来源可信的文件。

---

## 功能

- **一键启动 Minecraft for Windows**：通过 Windows 应用激活接口启动商店版游戏。
- **一键结束游戏**：启动按钮右侧的“结束游戏”按钮，确认后会强制结束正在运行的 Minecraft 进程。
- **游戏档案**：左侧新增 **游戏档案**，默认存在 **Minecraft 官方版**；点击“新增档案”会在弹窗中填写档案名称和启动路径，启动中心可切换当前档案。
- **档案导入 / 导出**：游戏档案页面提供“导入 / 导出”圆角按钮，可把全部档案保存为 `.steveprofiles` 文件，或从文件合并导入；重名档案自动加序号，不覆盖现有档案。
- **批量管理**：游戏档案、DLL 模块和资源库均支持批量模式，可勾选多项后批量删除；DLL 还支持批量启用/禁用，并提供全选和清空选择。
- **关闭行为可选**：第一次点击关闭按钮时会询问“隐藏到系统托盘”还是“直接关闭”；隐藏后左键托盘图标恢复界面，右键可打开或彻底关闭。之后可在设置中随时切换。
- **全局启动模式**：启动游戏按钮旁可选“带 DLL”或“仅启动”；默认带 DLL。托盘“直接启动”始终使用同一个全局模式。
- **托盘直接启动**：启动器隐藏到系统托盘后，右键菜单“直接启动”会按当前全局启动模式启动预设档案：带 DLL 模式会注入已启用 DLL，仅启动模式不会注入；没有已启用 DLL 时，带 DLL 模式会询问是否本次仅启动，且不会修改全局模式。
- **托盘结束游戏**：系统托盘右键菜单新增“结束当前进程”，可直接结束正在运行的 Minecraft 游戏进程。
- **启动完成提示**：游戏正常启动、DLL 注入成功或注入失败时，在屏幕右下角显示同款托盘提示，2 秒后自动消失。
- **档案列表滚动**：档案数量超过列表可视高度时才会显示右侧滑杆，支持鼠标滚轮上下切换和拖动滑杆。
- **统一细滑杆**：设置、运行日志与游戏档案使用同款右侧滑杆；内容未超出时自动隐藏，支持滚轮和拖动。
- **启动等待可视化配置**：设置界面可直接输入新启动游戏的初始化等待（0-60 秒），默认 10 秒，并支持一键重置。
- **首次运行自动建目录**：第一次打开时，在启动器所在目录创建与启动器同名的总文件夹 `STEVE CLIENT/`，其中包含：
  - `DLLs/`：放置需要注入的 DLL
  - `logs/`：运行日志
  - `config.ini`：配置文件和 DLL 启用状态
- **手动导入 DLL**：首次启动不会扫描或自动导入任何 DLL，请玩家自己通过“添加 DLL”或拖拽导入。
- **无 DLL 启动确认**：没有已启用的 DLL 时，点击启动会提示是否跳过 DLL、直接启动 Minecraft。
- **自动注入**：检测到游戏窗口后，按文件名顺序注入 `DLLs/` 中所有已启用的 DLL。
- **游戏已运行时直接注入**：如果 Minecraft 已经打开，点击启动按钮会直接注入当前进程，不会重复启动。
- **实时状态**：启动器每 2 秒检测一次游戏进程；游戏启动、退出后会自动刷新“运行中 / 未运行”状态。
- **日志查看**：运行日志支持鼠标滚轮与右侧滚动条上下翻看；只有停留在底部时才会自动跟随新日志。
- **后台注入**：注入只依赖游戏进程 PID，不要求启动器置顶；游戏窗口在前台时启动器会自动最小化，关闭窗口时也可以选择继续后台注入。
- **全局快捷键**：默认 `Ctrl+1` 直接注入已启用 DLL，`Ctrl+2` 按当前预设和启动模式直接启动游戏，`Ctrl+3` 直接结束当前游戏进程；三组快捷键默认关闭，可在设置中分别开启、重新录制或重置。通过快捷键启动或注入时会跳过启动等待和注入延迟。
- **DLL 管理**：启用/禁用、拖拽导入、右键移除到 `DLLs/.trash`、打开文件夹。
- **资源库**：按 **资源包 / 行为包 / 世界 / 模板** 四个分栏管理；自动扫描目标账号已有的内容，也可以添加 `.mcpack` / `.mcaddon` / `.mcworld` / `.mctemplate` / `.zip`，由启动器解包到正确的 `com.mojang` 子目录。
- **模板管理**：支持导入和管理世界模板（`.mctemplate`），自动读取 `manifest.json`、`texts/*.lang` 和 `world_icon.jpeg`，安装到 `world_templates`。
- **名称与图标**：包名读取 `manifest.json`（占位键会从 `texts/*.lang` 解析本地化名称）；资源包 / 行为包显示 `pack_icon`，世界显示 `world_icon` 缩略图。
- **跨账号 / 跨机器浏览**：切换账号查看不同账号的世界；还可以把其他机器或备份里的 `com.mojang` 作为只读扫描目录挂进来浏览。
- **多账号目录**：自动识别本机不同 Windows 账号下的 `com.mojang`，也区分正式版 / 预览版；每个账号的目录单独选择、互不干扰。
- **资源库缓存**：同一数据目录只在启动、导入、删除或手动刷新时全量扫描；切换页面直接使用内存缓存，图标按可见行异步加载，避免每次点击资源库都卡顿。
- **异步资源导入**：大型资源包 / 世界在后台解压与安装，显示实时进度和取消按钮；世界与模板在目标盘暂存后直接移动，减少二次复制。
- **深色界面**：自绘的深色 UI、圆角卡片、分层标题区域，减少 WinForms 闪烁。

---

## 系统要求

- Windows 10 / Windows 11，64 位
- Minecraft for Windows（Microsoft Store 正版），或在 **游戏档案** 中新增一个可用的自定义档案
- 默认以**标准权限**运行，不需要 UAC；如果游戏以管理员权限运行导致注入失败，可在设置里选择“以管理员身份重启”
- 需要 .NET Framework 4.8（Windows 10 1903+ / Windows 11 自带）

> 为支持从资源管理器直接拖入 DLL，启动器默认不申请管理员权限。管理员模式下 Windows 会阻止 Explorer 向高权限窗口拖放。

---

## 使用步骤

1. 将 `STEVE CLIENT 2.11.1.exe` 放到一个单独的文件夹中（不要直接放在 `C:\Windows` 等系统目录）。
2. 双击运行，允许管理员权限。
3. 首次运行会在启动器同目录创建 `STEVE CLIENT/` 总文件夹，里面包含 `DLLs`、`logs`、`config.ini`。
   - 启动器**不会**自动扫描或导入 DLL。
   - 请把 DLL 拖进启动器窗口，或点击 **DLL 模块 → 添加 DLL** 手动导入。
4. 在 **DLL 模块** 页面确认需要注入的 DLL 已启用（默认全部启用）。
5. 回到 **启动中心**，点击 **启动游戏**。
6. 启动器会：
   - 激活 Minecraft for Windows；
   - 等待游戏窗口出现；
   - 新启动的游戏先等待 `startupWarmupMs`（默认 10 秒，可在设置界面修改或重置）完成初始化，再等待注入延迟（默认 2.5 秒）；注入已运行的游戏时跳过预热；
   - 依次注入所有已启用的 DLL；
   - 显示每个模块的注入结果。
7. 游戏退出后，启动器会自动把状态更新为“未运行 / 等待启动”。

### 如果游戏已经打开

直接点击 **启动游戏**（游戏运行中时按钮显示为 **注入游戏**），启动器会连接当前 `Minecraft.Windows.exe` 进程并注入。

### 结束游戏

启动按钮右侧的 **结束游戏** 按钮会在游戏运行时启用。点击后需要确认，确认后会强制结束所有 `Minecraft.Windows.exe` 进程；未保存的世界进度可能丢失。

### 游戏档案

1. 打开左侧 **游戏档案**，列表默认包含 **Minecraft 官方版**（Microsoft Store 启动）。
2. 点击右上角 **新增档案**，在弹窗中填写档案名称，并选择该档案要启动的 `.exe` / `.lnk` / `.bat` / `.cmd`。
3. 在列表中选择档案，被选中的档案会显示“当前档案”标记。
4. 启动中心底部的 **启动档案** 卡片会显示当前档案；点击 **切换** 可直接选择其他档案，点击 **管理** 进入游戏档案页面。

官方档案固定存在、不能删除；自定义档案在列表中悬停后可以删除。档案的启动路径被移动或删除时，启动中心会提示路径不存在，启动时会要求先修复档案。

档案数量超过列表高度后，列表右侧会出现滑杆；可以直接用鼠标滚轮上下滚动，也可以拖动滑杆。档案较少时滑杆会自动隐藏。

**设置** 页面内容超出高度时同样使用右侧滑杆；**运行日志** 只在日志行数超过可视区域时显示滑杆，滚轮和拖动都能回看历史日志。

### 添加资源包 / 行为包 / 世界 / 模板

1. 打开 **资源库** 页面。列表会自动读取当前目标里已有的资源包、行为包、世界和模板，并用四个分栏分别显示数量、图标和缩略图。
2. 顶部“目标账号 / 数据目录”卡片会显示当前安装目标；点击 **切换** 可以选择本机的 Xbox 账号（按 XUID 区分）、正式版 / 预览版，或手动选择自定义目录。
3. 点击 **添加资源**，或把文件直接拖进窗口。支持 `.mcpack`、`.mcaddon`、`.mcworld`、`.mctemplate`、`.zip`。
4. 启动器会读取包内的 `manifest.json` / `level.dat`，自动判断类型后解包到：
   - 资源包 → 该版本的共享目录 `resource_packs`
   - 行为包（模组）→ 该版本的共享目录 `behavior_packs`
   - 世界 → 所选账号的 `minecraftWorlds`
   - 模板 → 共享目录 `world_templates`
5. 安装完成后重启游戏（或重新打开世界 / 资源包列表）即可看到。

部分 `.mcaddon` 会把资源包 / 行为包以 `.mcpack` 嵌套在压缩包内（例如 `behaviors.mcpack`、`resources.mcpack`），启动器会自动递归展开后再安装，不需要手动拆包。

包名优先使用 `manifest.json` 的 `header.name`；如果它是 `pack.name` 这类本地化占位键，会继续从 `texts/zh_CN.lang`、`texts/en_US.lang` 读取真正的名字。

如果资源在另一台机器或备份里：在 **切换** 菜单里选 **扫描其他机器目录…**，指向那边的 `com.mojang` 文件夹，就会以只读方式列出来；此时不能安装或移除，切回账号即可继续导入。

新版（GDK / Xbox 版）的实际布局是：

```
%APPDATA%\Minecraft Bedrock\
  Users\
    <XUID>\games\com.mojang\        ← 每个 Xbox 账号独立（世界在这里）
    Shared\games\com.mojang\        ← 资源包 / 行为包 / 模板共享（所有账号可用）
%APPDATA%\Minecraft Bedrock Preview\  ← 预览版同样结构
```

旧版 UWP 则使用 `%LOCALAPPDATA%\Packages\<包名>\LocalState\games\com.mojang`，启动器会自动识别并照常安装。

说明：

- 账号按 XUID 区分，显示名优先读取该账号的 `mp_username`；切换账号只影响世界的安装位置，不会改动其他账号。
- 资源包 / 行为包 / 模板按游戏自身的规则放在共享目录，因此**所有账号都能看到**；移除时也会对所有账号生效。
- 导入时如果资源包 / 行为包的 UUID、模板的 UUID 与现有内容重复，或世界同名，会弹窗询问是否覆盖；选择“覆盖”会把旧内容移到 `.steve-client-trash`，拒绝则请先删除现有资源再导入。
- 正式版与预览版的数据目录是分开的，启动器会分别列出。
- 同一个 UUID 的包再次安装会视为更新，旧版本移动到 `.steve-client-trash`。
- 世界重名时会自动追加序号，避免覆盖已有存档。
- 模板会解包到 `world_templates/<模板名>`；模板的显示名来自 `manifest.json` / `texts/*.lang`，缩略图来自 `world_icon.jpeg`。
- 移除资源同样只是移动到 `.steve-client-trash`，不会直接删除。

---

## 目录结构

```
STEVE CLIENT 2.11.1.exe
STEVE CLIENT/            首次运行后生成的总文件夹
  config.ini
  DLLs/
    你的模块.dll
    把 DLL 放在这里.txt
    .trash/              移除的 DLL 会移到这里
  logs/
    steve-client-YYYYMMDD.log
```

资源不会被复制到启动器目录，而是直接解包到对应账号的 `com.mojang` 下。

---

## 配置说明

`config.ini` 会自动生成，通常不需要手动修改：

```ini
[general]
firstRunCompleted=true
injectDelayMs=2500
startupWarmupMs=10000
minimizeAfterInject=true
closeAfterInject=false
verifyArchitecture=true
hideToTrayOnClose=false
closeBehaviorAsked=false
injectHotkey=Ctrl+1
launchHotkey=Ctrl+2
closeHotkey=Ctrl+3
enableInjectHotkey=false
enableLaunchHotkey=false
enableCloseHotkey=false
launchWithDlls=true

[dlls]
Latite.dll=true
BetterRenderDragon.dll=true

[resources]
dataDir=C:\Users\你\AppData\Roaming\Minecraft Bedrock\Users\11906446262327495435\games\com.mojang
custom=false

[profiles]
selected=official
count=2
p0.id=official
p0.name=Minecraft 官方版
p0.path=
p1.id=1a2b3c4d5e6f
p1.name=我的 1.21 档案
p1.path=C:\Games\Minecraft\Minecraft.Windows.exe
```

- `injectDelayMs`：游戏窗口出现后等待多久再注入，默认 2500 毫秒。
- `startupWarmupMs`：新启动游戏时的初始化等待，默认 10000 毫秒（10 秒），可在设置界面直接输入 0-60 秒或点击重置；注入后游戏未响应可调大，游戏加载快可调小。注入已运行的游戏时不会使用这个值。
- `minimizeAfterInject`：注入完成后是否最小化启动器。
- `closeAfterInject`：注入完成后是否退出启动器。
- `verifyArchitecture`：是否在启动前拦截明显不是 64 位的 DLL。
- `hideToTrayOnClose`：点击关闭按钮时是否隐藏到系统托盘；`closeBehaviorAsked` 记录是否已经询问过关闭方式。
- `injectHotkey`：直接注入快捷键，默认 `Ctrl+1`；设置界面可重新录制或重置。
- `launchHotkey`：直接启动快捷键，默认 `Ctrl+2`，按当前预设和启动模式启动。
- `closeHotkey`：直接关闭游戏快捷键，默认 `Ctrl+3`，直接结束当前游戏进程。
- `enableInjectHotkey` / `enableLaunchHotkey` / `enableCloseHotkey`：三组快捷键的启用状态，默认均为 `false`。
- `launchWithDlls`：全局启动模式，`true` 为带 DLL 启动，`false` 为仅启动游戏；托盘直接启动沿用该设置。
- `[profiles] selected`：当前使用的游戏档案 ID；`p0` 固定为官方档案，`p1` 起为自定义档案。旧版本的 `launchPath` 会自动迁移成一个“自定义启动”档案。
- `[dlls]`：每个 DLL 的启用状态。
- `[resources] dataDir`：上次选择的游戏数据目录；启动器启动时会优先选中它，不存在时自动回退到本机可用的账号目录。
- `[resources] custom`：`dataDir` 是否为手动指定的自定义目录；手动选择目录后置为 `true`。
- `[resources] scanDir`：外部扫描目录（其他机器 / 备份的 `com.mojang`），只读。

也可以在 **设置** 页面直接调整这些选项。

---

## 常见问题

### 提示“未检测到 Minecraft”

请确认安装的是 **Minecraft for Windows**（Microsoft Store 的基岩版），而不是 Java 版或第三方启动器版本。安装后重新打开启动器。

### 注入失败 / 拒绝访问

- 右键 `STEVE CLIENT 2.11.1.exe` → **以管理员身份运行**。
- 管理员模式下 Windows 会阻止从 Explorer 拖放 DLL，此时请用“添加 DLL”按钮导入。
- 关闭杀毒软件对注入行为的拦截，或将启动器加入白名单。
- 确认 DLL 是 **64 位**，并且与当前游戏版本兼容。
- 某些 DLL 需要游戏进入主菜单后才能加载；可以在设置中把注入延迟调到 4 秒或 6 秒。

### DLL 加载失败

常见原因：

- DLL 是 32 位；
- DLL 缺少同目录依赖；
- DLL 与游戏版本不匹配；
- DLL 被安全软件拦截；
- 游戏更新后客户端 DLL 尚未更新。

具体错误会写进 `logs` 目录中的日志。

### 游戏更新后

Minecraft 更新可能改变内部结构，部分客户端 DLL 需要同步更新。启动器本身通常不需要更新。

### 杀毒软件报毒

进程注入类工具经常会被启发式规则误报。本工具只做本地 DLL 加载，不上传任何数据。请自行判断是否信任；不要注入来源不明的 DLL。

---

## 安全说明

- 本工具不会下载、上传或替换任何 DLL。
- 注入的 DLL 拥有与游戏进程相同的权限，可能读写你的游戏数据。请只使用可信模块。
- 使用第三方模块可能导致游戏崩溃、存档损坏或账号风险，责任由使用者自行承担。
- Minecraft 是 Microsoft / Mojang 的商标，本项目与官方无关。

---

## 从源码构建

需要：

- Windows 10/11 x64
- .NET Framework 4.8（`csc.exe`）
- Windows SDK 的 `rc.exe`（可选，用于图标和版本资源）

运行：

```powershell
powershell -ExecutionPolicy Bypass -File .\build.ps1
```

输出（文件名均包含版本号）：

- `dist/STEVE CLIENT 2.11.1.exe`
- `dist/STEVE CLIENT 2.11.1.zip`
- `dist/README 2.11.1.md`

测试构建（不要求管理员权限）：

```powershell
powershell -ExecutionPolicy Bypass -File .\build.ps1 -Test -NoZip
```

源码目录：

```
src/             C# WinForms 源码
assets/          图标与图标生成脚本
app.manifest     管理员权限、DPI 感知
app.rc           图标、版本信息、清单资源
build.ps1        构建脚本
```
