# cc-plugins

luoyjchn 的个人 Claude Code 插件市场（marketplace），通过 git submodule 聚合多个插件。

## 插件列表

| 插件 | 版本 | 说明 | 独立仓库 |
| --- | --- | --- | --- |
| file-scope-guard | 0.2.0 | 跨平台删除文件作用域防护：默认仅允许在项目根目录内删除，可配置 allow/deny/ask 规则 | [luoyjchn/file-scope-guard](https://github.com/luoyjchn/file-scope-guard) |
| jetbrains-mcp-bridge | 0.4.1 | Bridge JetBrains IDE features to Claude Code via MCP | [luoyjchn/jetbrains-mcp-bridge](https://github.com/luoyjchn/jetbrains-mcp-bridge) |

## 安装

在 Claude Code 中执行：

```
/plugin marketplace add luoyjchn/cc-plugins
/plugin install file-scope-guard
/plugin install jetbrains-mcp-bridge
```

> 注意：`file-scope-guard` 独立仓库为 **private**，若拉取失败需在本机配置对该仓库的 git/gh 访问权限。

## 结构

```
cc-plugins/
├── .claude-plugin/
│   └── marketplace.json     # 市场清单
├── plugins/
│   ├── file-scope-guard/    # submodule
│   └── jetbrains-mcp-bridge/  # submodule
└── README.md
```

## 新增插件

1. 克隆独立插件仓库：`git submodule add <url> plugins/<name>`
2. 在 `.claude-plugin/marketplace.json` 的 `plugins` 数组中添加条目（`source` 指向 `./plugins/<name>`）
3. 提交并推送

## 更新插件

```bash
git submodule update --remote
git add plugins/ .gitmodules
git commit -m "chore: bump plugin submodules"
git push
```
