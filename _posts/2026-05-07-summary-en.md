---
layout: default
title: "Horizon Summary: 2026-05-07 (EN)"
date: 2026-05-07
lang: en
---

> From 35 items, 15 important content pieces were selected

---

1. [Apple Plans to Let Users Choose Third-Party AI Models](#item-1) ⭐️ 9.0/10
2. [SGLang v0.5.11: Speculative Decoding V2, CUDA 13, New Models](#item-2) ⭐️ 8.0/10
3. [Valve Open-Sources Steam Controller CAD Files](#item-3) ⭐️ 8.0/10
4. [Critique of AI-Driven Productivity Theater in the Workplace](#item-4) ⭐️ 8.0/10
5. [Vibe Coding and Agentic Engineering Converge, Raising Trust Issues](#item-5) ⭐️ 8.0/10
6. [From Supabase to Clerk to Better Auth: A Migration Story](#item-6) ⭐️ 8.0/10
7. [Google Cloud Fraud Defense: QR codes replace CAPTCHA](#item-7) ⭐️ 8.0/10
8. [Anthropic boosts Claude limits and secures compute deal with SpaceX](#item-8) ⭐️ 8.0/10
9. [Microsoft Edge Exposes All Saved Passwords in Memory Plaintext](#item-9) ⭐️ 8.0/10
10. [Meta Plans AI Assistant Powered by Muse Spark Model](#item-10) ⭐️ 8.0/10
11. [DeepSeek Reportedly Targets $45B Valuation in First Funding Round](#item-11) ⭐️ 8.0/10
12. [Chrome silently downloads 4GB AI model without permission](#item-12) ⭐️ 8.0/10
13. [EU to Mandate Removal of Huawei, ZTE Equipment](#item-13) ⭐️ 8.0/10
14. [NVIDIA, OpenAI, Microsoft Release Open MRC Protocol for AI Clusters](#item-14) ⭐️ 8.0/10
15. [Moonshot AI valuation tops $10B with new $700M funding](#item-15) ⭐️ 8.0/10

---

<a id="item-1"></a>
## [Apple Plans to Let Users Choose Third-Party AI Models](https://www.bloomberg.com/news/articles/2026-05-05/ios-27-features-apple-plans-to-let-users-swap-models-across-apple-intelligence) ⭐️ 9.0/10

Apple plans to allow users to select third-party AI models for system functions in iOS 27, iPadOS 27, and macOS 27, such as text generation, image generation, and editing. This move breaks ChatGPT's current exclusivity in Apple Intelligence. This marks a strategic shift for Apple from a single-partner AI model to an open platform, potentially giving users more choice and fostering competition among AI providers. It could significantly impact the AI ecosystem by making models like Google's and Anthropic's accessible system-wide on Apple devices. The feature is internally called 'Extensions' and will be available in a settings menu to connect third-party AI services for Siri, Writing Tools, and Image Playground. Internal testing has already covered models from Google and Anthropic.

telegram · zaihuapd · May 6, 05:38

**Background**: Apple Intelligence is Apple's generative AI system announced in June 2024, available on iOS 18, iPadOS 18, and macOS Sequoia, with features like Writing Tools, Image Playground, and ChatGPT integration. Currently, ChatGPT is the only third-party model integrated into Apple Intelligence. The new 'Extensions' feature would allow users to choose alternative models, making Apple Intelligence a platform that hosts multiple AI services.

<details><summary>References</summary>
<ul>
<li><a href="https://en.wikipedia.org/wiki/Apple_Intelligence">Apple Intelligence</a></li>
<li><a href="https://www.apple.com/apple-intelligence/">Apple Intelligence - Apple</a></li>
<li><a href="https://www.macrumors.com/guide/image-playground/">iOS 18.2: Everything You Should Know About Image Playground</a></li>

</ul>
</details>

**Tags**: `#Apple`, `#AI`, `#iOS`, `#third-party models`, `#platform strategy`

---

<a id="item-2"></a>
## [SGLang v0.5.11: Speculative Decoding V2, CUDA 13, New Models](https://github.com/sgl-project/sglang/releases/tag/v0.5.11) ⭐️ 8.0/10

SGLang v0.5.11 introduces default speculative decoding V2, upgrades to CUDA 13 and PyTorch 2.11, adds decode-side radix caching for prefill/decode disaggregation, and supports new models including Gemma 4, Qwen3.6, and Kimi-K2.6. This release significantly boosts LLM inference performance through speculative decoding improvements and updated GPU kernel support, making it easier to deploy state-of-the-art models at scale. The new features lower latency and improve throughput for both prefill and decode stages. The default CUDA version is now 13.0 across SGLang, sgl-kernel, and Docker images, with PyTorch upgraded from 2.9 to 2.11. Speculative decoding V2 uses overlap scheduling to hide CPU overhead, and the decode-side radix cache recovers hit rates for long shared prefixes in disaggregated deployments.

github · Kangyan-Zhou · May 5, 21:28

**Background**: LLM inference often separates the prefill (processing input) and decode (generating tokens) stages to optimize resource use, known as PD disaggregation. Speculative decoding uses a small draft model to predict multiple tokens at once, then verifies them in parallel with the target model, speeding up generation. Radix caching stores key-value caches for prefixes to avoid redundant computation.

<details><summary>References</summary>
<ul>
<li><a href="https://docs.vllm.ai/en/latest/features/speculative_decoding/">Speculative Decoding - vLLM</a></li>
<li><a href="https://llm-d.ai/docs/guide/Installation/pd-disaggregation">Prefill/Decode Disaggregation | llm-d</a></li>
<li><a href="https://github.com/sgl-project/sglang/issues/24544">[sglang-miles] Integrate PD decode radix cache · Issue #24544 - GitHub</a></li>

</ul>
</details>

**Tags**: `#LLM inference`, `#speculative decoding`, `#CUDA`, `#PyTorch`, `#SGLang`

---

<a id="item-3"></a>
## [Valve Open-Sources Steam Controller CAD Files](https://www.digitalfoundry.net/news/2026/05/valve-releases-steam-controller-cad-files-under-creative-commons-license) ⭐️ 8.0/10

Valve released the CAD files for the Steam Controller and Steam Controller Puck under a Creative Commons license, including STP and STL models and engineering drawings. This move empowers the community to create custom modifications, accessibility adaptations, and 3D-printed accessories, fostering an open hardware ecosystem around Steam Input. The repository includes STP (STEP) and STL models along with an engineering drawing showing critical features and keep-out zones, enabling precise modification and 3D printing.

hackernews · haunter · May 6, 15:44 · [Discussion](https://news.ycombinator.com/item?id=48037555)

**Background**: CAD (Computer-Aided Design) files contain precise 3D geometry used for manufacturing and 3D printing. The Creative Commons license allows free use, modification, and sharing with attribution. Open-source hardware principles encourage community collaboration on physical designs, similar to open-source software.

<details><summary>References</summary>
<ul>
<li><a href="https://en.wikipedia.org/wiki/Open-source_hardware">Open-source hardware - Wikipedia</a></li>

</ul>
</details>

**Discussion**: Comments are largely positive, with users praising the friendly readme and highlighting benefits for disabled gamers who need custom controller modifications. However, some express concern that the controller only works within Steam, potentially creating a walled garden.

**Tags**: `#open hardware`, `#valve`, `#steam controller`, `#3d printing`, `#accessibility`

---

<a id="item-4"></a>
## [Critique of AI-Driven Productivity Theater in the Workplace](https://nooneshappy.com/article/appearing-productive-in-the-workplace/) ⭐️ 8.0/10

An article highlights how workplace documents and updates are becoming unnecessarily long, and AI tools are being used to create an illusion of productivity without actual output improvement. This critique resonates deeply as it exposes the growing trend of pseudo-productivity driven by AI, which could lead to misallocation of resources and hinder genuine innovation in the tech industry. The article notes that requirement documents expanded from one page to twelve, and status updates became bulleted summaries of summaries, all produced by people who do not read what they write, for readers who do not read what they receive.

hackernews · diebillionaires · May 6, 16:18 · [Discussion](https://news.ycombinator.com/item?id=48038001)

**Background**: In many workplaces, 'productivity theater' refers to activities that make employees look busy without contributing to real output. With the rise of AI tools like LLMs, workers can generate large volumes of text or code quickly, potentially masking a lack of substantive progress. This phenomenon is especially prevalent in corporate and tech cultures that reward visible effort over actual results.

**Discussion**: Community members strongly agreed with the critique, sharing personal experiences of AI mandated usage with no throughput improvement and of over-engineered architectures praised by non-technical management. One commenter noted that LLMs have automated 'sucking up to management'.

**Tags**: `#workplace productivity`, `#AI tools`, `#over-engineering`, `#corporate culture`, `#tech industry`

---

<a id="item-5"></a>
## [Vibe Coding and Agentic Engineering Converge, Raising Trust Issues](https://simonwillison.net/2026/May/6/vibe-coding-and-agentic-engineering/#atom-everything) ⭐️ 8.0/10

Simon Willison, a prominent software engineer, reveals that in his own work, vibe coding and agentic engineering are blurring together as AI coding agents become more reliable, leading him to sometimes skip reviewing AI-generated code even for production systems. This convergence challenges the previously clear distinction between irresponsible vibe coding and responsible agentic engineering, raising critical questions about trust, quality, and accountability in AI-assisted software development. Willison notes that for tasks like building a JSON API endpoint, he trusts Claude Code to do it correctly without review, but feels guilt about not reviewing code for production; he draws an analogy to trusting code from other teams in large organizations.

rss · Simon Willison · May 6, 14:24 · [Discussion](https://news.ycombinator.com/item?id=48037128)

**Background**: Vibe coding, coined by Andrej Karpathy, refers to using AI to generate code by describing intent in plain language without deeply understanding the code. Agentic engineering, also popularized by Karpathy, involves professional developers using coding agents like Claude Code, OpenAI Codex, or Gemini CLI as assistants while maintaining responsibility for quality and security.

<details><summary>References</summary>
<ul>
<li><a href="https://en.wikipedia.org/wiki/Vibe_coding">Vibe coding - Wikipedia</a></li>
<li><a href="https://www.ibm.com/think/topics/agentic-engineering">What is agentic engineering? - IBM</a></li>
<li><a href="https://simonwillison.net/guides/agentic-engineering-patterns/what-is-agentic-engineering/">What is agentic engineering? - Agentic Engineering Patterns</a></li>

</ul>
</details>

**Discussion**: Community comments express skepticism: jwpapi doubts that AI always gets it right, noting many design decisions are needed; zarzavat warns that AI errors become more subtle rather than disappearing; etothet argues that undisciplined engineering existed before LLMs, which just accelerate it; devin criticizes the use of lines of code as a metric; Havoc suggests it's a spectrum rather than a binary distinction.

**Tags**: `#vibe coding`, `#agentic engineering`, `#AI coding tools`, `#software engineering`, `#LLM`

---

<a id="item-6"></a>
## [From Supabase to Clerk to Better Auth: A Migration Story](https://blog.val.town/better-auth) ⭐️ 8.0/10

A developer details their migration from third-party auth providers Supabase and Clerk to the open-source Better Auth framework, sparking community debate on authentication outsourcing. Authentication is a critical but often complex part of web apps, and this discussion highlights the trade-offs between ease of use with third-party services versus control and cost with self-hosted solutions. Better Auth is a framework-agnostic, open-source authentication library for TypeScript with a plugin ecosystem, aiming to simplify self-hosted auth. The migration involved moving from Clerk, a paid auth service, to Better Auth.

hackernews · stevekrouse · May 6, 17:19 · [Discussion](https://news.ycombinator.com/item?id=48038827)

**Background**: Many web developers use third-party authentication services like Clerk or Supabase Auth to save time, but concerns about vendor lock-in, costs, and data control drive some to self-hosted solutions. Better Auth offers an open-source alternative that can be deployed on one's own infrastructure.

<details><summary>References</summary>
<ul>
<li><a href="https://better-auth.com/">Better Auth</a></li>
<li><a href="https://clerk.com/">Clerk | Authentication and User Management</a></li>

</ul>
</details>

**Discussion**: Comments varied: some defended rolling custom auth for full control, others questioned the need for third-party services. The creator of Better Auth (bekacru) responded positively, noting the project grew from personal need into a company.

**Tags**: `#authentication`, `#web development`, `#self-hosting`, `#third-party services`, `#better-auth`

---

<a id="item-7"></a>
## [Google Cloud Fraud Defense: QR codes replace CAPTCHA](https://cloud.google.com/blog/products/identity-security/introducing-google-cloud-fraud-defense-the-next-evolution-of-recaptcha/) ⭐️ 8.0/10

Google Cloud has introduced Fraud Defense, the next evolution of reCAPTCHA, which replaces traditional image and audio challenges with a QR code that users scan with their mobile device to verify they are human. This change addresses the growing ability of AI bots to solve visual CAPTCHAs, but it introduces significant accessibility, privacy, and security concerns, potentially excluding users without modern mobile devices and raising risks of de-anonymization and QR code phishing. The QR code challenge requires a modern Android device with Google Play Services or an iPhone/iPad, and existing reCAPTCHA customers are automatically upgraded to Fraud Defense with no action needed. Google claims the new system simplifies the user experience, but critics point to the mandatory mobile device requirement and potential for device fingerprinting.

hackernews · unforgivenpasta · May 6, 17:59 · [Discussion](https://news.ycombinator.com/item?id=48039362)

**Background**: CAPTCHAs are tests designed to distinguish human users from automated bots. Google's reCAPTCHA has evolved from distorted text to image recognition to invisible risk analysis, but AI advancements have made these challenges increasingly solvable by bots. Google's new Fraud Defense platform aims to secure the 'agentic web' by using mobile device scanning as a more robust verification method, though QR codes themselves are increasingly exploited in phishing attacks.

<details><summary>References</summary>
<ul>
<li><a href="https://cloud.google.com/blog/products/identity-security/introducing-google-cloud-fraud-defense-the-next-evolution-of-recaptcha/">Introducing Google Cloud Fraud Defense, the next evolution of reCAPTCHA | Google Cloud Blog</a></li>
<li><a href="https://www.heise.de/en/news/Instead-of-picture-puzzles-Google-introduces-QR-code-challenge-against-AI-bots-11273871.html">Instead of picture puzzles: Google introduces QR code challenge against AI bots | heise online</a></li>

</ul>
</details>

**Discussion**: Commenters expressed strong concerns: one noted that the requirement for a modern mobile device with Google Play Services effectively excludes users of custom ROMs like LineageOS and raises de-anonymization risks. Another highlighted accessibility issues, especially for blind users who struggle with current audio challenges. Others warned about QR code security, comparing blind scanning to running 'curl $URL | bash', and noted that QR code phishing attacks are surging.

**Tags**: `#recaptcha`, `#fraud defense`, `#google cloud`, `#security`, `#privacy`

---

<a id="item-8"></a>
## [Anthropic boosts Claude limits and secures compute deal with SpaceX](https://www.anthropic.com/news/higher-limits-spacex) ⭐️ 8.0/10

Anthropic announced higher usage limits for Claude, including doubled 5-hour rate limits for Claude Code and lifted peak-hour restrictions for Pro and Max users, along with increased API rate limits for Claude Opus. The company also signed a compute deal with SpaceX to access over 300 megawatts of capacity and 220,000+ NVIDIA GPUs at the Colossus 1 data center, with plans to explore orbital AI compute capacity. This deal directly enhances Claude's performance and availability for users, while the partnership with SpaceX underscores the immense compute demands of cutting-edge AI and the emergence of orbital data centers as a potential future infrastructure. It also signals Anthropic's aggressive push to scale its AI capabilities despite environmental concerns surrounding Colossus 1. The compute deal provides Anthropic with over 300 megawatts of new capacity and more than 220,000 NVIDIA GPUs from SpaceX's Colossus 1 supercomputer. As part of the agreement, Anthropic expressed interest in jointly developing multiple gigawatts of orbital AI compute capacity with SpaceX, though specific timelines remain unspecified.

hackernews · meetpateltech · May 6, 16:17 · [Discussion](https://news.ycombinator.com/item?id=48037986)

**Background**: Colossus 1 is a massive supercomputer built by Elon Musk for xAI's Grok, located in Memphis, Tennessee. It has been controversial due to its use of unauthorized power connections and environmental concerns in nearby communities. AI models like Claude require enormous computational resources for training and inference, leading companies like Anthropic to seek large-scale compute partnerships with data center operators like SpaceX.

<details><summary>References</summary>
<ul>
<li><a href="https://www.techrepublic.com/article/news-anthropic-spacex-claude-compute-colossus-1/">Anthropic, SpaceX Deal Boosts Claude Compute and Points to ...</a></li>
<li><a href="https://dev.to/mcrolly/anthropic-strikes-compute-deal-with-spacex-what-it-means-for-the-future-of-ai-1moj">Anthropic strikes compute deal with SpaceX — what it means ...</a></li>
<li><a href="https://www.coindesk.com/tech/2026/05/06/anthropic-signs-elon-musk-s-spacex-for-colossus-1-compute-ahead-of-june-ipo">Anthropic signs Elon Musk's SpaceX for Colossus 1 compute ...</a></li>

</ul>
</details>

**Discussion**: Community comments highlight irony in Anthropic using a data center built for xAI's Grok, and amazement at the scale of 300 MW and 220,000 GPUs. Environmental concerns are raised about Colossus 1's illegal power usage and pollution, with some criticizing Anthropic's safety rhetoric. One commenter notes that doubling the 5-hour limit is a marketing stunt if weekly limits remain unchanged.

**Tags**: `#AI`, `#Anthropic`, `#Claude`, `#SpaceX`, `#Compute`

---

<a id="item-9"></a>
## [Microsoft Edge Exposes All Saved Passwords in Memory Plaintext](https://cybernews.com/security/microsoft-edge-loads-cleartext-passwords-to-memory/) ⭐️ 8.0/10

Security researcher Tom Jøran Sønstebyseter Rønning discovered that Microsoft Edge decrypts and loads all saved passwords into memory in plaintext at startup, keeping them exposed throughout the entire browsing session. This behavior significantly increases the risk of credential theft for users who have saved passwords in Edge, as any malware or attacker with administrative access can easily read the plaintext passwords from memory, unlike other Chromium browsers that only decrypt passwords on demand. The vulnerability affects all versions of Microsoft Edge and persists even if the user never visits websites that require those credentials. Microsoft has acknowledged the issue and stated that this is by design.

telegram · zaihuapd · May 5, 23:31

**Background**: Most modern browsers, including Google Chrome, use application-bound encryption to protect saved passwords, decrypting them only when needed. The encryption keys are bound to the browser's identity, preventing other apps from accessing them. Microsoft Edge, despite being based on Chromium, deviates from this standard by decrypting all passwords at startup and keeping them in memory, making them vulnerable to memory-scraping attacks.

<details><summary>References</summary>
<ul>
<li><a href="https://cybernews.com/security/microsoft-edge-loads-cleartext-passwords-to-memory/">Edge keeps unencrypted passwords in memory | Cybernews</a></li>
<li><a href="https://www.forbes.com/sites/daveywinder/2026/05/06/microsoft-says-edge-password-security-vulnerability-is-by-design-is-it-time-to-switch-to-chrome/">Microsoft Says Edge Password Security Vulnerability Is ‘By ...</a></li>
<li><a href="https://learn.microsoft.com/en-us/deployedge/microsoft-edge-browser-policies/applicationboundencryptionenabled">Microsoft Edge Browser Policy Documentation ...</a></li>

</ul>
</details>

**Tags**: `#security`, `#Microsoft Edge`, `#password management`, `#vulnerability`, `#memory safety`

---

<a id="item-10"></a>
## [Meta Plans AI Assistant Powered by Muse Spark Model](https://www.ft.com/content/5b48360c-53f2-444a-80a8-f7034750fd62?syn-25a6b1a6=1) ⭐️ 8.0/10

Meta is developing a personalized AI agent for its 3 billion users, powered by the new Muse Spark model, with capabilities similar to the open-source OpenClaw project, and it is currently in internal testing. This move positions Meta to compete with major AI assistants, potentially leveraging its massive user base while facing investor pressure over rising capital expenditure on AI. Users can choose whether to share sensitive information like health and financial data with the assistant. Meta raised its 2026 capital expenditure by $10 billion to up to $145 billion, leading to a significant stock drop.

telegram · zaihuapd · May 6, 03:00

**Background**: Muse Spark is Meta's first major AI model from its Superintelligence Labs, announced in April 2026, aimed at personal superintelligence. OpenClaw is an open-source personal AI assistant framework that can time-block tasks, generate invoices, and more.

<details><summary>References</summary>
<ul>
<li><a href="https://ai.meta.com/blog/introducing-muse-spark-msl/">Introducing Muse Spark: Scaling Towards Personal Superintelligence</a></li>
<li><a href="https://about.fb.com/news/2026/04/introducing-muse-spark-meta-superintelligence-labs/">Introducing Muse Spark: Meta's Most Powerful Model Yet</a></li>
<li><a href="https://en.wikipedia.org/wiki/OpenClaw">OpenClaw - Wikipedia</a></li>

</ul>
</details>

**Tags**: `#Meta`, `#AI Assistant`, `#Open Source`, `#Capital Expenditure`

---

<a id="item-11"></a>
## [DeepSeek Reportedly Targets $45B Valuation in First Funding Round](https://www.bloomberg.com/news/articles/2026-05-06/china-chip-fund-in-talks-to-lead-mega-deepseek-funding-ft-says) ⭐️ 8.0/10

DeepSeek, a Chinese AI startup, is reportedly in talks for its first external funding round led by China's National Integrated Circuit Industry Investment Fund, with a valuation around $45 billion. This funding round would mark a significant milestone for DeepSeek as it transitions from internal funding to external investment, and the involvement of a state-backed fund highlights the Chinese government's strategic support for domestic AI champions amidst global tech competition. The reported valuation of up to $50 billion makes DeepSeek one of the most valuable AI startups globally. DeepSeek, founded in July 2023 by Liang Wenfeng and owned by hedge fund High-Flyer, has not raised external capital before.

telegram · zaihuapd · May 6, 06:28

**Background**: DeepSeek is a Chinese AI company based in Hangzhou, known for its large language models and chatbot launched in January 2025. The National Integrated Circuit Industry Investment Fund, also called the Big Fund, is a state-backed investment vehicle established to boost China's semiconductor and technology self-sufficiency, with over $47 billion in its third phase.

<details><summary>References</summary>
<ul>
<li><a href="https://www.reuters.com/world/asia-pacific/deepseek-nears-45-billion-valuation-chinas-big-fund-leads-investment-talks-ft-2026-05-06/">DeepSeek could be valued at up to $50 billion in first ...</a></li>
<li><a href="https://en.wikipedia.org/wiki/China_Integrated_Circuit_Industry_Investment_Fund">China Integrated Circuit Industry Investment Fund - Wikipedia</a></li>

</ul>
</details>

**Tags**: `#AI`, `#Funding`, `#DeepSeek`, `#China`

---

<a id="item-12"></a>
## [Chrome silently downloads 4GB AI model without permission](https://www.tomshardware.com/tech-industry/cyber-security/google-chrome-silently-downloads-4gb-ai-model-to-your-device-without-permission-report-claims-researcher-says-practice-may-violate-eu-law-waste-thousands-of-kilowatts-of-energy) ⭐️ 8.0/10

Security researcher Alexander Hanff revealed that Google Chrome automatically downloads the 4GB Gemini Nano AI model (weights.bin) to users' devices without consent, and the file is re-downloaded even if manually deleted. This practice potentially violates EU GDPR and other privacy laws, wastes bandwidth and energy—estimated at 60,000 tons of carbon emissions if deployed to 1 billion users—and undermines user control over their devices. The model is stored in the OptGuideOnDeviceModel directory within Chrome's user profile. The download triggers only on devices meeting hardware requirements, and no opt-in prompt is shown.

telegram · zaihuapd · May 6, 11:15

**Background**: Gemini Nano is Google's on-device AI model designed for tasks like text generation without needing a network connection. Google has been integrating AI features into Chrome, but this silent deployment has sparked significant privacy and environmental concerns.

<details><summary>References</summary>
<ul>
<li><a href="https://www.tomshardware.com/tech-industry/cyber-security/google-chrome-silently-downloads-4gb-ai-model-to-your-device-without-permission-report-claims-researcher-says-practice-may-violate-eu-law-waste-thousands-of-kilowatts-of-energy">Google Chrome 'silently' downloads 4GB AI model to your device without permission, report claims — researcher says practice may violate EU law, waste thousands of kilowatts of energy | Tom's Hardware</a></li>

</ul>
</details>

**Tags**: `#privacy`, `#chrome`, `#AI`, `#GDPR`, `#ethics`

---

<a id="item-13"></a>
## [EU to Mandate Removal of Huawei, ZTE Equipment](https://t.me/zaihuapd/41247) ⭐️ 8.0/10

The European Commission is considering new regulations that would compel all EU member states to remove equipment from Huawei and ZTE from their telecommunications and broadband infrastructure, upgrading previous non-binding advice to enforceable law. This would significantly impact global telecom supply chains and escalate geopolitical tensions, potentially forcing other countries to follow suit. It also underscores the EU's push for digital sovereignty and cybersecurity. If enacted, member states that fail to remove the equipment by a deadline could face investigations and financial penalties. Additionally, the EU plans to tighten external infrastructure funding, halting loans for non-EU countries using Huawei equipment.

telegram · zaihuapd · May 6, 14:00

**Background**: In 2020, the EU issued a non-binding '5G Security Toolbox' that recommended limiting high-risk vendors. However, it lacked legal force. The new regulation would make those recommendations mandatory, reflecting growing concerns over espionage and supply chain security, despite Chinese denials.

<details><summary>References</summary>
<ul>
<li><a href="https://www.lexology.com/library/detail.aspx?g=656444e9-e0b8-4e33-9f7f-e2d16624bbc3">The EU’s “High-Risk Vendor” Designation for Chinese 5G Equipment Suppliers - Proposed EU-Wide Ban of Huawei and ZTE Elevates Geopolitics Over Technical Risk Assessment - Lexology</a></li>
<li><a href="https://digital-strategy.ec.europa.eu/en/library/eu-toolbox-5g-security">The EU toolbox for 5G security - Shaping Europe’s digital ...</a></li>
<li><a href="https://commission.europa.eu/topics/international-partnerships/global-gateway_en">Global Gateway - European Commission</a></li>

</ul>
</details>

**Tags**: `#geopolitics`, `#telecom`, `#Huawei`, `#EU regulation`, `#cybersecurity`

---

<a id="item-14"></a>
## [NVIDIA, OpenAI, Microsoft Release Open MRC Protocol for AI Clusters](https://blogs.nvidia.com/blog/spectrum-x-ethernet-mrc/) ⭐️ 8.0/10

NVIDIA, OpenAI, Microsoft, and others jointly released and open-sourced the Multi-path Reliable Connection (MRC) protocol, a new RDMA transport designed for AI supercomputing clusters. MRC addresses key bottlenecks in large-scale AI training by using packet spraying to fully utilize multiple network paths, reducing GPU idle time and improving cluster throughput and stability. The protocol supports microsecond-level fault rerouting and is already deployed in NVIDIA Spectrum-X platforms and Blackwell architecture, powering clusters like Microsoft Fairwater and Oracle OCI Abilene for GPT-5.5 training.

telegram · zaihuapd · May 6, 14:39

**Background**: In large-scale AI training, Ethernet-based RDMA (RoCE) often suffers from congestion hotspots and load imbalance due to low entropy traffic. MRC is a transport protocol that distributes packets across multiple paths simultaneously, improving goodput and reliability. It is being standardized as an Open Compute Project (OCP) specification to reduce industry fragmentation.

<details><summary>References</summary>
<ul>
<li><a href="https://www.broadcom.com/blog/enabling-ai-networking-scale-with-multi-path-reliable-connections-mrc">Enabling AI Networking @ Scale with Multi-path Reliable Connections ...</a></li>
<li><a href="https://www.amd.com/en/blogs/2026/amd-advances-ai-networking-at-scale-with-mrc.html">AMD and OpenAI Advance AI Networking at Scale with MRC</a></li>
<li><a href="https://www.opencompute.org/documents/ocp-mrc-1-0-pdf">[PDF] Multipath Reliable Connection (MRC) Specification - Open Compute Project</a></li>

</ul>
</details>

**Tags**: `#networking`, `#RDMA`, `#AI training`, `#NVIDIA`, `#protocol`

---

<a id="item-15"></a>
## [Moonshot AI valuation tops $10B with new $700M funding](https://t.me/zaihuapd/41251) ⭐️ 8.0/10

Moonshot AI, the company behind the Kimi assistant, completed a new funding round exceeding $700 million led by Alibaba, Tencent, and others, pushing its valuation past $10 billion in just over two years. Additionally, Kimi's cumulative revenue over the last 20 days has already surpassed its entire 2024 full-year revenue, with overseas revenue now exceeding domestic revenue. This rapid valuation growth and revenue surge highlight the strong market traction and investor confidence in Chinese AI startups, particularly in large language models. It also signals that Kimi's global expansion is gaining momentum, challenging international competitors. The latest round brings Moonshot AI's total funding to over $1.2 billion. The K2.5 model has been made available on OpenRouter, a unified API gateway, and is an open-source multimodal model that supports vision, language, and agentic workflows.

telegram · zaihuapd · May 7, 00:30

**Background**: Moonshot AI is a Chinese AI startup founded in 2023, known for developing the Kimi assistant, a conversational AI product. “Ten-horned beast” is a Chinese term for a startup valued over $10 billion. Large language models (LLMs) like Kimi use deep learning to generate human-like text and can be accessed via APIs. OpenRouter is a platform that provides a unified API to hundreds of LLMs.

<details><summary>References</summary>
<ul>
<li><a href="https://www.kimi.com/ai-models/kimi-k2-5">Kimi K2.5 | Open Visual Agentic Model for Real Work</a></li>
<li><a href="https://huggingface.co/moonshotai/Kimi-K2.5">moonshotai/Kimi-K2.5 · Hugging Face</a></li>
<li><a href="https://aiwiki.ai/wiki/openrouter">OpenRouter - AI Wiki</a></li>

</ul>
</details>

**Tags**: `#AI startup`, `#fundraising`, `#Chinese AI`, `#Kimi`, `#valuation`

---