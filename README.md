# Hi, I'm Ronnie W

## English

I design and build LLM systems with clear `context-window`, `token-budget`, and `agent/runtime` boundaries, along with local-first products that remain stable under real device constraints and messy inputs.

My work is not about wiring models into products. I turn inference, context management, state transitions, failure boundaries, and intermediate artifacts into observable, replayable, reviewable systems. That includes local inference, long-document routing and chunking, white-box multimodal generation pipelines, and runtime engineering for deterministic behavior on constrained platforms.

I care about clear system boundaries, explainable `token accounting`, verifiable context management, human-in-the-loop control, and operational reliability over black-box magic.

## What I Build

- LLM systems with explicit `context-window`, `token-budget`, and routing design
- `Agent/runtime` architectures with explicit state, failure boundaries, and observability
- Local-first reading and knowledge products on Apple platforms
- White-box multimodal generation pipelines and tvOS / Apple TV media runtimes with plugin boundaries

## Core Projects

### eisonAI

`eisonAI` is a local-first reading system for macOS, iOS, and iPadOS. Its core is not "AI summaries," but a long-document inference flow designed around real `context-window` and `token-budget` constraints on Apple devices. The problem it addresses is not generic AI chat, but how to preserve semantic stability and reading control when documents are long, references are scattered, and context is limited.

Its implementation splits responsibilities cleanly across a Safari Extension and a native app. The content script only extracts article text. The Safari popup runs on-device inference with WebLLM (`WebGPU + WebWorker`). The native app uses MLCSwift for another local inference path. Models and wasm assets are bundled directly instead of being downloaded at runtime. The important part is not the "local AI" label, but the clarity of runtime lifecycle, resource boundaries, and inference ownership.

Another core aspect is that token estimation, routing, and chunking are treated as system design, not UI detail. `eisonAI` does not design around a model's advertised theoretical context window. It routes, chunks, and falls back based on the token budget actually available on-device, while trying to keep tokenizer and chunking behavior aligned across the App and the Extension. The long-document flow is also not just `chunk + reduce`: it generates high-trust reading anchors first, then compresses those anchors into a presentation summary, keeping intermediate state reviewable while controlling semantic drift and hallucination.

The hard part is not getting a model to run. It is productizing a model-aware local inference system on Apple platforms while keeping token/context management consistent, privacy intact, and the workflow usable in real reading.

### HLN Machine

`HLN Machine` is a fully local, white-box, fault-tolerant multimodal generation system that turns a news seed into a complete YouTube Short without relying on cloud APIs. The problem is not simply chaining models together. It is building a production runtime where `LLM`, `VL`, `Whisper`, and video generation can coexist with explicit intermediate states, partial reruns, and reviewable outputs.

One of its strongest implementations is the B-Roll system. Instead of asking an LLM to directly invent shots or prompts, it computes semantic energy from the script, uses `entropy`, `PAC`, `VSI`, and energy gradients to locate the right insertion points, maps abstract meaning into "reality symbols," filters with VL models, and only then lets an LLM select candidates before handing them to WAN. That turns B-Roll from a taste-driven generation trick into an analyzable, repeatable decision path.

Another major difficulty is word-level subtitle alignment. HLN does not stop at sentence-level correction. It combines Whisper word timestamps, an official script, and a tightly constrained LLM proofreader. The model is allowed to change only each `word` field while `index / start / end / confidence / JSON structure` stay locked. With colloquial rewrites, segment-level retries, and global verification, the system aligns semantic truth back to the real audio timeline. This is not copy editing. It is controlled correction under structural invariants.

At the system level, everything revolves around `IR.json`, dependency hashes, checkpoints, partial reruns, and structural validation. ComfyUI is treated as a local video-generation microservice, not as a GUI toy. That is representative of how I work: when models are unreliable, the answer is stronger architecture, tighter constraints, and better observability.

### Syncnext

`Syncnext` is a long-running tvOS project. Starting from the early `SyncPlayer 1.0` line in 2019 and still evolving today, it is not a short-term player app for me but a long-built Apple TV media system. Its weight comes not from "having built a player," but from spending years turning a product that constantly hits edge conditions into one that can still be maintained.

Another core side of the project is learning how to make a non-typical app survive on tvOS. tvOS is not a larger iPad. It has no reliable local persistence, no browser or WebView, and an interaction model centered on Focus. Even input, back-navigation, search, and player controls come with platform-specific constraints. Those constraints forced many things that look like product detail to be treated as system engineering: the division between Focus Engine and SwiftUI focus, raw remote input via Game Controller Framework, UIKit / TVUIKit wrappers for actually usable input and presentation, and a local server path for reconstructed HLS playback.

