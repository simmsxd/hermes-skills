# Dig me

Dig me 的 skill 集合。每个 skill 是一个自包含的目录，可直接克隆到 agent 的 skills 目录使用。

## 索引

| Skill | 一句话 | 版本 |
|---|---|---|
| [`dig-me`](skills/dig-me/) | 自我挖掘追问技能——用多轮单点提问收集行为证据，生成基于事实的自我画像 | v1.0.0 |

## 目录结构

```
skills/
└── dig-me/
    ├── SKILL.md                # 技能主文件（指令与纪律）
    └── references/
        └── question-bank.md    # 六大维度问题库与追问模板
```

## 关于 dig-me

把「认识自己」从一次性的哲学问题，变成一场结构化的证据收集。

- **核心原则**：真正的自己不是"想"出来的，是"做"出来、再从做的结果里反推出来的。
- **三种模式**：单人（默认）/ 多人（多对象独立 session）/ 公开资料（分析不在场人物，强制声明证据滤镜）
- **六大维度**：能量与满足感 / 压力与选择 / 情绪溯源 / 决策回看 / 他人镜像 / 矛盾检测
- **追问纪律**：一次只问一个问题；形容词一律触发「说一件具体的事」；深度优先不广撒网
- **产出**：Markdown 自我画像，含反复出现的主题、推断的价值排序、行为与自我叙事的偏差、
  未测试区域、3 个行为实验建议

与 [`grill-me`] 的区别：grill-me 审查**外部方案**，dig-me 挖掘**内部自我**。

## 安装

```bash
# 稀疏检出，只取 dig-me，不拉整个仓库
git clone --filter=blob:none --sparse https://github.com/simmsxd/hermes-skills.git
cd hermes-skills
git sparse-checkout set skills/dig-me
```

或直接拷目录：

```bash
git clone --depth 1 https://github.com/simmsxd/hermes-skills.git /tmp/hermes-skills
mkdir -p ~/.workbuddy/skills/dig-me
cp -r /tmp/hermes-skills/skills/dig-me/. ~/.workbuddy/skills/dig-me/
```

Windows PowerShell:

```powershell
git clone --depth 1 https://github.com/simmsxd/hermes-skills.git "$env:TEMP\hermes-skills"
$dst = "$env:USERPROFILE\.workbuddy\skills\dig-me"
New-Item -ItemType Directory -Force -Path $dst | Out-Null
Copy-Item "$env:TEMP\hermes-skills\skills\dig-me\*" $dst -Recurse -Force
```

## 新增 skill 的约定

1. 目录名 = skill 名，放在 `skills/<name>/`
2. 必须含 `SKILL.md`，YAML frontmatter 至少要有 `name` 和 `description`
3. 辅助材料放 `references/`，脚本放 `scripts/`
4. 需要固定外部工具权限时，用 `allowed-tools` 显式声明
5. 在本 README 的索引表里加一行

## 隐私提醒

**不要提交任何由 skill 生成的个人数据文件。** 例如 dig-me 会生成自我画像
（`dig-me-*.md`），属于私密内容，已在 `.gitignore` 中屏蔽。新增 skill 时请一并补充
对应的忽略规则。

## License

MIT — 见 [LICENSE](LICENSE)
