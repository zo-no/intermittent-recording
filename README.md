# Intermittent Recording Plugin

间歇性记录插件 - 柳比歇夫式时间日志系统

[![Claude Code Plugin](https://img.shields.io/badge/Claude%20Code-Plugin-blue)](https://code.claude.com/docs/zh-CN/plugins)

## 简介

这是一个用于 [Claude Code](https://code.claude.com) 的插件，实现了一套完整的柳比歇夫式时间记录与复盘系统。通过两个核心技能协同工作，帮助你将零散的时间记录转化为结构化的时间日志，并生成深度洞察。

## 核心技能

### 1. diary-builder（日记构建器）

**功能**：将零散、粗糙的间歇性记录，完善为小时级粒度的时间日志。

**核心原则**：
- **原文神圣**：原始记录一字不改，完整保留
- **仅做补充**：只在空白时段添加记录，以 `[补充]` 明确标记
- **分类后置**：标签、统计、洞察全交给 day-reflection

**使用方法**：
```bash
/diary-builder           # 完善今天的记录
/diary-builder 2026-02-20 # 完善指定日期
```

### 2. day-reflection（日复盘）

**功能**：基于结构化时间日志，进行柳比歇夫式时间统计，发现行为模式，生成推动身份改变的洞察与犀利建议。

**核心价值**：
1. **时间可视化** - 精确统计时间分配，发现"时间黑洞"
2. **模式洞察** - 识别高效/低效时段，发现行为规律
3. **身份检查** - 对比今日行为与长期目标，暴露错位（犀利直接）
4. **明日行动** - 给出一个可立即执行的小改变
5. **周日提醒** - 周日自动提醒进行周回顾

**使用方法**：
```bash
/day-reflection           # 复盘今天
/day-reflection 2026-02-20 # 复盘指定日期
```

## 工作流程

```
┌─────────────────┐     ┌─────────────────┐
│  diary-builder  │ ──▶ │ day-reflection  │
│   (完善记录)     │     │ (统计+洞察+建议) │
└─────────────────┘     └─────────────────┘
```

**必须先运行 diary-builder，再运行 day-reflection。**

## 安装

### 方法一：通过 GitHub 安装

```bash
claude /plugin install https://github.com/zo-no/intermittent-recording
```

### 方法二：本地开发测试

```bash
git clone https://github.com/zo-no/intermittent-recording.git
claude --plugin-dir ./intermittent-recording
```

## 文件结构

```
intermittent-recording/
├── .claude-plugin/
│   └── plugin.json          # 插件清单
├── skills/
│   ├── diary-builder/
│   │   └── SKILL.md         # 日记构建器技能
│   └── day-reflection/
│       └── SKILL.md         # 日复盘技能
└── README.md                # 本文件
```

## 时间分类体系

day-reflection 使用六类时间分类：

| 类别 | 定义 | 对应标签 | 颜色 |
|------|------|----------|------|
| 🟢 核心工作 | 产出直接价值的工作 | `#工作` + `#深度` | 绿色 |
| 🔵 个人发展 | 学习、阅读、技能提升 | `#学习` | 蓝色 |
| 🟡 生活管理 | 必要的日常事务 | `#生活` | 黄色 |
| 🟠 社交娱乐 | 有意识的社交、娱乐 | `#社交` | 橙色 |
| ⚪ 休息 | 睡眠、冥想、真正的放松 | `#休息` | 灰色 |
| 🔴 消耗/黑洞 | 无意识刷手机、拖延、发呆 | （专注度≤2且无产出）| 红色 |

## 人生目标配置

day-reflection 需要读取人生目标文件进行身份检查：

**文件路径**：`2-长期项目/人生目标.md`

**文件结构示例**：
```markdown
# 人生目标

## 角色维度定义

### 1. 职业角色：自媒体创作者（含技术输出）

**目标身份**：...

**目标行为**（每月/每周）：
- ...

**关键指标**：
- ...
```

## 许可证

MIT License

## 作者

[zo-no](https://github.com/zo-no)

## 致谢

- 柳比歇夫时间管理法
- [Claude Code](https://code.claude.com)