One major evolution point is the plugin system. It did not exist from day one; it first appeared in the repo on August 30, 2023 as `Plugin Alpha 1 // JSON configuration mode`, and reached a usable `Alpha v2` on September 9, 2023. That means plugins were not a narrative layer but a system boundary that grew out of real product pressure: source sites kept changing, parsing rules kept rotting, and the native app should not hardcode every source integration.

The result is a split runtime. The native tvOS app owns playback, focus, state, and runtime control. `SyncnextAPI` and JavaScript plugins absorb the high-volatility parts: source lists, site parsing, search, episode resolution, and play URL generation. This split protects the stability of the native runtime from the volatility of the source world.

The longest-running difficulty is still playback and transmux stability. The hard problem is not simply supporting many sources, but dealing with `HLS`, `Transmux`, `GOP alignment`, `Live-to-VOD` upgrades, hardware decode hangs, and container / codec edge cases on Apple TV. The goal is not a theoretically correct player, but a system that stays playable, recoverable, and debuggable under the worst real-world inputs.

## What To Contact Me For

- LLM systems that need `context-window`, `token-budget`, and routing design
- `Agent/runtime` architecture with explicit state, observability, and failure handling
- Local-first inference, reading, and knowledge products on Apple platforms
- White-box multimodal pipelines with reviewable intermediate states and partial reruns
- tvOS / Apple TV runtimes with plugin boundaries, playback constraints, and real-device limitations

---

## 中文版

我設計與構建理解 `context windows`、`token budgets`、`agent/runtime boundaries` 的 LLM systems，以及能在真實設備與真實輸入條件下穩定運行的本地優先產品。

我的工作重點，不是把模型接進產品，而是把推理過程、上下文管理、狀態轉移、失敗邊界與中間結果，整理成可觀測、可重跑、可審查的系統。這包括本地推理、長文路由與分段策略、白盒多模型生成管線，以及在受限平台上維持 deterministic behavior 的 runtime engineering。

我重視清晰的系統邊界、可解釋的 `token accounting`、可驗證的 context 管理、human-in-the-loop control，以及比「更像魔法」更重要的 observability 與 operational reliability。

## 我做什麼

- 理解 `context windows`、`token budgets` 與 routing thresholds 的 LLM systems
- 具明確 state、failure boundaries 與 observability 的 `agent/runtime architecture`
- Apple 平台上的本地優先閱讀與知識產品
- 白盒多模型生成管線，以及帶有插件邊界的 tvOS / Apple TV 媒體 runtime

## 核心項目

### eisonAI

這是一個面向 macOS、iOS 與 iPadOS 的本地優先閱讀系統，核心不是「做摘要」，而是在 Apple 裝置上建立一條真正理解 `context window` 與 `token budget` 約束的長文推理流程。`eisonAI` 想處理的不是一般 AI chat，而是當材料過長、重點分散、參照關係模糊時，如何在有限上下文下仍然保持語義穩定與閱讀可控性。

它的特殊實現，在於把 Safari Extension 與原生 App 做成一個混合 runtime，但嚴格切開責任。content script 只抓正文，不做推理；Safari popup 內的 WebLLM（WebGPU + WebWorker）負責 extension 端推理；App 端則用 MLCSwift 承接另一條本機推理路徑。模型與 wasm 資產直接打包進 bundle，不依賴 runtime 下載。這裡真正重要的不是「本地 AI」這個標籤，而是 runtime lifecycle、資源邊界與推理責任被切得很清楚。

另一個核心實現，是它把 token 計算、分流與切段當成系統問題，而不是 UI 細節。`eisonAI` 不以模型宣告的理論 context window 作為設計前提，而是根據裝置上真正可用的 token budget 做 routing、chunking 與 fallback，並要求 App 與 Extension 兩端的 tokenizer / chunking 行為盡可能對齊。長文流程也不是單純的 `chunk + reduce`：它先生成高可信的 reading anchors，再把 anchors 壓成展示摘要，藉此控制 semantic drift、降低 hallucination，並讓輸出保持可審查的中間狀態。

這個項目真正困難的地方，不是把模型跑起來，而是如何在 Apple 平台上，把一套 model-aware 的本地推理系統產品化，同時維持 token/context 管理的一致性、尊重隱私、並能真正落進現實閱讀流程。

### HLN Machine

這是一個完全本地、白盒、具容錯能力的 multimodal generation system，目標是在不依賴雲端 API 的前提下，把一則新聞 seed 自動轉成完整的 YouTube Short。它真正要解決的問題，不是單純把很多模型串起來，而是如何把 LLM、VL、Whisper 與影片生成這些不穩定子系統，放進一條具明確中間狀態、可局部重跑、可審查的生產 runtime。

