---
title: 5. AI セキュリティテスト
weight: 6
---
> カテゴリ: ディスカッション  
> パーマリンク: https://owaspai.org/goto/testing/

## イントロダクション
AI システムのセキュリティをテストするには、以下の三つの戦略に依存します。
1. **従来のセキュリティテスト** (つまり _ペンテスト_)。 [セキュアソフトウェア開発](1_general_controls.md#secdevprogram) を参照してください。
2. **モデルパフォーマンスバリデーション** ([継続的バリデーション](1_general_controls.md#continuousvalidation) を参照): モデルの意図した動作を表す入力と出力を持つバリデーションセットを用いて、モデルが指定された受け入れ基準に従って動作するかどうかをテストします。セキュリティとしては、これはデータポイズニングやモデルポイズニングによってモデルの動作が恒久的に改変されていないかを検出することです。セキュリティ以外としては、これは機能の正確性やモデルドリフトなどをテストすることです。
3. **AI セキュリティテスト** (本セクション) は、特定の攻撃をシミュレートして AI モデルがこれらの攻撃を耐えることができるかどうかをテストする、_AI レッドチーミング_ の一部です。

AI セキュリティテストは敵対的な動作をシミュレートして、AI システムの脆弱性、弱点、リスクを明らかにします。従来の AI テストの焦点領域は機能性とパフォーマンスですが、AI レッドチーミングの焦点領域は標準的なバリデーションを超え、意図的なストレステスト、攻撃、セーフガードのバイパスの試みを含みます。レッドチーミングの焦点はセキュリティにとどまりませんが、このドキュメントでは、主に「AI セキュリティのための AI レッドチーミング」に焦点を当てています。

このセクションでは、予測 AI と生成 AI の異なる性質、リスク、用途に基づき、AI レッドチーミングを区別します。開発時のサプライチェーンの脅威など、一部の脅威は両方のタイプの AI に共通する可能性がありますが、アプリケーションでそれらが発現する方法は大きく異なることがあります。

AI レッドチーミングへの体系的なアプローチには、以下に示した重要なステップがあります。

- **目的とスコープの定義**: 目的の特定。組織、コンプライアンス、リスク管理要件との整合。
- **AI システムの理解:** モデル、ユースケース、デプロイメントシナリオの詳細。
- **潜在的な脅威の特定:** 脅威モデリング。攻撃対象領域、調査、脅威アクターの特定。
- **攻撃シナリオの作成:** 攻撃シナリオとエッジケースの設計。
- **テスト実行:** 攻撃シナリオの手動テストや自動テストの実施。
- **リスク評価:** 特定された脆弱性とリスクの文書化。
- **優先順位付けとリスク緩和:** 修復のための行動計画の策定、緩和策の実施、残存リスクの算出。
- **修正の検証:** 修復後システムの再テスト。

AI セキュリティテストの詳細については、[OWASP AI テストガイド](https://github.com/OWASP/www-project-ai-testing-guide) を参照してください。


## テストすべき脅威
資産、影響、攻撃対象領域に基づいた脅威とコントロールのカバレッジの包括的なリストは [AI セキュリティの周期表](ai_security_overview.md#periodic-table-of-ai-security) として利用できます。このセクションでは、AI レッドチーミングの予測型および生成型 AI システム向けのツールのリストを提供し、攻撃シナリオ、自動レッドチーミングを通じたテスト実行、そして多くの場合、リスクスコアリングを通じたリスク評価などのステップを支援します。

リストされている各ツールは AI システムの脅威ランドスケープのサブセットに対応しています。以下に、考慮すべき主要な脅威をいくつか挙げます。

**予測 AI (Predictive AI):** 予測 AI システムは入力データに基づいて予測や分類を行うように設計されています。例としては、不正検知、画像認識、レコメンデーションシステムなどがあります。

**予測 AI への主要な脅威:**

- [回避攻撃](2_threats_through_use.md#21-evasion): これらの攻撃は、攻撃者がモデルを誤誘導する入力を作成する際に発生し、タスクを誤って実行させます。
- [モデル窃取](2_threats_through_use.md#24-model-theft-through-use): この攻撃では、モデルのパラメータや機能が盗まれます。これは、攻撃者がレプリカモデルを作成することを可能にし、それを敵対的攻撃やその他の複合的な脅威を作成するためのオラクルとして使用できます。
- [モデルポイズニング](3_development_time_threats.md#31-broad-model-poisoning-development-time): これは、トレーニングフェーズ (開発フェーズ) 時にデータ、データパイプライン、またはモデルトレーニングサプライチェーンの操作を伴います。攻撃者の目的は、モデルの動作を改変し、望ましくないモデル操作を引き起こすことです。

**生成 AI (Generative AI):** 生成 AI システムは、テキスト、画像、音声などの出力を生成します。例としては、ChatGPT などの大規模言語モデル (LLM) や、DALL-E や MidJourney などの大規模視覚モデル (LVM) などがあります。

**生成 AI への主要な脅威:**

- [プロンプトインジェクション](2_threats_through_use.md#222-indirect-prompt-injection): この種の攻撃では、攻撃者はモデルに対して、悪意のある結果や目的を達成することを目指した操作指示を与えます。
- [直接的な実行時のモデル盗用](4_runtime_application_security_threats.md#43-direct-runtime-model-theft): 攻撃者はモデルの一部、またはシステムプロンプトなどの重要なコンポーネントを標的とします。そうすることで、ガードレールをバイパスする高度な入力を作成できるようになります。
- [安全でない出力処理](4_runtime_application_security_threats.md#44-insecure-output-handling): 生成 AI システムは、従来のインジェクション攻撃に脆弱である可能性があり、出力が不適切に対処ないし処理されるとリスクにつながります。
- エージェント AI システムのテストの詳細については、CSA と AI Exchange の間でコラボレーションした [Agentic AI red teaming guide](https://cloudsecurityalliance.org/download/artifacts/agentic-ai-red-teaming-guide) を参照してください。

各 AI パラダイムに対する主要な脅威について言及しましたが、AI レッドチーミングの目標とスコープの定義フェーズの結果に基づき、AI Exchange のすべての脅威を参照することを読者に強くお勧めします。

## **AI および生成 AI のためのレッドチーミングツール**

以下のマインドマップは、AI レッドチーミングのオープンソースツールの概要を示しており、予測 AI レッドチーミングと生成 AI レッドチーミングに分類され、ART, Armory, TextAttack, Promptfoo などの例を挙げています。これらのツールは現時点での機能を示していますが、網羅的ではなく、重要度順にランク付けされているわけでもありません。今後、新たなツールや手法が出現し、この分野に統合される可能性が高いためです。

[![](https://owaspai.org/images/testtoolstoattacks.png)](https://owaspai.org/images/testtoolstoattacks.png)

以下の図は AI システムの脅威を分類し、これらの脅威に対処するために設計された関連するオープンソースツールにマップしています。

[![](https://owaspai.org/images/attackstotesttools.jpg)](https://owaspai.org/images/attackstotesttools.jpg)

以下のセクションでは予測 AI のツールについて説明し、その後に生成 AI のセクションに続きます。

## **予測 AI レッドチーミングのためのオープンソースツール**

This sub section covers the following tools for security testing Predictive AI: Adversarial Robustness Toolbox (ART), Armory, Foolbox, DeepSec, and TextAttack.

### **ツール名: 敵対的ロバストネスツールボックス (Adversarial Robustness Toolbox, ART)**

| **Tool Name: The Adversarial Robustness Toolbox (ART)** |  |
| --- | --- |
| Developer/ Source | IBM Research / the Linux Foundation AI & Data Foundation (LF AI & Data) |
| Github Reference | https://github.com/Trusted-AI/adversarial-robustness-toolbox |
| Language | Python |
| Licensing | Open-source under the MIT License. |
| Provides Mitigation | Prevention: No ❌ Detection: Yes ✅ |
| API Availability | Yes ✅ |

| Factor | Details |
| --- | --- |
| **Popularity** | - **GitHub Stars:** ~4.9K stars (as of 2024) |
|  | - **GitHub Forks:** ~1.2K forks |
|  | - **Number of Issues:** ~131 open issues, 761 closed issues |
|  | - **Trend:** Steady growth, with consistent updates and industry adoption for adversarial robustness. |
| **Community Support** | - **Active Issues:** Responsive team, typically addressing issues within a week. |
|  | - **Documentation:** Detailed and regularly updated, with comprehensive guides and API documentation on IBM's website. |
|  | - **Discussion Forums:** Primarily discussed in academic settings, with some presence on Stack Overflow and GitHub. |
|  | - **Contributors:** Over 100 contributors, including IBM researchers and external collaborators. |
| **Scalability** | - **Framework Support:** Scales across TensorFlow, Keras, and PyTorch with out-of-the-box support. |
|  | - **Large-Scale Deployment:** Proven to handle large, enterprise-level deployments in industries like healthcare, finance, and defense. |
| **Integration** | - **Compatibility:** Works with TensorFlow, PyTorch, Keras, MXNet, and Scikit-learn. |

**Tool Rating**

| **Criteria** | **High** | **Medium** | **Low** |
| --- | --- | --- | --- |
| **Popularity** | ✅ |  |  |
| **Community Support** | ✅ |  |  |
| **Scalability** | ✅ |  |  |
| **Ease of Integration** | ✅ |  |  |

**Data Modality**

| Data Modality | Supported |
| --- | --- |
| Text | ✅ |
| Image | ✅ |
| Audio | ✅ |
| Video | ✅ |
| Tabular data | ✅ |

**Machine Learning Tasks**

| Task Type | Data Modality | Supported |
| --- | --- | --- |
| Classification | All (See Data modality section) | ✅ |
| Object Detection | Computer Vision | ✅ |
| Speech Recognition | Audio | ✅ |

**Framework Applicability**

| Framework / Tool | Category | Supported |
| --- | --- | --- |
| Tensorflow | DL, GenAI | ✅ |
| Keras | DL, GenAI | ✅ |
| PyTorch | DL, GenAI | ✅ |
| MxNet | DL | ✅ |
| Scikit-learn | ML | ✅ |
| XGBoost | ML | ✅ |
| LightGBM | ML | ✅ |
| CatBoost | ML | ✅ |
| GPy | ML | ✅ |

**OWASP AI Exchange Threat Coverage**

| Topic | Coverage |
| --- | --- |
| Development time model poisoning | ✅ |
| Runtime model poisoning |  |
| Model theft by use | ✅ |
| Training data poisoning |  |
| Training data leak |  |
| Runtime model theft |  |
| Evasion (Tests model performance against adversarial inputs) | ✅ |
| Model inversion / Membership inference | ✅ |
| Denial of model service |  |
| Direct prompt injection |  |
| Data disclosure |  |
| Model input leak |  |
| Indirect prompt injection |  |
| Development time model theft |  |
| Output contains injection |  |

Notes:

- Development-time Model poisoning: Simulates attacks during development to evaluate vulnerabilities[*https://owaspai.org/goto/modelpoison/*](https://owaspai.org/goto/modelpoison/)
- Evasion:Tests model performance against adversarial inputs  [*https://owaspai.org/goto/evasion/*](https://owaspai.org/goto/evasion/)
- Model theft through use: Evaluates risks of model exploitation during usage  [*https://owaspai.org/goto/modeltheftuse*](https://owaspai.org/goto/modeltheftuse/)
- Model inference: *Assesses exposure to membership and inversion attacks*
*[https://owaspai.org/goto/modelinversionandmembership/](https://owaspai.org/goto/modelinversionandmembership/)*

### **ツール名: Armory**

| **Tool Name: Armory** |  |
| --- | --- |
| Developer/ Source | MITRE Corporation |
| Github Reference | [https://github.com/twosixlabs/armory-library](https://github.com/twosixlabs/armory-library)[https://github.com/twosixlabs/armory](https://github.com/twosixlabs/armory) |
| Language | Python |
| Licensing | Open-source under the MIT License. |
| Provides Mitigation | Prevention: No ❌Detection: Yes ✅ |
| API Availability | Yes ✅ |

| Factor | Details |
| --- | --- |
| **Popularity** | - **GitHub Stars:**  ~176 stars (as of 2024) |
|  | - **GitHub Forks:**  ~67 forks |
|  | - **Number of Issues:** ~ 59 open issues, 733 closed, 26 contributors |
|  | - **Trend:** Growing, particularly within defense and cybersecurity sectors. |
| **Community Support** | - **Active Issues:**  Fast response to issues (typically resolved within days to a week). |
|  | - **Documentation:** Comprehensive, but more security-focused, with advanced tutorials on adversarial attacks and defenses. |
|  | - **Discussion Forums:** Active GitHub discussions, some presence on security-specific forums (e.g., in relation to DARPA projects). |
|  | - **Contributors:** Over 40 contributors, mostly security experts and researchers. |
| **Scalability** | - **Framework Support:** Supports TensorFlow and Keras natively, with some integration options for PyTorch. |
|  | - **Large-Scale Deployment:** Mostly used in security-related deployments; scalability for non-security tasks is less documented. |
| **Integration** | - **Compatibility:** Works well with TensorFlow and Keras; IBM ART integration for enhanced robustness |
|  | - **API Availability**: Limited compared to IBM ART, but sufficient for adversarial ML use cases. |

**Tool Rating**

| **Criteria** | **High** | **Medium** | **Low** |
| --- | --- | --- | --- |
| **Popularity** |  |  | ✅ |
| **Community Support** |  | ✅ |  |
| **Scalability** |  | ✅ |  |
| **Ease of Integration** | ✅ |  |  |

**Data Modality**

| Data Modality | Supported |
| --- | --- |
| Text | ✅ |
| Image | ✅ |
| Audio | ✅ |
| Video | ✅ |
| Tabular data | ✅ |

**Machine Learning Tasks**

| Task Type | Data Modality | Supported |
| --- | --- | --- |
| Classification | All (See Data modality section) | ✅ |
| Object Detection | Computer Vision | ✅ |
| Speech Recognition | Audio | ✅ |

**Framework Applicability**

| Framework / Tool | Category | Supported |
| --- | --- | --- |
| Tensorflow | DL, GenAI | ✅ |
| Keras | DL, GenAI |  |
| PyTorch | DL, GenAI | ✅ |
| MxNet | DL |  |
| Scikit-learn | ML |  |
| XGBoost | ML |  |
| LightGBM | ML |  |
| CatBoost | ML |  |
| GPy | ML |  |

**OWASP AI Exchange Threat Coverage**

| Topic | Coverage |
| --- | --- |
| Development time model poisoning | ✅ |
| Runtime model poisoning |  |
| Model theft by use |  |
| Training data poisoning |  |
| Training data leak |  |
| Runtime model theft |  |
| Evasion (Tests model performance against adversarial inputs) | ✅ |
| Model inversion / Membership inference |  |
| Denial of model service |  |
| Direct prompt injection | ✅ |
| Data disclosure |  |
| Model input leak |  |
| Indirect prompt injection |  |
| Development time model theft |  |
| Output contains injection |  |

Notes:

- Development-time Model poisoning: Simulates attacks during development to evaluate vulnerabilities[*https://owaspai.org/goto/modelpoison/*](https://owaspai.org/goto/modelpoison/)
- Evasion:Tests model performance against adversarial inputs  [*https://owaspai.org/goto/evasion/*](https://owaspai.org/goto/evasion/)
- Prompt Injection: Evaluates the robustness of generative AI models by exploiting weaknesses in prompt design, leading to undesired outputs or bypassing model safeguards.
*https://owaspai.org/goto/promptinjection/*

### **ツール名: Foolbox**

| **Tool Name: Foolbox** |  |
| --- | --- |
| Developer/ Source | Authors/Developers of Foolbox |
| Github Reference | [https://github.com/bethgelab/foolbox](https://github.com/bethgelab/foolbox) |
| Language | Python |
| Licensing | Open-source under the MIT License. |
| Provides Mitigation | Prevention: No ❌Detection: Yes ✅ |
| API Availability | Yes ✅ |

| Factor | Details |
| --- | --- |
| **Popularity** | - **GitHub Stars:**  ~2,800 stars (as of 2024) |
|  | - **GitHub Forks:** ~428 forks |
|  | - **Number of Issues:** ~21 open issues, 350 closed issues |
|  | - **Trend:** Steady, with consistent updates from the academic community. |
| **Community Support** | - **Active Issues:** Typically resolved within a few weeks. |
|  | - **Documentation:** Moderate documentation with basic tutorials; more research-focused. |
|  | - **Discussion Forums:** Primarily discussed in academic settings, with limited industry forum activity. |
|  | - **Contributors:** Over 30 contributors, largely from academia. |
| **Scalability** | - **Framework Support:** Framework Support: Compatible with TensorFlow, PyTorch, and JAX |
|  | - **Large-Scale Deployment:**  Limited scalability for large-scale industry deployments, more focused on research and experimentation. |
| **Integration** | - **Compatibility:**  Strong integration with TensorFlow, PyTorch, and JAX. |

**Total Rating**

| **Criteria** | **High** | **Medium** | **Low** |
| --- | --- | --- | --- |
| **Popularity** |  | ✅ |  |
| **Community Support** |  | ✅ |  |
| **Scalability** |  |  | ✅ |
| **Ease of Integration** |  | ✅ |  |

**Data Modality**

| Data Modality | Supported |
| --- | --- |
| Text | ✅ |
| Image | ✅ |
| Audio |  |
| Video |  |
| Tabular data |  |

**Machine Learning Tasks**

| Task Type | Data Modality | Supported |
| --- | --- | --- |
| Classification | All (See Data modality section) | ✅ |
| Object Detection | Computer Vision | ✅ |
| Speech Recognition | Audio |  |

**Framework Applicability**

| Framework / Tool | Category | Supported |
| --- | --- | --- |
| Tensorflow | DL, GenAI | ✅ |
| Keras | DL, GenAI | ✅ |
| PyTorch | DL, GenAI | ✅ |
| MxNet | DL |  |
| Scikit-learn | ML |  |
| XGBoost | ML |  |
| LightGBM | ML |  |
| CatBoost | ML |  |
| GPy | ML |  |

**OWASP AI Exchange Threat Coverage**

| Topic | Coverage |
| --- | --- |
| Development time model poisoning |  |
| Runtime model poisoning |  |
| Model theft by use |  |
| Training data poisoning |  |
| Training data leak |  |
| Runtime model theft |  |
| Evasion (Tests model performance against adversarial inputs) | ✅ |
| Model inversion / Membership inference |  |
| Denial of model service |  |
| Direct prompt injection |  |
| Data disclosure |  |
| Model input leak |  |
| Indirect prompt injection |  |
| Development time model theft |  |
| Output contains injection |  |

Notes:

Evasion:Tests model performance against adversarial inputs

[*https://owaspai.org/goto/evasion/*](https://owaspai.org/goto/evasion/)

**Tool Name: DeepSec**

| **Tool Name: DeepSec** |  |
| --- | --- |
| Developer/ Source | Developed by a team of academic researchers in collaboration with the National University of Singapore. |
| Github Reference | [https://github.com/ryderling/DEEPSEC](https://github.com/ryderling/DEEPSEC) |
| Language | Python |
| Licensing | Open-source under the Apache License 2.0. |
| Provides Mitigation | Prevention: No ❌Detection: Yes ✅ |
| API Availability | Yes ✅ |

| Factor | Details |
| --- | --- |
| **Popularity** | - **GitHub Stars:** 209 (as of 2024) |
|  | - **GitHub Forks:** ~70 |
|  | - **Number of Issues:** ~15 open issues |
|  | - **Trend:** Stable with a focus on deep learning security |
| **Community Support** | - **Active Issues:** Currently has ongoing issues and updates, suggesting active maintenance. |
|  | - **Documentation:** Available through GitHub, covering setup, use, and contributions. |
|  | - **Discussion Forums:**  GitHub Discussions section and community channels support developer interactions. |
|  | - **Contributors:**  A small but dedicated contributor base. |
| **Scalability** | - **Framework Support:**  Primarily supports PyTorch and additional libraries like TorchVision. |
|  | - **Large-Scale Deployment:** Suitable for research and testing environments but may need adjustments for production-grade scaling |
| **Integration** | - **Compatibility:** Compatible with machine learning libraries in Python. |

**Tool Rating**

| **Criteria** | **High** | **Medium** | **Low** |
| --- | --- | --- | --- |
| **Popularity** |  |  | ✅ |
| **Community Support** |  |  | ✅ |
| **Scalability** |  |  | ✅ |
| **Ease of Integration** |  |  | ✅ |

**Data Modality**

| Data Modality | Supported |
| --- | --- |
| Text | ✅ |
| Image | ✅ |
| Audio |  |
| Video |  |
| Tabular data |  |

**Machine Learning Tasks**

| Task Type | Data Modality | Supported |
| --- | --- | --- |
| Classification | All (See Data modality section) | ✅ |
| Object Detection | Computer Vision |  |
| Speech Recognition | Audio |  |

**Framework Applicability**

| Framework / Tool | Category | Supported |
| --- | --- | --- |
| Tensorflow | DL, GenAI | ✅ |
| Keras | DL, GenAI |  |
| PyTorch | DL, GenAI | ✅ |
| MxNet | DL |  |
| Scikit-learn | ML |  |
| XGBoost | ML |  |
| LightGBM | ML |  |
| CatBoost | ML |  |
| GPy | ML |  |

**OWASP AI Exchange Threat Coverage**

| Topic | Coverage |
| --- | --- |
| Development time model poisoning |  |
| Runtime model poisoning |  |
| Model theft by use |  |
| Training data poisoning |  |
| Training data leak |  |
| Runtime model theft |  |
| Evasion (Tests model performance against adversarial inputs) | ✅ |
| Model inversion / Membership inference |  |
| Denial of model service |  |
| Direct prompt injection |  |
| Data disclosure |  |
| Model input leak |  |
| Indirect prompt injection |  |
| Development time model theft |  |
| Output contains injection |  |

Notes:

Evasion:Tests model performance against adversarial inputs

[*https://owaspai.org/goto/evasion/*](https://owaspai.org/goto/evasion/)

### ツール名: TextAttack

| **Tool Name: TextAttack** |  |
| --- | --- |
| Developer/ Source | Developed by researchers at the University of Maryland and Google Research. |
| Github Reference | [https://github.com/QData/TextAttack](https://github.com/QData/TextAttack) |
| Language | Python |
| Licensing | Open-source under the MIT License. |
| Provides Mitigation | Prevention: No ❌ Detection: Yes ✅ |
| API Availability | Yes ✅ |

| Factor | Details |
| --- | --- |
| **Popularity** | - **GitHub Stars:** ~3.7K (as of 2024) |
|  | - **GitHub Forks:** ~455 |
|  | - **Number of Issues:** ~130 open issues |
|  | - **Trend:** Popular with ongoing updates and regular contributions |
| **Community Support** | - **Active Issues:**  Issues are actively managed with frequent bug fixes and improvements. |
|  | - **Documentation:** Detailed documentation is available, covering everything from attack configuration to custom dataset integration |
|  | - **Discussion Forums:** GitHub Discussions are active, with support for technical queries and community interaction. |
|  | - **Contributors:** Over 20 contributors, reflecting diverse input and enhancements. |
| **Scalability** | - **Framework Support:** Supports NLP models in PyTorch and integrates well with Hugging Face’s Transformers and Datasets libraries, making it compatible with a broad range of NLP tasks. |
|  | - **Large-Scale Deployment:** Primarily designed for research and experimentation; deployment at scale would likely require customization. |
| **Integration** | - **Compatibility:** Model-agnostic, allowing use with various NLP model architectures as long as they meet the interface requirements. |

**Tool Rating**

| **Criteria** | **High** | **Medium** | **Low** |
| --- | --- | --- | --- |
| **Popularity** | ✅ |  |  |
| **Community Support** | ✅ |  |  |
| **Scalability** |  | ✅ |  |
| **Ease of Integration** | ✅ |  |  |

**Data Modality**

| Data Modality | Supported |
| --- | --- |
| Text | ✅ |
| Image |  |
| Audio |  |
| Video |  |
| Tabular data |  |

**Machine Learning Tasks**

| Task Type | Data Modality | Supported |
| --- | --- | --- |
| Classification | All (See Data modality section) | ✅ |
| Object Detection | Computer Vision |  |
| Speech Recognition | Audio |  |

**Framework Applicability**

| Framework / Tool | Category | Supported |
| --- | --- | --- |
| Tensorflow | DL, GenAI | ✅ |
| Keras | DL, GenAI |  |
| PyTorch | DL, GenAI | ✅ |
| MxNet | DL |  |
| Scikit-learn | ML |  |
| XGBoost | ML |  |
| LightGBM | ML |  |
| CatBoost | ML |  |
| GPy | ML |  |

**OWASP AI Exchange Threat Coverage**

| Topic | Coverage |
| --- | --- |
| Development time model poisoning | ✅ |
| Runtime model poisoning |  |
| Model theft by use |  |
| Training data poisoning |  |
| Training data leak |  |
| Runtime model theft |  |
| Evasion (Tests model performance against adversarial inputs) | ✅ |
| Model inversion / Membership inference |  |
| Denial of model service |  |
| Direct prompt injection |  |
| Data disclosure |  |
| Model input leak |  |
| Indirect prompt injection |  |
| Development time model theft |  |
| Output contains injection |  |

Notes:

- Development-time Model poisoning: Simulates attacks during development to evaluate vulnerabilities[*https://owaspai.org/goto/modelpoison/*](https://owaspai.org/goto/modelpoison/)
- Evasion:Tests model performance against adversarial inputs[*https://owaspai.org/goto/evasion/*](https://owaspai.org/goto/evasion/)

## 生成 AI レッドチーミングのためのオープンソースツール

This sub section covers the following tools for security testing Generative AI: PyRIT, Garak, Prompt Fuzzer, Guardrail, and Promptfoo.

A list of GenAI test tools can also be found at the [OWASP GenAI security project solutions page](https://genai.owasp.org/ai-security-solutions-landscape/) (click the category 'Test & Evaluate'. This project also published a [GenAI Red Teaming guide](https://genai.owasp.org/resource/genai-red-teaming-guide/).


### ツール名: PyRIT

| **Tool Name: PyRIT** |  |
| --- | --- |
| Developer/ Source | Microsoft |
| Github Reference | [https://github.com/Azure/PyRIT](https://github.com/Azure/PyRIT) |
| Language | Python |
| Licensing | Open-source under the MIT License. |
| Provides Mitigation | Prevention: No ❌ Detection: Yes ✅ |
| API Availability | Yes ✅ , library based |

| Factor | Details |
| --- | --- |
| **Popularity** | - **GitHub Stars:** ~2k (as of Dec-2024) |
|  | - **GitHub Forks:** ~384forks |
|  | - **Number of Issues:** ~63 open issues, 79 closed issues |
|  | - **Trend:** Steady growth, with consistent updates and industry adoption for adversarial robustness. |
| **Community Support** | - **Active Issues:** Issues are being addressed within a week. |
|  | - **Documentation:** Detailed and regularly updated, with comprehensive guides and API documentation. |
|  | - **Discussion Forums:** Active GitHub issues |
|  | - **Contributors:** Over 125 contributors. |
| **Scalability** | - **Framework Support:** Scales across TensorFlow, PyTorch and supports models on local like ONNX |
|  | - **Large-Scale Deployment:** Can be extended to Azure pipeline. |
| **Integration** | - **Compatibility:** Compatible with majority of LLMs |

**Tool Rating**

| **Criteria** | **High** | **Medium** | **Low** |
| --- | --- | --- | --- |
| **Popularity** |  | ✅ |  |
| **Community Support** | ✅ |  |  |
| **Scalability** | ✅ |  |  |
| **Ease of Integration** |  | ✅ |  |

**Data Modality**

| Data Modality | Supported |
| --- | --- |
| Text | ✅ |
| Image |  |
| Audio |  |
| Video |  |
| Tabular data |  |

**Machine Learning Tasks**

| Task Type | Data Modality | Supported |
| --- | --- | --- |
| Classification | All (See Data modality section) | ✅ |
| Object Detection | Computer Vision | ✅ |
| Speech Recognition | Audio | ✅ |

**Framework Applicability**

| Framework / Tool | Category | Supported |
| --- | --- | --- |
| Tensorflow | DL, GenAI | ✅ |
| PyTorch | DL, GenAI | ✅ |
| Azure OpenAI | GenAI | ✅ |
| Huggingface | ML, GenAI | ✅ |
| Azure managed endpoints | Machine Learning Deployment | ✅ |
| Cohere | GenAI | ✅ |
| Replicate Text Models	 | GenAI | ✅ |
| OpenAI API | GenAI | ✅ |
| GGUF (Llama.cpp) | GenAI, Lightweight Inference | ✅ |

**OWASP AI Exchange Threat Coverage**

| Topic | Coverage |
| --- | --- |
| Development time model poisoning |  |
| Runtime model poisoning |  |
| Model theft by use |  |
| Training data poisoning |  |
| Training data leak |  |
| Runtime model theft |  |
| Evasion Tests model performance against adversarial inputs | ✅ |
| Model inversion / Membership inference |  |
| Denial of model service |   |
| Direct prompt injection |  ✅ |
| Data disclosure |   |
| Model input leak |   |
| Indirect prompt injection |  |
| Development time model theft |  |
| Output contains injection |  |

Notes:

- Evasion:Tests model performance against adversarial inputs  [*https://owaspai.org/goto/evasion/*](https://owaspai.org/goto/evasion/)
- Prompt Injection: Evaluates the robustness of generative AI models by exploiting weaknesses in prompt design, leading to undesired outputs or bypassing model safeguards.*https://owaspai.org/goto/promptinjection/*

### ツール名: Garak

| **Tool Name: Garak** |  |
| --- | --- |
| Developer/ Source | NVIDIA |
| Github Reference | https://docs.garak.ai/garak  moved to https://github.com/NVIDIA/garak
Literature: https://arxiv.org/abs/2406.11036
https://github.com/NVIDIA/garak |
| Language | Python |
| Licensing | Apache 2.0 License |
| Provides Mitigation | Prevention: No ❌ Detection: Yes ✅ |
| API Availability | Yes ✅ |

| Factor | Details |
| --- | --- |
| **Popularity** | - **GitHub Stars:** ~3,5K stars (as of Dec 2024) |
|  | - **GitHub Forks:** ~306forks |
|  | - **Number of Issues:** ~303 open issues, 299 closed issues |
|  | - **Trend:** Growing, particularly with in attack generation, and LLM vulnerability scanning. |
| **Community Support** | - **Active Issues:** Actively responds to the issues and tries to close it within a week |
|  | - **Documentation:** Detailed documentation with guidance and example experiments. |
|  | - **Discussion Forums:**  Active GitHub discussions, as well as discord. |
|  | - **Contributors:** Over 27 contributors. |
| **Scalability** | - **Framework Support:** Supports various LLMs from hugging face, openai api, litellm.   |
|  | - **Large-Scale Deployment:** Mostly used in attack LLM, detect LLM failures and assessing LLM security. Can be integrated with NeMo Guardrails |
| **Integration** | - **Compatibility:**  All LLMs, Nvidia models |

**Tool Rating**

| **Criteria** | **High** | **Medium** | **Low** |
| --- | --- | --- | --- |
| **Popularity** | ✅ |  |  |
| **Community Support** |  | ✅ |  |
| **Scalability** |  | ✅ |  |
| **Ease of Integration** |  | ✅ |  |

**Data Modality**

| Data Modality | Supported |
| --- | --- |
| Text | ✅ |
| Image |  |
| Audio |  |
| Video |  |
| Tabular data |  |

**Machine Learning Tasks**

| Task Type | Data Modality | Supported |
| --- | --- | --- |
| Classification | All (See Data modality section) | ✅ |
| Object Detection | Computer Vision | ✅ |
| Speech Recognition | Audio |  |

**Framework Applicability**

| Framework / Tool | Category | Supported |
| --- | --- | --- |
| Tensorflow | DL, GenAI |  |
| PyTorch | DL, GenAI | ✅ |
| Azure OpenAI | GenAI |  |
| Huggingface | ML, GenAI | ✅ |
| Azure managed endpoints | Machine Learning Deployment |  |
| Cohere | GenAI | ✅ |
| Replicate Text Models	 | GenAI | ✅ |
| OpenAI API | GenAI | ✅ |
| GGUF (Llama.cpp) | GenAI, Lightweight Inference | ✅ |
| OctoAI | GenAI | ✅ |

**OWASP AI Exchange Threat Coverage**

| Topic | Coverage |
| --- | --- |
| Development time model poisoning |  |
| Runtime model poisoning |  |
| Model theft by use |  |
| Training data poisoning |  |
| Training data leak |  |
| Runtime model theft |  |
| Evasion (Tests model performance against adversarial inputs) | ✅ |
| Model inversion / Membership inference |  |
| Denial of model service |  |
| Direct prompt injection | ✅ |
| Data disclosure |  |
| Model input leak |  |
| Indirect prompt injection |  |
| Development time model theft |  |
| Output contains injection |  |
- Evasion:Tests model performance against adversarial inputs  [*https://owaspai.org/goto/evasion/*](https://owaspai.org/goto/evasion/)
- Prompt Injection: Evaluates the robustness of generative AI models by exploiting weaknesses in prompt design, leading to undesired outputs or bypassing model safeguards.
*https://owaspai.org/goto/promptinjection/*

### ツール名: Prompt Fuzzer

| **Tool Name: Prompt Fuzzer** |  |
| --- | --- |
| Developer/ Source | Prompt Security |
| Github Reference | [https://github.com/prompt-security/ps-fuzz](https://github.com/prompt-security/ps-fuzz) |
| Language | Python |
| Licensing | Open-source under the MIT License. |
| Provides Mitigation | Prevention: No ❌ Detection: Yes ✅ |
| API Availability | Yes ✅ |

| Factor | Details |
| --- | --- |
| **Popularity** | - **GitHub Stars:** ~427 stars (as of Dec 2024) |
|  | - **GitHub Forks:** ~56 forks |
|  | - **Number of Issues:**  ~10 open issues, 6 closed issues |
|  | - **Trend:** Not updating since Aug |
| **Community Support** | - **Active Issues:** Not updated nor solved any bugs since July. |
|  | - **Documentation:** Moderate documentation with few examples |
|  | - **Discussion Forums:**  GitHub issue forums |
|  | - **Contributors:** Over 10 contributors. |
| **Scalability** | - **Framework Support:** Python and docker image. |
|  | - **Large-Scale Deployment:** It only assesses the security of your GenAI application's system prompt against various dynamic LLM-based attacks, so it can be integrated with current env. |
| **Integration** | - **Compatibility:**  Any device. |

**Tool Rating**

| **Criteria** | **High** | **Medium** | **Low** |
| --- | --- | --- | --- |
| **Popularity** |  |  | ✅ |
| **Community Support** |  |  | ✅ |
| **Scalability** |  | ✅ |  |
| **Ease of Integration** |  | ✅ |  |

**Data Modality**

| Data Modality | Supported |
| --- | --- |
| Text | ✅ |
| Image |  |
| Audio |  |
| Video |  |
| Tabular data |  |

**Machine Learning Tasks**

| Task Type | Data Modality | Supported |
| --- | --- | --- |
| Classification | All (See Data modality section) | ✅ |
| Object Detection | Computer Vision |  |
| Speech Recognition | Audio |  |

**Framework Applicability**

*(LLM Model agnostic in the API mode of use)*

| Framework / Tool | Category | Supported |
| --- | --- | --- |
| Tensorflow | DL, GenAI |  |
| PyTorch | DL, GenAI |  |
| Azure OpenAI | GenAI |  |
| Huggingface | ML, GenAI |  |
| Azure managed endpoints | Machine Learning Deployment |  |
| Cohere | GenAI |  |
| Replicate Text Models | GenAI |  |
| OpenAI API | GenAI | ✅ |
| GGUF (Llama.cpp) | GenAI, Lightweight Inference |  |
| OctoAI | GenAI |  |

**OWASP AI Exchange Threat Coverage**

| Topic | Coverage |
| --- | --- |
| Development time model poisoning |  |
| Runtime model poisoning |  |
| Model theft by use |  |
| Training data poisoning |  |
| Training data leak |  |
| Runtime model theft |  |
| Evasion (Tests model performance against adversarial inputs) | ✅ |
| Model inversion / Membership inference |  |
| Denial of model service |  |
| Direct prompt injection | ✅ |
| Data disclosure |  |
| Model input leak |  |
| Indirect prompt injection |  |
| Development time model theft |  |
| Output contains injection |  |

Notes:

- Evasion:Tests model performance against adversarial inputs  [*https://owaspai.org/goto/evasion/*](https://owaspai.org/goto/evasion/)
- Prompt Injection: Evaluates the robustness of generative AI models by exploiting weaknesses in prompt design, leading to undesired outputs or bypassing model safeguards. *https://owaspai.org/goto/promptinjection/*

### ツール名: Guardrail

| **Tool Name: Guardrail** |  |
| --- | --- |
| Developer/ Source | Guardrails AI |
| Github Reference | [GitHub - guardrails-ai/guardrails: Adding guardrails to large language models.](https://github.com/guardrails-ai/guardrails) | [Guardrails Hub | Guardrails AI](https://hub.guardrailsai.com/) |
| Language | Python |
| Licensing | Apache 2.0 License |
| Provides Mitigation | Prevention: Yes ✅ Detection: Yes ✅ |
| API Availability |  |

| Factor | Details |
| --- | --- |
| **Popularity** | - **GitHub Stars:** ~4,3K (as 2024) |
|  | - **GitHub Forks:** ~326 |
|  | - **Number of Issues:**  ~296 Closed, 40 Open.  |
|  | - **Trend:** Steady growth with consistent and timely updates. |
| **Community Support** | - **Active Issues:** Issues are mostly solved within weeks. |
|  | - **Documentation:** Detailed documentation with examples and user guide |
|  | - **Discussion Forums:**  Primarily github issues and also, support is available on discord Server and twitter. |
|  | - **Contributors:** Over 60 contributors |
| **Scalability** | - **Framework Support:** Supports Pytorch. Language: Python and Javascript. Working to add more support |
|  | - **Large-Scale Deployment:** Can be extended to Azure, langchain. |
| **Integration** | - **Compatibility:**  Compatible with various open source LLMs like OpenAI, Gemini, Anthropic. |

**Tool Rating**

| **Criteria** | **High** | **Medium** | **Low** |
| --- | --- | --- | --- |
| **Popularity** | ✅ |  |  |
| **Community Support** | ✅ |  |  |
| **Scalability** |  | ✅ |  |
| **Ease of Integration** | ✅ |  |  |

**Data Modality**

| Data Modality | Supported |
| --- | --- |
| Text | ✅ |
| Image |  |
| Audio |  |
| Video |  |
| Tabular data |  |

**Machine Learning Tasks**

| Task Type | Data Modality | Supported |
| --- | --- | --- |
| Classification | All (See Data modality section) | ✅ |
| Object Detection | Computer Vision |  |
| Speech Recognition | Audio |  |

**Framework Applicability**

| Framework / Tool | Category | Supported |
| --- | --- | --- |
| Tensorflow | DL, GenAI |  |
| PyTorch | DL, GenAI | ✅ |
| Azure OpenAI | GenAI | ✅ |
| Huggingface | ML, GenAI | ✅ |
| Azure managed endpoints | Machine Learning Deployment |  |
| Cohere | GenAI | ✅ |
| Replicate Text Models | GenAI |  |
| OpenAI API | GenAI | ✅ |
| GGUF (Llama.cpp) | GenAI, Lightweight Inference |  |
| OctoAI | GenAI |  |

**OWASP AI Exchange Threat Coverage**

| Topic | Coverage |
| --- | --- |
| Development time model poisoning |  |
| Runtime model poisoning |  |
| Model theft by use |  |
| Training data poisoning |  |
| Training data leak |  |
| Runtime model theft |  |
| Evasion (Tests model performance against adversarial inputs) | ✅ |
| Model inversion / Membership inference |  |
| Denial of model service |  |
| Direct prompt injection | ✅ |
| Data disclosure |  |
| Model input leak |  |
| Indirect prompt injection |  |
| Development time model theft |  |
| Output contains injection |  |

Notes:

- Evasion:Tests model performance against adversarial inputs  [*https://owaspai.org/goto/evasion/*](https://owaspai.org/goto/evasion/)
- Prompt Injection: Evaluates the robustness of generative AI models by exploiting weaknesses in prompt design, leading to undesired outputs or bypassing model safeguards.   *https://owaspai.org/goto/promptinjection/*

### ツール名: Promptfoo

| **Tool Name: Promptfoo** |  |
| --- | --- |
| Developer/ Source | Promptfoo community |
| Github Reference | [https://github.com/promptfoo/promptfoo](https://github.com/promptfoo/promptfoo) | [Types of LLM vulnerabilities | promptfoo](https://www.promptfoo.dev/docs/red-team/llm-vulnerability-types/) |
| Language | Python, NodeJS |
| Licensing | Open-source under the MIT License.  |
|  | This project is licensed under multiple licenses:

1. The main codebase is licensed under the MIT License (see below)
2. The `/src/redteam/` directory is proprietary and licensed under the Promptfoo Enterprise License
3. Some third-party components have their own licenses as indicated by LICENSE files in their respective directories |
| Provides Mitigation | Prevention: Yes ✅ Detection: Yes ✅ |
| API Availability | Yes ✅  |

| Factor | Details |
| --- | --- |
| **Popularity** | - **GitHub Stars:** ~4.3K stars (as of 2024) |
|  | - **GitHub Forks:**  ~320 forks |
|  | - **Number of Issues:** ~523 closed, 108 open |
|  | - **Trend:** Consistent update |
| **Community Support** | - **Active Issues:** Issues are  addressed within acouple of days. |
|  | - **Documentation:** Detailed documentation with user guide and examples. |
|  | - **Discussion Forums:** Active Github issue and also support available on Discord |
|  | - **Contributors:** Over 113 contributors. |
| **Scalability** | - **Framework Support:**  Language: JavaScript |
|  | - **Large-Scale Deployment:** Enterprise version available, that supports cloud deployment. |
| **Integration** | - **Compatibility:** Compatible with majority of the LLMs |

**Tool Rating**

| **Criteria** | **High** | **Medium** | **Low** |
| --- | --- | --- | --- |
| **Popularity** | ✅ |  |  |
| **Community Support** | ✅ |  |  |
| **Scalability** |  | ✅ |  |
| **Ease of Integration** |  | ✅ |  |

**Data Modality**

| Data Modality | Supported |
| --- | --- |
| Text | ✅ |
| Image |  |
| Audio |  |
| Video |  |
| Tabular data |  |

**Machine Learning Tasks**

| Task Type | Data Modality | Supported |
| --- | --- | --- |
| Classification | All (See Data modality section) | ✅ |
| Object Detection | Computer Vision |  |
| Speech Recognition | Audio |  |

**Framework Applicability**

| Framework / Tool | Category | Supported |
| --- | --- | --- |
| Tensorflow | DL, GenAI |  |
| PyTorch | DL, GenAI |  |
| Azure OpenAI | GenAI | ✅ |
| Huggingface | ML, GenAI | ✅ |
| Azure managed endpoints | Machine Learning Deployment |  |
| Cohere | GenAI | ✅ |
| Replicate Text Models | GenAI | ✅ |
| OpenAI API | GenAI | ✅ |
| GGUF (Llama.cpp) | GenAI, Lightweight Inference | ✅ |
| OctoAI | GenAI |  |

**OWASP AI Exchange Threat Coverage**

| Topic | Coverage |
| --- | --- |
| Development time model poisoning |  |
| Runtime model poisoning |  |
| Model theft by use |  |
| Training data poisoning |  |
| Training data leak |  |
| Runtime model theft |  |
| Evasion (Tests model performance against adversarial inputs) | ✅ |
| Model inversion / Membership inference |  |
| Denial of model service |   |
| Direct prompt injection |   |
| Data disclosure |   |
| Model input leak |   |
| Indirect prompt injection | ✅ |
| Development time model theft |  |
| Output contains injection |  |

Notes:

- Model theft through use:Evaluates risks of model exploitation during usage  [*https://owaspai.org/goto/modeltheftuse/*](https://owaspai.org/goto/modeltheftuse/)
- Prompt Injection: Evaluates the robustness of generative AI models by exploiting weaknesses in prompt design, leading to undesired outputs or bypassing model safeguards.
*[https://owaspai.org/goto/promptinjection/](https://owaspai.org/goto/promptinjection/)*

## ツール評価
This section rates the discussed tools by Popularity, Community Support, Scalability and Integration.

[![](https://owaspai.org/images/testtoolrating.png)](https://owaspai.org/images/testtoolrating.png)

| **Attribute** | High | Medium | Low |
| --- | --- | --- | --- |
| Popularity | >3,000 stars | 1,000–3,000 stars | <1,000 stars |
| Community Support | >100 contributors, quick response (<3 days) | 50–100 contributors, response in 3–14 days | <50 contributors, slow response (>14 days) |
| Scalability | Proven enterprise-grade, multi-framework | Moderate scalability, limited frameworks | Research focused, small-scale |
| Integration | Broad compatibility | Limited compatibility, narrow use-case | Minimal or no integration, research tools only |

Disclaimer on the use of the Assessment:

- ***Scope of Assessment: This review exclusively focuses on open-source RedTeaming tools. Proprietary or commercial solutions were not included in this evaluation.***
- ***Independent Review: The evaluation is independent and based solely on publicly available information from sources such as GitHub repositories, official documentation, and related community discussions.***
- ***Tool Version and Relevance: The information and recommendations provided in this assessment are accurate as of September 2024. Any future updates, enhancements, or changes to these tools should be verified directly via the provided links or respective sources to ensure continued relevance.***

***Tool Fit and Usage:***

*The recommendations in this report should be considered based on your organization's specific use case, scale, and security posture. Some tools may offer advanced features that may not be necessary for smaller projects or environments, while others may be better suited to specific frameworks or security goals.*
