---
layout: default
title: "Horizon Summary: 2026-05-07 (ZH)"
date: 2026-05-07
lang: zh
---

> From 35 items, 15 important content pieces were selected

---

1. [苹果计划开放第三方 AI 模型选择](#item-1) ⭐️ 9.0/10
2. [SGLang v0.5.11：默认推测解码 V2 与 CUDA 13 更新](#item-2) ⭐️ 8.0/10
3. [Valve 开源 Steam 控制器 CAD 文件](#item-3) ⭐️ 8.0/10
4. [职场 AI 驱动的生产表演批判](#item-4) ⭐️ 8.0/10
5. [Vibe 编码与智能工程融合，引发信任问题](#item-5) ⭐️ 8.0/10
6. [从 Supabase 到 Clerk 再到 Better Auth 的迁移故事](#item-6) ⭐️ 8.0/10
7. [Google Cloud 欺诈防御：二维码取代验证码](#item-7) ⭐️ 8.0/10
8. [Anthropic 提升 Claude 限制并与 SpaceX 达成算力合作](#item-8) ⭐️ 8.0/10
9. [微软 Edge 浏览器在内存中明文暴露所有已保存密码](#item-9) ⭐️ 8.0/10
10. [Meta 计划推出基于 Muse Spark 的 AI 助手](#item-10) ⭐️ 8.0/10
11. [DeepSeek 首轮融资估值据称达 450 亿美元](#item-11) ⭐️ 8.0/10
12. [Chrome 未经许可静默下载 4GB AI 模型](#item-12) ⭐️ 8.0/10
13. [欧盟拟强制移除华为中兴设备](#item-13) ⭐️ 8.0/10
14. [英伟达、OpenAI 和微软联合发布开放 MRC 协议，提升 AI 集群效率](#item-14) ⭐️ 8.0/10
15. [月之暗面估值突破 100 亿美元，新融资超 7 亿](#item-15) ⭐️ 8.0/10

---

<a id="item-1"></a>
## [苹果计划开放第三方 AI 模型选择](https://www.bloomberg.com/news/articles/2026-05-05/ios-27-features-apple-plans-to-let-users-swap-models-across-apple-intelligence) ⭐️ 9.0/10

苹果计划在 iOS 27、iPadOS 27 和 macOS 27 中允许用户选择第三方 AI 模型用于系统功能，如文本生成、图像生成和编辑。此举打破了 ChatGPT 在 Apple Intelligence 中的独家地位。 这标志着苹果从单一合作伙伴 AI 模型向开放平台的战略转变，可能为用户提供更多选择，并促进 AI 提供商之间的竞争。它可能通过使 Google 和 Anthropic 等模型在苹果设备上系统级可用，显著影响 AI 生态系统。 该功能内部称为'Extensions'，用户可在设置中接入第三方 AI 服务，用于 Siri、Writing Tools 和 Image Playground。内部测试已覆盖 Google 和 Anthropic 的模型。

telegram · zaihuapd · May 6, 05:38

**背景**: Apple Intelligence 是苹果在 2024 年 6 月宣布的生成式 AI 系统，在 iOS 18、iPadOS 18 和 macOS Sequoia 上可用，功能包括 Writing Tools、Image Playground 以及 ChatGPT 集成。目前，ChatGPT 是 Apple Intelligence 中集成的唯一第三方模型。新的'Extensions'功能将允许用户选择替代模型，使 Apple Intelligence 成为托管多种 AI 服务的平台。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://en.wikipedia.org/wiki/Apple_Intelligence">Apple Intelligence</a></li>
<li><a href="https://www.apple.com/apple-intelligence/">Apple Intelligence - Apple</a></li>
<li><a href="https://www.macrumors.com/guide/image-playground/">iOS 18.2: Everything You Should Know About Image Playground</a></li>

</ul>
</details>

**标签**: `#Apple`, `#AI`, `#iOS`, `#third-party models`, `#platform strategy`

---

<a id="item-2"></a>
## [SGLang v0.5.11：默认推测解码 V2 与 CUDA 13 更新](https://github.com/sgl-project/sglang/releases/tag/v0.5.11) ⭐️ 8.0/10

SGLang v0.5.11 默认启用推测解码 V2，升级 CUDA 13 和 PyTorch 2.11，为预填充/解码分离添加了解码端基数缓存，并新增了对 Gemma 4、Qwen3.6、Kimi-K2.6 等模型的支持。 此版本通过推测解码改进和更新的 GPU 内核支持显著提升了 LLM 推理性能，使大规模部署最新模型更加容易。新功能降低了预填充和解码阶段的延迟并提高了吞吐量。 默认 CUDA 版本升级为 13.0，涵盖 SGLang、sgl-kernel 和 Docker 镜像，PyTorch 从 2.9 升级到 2.11。推测解码 V2 采用重叠调度以隐藏 CPU 开销，解码端基数缓存可恢复分离部署中长共享前缀的命中率。

github · Kangyan-Zhou · May 5, 21:28

**背景**: LLM 推理通常将预填充（处理输入）和解码（生成 token）阶段分离以优化资源使用，称为 PD 分离。推测解码使用小型草稿模型一次预测多个 token，然后与目标模型并行验证，从而加速生成。基数缓存存储前缀的键值缓存以避免重复计算。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://docs.vllm.ai/en/latest/features/speculative_decoding/">Speculative Decoding - vLLM</a></li>
<li><a href="https://llm-d.ai/docs/guide/Installation/pd-disaggregation">Prefill/Decode Disaggregation | llm-d</a></li>
<li><a href="https://github.com/sgl-project/sglang/issues/24544">[sglang-miles] Integrate PD decode radix cache · Issue #24544 - GitHub</a></li>

</ul>
</details>

**标签**: `#LLM inference`, `#speculative decoding`, `#CUDA`, `#PyTorch`, `#SGLang`

---

<a id="item-3"></a>
## [Valve 开源 Steam 控制器 CAD 文件](https://www.digitalfoundry.net/news/2026/05/valve-releases-steam-controller-cad-files-under-creative-commons-license) ⭐️ 8.0/10

Valve 以 Creative Commons 许可证发布了 Steam 控制器和 Steam 控制器底座的 CAD 文件，包括 STP 和 STL 模型以及工程图纸。 此举授权社区创建自定义修改、无障碍适配和 3D 打印配件，促进了围绕 Steam Input 的开放硬件生态系统。 仓库包含 STP（STEP）和 STL 模型，以及显示关键特征和禁止区域的工程图纸，支持精确修改和 3D 打印。

hackernews · haunter · May 6, 15:44 · [社区讨论](https://news.ycombinator.com/item?id=48037555)

**背景**: CAD（计算机辅助设计）文件包含用于制造和 3D 打印的精确 3D 几何数据。Creative Commons 许可证允许免费使用、修改和分享（需署名）。开源硬件原则鼓励社区在物理设计上进行协作，类似于开源软件。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://en.wikipedia.org/wiki/Open-source_hardware">Open-source hardware - Wikipedia</a></li>

</ul>
</details>

**社区讨论**: 评论总体积极，用户称赞友好的说明文件，并强调其对需要定制控制器改造的残障玩家的好处。但也有部分人担心该控制器只能在 Steam 中使用，可能形成围墙花园。

**标签**: `#open hardware`, `#valve`, `#steam controller`, `#3d printing`, `#accessibility`

---

<a id="item-4"></a>
## [职场 AI 驱动的生产表演批判](https://nooneshappy.com/article/appearing-productive-in-the-workplace/) ⭐️ 8.0/10

一篇文章指出，职场文档和更新正变得不必要地冗长，而 AI 工具被用来制造产出增加的假象，实际效率并未提升。 这一批判引起了广泛共鸣，因为它揭示了由 AI 驱动的伪生产力趋势，可能导致资源错配，阻碍科技行业的真正创新。 文章指出，需求文档从一页扩展到十二页，状态更新变成了摘要的摘要，这些内容由不阅读自己产出的人编写，送给不阅读接收内容的读者。

hackernews · diebillionaires · May 6, 16:18 · [社区讨论](https://news.ycombinator.com/item?id=48038001)

**背景**: 在许多职场中，'生产力表演'指的是让员工看起来忙碌但实际产出无益的活动。随着 AI 工具如大语言模型的兴起，员工可以迅速生成大量文本或代码，可能掩盖实质性进展的缺失。这种现象在奖励可见努力而非实际成果的企业和科技文化中尤为普遍。

**社区讨论**: 社区成员强烈认同这一批评，分享了个人经历：强制使用 AI 但产出未提升，以及非技术管理层赞扬过度工程化的架构。一位评论者指出，大语言模型已经自动化了'向上管理'。

**标签**: `#workplace productivity`, `#AI tools`, `#over-engineering`, `#corporate culture`, `#tech industry`

---

<a id="item-5"></a>
## [Vibe 编码与智能工程融合，引发信任问题](https://simonwillison.net/2026/May/6/vibe-coding-and-agentic-engineering/#atom-everything) ⭐️ 8.0/10

知名软件工程师 Simon Willison 透露，在他的工作中，vibe 编码与 agentic engineering 正在融合，因为 AI 编码代理变得更加可靠，导致他有时会跳过对生产系统 AI 生成代码的审查。 这种融合挑战了之前不负责任的 vibe 编码与负责任的 agentic engineering 之间的明确界限，提出了关于 AI 辅助软件开发中信任、质量和问责制的关键问题。 Willison 指出，对于构建 JSON API 端点等任务，他信任 Claude Code 无需审查即可正确完成，但对不审查生产代码感到内疚；他将此类比于大型组织中信任其他团队的代码。

rss · Simon Willison · May 6, 14:24 · [社区讨论](https://news.ycombinator.com/item?id=48037128)

**背景**: Vibe 编码由 Andrej Karpathy 提出，指通过自然语言描述意图来让 AI 生成代码，而无需深入理解代码。Agentic engineering 同样由 Karpathy 推广，指专业开发者使用 Claude Code、OpenAI Codex 或 Gemini CLI 等编码代理作为助手，同时保持对质量和安全性的责任。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://en.wikipedia.org/wiki/Vibe_coding">Vibe coding - Wikipedia</a></li>
<li><a href="https://www.ibm.com/think/topics/agentic-engineering">What is agentic engineering? - IBM</a></li>
<li><a href="https://simonwillison.net/guides/agentic-engineering-patterns/what-is-agentic-engineering/">What is agentic engineering? - Agentic Engineering Patterns</a></li>

</ul>
</details>

**社区讨论**: 社区评论表达了怀疑：jwpapi 怀疑 AI 是否总能做对，指出了多个设计决策；zarzavat 警告 AI 错误变得更加微妙而非消失；etothet 认为不规范的工程实践在 LLM 之前就已存在，LLM 只是加速了它；devin 批评使用代码行数作为指标；Havoc 认为这更像是一个谱系而非二元区分。

**标签**: `#vibe coding`, `#agentic engineering`, `#AI coding tools`, `#software engineering`, `#LLM`

---

<a id="item-6"></a>
## [从 Supabase 到 Clerk 再到 Better Auth 的迁移故事](https://blog.val.town/better-auth) ⭐️ 8.0/10

一位开发者详细记录了从第三方认证服务 Supabase 和 Clerk 迁移到开源框架 Better Auth 的过程，引发了社区关于认证外包的讨论。 认证是 Web 应用的关键但常复杂的部分，此次讨论凸显了使用第三方服务的便捷性 vs. 自托管方案的控制力与成本之间的权衡。 Better Auth 是一个框架无关、开源的 TypeScript 认证库，拥有插件生态，旨在简化自托管认证。迁移过程涉及从付费服务 Clerk 转移到 Better Auth。

hackernews · stevekrouse · May 6, 17:19 · [社区讨论](https://news.ycombinator.com/item?id=48038827)

**背景**: 许多 Web 开发者使用 Clerk 或 Supabase Auth 等第三方认证服务以节省时间，但对供应商锁定、成本和数据控制的担忧促使部分人转向自托管方案。Better Auth 提供了一种开源替代方案，可部署在自己的基础设施上。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://better-auth.com/">Better Auth</a></li>
<li><a href="https://clerk.com/">Clerk | Authentication and User Management</a></li>

</ul>
</details>

**社区讨论**: 评论观点不一：有人主张自建认证以获得完全控制权，也有人质疑第三方服务的必要性。Better Auth 的创建者 bekacru 积极回应，称该项目从个人需求发展成了一家公司。

**标签**: `#authentication`, `#web development`, `#self-hosting`, `#third-party services`, `#better-auth`

---

<a id="item-7"></a>
## [Google Cloud 欺诈防御：二维码取代验证码](https://cloud.google.com/blog/products/identity-security/introducing-google-cloud-fraud-defense-the-next-evolution-of-recaptcha/) ⭐️ 8.0/10

Google Cloud 推出了欺诈防御（Fraud Defense），这是 reCAPTCHA 的下一代演进，用二维码取代了传统的图像和音频验证码，用户需通过移动设备扫描二维码来验证身份。 这一变化旨在应对 AI 机器人日益增强的破解视觉验证码能力，但同时也带来了严重的可访问性、隐私和安全问题，可能将没有现代移动设备的用户排除在外，并增加了去匿名化和二维码钓鱼的风险。 二维码挑战要求使用装有 Google Play Services 的现代 Android 设备或 iPhone/iPad，现有 reCAPTCHA 用户将自动升级到 Fraud Defense，无需任何操作。Google 声称新系统简化了用户体验，但批评者指出它强制要求使用移动设备，并可能导致设备指纹识别。

hackernews · unforgivenpasta · May 6, 17:59 · [社区讨论](https://news.ycombinator.com/item?id=48039362)

**背景**: CAPTCHA 是一种用于区分人类用户和自动化机器人的测试。Google 的 reCAPTCHA 从扭曲文本发展为图像识别，再到隐形风险分析，但 AI 的进步使得这些挑战越来越容易被机器人破解。Google 新的欺诈防御平台旨在通过移动设备扫描作为一种更强大的验证方法来保护“智能代理网络”，尽管二维码本身正越来越多地被用于钓鱼攻击。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://cloud.google.com/blog/products/identity-security/introducing-google-cloud-fraud-defense-the-next-evolution-of-recaptcha/">Introducing Google Cloud Fraud Defense, the next evolution of reCAPTCHA | Google Cloud Blog</a></li>
<li><a href="https://www.heise.de/en/news/Instead-of-picture-puzzles-Google-introduces-QR-code-challenge-against-AI-bots-11273871.html">Instead of picture puzzles: Google introduces QR code challenge against AI bots | heise online</a></li>

</ul>
</details>

**社区讨论**: 评论者表达了强烈担忧：有人指出，要求使用装有 Google Play Services 的现代移动设备实际上排除了使用 LineageOS 等自定义 ROM 的用户，并增加了去匿名化风险。另有人强调了可访问性问题，尤其是对在现有音频验证码上遇到困难的盲人用户。其他人则警告二维码安全性，将盲目扫描比作运行 'curl $URL | bash'，并指出二维码钓鱼攻击正在激增。

**标签**: `#recaptcha`, `#fraud defense`, `#google cloud`, `#security`, `#privacy`

---

<a id="item-8"></a>
## [Anthropic 提升 Claude 限制并与 SpaceX 达成算力合作](https://www.anthropic.com/news/higher-limits-spacex) ⭐️ 8.0/10

Anthropic 宣布大幅提升 Claude 的使用限制，包括将 Claude Code 的 5 小时速率限制翻倍，取消 Pro 和 Max 用户的高峰期限制，并显著提高 Claude Opus 的 API 速率限制。该公司还与 SpaceX 签署算力协议，获得 Colossus 1 数据中心超过 300 兆瓦容量和 22 万余块 NVIDIA GPU 的使用权，并计划探索轨道 AI 算力能力。 这项协议直接提升了 Claude 的用户体验和可用性，而与 SpaceX 的合作则突显了前沿 AI 对巨大算力的需求，以及轨道数据中心作为未来基础设施的潜力。这也表明 Anthropic 在积极扩大其 AI 能力，尽管 Colossus 1 存在环境争议。 该算力协议为 Anthropic 提供了超过 300 兆瓦的新增容量和 22 万余块来自 SpaceX Colossus 1 超级计算机的 NVIDIA GPU。作为协议的一部分，Anthropic 表示有兴趣与 SpaceX 共同开发多个吉瓦的轨道 AI 算力容量，但具体时间表尚未公布。

hackernews · meetpateltech · May 6, 16:17 · [社区讨论](https://news.ycombinator.com/item?id=48037986)

**背景**: Colossus 1 是埃隆·马斯克为 xAI 的 Grok 建造的大型超级计算机，位于田纳西州孟菲斯。它因使用未经授权的电力连接并对附近社区造成环境问题而引发争议。像 Claude 这样的人工智能模型需要巨大的计算资源进行训练和推理，因此 Anthropic 等公司寻求与 SpaceX 等数据中心运营商建立大规模算力合作。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.techrepublic.com/article/news-anthropic-spacex-claude-compute-colossus-1/">Anthropic, SpaceX Deal Boosts Claude Compute and Points to ...</a></li>
<li><a href="https://dev.to/mcrolly/anthropic-strikes-compute-deal-with-spacex-what-it-means-for-the-future-of-ai-1moj">Anthropic strikes compute deal with SpaceX — what it means ...</a></li>
<li><a href="https://www.coindesk.com/tech/2026/05/06/anthropic-signs-elon-musk-s-spacex-for-colossus-1-compute-ahead-of-june-ipo">Anthropic signs Elon Musk's SpaceX for Colossus 1 compute ...</a></li>

</ul>
</details>

**社区讨论**: 社区评论指出 Anthropic 使用为 xAI 的 Grok 建造的数据中心具有讽刺意味，并对 300 兆瓦和 22 万 GPU 的规模感到震惊。有人提出对 Colossus 1 非法用电和污染的环境担忧，批评 Anthropic 的安全言论。一位评论者指出，如果每周限制不变，翻倍 5 小时限制只是营销噱头。

**标签**: `#AI`, `#Anthropic`, `#Claude`, `#SpaceX`, `#Compute`

---

<a id="item-9"></a>
## [微软 Edge 浏览器在内存中明文暴露所有已保存密码](https://cybernews.com/security/microsoft-edge-loads-cleartext-passwords-to-memory/) ⭐️ 8.0/10

安全研究员 Tom Jøran Sønstebyseter Rønning 发现，Microsoft Edge 在启动时会解密所有已保存密码并以明文形式加载到内存中，在整个浏览会话期间保持暴露状态。 这一行为显著增加了在 Edge 中保存密码的用户凭据被盗的风险，因为任何拥有管理员权限的恶意软件或攻击者都可以轻松从内存中读取明文密码，而其他 Chromium 浏览器仅在需要时才解密密码。 该漏洞影响所有版本的 Microsoft Edge，即使用户从未访问需要这些凭据的网站也会持续存在。微软已承认该问题，并表示这是有意为之的设计。

telegram · zaihuapd · May 5, 23:31

**背景**: 大多数现代浏览器（包括 Google Chrome）使用应用绑定加密来保护保存的密码，仅在需要时才解密。加密密钥与浏览器身份绑定，防止其他应用程序访问。尽管 Microsoft Edge 基于 Chromium，但它偏离了这一标准，在启动时解密所有密码并将其保存在内存中，从而使其容易受到内存抓取攻击。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://cybernews.com/security/microsoft-edge-loads-cleartext-passwords-to-memory/">Edge keeps unencrypted passwords in memory | Cybernews</a></li>
<li><a href="https://www.forbes.com/sites/daveywinder/2026/05/06/microsoft-says-edge-password-security-vulnerability-is-by-design-is-it-time-to-switch-to-chrome/">Microsoft Says Edge Password Security Vulnerability Is ‘By ...</a></li>
<li><a href="https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/applicationboundencryptionenabled">Microsoft Edge Browser Policy Documentation ...</a></li>

</ul>
</details>

**标签**: `#security`, `#Microsoft Edge`, `#password management`, `#vulnerability`, `#memory safety`

---

<a id="item-10"></a>
## [Meta 计划推出基于 Muse Spark 的 AI 助手](https://www.ft.com/content/5b48360c-53f2-444a-80a8-f7034750fd62?syn-25a6b1a6=1) ⭐️ 8.0/10

Meta 正在为其超过 30 亿用户开发一款个性化 AI 代理，由新模型 Muse Spark 驱动，功能类似开源项目 OpenClaw，目前已在内部试用。 此举使 Meta 有能力与主流 AI 助手竞争，可能借助其庞大用户基础，同时面对投资者对 AI 资本支出增加的担忧。 用户可选择是否向助手分享健康、财务等敏感信息。Meta 将 2026 年资本支出上调 100 亿美元至最高 1450 亿美元，导致股价大幅下跌。

telegram · zaihuapd · May 6, 03:00

**背景**: Muse Spark 是 Meta 超级智能实验室于 2026 年 4 月发布的首个重要 AI 模型，旨在实现个人超级智能。OpenClaw 是一个开源个人 AI 助手框架，能够定时安排任务、生成发票等。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://ai.meta.com/blog/introducing-muse-spark-msl/">Introducing Muse Spark: Scaling Towards Personal Superintelligence</a></li>
<li><a href="https://about.fb.com/news/2026/04/introducing-muse-spark-meta-superintelligence-labs/">Introducing Muse Spark: Meta's Most Powerful Model Yet</a></li>
<li><a href="https://en.wikipedia.org/wiki/OpenClaw">OpenClaw - Wikipedia</a></li>

</ul>
</details>

**标签**: `#Meta`, `#AI Assistant`, `#Open Source`, `#Capital Expenditure`

---

<a id="item-11"></a>
## [DeepSeek 首轮融资估值据称达 450 亿美元](https://www.bloomberg.com/news/articles/2026-05-06/china-chip-fund-in-talks-to-lead-mega-deepseek-funding-ft-says) ⭐️ 8.0/10

据报导，中国 AI 初创公司 DeepSeek 正在与由国家集成电路产业投资基金领投的投资者洽谈首轮外部融资，估值约为 450 亿美元。 本轮融资将是 DeepSeek 从内部资金转向外部投资的重要里程碑，而国家背景基金的参与凸显了中国政府在科技竞争中对本土 AI 领军企业的战略支持。 据报导估值最高可达 500 亿美元，使 DeepSeek 成为全球最具价值的 AI 初创公司之一。DeepSeek 于 2023 年 7 月由梁文锋创立，由对冲基金 High-Flyer 所有，此前从未进行过外部融资。

telegram · zaihuapd · May 6, 06:28

**背景**: DeepSeek 是一家位于杭州的中国 AI 公司，以其大语言模型和 2025 年 1 月推出的聊天机器人而闻名。国家集成电路产业投资基金（又称“大基金”）是由政府支持的投资工具，旨在推动中国半导体和技术自给自足，其第三期规模超过 470 亿美元。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.reuters.com/world/asia-pacific/deepseek-nears-45-billion-valuation-chinas-big-fund-leads-investment-talks-ft-2026-05-06/">DeepSeek could be valued at up to $50 billion in first ...</a></li>
<li><a href="https://en.wikipedia.org/wiki/China_Integrated_Circuit_Industry_Investment_Fund">China Integrated Circuit Industry Investment Fund - Wikipedia</a></li>

</ul>
</details>

**标签**: `#AI`, `#Funding`, `#DeepSeek`, `#China`

---

<a id="item-12"></a>
## [Chrome 未经许可静默下载 4GB AI 模型](https://www.tomshardware.com/tech-industry/cyber-security/google-chrome-silently-downloads-4gb-ai-model-to-your-device-without-permission-report-claims-researcher-says-practice-may-violate-eu-law-waste-thousands-of-kilowatts-of-energy) ⭐️ 8.0/10

安全研究员 Alexander Hanff 指出，Google Chrome 在未经用户同意的情况下自动下载约 4GB 的 Gemini Nano AI 模型文件（weights.bin），即便手动删除也会自动重新下载。 这一做法可能违反欧盟 GDPR 等隐私法，浪费带宽和能源——据估算若覆盖 10 亿用户，碳排放可达 6 万吨——并削弱用户对设备的控制权。 该模型存储在 Chrome 用户配置文件的 OptGuideOnDeviceModel 目录中。只有符合硬件条件的设备才会触发下载，且未显示任何选择加入的提示。

telegram · zaihuapd · May 6, 11:15

**背景**: Gemini Nano 是 Google 的端侧 AI 模型，用于无需网络连接的文本生成等任务。Google 一直在将 AI 功能集成到 Chrome 中，但这种静默部署引发了重大的隐私和环境担忧。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.tomshardware.com/tech-industry/cyber-security/google-chrome-silently-downloads-4gb-ai-model-to-your-device-without-permission-report-claims-researcher-says-practice-may-violate-eu-law-waste-thousands-of-kilowatts-of-energy">Google Chrome 'silently' downloads 4GB AI model to your device without permission, report claims — researcher says practice may violate EU law, waste thousands of kilowatts of energy | Tom's Hardware</a></li>

</ul>
</details>

**标签**: `#privacy`, `#chrome`, `#AI`, `#GDPR`, `#ethics`

---

<a id="item-13"></a>
## [欧盟拟强制移除华为中兴设备](https://t.me/zaihuapd/41247) ⭐️ 8.0/10

欧盟委员会正考虑制定新规，强制所有成员国从其电信和宽带基础设施中移除华为和中兴的设备，将此前非约束性建议升级为具有法律效力的强制性规定。 这将显著影响全球电信供应链，并加剧地缘政治紧张局势，可能促使其他国家效仿。同时凸显欧盟推动数字主权和网络安全的决心。 若新规落地，未按期剥离相关设备的成员国将面临违规调查和经济处罚。此外，欧盟计划收紧对外基建资金池，停止向使用华为设备的非欧盟国家提供项目贷款。

telegram · zaihuapd · May 6, 14:00

**背景**: 2020 年，欧盟发布了不具约束力的'5G 网络安全工具箱'，建议限制高风险供应商，但缺乏法律强制力。新规将使这些建议成为强制性要求，反映欧盟对间谍活动和供应链安全的日益担忧，尽管中方予以否认。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.lexology.com/library/detail.aspx?g=656444e9-e0b8-4e33-9f7f-e2d16624bbc3">The EU’s “High-Risk Vendor” Designation for Chinese 5G Equipment Suppliers - Proposed EU-Wide Ban of Huawei and ZTE Elevates Geopolitics Over Technical Risk Assessment - Lexology</a></li>
<li><a href="https://digital-strategy.ec.europa.eu/en/library/eu-toolbox-5g-security">The EU toolbox for 5G security - Shaping Europe’s digital ...</a></li>
<li><a href="https://commission.europa.eu/topics/international-partnerships/global-gateway_en">Global Gateway - European Commission</a></li>

</ul>
</details>

**标签**: `#geopolitics`, `#telecom`, `#Huawei`, `#EU regulation`, `#cybersecurity`

---

<a id="item-14"></a>
## [英伟达、OpenAI 和微软联合发布开放 MRC 协议，提升 AI 集群效率](https://blogs.nvidia.com/blog/spectrum-x-ethernet-mrc/) ⭐️ 8.0/10

英伟达、OpenAI 和微软等公司联合发布并开源了多路径可靠连接（MRC）协议，这是一种专为 AI 超算集群设计的全新 RDMA 传输协议。 MRC 通过数据包喷射技术充分利用多条网络路径，减少 GPU 闲置时间，提升集群吞吐量和稳定性，从而解决大规模 AI 训练的关键瓶颈。 该协议支持微秒级故障重路由，并已部署在 NVIDIA Spectrum-X 平台和 Blackwell 架构中，用于支撑微软 Fairwater 和甲骨文 OCI Abilene 等集群的 GPT-5.5 训练。

telegram · zaihuapd · May 6, 14:39

**背景**: 在大规模 AI 训练中，基于以太网的 RDMA（RoCE）常因低熵流量导致拥塞热点和负载不均衡。MRC 是一种传输协议，可同时在多条路径上分发数据包，提高有效吞吐量和可靠性。该协议正作为开放计算项目（OCP）规范进行标准化，以减少行业碎片化。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.broadcom.com/blog/enabling-ai-networking-scale-with-multi-path-reliable-connections-mrc">Enabling AI Networking @ Scale with Multi-path Reliable Connections ...</a></li>
<li><a href="https://www.amd.com/en/blogs/2026/amd-advances-ai-networking-at-scale-with-mrc.html">AMD and OpenAI Advance AI Networking at Scale with MRC</a></li>
<li><a href="https://www.opencompute.org/documents/ocp-mrc-1-0-pdf">[PDF] Multipath Reliable Connection (MRC) Specification - Open Compute Project</a></li>

</ul>
</details>

**标签**: `#networking`, `#RDMA`, `#AI training`, `#NVIDIA`, `#protocol`

---

<a id="item-15"></a>
## [月之暗面估值突破 100 亿美元，新融资超 7 亿](https://t.me/zaihuapd/41251) ⭐️ 8.0/10

月之暗面（Kimi 助手背后的公司）完成新一轮超 7 亿美元融资，由阿里巴巴、腾讯等领投，估值在两年多内突破 100 亿美元。此外，Kimi 近 20 天累计收入已超过 2024 年全年总额，海外收入超过国内收入。 这一快速的估值增长和收入激增，突显了中国 AI 初创公司（尤其是大语言模型领域）强劲的市场吸引力和投资者信心。同时表明 Kimi 的全球扩张正在加速，对国际竞争对手形成挑战。 最新一轮融资使月之暗面累计融资额超过 12 亿美元。其 K2.5 模型已在统一 API 网关 OpenRouter 上提供，该模型是开源多模态模型，支持视觉、语言和智能体工作流。

telegram · zaihuapd · May 7, 00:30

**背景**: 月之暗面是一家成立于 2023 年的中国 AI 初创公司，以开发对话式 AI 产品 Kimi 而闻名。“十角兽”是中文术语，指估值超过 100 亿美元的初创企业。像 Kimi 这样的大语言模型利用深度学习生成类似人类的文本，可以通过 API 访问。OpenRouter 是一个提供统一 API 接入数百个 LLM 的平台。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.kimi.com/ai-models/kimi-k2-5">Kimi K2.5 | Open Visual Agentic Model for Real Work</a></li>
<li><a href="https://huggingface.co/moonshotai/Kimi-K2.5">moonshotai/Kimi-K2.5 · Hugging Face</a></li>
<li><a href="https://aiwiki.ai/wiki/openrouter">OpenRouter - AI Wiki</a></li>

</ul>
</details>

**标签**: `#AI startup`, `#fundraising`, `#Chinese AI`, `#Kimi`, `#valuation`

---