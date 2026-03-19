# CC Config - Claude Code 配置管理工具

一个使用 TypeScript 和 Bun 构建的命令行工具，用于管理 Claude Code 的多个配置方案，支持快速切换不同的 API 提供商和模型映射。

## ✨ 功能特性

- ✅ 添加、编辑、删除、切换配置方案
- ✅ 命令行操作，简洁高效
- ✅ 支持配置多个 API 提供商（阿里云、OpenAI、Anthropic 等）
- ✅ 自定义模型映射（Opus/Sonnet/Haiku）
- ✅ 交互式输入 + 命令行参数双模式
- ✅ 配置预览功能
- ✅ 配置立即生效
- ✅ **自动备份初始配置**
- ✅ **恢复初始设置功能**
- ✅ **清理所有配置功能**
- ✅ **一键解锁 Claude Code 隐藏超能力**
  - 循环执行模式 (/loop)
  - 顺便执行模式 (/btw)
  - 1M 上下文窗口 (/context1m)
  - MCP 搜索增强 (/MCPSearch)
- ✅ 支持编译为独立可执行文件
- ✅ 完整的错误处理和输入验证
- ✅ API Key 安全显示

## 📦 安装

### 方式 1: npm (推荐)

```bash
# 全局安装
npm install -g @0x86/cc-config

# 运行
cc-config
```

### 方式 2: Bun

```bash
# 全局安装
bun install -g @0x86/cc-config

# 运行
cc-config
```

### 方式 3: 从源码安装

```bash
# 克隆仓库
git clone https://github.com/xyhuangjia/claude-config-cli.git
cd claude-config-cli

# 安装依赖
bun install

# 运行
bun start
```

### 方式 4: 编译为可执行文件

```bash
# 编译
bun run build

# 运行
./cc-config
```

### 方式 5: 下载可执行文件

```bash
# macOS/Linux
curl -L https://raw.githubusercontent.com/xyhuangjia/claude-config-cli/main/install.sh | bash

# 或手动下载
# 访问 https://github.com/xyhuangjia/claude-config-cli/releases
```

## 🚀 使用方法

### 查看帮助

```bash
cc-config help
```

### 命令列表

| 命令 | 简写 | 别名 | 说明 |
|------|------|------|------|
| `list` | `ls`, `l` | - | 列出所有配置 |
| `show` | `s` | `current` | 显示当前配置 |
| `switch` | `sw` | `use` | 切换到指定配置 |
| `add` | `a` | `new`, `create` | 添加新配置 |
| `edit` | `e` | `update` | 编辑配置 |
| `delete` | `d`, `rm` | `remove` | 删除配置 |
| `restore` | `r` | - | 恢复初始设置 |
| `clean` | `c` | `uninstall` | 清理所有配置文件 |
| `enable` | `en` | - | 启用隐藏功能 |
| `disable` | `dis` | - | 禁用隐藏功能 |
| `status` | `st` | - | 查看功能状态 |
| `version` | `-v`, `--version` | - | 查看版本号 |

### 基本操作

#### 1. 列出所有配置

```bash
cc-config list
# 或使用简写
cc-config ls
cc-config l
```

输出示例：
```
配置列表

⭐ 1. aliyun
      API Key: sk-sp-ee...15a1
      Base URL: https://coding.dashscope.aliyuncs.com/apps/anthropic
   2. openai
      API Key: sk-proj...abcd
      Base URL: https://api.openai.com/v1
```

#### 2. 查看当前配置

```bash
cc-config show
# 或使用简写
cc-config s
```

#### 3. 切换配置

```bash
cc-config switch aliyun
# 或使用简写
cc-config sw aliyun
```

#### 4. 添加新配置

交互式添加（会提示输入各项配置）：

```bash
cc-config add openai
# 或使用简写
cc-config a openai
```

或通过参数直接添加：

