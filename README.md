# Find Skills

一个帮助 AI agent 与开发者发现、评估和安装可复用 skills 的工作流。入口说明见 [SKILL.md](SKILL.md)。

## 适用场景

- 想给 agent 增加某项能力，先查是否已有可复用 skill。
- 想比较多个候选 skill 的来源、维护状态和适用范围。
- 想通过 Skills CLI 搜索、安装或检查已安装的 skills。

它提供发现与筛选流程，不会自动保证搜索结果可信，也不会替用户安装或执行候选 skill。

## 快速开始

此仓库是一个标准 skill，根目录包含 SKILL.md。按 agent 平台支持的方式安装；使用 Skills CLI 时：

~~~bash
npx skills find "react performance"
npx skills add owner/repository-name
npx skills check
npx skills update
~~~

Skills CLI 默认收集匿名遥测；如不希望发送，可在运行前设置 DISABLE_TELEMETRY=1。当前遥测说明见 [CLI 文档](https://www.skills.sh/docs/cli)。

将 owner/repository-name 替换成要安装的 GitHub 仓库。安装前检查候选来源、文件内容和请求的权限；也可先运行 npx skills --help。手动安装时，把本仓库目录放进 agent 支持的 skills 目录，确认 SKILL.md 位于该 skill 文件夹根部，再重启或刷新 agent。

浏览社区目录：[skills.sh](https://skills.sh/)。

## 推荐发现流程

1. 先确认任务、领域和目标 agent，避免只凭宽泛关键词搜索。
2. 在 skills.sh 查看该领域的热门项目；热门度仅用于发现，不代表安全或质量背书。
3. 运行 npx skills find "<query>"，必要时尝试同义词。
4. 打开候选仓库检查来源、文档、维护情况、安装脚本、网络访问和文件写入行为。
5. 向用户说明候选解决什么问题、来源、维护/流行度线索和安装命令；不把未经核查的结果说成推荐。
6. 只有用户确认后才安装；不要静默跳过需要用户判断的安装步骤。

## 评估清单

- **来源**：是否来自官方组织或可核验的维护者。
- **内容**：SKILL.md 是否与仓库文件一致；是否读取凭据、上传文件、执行 shell、修改代码或访问外部服务。
- **权限**：所需权限是否与任务相称，能否在较小权限下使用。
- **维护**：更新记录、issue、依赖和兼容性是否仍有效。
- **适配**：目标 agent 是否支持该目录结构和 frontmatter。

不要仅凭安装量、星数或搜索摘要作安全判断。安装量和榜单会变化，查看时应注明查询时间。

## 找不到合适的 skill

明确说明没有找到足够可靠的候选，可以直接用 agent 通用能力完成任务；若某流程会反复使用，再考虑自行创建 skill。

## 文件结构

- [SKILL.md](SKILL.md)：触发条件、搜索流程、评估标准和对话方式。
- **README.md**：项目入口与上手说明。

## 许可证

当前仓库未附 LICENSE 文件。公开可见不等于授予复制、修改或再分发许可。
