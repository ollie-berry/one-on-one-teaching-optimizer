# 一对一教学 Prompt 优化系统

这是一个面向 Codex Chat 与 Work 场景的一对一教学优化插件。它把项目现有沉淀包装成一个安装单元，包含两个独立 Skill 和一套由两者按需读取的公共知识背景。

## 包含的能力

- `$one-on-one-effect-review`：遍历教学 case，定位并定义效果问题，给出可追溯的判断依据。
- `$one-on-one-prompt-optimizer`：在问题得到确认后，分析 Prompt 根因，提出修改并检查潜在回归。
- 公共知识背景：项目定义、规则优先级、场景与学科边界、产品结束轮契约和已确认业务裁决。

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

仓库内容更新后，使用者执行：

```bash
codex plugin marketplace upgrade one-on-one-teaching
codex plugin add one-on-one-teaching-optimizer@one-on-one-teaching
```

随后新建任务，以加载最新版本。

## 仓库结构

```text
.agents/plugins/marketplace.json
plugins/one-on-one-teaching-optimizer/
├── .codex-plugin/plugin.json
├── skills/
│   ├── one-on-one-effect-review/
│   └── one-on-one-prompt-optimizer/
└── shared/context/00_公共知识背景/
```

本仓库当前未附加开源许可证。
