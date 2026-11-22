# utools-agents

面向 AI Agent（Antigravity / Codex / Claude Code 等）的 [farfarfun-utools](https://github.com/farfarfun-utools) 生态 `.agents` 配置与多 Skill 仓库。仓库根目录直接对应项目的 `.agents/` 目录布局，可直接 `git clone` 为目标项目的 `.agents` 目录开箱即用，也可在一个仓库内持续扩展多个 `skills/*`、`rules/*` 等。

## Skills

| Skill | 适用场景 | 入口 |
| --- | --- | --- |
| `utools-plugin-development` | `farfarfun-utools` 组织的 uTools 插件开发、清单约束（含单功能 ≤ 5 条 `cmds`）、品牌图标、AI/MCP 工具、截图、GitHub Release、组织索引与 `farfarfun/packages` 发布联动 | [skills/utools-plugin-development/SKILL.md](skills/utools-plugin-development/SKILL.md) |

## 目录结构

```text
.agents/  (即 utools-agents 仓库根目录)
├── .github/workflows/validate.yml   # 自动校验所有 skills/*/SKILL.md、openai.yaml 与相对链接
├── skills/
│   └── <skill-name>/
│       ├── SKILL.md                 # Skill 主入口（YAML frontmatter + 核心规范）
│       ├── agents/openai.yaml       # Agent UI 元数据
│       └── references/              # 按需加载的详细参考文档
├── LICENSE
└── README.md
```

## 安装与使用

### 方式一：直接克隆为项目的 `.agents` 目录（推荐，Antigravity / 通用工作区）

在项目根目录执行：

```bash
git clone https://github.com/farfarfun-utools/utools-agents.git .agents
```

> 若不希望把 `.agents/` 提交到宿主仓库，将其加入宿主仓库的 `.gitignore` 即可；后续在 `.agents/` 内 `git pull`（或在 `utools-dev` 执行 `node scripts/ws.mjs sync --pull`）即可同步最新 Skill。

### 方式二：使用 `skills` CLI

```bash
npx skills add farfarfun-utools/utools-agents
```

### 方式三：安装到全局 Agent 目录（Codex / Claude Code）

```bash
git clone https://github.com/farfarfun-utools/utools-agents.git
cd utools-agents

# Codex（全局软链，拉取仓库后自动生效）
mkdir -p "${CODEX_HOME:-$HOME/.codex}/skills"
for skill in skills/*; do
  ln -s "$(pwd)/$skill" "${CODEX_HOME:-$HOME/.codex}/skills/$(basename "$skill")"
done

# Claude Code（全局）
mkdir -p ~/.claude/skills
cp -R skills/* ~/.claude/skills/
```

## 新增 Skill

在 `skills/<new-skill-name>/` 下创建 `SKILL.md`（frontmatter 的 `name` 必须与目录名一致）和 `agents/openai.yaml`，按需在 `references/` 放置长文档，并在本 `README.md` 的 Skills 表格中登记。CI 的 [validate.yml](.github/workflows/validate.yml) 会自动扫描 `skills/*` 校验元数据与 Markdown 相对链接。

---

## 关于 farfarfun-utools

[farfarfun](https://github.com/farfarfun) 的 uTools 插件产品线：本地优先、集成 uTools 主搜索框与 AI/MCP 工具。

- 🏠 组织主页：<https://github.com/farfarfun-utools>
- 📦 插件下载站：<https://farfarfun.github.io/packages>
- 📧 联系：farfarfun@qq.com

本项目基于 [MIT](LICENSE) 协议开源。
