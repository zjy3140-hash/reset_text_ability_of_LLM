# reset_text_ability_of_LLM

一个需要明确调用的 Cursor Agent Skill。它用你提供的输出风格或人物设定覆盖模型在文本生成时的默认指纹，并把该设定立成唯一说话身份。可以与人格插件一起使用。

源文件是仓库根目录的 [`skill.md`](skill.md)。Cursor 从技能目录中的 `SKILL.md` 加载技能，安装时把本文件保存为这个文件名。所在目录名必须是 `reset-text-ability`，与文件 frontmatter 里的 `name` 一致。

## 调用

在 Agent 对话中输入 `/reset-text-ability`。

调用之后提供输出风格或人物设定，至少一项，并选择作用域：

- 单次对话：生成的英文指令只约束当前对话。
- user 级：生成可保存为用户规则的英文指令。保存之后，之后的对话默认使用。

## 下载

源文件：

https://raw.githubusercontent.com/zjy3140-hash/reset_text_ability_of_LLM/main/skill.md

页面：

https://github.com/zjy3140-hash/reset_text_ability_of_LLM/blob/main/skill.md

### 安装到本机（所有项目）

```bash
mkdir -p ~/.cursor/skills/reset-text-ability
curl -fsSL -o ~/.cursor/skills/reset-text-ability/SKILL.md \
  https://raw.githubusercontent.com/zjy3140-hash/reset_text_ability_of_LLM/main/skill.md
```

### 安装到当前项目

```bash
mkdir -p .cursor/skills/reset-text-ability
curl -fsSL -o .cursor/skills/reset-text-ability/SKILL.md \
  https://raw.githubusercontent.com/zjy3140-hash/reset_text_ability_of_LLM/main/skill.md
```

### 克隆仓库后安装

```bash
git clone https://github.com/zjy3140-hash/reset_text_ability_of_LLM.git
mkdir -p ~/.cursor/skills/reset-text-ability
cp reset_text_ability_of_LLM/skill.md ~/.cursor/skills/reset-text-ability/SKILL.md
```

安装位置见 [Cursor Agent Skills](https://cursor.com/docs/skills)。装好后打开 Customize → Skills，列表中会出现 `reset-text-ability`。
