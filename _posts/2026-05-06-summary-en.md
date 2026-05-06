---
layout: default
title: "Horizon Summary: 2026-05-06 (EN)"
date: 2026-05-06
lang: en
---

> From 45 items, 14 important content pieces were selected

---

1. [SGLang v0.5.11: CUDA 13, Spec Decode V2, Radix Cache](#item-1) ⭐️ 8.0/10
2. [DNSSEC disruption for .de domains resolved after misconfiguration](#item-2) ⭐️ 8.0/10
3. [Gemma 4 Gets 3x Faster Inference with Multi-Token Prediction Drafters](#item-3) ⭐️ 8.0/10
4. [Computer Use 45x More Expensive Than Structured APIs](#item-4) ⭐️ 8.0/10
5. [Three Inverse Laws of AI Challenge Human-AI Interaction](#item-5) ⭐️ 8.0/10
6. [Why Most Product Tours Get Skipped](#item-6) ⭐️ 8.0/10
7. [Google Chrome silently installs 4GB AI model without consent](#item-7) ⭐️ 8.0/10
8. [Redis Array Playground: Test New Data Type in Browser](#item-8) ⭐️ 8.0/10
9. [GitHub Apologizes for Outages, Reveals 30x Scaling Plan](#item-9) ⭐️ 8.0/10
10. [Google DeepMind London Workers Vote to Unionize Over Military AI](#item-10) ⭐️ 8.0/10
11. [Microsoft Edge stores all passwords cleartext in memory during session](#item-11) ⭐️ 8.0/10
12. [Anthropic commits $200B to Google Cloud over five years](#item-12) ⭐️ 8.0/10
13. [Apple plans to let users choose third-party AI models in iOS 27](#item-13) ⭐️ 8.0/10
14. [DeepSeek Reportedly in Talks for $45B Valuation Funding Round](#item-14) ⭐️ 8.0/10

---

<a id="item-1"></a>
## [SGLang v0.5.11: CUDA 13, Spec Decode V2, Radix Cache](https://github.com/sgl-project/sglang/releases/tag/v0.5.11) ⭐️ 8.0/10

SGLang v0.5.11 makes CUDA 13 the default, enables Speculative Decoding V2 with overlap scheduling, and introduces a decode-side radix cache for prefill/decode disaggregation. It also adds support for multiple new models like Gemma 4 and Qwen3.6. This release significantly improves LLM inference efficiency by reducing per-step CPU overhead through Spec Decode V2 and recovering cache hit rates in disaggregated deployments. The modernized CUDA and PyTorch defaults unlock newer kernel optimizations, benefiting the entire SGLang user base. Speculative Decoding V2 is now default, using overlap scheduling to hide CPU overhead for EAGLE/MTP/DFLASH paths. The decode radix cache for PD disaggregation enables prefix caching on decode nodes, reducing time-to-first-token for shared prefixes.

github · Kangyan-Zhou · May 5, 21:28

**Background**: SGLang is an open-source inference engine for large language models (LLMs) that focuses on performance and flexibility. Speculative decoding is a technique that uses a smaller draft model to propose tokens, verified by the larger base model, to speed up generation without loss. Prefill-decode disaggregation separates the prefill and decode phases onto different nodes to optimize resource utilization and throughput.

<details><summary>References</summary>
<ul>
<li><a href="https://arxiv.org/abs/2510.13161">[2510.13161] Mirror Speculative Decoding: Breaking the Serial ...</a></li>
<li><a href="https://docs.ray.io/en/latest/serve/llm/architecture/serving-patterns/prefill-decode.html">Prefill-decode disaggregation — Ray 2.54.1</a></li>

</ul>
</details>

**Tags**: `#SGLang`, `#LLM inference`, `#speculative decoding`, `#radix cache`, `#CUDA`

---

<a id="item-2"></a>
## [DNSSEC disruption for .de domains resolved after misconfiguration](https://status.denic.de/pages/incident/592577eab611ce1e0d00046f/69fa60ef9d12f5057a974f38) ⭐️ 8.0/10

A DNSSEC misconfiguration caused widespread resolution failures for .de domains, which was subsequently resolved by DENIC. The incident affected validating resolvers globally, causing SERVFAIL responses for all .de names. This incident highlights real-world operational challenges with DNSSEC, affecting a major country-code top-level domain (.de). It underscores the fragility of DNSSEC deployment and the importance of rigorous testing before publishing zone changes. The issue was that DENIC published an RRSIG over an NSEC3 record that did not validate against the zone's ZSK (keytag 33834), causing all validating resolvers to return SERVFAIL. Cloudflare temporarily disabled DNSSEC validation on its 1.1.1.1 resolver as a workaround.

hackernews · warpspin · May 5, 20:16 · [Discussion](https://news.ycombinator.com/item?id=48027897)

**Background**: DNSSEC (DNS Security Extensions) adds cryptographic signatures to DNS records to allow resolvers to verify their authenticity and integrity. When a DNSSEC-signed zone contains an invalid signature, validating resolvers will refuse to answer with a SERVFAIL error, causing all domains under that zone to become unreachable for users relying on validation. The incident affected .de domains served by DENIC, the German registry.

<details><summary>References</summary>
<ul>
<li><a href="https://www.cloudflare.com/learning/dns/dnssec/how-dnssec-works/">How does DNSSEC work? - Cloudflare</a></li>

</ul>
</details>

**Discussion**: The community quickly identified the root cause as a DNSSEC misconfiguration, not a nameserver outage. Some comments joked about the DENIC team being at a party, while others noted that Cloudflare disabled DNSSEC validation on 1.1.1.1. A user suggested that DNSSEC operations should be tackled with formal methods to prevent such issues.

**Tags**: `#DNSSEC`, `#DNS`, `#outage`, `#.de`, `#incident`

---

<a id="item-3"></a>
## [Gemma 4 Gets 3x Faster Inference with Multi-Token Prediction Drafters](https://blog.google/innovation-and-ai/technology/developers-tools/multi-token-prediction-gemma-4/) ⭐️ 8.0/10

Google released Multi-Token Prediction (MTP) drafters for the Gemma 4 family, enabling up to 3x faster inference without quality degradation compared to standard decoding. This advance significantly reduces latency for Gemma 4 models, making them more practical for real-time applications and local deployment, while preserving output quality. The drafters use speculative decoding: a smaller draft model predicts multiple tokens in the time the main model takes for one, then verifies them in a single forward pass.

hackernews · amrrs · May 5, 16:14 · [Discussion](https://news.ycombinator.com/item?id=48024540)

**Background**: Speculative decoding is an inference optimization that generates multiple tokens per step using a fast draft model and a slower target model. A small draft model proposes candidate tokens, and the target model verifies them in parallel, preserving the original distribution. This technique can cut latency by 2-3x without accuracy loss, similar to speculative execution in CPUs.

<details><summary>References</summary>
<ul>
<li><a href="https://blog.google/innovation-and-ai/technology/developers-tools/multi-token-prediction-gemma-4/">Accelerating Gemma 4: faster inference with multi-token prediction drafters</a></li>
<li><a href="https://en.wikipedia.org/wiki/Speculative_decoding">Speculative decoding</a></li>
<li><a href="https://aitoolly.com/ai-news/article/2026-05-06-google-boosts-gemma-4-performance-multi-token-prediction-drafters-deliver-3x-faster-inference">Google Gemma 4 MTP Drafters: 3x Faster AI Inference Speed | AIToolly</a></li>

</ul>
</details>

**Discussion**: Community members praised speculative decoding as clever and effective, noting that Gemma models use fewer tokens per output than competitors. Some discussed practical challenges like fitting the model and drafter into 24GB VRAM, while others reported progress integrating MTP support into llama.cpp.

**Tags**: `#gemma`, `#speculative decoding`, `#inference optimization`, `#AI`, `#multi-token prediction`

---

<a id="item-4"></a>
## [Computer Use 45x More Expensive Than Structured APIs](https://reflex.dev/blog/computer-use-is-45x-more-expensive-than-structured-apis/) ⭐️ 8.0/10

A new analysis from Reflex.dev shows that using AI vision agents to perform UI interactions costs 45 times more than using structured APIs, based on a direct comparison of a multi-step workflow. This cost disparity highlights a critical trade-off in AI agent design: while computer vision agents offer flexibility for interacting with arbitrary UIs, structured APIs provide dramatically lower costs for well-defined tasks, making API-based approaches far more scalable for enterprise automation. The analysis compared a 14-step walkthrough using a vision agent versus a structured API call with explicit instructions; each step with the vision agent consumed significantly more tokens and compute, leading to the 45x cost multiplier.

hackernews · palashawas · May 5, 16:34 · [Discussion](https://news.ycombinator.com/item?id=48024859)

**Background**: Computer use, or vision-based UI automation, relies on AI models to interpret screenshots and generate actions like mouse clicks, which is computationally expensive. In contrast, structured APIs expose direct programmatic interfaces that return data in a predictable format without rendering a visual interface, making them far cheaper and faster for known operations.

<details><summary>References</summary>
<ul>
<li><a href="https://reflex.dev/blog/computer-use-is-45x-more-expensive-than-structured-apis/">Computer use is 45x More Expensive Than Structured APIs</a></li>
<li><a href="https://aitoolly.com/ai-news/article/2026-05-06-the-45x-cost-penalty-why-ai-vision-agents-struggle-against-structured-apis-in-new-benchmarks">AI Vision Agents vs APIs: A 45x Cost Difference Analysis</a></li>
<li><a href="https://www.nngroup.com/articles/ai-agents-as-users/">AI Agents as Users - NN/G</a></li>

</ul>
</details>

**Discussion**: Hacker News commenters noted that adversarial UI design could intentionally drive up costs for agents, while others argued that well-designed backends with decoupled APIs eliminate the need for vision-based interaction entirely, and some suggested using accessibility APIs as a middle ground.

**Tags**: `#AI agents`, `#cost analysis`, `#APIs`, `#computer vision`, `#Hacker News`

---

<a id="item-5"></a>
## [Three Inverse Laws of AI Challenge Human-AI Interaction](https://susam.net/inverse-laws-of-robotics.html) ⭐️ 8.0/10

A new article proposes three 'inverse laws of AI' that direct human behavior when interacting with AI systems: do not anthropomorphize, do not blindly trust outputs, and do not defer responsibility to AI. This framework directly addresses the growing concerns about over-reliance and emotional attachment to AI, sparking critical discussions on AI ethics, trust, and human accountability. The laws are intended for humans, not AI, and contrast with Asimov's classic three laws for robots. The article acknowledges that following these laws may be difficult due to innate human tendencies to anthropomorphize and trust.

hackernews · blenderob · May 5, 15:27 · [Discussion](https://news.ycombinator.com/item?id=48023861)

**Background**: Isaac Asimov's Three Laws of Robotics are fictional rules designed to ensure robots behave safely towards humans. The inverse laws flip the perspective, focusing on human responsibility rather than machine constraints, highlighting the need for human vigilance in an AI-augmented world.

<details><summary>References</summary>
<ul>
<li><a href="https://susam.net/inverse-laws-of-robotics.html">Three Inverse Laws of AI and Robotics</a></li>
<li><a href="https://news.ycombinator.com/item?id=48023861">Three Inverse Laws of AI | Hacker News</a></li>

</ul>
</details>

**Discussion**: Community reactions are mixed. Some commenters argue that anthropomorphism is inevitable and that humans will always trust AI, making the laws impractical. Others agree with the principles but question their enforceability, noting that providers incentivize anthropomorphic behavior and that blind trust is difficult to avoid.

**Tags**: `#AI`, `#ethics`, `#anthropomorphism`, `#human-computer interaction`, `#robotics`

---

<a id="item-6"></a>
## [Why Most Product Tours Get Skipped](https://productonboarding.com/articles/why-product-tours-get-skipped) ⭐️ 8.0/10

A new analysis explores why users skip product tours and argues for just-in-time, contextual onboarding inspired by game design patterns. This matters because effective onboarding is critical for user retention and satisfaction; many products lose users due to intrusive, untimely tours. The article compares product tour fatigue to cookie consent dialogs, and highlights game design patterns such as progressive disclosure and contextual hints that respect user intent.

hackernews · pancomplex · May 5, 21:05 · [Discussion](https://news.ycombinator.com/item?id=48028546)

**Background**: Product tours are step-by-step introductions to an app's features, often shown on first use. Just-in-time onboarding delivers help exactly when users need it, instead of upfront. Game design patterns like incremental tutorials and contextual tooltips reduce overwhelm and keep users engaged.

<details><summary>References</summary>
<ul>
<li><a href="https://www.disco.co/blog/how-to-build-just-in-time-onboarding-paths-with-ai">How to Build Just-in-Time Onboarding Paths with AI - disco.co</a></li>
<li><a href="https://www.numberanalytics.com/blog/onboarding-in-game-design-ultimate-guide">Onboarding in Game Design - numberanalytics.com</a></li>

</ul>
</details>

**Discussion**: Commenters express strong dislike for product tours, comparing them to intrusive cookie consent dialogs. Some draw parallels to game tutorials, noting incremental games like 'Universal Paperclips' reveal mechanics gradually, suggesting similar patterns could work in apps. The sentiment is overwhelmingly negative towards forced onboarding.

**Tags**: `#UX`, `#product design`, `#onboarding`, `#user behavior`

---

<a id="item-7"></a>
## [Google Chrome silently installs 4GB AI model without consent](https://www.thatprivacyguy.com/blog/chrome-silent-nano-install/) ⭐️ 8.0/10

Google Chrome has been discovered silently downloading a 4GB AI model, Gemini Nano, onto user devices without explicit consent, enabling on-device generative AI features like the Prompt API. This raises serious privacy and resource concerns as it consumes significant bandwidth and disk space without user awareness, especially for administrators managing shared or lab environments. The model is approximately 2.7 GiB for CPU and 4.0 GiB for GPU, and is downloaded when Chrome flags like #optimization-guide-on-device-model and #prompt-api-for-gemini-nano are enabled, often as part of Origin Trials.

hackernews · john-doe · May 5, 07:34 · [Discussion](https://news.ycombinator.com/item?id=48019219)

**Background**: Gemini Nano is a compact version of Google's Gemini family of large language models, designed to run on-device without an internet connection, offering generative AI capabilities within apps. Chrome's auto-update mechanism has traditionally downloaded new features without separate consent, but the large size of this AI model has sparked debate about what constitutes acceptable background updates.

<details><summary>References</summary>
<ul>
<li><a href="https://en.wikipedia.org/wiki/Gemini_Nano">Gemini Nano</a></li>
<li><a href="https://en.wikipedia.org/wiki/Gemini_(language_model)">Gemini (language model) - Wikipedia</a></li>
<li><a href="https://developer.android.com/ai/gemini-nano">Gemini Nano | AI | Android Developers</a></li>

</ul>
</details>

**Discussion**: Some commenters argue that downloading AI models is no different from downloading spell-check dictionaries and is covered by the initial consent to install Chrome, while others highlight the administrative burden in shared environments where the model may be repeatedly downloaded, wasting bandwidth and storage.

**Tags**: `#Chrome`, `#AI`, `#privacy`, `#consent`, `#Gemini Nano`

---

<a id="item-8"></a>
## [Redis Array Playground: Test New Data Type in Browser](https://simonwillison.net/2026/May/4/redis-array/#atom-everything) ⭐️ 8.0/10

Simon Willison created an interactive browser-based playground that compiles a subset of Redis to WebAssembly, allowing users to test the proposed Redis array data type commands from Salvatore Sanfilippo's pull request. This new array data type could significantly extend Redis's capabilities for structured data processing, especially for AI agents and server-side pattern matching. The playground enables developers to experiment with the feature before it is merged into the main Redis codebase. The playground supports 18 new AR commands, including ARGREP which leverages the TRE regex library for server-side grep-like searches. The WASM build runs entirely in the browser, requiring no server setup.

rss · Simon Willison · May 4, 15:53

**Background**: Redis is an in-memory data structure store widely used for caching, messaging, and real-time analytics. Currently, Redis supports data types such as strings, lists, sets, and hashes. The proposed array type introduces ordered, indexable collections with advanced operations like range queries and regular expression matching. Compiling Redis to WebAssembly allows running native C code in the browser, enabling interactive testing without deploying a server instance.

<details><summary>References</summary>
<ul>
<li><a href="https://antirez.com/news/164">Redis array type: short story of a long development</a></li>
<li><a href="https://madewithwebassembly.com/showcase/redis/">Redis - Made with WebAssembly</a></li>
<li><a href="https://redis.io/docs/latest/develop/data-types/">Redis data types | Docs</a></li>

</ul>
</details>

**Tags**: `#Redis`, `#data structures`, `#development tools`, `#WASM`

---

<a id="item-9"></a>
## [GitHub Apologizes for Outages, Reveals 30x Scaling Plan](https://github.blog/news-insights/company-news/an-update-on-github-availability/) ⭐️ 8.0/10

GitHub CTO Vlad Fedorov issued a post-mortem and scaling plan after April outages, including migrating performance-sensitive code from Ruby to Go, offloading MySQL database loads, and moving from custom data centers to Azure multi-cloud architecture. This transparency from GitHub is significant for the developer community, as it details major infrastructure shifts that will improve reliability and scalability, affecting millions of users and repositories. Two specific incidents were detailed: on April 23, a merge queue bug affected 658 repositories causing incorrect squashes and reverts, and on April 27, an Elasticsearch cluster overload (possibly an attack) made search unavailable, though core Git operations were unaffected.

telegram · zaihuapd · May 5, 11:42

**Background**: GitHub has historically relied on a Ruby on Rails monolith and MySQL for its core services. As the platform grows, especially with AI-driven workloads, scaling challenges have emerged, prompting a shift to Go for performance-sensitive parts and a move to multi-cloud for resilience. The 30x scaling plan aims to accommodate future growth.

**Tags**: `#GitHub`, `#Infrastructure`, `#Scaling`, `#Cloud Migration`, `#Go`

---

<a id="item-10"></a>
## [Google DeepMind London Workers Vote to Unionize Over Military AI](https://www.theverge.com/tech/923918/google-deepmind-union-bid-ai-military-israel) ⭐️ 8.0/10

Over 1,000 Google DeepMind employees in London voted to form a union to protest military AI contracts with the U.S. Department of Defense and the Israeli government. This action highlights growing ethical concerns among AI workers about military applications and could pressure Google to adopt stricter ethical guidelines and employee protections. Employees demand a commitment from Google not to develop weapons or surveillance tech, establish independent ethics oversight, and grant the right to refuse projects on moral grounds.

telegram · zaihuapd · May 5, 12:36

**Background**: Project Nimbus is a $1.2 billion cloud computing contract between Israel and Google and Amazon to provide AI and cloud services to the Israeli government. In 2024, Google fired over 50 employees who protested Project Nimbus. The Pentagon also recently confirmed agreements with Google, OpenAI, Nvidia, and SpaceX for use of AI models by the U.S. military.

<details><summary>References</summary>
<ul>
<li><a href="https://en.wikipedia.org/wiki/Project_Nimbus">Project Nimbus - Wikipedia</a></li>

</ul>
</details>

**Tags**: `#AI ethics`, `#military AI`, `#Google`, `#DeepMind`, `#labor rights`

---

<a id="item-11"></a>
## [Microsoft Edge stores all passwords cleartext in memory during session](https://cybernews.com/security/microsoft-edge-loads-cleartext-passwords-to-memory/) ⭐️ 8.0/10

Security researcher Tom Jøran Sønstebyseter Rønning discovered that Microsoft Edge decrypts all saved passwords and stores them in cleartext memory for the entire session, even without visiting sites requiring those credentials. Unlike other Chromium browsers, Edge does not use application-bound encryption or on-demand decryption. This design choice significantly weakens password protection on Edge, allowing attackers with admin access to extract all saved credentials from process memory, including from other logged-in users on terminal servers. It highlights a fundamental security trade-off between convenience and safety in browser password managers. The vulnerability (which Microsoft acknowledges as by design) requires local admin privileges to exploit, limiting remote attack vectors. Other Chromium browsers like Chrome only decrypt passwords on-demand and leverage application-bound encryption to tie keys to the app process.

telegram · zaihuapd · May 5, 23:31

**Background**: Modern browsers offer built-in password managers that store credentials encrypted on disk. Chrome's application-bound encryption (ABE) ensures that only the Chrome process itself can decrypt the keys, preventing other apps—even with admin rights—from reading them. Edge, however, decrypts all passwords at startup and leaves them in plaintext in memory, making them accessible via memory dumping tools like Process Hacker or Volatility. This behavior was first reported by a security researcher and confirmed by Microsoft.

<details><summary>References</summary>
<ul>
<li><a href="https://chromeenterprise.google/policies/application-bound-encryption-enabled/">ApplicationBoundEncryptionEnabled: Enable Application Bound ...</a></li>
<li><a href="https://www.cyberark.com/resources/threat-research-blog/extracting-clear-text-credentials-directly-from-chromium-s-memory">Extracting Clear-Text Credentials Directly From Chromium’s Memory</a></li>

</ul>
</details>

**Tags**: `#security`, `#Microsoft Edge`, `#privacy`, `#vulnerability`, `#browser`

---

<a id="item-12"></a>
## [Anthropic commits $200B to Google Cloud over five years](https://www.theinformation.com/articles/anthropic-commits-spending-200-billion-googles-cloud-chips?utm_source=chatgpt.com) ⭐️ 8.0/10

Anthropic has committed to spend $200 billion on Google Cloud over the next five years, representing over 40% of Google Cloud's disclosed backlog. Additionally, Alphabet plans to invest up to $40 billion in Anthropic at a $350 billion valuation. This deal underscores the massive capital requirements in AI infrastructure and deepens the strategic partnership between Anthropic and Google Cloud, potentially reshaping the competitive landscape of cloud AI services. It signals that leading AI labs are securing long-term compute commitments to train and deploy advanced models. Anthropic and Google also signed an agreement with Broadcom in April to lock in multiple gigawatts of TPU compute power, expected to come online starting in 2027. The $200 billion commitment is a multi-year cloud services agreement, not a one-time payment.

telegram · zaihuapd · May 6, 03:53

**Background**: Tensor Processing Units (TPUs) are Google's custom-designed application-specific integrated circuits (ASICs) for accelerating machine learning workloads, particularly neural networks. They were launched internally in 2015 and made available on Google Cloud in 2018. TPUs are designed to work with TensorFlow and offer high efficiency for AI training and inference, competing with NVIDIA's GPUs. The huge compute commitment from Anthropic highlights the growing demand for specialized AI hardware in training large language models.

<details><summary>References</summary>
<ul>
<li><a href="https://zh.wikipedia.org/zh-hans/张量处理单元">张量处理单元 - 维基百科，自由的百科全书</a></li>

</ul>
</details>

**Tags**: `#Anthropic`, `#Google Cloud`, `#AI Infrastructure`, `#Business Deal`, `#Cloud Computing`

---

<a id="item-13"></a>
## [Apple plans to let users choose third-party AI models in iOS 27](https://www.bloomberg.com/news/articles/2026-05-05/ios-27-features-apple-plans-to-let-users-swap-models-across-apple-intelligence) ⭐️ 8.0/10

Apple plans to introduce a feature called 'Extensions' in iOS 27, iPadOS 27, and macOS 27, allowing users to select from multiple third-party AI models for tasks like text generation, image generation, and editing, breaking ChatGPT's exclusive position in Apple Intelligence. This move signifies a shift from a closed to an open AI platform, potentially reshaping the mobile AI ecosystem by giving users more choice and fostering competition among AI providers. It could also pressure other tech giants to adopt similar open strategies. The feature internally called 'Extensions' will allow third-party AI models to power Siri, Writing Tools, and Image Playground. Apple has already tested Google and Anthropic models internally, and will continue offering its own models alongside third-party options.

telegram · zaihuapd · May 6, 05:38

**Background**: Apple Intelligence, announced in June 2024, is Apple's generative AI system integrated into iOS 18 and later, offering features like writing assistance, image generation, and ChatGPT integration. Currently, ChatGPT is the only third-party model integrated into Apple Intelligence. The new Extensions feature would open the platform to multiple providers, giving users control over which AI model handles tasks.

<details><summary>References</summary>
<ul>
<li><a href="https://www.theverge.com/tech/924515/apple-intelligence-third-party-chatbot-extensions-ios-27">Apple could let you pick a favorite AI model in iOS 27 | The Verge</a></li>
<li><a href="https://www.digit.in/news/general/apple-may-allow-rival-ai-models-across-ios-27-features-what-it-means.html">Apple may allow rival AI models across iOS 27 features: What it means</a></li>
<li><a href="https://en.wikipedia.org/wiki/Apple_Intelligence">Apple Intelligence</a></li>

</ul>
</details>

**Tags**: `#Apple`, `#AI模型`, `#iOS`, `#第三方接入`, `#人工智能`

---

<a id="item-14"></a>
## [DeepSeek Reportedly in Talks for $45B Valuation Funding Round](https://www.bloomberg.com/news/articles/2026-05-06/china-chip-fund-in-talks-to-lead-mega-deepseek-funding-ft-says) ⭐️ 8.0/10

DeepSeek is reportedly in negotiations for its first major external funding round, which could value the company at approximately $45 billion, with China's National Integrated Circuit Industry Investment Fund leading the investment. This marks significant state-backed involvement in China's AI core companies, potentially signaling stronger government support for AI development and influencing the competitive landscape in the AI industry. The funding round would be DeepSeek's first major external capital raise, and the lead investor, China's state chip fund, is known for investing in semiconductor and technology companies with strategic importance.

telegram · zaihuapd · May 6, 06:28

**Background**: The National Integrated Circuit Industry Investment Fund, also known as the 'Big Fund', was established in 2014 to boost China's semiconductor industry. It has raised three phases of funds, with the third phase in 2024 having a registered capital of 344 billion yuan. DeepSeek is an AI company developing large language models, and this funding would be a major milestone for both the company and China's AI ambitions.

<details><summary>References</summary>
<ul>
<li><a href="https://zh.wikipedia.org/wiki/国家大基金">国家大基金 - 维基百科，自由的百科全书</a></li>
<li><a href="https://baike.baidu.com/item/国家集成电路产业投资基金/15891498">国家集成电路产业投资基金_百度百科</a></li>

</ul>
</details>

**Tags**: `#DeepSeek`, `#AI`, `#funding`, `#China`, `#semiconductors`

---