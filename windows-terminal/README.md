# Windows Terminal — Vibe Coding 配置

面向 CLI 开发的 Windows Terminal 全局设置，针对多窗格工作流优化。

## 配置内容

### 外观
| 项目 | 值 |
|------|----|
| 默认 Shell | Git Bash |
| 字体 | Cascadia Code 13px，启用连字 |
| 配色（亮色） | GitHub Light（跟随系统自动切换） |
| 配色（暗色） | GitHub Dark（跟随系统自动切换） |
| 窗口主题 | 跟随系统亮/暗模式（`theme: system`） |
| 背景 | Acrylic 磨砂透明（96%） |
| 光标 | Bar（竖线，更精准） |
| 滚动条 | 隐藏（更简洁） |

### 快捷键
| 操作 | 快捷键 |
|------|--------|
| 垂直分割（左\|右，保持当前路径） | `Ctrl+Shift+D` |
| 水平分割（上/下，保持当前路径） | `Ctrl+Shift+E` |
| 在窗格间移动焦点 | `Alt+方向键` |
| 调整窗格大小 | `Alt+Shift+方向键` |
| 关闭当前窗格 | `Ctrl+Shift+W` |
| 新 Tab | `Ctrl+T` |
| 切换 Tab | `Ctrl+Tab` / `Ctrl+Shift+Tab` |
| 复制 | `Ctrl+C` |
| 粘贴 | `Ctrl+V` |
| 搜索 | `Ctrl+Shift+F` |

### 可见 Profile
- Git Bash（默认）
- Windows PowerShell
- Ubuntu-24.04（WSL，如已安装）
- Ubuntu-22.04（WSL，如已安装）
- 自定义 SSH Profile（根据需要添加）

VS Developer Prompt 等噪音 Profile 全部隐藏。

---

## 在新电脑上安装

### 第一步：安装前置依赖

```powershell
# 1. Windows Terminal（Microsoft Store 或 winget）
winget install Microsoft.WindowsTerminal

# 2. Git for Windows（提供 Git Bash）
winget install Git.Git

# 3. Cascadia Code 字体（Windows Terminal 通常自带，手动安装更保险）
winget install Microsoft.CascadiaCode
```

> 不再依赖 Nerd Font 变体（`Cascadia Code NF`），使用官方 `Cascadia Code` 即可。

### 第二步：复制配置文件

**方式 A：手动复制（推荐）**

1. 打开 Windows Terminal，按 `Ctrl+,` 打开设置
2. 左下角点击「打开 JSON 文件」
3. 用本目录的 `settings.json` 内容完全替换

**方式 B：PowerShell 命令一键复制**

```powershell
# 找到 settings.json 路径
$wtPath = "$env:LOCALAPPDATA\Packages\Microsoft.WindowsTerminal_8wekyb3d8bbwe\LocalState\settings.json"

# 从本 dotfiles 复制（修改源路径为实际位置）
Copy-Item "D:\Repos\YanZhiwei\dotfiles\windows-terminal\settings.json" $wtPath -Force
```

**方式 C：如果 Windows Terminal 装在非 Store 路径**

```powershell
$wtPath = "$env:LOCALAPPDATA\Microsoft\Windows Terminal\settings.json"
Copy-Item "D:\Repos\YanZhiwei\dotfiles\windows-terminal\settings.json" $wtPath -Force
```

### 第三步：按需调整

新电脑上打开 settings.json，**删除或修改**以下机器特定内容：

- `novahub` SSH profile（改为你的服务器地址，或删除）
- WSL Ubuntu profile（根据实际安装的版本保留）
- VS Developer Prompt（如有安装 VS，按需显示）

### 验证

重启 Windows Terminal，确认：
- [ ] 默认打开 Git Bash
- [ ] Git Bash 启动无报错（无 starship 相关错误）
- [ ] 亮色模式下配色为 GitHub Light，暗色模式下为 GitHub Dark
- [ ] 切换 Windows 系统主题后，Terminal 配色自动跟随
- [ ] `Ctrl+Shift+D` 分割窗格后路径与当前一致
- [ ] `Alt+方向键` 可以在窗格间跳转

---

## 文件说明

```
windows-terminal/
  settings.json   — 通用配置（已移除机器特定 profile）
  README.md       — 本文件
```

本机完整配置（含所有 VS Profile 的 hidden 条目）存放在：
`%LOCALAPPDATA%\Packages\Microsoft.WindowsTerminal_8wekyb3d8bbwe\LocalState\settings.json`
