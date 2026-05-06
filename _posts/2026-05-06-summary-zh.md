---
layout: default
title: "Horizon Summary: 2026-05-06 (ZH)"
date: 2026-05-06
lang: zh
---

> From 45 items, 14 important content pieces were selected

---

1. [SGLang v0.5.11：CUDA 13、投机解码 V2、Radix 缓存](#item-1) ⭐️ 8.0/10
2. [.de 域名 DNSSEC 故障已解决由配置错误导致](#item-2) ⭐️ 8.0/10
3. [Gemma 4 通过多 token 预测草稿器实现 3 倍推理加速](#item-3) ⭐️ 8.0/10
4. [计算机视觉操作比结构化 API 贵 45 倍](#item-4) ⭐️ 8.0/10
5. [AI 三条逆定律挑战人机交互](#item-5) ⭐️ 8.0/10
6. [为什么大多数产品导览被跳过](#item-6) ⭐️ 8.0/10
7. [谷歌 Chrome 悄悄安装 4GB AI 模型，未获用户同意](#item-7) ⭐️ 8.0/10
8. [Redis 数组数据类型浏览器测试平台](#item-8) ⭐️ 8.0/10
9. [GitHub 就故障致歉并披露 30 倍扩容计划](#item-9) ⭐️ 8.0/10
10. [谷歌 DeepMind 英国员工投票成立工会抗议军事 AI](#item-10) ⭐️ 8.0/10
11. [微软 Edge 浏览器会话期间明文存储所有密码于内存](#item-11) ⭐️ 8.0/10
12. [Anthropic 五年内向谷歌云承诺 2000 亿美元支出](#item-12) ⭐️ 8.0/10
13. [苹果计划在 iOS 27 中允许用户选择第三方 AI 模型](#item-13) ⭐️ 8.0/10
14. [DeepSeek 据称融资估值将达 450 亿美元](#item-14) ⭐️ 8.0/10

---

<a id="item-1"></a>
## [SGLang v0.5.11：CUDA 13、投机解码 V2、Radix 缓存](https://github.com/sgl-project/sglang/releases/tag/v0.5.11) ⭐️ 8.0/10

SGLang v0.5.11 将 CUDA 13 设为默认版本，启用了带重叠调度的投机解码 V2，并引入了用于预填充/解码分离的解码侧 radix 缓存。此外，还新增了对 Gemma 4、Qwen3.6 等多个新模型的支持。 此版本通过投机解码 V2 降低了每步 CPU 开销，并恢复了分离部署中的缓存命中率，从而显著提升了 LLM 推理效率。更新的 CUDA 和 PyTorch 默认设置解锁了更新的内核优化，使所有 SGLang 用户受益。 投机解码 V2 现为默认，采用重叠调度来隐藏 EAGLE/MTP/DFLASH 路径的 CPU 开销。用于 PD 分离的解码 radix 缓存在解码节点上实现前缀缓存，减少了共享前缀的首 token 延迟。

github · Kangyan-Zhou · May 5, 21:28

**背景**: SGLang 是一个面向大语言模型（LLM）的开源推理引擎，专注于性能和灵活性。投机解码是一种使用小型草稿模型提议 token，并由大型基模型验证以加速生成且不损失质量的技术。预填充-解码分离将预填充和解码阶段分配到不同节点上，以优化资源利用率和吞吐量。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://arxiv.org/abs/2510.13161">[2510.13161] Mirror Speculative Decoding: Breaking the Serial ...</a></li>
<li><a href="https://docs.ray.io/en/latest/serve/llm/architecture/serving-patterns/prefill-decode.html">Prefill-decode disaggregation — Ray 2.54.1</a></li>

</ul>
</details>

**标签**: `#SGLang`, `#LLM inference`, `#speculative decoding`, `#radix cache`, `#CUDA`

---

<a id="item-2"></a>
## [.de 域名 DNSSEC 故障已解决由配置错误导致](https://status.denic.de/pages/incident/592577eab611ce1e0d00046f/69fa60ef9d12f5057a974f38) ⭐️ 8.0/10

DNSSEC 配置错误导致.de 域名出现大范围解析失败，随后由 DENIC 修复。该事件影响了全球的验证解析器，使所有.de 域名返回 SERVFAIL 响应。 该事件突显了 DNSSEC 在实际运营中的挑战，影响了一个重要的国家顶级域名.de。它暴露了 DNSSEC 部署的脆弱性，以及在发布区域变更前进行严格测试的重要性。 问题在于 DENIC 发布了一个针对 NSEC3 记录的 RRSIG，该签名无法通过区域 ZSK（密钥标签 33834）验证，导致所有验证解析器返回 SERVFAIL。Cloudflare 临时在其 1.1.1.1 解析器上禁用了 DNSSEC 验证作为变通方案。

hackernews · warpspin · May 5, 20:16 · [社区讨论](https://news.ycombinator.com/item?id=48027897)

**背景**: DNSSEC（域名系统安全扩展）为 DNS 记录添加加密签名，使解析器能够验证其真实性和完整性。当 DNSSEC 签名的区域包含无效签名时，验证解析器将拒绝应答并返回 SERVFAIL 错误，导致该区域下的所有域名对依赖验证的用户不可达。该事件影响了由德国注册管理机构 DENIC 运营的.de 域名。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.cloudflare.com/learning/dns/dnssec/how-dnssec-works/">How does DNSSEC work? - Cloudflare</a></li>

</ul>
</details>

**社区讨论**: 社区迅速识别出根本原因是 DNSSEC 配置错误，而非名称服务器故障。有评论调侃 DENIC 团队当时正在聚会，也有人注意到 Cloudflare 在 1.1.1.1 上禁用了 DNSSEC 验证。一位用户建议应使用形式化方法来处理 DNSSEC 运维，以防止此类问题。

**标签**: `#DNSSEC`, `#DNS`, `#outage`, `#.de`, `#incident`

---

<a id="item-3"></a>
## [Gemma 4 通过多 token 预测草稿器实现 3 倍推理加速](https://blog.google/innovation-and-ai/technology/developers-tools/multi-token-prediction-gemma-4/) ⭐️ 8.0/10

Google 发布了针对 Gemma 4 系列的多 token 预测（MTP）草稿器，与标准解码相比，推理速度最高提升 3 倍，且质量无损失。 这一进展显著降低了 Gemma 4 模型的延迟，使其在实时应用和本地部署中更加实用，同时保持了输出质量。 这些草稿器采用推测解码：一个较小的草稿模型在主模型处理一个 token 的时间内预测多个 token，然后在一次前向传播中验证它们。

hackernews · amrrs · May 5, 16:14 · [社区讨论](https://news.ycombinator.com/item?id=48024540)

**背景**: 推测解码是一种推理优化技术，通过快速的草稿模型和较慢的目标模型每步生成多个 token。小型草稿模型提出候选 token，目标模型并行验证，保持原始输出分布。该技术可以在不损失精度的情况下将延迟降低 2-3 倍，类似于 CPU 中的推测执行。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://blog.google/innovation-and-ai/technology/developers-tools/multi-token-prediction-gemma-4/">Accelerating Gemma 4: faster inference with multi-token prediction drafters</a></li>
<li><a href="https://en.wikipedia.org/wiki/Speculative_decoding">Speculative decoding</a></li>
<li><a href="https://aitoolly.com/ai-news/article/2026-05-06-google-boosts-gemma-4-performance-multi-token-prediction-drafters-deliver-3x-faster-inference">Google Gemma 4 MTP Drafters: 3x Faster AI Inference Speed | AIToolly</a></li>

</ul>
</details>

**社区讨论**: 社区成员称赞推测解码巧妙且有效，指出 Gemma 模型每个输出使用的 token 比竞争对手少。一些人讨论了将模型和草稿器装入 24GB VRAM 的实际挑战，而另一些人则报告了将 MTP 支持集成到 llama.cpp 中的进展。

**标签**: `#gemma`, `#speculative decoding`, `#inference optimization`, `#AI`, `#multi-token prediction`

---

<a id="item-4"></a>
## [计算机视觉操作比结构化 API 贵 45 倍](https://reflex.dev/blog/computer-use-is-45x-more-expensive-than-structured-apis/) ⭐️ 8.0/10

Reflex.dev 的一项新分析显示，使用 AI 视觉代理执行 UI 交互的成本是使用结构化 API 的 45 倍，该比较基于一个多步骤工作流的直接对比。 这一成本差异凸显了 AI 代理设计中的关键权衡：虽然计算机视觉代理为与任意 UI 交互提供了灵活性，但结构化 API 在定义明确的任务上成本显著更低，使得基于 API 的方法在企业自动化中更具可扩展性。 该分析比较了使用视觉代理进行的 14 步工作流与带有明确指令的结构化 API 调用；视觉代理的每一步都消耗了更多的 token 和计算资源，导致成本增加了 45 倍。

hackernews · palashawas · May 5, 16:34 · [社区讨论](https://news.ycombinator.com/item?id=48024859)

**背景**: 计算机视觉操作（即基于视觉的 UI 自动化）依赖 AI 模型解释截图并生成如鼠标点击等动作，计算成本高昂。相比之下，结构化 API 提供直接的编程接口，以可预测的格式返回数据，无需渲染可视化界面，因此对已知操作而言成本更低、速度更快。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://reflex.dev/blog/computer-use-is-45x-more-expensive-than-structured-apis/">Computer use is 45x More Expensive Than Structured APIs</a></li>
<li><a href="https://aitoolly.com/ai-news/article/2026-05-06-the-45x-cost-penalty-why-ai-vision-agents-struggle-against-structured-apis-in-new-benchmarks">AI Vision Agents vs APIs: A 45x Cost Difference Analysis</a></li>
<li><a href="https://www.nngroup.com/articles/ai-agents-as-users/">AI Agents as Users - NN/G</a></li>

</ul>
</details>

**社区讨论**: Hacker News 的评论者指出，对抗性的 UI 设计可能故意推高代理的成本，而其他人则认为，后端设计良好且 API 解耦的应用完全无需基于视觉的交互，还有人建议使用辅助功能 API 作为折中方案。

**标签**: `#AI agents`, `#cost analysis`, `#APIs`, `#computer vision`, `#Hacker News`

---

<a id="item-5"></a>
## [AI 三条逆定律挑战人机交互](https://susam.net/inverse-laws-of-robotics.html) ⭐️ 8.0/10

一篇新文章提出了 AI 的“三条逆定律”，用于指导人类在与 AI 系统交互时的行为：不要人格化 AI、不要盲目信任其输出、不要将责任推卸给 AI。 这一框架直接回应了人们对过度依赖 AI 和情感依附的担忧，引发了关于 AI 伦理、信任和人类责任的关键讨论。 这些定律是针对人类而非 AI 的，与阿西莫夫的经典机器人三定律形成对比。文章承认，由于人类天生容易人格化和信任，遵守这些定律可能很困难。

hackernews · blenderob · May 5, 15:27 · [社区讨论](https://news.ycombinator.com/item?id=48023861)

**背景**: 艾萨克·阿西莫夫的机器人三定律是虚构规则，旨在确保机器人对人类安全。逆定律转换了视角，聚焦于人类责任而非机器约束，强调在 AI 增强的世界中人类保持警惕的必要性。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://susam.net/inverse-laws-of-robotics.html">Three Inverse Laws of AI and Robotics</a></li>
<li><a href="https://news.ycombinator.com/item?id=48023861">Three Inverse Laws of AI | Hacker News</a></li>

</ul>
</details>

**社区讨论**: 社区反应不一。一些评论者认为人格化是不可避免的，人类总会信任 AI，使得这些定律不切实际。另一些人同意这些原则，但质疑其可执行性，指出供应商会激励人格化行为，盲目信任难以避免。

**标签**: `#AI`, `#ethics`, `#anthropomorphism`, `#human-computer interaction`, `#robotics`

---

<a id="item-6"></a>
## [为什么大多数产品导览被跳过](https://productonboarding.com/articles/why-product-tours-get-skipped) ⭐️ 8.0/10

一项新分析探讨了用户跳过产品导览的原因，并主张采用受游戏设计模式启发的即时、上下文相关的 onboarding 方式。 这很重要，因为有效的 onboarding 对用户留存和满意度至关重要；许多产品因侵入性、不合时宜的导览而失去用户。 文章将产品导览疲劳与 cookie 同意对话框类比，并强调了渐进式披露和上下文提示等尊重用户意图的游戏设计模式。

hackernews · pancomplex · May 5, 21:05 · [社区讨论](https://news.ycombinator.com/item?id=48028546)

**背景**: 产品导览是引导用户了解应用功能的分步介绍，通常首次使用时展示。即时 onboarding 在用户需要时提供帮助，而非一次性展示所有内容。游戏设计模式如渐进式教程和上下文提示减少信息过载，保持用户参与度。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.disco.co/blog/how-to-build-just-in-time-onboarding-paths-with-ai">How to Build Just-in-Time Onboarding Paths with AI - disco.co</a></li>
<li><a href="https://www.numberanalytics.com/blog/onboarding-in-game-design-ultimate-guide">Onboarding in Game Design - numberanalytics.com</a></li>

</ul>
</details>

**社区讨论**: 评论者强烈反对产品导览，将其与侵入性 cookie 同意对话框类比。一些人将其与游戏教程相提并论，指出像《Universal Paperclips》这样的增量游戏逐步揭示机制，暗示类似模式可应用于应用。总体情绪对强制 onboarding 持否定态度。

**标签**: `#UX`, `#product design`, `#onboarding`, `#user behavior`

---

<a id="item-7"></a>
## [谷歌 Chrome 悄悄安装 4GB AI 模型，未获用户同意](https://www.thatprivacyguy.com/blog/chrome-silent-nano-install/) ⭐️ 8.0/10

谷歌 Chrome 被发现在未经用户明确同意的情况下，悄悄向用户设备下载了一个 4GB 的 AI 模型 Gemini Nano，以启用设备端生成式 AI 功能（如 Prompt API）。 此事引发了严重的隐私和资源担忧，因为它在用户不知情的情况下消耗大量带宽和磁盘空间，尤其对管理共享或实验室环境的系统管理员影响巨大。 该模型 CPU 版本约 2.7 GiB，GPU 版本约 4.0 GiB，当 Chrome 启用了#optimization-guide-on-device-model 和#prompt-api-for-gemini-nano 等标志（通常作为 Origin Trial 的一部分）时，便会下载。

hackernews · john-doe · May 5, 07:34 · [社区讨论](https://news.ycombinator.com/item?id=48019219)

**背景**: Gemini Nano 是谷歌 Gemini 系列大型语言模型的紧凑版本，旨在无网络连接的设备上运行，为应用提供生成式 AI 能力。Chrome 的自动更新机制传统上会在不单独征得同意的情况下下载新功能，但此 AI 模型的大体积引发了关于何为可接受后台更新的争议。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://en.wikipedia.org/wiki/Gemini_Nano">Gemini Nano</a></li>
<li><a href="https://en.wikipedia.org/wiki/Gemini_(language_model)">Gemini (language model) - Wikipedia</a></li>
<li><a href="https://developer.android.com/ai/gemini-nano">Gemini Nano | AI | Android Developers</a></li>

</ul>
</details>

**社区讨论**: 部分评论者认为，下载 AI 模型与下载拼写检查词典并无区别，属于安装 Chrome 时的初始同意范畴；而另一些人则指出，在共享环境中，该模型可能被反复下载，造成带宽和存储的浪费，增加了管理负担。

**标签**: `#Chrome`, `#AI`, `#privacy`, `#consent`, `#Gemini Nano`

---

<a id="item-8"></a>
## [Redis 数组数据类型浏览器测试平台](https://simonwillison.net/2026/May/4/redis-array/#atom-everything) ⭐️ 8.0/10

Simon Willison 创建了一个基于浏览器的交互式测试平台，将 Redis 子集编译为 WebAssembly，让用户能够测试 Salvatore Sanfilippo 提交通知中建议的 Redis 数组数据类型命令。 这一新的数组数据类型可能显著扩展 Redis 在结构化数据处理方面的能力，尤其适用于 AI 代理和服务器端模式匹配。该测试平台让开发者能在该功能合并到 Redis 主代码库之前先行体验。 该测试平台支持 18 个新的 AR 命令，其中 ARGREP 利用 TRE 正则表达式库进行服务器端的类 grep 搜索。WASM 构建完全在浏览器中运行，无需搭建服务器。

rss · Simon Willison · May 4, 15:53

**背景**: Redis 是一种内存数据结构存储系统，广泛用于缓存、消息传递和实时分析。目前 Redis 支持字符串、列表、集合、哈希等数据类型。提议的数组类型引入了有序、可索引的集合，支持范围查询和正则表达式匹配等高级操作。将 Redis 编译为 WebAssembly 可以在浏览器中运行原生 C 代码，从而无需部署服务器实例即可进行交互式测试。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://antirez.com/news/164">Redis array type: short story of a long development</a></li>
<li><a href="https://madewithwebassembly.com/showcase/redis/">Redis - Made with WebAssembly</a></li>
<li><a href="https://redis.io/docs/latest/develop/data-types/">Redis data types | Docs</a></li>

</ul>
</details>

**标签**: `#Redis`, `#data structures`, `#development tools`, `#WASM`

---

<a id="item-9"></a>
## [GitHub 就故障致歉并披露 30 倍扩容计划](https://github.blog/news-insights/company-news/an-update-on-github-availability/) ⭐️ 8.0/10

GitHub CTO Vlad Fedorov 针对 4 月故障发布说明，披露了 30 倍扩容计划，包括将性能敏感代码从 Ruby 迁移至 Go、将数据库负载从 MySQL 移出，以及从自定义数据中心迁移至 Azure 多云架构。 GitHub 的透明通报对开发者社区意义重大，详细说明了将大幅提升可靠性和可扩展性的基础设施变革，影响数百万用户和仓库。 具体说明了两次故障：4 月 23 日合并队列错误影响 658 个仓库，导致 Squash 合并出错并意外还原；4 月 27 日 Elasticsearch 集群疑似因攻击过载，搜索不可用，但核心 Git 操作未受影响。

telegram · zaihuapd · May 5, 11:42

**背景**: GitHub 历史上一直依赖 Ruby on Rails 单体架构和 MySQL 支撑核心服务。随着平台发展，特别是 AI 驱动工作负载的出现，扩展挑战凸显，促使其将性能敏感部分迁移至 Go，并转向多云架构以提升弹性。30 倍扩容计划旨在应对未来增长。

**标签**: `#GitHub`, `#Infrastructure`, `#Scaling`, `#Cloud Migration`, `#Go`

---

<a id="item-10"></a>
## [谷歌 DeepMind 英国员工投票成立工会抗议军事 AI](https://www.theverge.com/tech/923918/google-deepmind-union-bid-ai-military-israel) ⭐️ 8.0/10

伦敦的 1000 多名谷歌 DeepMind 员工投票组建工会，抗议公司与美国国防部和以色列政府签订的军事 AI 合同。 这一行动凸显了 AI 员工对军事应用的道德担忧日益增加，可能迫使谷歌采取更严格的道德准则和员工保护措施。 员工要求谷歌承诺不研发武器或监控技术，建立独立伦理监管机制，并赋予员工基于道德立场拒绝项目的权利。

telegram · zaihuapd · May 5, 12:36

**背景**: Project Nimbus 是以色列政府与谷歌和亚马逊之间价值 12 亿美元的云计算合同，旨在为以色列政府提供人工智能和云服务。2024 年，谷歌解雇了 50 多名抗议 Project Nimbus 的员工。五角大楼近期也确认与谷歌、OpenAI、Nvidia 和 SpaceX 达成协议，允许美军使用其 AI 模型。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://en.wikipedia.org/wiki/Project_Nimbus">Project Nimbus - Wikipedia</a></li>

</ul>
</details>

**标签**: `#AI ethics`, `#military AI`, `#Google`, `#DeepMind`, `#labor rights`

---

<a id="item-11"></a>
## [微软 Edge 浏览器会话期间明文存储所有密码于内存](https://cybernews.com/security/microsoft-edge-loads-cleartext-passwords-to-memory/) ⭐️ 8.0/10

安全研究员 Tom Jøran Sønstebyseter Rønning 发现，Microsoft Edge 在启动时会将所有已保存密码解密并明文加载到内存，整个会话期间保持明文，即使用户未访问需要这些凭证的网站。与其他 Chromium 浏览器不同，Edge 未使用应用绑定加密或按需解密。 这一设计选择显著削弱了 Edge 的密码保护，使得拥有管理员权限的攻击者可以从进程内存中提取所有已保存凭证，甚至包括终端服务器上其他登录用户的密码。它凸显了浏览器密码管理器在便利性与安全性之间的基本权衡。 该漏洞（微软承认是其设计如此）需要本地管理员权限才能利用，限制了远程攻击途径。其他 Chromium 浏览器如 Chrome 仅在需要时解密密码，并利用应用绑定加密将密钥与应用进程绑定。

telegram · zaihuapd · May 5, 23:31

**背景**: 现代浏览器提供内置密码管理器，将凭证加密存储在磁盘上。Chrome 的应用绑定加密（ABE）确保只有 Chrome 进程本身才能解密密钥，防止其他应用（即使具有管理员权限）读取。然而，Edge 在启动时解密所有密码，并在内存中保持明文，使得可以通过 Process Hacker 或 Volatility 等内存转储工具访问。此行为由一名安全研究员首次报告，并得到微软确认。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://chromeenterprise.google/policies/application-bound-encryption-enabled/">ApplicationBoundEncryptionEnabled: Enable Application Bound ...</a></li>
<li><a href="https://www.cyberark.com/resources/threat-research-blog/extracting-clear-text-credentials-directly-from-chromium-s-memory">Extracting Clear-Text Credentials Directly From Chromium’s Memory</a></li>

</ul>
</details>

**标签**: `#security`, `#Microsoft Edge`, `#privacy`, `#vulnerability`, `#browser`

---

<a id="item-12"></a>
## [Anthropic 五年内向谷歌云承诺 2000 亿美元支出](https://www.theinformation.com/articles/anthropic-commits-spending-200-billion-googles-cloud-chips?utm_source=chatgpt.com) ⭐️ 8.0/10

Anthropic 已承诺未来五年向谷歌云支付 2000 亿美元，金额占谷歌云已披露积压订单的 40% 以上。同时，Alphabet 计划以 3500 亿美元估值向 Anthropic 投资最多 400 亿美元。 该交易凸显了人工智能基础设施的巨大资本需求，并加深了 Anthropic 与谷歌云之间的战略合作，可能重塑云 AI 服务的竞争格局。这表明领先的 AI 实验室正在确保长期算力承诺，以训练和部署先进模型。 Anthropic 和谷歌今年 4 月还与博通签下协议，锁定数吉瓦 TPU 算力，预计 2027 年起陆续上线。这 2000 亿美元的承诺是一项多年云服务协议，并非一次性付款。

telegram · zaihuapd · May 6, 03:53

**背景**: 张量处理单元（TPU）是谷歌专门为加速机器学习工作负载（尤其是神经网络）而设计的专用集成电路（ASIC），于 2015 年在内部使用，2018 年向谷歌云用户开放。TPU 专为 TensorFlow 框架设计，在 AI 训练和推理方面效率极高，与英伟达的 GPU 竞争。Anthropic 的巨额算力承诺凸显了训练大型语言模型对专用 AI 硬件的日益增长的需求。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://zh.wikipedia.org/zh-hans/张量处理单元">张量处理单元 - 维基百科，自由的百科全书</a></li>

</ul>
</details>

**标签**: `#Anthropic`, `#Google Cloud`, `#AI Infrastructure`, `#Business Deal`, `#Cloud Computing`

---

<a id="item-13"></a>
## [苹果计划在 iOS 27 中允许用户选择第三方 AI 模型](https://www.bloomberg.com/news/articles/2026-05-05/ios-27-features-apple-plans-to-let-users-swap-models-across-apple-intelligence) ⭐️ 8.0/10

苹果计划在 iOS 27、iPadOS 27 和 macOS 27 中推出名为'Extensions'的功能，允许用户从多个第三方 AI 模型中选择，用于文本生成、图像生成和编辑等任务，打破 ChatGPT 在 Apple Intelligence 中的独家地位。 此举标志着苹果 AI 平台从封闭转向开放，可能重塑移动 AI 生态，给用户更多选择并促进 AI 提供商之间的竞争。这也可能迫使其他科技巨头采取类似的开放策略。 该功能内部称为'Extensions'，将允许第三方 AI 模型为 Siri、Writing Tools 和 Image Playground 提供支持。苹果已在内部测试了谷歌和 Anthropic 的模型，并将继续提供自研模型与第三方选项并存。

telegram · zaihuapd · May 6, 05:38

**背景**: Apple Intelligence 是苹果于 2024 年 6 月发布的生成式 AI 系统，集成在 iOS 18 及更高版本中，提供写作辅助、图像生成和 ChatGPT 集成等功能。目前，ChatGPT 是唯一集成到 Apple Intelligence 中的第三方模型。新的 Extensions 功能将开放平台给多个提供商，让用户控制哪些 AI 模型处理任务。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.theverge.com/tech/924515/apple-intelligence-third-party-chatbot-extensions-ios-27">Apple could let you pick a favorite AI model in iOS 27 | The Verge</a></li>
<li><a href="https://www.digit.in/news/general/apple-may-allow-rival-ai-models-across-ios-27-features-what-it-means.html">Apple may allow rival AI models across iOS 27 features: What it means</a></li>
<li><a href="https://en.wikipedia.org/wiki/Apple_Intelligence">Apple Intelligence</a></li>

</ul>
</details>

**标签**: `#Apple`, `#AI模型`, `#iOS`, `#第三方接入`, `#人工智能`

---

<a id="item-14"></a>
## [DeepSeek 据称融资估值将达 450 亿美元](https://www.bloomberg.com/news/articles/2026-05-06/china-chip-fund-in-talks-to-lead-mega-deepseek-funding-ft-says) ⭐️ 8.0/10

据称，DeepSeek 正在进行首轮大规模外部融资谈判，估值可能达到约 450 亿美元，领投方为中国国家集成电路产业投资基金。 这标志着国家资金对中国核心 AI 公司的深度介入，可能预示着政府对 AI 发展的更强支持，并影响 AI 行业的竞争格局。 本轮融资将是 DeepSeek 首次大规模外部融资，领投方中国国家集成电路产业投资基金以投资具有战略重要性的半导体和科技公司而闻名。

telegram · zaihuapd · May 6, 06:28

**背景**: 国家集成电路产业投资基金（俗称'大基金'）成立于 2014 年，旨在推动中国半导体产业发展，已设立三期基金，其中第三期于 2024 年成立，注册资本 3440 亿元。DeepSeek 是一家开发大语言模型的 AI 公司，此轮融资若落地，将是该公司及中国 AI 发展的重要里程碑。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://zh.wikipedia.org/wiki/国家大基金">国家大基金 - 维基百科，自由的百科全书</a></li>
<li><a href="https://baike.baidu.com/item/国家集成电路产业投资基金/15891498">国家集成电路产业投资基金_百度百科</a></li>

</ul>
</details>

**标签**: `#DeepSeek`, `#AI`, `#funding`, `#China`, `#semiconductors`

---