```bash
cc-config a openai \
  --key sk-xxx \
  --url https://api.openai.com/v1 \
  --opus gpt-4 \
  --sonnet gpt-4-turbo \
  --haiku gpt-3.5-turbo
```

#### 5. 编辑配置

交互式编辑：

```bash
cc-config edit aliyun
# 或使用简写
cc-config e aliyun
```

或通过参数直接修改：

```bash
cc-config e aliyun --key sk-new-key --url https://new-url.com
```

#### 6. 删除配置

```bash
cc-config delete openai
# 或使用简写
cc-config d openai
cc-config rm openai
```

#### 7. 恢复初始设置

```bash
cc-config restore
# 或使用简写
cc-config r
```

> **说明**：工具会在首次运行时自动备份当前的 Claude Code 配置，备份文件保存在 `~/.claude-config-manager/original_settings_backup.json`

#### 8. 清理所有配置

```bash
cc-config clean
# 或使用简写
cc-config c
```

### 🔓 隐藏功能管理

Claude Code 有一些隐藏的超能力，可以通过 cc-config 轻松开启：

#### 查看所有隐藏功能状态

```bash
cc-config status
# 或查看单个功能
cc-config status loop
```

#### 启用隐藏功能

```bash
# 循环执行模式 - 让 Claude 重复执行任务
cc-config enable loop

# 顺便执行模式 - 在当前任务完成后顺便执行另一个任务
cc-config enable btw

# 1M 上下文窗口 - 启用超长上下文模式
cc-config enable context1m

# MCP 搜索增强 - 使用 MCP 进行高级代码搜索
cc-config enable mcp

# 自定义快捷键
cc-config enable keybindings
```

#### 禁用隐藏功能

```bash
cc-config disable loop
cc-config disable btw
cc-config disable context1m
cc-config disable mcp
cc-config disable keybindings
```

#### 隐藏功能说明

| 功能 | 命令 | 说明 |
|------|------|------|
| 循环执行模式 | `/loop` | 让 Claude 重复执行某个任务，直到完成或达到指定次数 |
| 顺便执行模式 | `/btw` | 在当前任务完成后，顺便执行另一个任务 |
| 自定义快捷键 | `/keybindings` | 查看和配置 Claude Code 的键盘快捷键（内置命令） |
| 1M 上下文 | `/context1m` | 启用超长上下文模式，支持处理更大的代码库 |
| MCP 搜索 | `/MCPSearch` | 使用 MCP (Model Context Protocol) 进行高级代码搜索 |

> **提示**: 开启功能后，在 Claude Code 对话框中直接输入这些命令即可使用

输出示例：
```
配置列表

⭐ 1. aliyun
      API Key: sk-sp-ee...15a1
      Base URL: https://coding.dashscope.aliyuncs.com/apps/anthropic
   2. openai
      API Key: sk-proj...abcd
      Base URL: https://api.openai.com/v1
```

#### 2. 查看当前配置

```bash
cc-config show
```

#### 3. 切换配置

```bash
cc-config switch aliyun
```

#### 4. 添加新配置

交互式添加（会提示输入各项配置）：

```bash
cc-config add openai
```

或通过参数直接添加：

```bash
cc-config add openai \
  --key sk-xxx \
  --url https://api.openai.com/v1 \
  --opus gpt-4 \
  --sonnet gpt-4-turbo \
  --haiku gpt-3.5-turbo
```

#### 5. 编辑配置

交互式编辑：

```bash
cc-config edit aliyun
```

或通过参数直接修改：

```bash
cc-config edit aliyun --key sk-new-key --url https://new-url.com
```

#### 6. 删除配置

```bash
cc-config delete openai
```

#### 7. 恢复初始设置

```bash
cc-config restore
```

> **说明**：工具会在首次运行时自动备份当前的 Claude Code 配置，备份文件保存在 `~/.claude/original_settings_backup.json`

#### 8. 清理所有配置

```bash
cc-config clean
```

此命令会删除所有配置文件和备份，需要输入 "DELETE" 确认。

