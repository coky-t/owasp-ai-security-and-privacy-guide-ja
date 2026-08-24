---
title: 0. AI セキュリティ概要
heroTitle: "AI セキュリティ概要"
heroText: "このページは、導入、脅威とコントロールの概要、段階的なリスク分析、分野横断的な懸念事項について説明します。次のページでは脅威とコントロールについてさらに深堀していきます。"
weight: 1
---

## Introduction

### Table of contents
>Category: discussion  
>Permalink: https://owaspai.org/go/toc/

* [AI Security Overview](/docs/ai_security_overview/)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- [About the AI Exchange](/go/about/)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- [Roadmap](/go/roadmap/)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- [How to use this document](/go/document/)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- [Organize AI](/go/organize/)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- [Essentials](/go/essentials/)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- [Threats](/go/threatsoverview/)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[Highlight: Threat matrix](/go/aisecuritymatrix/)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[Highlight: Agentic AI overview](/go/agenticaioverview/)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[Highlight: Navigator](/go/navigator/)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- [Controls](/go/controlsoverview/)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[Highlight: Periodic table of threats and controls](/go/periodictable/)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- [Risk analysis](/go/riskanalysis/)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[Highlight: Threat modeling](/go/threatmodel/)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- [How about ...](/docs/ai_security_overview/#how-about-)  

* [Deep dive into threats and controls:](/go/navigator/)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- [1. General controls](/docs/1_general_controls)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[1.1 Governance controls](/go/governancecontrols/)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[1.2 Data limitation](/go/datalimit/)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[1.3 Limit unwanted behaviour](/go/limitunwanted/)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- [2. Input threats and controls](/docs/2_threats_through_use/)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[Highlight: Prompt injection protection](/go/promptinjectionsevenlayers/)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- [3. Development-time threats and controls](/docs/3_development_time_threats/)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- [4. Runtime conventional security threats and controls](/docs/4_runtime_application_security_threats/)  

* [AI security testing](/docs/5_testing/)
* [AI privacy](/go/aiprivacy/)  
* [References](/docs/ai_security_references/)
* [Index](/docs/ai_security_index/)

### AI Exchange について
>カテゴリ: ディスカッション  
>パーマリンク: https://owaspai.org/go/about/

If you want to jump right into the content, head on to the [Table of contents](/go/toc/) or [How to use this document](/go/document/).  

**Summary**  
Welcome to the go-to comprehensive resource for AI security & privacy - over 300 pages of practical advice and references on protecting AI, and data-centric systems from threats - where AI consists of ALL AI: Agentic AI, Analytical AI, Discriminative AI, Generative AI and heuristic systems. This content serves as key bookmark for practitioners, and is contributed actively and substantially to international standards such as ISO/IEC and the AI Act through official standard partnerships. Through broad collaboration with key institutes and SDOs, the _Exchange_ represents the consensus on AI security and privacy.

 <p class="text-center">
  <a href="https://youtu.be/kQC7ouDB_z8" target="_blank" rel="noopener noreferrer">
    <img
      src="https://raw.githubusercontent.com/OWASP/www-project-ai-security-and-privacy-guide/refs/heads/main/content/ai_exchange/static/images/ai-overview.png"
      alt="AI Overview Video"
      width="950"
      height="200"
      class="mx-auto"
    />
  </a>
</p>


**Details**  
The OWASP AI Exchange has open sourced the global discussion on the security and privacy of AI and data-centric systems. It is an open collaborative OWASP Flagship project to advance the development of AI security & privacy standards, by providing a comprehensive framework of AI threats, controls, and related best practices. Through a unique official liaison partnership, this content is feeding into standards for the EU AI Act (70 pages contributed to prEN 18282), ISO/IEC 27090 (AI security, 70 pages contributed), ISO/IEC 27091 (AI privacy), and [OpenCRE](https://opencre.org) - which links AI Exchange with many of the AI security standards and guidelines - and makes it accessible through the security chatbot [OpenCRE-Chat](https://opencre.org/chatbot).

データ中心のシステムは、AI システムと、AI Exchange の脅威とコントロール (データポイズニング、データサプライチェーンマネジメント、データパイプラインセキュリティなど) の多くに関連する AI モデルを持たない「ビッグデータ」システム (データウェアハウス、BI、レポーティング、ビッグデータなど) に分けられます。

Security here means preventing unauthorized access, use, disclosure, disruption, modification, or destruction. Modification includes manipulating the behaviour of an AI model in unwanted ways.

Our **mission** is to be the global go-to resource for security and privacy practitioners working with AI and data-centric systems—bringing alignment and encouraging collaboration across initiatives. In doing so, we create a safe, open, and independent space where everyone can find and share insights. Follow [AI Exchange at LinkedIn](https://www.linkedin.com/company/owasp-ai-exchange/).

**How it works**  
The AI Exchange is displayed here at [owaspai.org](https://owaspai.org) and edited using a [GitHub repository](https://github.com/OWASP/www-project-ai-security-and-privacy-guide/tree/main/content/ai_exchange/content) (see the links _Edit page_ at the top of every page). It is an **open-source living publication** for the worldwide exchange of AI security & privacy expertise. It is structured as one coherent resource consisting of several sections under 'content', each represented by a page on the website.

This material is evolving constantly through open source continuous delivery. The authors group consists of over 170 carefully selected experts (researchers, practitioners, vendors, data scientists, etc.) and other people in the community are welcome to provide input too. See the [contribute page](/contribute/).

<p xmlns:cc="http://creativecommons.org/ns#" xmlns:dct="http://purl.org/dc/terms/"><span property="cc:attributionName">AI セキュリティコミュニティ</span> による <a property="dct:title" rel="cc:attributionURL" href="https://owaspai.org">OWASP AI Exchange</a> には <a href="http://creativecommons.org/publicdomain/zero/1.0?ref=chooser-v1" target="_blank" rel="license noopener noreferrer" style="display:inline-block;">CC0 1.0</a> のマークが付けられており、著作権や帰属を明示することなく、どの部分でも自由に利用できることを意味します。可能であれば、読者がより多くの情報を見つけられるように、OWASP AI Exchange のクレジットやリンクを記載していただけると幸いです。</p>

**Who is this for**  
The Exchange is for practitioners in security, privacy, engineering, testing, governance, and for end users in an organization - anyone interested in the security and privacy of AI systems. The goal is to make the material as easy as possible to access. Using the [Risk analysis section](/go/riskanalysis/) you can quickly narrow down the issues that matter to your situation, whether you are a large equipment manufacturer designing an AI medical device, or a small travel agency using a chatbot for HR purposes.

**History**  
AI Exchange は [Rob van der Veer](https://www.linkedin.com/in/robvanderveer/) によって 2022 年に設立されました。セキュリティ標準の橋渡し役、[Software Improvement Group](https://www.softwareimprovementgroup.com) の最高 AI 責任者、AI とセキュリティで 34 年の経験を持ち、AI ライフサイクルに関する ISO/IEC 5338 の主執筆者、OpenCRE の創設者であり、現在は CEN/CENELEC で ISO/IEC 27090、ISO/IEC 27091、EU AI 法に関するセキュリティ要件に取り組んでおり、EU 加盟国によって共同編集者に選出されました。

The project started out as the 'AI security and privacy guide' on October 22 and was rebranded a year later as 'AI Exchange' to highlight the element of global collaboration. In March 2025 the AI Exchange was awarded the status of 'OWASP Flagship project' because of its critical importance, together with the ['GenAI Security Project'](https://genai.owasp.org/).

**The AI Exchange is trusted by industry giants**

Dimitri van Zantvliet, Director Cybersecurity, Dutch Railways:
> "A risk-based, context-aware approach—like the one OWASP Exchange champions—not only supports the responsible use of AI, but ensures that real threats are mitigated without burdening engineers with irrelevant checklists. We need standards written by those who build and defend these systems every day."

Sri Manda, Chief Security & Trust Officer at Peloton Interactive:
> “AI regulation is critical for protecting safety and security, and for creating a level playing field for vendors. The challenge is to remove legal uncertainty by making standards really clear, and to avoid unnecessary requirements by building in flexible compliance. I’m very happy to see that OWASP Exchange has taken on these challenges by bringing the security community to the table to ensure we get standards that work.”

Prateek Kalasannavar, Staff AI Security Engineer, Lenovo:
> “At Lenovo, we’re operationalizing AI product security at scale, from embedded inference on devices to large-scale cloud-hosted models. OWASP AI Exchange serves as a vital anchor for mapping evolving attack surfaces, codifying AI-specific testing methodologies, and driving community-aligned standards for AI risk mitigation. It bridges the gap between theory and engineering.”

**Mission/vision**

The mission of the AI Exchange is to enable people to find and use information to ensure that AI systems are secure and privacy preserving.

The vision of the AI Exchange is that the main challenge for people is to find the right information and then understand it so it can be turned into action. One of the underlying issues is the complexity, inconsistency, fragmentation and incompleteness of the standards and guideline landscape - with  issues of quality and being outdated - caused by the general lack of expertise in AI security in the industry. What resource to use?

The AI Exchange achieves:
- AUTHORITATIVE - active alignment with other resources through careful analysis and through close collaboration - particularly through substantial contribution to leading international standards at ISO/IEC and the AI Act - making sure the AI Exchange represents consensus. 
- OPEN - Anybody that wants to, can contribute to the AI Exchange body of knowledge, with strong quality assurance, including a screening process for Authors.
- FREE - Anybody that wants to, use can use it in any way. Free of copyright and attribution. 
- COVERAGE - comprehensive guidance instead of a selected set of issues (like a top 10 which is more for awareness) - and about all AI and data-intensive systems. AI is much more than Generative AI.
- UNIFIED - a coherent resource instead of a fragmented set of disconnected separate resources.
- CLEAR - clear explanation, including also the why and how and not just the what.
- LINKED - referring to various other sources instead of complex text that incorrectly suggests it is complete. This makes the Exchange the place to start
- EVOLVING - continuous updates instead of occasional publications.

All aspects above make the Exchange the go-to resource for practitioners, users, and training institutes - effectively and informally making the AI Exchange the standard in AI security.

NOTE: Producing and continuously updating a comprehensive and coherent quality resource requires a strong coordinated approach. It is much harder than an approach of every person for themselves. But necessary.


### <a name="relevant-owasp-ai-initiatives">関連する OWASP AI イニシアチブ</a>
>カテゴリ: ディスカッション  
>パーマリンク: https://owaspai.org/go/aiatowasp/

[![](https://raw.githubusercontent.com/OWASP/www-project-ai-security-and-privacy-guide/refs/heads/main/content/ai_exchange/static/images/aixpositioning.png)](https://raw.githubusercontent.com/OWASP/www-project-ai-security-and-privacy-guide/refs/heads/main/content/ai_exchange/static/images/aixpositioning.png)

In short:
- The **OWASP AI Exchange** is a comprehensive core framework of the AI security fundamentals: threats, controls and related best practices for all AI, actively aligned with international standards and feeding into them. It covers all types of AI, and next to security it discusses privacy as well.
- The **OWASP GenAI Security Project** is a growing collection of documents on the security of Generative AI, covering a wide range of topics including the LLM top 10.

Here's more information on AI at OWASP: 
- If you want to **understand how to ensure security or privacy of your AI or data-centric system** (GenAI or not), or want to align with AI security standards, you can use the [AI Exchange](https://owaspai.org), and from there you will be referred to relevant further material (including GenAI security project material) where necessary. 
- If you want to achieve **quick awareness** of the top security concerns for Large Language Models, check out the [LLM top 10 of the GenAI project](https://genai.owasp.org/llm-top-10/). Please know that it is not complete, intentionally - for example it does not include the security of prompts.
- If you want to **assess or audit the security of your AI application** against technical security requirements, use the [OWASP AISVS](https://owasp.org/www-project-artificial-intelligence-security-verification-standard-aisvs-docs/).

Some more details on projects: 
- [The OWASP AI Exchange(this work)](/go/about/) is the go-to single resource for AI security & privacy - over 300 pages of practical advice and references on protecting AI, and data-centric systems from threats - where AI consists of Analytical AI, Discriminative AI, Generative AI and heuristic systems. This content serves as a key bookmark for practitioners, and is contributed actively and substantially to international standards such as ISO/IEC and the AI Act through official standard partnerships.
- The [OWASP GenAI Security Project](https://genai.owasp.org/) is an umbrella project of various initiatives that publish documents on Generative AI security, including the LLM AI Security & Governance Checklist and the LLM top 10 - featuring the most severe security risks of Large Language Models.
- The [OWASP AISVS](https://owasp.org/www-project-artificial-intelligence-security-verification-standard-aisvs-docs/) (Artificial Intelligence Security Verification Standard) focuses on providing developers, architects, and security professionals with a structured checklist to verify the security of AI-driven applications. It provides three verification levels aligned with ASVS, and covers the full AI lifecycle from training data integrity to deployment monitoring.
- [OpenCRE.org](https://opencre.org) has been established under the OWASP Integration standards project(from the _Project wayfinder_) and holds a catalog of common requirements across various security standards inside and outside of OWASP. OpenCRE links all AI security controls and threats across standards and guidelines, and the Exchange features a mechanism to insert the correct references for all sections to owaspai.org. This effectively makes the Exchange a hub for the AI security standards landscape. More details in [this LinkedIn post](https://www.linkedin.com/posts/robvanderveer_announcing-the-rosetta-stone-of-ai-security-share-7454426279262564352-SLzR).
- Further AI projects at OWASP can be found [here](https://owasp.org/search/?searchString=AI)

What makes the Exchange special is FOUNDATION:
- F – Fundamentals: comprehensive threat & control model
- O – One integrated body of knowledge (as opposed to a collection of documents)
- U – Universal: covers all AI & data-centric systems
- N – No copyright restrictions (fully shareable)
- D – Data & privacy included
- A – Aligned with international standards
- T – Technically grounded (engineering-oriented)
- I – Iteratively updated (continuous instead of yearly)
- O – Open (any expert can contribute)
- N – Networked - bridge between standards, researchers, and practitioners

The AI Exchange has strong and diverse collaboration with industry and institutes, for example a formal ongoing collaboration with SANS Institute to share expertise and support broad education.


### AI Exchange roadmap
>Category: discussion  
>Permalink: https://owaspai.org/go/roadmap/

Our **mission** is to be the global go-to resource for security and privacy practitioners working with AI and data-centric systems—bringing alignment and encouraging collaboration across initiatives. In doing so, we create a safe, open, and independent space where everyone can find and share insights.

**Priority content workstreams to deliver major update before summer 2026**
- **Agentic AI**: Extending the Exchange further with the emerging security challenges of autonomous multi-agent systems, led by Chris Cochran
- **Harmonization**: Solving gaps and mapping the Exchange to leading frameworks including NIST, MITRE ATLAS, and ETSI led by Rob van der Veer and Yuvaraj
- **Red Teaming** (Testing): Extending the testing section and evaluating open-source tools for Predictive and Generative AI to withstand adversarial attack led by Behnaz Karimi
- **EU AI Act Flow Back**: Integration of the extensive research the group did for the contributions to the EU AI Act security standard, led by Rob van der Veer
- **Step-by-Step Guide**: Providing organizations with a structured path to implement AI security processes, led by Aruneesh Salhotra.
- Improved **AI-findability** of owaspai.org - for training sets and web search. Mostly: getting links.

**Specialized Project Groups**
- **Risk Analysis**: Designing formal processes for AI risk assessment and responsibility
assignment.
- **Education Guidance**: Providing training guidance and security mindsets for data
scientists and developers.
- **Legislation**: Tracking global laws and regulations.
- **Requirements**: The group working on the AI Act and ISO 27090 contributions
- **Mathematical**: Ensuring completeness of the mathematical data science topics for AI robustness and
security.

**Strategic & Operational Workstreams**
- **Standards alignment**: Through engagements, partnerships, events, and mapping, drive alignment of standards when it comes to AI security. Goal: clarity for practitioners and supervisors. Led by Rob van der Veer and Aruneesh Salhotra
- **Promotion & Outreach**: Development of global and regional marketing plans to drive
community engagement and project visibility, led by Aruneesh Salhotra.
- **Sponsorship & Fundraising**: Operational efforts to secure the necessary resources
and funding to sustain project growth, led by Aruneesh Salhotra.
Core Technical Workstreams
  
**Project Leadership Team**
- Rob van der Veer: Project Founder and Lead Editor.
- Aruneesh Salhotra: Leads Promotion, Collaboration, and Fundraising.
- Behnaz Karimi: Leads Red Teaming, Training, and People Matters.

## このドキュメントの使い方
>カテゴリ: ディスカッション  
>パーマリンク: https://owaspai.org/go/document/

The AI Exchange is a single coherent resource on the security and privacy of AI systems, presented on this website, divided over several pages - containing threats, controls, guidelines, tests and references.

**Ways to start, depending on your need:**
- **Ask any question on AI Security**
  Ask an AI security/privacy question based on the content of the Exchange: [AI Exchange AGENT](https://notebooklm.google.com/notebook/75840a00-78f8-454d-ad4d-9ac27ae4cf48) (uses Google service so requires Google account).
- **Learn what the AI Exchange is**:  
  See [About](https://owaspai.org/go/about/)
- **Start AI security as organization**:  
  See [How to organize AI security](https://owaspai.org/go/organize/)..
- **Start AI security as individual**:  
  See 'Learn AI security' below to familiarize yourself with the threats and controls or look in the [references section](/go/references/) for a large table with training material.
- **Understand how AI systems are engineered before securing them**:
  See the [AI engineering primer for security professionals](/go/aiengineeringprimer/) below. It explains common delivery models, engineering activities, artifacts, and the security decisions attached to them.
- **Threat model your system, to learn how to secure it**:  
   If you want your **AI system to be secure**, start with [threat modeling](/go/threatmodel/) to guide you through a number of questions, resulting in the threats that apply. And when you click on those threats you'll find the controls (countermeasures) to check for, or to implement.
   Alternatively, you can let our [THREAT ADVISOR](/go/threatadvisor/) ask YOU questions about your system and threat model for you. Just go to the advisor (requires a Google account) and start by briefly describing your system. Your data will remain in your own Google workspace.
- **Learn AI security**:  
  - Step 1: If you like a 101 on AI engineering, walk throught the [AI engineering primer for security professionals](/go/aiengineeringprimer/)
  - Step 2: First study the brief [AI security essentials](/go/essentials/) for the **big picture**.
  - Step 3: **Select** the threats that are relevant to your practice, by looking at [threat modeling](/go/threatmodel/) - or let AI interview you to find out (see above), or skip this step if you want to learn the complete threat picture.
  - Step 4: If you're AI models can **trigger actions**, see the brief [Agentic AI overview](/go/agenticaioverview/) to see how that aspect is throughout the Exchange.
  - Step 5: If you run a **ready-made model**, have a look at the [threat model on ready-made models](/go/readymademodel/).
  - Step 6: See your **threats** in their context ** in the [AI threat model](/go/threatsoverview/) and the [AI security matrix](/go/aisecuritymatrix).
  - Step 7: Click on your relevant threats in that overview to get more information and how to protect against it.
  - Step 8: To find out what to do against a specific threat, check the **Controls** section of that threat, or the [periodic table](/go/periodictable/) which lists the controls for every threat.
  - Step 9: To learn about the bigger picture how controls play a role, and interact: see the [controls overview](/go/controlsoverview/) 
  - Step 10: If **privacy** is in scope for you: see [the privacy section](/go/aiprivacy/).
  - Step 11: If you're involved in **testing**: see [the testing section](/go/testing/).
  - Step 12: A great way to better understand AI threats is to act as an attacker, for which we recommend [PwnzzAI!](https://github.com/OWASP/PwnzzAI ): a hacking lab project with the Exchange as founding partner. A great exercise!
  - To learn more about education programs, see [#SEC EDUCATE](/go/seceducate/)
  - If you prefer one document: download a [snapshot of the Exchange in pdf](/OWASP-AI-Exchange.pdf).
- **Lookup**:
  - To look up a specific topic, use the search function or the [index](/go/index/).
  - Looking for more information, or training material: see the [references](/go/references/).


The AI exchange covers both heuristic artificial intelligence (e.g., expert systems) and machine learning. This means that when we talk about an AI system, it can for example be a Large Language Model, a linear regression function, a rule-based system, or a lookup table based on statistics. Throughout this document, it is made clear which threats and controls play a role and when.

**The structure**  
You can see the high-level structure on the [main page](https://owaspai.org). On larger screens you can see the structure of pages on the left sidebar and the structure within the current page on the right. On smaller screens you can view these structures through the menu. There is also a section with the most important topics in a [Table of contents](/go/toc/).

The main structure is made of the following pages:  
  (0) [AI security overview - this page](/go/toc/), contains an overview of AI security and discussions of various topics.  
  (1) [General controls, such as AI governance](/go/generalcontrols/)  
  (2) [Input threats, such as evasion attacks](/go/inputthreats/)  
  (3) [Development-time threats, such as data poisoning](/go/developmenttime/)  
  (4) [Runtime conventional security threats, such as leaking input](/go/runtimeconventionalsec/)  
  (5) [AI security testing](/go/testing/)  
  (6) [AI privacy](/go/aiprivacy/)  
  (7) [References](/go/references/)

このページ (AI セキュリティ概要) では以下について取り上げます。
- 脅威の上位の概要
- 脅威とコントロールのさまざまな概要: マトリックス、周期表、ナビゲータ
- 関連する脅威とコントロールを選択するためのリスク分析
- さまざまな他のトピック: ヒューリスティックシステム、責任ある AI、生成 AI、NCSC/CISA ガイドライン、著作権

---

### AI engineering primer for security professionals
>Category: discussion  
>Permalink: https://owaspai.org/go/aiengineeringprimer/

Security reviews become difficult when "the AI" is treated as one component. An AI-enabled product is usually a software system built around data, one or more models, prompts, retrieval sources, tools, and conventional infrastructure. The way these parts are sourced and operated determines which risks an organization owns, which controls it can implement, and which assurances it must obtain from suppliers.

**Three common delivery models**

1. **Use a hosted model or AI service.** The supplier operates the model and its serving infrastructure. The customer still owns the security of its application, prompts, retrieved data, identities, tool permissions, output handling, and monitoring.
2. **Run an externally sourced model.** The organization also owns model selection, artifact integrity, deployment hardening, isolation, patching, and capacity management. The origin and maintenance of the model remain supply-chain concerns.
3. **Train or adapt a model.** The organization additionally owns the training or fine-tuning data, pipeline, evaluation process, resulting model artifacts, and release decisions. Fine-tuning a hosted model falls between the first and third models because responsibilities are shared.

Real systems often combine all three. A product can use a hosted general-purpose model, a self-hosted classifier, and a fine-tuned embedding model in the same request path. Record responsibilities per component rather than assigning one label to the whole product. See [ready-made models](/go/readymademodel/) and [data, model, and hosting supply-chain management](/go/supplychainmanage/) for the corresponding controls.

**The engineering lifecycle and its security entry points**

| Engineering activity | Typical artifacts | Security question | Start in the Exchange |
| --- | --- | --- | --- |
| Frame the task and acceptance criteria | Use cases, data-flow diagrams, quality targets, unacceptable outcomes | Should AI be used here, what can go wrong, and who can be harmed? | [Essentials](/go/essentials/), [threat modeling](/go/threatmodel/), [privacy](/go/aiprivacy/) |
| Source or build models and data | Service contracts, model cards, datasets, licenses, model artifacts | Can the source be trusted, and what evidence or control remains with the supplier? | [Supply-chain management](/go/supplychainmanage/), [ready-made models](/go/readymademodel/) |
| Adapt behaviour | System prompts, prompt templates, retrieval indexes, fine-tuning data and configuration | Which untrusted data or instructions can change model behaviour? | [Prompt injection](/go/promptinjection/), [development practices](/go/devprogram/) |
| Integrate the model into a product | Application code, APIs, agents, tools, identities, secrets, output parsers | What can the model read, disclose, modify, or trigger, and with whose privileges? | [Agentic AI overview](/go/agenticaioverview/), [secure development](/go/secdevprogram/) |
| Evaluate and release | Evaluation sets, test results, red-team findings, model and prompt versions | Does the system meet both its functional and security requirements on representative and adversarial inputs? | [Continuous validation](/go/continuousvalidation), [AI security testing](/go/testing/) |
| Operate and change the system | Telemetry, incidents, user feedback, version history, rollback procedures | Can failures, abuse, and behavioural drift be detected, investigated, and contained? | [Monitoring](/go/monitoruse/), [AI security testing](/go/testing/) |

Several properties distinguish AI engineering from ordinary deterministic software development:

- **The model is not the system.** Security conclusions about a model do not automatically apply to the application, retrieval layer, tools, or deployment around it.
- **Evaluation characterizes behaviour; it does not prove correctness.** Test results depend on the chosen data, threat model, model version, configuration, and operating context. Record all of them with the result.
- **Data can be both content and instruction.** User input, retrieved documents, tool output, and stored memory may influence model behaviour even when engineers intended them to be data only.
- **Small changes can alter security behaviour.** A model, prompt, retrieval source, tool, policy, or threshold update can invalidate earlier evidence. Version these parts together and retest after change.
- **Supplier boundaries do not remove accountability.** If a control cannot be implemented directly, turn it into a supplier requirement and verify the evidence provided.

A practical first pass is to draw the flow of data, instructions, and actions through the system; list the model, data, prompt, retrieval, tool, and infrastructure artifacts at each step; and assign an owner or supplier to each artifact. Use that inventory to [threat model the system](/go/threatmodel/), select controls, and decide what evidence is required before release.

---

## High level view

This section discusses the main steps for adopting AI security in your organization, and for understanding the essentials of AI security.

### AI セキュリティをどのように編成するか？
>カテゴリ: ディスカッション  
>パーマリンク: https://owaspai.org/go/organize/

Organizations: start here!  
人工知能 (AI) はとてつもない好機を与える一方で、セキュリティ脅威などの新たなリスクももたらします。そのため、潜在的な脅威とそれに対するコントロールを明確に理解した上で、AI アプリケーションに取り組むことが不可欠です。AI は信頼できる場合にのみ繁栄できます。

[![](https://raw.githubusercontent.com/OWASP/www-project-ai-security-and-privacy-guide/main/content/ai_exchange/static/images/guard.png)](https://raw.githubusercontent.com/OWASP/www-project-ai-security-and-privacy-guide/main/content/ai_exchange/static/images/guard.png)

The five steps - G.U.A.R.D - to organize AI security as an organization are: 

1. **Govern**  
  Start implementing general AI Governance so the organization can manage AI: know where it is applied, what people's responsibilities are, establish policies, do impact assessment, arrange [compliance](/go/checkcompliance/), organize [education](/go/seceducate/), et cetera. See [#AI Program](/go/aiprogram/) for guidance, including a quickstart. This is a general AI management process - not just security.
2. **Understand**  
   - Based on the inventory of your applications of AI and AI ideas, understand which threats apply, using the decision tree in the [risk analysis section](/go/threatmodel/).
   - Then make sure engineers and security professionals understand those relevant threats and their controls, using the guidance of the relevant [threat sections](/go/threatsoverview/) and the corresponding [process controls and technical controls](/go/periodictable/). Note that most of these controls are about familiar conventional security countermeasures, unless you are training your own model.
   - Use the courses and resources in the [references section](/go/references/) to support the understanding.
   - Distinguish between controls that your organization has to implement, and those that are the responsibility of your supplier. Make the latter category part of your [supply chain management](/go/supplychainmanage/). See the [section on ready-made models](/go/readymademodel/) if you don't train your own models.
3. **Adapt**  
    -  [セキュリティプラクティスを採用](1_general_controls.md#sec-program) して、このドキュメントの AI セキュリティ資産、脅威、コントロールを含めます。Also take into account that new regulation can be more outcome-based (e.g. the EU AI Act), instead of control-focused (like ISO/IEC 27001) which makes it important to extend the Information Security Management System with assurance processes for showing that risks have been sufficiently mitigated.
    - Document risk assessment, control selection, the rationale, and the risk-mitigation evidence (a good idea in general, and mandatory for the AI Act.
    - Adapt your threat modelling to include the [AI security threat modeling](/go/threatmodel/) approach and do cross-team threat modelling, involving representation from all engineers.
    - Adapt your testing to include [AI-specific security testing](/go/testing/).
    - Adapt your supply chain management to include [data, model, and hosting management](/go/supplychainmanage/) and to make sure that your suppliers are taking care of the identified threats.
    - AI システムを開発する場合 (独自のモデルをトレーニングしない場合でも): Adapt your [software development practices](/go/devprogram/) and [secure development program](/go/secdevprogram/) to involve AI engineering activities. 
4. **Reduce**  
  Reduce potential impact by [minimizing or obfuscating sensitive data](/go/datalimit/) and [limiting the impact of unwanted behaviour](/go/limitunwanted/) (e.g., managing privileges, guardrails, human oversight etc. Basically: apply Murphy's law). This is critical because AI models can always be wrong or manipulated. 
5. **Demonstrate**  
    Establish evidence of responsible AI security through transparency, [testing](/go/testing/), documentation, and communication. Prove to management, regulators, and clients that your AI systems are under control and that the applied safeguards work as intended.

And finally: think before you build an AI solution. AI can have fantastic benefits, but it always needs to be balanced with risks. Securing AI is typically harder than securing non-AI systems, first because it's relatively new, but also because there is a level of uncertainty in all data-driven technology. For example in the case of LLMs, we are dealing with the fluidity of natural language. LLMs essentially offer an unstable, undocumented interface with an unclear set of policies. That means that security measures applied to AI often cannot offer security properties to a standard you might be used to with other software. Consider whether AI is the appropriate technology choice for the problem you are trying to solve. Removing an unnecessary AI component eliminates all AI-related risks.  

---


### Essentials: how to understand the basics of AI security
>Category: discussion  
>Permalink: https://owaspai.org/go/essentials/

This section serves as THE starting point to understand the foundations of AI security, and was established in close collaboration with industry and institutes, including complete alignment with the [SANS Critical AI security guidelines](https://assets.contentstack.io/v3/assets/bltabe50a4554f8e97f/blte964a6eef293d57e/whitepaper-critical-ai-security-guidelines) and formal standards ISO/IEC 27090 (AI security) and prEN18282 (Cybersecurity for the AI Act).

---

**AI-specific threats** (full overview [here](/go/threatsoverview/)):
  1. **[Model input threats](/go/inputthreats/)**:  
      - [Evasion](/go/evasion/): Misleading a model by crafting data to force wrong decisions
      - [Prompt injection](/go/promptinjection/): Misleading a model by crafting instructions to manipulate behaviour
      - [Extracting data from the model](/go/disclosureinoutput/): training data, augmentation data (including system prompts), or input
      - [Extracting of the model itself](/go/modelexfiltration/) by querying the model
      - [Resource exhaustion](/go/airesourceexhaustion/) through use
  2. **New suppliers** introduce threats of corrupted external [data](/go/datapoison/), [models](/go/supplymodelpoison/), and [model hosting](/go/readymademodel/)
  3. **New AI assets** with conventional threats, notably:  
      - Training data / augmentation data (e.g. system prompts) - can leak and [poisoning](/go/datapoison/) this data manipulates model behaviour
      - Model - can suffer from [leaking during development](/go/devmodelleak/) or [leaking during runtime](/go/runtimemodelleak/) and when it comes to integrity: from [poisoning during development](/go/devmodelpoison/) or [poisoning during runtime](/go/runtimemodelpoison/)
      - Input - can [leak](/go/inputdataleak/)
      - Output - can contain [injection attacks](/go/outputcontainsconventionalinjection/)

Note: Attackers that obtain the model (or a similar one) can perform or prepare input attacks efficiently and without being noticed.

---
    
**AI-specific controls** (overview [here](/go/controlsoverview/)):

The controls for AI security can be divided into four essential categories and 8 essential sub categories, linking to over 50 individual controls discussed in depth at the Exchange.

**Manage**:
- Extend existing **Governance, Risk, and Compliance** - in order to secure AI, you need overview, analysis, policy, training, responsibilities, and control:
  > [AI PROGRAM](/go/aiprogram/ ), [DEV PROGRAM](/go/devprogram/), [CHECK COMPLIANCE](/go/checkcompliance/), [SEC EDUCATE](/go/seceducate/)
- Extend **Supply chain management** to incorporate suppliers providing data, models, and hosting
  > [Supply chain management](/go/supplychainmanage/)
- Extend existing **conventional security controls** to protect the AI-specific assets
  - Managing security:
    > [SEC PROGRAM](/go/secprogram/), [SECDEV PROGRAM](/go/secdevprogram/)
  - Development-time (model, data, and documentation):
    > [DEV SECURITY](/go/devsecurity/), [SEGREGATE DATA](/go/segregatedata/), [DISCRETE](/go/discrete/)
  - Runtime: (model storage, model use, augmentation data (including system prompts), and model input/output):  
    > [MODEL ACCESS CONTROL](/go/modelaccesscontrol/), [RUNTIME MODEL INTEGRITY](/go/runtimemodelintegrity/), [RUNTIME MODEL IO INTEGRITY](/go/runtimemodeliointegrity/), [RUNTIME MODEL CONFIDENTIALITY](/go/runtimemodelconfidentiality/), [MODEL INPUT CONFIDENTIALITY](/go/modelinputconfidentiality/), [ENCODE MODEL OUTPUT](/go/encodemodeloutput/), [LIMIT RESOURCES](/go/limitresources/), [AUGMENTATION DATA CONFIDENTIALITY](/go/augmentationdataconfidentiality/), [AUGMENTATION DATA INTEGRITY](/go/augmentationdataintegrity/), [CONF COMPUTE](/go/confcompute/), [MODEL OBFUSCATION](/go/modelobfuscation/)   

**Have resilient models**:
- Apply **data/model engineering controls** during model development for resilience against input attacks. This is the work of data and model engineers. Input attacks include triggering poisoned models - which of course can also be mitigated by preventing the model being poisoned using conventional controls:
  > [MODEL ALIGNMENT](/go/modelalignment/), [FEDERATED LEARNING](/go/federatedlearning/), [CONTINUOUS VALIDATION](/go/continuousvalidation/), [UNWANTED BIAS TESTING](/go/unwantedbiastesting/), [EVASION ROBUST MODEL](/go/evasionrobustmodel/), [POISON ROBUST MODEL](/go/poisonrobustmodel/), [TRAIN ADVERSARIAL](/go/trainadversarial/), [TRAIN DATA DISTORTION](/go/traindatadistortion/), [ADVERSARIAL ROBUST DISTILLATION](/go/adversarialrobustdistillation/), [MODEL ENSEMBLE](/go/modelensemble/), [MORE TRAINDATA](/go/moretraindata/), [SMALL MODEL](/go/smallmodel/), [DATA QUALITY CONTROL](/go/dataqualitycontrol/)

**Watch:**
- Apply **Model I/O handling** for runtime filtering, stopping or alerting to suspicious input or output. It is typically the territory of data and model engineers e.g. data scientists, involving elements from mathematics, statistics, linguistics and machine learning:
  > [ANOMALOUS INPUT HANDLING](/go/anomalousinputhandling/), [EVASION INPUT HANDLING](/go/evasioninputhandling/), [UNWANTED INPUT SERIES HANDLING](/go/unwantedinputserieshandling/), [PROMPT INJECTION I/O HANDLING](/go/promptinjectioniohandling/), [DOS INPUT VALIDATION](/go/dosinputvalidation/), [INPUT DISTORTION](/go/inputdistortion/), [SENSITIVE OUTPUT HANDLING](/go/sensitiveoutputhandling/), [OBSCURE CONFIDENCE](/go/obscureconfidence/), [RATE LIMIT](/go/ratelimit/)
 - **Monitoring** of model inference - extending <odel I/O handing, Oversight (see below) and overlooking general usage of the AI system:
   > [MONITOR USE](/go/monitoruse/)

**Limit:**   
- **Minimize or obfuscate sensitive data** because a model can accidentally leak daa or be misled to:
  > ([DATA MINIMIZE](/go/dataminimize/), [ALLOWED DATA](/go/alloweddata/), [SHORT RETAIN](/go/shortretain/), [OBFUSCATE TRAINING DATA](/go/obfuscatetrainingdata/))
- **Limit model behaviour**  because a model can accidentally make a mistake or be misled to:
  > [OVERSIGHT](/go/oversight/), [LEAST MODEL PRIVILEGE](/go/leastmodelprivilege/), [AI TRANSPARENCY](/go/aitransparency/), [EXPLAINABILITY](/go/explainability/), [CONTINUOUS VALIDATION](/go/continuousvalidation/), [UNWANTED BIAS TESTING](/go/unwantedbiastesting/)

[![](https://raw.githubusercontent.com/OWASP/www-project-ai-security-and-privacy-guide/main/content/ai_exchange/static/images/essentials6.png)](https://raw.githubusercontent.com/OWASP/www-project-ai-security-and-privacy-guide/main/content/ai_exchange/static/images/essentials6.png)

Many experts and organizations contributed to this overview of essentials - including close collaboration with SANS Institute, ensuring alignment with SANS’ [Critical AI security guidelines](https://assets.contentstack.io/v3/assets/bltabe50a4554f8e97f/blte964a6eef293d57e/whitepaper-critical-ai-security-guidelines). SANS and the AI Exchange have a formal ongoing collaboration to share expertise and support broad education.

The upcoming sections provide overviews of AI security threats and controls.

---

## 脅威の概要
>カテゴリ: ディスカッション  
>パーマリンク: https://owaspai.org/go/threatsoverview/

### Scope of Threats
In the AI Exchange we focus on AI-specific threats, meaning threats to AI assets (see [#SEC PROGRAM](/go/secprogram/)), such as training data. Threats to other assets are already covered in many other resources - for example the protection of a user database. AI systems are IT systems so they suffer from various security threats. Therefore, when securing AI systems, the AI Exchange needs to be seen as an extension of your existing security program: 
AI security = threats to AI-specific assets (AI Exchange) +threats to other assets (other resources)

### 脅威マップ
私たちは三つのタイプの脅威を区別します:
1. 開発時 (データの取得および準備時、モデルの学習/取得時) の脅威 - 例: データポイズニング
2. 入力の脅威: 攻撃者によるモデル使用時 (推論時、入力の提供と出力の取得時) - 例: プロンプトインジェクションや回避
3. 実行時 (運用時、推論時ではない) のシステムへのその他の脅威 - 例: モデル入力の窃取

AI では、3 つのタイプの攻撃者の目的 (開示、欺瞞、妨害) に沿って、6 つのタイプの影響を概説します:
1. 開示: トレーニングデータやテストデータの機密性を損なう
2. 開示: モデル知的財産 (_モデルパラメータ_ やそれにつながるプロセスとデータ) の機密性を損なう
3. 開示: 入力データや拡張データの機密性を損なう
4. 欺瞞: モデル動作の完全性を損なう (モデルが望ましくない動作をするように操作され、結果としてユーザーを欺く)
5. 妨害: モデルの可用性を損なう (モデルが機能しないか、望ましくない動作をする - ユーザーを欺くためではなく、通常の運用を妨害するため)
6. 開示/妨害: AI 固有ではない資産の機密性、完全性、可用性

このような影響をもたらす脅威はさまざまな攻撃対象領域を使用します。たとえば、トレーニングデータの機密性は開発中にデータベースにハッキングすることで侵害される可能性がありますが、特定の個人のデータを入力して、モデル出力の詳細を見るだけで、その個人がトレーニングデータにあるかどうかを知ることができる _メンバーシップ推論攻撃_ によって漏洩する可能性もあります。

このマップでは脅威を矢印で示しています。各脅威には特定の影響があり、Impact legend を参照する文字で示されています。[コントロールの概要のセクション](ai_security_overview.md#controls-overview) には、この図にコントロールのグループを追加したものがあります。このマップの資産の一覧については、[セキュリティプログラムのサブセクション](1_general_controls.md#sec-program) を参照してください。
[![](https://raw.githubusercontent.com/OWASP/www-project-ai-security-and-privacy-guide/main/content/ai_exchange/static/images/threats.png?v=2)](https://raw.githubusercontent.com/OWASP/www-project-ai-security-and-privacy-guide/main/content/ai_exchange/static/images/threats.png?v=2)

Note that some threats represent attacks consisting of several steps, and therefore present multiple threats in one, for example:
—	An adversary performs a data poisoning attack by hacking into the training database and placing poisoned samples, and then after the data has been used for training, presents specific inputs to make use of the corrupted behaviour.
—	An adversary breaks into a development environment to steal a model so it can be used to experiment on to craft manipulated inputs to achieve a certain goal, and then present that input to the deployed system.


### Agentic AI overview
>Category: discussion  
>Permalink: https://owaspai.org/go/agenticaioverview/

Agentic AI systems are AI systems where the inference of a model can specify actions to perform without per-action human approval - in contrast of just providing the output for viewing. Actions may represent plans, orchestration, and messages as input to models for further inference and actions, while maintaining state.

There are many dimensions to Agentic AI, so it's best not to treat it in one specific way. Instead, the key is to look at an AI system's properties underneath: Can the AI models trigger actions? What harm can they cause? Are external services used? Is untrusted data coming in? Is memory used to keep context and plans? Can actions send out data? 

In essence: **'Agentic’ can be seen as a spectrum**, where capability, autonomy, and impact increase. There are ‘mildly’ agentic systems at the one end, such as a door-opening AI camera, and ‘very’ agentic systems at the other end: with agents planning without human intervention, running in a loop, performing actions:
- Mildy Agentic AI: performs actions
- Fairly Agentic AI: also plans
- Quite Agentic AI: also runs in loops
- Very Agentic AI: all of the above without any human intervention

The AI Exchange covers all AI systems, so also agentic AI systems, throughout its content. For the full threat and control picture, see the [threats overview](/go/threatsoverview/), [AI security matrix](/go/aisecuritymatrix/), and [periodic table of threats and controls](/go/periodictable/).  
This section highlights agentic attention points only — not a separate threat landscape. 

**There are four typical properties of agentic AI:**  
1. **Action**: Agents don’t just chat — they invoke functions such as sending an email. That makes [LEAST MODEL PRIVILEGE](/go/leastmodelprivilege/) a key control — including the [agentic authorisation framework](/go/leastmodelprivilege/) (deny-by-default, infrastructure policy enforcement, task-bound tokens, agent identity).
2. **Autonomous** (optional): Agents can trigger each other, enabling autonomous responses (e.g., a script receives an email, triggering a GenAI follow-up). That makes [OVERSIGHT](/go/oversight/) important, and it makes working memory an attack vector because that's where the state and the plan of an autonomous agent lives.
3. **Complex** (optional): Agentic behaviour is emergent.
4. **Multi-system** (optional): You often work with a mix of systems and interfaces. Because of that, developers tend to assign responsibilities regarding access control to the AI using instructions, opening up the door for manipulation through [prompt injection](/go/promptinjection/). Agent-to-service and inter-agent calls need machine-to-machine [#MODEL ACCESS CONTROL](/go/modelaccesscontrol/) (scoped tokens, session binding, mutual auth) alongside [#LEAST MODEL PRIVILEGE](/go/leastmodelprivilege/).

**What does this mean for security ?**
- When agents invoke tools, the **impact of attacks is typically higher** than with just text output. Risks shift from bad answers to goal drift, reward hacking, runaway escalation. Blast radius control ([impact limitation](/go/limitunwanted/)) is key.
- Hallucinations and [prompt injections](/go/promptinjection/) can **invoke unwanted actions** — or even escalate privileges. Key controls are defence in depth and addressing untrusted data entering the agentic flow- for example by [#INPUT SEGREGATION](/go/inputsegregation/) and [#PROMPT INJECTION I/O HANDLING](/go/promptinjectioniohandling/). The limitations of these controls to prevent a successful attack increase the importance of blast radius control.
- It can be tempting for AI system makers to use agents for implementing security features, such as access control. **Security features need to be built outside the LLMs**, in the architecture of the system, because of the vulnerability/robustness issue above.
- Existing assumptions about things like trust boundaries and other established security measures might need to be revisited because agentic AI changes interconnectivity and data flows between system components.
- Agents deployed with their own sets of permissions open up privilege escalation vectors because they are susceptible to becoming a confused deputy
- **Memory and context:** Agents accumulate state in working memory, vector stores, and cross-session stores — three surfaces ([in-context](/go/indirectpromptinjection/), [persistent poisoning](/go/augmentationdatamanipulation/), cross-session persistence). Apply [#AUGMENTATION DATA INTEGRITY](/go/augmentationdataintegrity/) and cross-link to [data poisoning](/go/datapoison/) where memory acts as a de facto training-like data source. In-context attacks overlap [prompt injection](/go/promptinjection/); persistent writes are a future read attack on other agents.
- **Jailbreak vs escape:** [Jailbreak](/go/directpromptinjection/) bypasses safety constraints within the agent's boundary; [agent escape](/go/agentescape/) exceeds that boundary (unauthorised tools or scope). Multi-turn jailbreak needs session-level [#OVERSIGHT](/go/oversight/); escape needs infrastructure [#LEAST MODEL PRIVILEGE](/go/leastmodelprivilege/).
- **Deceptive reasoning:** Agents can produce plans that appear well-reasoned but rest on manipulated intermediate steps. Compare stated reasoning to actual tool calls ([#OVERSIGHT](/go/oversight/), [#MONITOR USE](/go/monitoruse/)); corrupted reasoning often follows [prompt injection](/go/promptinjection/) or [memory manipulation](/go/augmentationdatamanipulation/) rather than a separate attack class.
- **Delegation and impersonation:** Signed delegation chains and scope non-expansion belong in [#LEAST MODEL PRIVILEGE](/go/leastmodelprivilege/); forged agent identity or message envelopes map to [agent message structure manipulation](/go/agentmessagestructuremanipulation/).
- **Multi-agent systems:** Layer on single-agent controls — **no transitive trust**; enforce inter-agent security at the message bus/orchestrator, not in agent prompts. Threat: [agent message structure manipulation](/go/agentmessagestructuremanipulation/). Orchestrator is a high-value target; monitor collective behaviour, not only per-agent actions ([#MONITOR USE](/go/monitoruse/), [#OVERSIGHT](/go/oversight/)).
- **Goal hijacking:** Treat as [impact](/go/limitunwanted/) — redirected objectives, not a separate threat permalink; attack vectors remain [prompt injection](/go/promptinjection/) and related paths.
- **Data access:** Purpose-bound, ephemeral agent context and classification enforcement live under [data limitation](/go/datalimit/) ([#DATA MINIMIZE](/go/dataminimize/), [#SHORT RETAIN](/go/shortretain/)).
- The attack surface is wide, and the potential impact should not be underestimated.
- Because of that, the [known controls](/go/controlsoverview/) become even more important, divided into:
  - Prevention: for example: security of inter-model communication (e.g., MCP), [agent sandboxing](/go/agentsandboxing/), [protecting of memory integrity](/go/augmentationdataintegrity/), [prompt injection defenses](/go/promptinjection/), and [agent message structure manipulation](/go/agentmessagestructuremanipulation/)
  - Blast radius control: [rule-based / human oversight](/go/oversight/) and [least model privilege](/go/leastmodelprivilege/)
  - Observability: [monitoring](/go/monitoruse/)
- **Validation gap:** Tools and methods to evaluate agentic security architecture and deployments are still evolving; without reliable validation, design and implementation weaknesses are harder to find before production. See [testing](/go/testing/) and [continuous validation](/go/continuousvalidation/).

For leaking sensitive data in agentic AI, you need three things, also called the _lethal trifecta_:
1. Data: Control of the attacker of data that find its way into an LLM at some point in the session of a user that has the desired access, to perform [indirect prompt injection](/go/indirectpromptinjection/) 
2. Access: Access of that LLM or connected agents to sensitive data
3. Send: The ability of that LLM or connected agents to initiate sending out data to the attacker

See [Simon Willison’s excellent work](https://simonwillison.net/2025/Jun/16/the-lethal-trifecta/) for more details, and for examples in agentic AI software development [here](https://www.darkreading.com/application-security/github-copilot-camoleak-ai-attack-exfils-data) and [here](https://ainativedev.io/news/malicious-github-issue-ai-agent-leak).

[Prompt injection](/go/promptinjection/) and mostly the [indirect](/go/indirectpromptinjection/) form is the key threat in most agentic AI systems. The [prompt injection section](/go/promptinjection/) covers agentic taxonomy (stored injection, multi-agent propagation) and structural mitigations (Agentic Rule of Two, tool-boundary firewalls). See the [seven layers section](/go/promptinjectionsevenlayers/) on how these controls form layers of protection. After model alignment and filtering and detection, it should be assumed that prompt injection can still happen and therefore it is critical that _blast radius control_ is performed.

**Agentic security architecture principles**

Agentic systems move AI from consulted component to **operational actor** — planning, calling tools, coordinating with other agents, and adapting with limited oversight. These are security design constraints, not a separate control catalogue:

- **Enforce at infrastructure, not in prompts.** Access control, policy, and containment belong in surrounding systems ([#LEAST MODEL PRIVILEGE](/go/leastmodelprivilege/), [#MODEL ACCESS CONTROL](/go/modelaccesscontrol/), [#AGENT SANDBOXING](/go/agentsandboxing/)), not in model instructions alone.
- **Design for compositional behaviour.** An agent with access to many tools and multi-step chaining produces a vast space of possible workflows — you cannot fully pre-specify purpose, boundaries, and side effects at design time. Threat modelling and governance specification remain necessary, but **runtime** guardrails ([#MONITOR USE](/go/monitoruse/), [#OVERSIGHT](/go/oversight/), [#LEAST MODEL PRIVILEGE](/go/leastmodelprivilege)) are required because emergent execution paths cannot all be enumerated upfront. Where regulation assumes pre-deployment describability of every workflow, compositional agentic systems need explicit program handling — see [#CHECK COMPLIANCE](/go/checkcompliance/) AI regulatory mapping.
- **Assume cascade across layers.** Data, reasoning, tools, APIs, and peer agents form one compositional attack surface; a weakness at any layer can propagate to others.
- **Bound blast radius by default.** Deny-by-default tool access, non-transferable sessions, and **no transitive trust** between agents limit harm when [prompt injection](/go/promptinjection/) or misalignment occurs.


Further links:
- For more details on the agentic AI threats, see the [Agentic AI threats and mitigations, from the GenAI security project](https://genai.owasp.org/resource/agentic-ai-threats-and-mitigations/).
- For a more general discussion of Agentic AI, see [this article from Chip Huyen](https://huyenchip.com/2025/01/07/agents.html).
- The [testing section](/go/testing/) discusses more about agentic AI red teaming and links to the collaboration between CSA and the Exchange: the Agentic AI red teaming guide.
- [OWASP Agentic AI security top 10](https://genai.owasp.org/resource/owasp-top-10-for-agentic-applications-for-2026/) plus [Rock's blog on it](https://www.rockcybermusings.com/p/owasp-top-10-agentic-applications-security-guide)
- [Microsoft Pulse report on Agentic security](https://www.microsoft.com/en-us/security/security-insider/emerging-trends/cyber-pulse-ai-security-report)


### RAG systems overview
>Category: discussion  
>Permalink: https://owaspai.org/go/ragoverview/

Retrieval-Augmented Generation (RAG) systems retrieve data at inference time and insert it into the model's input to ground its output. This is the most common form of **augmentation data** discussed throughout the Exchange, alongside system prompts and agent memory — see the augmentation-data branch of the [threat model](/go/threatmodel/).

An example of RAG is when you ask a company chatbot about things that are in company documents. The AI model has not been trained on those documents, but the RAG system looks through them for information relevant to your question, and gives it to the AI, together with your question. The model learns in the same go as it gets the question - which is why this is called 'in-context learning'.

A typical RAG pipeline has five stages, each with a distinct trust boundary:
1. **Ingestion**: source documents (files, wikis, tickets, web pages, emails) are collected.
2. **Indexing**: documents are chunked, embedded, and stored in a vector store or search index.
3. **Retrieval**: a query (often derived from user input) is used to fetch the top-matching chunks.
4. **Augmentation**: retrieved chunks are inserted into the model's prompt.
5. **Generation**: the model produces output based on the augmented prompt.

RAG is not a separate threat landscape — the same asset/impact model applies (see the [threats overview](/go/threatsoverview/) and [AI security matrix](/go/aisecuritymatrix/)). This section highlights where RAG concentrates existing threats, and where it introduces attack surface that a plain chatbot or single-document-in-context system doesn't have.

Below is a diagram explaining RAG, with [OpenCRE](opencre.org/chatbot) as an example: 
1. You ask a question on security.
2. The system finds relevant information in the security standards in OpenCRE
3. That relevant information is added to your question to form a prompt to an LLM that answers your question using primarily the information plus what it has learned by reading the internet.
[![](/images/opencrechat.png?v=1)](/images/opencrechat.png?v=3)


**Why RAG changes the picture:**
- **Access control and retrieval scope frequently diverge.** The vector store rarely enforces the same per-document ACLs as the source system it was built from, which creates a confused-deputy pattern: the model (and by extension the user) can end up retrieving chunks the user was never authorized to see.
- The **corpus itself becomes an asset** with its own confidentiality, integrity and availability requirements — often larger, less curated, and more frequently updated than training data, and often assembled from many contributors with different trust levels.
- **Retrieval is a second, mostly invisible input channel.** The user only sees their own query; the model also sees whatever the retriever selected. Any content that can enter the index — a shared drive, a ticketing system, a public wiki, a crawled web page — is a potential attack surface, whether or not the current user could reach it directly.

**Key threats to consider, mapped to existing threat categories**
- **[Indirect prompt injection](/go/indirectpromptinjection/)**: an attacker plants instructions in a document that later gets ingested, indexed, and retrieved into another user's prompt — the classic RAG attack. Reachability depends only on getting content into the corpus, not on querying the system directly. This is the most consequential RAG-specific instance of prompt injection.
- **[Data poisoning](/go/datapoison/) of the retrieval corpus**: an attacker with write access to a source (or to the crawl/ingestion pipeline) inserts or edits documents to bias what gets retrieved and surfaced as "fact" — closer to a persistent integrity attack on the corpus than a one-off injection.
- **[Augmentation data manipulation](/go/augmentationdatamanipulation/)**: broader than poisoning — includes manipulating chunking, embeddings, or metadata (e.g., forging a source field or timestamp) to change what gets retrieved or how much the model trusts it, without touching the underlying document. Special forms:
  -  A special form of Augmentation data manipulation is **Vector index manipulation**: the index is a distinct asset from the corpus — an attacker who can write to it directly (misconfigured or default-open vector database, over-privileged ingestion service) can change what gets retrieved without touching a single source document. This is an integrity threat in its own right, not just a downstream effect of corpus poisoning.
  - Another special form of Augmentation data manipulation is an attack that prevents augmentation data being used: **Unsafe fallback on component failure**. If retrieval, an access-control check, or hash verification fails and the system falls back to answering from model memory alone, filtering nothing, or serving a stale cached response, every control above this point in the pipeline is silently bypassed. This is an availability/integrity trade-off attackers can deliberately trigger by forcing failures.
- **[Disclosure in output](/go/disclosureinoutput/)**: retrieval crossing an authorization boundary — cross-tenant leakage, retrieval of documents the querying user lacks permission for, or an attacker crafting queries to enumerate corpus contents (membership-inference-style probing of the index rather than the model).
- **[Input data leak](/go/inputdataleak/)**: user prompts are sent to an AI while possibly crossing a trust boundary - for example when sent to a commercial cloud AI. Furthermore, prompts often logged for debugging or evaluation. This data can leak in-transit and at rest.
- **[Direct augmentation data leak](/go/augmentationdataleak/)**: attack surface for the augmentation data consists of the retrieval corpus and logs, for example a log of the final input to the model. Special forms:
  - A special form of leaking augmentation data is **Embedding inversion**: an attacker with direct access to the vector store (not the model API) can attempt to reconstruct the original text from a stored embedding vector. This is mechanically distinct from [model inversion and membership inference](/go/modelinversionandmembership/) — that threat reconstructs training data through iterative query optimization against the model; embedding inversion requires no model queries at all, only read access to the stored vectors, making the vector store itself a direct confidentiality target independent of the model.
  - Another special form of leaking augmentation data is **Incomplete data deletion propagation**: deleting or de-permissioning a source document doesn't automatically remove its chunks, embeddings, or cached responses — an "authorized deletion" that isn't cascaded leaves the same data reachable through the retriever, which is both a [disclosure](/go/disclosureinoutput/) risk and, where regulated data is involved, a compliance failure.
- **[Output contains conventional injection](/go/outputcontainsconventionalinjection/)**: retrieved content carrying markup, scripts, or malicious links that get echoed into the model's output and rendered downstream (XSS, Markdown-based exfiltration links, etc.) — the RAG-specific path into this existing threat.
- **[AI resource exhaustion](/go/airesourceexhaustion/)**: oversized or adversarially crafted documents at ingestion time, or queries engineered to force expensive retrieval/re-ranking, degrading availability.


**The lethal trifecta, applied to RAG**

RAG is frequently the "data" leg of the [lethal trifecta](/go/agenticaioverview/) described in the Agentic AI overview: attacker-influenced data reaching the model (via indirect prompt injection through a retrieved chunk), access to sensitive data (the corpus itself, or other documents reachable through the same retriever), and an ability to send data out (an agent action, or an exfiltration channel embedded in the output). A RAG system doesn't need to be "agentic" in the action-triggering sense for this to matter — read access to a sensitive corpus plus an output channel a user can observe (e.g., a rendered link) is enough.

**Threat-model questions specific to RAG** (extending the decision tree in [risk analysis](/go/threatmodel/)):
- Does your system insert retrieved data into the model's input? → consider [indirect prompt injection](/go/indirectpromptinjection/) and [augmentation data manipulation](/go/augmentationdatamanipulation/).
- Can anyone other than trusted engineers add, edit, or influence documents that end up in the corpus (shared drives, tickets, web crawls, user uploads)? → consider [data poisoning](/go/datapoison/) of the corpus, and treat the ingestion pipeline itself as a threat surface.
- Does retrieval scope match the source documents' access control, per user/session? → if not, consider augmentation data leak via authorization mismatch — see [disclosure in output](/go/disclosureinoutput/).
- Is the corpus, embedding model, or vector-store service provided by a third party? → apply [supply chain management](/go/supplychainmanage/).
- Can retrieved content reach a rendering context (browser, chat UI with Markdown/HTML) or a downstream action? → consider [output contains conventional injection](/go/outputcontainsconventionalinjection/) and, if the system can act on retrieved content, cross-reference the [Agentic AI overview](/go/agenticaioverview/).
- Does anything other than the ingestion pipeline have write access to the vector index? → consider vector index integrity as a distinct threat from corpus poisoning.
- Do responses carry verifiable source attribution (which chunks, which documents, with what hash)? → if not, a poisoning or staleness incident may be undetectable after the fact.
- What does the system do when retrieval, an access-control check, or hash verification fails? → if it falls back to unfiltered or cached behavior, every upstream control can be bypassed by deliberately triggering that failure.
- When a source document is deleted or de-permissioned, is that propagated to its chunks, embeddings, and cached responses? → an uncascaded deletion leaves the data reachable through the retriever.

**Controls**: the [periodic table of AI security](/go/periodictable/) already lists the applicable controls per threat above; no RAG-specific control category is needed. Attention points:
- Apply [augmentation data confidentiality/integrity](/go/augmentationdataintegrity/) and [input segregation](/go/inputsegregation/) specifically to the retrieval channel, treating the corpus with the same rigor as [training data](/go/datapoison/) — access-controlled, versioned, and attributable — and applying fail-closed defaults at every pipeline stage rather than only at the model boundary.
- [Supply chain management](/go/supplychainmanage/) requires extra attention when using third-party or externally hosted embedding models, vector-store services, or ingestion connectors.
- For the [#MONITOR USE](/go/monitoruse/) control: if a RAG response doesn't carry verifiable provenance (which chunks, from which documents, with what hash), there's no way to detect after the fact whether a poisoned or stale document influenced an answer — this turns an otherwise detectable [data poisoning](/go/datapoison/) incident into an undetectable one.

For the full threat and control picture, see the [threats overview](/go/threatsoverview/) and the [periodic table](/go/periodictable/).  
This section highlights RAG-specific attention points only — not a separate threat landscape.


### <a name="ai-security-matrix">AI セキュリティマトリクス</a>
>カテゴリ: ディスカッション  
>パーマリンク: https://owaspai.org/go/aisecuritymatrix/

以下の AI セキュリティマトリクス (クリックで拡大) は、主要な脅威とリスクを、タイプと影響の順に示しています。
[![](https://raw.githubusercontent.com/OWASP/www-project-ai-security-and-privacy-guide/main/assets/images/OwaspAIsecuritymatrix.png?v=3)](https://raw.githubusercontent.com/OWASP/www-project-ai-security-and-privacy-guide/main/assets/images/OwaspAIsecuritymatrix.png?v=3)

Clickable version, based on the [Periodic table](/go/periodictable/):
<table><thead>
<tr><th>Asset &amp; Impact</th><th>Attack surface with lifecycle</th><th>Threat/Risk category</th></tr>
</thead><tbody>
<tr><td rowspan="7">Model behaviour Integrity</td><td rowspan="3">Runtime -Model use (provide input/ read output)</td><td><a href="/go/directpromptinjection/">Direct prompt injection</a></td></tr>
<tr>                                         <td><a href="/go/indirectpromptinjection/">Indirect prompt injection</a></td></tr>
<tr>                                         <td><a href="/go/evasion/">Evasion</a> (e.g., adversarial examples)</td></tr>
<tr>                                         <td>Runtime - Break into deployed model</td><td><a href="/go/runtimemodelpoison/">Model poisoning runtime</a> (reprogramming)</td></tr>
<tr><td rowspan="2">Development -Engineering environment</td><td><a href="/go/devmodelpoison/">Direct development-environment model poisoning</a></td></tr>
<tr>                                         <td><a href="/go/datapoison/">Data poisoning of train/finetune data</a></td></tr>
<tr><td>Development - Supply chain</td><td><a href="/go/supplymodelpoison/">Supply-chain model poisoning</a></td></tr>
<tr><td rowspan="3">Training data Confidentiality</td><td rowspan="2">Runtime - Model use</td><td><a href="/go/disclosureinoutput/">Disclosure in output</a></td></tr>
<tr><td><a href="/go/modelinversionandmembership/">Model inversion / Membership inference</a></td></tr>
<tr><td>Development - Engineering environment</td><td><a href="/go/devdataleak/">Development-time data leak</a></td></tr>
<tr><td rowspan="3">Model confidentiality</td><td>Runtime - Model use</td><td><a href="/go/modelexfiltration/">Model exfiltration</a> (input-output harvesting)</td></tr>
<tr><td>Runtime - Break into deployed model</td><td><a href="/go/runtimemodelleak/">Direct runtime model leak</a></td></tr>
<tr><td>Development - Engineering environment</td><td><a href="/go/devmodelleak/">Direct development-time model-leak</a></td></tr>
<tr><td>Model behaviour Availability</td><td>Model use</td><td><a href="/go/airesourceexhaustion/">AI resource exhaustion</a></td></tr>
<tr><td>Model input data Confidentiality</td><td>Runtime - All IT</td><td><a href="/go/inputdataleak/">Input data leak</a></td></tr>
<tr><td>Any asset, CIA</td><td>Runtime-All IT</td><td><a href="/go/outputcontainsconventionalinjection/">Output contains conventional injection</a></td></tr>
<tr><td>Any asset, CIA</td><td>Runtime - All IT</td><td>Generic runtime security threats</td></tr>
<tr><td>Any asset, CIA</td><td>Runtime - All IT</td><td>Generic development-environment and supply-chain threats</td></tr>
</tbody></table>


---

## コントロールの概要
>カテゴリ: ディスカッション  
>パーマリンク: https://owaspai.org/go/controlsoverview/

**Select and implement controls with care**  
The AI exchange lists a number of controls to mitigate risks of attack. Be aware that many of the controls are expensive to implement and are subject to trade-offs with other AI properties that can affect correctness and normal operations of the model. Particularly, controls that involve changes to the learning process and data distributions can have un-intended downstream side effects, and must be considered and introduced with care.

**Scope of controls**
In the AI Exchange we focus on AI-specific threats and their corresponding controls. Some of the controls are AI-specific (e.g., adding noise to the training set) and others are not (e.g., encrypting the training database). We refer to the latter as 'conventional controls'. The Exchange focuses on the details of the AI-specific controls because the details of conventional controls are specified elsewhere - see for example [OpenCRE](https://opencre.org). We do provide AI-specific aspects of those controls, for example that protection of model parameters can be implemented using a Trusted Execution Environment.

### From general risks to controls
The table below gives practitioners a compact way to move from a general AI risk area to the relevant AI Exchange control groups. It complements the detailed [Periodic table of AI security](/go/periodictable/), which maps individual threat categories to specific controls.

| Risk area | Typical concern | Primary control groups to review |
| --- | --- | --- |
| AI governance and accountability | Unknown AI use, unclear ownership, unmanaged risk decisions, or incomplete compliance coverage | [AI PROGRAM](/go/aiprogram/), [SEC PROGRAM](/go/secprogram/), [CHECK COMPLIANCE](/go/checkcompliance/), [SEC EDUCATE](/go/seceducate/) |
| AI development lifecycle | AI engineering work is separated from secure development, software quality, model traceability, or risk management | [DEV PROGRAM](/go/devprogram/), [SECDEV PROGRAM](/go/secdevprogram/), [CONTINUOUS VALIDATION](/go/continuousvalidation/), [UNWANTED BIAS TESTING](/go/unwantedbiastesting/), [DISCRETE](/go/discrete/), [DEV SECURITY](/go/devsecurity/), [SEGREGATE DATA](/go/segregatedata/) |
| Data and model supply chain | Untrusted data, third-party models, external hosting, or inherited vulnerabilities enter the AI system | [SUPPLY CHAIN MANAGE](/go/supplychainmanage/), [DATA QUALITY CONTROL](/go/dataqualitycontrol/)|
| Sensitive data exposure | Training data, prompts, outputs, embeddings, logs, or augmentation data may reveal confidential or personal data | [DATA MINIMIZE](/go/dataminimize/), [ALLOWED DATA](/go/alloweddata/), [SHORT RETAIN](/go/shortretain/), [OBFUSCATE TRAINING DATA](/go/obfuscatetrainingdata/), [SENSITIVE OUTPUT HANDLING](/go/sensitiveoutputhandling/), [SMALL MODEL](/go/smallmodel/), [MODEL INPUT CONFIDENTIALITY](/go/modelinputconfidentiality/), [AUGMENTATION DATA CONFIDENTIALITY](/go/augmentationdataconfidentiality/) |
| Manipulated model behavior | Adversarial inputs, prompt injection, poisoned data, or compromised models can change intended behavior | [OVERSIGHT](/go/oversight/), [LEAST MODEL PRIVILEGE](/go/leastmodelprivilege/), [MODEL ALIGNMENT](/go/modelalignment/), [PROMPT INJECTION I/O HANDLING](/go/promptinjectioniohandling/), [INPUT SEGREGATION](/go/inputsegregation/), [ANOMALOUS INPUT HANDLING](/go/anomalousinputhandling/), [EVASION INPUT HANDLING](/go/evasioninputhandling/), [EVASION ROBUST MODEL](/go/evasionrobustmodel/), [TRAIN ADVERSARIAL](/go/trainadversarial/), [ADVERSARIAL ROBUST DISTILLATION](/go/adversarialrobustdestillation/), [POISON ROBUST MODEL](/go/poisonrobustmodel/) |
| Runtime resilience and abuse | Attackers can perform input attacks | [MONITOR USE](/go/monitoruse/), [RATE LIMIT](/go/ratelimit/), [MODEL ACCESSS CONTROL](/go/modelaccesscontrol/), [ANOMALOUS INPUT HANDLING](/go/anomalousinputhandling/), [DOS INPUT VALIDATION](/go/dosinputvalidation/), [LIMIT RESOURCES](/go/limitresources/), [UNWANTED INPUT SERIES HANDLING](/go/unwantedinputserieshandling/), and see Manipulated model behaviour for controls against those input attacks |
| Ready-made or externally hosted models | The organization depends on a provider, external model hosting, or user-facing "shadow AI" alternatives | [SUPPLY CHAIN MANAGE](/go/supplychainmanage/),  [DATA MINIMIZE](/go/dataminimize/), [ALLOWED DATA](/go/alloweddata/) |

### 脅威マップとコントロール - 全般
以下のマップは AI Exchange のコントロールをグループに分け、これらのグループを対応する脅威とともに適切なライフサイクルに配置したものです。
[![](https://raw.githubusercontent.com/OWASP/www-project-ai-security-and-privacy-guide/main/content/ai_exchange/static/images/threatscontrols.png?v=2)](https://raw.githubusercontent.com/OWASP/www-project-ai-security-and-privacy-guide/main/content/ai_exchange/static/images/threatscontrols.png?v=2)

### Essential categories of controls
The controls for AI security can be divided into four essential categories and 8 essential sub categories, linking to over 50 individual controls discussed in depth at the Exchange (copied from the [Essentials section](go/essentials/):

**Manage**:
- Extend existing **Governance, Risk, and Compliance** - in order to secure AI, you need overview, analysis, policy, training, responsibilities, and control:
  > [AI PROGRAM](/go/aiprogram/ ), [DEV PROGRAM](/go/devprogram/), [CHECK COMPLIANCE](/go/checkcompliance/), [SEC EDUCATE](/go/seceducate/)
- Extend **Supply chain management** to incorporate suppliers providing data, models, and hosting
  > [Supply chain management](/go/supplychainmanage/)
- Extend existing **conventional security controls** to protect the AI-specific assets
  - Managing security:
    > [SEC PROGRAM](/go/secprogram/), [SECDEV PROGRAM](/go/secdevprogram/)
  - Development-time (model, data, and documentation):
    > [DEV SECURITY](/go/devsecurity/), [SEGREGATE DATA](/go/segregatedata/), [DISCRETE](/go/discrete/)
  - Runtime: (model storage, model use, augmentation data (including system prompts), and model input/output):  
    > [MODEL ACCESS CONTROL](/go/modelaccesscontrol/), [RUNTIME MODEL INTEGRITY](/go/runtimemodelintegrity/), [RUNTIME MODEL IO INTEGRITY](/go/runtimemodeliointegrity/), [RUNTIME MODEL CONFIDENTIALITY](/go/runtimemodelconfidentiality/), [MODEL INPUT CONFIDENTIALITY](/go/modelinputconfidentiality/), [ENCODE MODEL OUTPUT](/go/encodemodeloutput/), [LIMIT RESOURCES](/go/limitresources/), [AUGMENTATION DATA CONFIDENTIALITY](/go/augmentationdataconfidentiality/), [AUGMENTATION DATA INTEGRITY](/go/augmentationdataintegrity/), [CONF COMPUTE](/go/confcompute/), [MODEL OBFUSCATION](/go/modelobfuscation/)   

**Have resilient models**:
- Apply **data/model engineering controls** during model development for resilience against input attacks. This is the work of data and model engineers. Input attacks include triggering poisoned models - which of course can also be mitigated by preventing the model being poisoned using conventional controls:
  > [MODEL ALIGNMENT](/go/modelalignment/), [FEDERATED LEARNING](/go/federatedlearning/), [CONTINUOUS VALIDATION](/go/continuousvalidation/), [UNWANTED BIAS TESTING](/go/unwantedbiastesting/), [EVASION ROBUST MODEL](/go/evasionrobustmodel/), [POISON ROBUST MODEL](/go/poisonrobustmodel/), [TRAIN ADVERSARIAL](/go/trainadversarial/), [TRAIN DATA DISTORTION](/go/traindatadistortion/), [ADVERSARIAL ROBUST DISTILLATION](/go/adversarialrobustdistillation/), [MODEL ENSEMBLE](/go/modelensemble/), [MORE TRAINDATA](/go/moretraindata/), [SMALL MODEL](/go/smallmodel/), [DATA QUALITY CONTROL](/go/dataqualitycontrol/)

**Watch:**
- Apply **Model I/O handling** for runtime filtering, stopping or alerting to suspicious input or output. It is typically the territory of data and model engineers e.g. data scientists, involving elements from mathematics, statistics, linguistics and machine learning:
  > [ANOMALOUS INPUT HANDLING](/go/anomalousinputhandling/), [EVASION INPUT HANDLING](/go/evasioninputhandling/), [UNWANTED INPUT SERIES HANDLING](/go/unwantedinputserieshandling/), [PROMPT INJECTION I/O HANDLING](/go/promptinjectioniohandling/), [DOS INPUT VALIDATION](/go/dosinputvalidation/), [INPUT DISTORTION](/go/inputdistortion/), [SENSITIVE OUTPUT HANDLING](/go/sensitiveoutputhandling/), [OBSCURE CONFIDENCE](/go/obscureconfidence/), [RATE LIMIT](/go/ratelimit/)
 - **Monitoring** of model inference - extending <odel I/O handing, Oversight (see below) and overlooking general usage of the AI system:
   > [MONITOR USE](/go/monitoruse/)

**Limit:**   
- **Minimize or obfuscate sensitive data** because a model can accidentally leak daa or be misled to:
  > ([DATA MINIMIZE](/go/dataminimize/), [ALLOWED DATA](/go/alloweddata/), [SHORT RETAIN](/go/shortretain/), [OBFUSCATE TRAINING DATA](/go/obfuscatetrainingdata/))
- **Limit model behaviour**  because a model can accidentally make a mistake or be misled to:
  > [OVERSIGHT](/go/oversight/), [LEAST MODEL PRIVILEGE](/go/leastmodelprivilege/), [AI TRANSPARENCY](/go/aitransparency/), [EXPLAINABILITY](/go/explainability/), [CONTINUOUS VALIDATION](/go/continuousvalidation/), [UNWANTED BIAS TESTING](/go/unwantedbiastesting/)


すべての脅威とコントロールについては AI Exchange の対応する脅威セクションでより詳細に説明します。

### Threat map with controls - ready-made model
>Category: discussion  
>Permalink: https://owaspai.org/go/readymademodel/

If possible, and depending on price, organisations can prefer to use a ready-made model, instead of training or fine-tuning themselves. For example: an open source model to detect people in a camera image, or a general purpose LLM such as Google Gemini, OpenAI ChatGPT, Anthropic Claude, Alibaba QWen, Deepseek, Mistral, Grok or Falkon. Training such models yourself can cost millions of dollars, requires deep expertise and vast amounts of data.  

The provider (e.g., OpenAI) has done the training/fine-tuning and therefore is responsible for part of security. Hence, proper supply chain management regarding the model provider is required. 

The following deployment options apply for ready-made models:
- Closed source model, hosted by the provider - for the largest models typically the only available option
- Self-hosted: Open source model (open weights) deployed on-premise (most secure) or in the virtual private cloud (secure if the cloud provider is trusted) - these options provide more security and may be the best option cost-wise, but do not support the largest models
- Open source model (open weights) at a paid hosting service - convenient

**Self-hosted**

The map below shows threats and controls of a ready-made model in a self-hosting situation.

[![AI Security Threats and controls - GenAI as-is](https://raw.githubusercontent.com/OWASP/www-project-ai-security-and-privacy-guide/main/content/ai_exchange/static/images/threatscontrols-readymodel-selfhosted.png?v=2)](https://raw.githubusercontent.com/OWASP/www-project-ai-security-and-privacy-guide/main/content/ai_exchange/static/images/threatscontrols-readymodel-selfhosted.png?v=2)


**External-hosted**

If the model is hosted externally, security largely depends on how the supplier handles data, including the security configuration. 
Some relevant questions to ask here include: 

1. Where does the model run?  
Is the model running in the vendor's processes or in your own virtual private cloud? Some vendors say you get a 'private instance', but that may refer to the API, and not the model. If the model runs on the cluster operated by your vendor, your data leaves your environment in clear text. Vendors will minimize storage and transfer, but they may log and monitor. 

2. What are the data retention rules?  
Has a court required the vendor to retain logs for litigation? This happened to OpenAI in the US for a period of time.

3. What is exactly logged and monitored?  
Read the small print.
Is logging enabled, and if so, what is logged?
And what is monitored - by operators or by algorithms? And in the case of monitoring algorithms: how is that infrastructure protected? Some vendors allow you to opt out of logging, but only with specific licenses. 

4. Is your input used for training?  
This is a common fear, but in the vast majority of cases the input is not used. If vendors would do this secretly, it would get out because there are ways to tell.

If you can't accept the risk for certain data, then hosting your own (smaller) model is the safest option. Typically it won't be as good and there's the catch 22.

It is important to realise that a provider-hosted model needs your input data in clear text, because the model must read the data to process it. This means your sensitive data will exist unencrypted outside your infrastructure.  
This is not unique to LLM providers — it is the same for other multi-tenant SaaS services, such as commercial hosted Office suites. Even though providers usually minimise data storage, limit retention, and reduce data movement, the fact remains:
your data leaves your environment in readable form.

When weighing this risk, compare it fairly: the vendor may still protect that environment better than you can protect your own.


The map below shows threats and controls of a ready-made model in an externally hosted situation.

[![AI Security Threats and controls - GenAI as-is](https://raw.githubusercontent.com/OWASP/www-project-ai-security-and-privacy-guide/main/content/ai_exchange/static/images/threatscontrols-readymodel-hosted.png?v=2)](https://raw.githubusercontent.com/OWASP/www-project-ai-security-and-privacy-guide/main/content/ai_exchange/static/images/threatscontrols-readymodel-hosted.png?v=2)

A typical challenge for organizations is to control the use of ready-made-models for general purpose Generative AI (e.g., ChatGPT), since employees typically can access many of them, even for free. Some of these models may not satisfy the organization's requirements for security and privacy. Still, employees can be very tempted to use them with the lack of a better alterative, sometimes referred to as _shadow AI_. The best solution for this problem is to provide a good alternative in the form of an AI model that has been deployed and configured in a secure and privacy-preserving way, of sufficient quality, and complying with the organization's values and policies. In addition, the risks of shadow AI need to be made very clear to users.

### <a name="periodic-table-of-ai-security">AI セキュリティの周期表</a>
>カテゴリ: ディスカッション  
>パーマリンク: https://owaspai.org/go/periodictable/

OWASP AI Exchange によって作成された以下の表は、AI に対するさまざまな脅威と、それに対して使用できるコントロールを示しています。すべての資産、影響、攻撃対象領域について整理しており、AI Exchange ウェブサイトの包括的なカバレッジへのディープリンクを付与しています。
[一般的なガバナンスコントロール](1_general_controls.md#11-general-governance-controls) はすべての脅威に適用されることに注意してください。

<table><thead>
<tr><th>資産と影響</th><th>ライフサイクルと攻撃対象領域</th><th>脅威/リスクのカテゴリ</th><th>コントロール</th></tr>
</thead><tbody>
<tr><td rowspan="7">モデル動作の完全性</td><td rowspan="3">ランタイム - モデル使用 (入力の提供 / 出力の読み取り)</td><td><a href="2_threats_through_use.md#221-direct-prompt-injection">直接的プロンプトインジェクション</a></td><td><a href="1_general_controls.md#13-controls-to-limit-the-effects-of-unwanted-behaviour">望ましくない動作の制限</a>, <a href="2_threats_through_use.md#MONITOR-USE">監視</a>, <a href="2_threats_through_use.md#RATE-LIMIT">レート制限</a>, <a href="2_threats_through_use.md#MODEL-ACCESS-CONTROL">モデルアクセス制御</a> プラス:, <a href="2_threats_through_use.md#PROMPT-INJECTION-IO-HANDLING">プロンプトインジェクション I/O 処理</a>, <a href="2_threats_through_use.md#MODEL-ALIGNMENT">モデルアラインメント</a></td></tr>
<tr>                                         <td><a href="2_threats_through_use.md#222-indirect-prompt-injection">間接的プロンプトインジェクション</a></td><td><a href="1_general_controls.md#13-controls-to-limit-the-effects-of-unwanted-behaviour">望ましくない動作の制限</a>, <a href="2_threats_through_use.md#PROMPT-INJECTION-IO-HANDLING">プロンプトインジェクション I/O 処理</a>, <a href="2_threats_through_use.md#INPUT-SEGREGATION">入力セグリゲーション</a></td></tr>
<tr>                                         <td><a href="2_threats_through_use.md#21-evasion">回避</a> (例: 敵対的事例)</td><td><a href="1_general_controls.md#13-controls-to-limit-the-effects-of-unwanted-behaviour">望ましくない動作の制限</a>, <a href="2_threats_through_use.md#MONITOR-USE">監視</a>, <a href="2_threats_through_use.md#RATE-LIMIT">レート制限</a>, <a href="2_threats_through_use.md#MODEL-ACCESS-CONTROL">モデルアクセス制御</a> 追補:<br><br><a href="2_threats_through_use.md#ANOMALOUS-INPUT-HANDLING">異常な入力処理</a>, <a href="2_threats_through_use.md#EVASION-INPUT-HANDLING">回避入力処理</a>, <a href="2_threats_through_use.md#UNWANTED-INPUT-SERIES-HANDLING">望ましくない入力シリーズ処理</a>, <a href="2_threats_through_use.md#EVASION-ROBUST-MODEL">回避ロバストモデル</a>, <a href="2_threats_through_use.md#TRAIN-ADVERSARIAL">敵対的トレーニング</a>, <a href="2_threats_through_use.md#INPUT-DISTORTION">入力の歪曲</a>, <a href="2_threats_through_use.md#ADVERSARIAL-ROBUST-DISTILLATION">敵対的ロバスト蒸留</a></td></tr>
<tr>                                         <td>ランタイム - デプロイされるモデルへの侵入</td><td><a href="4_runtime_application_security_threats.md#42-direct-runtime-model-poisoning">直接的な実行時モデルポイズニング</a> (リプログラミング)</td><td><a href="1_general_controls.md#13-controls-to-limit-the-effects-of-unwanted-behaviour">望ましくない動作の制限</a>, <a href="4_runtime_application_security_threats.md#RUNTIMEMODELINTEGRITY">実行時のモデルの完全性</a>, <a href="4_runtime_application_security_threats.md#RUNTIMEMODELIOINTEGRITY">実行時のモデル入出力の完全性</a></td></tr>
<tr><td rowspan="2">開発時 - エンジニアリング環境</td><td><a href="3_development_time_threats.md#312-development-time-model-poisoning">直接的な開発時モデルポイズニング</a></td><td><a href="1_general_controls.md#13-controls-to-limit-the-effects-of-unwanted-behaviour">望ましくない動作の制限</a>, <a href="3_development_time_threats.md#DEVSECURITY">開発環境のセキュリティ</a>, <a href="3_development_time_threats.md#SEGREGATEDATA">データセグリゲーション</a>, <a href="3_development_time_threats.md#FEDERATEDLEARNING">連合学習</a>, <a href="3_development_time_threats.md#SUPPLYCHAINMANAGE">サプライチェーンマネジメント</a> 追補:<br><br><a href="3_development_time_threats.md#MODELENSEMBLE">モデルアンサンブル</a></td></tr>
<tr>                                         <td><a href="3_development_time_threats.md#311-data-poisoning">トレーニングデータやファインチューニングデータのデータポイズニング</a></td><td><a href="1_general_controls.md#13-controls-to-limit-the-effects-of-unwanted-behaviour">望ましくない動作の制限</a>, <a href="3_development_time_threats.md#DEVSECURITY">開発環境のセキュリティ</a>, <a href="3_development_time_threats.md#SEGREGATEDATA">データセグリゲーション</a>, <a href="3_development_time_threats.md#FEDERATEDLEARNING">連合学習</a>, <a href="3_development_time_threats.md#SUPPLYCHAINMANAGE">サプライチェーンマネジメント</a> 追補:<br><br><a href="3_development_time_threats.md#MODELENSEMBLE">モデルアンサンブル</a> 追補:<br><br><a href="3_development_time_threats.md#MORETRAINDATA">トレーニングデータの増強</a>, <a href="3_development_time_threats.md#DATAQUALITYCONTROL">データ品質コントロール</a>, <a href="3_development_time_threats.md#TRAINDATADISTORTION">トレーニングデータの歪曲</a>, <a href="3_development_time_threats.md#POISONROBUSTMODEL">ポイズンロバストモデル</a>, <a href="2_threats_through_use.md#TRAIN-ADVERSARIAL">敵対的トレーニング</a></td></tr>
<tr><td>開発時 - サプライチェーン</td><td><a href="3_development_time_threats.md#313-supply-chain-model-poisoning">サプライチェーンのモデルポイズニング</a></td><td><a href="1_general_controls.md#13-controls-to-limit-the-effects-of-unwanted-behaviour">望ましくない動作の制限</a>,<br>サプライヤ: <a href="3_development_time_threats.md#DEVSECURITY">開発環境のセキュリティ</a>, <a href="3_development_time_threats.md#SEGREGATEDATA">データセグリゲーション</a>, <a href="3_development_time_threats.md#FEDERATEDLEARNING">連合学習</a><br><br>プロデューサー: <a href="3_development_time_threats.md#SUPPLYCHAINMANAGE">サプライチェーンマネジメント</a> 追補:<br><br><a href="3_development_time_threats.md#MODELENSEMBLE">モデルアンサンブル</a></td></tr>
<tr><td rowspan="3">トレーニングデータの機密性</td><td rowspan="2">ランタイム - モデル使用</td><td><a href="2_threats_through_use.md#231-disclosure-of-sensitive-data-in-model-output">出力での開示</a></td><td><a href="1_general_controls.md#12-general-controls-for-sensitive-data-limitation">機密データ制限</a> (データの最小化, 短期保持, トレーニングデータの難読化) 追補:<br><br><a href="2_threats_through_use.md#MONITOR-USE">監視</a>, <a href="2_threats_through_use.md#RATE-LIMIT">レート制限</a>, <a href="2_threats_through_use.md#MODEL-ACCESS-CONTROL">モデルアクセス制御</a> 追補:<br><br><a href="2_threats_through_use.md#SENSITIVEOUTPUTHANDLING">機密性の高い出力処理</a></td></tr>
<tr><td><a href="2_threats_through_use.md#232-model-inversion-and-membership-inference">モデル反転とメンバーシップ推論</a></td><td><a href="1_general_controls.md#12-general-controls-for-sensitive-data-limitation">機密データ制限</a> (データの最小化, 短期保持, トレーニングデータの難読化) 追補:<br><br><a href="2_threats_through_use.md#MONITOR-USE">監視</a>, <a href="2_threats_through_use.md#RATE-LIMIT">レート制限</a>, <a href="2_threats_through_use.md#MODEL-ACCESS-CONTROL">モデルアクセス制御</a> 追加:<br><br><a href="2_threats_through_use.md#UNWANTED-INPUT-SERIES-HANDLING">望ましくない入力シリーズ処理</a>, <a href="2_threats_through_use.md#OBSCURE-CONFIDENCE">曖昧な信頼性</a>, <a href="2_threats_through_use.md#SMALL-MODEL">スモールモデル</a></td></tr>
<tr><td>開発時 - エンジニアリング環境</td><td><a href="3_development_time_threats.md#321-development-time-data-leak">直接的なトレーニングデータ漏洩</a></td><td><a href="1_general_controls.md#12-general-controls-for-sensitive-data-limitation">機密データ制限</a> (データの最小化, 短期保持, トレーニングデータの難読化) 追補:<br><br><a href="3_development_time_threats.md#DEVSECURITY">開発環境のセキュリティ</a>, <a href="3_development_time_threats.md#SEGREGATEDATA">データセグリゲーション</a>, <a href="3_development_time_threats.md#FEDERATEDLEARNING">連合学習</a></td></tr>
<tr><td rowspan="3">モデルの機密性</td><td>ランタイム - モデル使用</td><td><a href="2_threats_through_use.md#24-model-exfiltration">モデル抽出</a> (入出力ハーベスティング)</td><td><a href="2_threats_through_use.md#MONITOR-USE">監視</a>, <a href="2_threats_through_use.md#RATE-LIMIT">レート制限</a>, <a href="2_threats_through_use.md#MODEL-ACCESS-CONTROL">モデルアクセス制御</a> 追加:<br><br><a href="2_threats_through_use.md#UNWANTED-INPUT-SERIES-HANDLING">望ましくない入力シリーズ処理</a></td></tr>
<tr><td>ランタイム - デプロイされるモデルへの侵入</td><td><a href="4_runtime_application_security_threats.md#43-direct-runtime-model-leak">直接的な実行時モデル漏洩</a></td><td><a href="4_runtime_application_security_threats.md#RUNTIMEMODELCONFIDENTIALITY">ランタイムモデルの機密性</a>, <a href="4_runtime_application_security_threats.md#MODELOBFUSCATION">モデルの難読化</a></td></tr>
<tr><td>開発時 - エンジニアリング環境</td><td><a href="3_development_time_threats.md#322-direct-development-time-model-leak">直接的な開発時モデル漏洩</a></td><td><a href="3_development_time_threats.md#DEVSECURITY">開発環境のセキュリティ</a>, <a href="3_development_time_threats.md#SEGREGATEDATA">データセグリゲーション</a>, <a href="3_development_time_threats.md#FEDERATEDLEARNING">連合学習</a></td></tr>
<tr><td>モデル動作の可用性</td><td>モデル使用</td><td><a href="2_threats_through_use.md#25-ai-resource-exhaustion">AI リソース枯渇</a> (モデルリソースの枯渇)</td><td><a href="2_threats_through_use.md#MONITOR-USE">監視</a>, <a href="2_threats_through_use.md#RATE-LIMIT">レート制限</a>, <a href="2_threats_through_use.md#MODEL-ACCESS-CONTROL">モデルアクセス制御</a> 追補:<br><br><a href="2_threats_through_use.md#DOS-INPUT-VALIDATION">サービス拒否の入力バリデーション</a>, <a href="2_threats_through_use.md#LIMIT-RESOURCES">リソースの制限</a></td></tr>
<tr><td>モデル入力データの機密性</td><td>ランタイム - すべての IT</td><td><a href="4_runtime_application_security_threats.md#45-input-data-leak">入力データ漏洩</a></td><td><a href="4_runtime_application_security_threats.md#MODELINPUTCONFIDENTIALITY">モデル入力の機密性</a></td></tr>
<tr><td>任意の資産, CIA</td><td>ランタイム - すべての IT</td><td><a href="4_runtime_application_security_threats.md#44-output-contains-conventional-injection">従来のインジェクションを含む出力</a></td><td><a href="4_runtime_application_security_threats.md#ENCODEMODELOUTPUT">モデル出力のエンコード</a></td></tr>
<tr><td>任意の資産, CIA</td><td>ランタイム - すべての IT</td><td>一般的な実行時セキュリティ脅威</td><td>従来のランタイムセキュリティコントロール</td></tr>
<tr><td>任意の資産, CIA</td><td>ランタイム - すべての IT</td><td>一般的な開発環境とサプライチェーンの脅威</td><td>従来の開発セキュリティとサプライチェーンマネジメントコントロール</td></tr>
</tbody></table>


### 詳細セクションにおける脅威とコントロールの構造
>カテゴリ: ディスカッション  
>パーマリンク: https://owaspai.org/go/navigator/

The details of threats and controls are covered in four deep-dive sections, each on a next page at the Exchange, grouping the threats, and discussing the corresponding controls:
- [1. General controls](/docs/1_general_controls)  
- [2. Input threats and controls](/docs/2_threats_through_use/)  
- [3. Development-time threats and controls](/docs/3_development_time_threats/)
- [4. Runtime conventional security threats and controls](/docs/4_runtime_application_security_threats/)  

以下のナビゲータ図は詳細セクションの構造を示し、脅威、コントロール、関連するリスク、適用されるコントロールの種類の間の関係を示しています。
<!-- {{< callout type="info" >}} -->
  画像をクリックすると、クリック可能なリンクを含む PDF を取得できます。
<!-- {{< /callout >}} -->
[![](https://raw.githubusercontent.com/OWASP/www-project-ai-security-and-privacy-guide/main/assets/images/owaspainavigator-thumb.png)](https://github.com/OWASP/www-project-ai-security-and-privacy-guide/raw/main/assets/images/owaspainavigator.pdf)

---

## <a name="how-to-select-relevant-threats-and-controls-risk-analysis">関連する脅威とコントロールをどのように選択するか？　リスク分析</a>
>カテゴリ: ディスカッション  
>パーマリンク: https://owaspai.org/go/riskanalysis/

There are quite a number of threats and controls described in this document. The relevance and severity of each threat and the appropriate controls depend on your specific use case and how AI is deployed within your environment. Determining which threats apply, to what extent, and who is responsible for implementing controls should be guided by a risk assessment based on your architecture and intended use. Simply go to the 'Identifying risks' section below and follow the steps.

**リスクマネジメント入門**  
組織はリスクをいくつかの主要な領域に分類します。戦略、運用、財務、コンプライアンス、評判、テクノロジ、環境、社会、ガバナンス (ESG) です。脅威は一つ以上の脆弱性を悪用するとリスクになります。このリソースで説明しているように、AI の脅威は複数のリスク領域にわたって大きな影響を及ぼす可能性があります。たとえば、AI システムに対する敵対的攻撃は、運用の中断、財務モデルの歪曲、コンプライアンスの問題を引き起こす可能性があります。AI 関連の脅威、リスク、潜在的な影響の概要については [AI セキュリティマトリクス](ai_security_overview.md#ai-security-matrix) を参照してください。

AI システムの一般的なリスクマネジメントは、通常、AI ガバナンス ([AIPROGRAM](1_general_controls.md#AIPROGRAM) を参照) によって推進され、関連する AI システムによるリスクとそれらのシステムに対するリスクの両方を含みます。セキュリティリスク評価は、通常、セキュリティマネジメントシステム ([SECPROGRAM](1_general_controls.md#SECPROGRAM) を参照) によって推進され、このシステムは、AI 資産、AI 脅威、AI システムを含めることが求められます (これらが対応するリポジトリに追加されている場合)。ISO/IEC 27005 はセキュリティリスク管理の国際標準です。

組織は一般的に ISO 31000 または ISO 23894 などの類似の規格に基づくリスクマネジメントフレームワークを採用することがよくあります。これらのフレームワークは下記の四つの主要なステップを通じてリスク管理のプロセスをガイドします。

1. **リスクの特定**:  
組織などに影響を及ぼす可能性のある潜在的なリスクを認識します。
2. **リスクの評価**:  
リスクが顕在化した場合の影響の発生可能性と深刻度を推定することにより、リスク発生の確立を評価し、リスクが顕在化した場合の潜在的な結果を評価する必要があります。発生可能性と深刻度の組み合わせがリスクのレベルを表します。これは一般的に発生可能性と深刻度を組み合わせたヒートマップの形で提示されます。
3. **リスク処置**:  
リスク処置はリスクに対処するための適切な戦略を選択することを意味します。これらの戦略には、リスクの軽減、移転、回避、受容があります。詳細については以下を参照してください。
4. **リスクコミュニケーションとモニタリング**:  
リスク情報を利害関係者と定期的に共有し、リスクマネジメント活動に対する意識と継続的な支援を確保します。効果的なリスク処置を確実に適用します。これには、リスクとその属性 (深刻度、処置計画、オーナーシップ、ステータスなど) の包括的なリストであるリスク登録簿が必要です。これについては以降のセクションでさらに詳しく説明します。
5. 上記のプロセスを定期的に、および変更が必要になったときに、繰り返します。

リスクマネジメントの手順を一つずつ見てきましょう。

### 1. リスクの特定 - 脅威モデルの決定ツリー
>Category: discussion  
>Permalink: https://owaspai.org/go/threatmodel/

The AI Exchange presents a foundational framework of threats and controls. This catalog of threats can be used to identify the risks that apply to a specific AI system, depending on architecture, context, domain and use case.  
NOTE: In this document, we focus on AI-specific risks only - meaning risks to the AI-specific assets.

This subsection takes you through each type of risk impact, and poses questions that will help to determine which threats apply. In addition, it provides guidance to translate that to risks.

There's an AI available that uses all this material to take you through the threat model process: [THREAT ADVISOR](/go/threatadvisor/). Just go to the advisor (requires a Google account) and start by briefly describing your system. It will then interview you. Your data will remain in your own Google workspace.

In essence, this is a 'Threat modeling' process: the bridge between a list of threats and a set of concrete, prioritized risks.  
The threats represent a catalogue of “attacks that could happen” and threat modeling answers three key questions:
1. Which threats theoretically apply to this system?
2. How could they realistically happen?
3. What would the impact be?

The step after that is detailed in the following subsection 2: to look in more detail at likelihood and impact.

The image below represents the AI Exchange threat modelling one-pager. It summarizes the step-by-step decision tree approach from this section. How to use:
1. Walk by each threat 
2. Base on the column ‘When’, determine when that threat applies in theory
3. If the threat applies in theory, use the column ‘Impact’ to help decide whether the risk needs to be treated or not, depending on the level of harm for the use case.

The result: you start big, but you end up with a relatively small list of risks to focus on. 

For example: You don’t have to protect against model inversion attacks that try to steal your training data, if that data isn’t sensitive. It sounds obvious, but I’ve seen many cases of protections in place for threats that effectively don’t matter.

Another example: If your agentic system uses an LLM, then it is in theory susceptible to indirect prompt injection: malicious instructions in untrusted data that  manipulate agent behaviour. But if your only concern is that sensitive company data leaks, and there is no way for the system to send data to an attacker (e.g., email), then this threat remains theoretical. The risk does not have to be treated.

[![](https://raw.githubusercontent.com/OWASP/www-project-ai-security-and-privacy-guide/main/content/ai_exchange/static/images/threatmodelonepager.png)](https://raw.githubusercontent.com/OWASP/www-project-ai-security-and-privacy-guide/main/content/ai_exchange/static/images/threatmodelonepager.png)  


[![](https://raw.githubusercontent.com/OWASP/www-project-ai-security-and-privacy-guide/main/content/ai_exchange/static/images/tn_threattree.png)](https://raw.githubusercontent.com/OWASP/www-project-ai-security-and-privacy-guide/main/content/ai_exchange/static/images/threattree.png)  



**望ましくないモデルの動作のリスクと影響を特定する**

  モデルの動作に関しては、このドキュメントのスコープがセキュリティであるため、攻撃者による操作に焦点を当てています。その他の望ましくない動作の原因には標準的な不正確さ (ハルシネーションなど) や特定のグループに関する望ましくない偏見 (差別) があります。

   > QUESTION: Is the model GenAI (e.g., a Large Language Model) and not classic machine learning or a heuristic model? If Yes:
  - Consider the threat of [direct prompt injection](/go/directpromptinjection/) in case a) an attacker can provide input to the model (e.g., a prompt), and b) the model could theoretically create output that results in harm - for example: offensive output, information leading to harm, or triggering harmful functions (Agentic AI).
    - For risk assessment of direct prompt injection, the first question is: has the model supplier done enough according to your risk appetite. For this, you can check tests that the supplier or others have performed, and when not available: have these tests done based on what harm means in your use case. What you accept, in other words: what you find too much effort in combination with too harmful, depends on your context. If a user wants the AI to say something offensive: do you regard it as a problem if that user succeeds in getting offended? Do you regard it as a problem if users can get a recipe to make poison - given that they can get this from many other AI's out there. See the linked prompt injection section for more details.
  - Consider the threat of [indirect prompt injection](/go/indirectpromptinjection/) when your system inserts untrusted data in a prompt e.g. you retrieve somebody's resume and include it in a prompt, or an agent retrieves data that is untrusted (i.e. may have been manipulated or placed by an attacker).

  
  > QUESTION: Who trains/finetunes the model?
  - The supplier: consider the threat of[Supply chain model poisoning](/go/supplymodelpoison/): obtaining or working with a model that has been manipulated to behave in unintended ways.
    - Mitigation guidance: This is done through proper [supply chain management](/go/supplychainmanage/) (e.g., selecting a trustworthy supplier and verifying the authenticity of the model). This is to gain assurance on the security posture of the provider, meaning the provider prevents model poisoning during development, including data poisoning, and uses uncompromised data. If the risk of data poisoning remains unacceptable, implementing post-training countermeasures can be an option if you have the expertise and if you have access to the model parameters (e.g., open source weights). See [POISONROBUSTMODEL](/go/poisonrobustmodel/). Note that providers are typically not very open about their security countermeasures, which means that it can be challenging to gain sufficient assurance. Regulations will hopefully help achieve more provider transparency. For more details, see [ready-made models](/go/readymademodel/).
  - You: consider the threat of [data poisoning](/go/datapoison/) in the development environment or by obtaining poisoned data from a third party, and consider the threat of attackers altering your model directly using [direct development-time model poisoning](/go/devmodelpoison/).

    Why not train/finetune a model yourself? There are many third party and open source models that may be able to perform the required task, perhaps after some fine-tuning. Organizations often choose external GenAI models because they are typically general purpose, and training is difficult and expensive (often millions of dollars). Fine-tuning of generative AI is also not often performed by organizations given the cost of compute and the complexity involved. Some GenAI models can be obtained and run on your own infrastructure. The reasons for this can be lower cost (if it is an open source model), and the fact that sensitive input information does not have to be sent externally. A reason to use an externally hosted GenAI model can be the quality of the model.
 
 
  > QUESTION: Does your system insert (augment) data to the input of your model, like for example in RAG (Retrieval Augmented Generation), or by inserting data from memory (e.g., stored state for an agent), or by having _system prompts_ (standard instructions to the model that are automatically added to the input) ? If yes: 
  
  - Consider the threat of [augmentation data manipulation](/go/augmentationdatamanipulation/) as this data plays a role in determining the model behaviour.
  - Is this augmentation data stored in a database for the purpose of the AI system (e.g., a vector database)? If Yes: you need to protect against [direct augmentation data leak](/go/augmentationdataleak/). Note that this also counts for system prompts, if they are sensitive.
  - Consult [RAG systems overview](/go/ragsystemsoverview/) for further considerations.

  > QUESTION: Who runs the model?
  - The supplier runs the model: select a trustworthy supplier through [supply chain management](/go/supplychainmanage/), to make sure the deployed model cannot be manipulated through ([runtime model poisoning](/go/runtimemodelpoison/)) - just the way you would expect any supplier to protect their running application from manipulation.
  - You run the model: You need to consider the threat of [runtime model poisoning](/go/runtimemodelpoison/) where attackers change the model that you have deployed.

 > QUESTION: Is the model (predictive AI or Generative AI) used in a classification task (e.g., spam or fraud detection)?
  - Yes: Consider the threat of an [evasion attack](/go/evasion/) in which a user tries to fool the model into a wrong decision using data (not instructions). Here, the level of risk is an important aspect to evaluate - see below. The risk of an evasion attack may be acceptable.
    
**Analysing the risk of unwanted model behaviour**

> QUESTION: Can the model trigger actions (e.g., API calls depending on a model classification output, or an LLM agent that triggers actions or other agents? If Yes:
  - This typically increases the impact of the risks mentioned above, depending on the action. The action can for example be adding an entry to a database, but also closing a watertight door in a ship. The threat is for example prompt injection or augmentation data manipulation, but the risk is that this leads to a specific impact (e.g., exfiltrating data, or un unsafe action in the physical world.)

> QUESTION: IF the model triggers actions, is there an action that is able to send data so it can be seen by an adversary, and is there sensitive data accessible in the system by one of the agents or actions that is reachable by the manipulated agent? If Yes:
  - This combination of 1) manipulated model behaviour, 2) ability for the model to send data, and 3) ability for the model to access sensitive data is called the 'Lethal trifecta'. The impact is: data exfiltration. For more details, see [Agentic threats](/go/agenticaithreats/).

NOTE: a special form of exfiltrating and sending data to an adversary is through [injecting exfiltration in model output](/go/outputcontainsconventionalinjection/): a model is manipulated to output sensitive data in code which sends out sensitive data. This can be javascript executed in a browser (XSS), but more simple: a link to an image on the server of an adversary, where the URL contains the sensitive data. Or in a similar fashion: the output containing a link for the user to click on, to that same server.
  
  In order to assess the level of risk for unwanted model behaviour through manipulation, consider what the motivation of an attacker could be. What could an attacker gain by misleading your model? Just a claim to fame? Could it be a disgruntled employee? Maybe a competitor? What could an attacker gain by a less conspicuous model behaviour attack, like an evasion attack or data poisoning with a trigger? Is there a scenario where an attacker benefits from fooling the model? An example where evasion IS interesting and possible: adding certain words in a spam email so that it is not recognized as such. An example where evasion is not interesting is when a patient gets a skin disease diagnosis based on a picture of the skin. The patient has no interest in a wrong decision, and also the patient typically has no control - well maybe by painting the skin. There are situations in which this CAN be of interest for the patient, for example to be eligible for compensation in case the (faked) skin disease was caused by certain restaurant food. This demonstrates that it all depends on the context whether a theoretical threat is a real threat or not. Depending on the probability and impact of the threats, and on the relevant policies, some threats may be accepted as risk. When not accepted, the level of risk is input to the strength of the controls. For example: if data poisoning can lead to substantial benefit for a group of attackers, then the training data needs to be given a high level of protection.

 **Identify risks with the impace of leaking training data**

 > QUESTION: Do you train/finetune the model yourself?
  - If yes, is the training data sensitive? If so, you need to consider the threats of:
    - [disclosure in model output](/go/disclosureuse/) in case the output can contain the sensitive data
    - [model inversion](/go/modelinversionandmembership/) 
    - [direct training data leak](/go/devdataleak/) from your engineering environment
    - [membership inference](/go/modelinversionandmembership/) - but only when the fact that something or someone was part of the training data constitutes sensitive information. For example, when the training set consists of criminals and their history to predict criminal careers. Membership of that set gives away the person is a convicted or alleged criminal.
    
> QUESTION: do you use insert data into the input (e.g., by using RAG -retrieve data and insert it in the prompt)?
  - Yes: apply the above to your augmentation data, as if it was part of the training set: as the repository data feeds into the model and can therefore be part of the output as well.

  If you don't train/finetune the model, then the supplier of the model is responsible, but not accountable per se, for unwanted content in the training data. This can be poisoned data (see above), data that is confidential, or data that is copyrighted. It is important to check licenses, warranties and contracts for these matters, or accept the risk based on your circumstances.


 **Identify risks with the impact of model theft**

> QUESTION: Do you train/finetune the model yourself and is it intellectual property or susceptible to an Evasion attack (see above)?
  - If yes, then you need to consider the threats:
    - [Model exfiltration](/go/modelexfiltration/)
    - [Direct development-time model leak](/go/devmodelleak/)
    - [Source code/configuration leak](/go/devcodeleak/)
    - [Direct runtime model leak](/go/runtimemodelleak/)
       
 **Identify risks with the impact of leaking input data**
 
> QUESTION: Is your input data sensitive?
  - Protect against [input data leak](/go/inputdataleak/). Especially if the model is run by a supplier, proper care needs to be taken to ensure that this data is minimized and transferred or stored securely. Review the security measures provided by the supplier, including any options to disable logging or monitoring on their end. Realise that most Cloud AI models have your input and output unencrypted in their infrastructure (just like documents in Google Suite and Microsoft 365). If you use the right license and configuration, you can prevent it from being stored or analysed. One risk that remains is that the government of the supplier may be forced to store and keep input and output to serve for subpoenas. If you're using a RAG system, remember that the data you retrieve and inject into the prompt also counts as input data. This often includes sensitive company information or personal data.


 **Identify further risks**

 > QUESTION: Does your model create text output?
  - Protect against [insecure output handling](/go/insecureoutput/), for example, when you display the output of the model on a website and the output contains malicious Javascript.

> ALWAYS DO:
  Make sure to protect against [AI resource exhaustions](/go/denialmodelservice/) (actors overusing your AI causing availability problems and/or high cost)). If your model is run by a supplier, then certain countermeasures may already be in place to address this.

  Since AI systems are software systems, they require appropriate conventional application security and operational security, apart from the AI-specific threats and controls mentioned in this section.

### 2. 発生可能性と影響度の推定によるリスクの評価
To determine the severity of a risk, it is necessary to assess the likelihood of the risk occurring and evaluating the potential consequences should the risk materialize.

**Estimating the Likelihood:**  
Estimating the likelihood and impact of an AI risk requires a thorough understanding of both the technical and contextual aspects of the AI system in scope. The likelihood of a risk occurring in an AI system is influenced by several factors, including the complexity of the AI algorithms, the data quality and sources, the conventional security measures in place, and the potential for adversarial attacks. For instance, an AI system that processes public data is more susceptible to data poisoning and inference attacks, thereby increasing the likelihood of such risks.  A financial institution's AI system, which assesses loan applications using public credit scores, is exposed to data poisoning attacks. These attacks could manipulate creditworthiness assessments, leading to incorrect loan decisions. 

Examples of aspects involved in rating probability:
- Opportunity regarding attacker access (OWASP, FAIR - Factor Analysis for Information Risk)
- Risk of getting caught (FAIR)
- Capabilities/tools/budget (ISO/IEC 27005, OWASP, FAIR)
- Susceptibility of the system (ISO/IEC 27005, FAIR)
- Motive(OWASP, FAIR, ISO/IEC 27005)
- Number of potential attackers(OWASP)
- Data regarding incidents and attempts (ISO/IEC 27005)

**Evaluating the Impact:**
Evaluating the impact of risks in AI systems involves understanding the potential consequences of threats materializing. This includes both the direct consequences, such as compromised data integrity or system downtime, and the indirect consequences, such as reputational damage or regulatory penalties. The impact is often magnified in AI systems due to their scale and the critical nature of the tasks they perform. For instance, a successful attack on an AI system used in healthcare diagnostics could lead to misdiagnosis, affecting patient health and leading to significant legal, trust, and reputational repercussions for the involved entities.

**Prioritizing risks**
The combination of likelihood and impact assessments forms the basis for prioritizing risks and informs the development of Risk Treatment decisions. Commonly organizations use a risk heat map to visually categorize risks by impact and likelihood. This approach facilitates risk communication and  decision-making.  It allows the management to focus on risks with highest severity (high likelihood and high impact).

### 3. リスク処置
Risk treatment is about deciding what to do with the risks: transfer, avoid, accept, or mitigate. Mitigation involves selecting and implementing controls. This process is critical due to the unique vulnerabilities and threats related to AI systems such as  data poisoning, model theft, and adversarial attacks. Effective risk treatment is essential to robust, reliable, and trustworthy AI.

Risk Treatment options are:
  1. **Mitigation**: Implementing controls to reduce the likelihood or impact of a risk. This is often the most common approach for managing AI cybersecurity risks. See the many controls in this resource and the 'Select controls' subsection below.  
    - Example: Enhancing data validation processes to prevent data poisoning attacks, where malicious data is fed into the Model to corrupt its learning process and negatively impact its performance.
  2. **Transfer**: Shifting the risk to a third party, typically through transfer learning, federated learning, insurance or outsourcing certain functions. 
    - Example: Using third-party cloud services with robust security measures for AI model training, hosting, and data storage, transferring the risk of data breaches and infrastructure attacks.
  3. **Avoidance**: Changing plans or strategies to eliminate the risk altogether. This may involve not using AI in areas where the risk is deemed too high.
    - Example: Deciding against deploying an AI system for processing highly sensitive personal data where the risk of data breaches cannot be adequately mitigated.
  4. **Acceptance**: Acknowledging the risk and deciding to bear the potential loss without taking specific actions to mitigate it. This option is chosen when the cost of treating the risk outweighs the potential impact.
    - Example: Accepting the minimal risk of model inversion attacks (where an attacker attempts to reconstruct publicly available input data from model outputs) in non-sensitive applications where the impact is considered low.

### 4. リスクコミュニケーションとモニタリング
Regularly sharing risk information with stakeholders to ensure awareness and support for risk management activities. 

A central tool in this process is the Risk Register, which serves as a comprehensive repository of all identified risks, their attributes (such as severity, treatment plan, ownership, and status), and the controls implemented to mitigate them.  Most large organizations already have such a Risk Register.  It is important to align AI risks and chosen vocabularies from Enterprise Risk Management to facilitate effective communication of risks throughout the organization.  

### 5. Arrange responsibility
For each selected threat, determine who is responsible for addressing it. By default, the organization that builds and deploys the AI system is responsible, but building and deploying may be done by different organizations, and some parts of the building and deployment may be deferred to other organizations, e.g. hosting the model, or providing a cloud environment for the application to run. Some aspects are shared responsibilities.

If some components of your AI system are hosted, then you share responsibility regarding all controls for the relevant threats with the hosting provider. This needs to be arranged with the provider by using a tool like the responsibility matrix. Components can be the model, model extensions, your application, or your infrastructure. See [Threat model of a ready-made model](/go/readymademodel/).

If an external party is not open about how certain risks are mitigated, consider requesting this information and when this remains unclear you are faced with either 1) accept the risk, 2) or provide your own mitigations, or 3) avoid the risk, by not engaging with the third party.

### 6. Verify external responsibilities
For the threats that are the responsibility of other organisations: attain assurance whether these organisations take care of it. This would involve the controls that are linked to these threats.

Example: Regular audits and assessments of third-party security measures.
 
### 7. Select controls
Next, for the threats that are relevant to your use-case and fall under your responsibility, review the associated controls, both those listed directly under the threat (or its parent category) and the general controls, which apply universally. See the [Periodic table](/go/periodictable/) for an overview of which controls mitigate the risks for each threat. For each control, consider its purpose and assess whether it's worth implementing, and to what extent. This decision should weigh the cost of implementation against how effectively the control addresses the threat, along with the level of the associated risk. These factors also influence the order in which you apply controls. Start with the highest-risk threats and prioritize low-cost, quick-win controls (the "low-hanging fruit").

Controls often have quality-related parameters that need to be adjusted to suit the specific situation and level of risk. For example, this could involve deciding how much noise to add to input data or setting appropriate thresholds for anomaly detection. Testing the effectiveness of these controls in a simulation environment helps you evaluate their performance and security impact to find the right balance. This tuning process should be continuous, using insights from both simulated tests and real-world production feedback.

When have you done enough? The AI system is sufficiently secure when all identified risks can be treated, meaning transferred, avoided or accepted, where acceptance in some cases can be done directly, without first taking action, and in other cases require you to implement controls to bring the risk to an acceptable level.

### 8. Residual risk acceptance
In the end, you need to be able to accept the risks that remain regarding each threat, given the controls that you implemented. 

### 9. Further management of the selected controls
(see [SECPROGRAM](/go/secprogram/)), which includes continuous monitoring, documentation, reporting, and incident response.

### 10. Continuous risk assessment
Implement continuous monitoring to detect and respond to new threats. Update the risk management strategies based on evolving threats and feedback from incident response activities.  
Example: Regularly reviewing and updating risk treatment plans to adapt to new vulnerabilities.

---

## ... についてはどうですか？
### 機械学習以外の AI についてはどうですか？
AI を理解するのに役立つ方法は、AI が機械学習 (現在主流の AI タイプ) モデルと _ヒューリスティックモデル_ から構成されていると考えることです。モデルはデータに基づいて計算方法を学習した機械学習モデルであることも、ルールベースのシステムなどの人間の知識に基づいて設計されたヒューリスティックモデルであることもあります。ヒューリスティックモデルは依然としてテストのためにデータを必要とし、場合によっては、人間が導出した知識のさらなる開発と検証をサポートする分析を実施するためにもデータが必要です。
このドキュメントは機械学習に焦点を当てています。とはいえ、ここではヒューリスティックシステムにも適用される、このドキュメントの機械学習の脅威を簡単に要約します。

- モデル回避はヒューリスティックモデルでも可能です。攻撃者は定義されたルールの抜け穴や弱点を見つけようとする可能性があります。
- モデル抽出 - ヒューリスティックモデルからの入出力の組み合わせに基づいて機械学習モデルを訓練できます。
- 使用による過度の依存 - ヒューリスティックシステムも過度に依存することがあります。適用された知識は誤りの可能性があります。
- データポイズニングとモデルポイズニングはどちらも、知識を強化するために使用されるデータの改竄や、開発時や実行時にルールを操作することによって発生する可能性があります。
- 分析やテストに使用されるデータの漏洩が依然として問題になる可能性があります。
- 知識、ソースコード、設定が知的財産である場合、機密データとみなされる可能性があり、保護が必要です。
- たとえばヒューリスティックシステムが患者を診断する必要がある場合、機密性の高い入力データが漏洩します。

### 責任ある AI や信頼できる AI についてはどうですか？
> カテゴリ: ディスカッション  
> パーマリンク: https://owaspai.org/go/responsibleai/

'Responsible AI' and 'trustworthy AI' aim for positive outcomes while mitigating risks. The terms overlap heavily and are often used interchangeably; the former is commonly used to emphasise ethics, society, and governance, while the latter tends to stress technical and operational aspects. Both include security.  
If your primary responsibility is security, it's best to start by focusing on just that. Once you have a solid grasp of the security part, you can expand your knowledge to other AI aspects, such as bias, performance and use of AI. Your professional instinct for spotting what can go wrong can support colleagues who are responsible for those other areas. Furthermore, some aspects can be a consequence of compromised AI and are therefore helpful to understand, such as issues with _bias_ and _safety_.  

General concepts:
- **Harm** is negative impact on stakeholders' interests — people (safety, rights, wellbeing), the operating organization (continuity, finance, security, liability, reputation), or society and ecosystems. Controlling _harm_ is central to responsible and trustworthy AI.
- **Safety** refers to the condition of being protected from / unlikely to cause harm. Harm is sometimes used to refer to physical harm, but it may also include health and fundamental rights issues. Safety of an AI system rests on (1) sufficient correctness where harm is at stake, (2) measures that mitigate the consequences of incorrect behaviour, and (3) security — since compromised systems can behave unsafely. Because a model can act unsafely without being attacked (e.g., due to bad training data), these measures are a shared concern between safety and security:
  -  [oversight](/go/oversight/) to restrict unsafe behaviour, and connected to that: applying least privilege to the AI,
  -  [continuous validation](/go/continuousvalidation/) to safeguard correctness,
  -  [transparency](/go/aitransparency/): see below,
  -  [explainability](/go/explainability/): see below.
- **Accountability**. Accountability means being able to demonstrate the measures taken and the processes that have led to those measures. In addition, operational traceability is important, just like in any IT system, in order to detect, reconstruct and respond to incidents and provide accountability.
Responsible/trustworthy AI can be broken down into four responsibilities: responsible use, standard performance, standard impartiality (where 'standard' means: when not under attack), and security.

#### Responsibility 1: Responsible use
Responsible use is about controlling harm caused by _functionality_ of the AI system in combination with its intended use. The goal is to have the AI system act in a lawful and ethical way. For example: applying AI to select candidates for a job vacancy with proper bias tests and meaningful review. The main control to manage responsible use is [AI Governance](/go/aiprogram/) which includes for example doing an impact assessment for AI ideas.  

Concepts regarding responsible use:
- **Privacy** consists of the security of personal data plus principles and rights depending on thelegal framework (e.g.the GDPR): transparency, consent, purpose limitation, data subject rights (access/rectification/erasure/objection), and a lawful basis for data collection. See the [Privacy section](/go/privacy/) for in-depth discussion.
- **Fairness**: There are different definitions of fairness. One definition is that fairness is the same as equal treatment. Other definitions give it a broader meaning of 'justified treatment', such as the EDPS’ guideline, which defines fairness as the prevention of “unjustifiably detrimental, unlawfully discriminatory, unexpected or misleading” processing of personal data. Following that definition, fairness includes all elements mentioned as fundamental rights under privacy.
- **Transparency**: sharing information about the applied approach, to warn users and depending systems of correctness risks, plus in many cases users have the right to know details about AI being used and how it has been created. Therefore it is a shared concern between security, privacy and safety.
- **Explainability**: sharing information to help users validate correctness by explaining in more detail how a specific result was calculated. Apart from validating correctness this can also support users to get transparency and to understand what needs to change to get a different outcome. Therefore it is a shared concern between security, privacy, safety and business function. A special case is when explainability is required by law, which adds 'compliance' to the list of aspects that share this concern. Explainability can support responsible use and is legally required for only a small set of use cases.

Responsible use diagram:  
[![](/images/wayfinder-use.png)](/images/wayfinder-use.png)


#### Responsibility 2: Standard correctness in terms of performance
AI is in essence always guessing and therefore can always be incorrect. This can lead to harm, including (physical) safety problems (e.g., an autonomous vehicle failing to stop for a red light) or other wrong decisions that are harmful (e.g., wrongfully declining a loan). Two types of correctness can be distinguished: performance and impartiality. This section discusses the former.  

 Concepts regarding performance:
- **Correctness** is about the degree to which the model's outputs are right for its 'business function'.
- **Standard correctness** is the correctness of AI when not under attack. It falls outside of the security scope and is the area of data and model engineering.
- **Robustness** is about the ability of maintaining correctness under expected or unexpected variations in input. Security is concerned with malicious variations (_adversarial robustness_), which often require different countermeasures than natural variations (_generalization robustness_). Just like with correctness, security is not involved per se in creating a robust model for normal variations.
- **Generalization robustness**: An AI model is not a lookup database, so when it is presented with input it has never seen before, it is trying to generalize. The success of that is expressed in generalization robustness: how good is the model with unknown data.
 Countermeasures against any incorrectness include continuous validation, unwanted bias testing, and ways to limit and respond to the impact of incorrect output, such as monitoring, least privilege and oversight. A well-known type of incorrect output of Generative AI is _hallucination_: fabricated content presented as fact.

 Standard correctness diagram:  
 [![](/images/wayfinder-correctness.png)](/images/wayfinder-correctness.png)


#### Responsibility 3: Standard correctness in terms of impartiality
Next to performance, another form of correctness is impartiality: the model not discriminating between protected groups (e.g. ethnicity or gender).  

Concepts regarding impartiality:
- **Bias**: any systematic incorrectness, which is not necessarily discrimination against protected groups. It can, for example, be a financial index value predictor being generally 10 points off.
- **Fairness**: See previous 'responsible use' sub clause.
- **Impartiality**: the absence of unwanted bias regarding protected attributes, meaning: limited systematic incorrectness where the model 'mistreats' certain groups (e.g. gender, ethnicity). Such discrimination is undesired for legal and ethical reasons. The word 'limited' is used as the complete absence of bias can be practically unattainable.


#### Responsibility 4: Security
AI security — protecting AI systems against attacks — is the main subject of the AI Exchange. For a high-level overview, see the [AI security essentials](/go/essentials/). It can be divided into two goals:
- **Security protecting correctness**: deal with attacks manipulating model behaviour (e.g., data/model poisoning, prompt injection, evasion), leading to incorrectness and potential harm. For simplicity, this includes security for protecting availability if we regard the goal of correctness as the presence of a sufficiently correct result: no availability means no correctness.
- **Security protecting confidentiality**: deal with attacks that attempt to leak sensitive data (e.g., training data extraction, input leak, model theft).

Security protecting correctness diagram:  
[![](/images/wayfinder-security-correct.png)](/images/wayfinder-security-correct.png)

Security protecting confidentiality diagram:  
[![](/images/wayfinder-security-confidential.png)](/images/wayfinder-security-confidential.png)


### The complete responsible/trustworthy AI picture
The image below shows all aspects of responsible/trustworthy AI in one visual. It also includes another security aspect outside the scope of the AI Exchange: the use of the AI system to perform attacks - either as intended or unintended use. This is a security concern when it comes to responsible use, but it is not about protecting the AI system against attacks.  

[![](/images/wayfinder.png)](/images/wayfinder.png)


### 生成 AI (LLM など) についてはどうですか？
> カテゴリ: ディスカッション  
> パーマリンク: https://owaspai.org/go/genai/

はい、生成 AI は現在の AI 変革をリードしており、AI セキュリティの中で最も急速に変化しているサブフィールドです。とはいえ、クレジットスコアリング、不正検出、医療診断、製品推奨、画像認識、予知保全、プロセス制御など、多くの重要なユースケースには他のタイプのアルゴリズム (_予測 AI_ と呼びましょう) が引き続き適用されることを認識することが重要です。このドキュメントでは関連するコンテンツには「生成 AI」のマークを付けています。

重要な注意: セキュリティ脅威の観点からは、生成 AI は他の形式の AI (_予測 AI_) とそれほど違いはありません。生成 AI の脅威とコントロールは一般的な AI と大部分が重複しており、非常によく似ています。とはいえ、一部のリスクは (はるかに) 高くなります。低いものもあります。生成 AI 固有のリスクはごくわずかです。生成 AI と予測 AI ではコントロールカテゴリが大きく異なるものがあり、主にデータサイエンスコントロール (トレーニングセットへのノイズ追加など) です。多くの場合、生成 AI ソリューションはモデルをそのまま使用し、組織によるトレーニングを一切行わず、セキュリティ責任の一部を組織からサプライヤに移します。それでも、 [既製のモデル](ai_security_overview.md#threat-model-with-controls---ready-made-model) を使用する場合は、依然としてそうした脅威に注意する必要があります。

LLM による主な新しい脅威は何ですか？
- まず第一に、LLM は脆弱性のあるコードを作成するために使用されたり、攻撃者がマルウェアを作成するために使用されたり、ハルシネーションによって害を及ぼす可能性があるため、セキュリティに新たな脅威をもたらします。しかし、これらの懸念事項は AI Exchange の範囲外であり、AI システム自体へのセキュリティ脅威に焦点を当てています。
- 入力について:
  - プロンプトインジェクションは、攻撃者が細工した命令や、時には隠された命令で、モデルの動作を操作するものです。
  - また、企業秘密や個人データを含む、大量のデータをプロンプトで送信する組織も新たにあります。
- 出力について: 出力にはインジェクション攻撃を含んだり、機密データや著作権で保護されたデータを含む可能性があるという事実が新たにあります ([著作権](ai_security_overview.md#how-about-copyright) 参照)。
- 過度の依存は問題です。私たちは LLM に物事を制御および作成され、LLM がどれほど正しいかを過信し、また、LLM が操作されるリスクを過小評価していることがあります。その結果、攻撃は大きな影響を与えることになります。
- トレーニングについて: トレーニングセットは非常に大きく、公開データに基づいているため、データポイズニングを実行することは容易です。また、汚染された基礎モデルはサプライチェーンの大きな問題でもあります。
- 他の AI システムと同様に、生成 AI システムは出力に基づいてアクションをトリガーできますが、生成 AI の場合、モデル出力はアクションを実行 (メールの送信など) したり、他の AI システムをトリガーするための関数呼び出しを含むことがあります。詳細については [エージェント AI](ai_security_overview.md#threats-to-agentic-ai) を参照してください。

生成 AI セキュリティの特徴は以下の通りです。

|No.| 生成 AI セキュリティの特徴 | OWASP for LLM TOP 10 (2026) |
|-| ----------|-------------------|
|1| 生成 AI モデルはプロンプト内の自然言語によって制御されるため、[プロンプトインジェクション](2_threats_through_use.md#22-prompt-injection) のリスクが生じます。直接プロンプトインジェクションはモデルを騙して望ましくない動作 (不快な言動など) をさせようとするもので、間接プロンプトインジェクションは第三者がこの目的 (決定を操作するなど) のためにプロンプトにコンテンツを注入するものです。 | ([OWASP for LLM 01: Prompt Injection](https://genai.owasp.org/resource/owasp-genai-llm-top-10-2026/)) | 
|2| 生成 AI モデルは一般的に非常に大規模なデータセットでトレーニングされているため、[機密データ](2_threats_through_use.md#231-disclosure-of-sensitive-data-in-model-output) や [ライセンスされているデータ](ai_security_overview.md#how-about-copyright) を出力する可能性が高くなりますが、モデルにはアクセス権限の制御が組み込まれていません。すべてのデータはモデルユーザーがアクセスできるでしょう。システムプロンプト、モデルアラインメント、出力フィルタリングに関していくつかのメカニズムが実装されているかもしれませんが、それらは一般的に完全ではありません。 | ([OWASP for LLM 02: Sensitive Information Disclosure](https://genai.owasp.org/resource/owasp-genai-llm-top-10-2026/)) |
|3| [データとモデルのポイズニング](3_development_time_threats.md#31-broad-model-poisoning-development-time) は AI 全般の問題ですが、生成 AI ではトレーニングデータがインターネットなどの制御が困難なさまざまな情報源から供給される可能性があるため、リスクは一般的に高くなります。たとえば、攻撃者はドメインを乗っ取り、操作された情報を配置する可能性があります。 | ([OWASP for LLM 05: Data and Model Poisoning](https://genai.owasp.org/resource/owasp-genai-llm-top-10-2026/)) |
|4| 生成 AI モデルは不正確で幻覚を起こす可能性があります。これは AI 全般のリスク要因であり、さらに大規模言語モデル (生成 AI) は非常に機密性が高く知識を持っているという印象を与えることで事態を悪化させる可能性があります。要するに、これはモデルが間違っていたり、モデルが操作されていたりするという可能性を過小評価するリスクに関するものです。つまり、それぞれすべてのセキュリティコントロールに関連しています。最も強く結びつくのは [望ましくないモデル動作の影響を制限するためのコントロール](1_general_controls.md#13-controls-to-limit-the-effects-of-unwanted-behaviour)、特に [最小モデル権限](/1_general_controls.md#LEASTMODELPRIVILEGE) です。 | ([OWASP for LLM 03: Excessive Agency](https://genai.owasp.org/resource/owasp-genai-llm-top-10-2026/)) および ([OWASP for LLM 07: Misinformation](https://genai.owasp.org/resource/owasp-genai-llm-top-10-2026/)) |
|5| [入力データ漏洩](4_runtime_application_security_threats.md#45-input-data-leak): 生成 AI モデルはほとんどがクラウドに存在し、多くの場合は外部パーティによって管理されているため、プロンプトの漏洩のリスクが高まります。この問題は生成 AI に限定されるものではありませんが、生成 AI には特に 2 つのリスクがあります。1) モデルの使用にはプロンプトを介したユーザーとのやり取り、ユーザーデータの追加、対応するプライバシーやセンシティビティの問題が含まれます。2) 生成 AI モデルの入力 (プロンプト) には機密データ (企業秘密など) を持つ豊富なコンテキスト情報を含む可能性があります。後者の問題はたとえば、コンサルタント会社でこれまでに書かれたすべてのレポートのデータなど、*コンテキスト内学習 (In-Context Learning)* や *検索拡張生成 (Retrieval Augmented Generation, RAG)* で発生します。まず第一に、この情報はプロンプトとともにクラウドに移動し、第二に、システムは情報に対する本来のアクセス権を考慮しない可能性があります。 | LLM Top 10 でのカバーなし |
|6| 事前トレーニング済みモデルは操作されている可能性があります。事前トレーニングの概念は生成 AI に限ったことではありませんが、このアプローチは生成 AI ではごく一般的であり、 [サプライチェーンのモデルポイズニング](3_development_time_threats.md#313-supply-chain-model-poisoning) のリスクを高めます。 | ([OWASP for LLM 04: Supply Chain](https://genai.owasp.org/resource/owasp-genai-llm-top-10-2026/)) |
|7| [モデル反転とメンバーシップ推論](2_threats_through_use.md##222-model-inversion-and-membership-inference) は生成 AI にとって低リスクまたはゼロリスクです。 | LLM Top 10 の特定のエントリとしてはカバーなし、最も近いものは [OWASP for LLM 02: Sensitive Information Disclosure](https://genai.owasp.org/resource/owasp-genai-llm-top-10-2026/) (推論に基づく露出)、上記を参照 |
|8| 生成 AI の出力にはクロスサイトスクリプティングなどの [インジェクション攻撃](4_runtime_application_security_threats.md#44-insecure-output-handling) を実行する要素を含むかもしれません。 | ([OWASP for LLM 10: Improper Output Handling](https://genai.owasp.org/resource/owasp-genai-llm-top-10-2026/)) |
|9| [リソース枯渇](2_threats_through_use.md#24-failure-or-malfunction-of-ai-specific-elements-through-use) はどの IT システムでも問題になる可能性がありますが、生成 AI モデルは一般的に実行コストが高いため、過負荷になると不要なコストが発生する可能性があります。 | ([OWASP for LLM 06: Unbounded Consumption](https://genai.owasp.org/resource/owasp-genai-llm-top-10-2026/)) |

生成 AI 参考情報:

- [OWASP LLM Top 10 (2026)](https://genai.owasp.org/resource/owasp-genai-llm-top-10-2026/)
- [Demystifying the LLM top 10](https://blog.kloudzone.co.in/demystifying-the-owasp-top-10-for-large-language-model-applications/)
- [Impacts and risks of GenAI](https://arxiv.org/pdf/2306.13033.pdf)
- [LLMsecurity.net](https://llmsecurity.net/)

### NCSC/CISA ガイドラインについてはどうですか？
>カテゴリ: ディスカッション  
>パーマリンク: https://owaspai.org/go/jointguidelines/

英国 NCSC / CISA の [安全な AI システム開発のガイドライン](https://www.ncsc.gov.uk/collection/guidelines-secure-ai-system-development) を AI Exchange のコントロールにマッピングします。
脅威とリンクしているコントロールを確認するには、[AI セキュリティの周期表](ai_security_overview.md#periodic-table-of-ai-security) を参照してください。

Note that the UK Government drove an initiative through their DSIT department to build on these joint guidelines and produce the [DSIT Code of Practice for the Cyber Security of AI](https://www.gov.uk/government/publications/ai-cyber-security-code-of-practice/code-of-practice-for-the-cyber-security-of-ai#code-of-practice-principles), which reorganizes things according to 13 principles, does a few tweaks, and adds a bit more of governance. The principle mapping is added below, and adds mostly post-market aspects:


- Principle 10: Communication and processes associated with end-users and affected entities
- Principle 13: Ensure proper data and model disposal

1. 安全な設計

- 脅威とリスクに対するスタッフの意識を高めます (DSIT principle 1):
  #[SECURITY EDUCATE](1_general_controls.md#SECEDUCATE)
- システムに対する脅威をモデル化します (DSIT principle 3):
  #[SECURITY PROGRAM](1_general_controls.md#SECPROGRAM) のリスク分析を参照してください
- 機能性とパフォーマンスだけでなくセキュリティも考慮してシステムを設計します (DSIT principle 2):
  #[AI PROGRAM](1_general_controls.md#AIPROGRAM), #[SECURITY PROGRAM](1_general_controls.md#SECPROGRAM), #[DEVELOPMENT PROGRAM](1_general_controls.md#DEVPROGRAM), #[SECURE DEVELOPMENT PROGRAM](1_general_controls.md#SECDEVPROGRAM), #[CHECK COMPLIANCE](1_general_controls.md#CHECKCOMPLIANCE), #[LEAST MODEL PRIVILEGE](1_general_controls.md#LEASTMODELPRIVILEGE), #[DISCRETE](1_general_controls.md#DISCRETE), #[OBSCURE CONFIDENCE](2_threats_through_use.md#OBSCURE-CONFIDENCE), #[OVERSIGHT](1_general_controls.md#OVERSIGHT), #[RATE LIMIT](2_threats_through_use.md#RATE-LIMIT), #[DOS INPUT VALIDATION](2_threats_through_use.md#DOS-INPUT-VALIDATION), #[LIMIT RESOURCES](2_threats_through_use.md#LIMIT-RESOURCES), #[MODEL ACCESS CONTROL](2_threats_through_use.md#MODEL-ACCESS-CONTROL), #[AI TRANSPARENCY](1_general_controls.md#AITRANSPARENCY)
- AI モデルを選択する際に、セキュリティの利点とトレードオフを考慮します
  すべての開発時のデータサイエンスコントロール (現在 13), #[EXPLAINABILITY](1_general_controls.md#EXPLAINABILITY)

2. 安全な開発

- サプライチェーンを保護します (DSIT principle 7):
  #[SUPPLY CHAIN MANAGE](3_development_time_threats.md#SUPPLYCHAINMANAGE)
- 資産を特定、追跡、保護します (DSIT principle 5):
  #[DEVELOPMENT SECURITY](3_development_time_threats.md#DEVSECURITY), #[SEGREGATE DATA](3_development_time_threats.md#SEGREGATEDATA), #[CONFIDENTIAL COMPUTE](3_development_time_threats.md#CONFCOMPUTE), #[MODEL INPUT CONFIDENTIALITY](4_runtime_application_security_threats.md#MODELINPUTCONFIDENTIALITY), #[RUNTIME MODEL CONFIDENTIALITY](4_runtime_application_security_threats.md#RUNTIMEMODELCONFIDENTIALITY), #[DATA MINIMIZE](1_general_controls.md#DATAMINIMIZE), #[ALLOWED DATA](1_general_controls.md#ALLOWEDDATA), #[SHORT RETAIN](1_general_controls.md#SHORTRETAIN), #[OBFUSCATE TRAINING DATA](1_general_controls.md#OBFUSCATETRAININGDATA) および #[SECURITY PROGRAM](1_general_controls.md#SECPROGRAM) の一部
- データ、モデル、プロンプトを文書化します (DSIT principle 8):
  #[DEVELOPMENT PROGRAM](1_general_controls.md#DEVPROGRAM) の一部
- 技術的負債を管理します:
  #[DEVELOPMENT PROGRAM](1_general_controls.md#DEVPROGRAM) の一部

3. 安全な展開

- インフラストラクチャを保護します (DSIT principle 6):
  #[SECURITY PROGRAM](1_general_controls.md#SECPROGRAM) の一部と「資産を特定、追跡、保護します」を参照してください
- モデルを継続的に保護します:
  #[INPUT DISTORTION](2_threats_through_use.md#INPUT-DISTORTION), #[FILTER SENSITIVE MODEL OUTPUT](2_threats_through_use.md#FILTER-SENSITIVE-MODEL-OUTPUT), #[RUNTIME MODEL IO INTEGRITY](4_runtime_application_security_threats.md#RUNTIMEMODELIOINTEGRITY), #[MODEL INPUT CONFIDENTIALITY](4_runtime_application_security_threats.md#MODELINPUTCONFIDENTIALITY), #[PROMPT INJECTION I/O HANDLING](2_threats_through_use.md#PROMPT-INJECTION-IO-HANDLING), #[INPUT SEGREGATION](2_threats_through_use.md#INPUT-SEGREGATION)
- インシデント管理手順を策定します:
  #[SECURITY PROGRAM](1_general_controls.md#SECPROGRAM) の一部
- 責任をもって AI をリリースします:
  #[DEVELOPMENT PROGRAM](1_general_controls.md#DEVPROGRAM) の一部
- ユーザーが正しいことを簡単にできるようにします (DSIT principle 4, called Enable human responsibility for AI systems):
  #[SECURITY PROGRAM](1_general_controls.md#SECPROGRAM) の一部, and also involving #[EXPLAINABILITY](/go/explainability/), documenting prohibited use cases, and #[HUMAN OVERSIGHT](/go/oversight/))

4. 安全な運用と保守

- システムの動作を監視します (DSIT principle 12 and similar to DSIT principle 9 - appropriate testing and validation):
  #[CONTINUOUS VALIDATION](1_general_controls.md#CONTINUOUSVALIDATION), #[UNWANTED BIAS TESTING](1_general_controls.md#UNWANTEDBIASTESTING)
- システムの入力を監視します:
  #[MONITOR USE](2_threats_through_use.md#MONITOR-USE), #[DETECT ODD INPUT](2_threats_through_use.md#DETECT-ODD-INPUT), #[DETECT ADVERSARIAL INPUT](2_threats_through_use.md#DETECT-ADVERSARIAL-INPUT)
- セキュアバイデザインのアプローチに従ってアップデートを行います (DSIT principle 11: Maintain regular security updates, patches and mitigations):
  #[SECURE DEVELOPMENT PROGRAM](1_general_controls.md#SECDEVPROGRAM) の一部
- 教訓を収集して共有します:
  #[SECURITY PROGRAM](1_general_controls.md#SECPROGRAM) および #[SECURE DEVELOPMENT PROGRAM](1_general_controls.md#SECDEVPROGRAM) の一部


### <a name="how-about-copyright">How about copyright?</a>
>Category: discussion  
>パーマリンク: https://owaspai.org/go/copyright/

#### Introduction
AI and copyright are two (of many) areas of law and policy, (both public and 
private), that raise complex and often unresolved questions. AI output or generated 
content is not yet protected by US copyright laws, for example. Many other jurisdictions have yet 
to announce any formal status as to intellectual property protections for such 
materials. On the other hand, the human contributor who provides the input 
content, text, training data, etc. may own a copyright for such materials. Finally, the
usage of certain copyrighted materials in AI training may be considered [fair use](https://en.wikipedia.org/wiki/Fair_use).

#### AI & Copyright Security
In AI, companies face a myriad of security threats that could have far-reaching 
implications for intellectual property rights, particularly copyrights. As AI systems, 
including large data training models, become more sophisticated, they 
inadvertently raise the specter of copyright infringement. This is due in part to the 
need for development and training of AI models that process vast amounts of data, 
which may contain copyright works. In these instances, if copyright works were 
inserted into the training data without the permission of the owner, and without 
consent of the AI model operator or provider, such a breach could pose significant 
financial and reputational risk of infringement of such copyright and corrupt the 
entire data set itself.  

The legal challenges surrounding AI are multifaceted. On one hand, there is the
question of whether the use of copyrighted works to train AI models constitutes 
infringement, potentially exposing developers to legal claims. On the other hand, 
the majority of the industry grapples with the ownership of AI-generated works and 
the use of unlicensed content in training data. This legal ambiguity affects all 
stakeholders including developers, content creators, and copyright owners alike.

#### Lawsuits Related to AI & Copyright
Recent lawsuits (writing is April 2024) highlight the urgency of these issues. For instance, a class 
action suit filed against Stability AI, Midjourney, and DeviantArt alleges infringement
on the rights of millions of artists by training their tools on web-scraped images.  
Similarly, Getty Images’ lawsuit against Stability AI for using images from its catalog
without permission to train an art-generating AI underscores the potential for 
copyright disputes to escalate. Imagine the same scenario where a supplier 
provides vast quantities of training data for your systems, that has been 
compromised by protected work, data sets, or blocks of materials not licensed or 
authorized for such use. 

#### Copyright of AI-generated source code
Source code constitutes a significant intellectual property (IP) asset of a 
software development company, as it embodies the innovation and creativity
of its developers. Therefore, source code is subject to IP protection, through 
copyrights, patents, and trade secrets. In most cases, human generated 
source code carries copyright status as soon as it is produced.

However, the emergence of AI systems capable of generating source code 
without human input poses new challenges for the IP regime. For instance, 
who is the author of the AI-generated source code? Who can claim the IP 
rights over it? How can AI-generated source code be licensed and exploited 
by third parties?

These questions are not easily resolved, as the current IP legal and 
regulatory framework does not adequately address the IP status of AI-
generated works. Furthermore, the AI-generated source code may not be 
entirely novel, as it may be derived from existing code or data 
sources. Therefore, it is essential to conduct a thorough analysis of the 
origin and the process of the AI-generated source code, to determine its IP 
implications and ensure the safeguarding of the company's IP assets. Legal 
professionals specializing in the field of IP and technology should be 
consulted during the process. 

As an example, a recent case still in adjudication shows the complexities of 
source code copyrights and licensing filed against GitHub, OpenAI, and 
Microsoft by creators of certain code they claim the three entities violated. 
More information is available here: [: GitHub Copilot copyright case narrowed 
but not neutered • The Register](https://www.theregister.com/2024/01/12/github_copilot_copyright_case_narrowed/)

####  Copyright damages indemnification
Note that AI vendors have started to take responsibility for copyright issues of their models, under certain circumstances. Microsoft offers users the so-called [Copilot Copyright Commitment](https://www.microsoft.com/en-us/licensing/news/microsoft-copilot-copyright-commitment), which indemnifies users from legal damages regarding copyright of code that Copilot has produced - provided [a number of things](https://learn.microsoft.com/en-us/legal/cognitive-services/openai/customer-copyright-commitment) including that the client has used content filters and other safety systems in Copilot and uses specific services. Google Cloud offers its [Generative AI indemnification](https://cloud.google.com/blog/products/ai-machine-learning/protecting-customers-with-generative-ai-indemnification).  
Read more at [The Verge on Microsoft indemnification](https://www.theverge.com/2023/9/7/23863349/microsoft-ai-assume-responsibility-copyright-lawsuit) and [Direction Microsoft on the requirements of the indemnification](https://www.directionsonmicrosoft.com/blog/why-microsofts-copilot-copyright-commitment-may-not-mean-much-for-customers-yet/).

#### Do generative AI models really copy existing work?
Do generative AI models really look up existing work that may be copyrighted? In essence: no. A Generative AI model does not have sufficient capacity to store all the examples of code or pictures that were in its training set. Instead, during training, it extracts patterns about how things work in the data that it sees, and then later, based on those patterns, it generates new content. Parts of this content may show remnants of existing work, but that is more of a coincidence. In essence, a model doesn't recall exact blocks of code, but uses its 'understanding' of coding to create new code. Just like with human beings, this understanding may result in reproducing parts of something you have seen before, but not per se because this was from exact memory. Having said that, this remains a difficult discussion that we also see in the music industry: did a musician come up with a chord sequence because she learned from many songs that this type of sequence works and then coincidentally created something that already existed, or did she copy it exactly from that existing song?

#### Treating copyrigh infringement Risk
Organizations have several key strategies to treat the risk of copyright 
infringement in their AI systems. Implementing them early can be much more cost-effective than fixing at later stages of AI system operations. While each comes with 
certain financial and operating costs, the “hard savings” may result in a positive 
outcome.  
These may include:  
- Select providers with documented copyright controls, transparency and relevant evaluation results, or those that transfer or share financial risk with licenses, warranties, and indemnities regarding copyright claims.
- Restrict use cases likely to reproduce protected expression, such as continuing or closely recreating existing books, articles, images, music or software.
- Detect or block prompts and supplied context that request verbatim reproduction or close imitation.
- Review:  Apply similarity checking and human review before publishing outputs in high-risk applications.
- When training or fine-tuning a model:
  - Control the provenance, copyright status and permitted use of training data.
  - Respect applicable rightsholder reservations and opt-outs.
  - Test the resulting model for memorisation and extraction of training material.
- Organize response: allow rightsholders to report and have procedures for takedown, investigation, and correction.


#### Helpful resources regarding AI and copyright:
- [Artificial Intelligence (AI) and Copyright | Copyright Alliance](https://copyrightalliance.org/education/artificial-intelligence-copyright/)
- [AI industry faces threat of copyright law in 2024 | Digital Watch  Observatory](https://dig.watch/updates/ai-industry-faces-threat-of-copyright-law-in-2024)
- [Using generative AI and protecting against copyright issues | World    
Economic Forum -weforum.org](https://www.weforum.org/agenda/2024/01/cracking-the-code-generative-ai-and-intellectual-property/)
- [Legal Challenges Against Generative AI: Key Takeaways | Bipartisan    
Policy Center](https://bipartisanpolicy.org/blog/legal-challenges-against-generative-ai-key-takeaways/)
- [Generative AI Has an Intellectual Property Problem - hbr.org](https://hbr.org/2023/04/generative-ai-has-an-intellectual-property-problem)
- [Recent Trends in Generative Artificial Intelligence Litigation in the    
United States | HUB | K&L Gates - klgates.com](https://www.klgates.com/Recent-Trends-in-Generative-Artificial-Intelligence-Litigation-in-the-United-States-9-5-2023)
- [Generative AI could face its biggest legal tests in 2024 | Popular    
Science - popsci.com](https://www.popsci.com/technology/generative-ai-lawsuits/)
- [Is AI Model Training Compliant With Data Privacy Laws? - termly.io](https://termly.io/resources/articles/is-ai-model-training-compliant-with-data-privacy-laws/)
- [The current legal cases against generative AI are just the beginning |    
TechCrunch](https://techcrunch.com/2023/01/27/the-current-legal-cases-against-generative-ai-are-just-the-beginning/?guccounter=1)
- [(Un)fair Use? Copyrighted Works as AI Training Data — AI: The    
Washington Report | Mintz](https://www.mintz.com/insights-center/viewpoints/54731/2024-01-10-unfair-use-copyrighted-works-ai-training-data-ai)
- [Potential Supreme Court clash looms over copyright issues in    
generative AI training data | VentureBeat](https://venturebeat.com/ai/potential-supreme-court-clash-looms-over-copyright-issues-in-generative-ai-training-data/)
- [AI-Related Lawsuits: How The Stable Diffusion Case Could Set a Legal    
Precedent | Fieldfisher](https://www.fieldfisher.com/en/insights/ai-related-lawsuits-how-the-stable-diffusion-case)
