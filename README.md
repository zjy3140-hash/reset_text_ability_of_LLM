# reset_text_ability_of_LLM

一份 [Agent Skills](https://agentskills.io/specification) 格式的技能。它用你提供的输出风格或人物设定覆盖模型在文本生成时的默认指纹，并把该设定立成唯一说话身份。可以与人格插件一起使用。

源文件是仓库根目录的 [`skill.md`](skill.md)。各 harness 加载的文件名是 `SKILL.md`，所在目录名必须是 `reset-text-ability`，与 frontmatter 里的 `name` 一致。把这一份文件放到目标 harness 的技能目录即可。

## 技能作用域

在 Agent 里按下面的方式明确调用。调用之后提供输出风格或人物设定，至少一项，并选择作用域：

- 单次对话：生成的英文指令只约束当前对话。
- user 级：生成可保存为用户规则的英文指令。保存之后，之后的对话默认使用。

这里的 user 级是技能运行后的效果，和下面把文件装到哪个目录是两件事。

| Harness | 明确调用 |
| --- | --- |
| Cursor、Claude Code | `/reset-text-ability` |
| Codex | `$reset-text-ability`，或打开 `/skills` |

`disable-model-invocation: true` 被 Cursor 和 Claude Code 识别，因此这两处不会按描述自动调用。该字段不属于 Agent Skills 规范的六个字段。claude.ai 上传和严格的规范打包只接受 `name`、`description`、`license`、`compatibility`、`metadata`、`allowed-tools`；走那条上传路径时需要先去掉这个字段。

## 下载

源文件：

https://raw.githubusercontent.com/zjy3140-hash/reset_text_ability_of_LLM/main/skill.md

页面：

https://github.com/zjy3140-hash/reset_text_ability_of_LLM/blob/main/skill.md

把 `<目录>` 换成下一节里的技能目录：

```bash
mkdir -p <目录>/reset-text-ability
curl -fsSL -o <目录>/reset-text-ability/SKILL.md \
  https://raw.githubusercontent.com/zjy3140-hash/reset_text_ability_of_LLM/main/skill.md
```

克隆后安装：

```bash
git clone https://github.com/zjy3140-hash/reset_text_ability_of_LLM.git
mkdir -p <目录>/reset-text-ability
cp reset_text_ability_of_LLM/skill.md <目录>/reset-text-ability/SKILL.md
```

## 安装目录

`~/.agents/skills` 是一条能同时被多个 harness 读到的本机目录：Cursor、Codex、Gemini CLI、GitHub Copilot。

```bash
mkdir -p ~/.agents/skills/reset-text-ability
curl -fsSL -o ~/.agents/skills/reset-text-ability/SKILL.md \
  https://raw.githubusercontent.com/zjy3140-hash/reset_text_ability_of_LLM/main/skill.md
```

Claude Code 读取自己的目录，不读取 `~/.agents/skills`：

```bash
mkdir -p ~/.claude/skills/reset-text-ability
curl -fsSL -o ~/.claude/skills/reset-text-ability/SKILL.md \
  https://raw.githubusercontent.com/zjy3140-hash/reset_text_ability_of_LLM/main/skill.md
```

| Harness | 本机，所有项目 | 当前项目 |
| --- | --- | --- |
| Cursor | `~/.agents/skills/`、`~/.cursor/skills/` | `.agents/skills/`、`.cursor/skills/` |
| Claude Code | `~/.claude/skills/` | `.claude/skills/` |
| Codex | `~/.agents/skills/` | `.agents/skills/` |
| Gemini CLI | `~/.agents/skills/`、`~/.gemini/skills/` | `.agents/skills/`、`.gemini/skills/` |
| GitHub Copilot | `~/.agents/skills/`、`~/.copilot/skills/` | `.agents/skills/`、`.github/skills/`、`.claude/skills/` |

目录依据：

- [Agent Skills 规范](https://agentskills.io/specification)
- [Cursor](https://cursor.com/docs/skills)
- [Claude Code](https://code.claude.com/docs/en/skills)
- [Codex](https://learn.chatgpt.com/docs/build-skills)
- [Gemini CLI](https://geminicli.com/docs/cli/skills/)
- [GitHub Copilot](https://docs.github.com/en/copilot/concepts/customizations/agent-skills)