### 配置选项参数

添加或编辑配置时可使用以下参数：

| 参数 | 别名 | 说明 |
|------|------|------|
| `--key` | `-k` | API Key (ANTHROPIC_AUTH_TOKEN) |
| `--url` | `-u` | Base URL (ANTHROPIC_BASE_URL) |
| `--opus` | `-o` | Opus 模型 |
| `--sonnet` | `-s` | Sonnet 模型 |
| `--haiku` | `-H` | Haiku 模型 |

## 📁 配置存储

配置文件分布在两个目录：

### Claude Code 配置目录 (~/.claude/)
```
~/.claude/
└── settings.json                    # 当前使用的配置（Claude Code 读取此文件）
```

### 配置管理工具目录 (~/.claude-config-manager/)
```
~/.claude-config-manager/
├── profiles/                        # 所有配置方案
│   ├── aliyun.json
│   ├── openai.json
│   └── anthropic.json
├── current_profile.txt              # 记录当前配置名称
└── original_settings_backup.json    # 初始配置备份（首次运行时自动创建）
```

## 📝 配置示例

### 阿里云配置

```json
{
  "name": "阿里云",
  "env": {
    "ANTHROPIC_AUTH_TOKEN": "sk-xxx",
    "ANTHROPIC_BASE_URL": "https://coding.dashscope.aliyuncs.com/apps/anthropic",
    "ANTHROPIC_DEFAULT_OPUS_MODEL": "glm-5",
    "ANTHROPIC_DEFAULT_SONNET_MODEL": "qwen3.5-plus",
    "ANTHROPIC_DEFAULT_HAIKU_MODEL": "MiniMax-M2.5"
  }
}
```

### OpenAI 配置

```json
{
  "name": "OpenAI",
  "env": {
    "ANTHROPIC_AUTH_TOKEN": "sk-xxx",
    "ANTHROPIC_BASE_URL": "https://api.openai.com/v1",
    "ANTHROPIC_DEFAULT_OPUS_MODEL": "gpt-4",
    "ANTHROPIC_DEFAULT_SONNET_MODEL": "gpt-4-turbo",
    "ANTHROPIC_DEFAULT_HAIKU_MODEL": "gpt-3.5-turbo"
  }
}
```

### Anthropic 官方配置

```json
{
  "name": "Anthropic",
  "env": {
    "ANTHROPIC_AUTH_TOKEN": "sk-ant-xxx",
    "ANTHROPIC_BASE_URL": "https://api.anthropic.com",
    "ANTHROPIC_DEFAULT_OPUS_MODEL": "claude-3-opus-20240229",
    "ANTHROPIC_DEFAULT_SONNET_MODEL": "claude-3-sonnet-20240229",
    "ANTHROPIC_DEFAULT_HAIKU_MODEL": "claude-3-haiku-20240307"
  }
}
```

## 🔧 技术栈

