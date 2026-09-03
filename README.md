# 一对一教学 Prompt 优化系统

这是一个面向 Codex Chat 与 Work 场景的一对一教学优化插件。它把项目现有沉淀包装成一个安装单元，包含两个独立 Skill 和一套由两者按需读取的公共知识背景。

## 包含的能力

- `$one-on-one-effect-review`：基于《寒雪一对一教学效果底层认知模型 v0.5》遍历教学 case，定位并定义效果问题，重点判断互动效果、提问质量和讲解节奏。
- `$one-on-one-prompt-optimizer`：在问题得到确认后，分析 Prompt 根因，提出修改并检查潜在回归。
- 公共知识背景：以《寒雪一对一教学公共背景知识 v0.1》为最高优先级场景事实核心，补充项目定义、规则优先级、学科与产品场景边界。

推荐的生产顺序是：先完成效果评定，再基于已确认的问题进入 Prompt 修改。两个 Skill 会按当前任务动态加载所需背景，不需要使用者手工拼接上下文。

## 安装

在 Codex 终端中执行：

```bash
codex plugin marketplace add ollie-berry/one-on-one-teaching-optimizer --ref main
codex plugin add one-on-one-teaching-optimizer@one-on-one-teaching
```

安装完成后，新建一个任务即可使用。可以直接指定 Skill：

```text
请使用 $one-on-one-effect-review 分析以下一对一教学 case，并定义当前最重要的效果问题。
```

```text
请使用 $one-on-one-prompt-optimizer，基于已确认的问题、当前 Prompt 和对应 case 分析根因并提出修改。
```

## 更新

仓库发布新版本后，使用者可以在 Codex 插件市场中选择“升级”。也可以执行：

```bash
codex plugin marketplace upgrade one-on-one-teaching
codex plugin add one-on-one-teaching-optimizer@one-on-one-teaching
```

随后新建任务，以加载最新版本。

版本变动见 [CHANGELOG.md](CHANGELOG.md)。

## 仓库结构

```text
.agents/plugins/marketplace.json
plugins/one-on-one-teaching-optimizer/
├── .codex-plugin/plugin.json
├── shared/context/00_公共知识背景/
│   ├── 00_寒雪一对一教学公共背景知识_v0.1.md
│   ├── 01_项目定义、角色与规则优先级.md
│   └── 10_场景与产品规则/
└── skills/
    ├── one-on-one-effect-review/
    └── one-on-one-prompt-optimizer/
```

本仓库当前未附加开源许可证。
