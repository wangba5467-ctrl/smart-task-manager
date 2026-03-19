# 智能任务管理器 (Smart Task Manager) v2.0

**任务门卫 - 快速判断任务类型并自动分发**

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![OpenClaw](https://img.shields.io/badge/OpenClaw-%3E%3D2026.3.0-blue.svg)](https://openclaw.ai)
[![Version](https://img.shields.io/badge/Version-2.0.0-green.svg)](https://github.com/wangba5467-ctrl/smart-task-manager)

---

## 🎯 核心功能

### 什么是"任务门卫"？

简单说：**帮你快速判断任务类型，然后分发到对应的处理方式**

```
用户任务
    ↓
门卫快速判断
    ├─ 简单任务 → 自己搞定（查文件、计算）
    └─ 复杂任务 → 指路给流程文档
```

---

## ⚡ 快速通道

**简单任务直接执行，不查流程文档，提速 10-20 倍**

| 类型 | 示例 | 响应时间 |
|------|------|---------|
| 查文件 | "找 agent.md" | ~2 秒 |
| 查文档 | "Python 版本" | ~1 秒 |
| 简单计算 | "1024 * 1024" | ~1 秒 |
| 小生成 | "写个快速排序" | ~10 秒 |

---

## 📋 标准流程

**复杂任务引导 AI 查流程文档，保证质量**

| 任务类型 | 触发词 | 流程文档位置 |
|---------|--------|-------------|
| 公众号写作 | 写文章、公众号 | `~/.openclaw/workspace/公众号写作流程.md` |
| 代码开发 | 开发功能 | （待创建） |
| 数据分析 | 分析数据 | （待创建） |

---

## 🚀 快速开始

### 安装

```bash
# 1. 复制到 OpenClaw skills 目录
cp -r smart-task-manager ~/.openclaw/skills/

# 2. 运行安装脚本（创建配置文件）
cd ~/.openclaw/skills/smart-task-manager/bin
node setup.js

# 3. 重启网关
openclaw gateway restart

# 4. 开始新对话
/new
```

### 使用

**安装后直接使用，无需额外操作：**

```
你好
帮我找 agent.md        → 快速通道，秒级响应
帮我写篇文章           → 标准流程，引导查文档
记住：代码必须加注释    → 自动写入记忆
```

---

## 🧠 记忆管理

### 自动记忆写入

**触发条件：**
- 用户说"记住"
- 用户表达要求/偏好
- 用户纠正错误

**示例：**
```
你：记住：代码必须加注释
AI：✅ 已记住
```

### 自动记忆检索

**每次对话开始时自动检索相关记忆**

---

## 🛠️ 工作原理

### 门卫模式

```
用户下达任务
    ↓
⚡ 快速通道检查
    ├─ 是（查文件/计算/小生成）
    │   └─ 🚀 直接执行（秒级）
    │
    └─ 否（复杂任务）
        └─ 📋 标准流程
            ↓
        🧠 记忆检索
            ↓
        📖 读取流程文档
            ↓
        ✅ 按流程执行
```

---

## 📊 性能对比

| 场景 | 不用 Skill | 用 Skill | 提升 |
|------|-----------|---------|------|
| 查文件 | 查流程文档 + 执行 | 直接执行 | **15x** |
| 简单计算 | 查流程文档 + 执行 | 直接计算 | **20x** |
| 写文章 | 可能忘记查文档 | 自动引导查文档 | 质量提升 |

---

## 📁 项目结构

```
smart-task-manager/
├── skill.md              # 核心逻辑（门卫模式）
├── 任务类型映射表.md       # 任务到流程的映射
├── skill.json            # Skill 配置
├── package.json          # npm 包配置
├── README.md             # 本文件
├── bin/
│   ├── setup.js          # 安装脚本（创建配置文件）
│   └── install.sh        # Shell 安装脚本
└── LICENSE               # MIT 许可证
```

---

## 🔄 v2.0 更新

### 简化改造

**从"复杂系统"简化为"任务门卫"：**

| v1.0 | v2.0 |
|------|------|
| 包含详细流程 | 只保留判断逻辑 |
| 重复现有文档 | 指向现有流程文档 |
| 600+ 行 skill.md | 180 行 skill.md |

**核心变化：**
- ✅ 简化为"门卫模式"
- ✅ 快速通道直接执行
- ✅ 标准流程指向现有文档
- ✅ 不重复造轮

---

## 📝 配置文件

安装后自动创建：

| 文件 | 位置 | 说明 |
|------|------|------|
| 任务类型映射表.md | `~/.openclaw/workspace/` | 定义任务到流程的映射 |

---

## 💡 最佳实践

### 1. 明确任务描述

```
✅ 帮我找 agent.md 文件
❌ 找文件
```

### 2. 复杂任务允许走流程

```
✅ 好的，按流程执行
❌ 别走流程了（复杂任务必须走流程）
```

### 3. 明确说"记住"

```
✅ 记住：代码必须加注释
❌ 代码要加注释
```

---

## 🛠️ 故障排查

### Skill 不触发

```bash
# 检查 skill.json
cat ~/.openclaw/skills/smart-task-manager/skill.json

# 重启网关
openclaw gateway restart
```

### 找不到流程文档

```bash
# 检查 workspace 目录
ls ~/.openclaw/workspace/

# 确保流程文档存在
ls ~/.openclaw/workspace/公众号写作流程.md
```

---

## 📦 依赖项

- **必需：** OpenClaw >= 2026.3.0
- **可选：** 现有流程文档（公众号写作流程.md 等）

---

## 🤝 贡献

欢迎贡献！

1. Fork 项目
2. 创建功能分支
3. 提交 Pull Request

---

## 📄 许可证

MIT License

---

## 📞 支持

- GitHub Issues: https://github.com/wangba5467-ctrl/smart-task-manager/issues
- OpenClaw Community

---

*智能任务管理器 v2.0 - 门卫模式*
*最后更新：2026-03-19*
*作者：Claude + 程哥*
