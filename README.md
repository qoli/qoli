# Hi, I'm Ronnie W

I build local-first products, AI/agent runtimes, and Apple-platform systems where the hard part is not "using AI", but making the workflow observable, repeatable, recoverable, and useful under real constraints.

My work usually starts from raw material: repos, logs, device behavior, user flows, browser output, release pipelines, and long-lived product maintenance. The result I care about is a system that can be inspected, rerun, debugged, shipped, and explained.

[RonnieCC](https://ronniewong.cc) is the public index of my projects and writing. GitHub is where many of the implementation surfaces, runtime experiments, and product-support repos live.

## What I Work On

- **LLM and agent runtimes**: session continuity, workspace binding, failure recovery, context restoration, tool boundaries, and reviewable intermediate state.
- **Local-first AI products**: Apple-platform reading, capture, indexing, and inference workflows designed around real context-window, token-budget, privacy, and device constraints.
- **Media and tvOS runtimes**: playback stability, source volatility, plugin boundaries, HLS/transmux edge cases, Apple TV focus, and long-term product maintenance.
- **Observable workflows**: turning debugging, publishing, SEO, design review, and AI collaboration into repeatable flows with visible evidence.
- **Distribution systems**: making content, docs, changelogs, project pages, and support surfaces readable by people, search engines, and agents.

## Selected Systems

### [eisonAI](https://github.com/qoli/eisonAI)

Local-first AI reading for macOS, iOS, iPadOS, and Safari Extension.

The interesting part is not a summary button. It is a structure-first reading workflow with bundled WebLLM popup inference, native app boundaries, token-aware long-document processing, and Apple-platform product constraints.

**Surface:** public Swift repo, App Store product, Safari Extension, local inference workflow.

### Syncnext

Long-running Apple TV media runtime and product ecosystem.

Syncnext is built around a practical boundary: the native tvOS app owns playback, focus, state, and recovery, while source data, parsing, search, episode resolution, routing rules, and plugin contracts live in external support surfaces.

**Surfaces:** [syncnext-api](https://github.com/qoli/syncnext-api), [syncnextPlugin](https://github.com/qoli/syncnextPlugin), [SyncnextClash](https://github.com/qoli/SyncnextClash), product docs and changelog.

### [threadBridge](https://github.com/qoli/threadBridge)

Workspace-first Codex runtime for binding remote messages to real local workspaces and existing Codex sessions.

The goal is not a chatbot wrapper. It is a desktop-owned runtime with Telegram as an adapter, local management surfaces, session repair, workspace state, release packaging, and continuation across machines and contexts.

**Surface:** public Rust repo, macOS release pipeline, Telegram-to-Codex session continuity.

### [RonnieCC](https://github.com/qoli/RonnieCC)

My public project and writing index.

RonnieCC is also a distribution system: Notion remains a material source, while the public site turns projects, posts, static pages, sitemaps, canonical URLs, and downstream mirrors into a verifiable publishing contract.

**Surface:** public site, static build, project index, blog sync, sitemap and distribution workflow.

### [codex-workflow-skills](https://github.com/qoli/codex-workflow-skills)

Practical Codex workflow skills extracted from repeated real work.

These are not prompt snippets. They capture workflows for context recovery, debugging discipline, model consultation, content handoff, and browser-visible validation so the same kind of work can start from a better default next time.

**Surface:** public Python repo, installable Codex skills, RonnieCC writing.

### HLN Machine

Local white-box AI video-generation pipeline.

This is an exploration in making multimodal generation inspectable: `IR.json`, checkpoints, dependency hashes, partial reruns, subtitle alignment, semantic B-roll selection, and human-reviewable intermediate state matter more than one-off generation output.

**Surface:** RonnieCC project notes and demo material.

## How I Work

I tend to turn messy work into systems through the same loop:

1. Start from evidence: repo state, logs, browser output, data files, device behavior, or publishing surfaces.
2. Find the boundary: what should be native, external, generated, cached, reviewed, retried, or rejected.
3. Make the workflow observable: add checks, artifacts, state, screenshots, tests, or structured outputs.
4. Preserve the method: docs, skills, scripts, project pages, changelogs, or blog posts.

This is the pattern behind most of my recent work: AI collaboration, Apple products, media runtime maintenance, browser validation, publishing pipelines, and project-memory extraction.

## 中文

我做的不是「把 AI 接進產品」而已，而是把真實工作裡的模型推理、上下文管理、狀態轉移、失敗邊界、發布流程和產品維護，整理成可觀測、可重跑、可審查、可交付的系統。

我的公開資料分成三層：

- **GitHub**：實作、runtime、工具、plugin、發布與維護表面。
- **RonnieCC**：項目、文章、方法論與公開索引。
- **Data / workspace**：真實 repo、日誌、瀏覽器驗收、Notion material、Codex session 和本地產品現場。

我關心的是從真實材料裡提煉可重複的方法：讓 AI 協作不再停在 prompt，讓產品維護不只靠記憶，讓內容分發不是發出去就結束，讓每一次有效的判斷都能被固定成下次可用的系統。

## Links

- Website: [ronniewong.cc](https://ronniewong.cc)
- GitHub: [github.com/qoli](https://github.com/qoli)
- Projects: [ronniewong.cc/projects](https://ronniewong.cc/projects)
- Blog: [ronniewong.cc/blog](https://ronniewong.cc/blog)
