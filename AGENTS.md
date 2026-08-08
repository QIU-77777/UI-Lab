# AGENTS.md

本文件为操作本仓库（UI-Lab）的 Agent 提供指引，说明代码结构与资源放置规则，确保新增 UI 作品时分门别类、放到正确位置，无需每次重新推断约定。

## 仓库用途

UI 组件实验仓库：存放可复用的前端 UI 组件 demo（以单文件 HTML/CSS/JS 为主）。原名 `UI-Experiment`，已改名为 `UI-Lab`。

## 目录结构

```
UI-Lab/
├── AGENTS.md
├── README.md              # 组件索引（Agent 需维护）
├── assets/                # 各组件预览图/视频（GIF 优先）
│   └── {组件名}.gif
└── Components/            # 每个组件一个目录
    └── {组件名}/
        └── {kebab-case}.html
```

## 资源放置规则（必须遵守）

1. **组件目录**：`Components/{组件名}/`，目录名用标题风格（如 `Aspect Ratio Picker`、`Chat Input`）。
2. **HTML 文件**：放在组件目录内，文件名用 kebab-case 且与该组件一一对应，例如 `aspect-ratio-picker.html`。文件名应能从组件名推导，便于溯源。
3. **预览媒体**：由用户自己把预览文件放入 `assets/`，命名为 `assets/{组件名}.{ext}`（与组件目录同名）。
   - **格式优先 GIF**：README 用标准 Markdown 图片语法 `![名称](./assets/xxx.gif)`。
   - 若用 MP4，README 需改用 `<video src="./assets/xxx.mp4" autoplay loop muted playsinline></video>`。
   - Agent 只负责在 README 中**引用**预览文件，**不要**自行生成或替换预览媒体（除非用户明确要求）。

## README 索引维护

每个组件在根 `README.md` 的 `## Components` 下占一节，格式：

```markdown
### {组件名}

{一句话描述组件用途/特性}。

- Source: [Components/{组件名}/{kebab}.html](Components/{组件名}/{kebab}.html)

![{组件名}](./assets/{组件名}.gif)
```

注意：
- 链接路径中的空格必须 URL 编码为 `%20`（如 `Components/Aspect%20Ratio%20Picker/aspect-ratio-picker.html`）。
- 新增组件时在 `## Components` 末尾追加，不要改动已有条目。

## 新增组件标准流程

1. 在 `Components/` 下创建 `组件名` 目录，放入 `{kebab}.html`。
2. 在 `README.md` 的 `## Components` 追加 `### 组件名` 一节（含 `Source` 链接 + 预览引用）。
3. 提交并推送，提交信息用 `Add {组件名} component`。

## 提交约定

- 不要改动其他组件的目录与文件，除非用户要求。
- 每次只提交与本次新增组件相关的改动。

## 环境提示（已知坑）

若执行直连 `github.com:443` 的 `git push` 时遇到 `SSL_ERROR_SYSCALL` / `HTTP2 framing` / `CONNECT tunnel 502` 等错误（沙箱代理拦截），尝试关闭沙箱隔离后再推送；`gh` API 通道（clone / view / rename）通常不受影响。
