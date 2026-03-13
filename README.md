# dotfiles

个人开发环境配置文件集合，面向 Windows 平台，涵盖终端、编辑器及常用 CLI 工具的统一管理与版本追踪。

---

## 目录结构

每个软件独立一个子目录，目录内包含配置文件及对应的 `README.md`（说明安装步骤与配置项）。

```
dotfiles/
├── windows-terminal/   # Windows Terminal 配置
└── ...                 # 后续软件按需添加
```

| 目录 | 软件 | 平台 | 说明 |
|------|------|------|------|
| `windows-terminal/` | Windows Terminal | Windows | 多窗格 CLI 工作流，Git Bash 默认 Shell，Catppuccin Mocha 主题 |

---

## 使用方式

各软件的前置依赖与复制命令详见对应子目录的 `README.md`。

---

## 贡献新配置

1. 在仓库根目录新建子目录，命名规范：**小写字母，单词间用连字符**（如 `vs-code`、`git`）
2. 将配置文件放入该目录
3. 在子目录内创建 `README.md`，说明：软件简介、前置依赖、安装步骤、需按机器调整的内容
4. 在本文件的目录表格中补充一行

---

## License

MIT