`HLN Machine` 最特殊、也最有辨識度的實現之一，是它的 B-Roll 方法。這裡不是讓 LLM 直接決定分鏡或直接吐 prompt，而是先從字幕稿中計算語義能量，透過 entropy、PAC、VSI 與能量梯度去找出真正值得插入 B-Roll 的區段，再把抽象語義落到「現實符號」搜尋，交給 VL 模型做語義描述與過濾，最後才讓 LLM 在高量素材描述中選出合適候選並送進 WAN。這種做法的價值在於，它把 B-Roll 從憑感覺的生成流程，變成一套可分析、可驗證、可重跑的決策路徑。

另一個真正耗時、也最難做穩的部分，是 word-level 字幕對齊。HLN 不是只做句級字幕修正，而是把 Whisper 產生的逐字時間戳、正式字幕稿、以及 LLM proofreader 組成一條受嚴格約束的對齊管線。這裡的關鍵不是讓 LLM「幫忙改字幕」，而是只允許它在鎖死 `index / start / end / confidence / JSON structure` 的前提下，修正每個 `word` 的內容，必要時配合口語化重寫、segment-level retry 與全局驗證，把語義真相對回真實語音時間軸。這個部分本質上不是文案修正，而是資料結構保真下的受控校正。

在系統層面，整個流程以 `IR.json`、dependency hash、checkpoint、局部重跑與結構驗證為中心，ComfyUI 也被當成本地 video-generation microservice 管理生命周期與輸出，而不是當成 GUI 玩具。這很能代表我的工程風格：當模型不可靠時，答案不是增加更多魔法，而是建立更強的架構、約束與觀測能力。

### Syncnext

這是一個我做了很多年的 tvOS 長線項目。從 2019 年的 `SyncPlayer 1.0` 構想與早期產品線開始，到今天仍持續演進，`Syncnext` 對我來說不是一個短期播放器專案，而是一個長時間打磨中的 Apple TV 媒體系統。它的重量不在於「做過一個播放器」，而在於我花了很多年，把一個會在真實世界裡持續碰撞邊界條件的產品，一步一步做成能長期維護的系統。

這個項目的另一個核心面向，是它其實在學習如何讓一個非典型的 App 在 tvOS 上活下來。tvOS 不是放大的 iPad。它沒有可靠的本地持久儲存、沒有瀏覽器與 WebView、交互模型以 Focus 為中心，連輸入、返回、搜尋與播放器控制都帶有強烈的平台約束。這些限制逼著我把很多看似「產品細節」的東西，實際當成系統工程去做，例如 Focus Engine 與 SwiftUI 焦點系統的分工、用 Game Controller Framework 走 RAW 遙控器輸入、用 UIKit / TVUIKit 包裝 tvOS 真正可用的輸入與呈現層、以及用 local server 來承接重建後的 HLS 播放路徑。

另一個很值得強調的節點，是 `Syncnext` 的 plugin system 不是從一開始就存在，而是到 **2023 年 8 月 30 日** 才在 repo 裡正式出現 `Plugin Alpha 1 // JSON configuration mode`，並在 **2023 年 9 月 9 日** 進到可用的 `Alpha v2`。這代表插件系統不是拿來包裝產品敘事的概念，而是在產品做了一段時間之後，為了處理來源站點持續變動、解析規則容易失效、以及原生 App 不應硬寫所有站點邏輯，才真正長出來的系統邊界。

這套拆法最後把 tvOS runtime 分成兩層：原生端負責播放器、焦點、狀態與運行時控制；`SyncnextAPI` 與 JavaScript 插件則承接高變動的來源清單、站點解析、搜尋、分集與播放 URL 生成。這種拆法的價值很直接，就是把「tvOS 原生 runtime 的穩定性」和「來源世界的高變動性」切開，讓 App 不會因為每個站點規則改一次，就被迫整體改版一次。

真正最耗時的，仍然是播放與 transmux 穩定性。對 `Syncnext` 來說，難點從來不是「支援很多來源」本身，而是如何在 Apple TV 這種受限裝置上處理 `HLS`、`Transmux`、`GOP alignment`、`Live-to-VOD` 升級、硬體解碼卡死、以及不同容器與編碼引發的播放連鎖問題。這部分不是做出一個理論上正確的播放器，而是把真實世界裡最差的輸入條件內化進系統，讓它仍然可播放、可恢復、可調試。

## 適合找我做什麼

- 設計需要 `context windows`、`token budgets` 與 routing strategies 的 LLM systems
- 定義具 explicit state、observability 與 failure handling 的 `agent/runtime architecture`
- 構建 Apple 平台上的本地優先推理、閱讀與知識產品
- 設計具中間狀態、可局部重跑、可審查的白盒 multimodal pipelines
- 構建帶有插件邊界、播放約束與真實設備限制的 tvOS / Apple TV runtime