- **Runtime**: [Bun](https://bun.sh/) - 快速的 JavaScript 运行时
- **Language**: TypeScript
- **CLI**: Node.js readline - 内置命令行交互
- **Colors**: [picocolors](https://github.com/alexeyraspopov/picocolors) - 终端颜色库

## 🎯 快速开始

```bash
# 1. 安装工具
npm install -g @0x86/cc-config

# 2. 添加第一个配置
cc-config add aliyun

# 3. 切换到新配置
cc-config switch aliyun

# 4. 查看当前配置
cc-config show

# 5. 开始使用 Claude Code
```

## 🔒 安全特性

- **API Key 安全显示**: 只显示前8位和后4位，中间用 `...` 代替
- **输入验证**: 验证配置名称、API Key 格式等
- **错误处理**: 完整的 try-catch 保护，防止程序崩溃
- **文件权限**: 建议设置 `chmod 700 ~/.claude` 和 `chmod 600 ~/.claude/*`

## 📌 注意事项

1. **安全性**：API Key 以明文存储在配置文件中，请确保配置目录权限设置正确
2. **当前配置保护**：删除当前配置时需要二次确认
3. **配置立即生效**：切换配置后，Claude Code 会立即使用新配置，无需重启
4. **保留其他设置**：切换配置时，只更新 `env` 相关字段，其他设置保持不变
5. **配置合并**：新配置只会覆盖非空值，保留原有的其他环境变量

## 🐛 故障排除

### 找不到 bun 命令

```bash
# 安装 Bun
curl -fsSL https://bun.sh/install | bash
```

### 配置不生效

1. 检查 `~/.claude/settings.json` 文件是否正确更新
2. 确保配置文件格式正确（有效的 JSON）
3. 重启 Claude Code（通常不需要，但如果遇到问题可以尝试）

### 权限问题

```bash
# 确保配置目录权限正确
chmod 700 ~/.claude
chmod 600 ~/.claude/settings.json
chmod 600 ~/.claude/profiles/*.json
```

### 配置文件损坏

如果配置文件损坏，工具会自动使用默认配置，并提示错误信息。你可以：
1. 删除损坏的配置文件
2. 重新添加配置

## 🗑️ 卸载

### 卸载工具

#### 方式 1: npm 全局安装卸载

```bash
npm uninstall -g @0x86/cc-config
```

#### 方式 2: Bun 全局安装卸载

```bash
bun uninstall -g @0x86/cc-config
```

#### 方式 3: 从源码安装卸载

```bash
# 删除项目目录
rm -rf claude-config-cli

# 如果创建了可执行文件
rm claude-config
```

### 清理配置文件

如果你想同时清理所有配置文件（可选）：

```bash
# 使用工具内置的清理功能
cc-config
# 选择 "🗑️  卸载/清理配置"

# 或手动删除
rm -rf ~/.claude/profiles
rm -f ~/.claude/settings.json
rm -f ~/.claude/current_profile.txt
rm -f ~/.claude/original_settings_backup.json
```

> **注意**：清理配置文件会删除所有保存的 API Keys 和配置方案，请谨慎操作！

## 📄 许可证

MIT

## 🔗 相关链接

- [快速开始](QUICKSTART.md) - 5分钟上手指南
- [更新日志](CHANGELOG.md) - 版本更新记录
- [发布指南](PUBLISHING.md) - 如何发布到 npm/GitHub
- [配置示例](example-profiles.json) - 常见配置示例

## 🤝 贡献

欢迎提交 Issue 和 Pull Request！

### 贡献方式
1. Fork 本仓库
2. 创建特性分支 (`git checkout -b feature/AmazingFeature`)
3. 提交更改 (`git commit -m 'Add some AmazingFeature'`)
4. 推送到分支 (`git push origin feature/AmazingFeature`)
5. 创建 Pull Request

## 📊 开发过程

本项目使用 AI Team 模式开发：
- **规划**: GLM-5 (Research Agent)
- **编码**: GLM-4.7 (Implement Agent)
- **检查**: GLM-5 (Check Agent)

## 🔍 代码质量

- ✅ TypeScript strict 模式
- ✅ 完整的错误处理
- ✅ 输入验证
- ✅ 类型安全
- ✅ 最佳实践

## 📈 项目统计

![GitHub stars](https://img.shields.io/github/stars/xyhuangjia/claude-config-cli?style=social)
![npm downloads](https://img.shields.io/npm/dt/@0x86/cc-config)
![GitHub license](https://img.shields.io/github/license/xyhuangjia/claude-config-cli)
![GitHub release](https://img.shields.io/github/v/release/xyhuangjia/claude-config-cli)

## ⭐ Star History

如果这个工具对你有帮助，请给个 Star ⭐️

## 💖 支持项目

如果你觉得这个工具有用，可以：
- ⭐ 给项目点星
- 🐛 报告 Bug
- 💡 提出新功能建议
- 📖 改进文档
- 🔀 提交 Pull Request
