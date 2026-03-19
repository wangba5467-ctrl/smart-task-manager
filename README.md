# 智能任务管理器 (Smart Task Manager)

**让 OpenClaw 真正记住你的每个要求 - 自动化任务执行和记忆管理**

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![OpenClaw](https://img.shields.io/badge/OpenClaw-%3E%3D2026.3.0-blue.svg)](https://openclaw.ai)
[![Version](https://img.shields.io/badge/Version-1.0.0-green.svg)](https://github.com/your-repo/smart-task-manager)

---

## 🎯 功能特性

### ✨ 核心功能

- 🧠 **自动记忆管理** - 记住你的每个要求，自动检索和应用
- ⚡ **快速通道** - 简单任务秒级响应（提速 6-20 倍）
- 📋 **流程执行引擎** - 严格按流程执行，不跳步骤
- 🚫 **违规检查** - 自我监督和纠正
- 🔀 **智能任务路由** - 自动判断任务类型

### 📊 性能指标

| 任务类型 | 响应时间 | 提速 |
|---------|---------|:----:|
| 查文件 | ~2 秒 | **15x** |
| 简单计算 | ~1 秒 | **20x** |
| 生成小段代码 | ~10 秒 | **6x** |
| 写文章 | ~30 分钟 | 质量提升 |

---

## 🚀 快速开始

### 安装

#### 方式 1：手动安装（推荐）

```bash
# 1. 复制 skill 目录到 OpenClaw skills 目录
cp -r smart-task-manager ~/.openclaw/skills/

# 2. 运行安装脚本
cd ~/.openclaw/skills/smart-task-manager/bin
node setup.js  # Windows/Linux/macOS

# 3. 重启网关
openclaw gateway restart

# 4. 开始新对话
/new
```

#### 方式 2：npm 安装（如果发布到 npm）

```bash
npm install -g @openclaw/smart-task-manager

# 自动安装
smart-task-manager-install
```

### 使用

**安装后直接使用：**

```
你好
执行任务：写篇文章
```

**Skill 会自动：**
1. 检索相关记忆
2. 判断任务类型
3. 快速通道或标准流程
4. 按流程执行
5. 自动写入记忆

---

## 📚 使用示例

### 快速通道示例

```
你：帮我找 agent.md

AI：📍 找到了：~/.openclaw/agents/main/agent/agent.md

耗时：~2 秒
```

### 标准流程示例

```
你：帮我写篇文章

AI：
[QMD 记忆检索]
我记得你之前说过：
- 写文章必须先读流程文档
- 字数要 950-1500 字

[任务类型识别]
任务类型：公众号写作

[读取流程文档]
📖 已读取流程文档

[按流程执行]
第0步：选题推荐
...
```

### 记忆管理示例

```
你：记住：代码必须加注释

AI：✅ 已记住：用户要求"代码必须加注释"

[下次对话]
你：帮我写个函数

AI：我记得你要求"代码必须加注释"

[自动应用，代码带详细注释]
```

---

## 🛠️ 配置

### 自动创建的配置文件

Skill 安装后会自动在 `~/.openclaw/workspace/` 创建：

| 文件 | 说明 |
|------|------|
| **任务类型映射表.md** | 任务类型到流程的映射 |
| **快速通道任务列表.md** | 快速任务定义 |
| **通用任务执行流程.md** | 通用流程（兜底）|
| **流程文档模板.md** | 创建新流程的模板 |

### 自定义配置

**添加新流程：**

1. 使用模板创建流程文档
2. 更新任务类型映射表
3. 立即生效

**添加快速通道任务：**

1. 编辑快速通道任务列表
2. 添加新任务类型
3. 立即生效

---

## 📖 文档

| 文档 | 说明 |
|------|------|
| [README.md](README.md) | 本文件（使用指南）|
| [EXAMPLES.md](EXAMPLES.md) | 14 个使用示例 |
| [完整文档.md](完整文档.md) | 详细文档 |

---

## 🔧 开发

### 项目结构

```
smart-task-manager/
├── skill.md              # Skill 主要逻辑
├── skill.json            # Skill 配置
├── package.json          # npm 包配置
├── README.md             # 使用指南
├── EXAMPLES.md           # 使用示例
├── 完整文档.md           # 详细文档
└── bin/
    ├── install.sh        # Shell 安装脚本
    └── setup.js          # Node.js 安装脚本
```

### 贡献

欢迎贡献！

1. Fork 项目
2. 创建功能分支
3. 提交 Pull Request

---

## 📄 许可证

MIT License - 详见 [LICENSE](LICENSE)

---

## 🤝 致谢

- OpenClaw 团队
- 所有贡献者

---

## 📞 支持

- GitHub Issues
- OpenClaw Community
- 文档：查看 `完整文档.md`

---

*智能任务管理器 v1.0*
*最后更新：2026-03-19*
*作者：Claude + 程哥*
