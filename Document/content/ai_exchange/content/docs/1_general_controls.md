---
title: 1. 一般的なコントロール
heroTitle: "一般的なコントロール"
heroText: "これらはすべての組織が導入すべきコントロールです。"
weight: 2
---
> カテゴリ: コントロールのグループ  
> パーマリンク: https://owaspai.org/goto/generalcontrols/
## 1.1 一般的なガバナンスコントロール
> カテゴリ: コントロールのグループ  
> パーマリンク: https://owaspai.org/goto/governancecontrols/

#### #AIPROGRAM
> カテゴリ: ガバナンスコントロール  
> パーマリンク: https://owaspai.org/goto/aiprogram/

**Description**  
AI program: Install and execute a program to govern AI.  
One could argue that this control is out of scope for cyber security, but it initiates action to get in control of AI security.

**Objective**  
The objective of an AI Program is to take responsibility for AI as an organization and make sure that all AI initiatives are known and under control, including their security.

**Implementation**  
This governance challenge may seem daunting because of all the new things to take care of, but there are numerous existing controls in organizations already that can be extended to include AI (e.g. policies, risk analysis, impact analysis, inventory of used services etc.).  
See [How to organize AI security](/goto/organize/) for the 5 GUARD steps and to see how governance fits into the whole.  
An AI Program includes:
- Keeping an inventory of AI initiatives
- Perform impact analysis on initiatives
- Organize AI innovation
- Include AI risks in risk management
- Assign responsibilities, e.g. model accountability, data accountability, and risk governance
- AI literacy (e.g. [training](/goto/seceducate/)
- Organize [compliance](/goto/checkcompliance/)
- Incorporate AI assets in the [security program](/goto/secprogram/)

AI イニシアチブで影響分析を行う際には、少なくとも以下の点を考慮してください。
- AI プログラムは、セキュリティリスクなどの AI にとってのリスクだけでなく、公平性や安全性などに対する脅威などの AI によるリスクもあることに注意してください。
- AI アプリケーションの種類によっては禁止されている可能性があるため、法律や規制を含めます (EU AI 法におけるソーシャルスコアリングなど)。#[CHECKCOMPLIANCE](1_general_controls.md#CHECKCOMPLIANCE) を参照してください。
- AI がどのように動作するかについて、要求される透明性を提供できますか？
- プライバシー権 (個人データへのアクセス、消去、訂正、更新の権利、異議申し立ての権利) を達成できますか？
- 保護される人々のグループに関する望ましくない偏見を十分に緩和できますか？
- その問題を解決するには本当に AI が必要ですか？
- 適切な専門知識 (データサイエンティストなど) は利用可能ですか？
- 特に別の目的で集められた個人データである場合、その目的のためにデータを使用することは許可されていますか？
- 望ましくない動作は緩和策 (望ましくない動作を制限するコントロールを参照) によって十分に抑制できますか？
- プライバシーを含むセキュリティ固有のリスク分析については [SECPROGRAM](1_general_controls.md#SECPROGRAM) のリスクマネジメントを参照してください。

**特殊性**  
一般的なリスクマネジメントでは、以下のような AI の特殊性を念頭に置くと役立つかもしれません。
1. 演繹的ではなく帰納的、つまり、機械学習モデルにとって間違っていることはゲームの一部であり、損害につながる可能性があります。
2. 1 に関連: モデルは陳腐化する可能性があります。
3. データに基づいて動作を組織化するため、データは機会 (複雑な現実世界の問題解決、適応性など) とリスク (望ましくないバイアス、不完全性、エラー、操作など) の源となります。
4. 組織や人々にとって馴染みのないものであり、実装ミス、過小な信頼、過大な信頼、人間の傾向の誤った帰属などのリスクがあります。
5. 理解できないものであり、信頼性に問題が生じます。
6. セキュリティ脅威を形作る新しい技術的資産 (データ/モデルサプライチェーン、トレーニングデータ、モデルパラメータ、AI ドキュメント) です。
7. 聴くことも話すこともできます: ユーザーインタフェースではなく自然言語を通じてやり取りします。
8. 聞くことも見ることもできます: 音声認識能力と視覚認識能力を持ちます。

**参考情報**  

 - [UNESCO on AI ethics and governance](https://www.unesco.org/ethics-ai/en)
 - [GenAI security project LLM AI Cybersecurity & governance checklist](https://genai.owasp.org/resource/llm-applications-cybersecurity-and-governance-checklist-english/)

有用な標準:
 - ISO/IEC 42001 AI マネジメントシステム。ギャップ: このコントロールを完全にカバーします。
 - [US Federal Reserve SR 11-07: Guidance on Model Risk Management](https://www.federalreserve.gov/supervisionreg/srletters/sr1107.htm): 銀行組織および監督当局のための監督指針。

ISO 42001 はリスクマネジメントシステムを拡張するもので、ガバナンスに焦点を当てています。ISO 5338 (下記 #[DEVPROGRAM](1_general_controls.md#DEVPROGRAM) 参照) はソフトウェアライフサイクルプラクティスを拡張するもので、エンジニアリングとその周辺のすべてに焦点を当てています。ISO 27001 が情報セキュリティのマネジメントシステムであるのと同様に、ISO 42001 は組織内の責任ある AI のガバナンスのためのマネジメントシステムとみなすことができます。ISO 42001 はライフサイクルプロセスには踏み込みません。たとえば、モデルのトレーニング方法、データリネージの実行方法、継続的検証、AI モデルのバージョン管理、プロジェクト計画の課題、エンジニアリングで機密データがいつどのように使用されるかについては触れていません。


#### #SECPROGRAM
> カテゴリ: ガバナンスコントロール  
> パーマリンク: https://owaspai.org/goto/secprogram/

**説明**  
セキュリティプログラム: 組織にセキュリティプログラム (_情報セキュリティマネジメントシステム_ ともよばれます) があり、AI ライフサイクル全体と AI 固有の側面を含むことを確認します。

**目的**  
セキュリティプログラムが AI 固有の脅威と対応するリスクに責任を持つことにより、情報セキュリティマネジメントを通じて AI セキュリティリスクを適切に軽減します。リスク分析でのこのドキュメントの使用の詳細については [リスク分析セクション](ai_security_overview.md#how-to-select-relevant-threats-and-controls-risk-analysis) を参照してください。

**実施**  
AI 固有の資産とそれらに対する脅威を必ず含めます。脅威はこのリソースでカバーされており、資産は以下のとおりです。
- トレーニングデータ
- テストデータ
- モデル - 多くの場合 _モデルパラメータ_ (モデルの学習時に変化する値) と呼ばれます
- ハイパーパラメータ
- 実験を含むモデルとその開発プロセスの文書化
- モデル入力
- モデル出力。トレーニングデータやモデルが信頼できない場合は、信頼できないものとみなす必要があります
- 意図したモデル動作
- 外部ソースから取得したトレーニングおよびテスト用のデータ
- 外部ソースからトレーニングおよび使用するモデル

これらの資産とそれらに対する脅威を組み込むことにより、セキュリティプログラムがこれらのリスクを軽減します。たとえば、意識向上トレーニングでエンジニアにドキュメントをその辺に置きっぱなしにしないよう告げます。あるいは、エンジニアが扱うとレーニンデータは機密性が高いため、エンジニアのマシンにマルウェア検出機能をインストールします。

新規、既存を問わず、すべての AI イニシアチブはプライバシーとセキュリティのリスク分析を実行すべきです。AI プログラムにはプライバシーとセキュリティに関するさらなる懸念があり、それを考慮する必要があります。各システムの実装はそのコンテキスト上の目的によって異なりますが、同じプロセスを適用できます。これらの分析は開発プロセスの前に実行でき、システムのセキュリティとプライバシーのコントロールをガイドします。これらのコントロールは機密性 (Confidentiality)、完全性 (Integrity)、可用性 (Availability) などのセキュリティ保護目標と、提示先の秘匿 (Unlinkability)、透明性 (Transparency)、介入可能性 (Intervenability) などのプライバシー目標に基づきます。ISO/IEC TR 27562:2023 はこれらの目標と適用範囲に関する注意事項の詳細なリストを提供します。

AI ユースケースのプライバシーとセキュリティの分析を実行するための一般的なプロセスは以下のとおりです。
 - エコシステムを記述します
 - 対称システムの評価を提供します
 - セキュリティとプライバシーの懸念事項を特定します
 - セキュリティとプライバシーのリスクを特定します
 - セキュリティとプライバシーのコントロールを特定します
 - セキュリティとプライバシーの保証に関する懸念事項を特定します

AI には特定の資産 (トレーニングデータなど) があるため、**AI 固有のハニーポット** は特に興味深いコントロールです。これは攻撃者が実際の資産にアクセスする前に、攻撃者を検出または捕捉するために、意図的に公開しているデータ/モデル/データサイエンスインフラストラクチャの偽物です。たとえば、以下があります。

- データサービスは堅牢化されていますが、パッチ未適用の脆弱性があります (Elasticsearch など)
- データレイクが公開されていますが、実際の資産の詳細は明らかになりません
- データアクセス API がブルートフォース攻撃に対して脆弱です
- 開発設備に似せた「ミラー」データサーバーですが、本番環境では SSH アクセスで公開され、"lab" などの名前でラベル付けされています
- ドキュメントが「うっかり」公開されていますが、ハニーポットに誘導するものです
- データサイエンス Python ライブラリがサーバー上に公開されています
- 特定のライブラリへの外部アクセスが許可されています
- GitHub からモデルをそのままインポートしています

監視とインシデント対応はセキュリティプログラムの標準的な要素であり、AI は関連する AI セキュリティ資産、脅威、コントロールを理解することでそれに含めることができます。脅威の説明には監視の一部となる検出メカニズムを含みます。


**参考情報**  
有用な標準:

  - ISO 27000-27005 の全範囲は IT システムであるため、一般的な意味で AI システムに適用できます。ギャップ: プロセスに関してこのコントロールを完全にカバーしており、情報セキュリティマネジメントで考慮する必要がある三つの AI 固有の攻撃対象領域があるという高レベルの特殊性があります: 1) AI 開発時の攻撃、2) モデルの使用による攻撃、3) AI アプリケーションセキュリティ攻撃。特殊性の詳細については対応するセクションのコントロールを参照してください。
    これらの標準には以下があります。

    - ISO/IEC 27000 – 情報セキュリティマネジメントシステム - 概要と用語
    - ISO/IEC 27001 – 情報セキュリティマネジメントシステム - 要件
    - ISO/IEC 27002 – 情報セキュリティマネジメントの実践のための規範 (下記参照)
    - ISO/IEC 27003 – 情報セキュリティマネジメントシステム: 実装ガイドライン
    - ISO/IEC 27004 – 情報セキュリティマネジメント測定
    - ISO/IEC 27005 – 情報セキュリティリスクマネジメント

  - このドキュメント全体で言及されている「ISO 27002 コントロール」は ISO 27001 の Annex にリストされており、ISO 27002 の実践で詳しく説明されています。抽象度の高いレベルでは、最も関連のある ISO 27002 コントロールは以下の通りです。
    - ISO 27002 コントロール 5.1 情報セキュリティのための方針群
    - ISO 27002 コントロール 5.10 情報およびその他の関連資産の許容される使用
    - ISO 27002 コントロール 5.8 プロジェクトマネジメントにおける情報セキュリティ
  - [OpenCRE のセキュリティプログラムマネジメント](https://www.opencre.org/cre/261-010)
  - リスク分析標準:
    - このドキュメントはリスク分析を容易にする AI セキュリティの脅威とコントロールを含みます。
    - [MITRE ATLAS framework for AI threats](https://atlas.mitre.org/) も参照してください。
    - ISO/IEC 27005 - 上述の通りです。ギャップ: このコントロールを完全にカバーしており、上記の特殊性を伴います (27005 は AI 固有の脅威について言及していないため)。
    - ISO/IEC 27563:2023 (AI ユースケースのセキュリティとプライバシー) AI ユースケースにおけるセキュリティとプライバシーの影響について説明しており、AI セキュリティリスク分析への有用なインプットとして役立つかもしれません。この取り組みでは ISO/IEC TR 24030:2021 の 22 のアプリケーションドメインに属する 132 のユースケースの AI ユースケースのリストを基にしており、セキュリティに関する最大の懸念評価を持つ 11 のユースケースと、プライバシーに関する最大の懸念評価を持つ 49 のユースケースを特定しています
    - ISO/IEC 23894 (AI リスクマネジメント)。ギャップ: このコントロールを完全にカバーします - AI セキュリティ脅威については ISO/IEC 24028 (AI の信頼性) を参照しています。かし、ISO/IEC 24028 は脅威の列挙よりもリスクマネジメントに重点を置いているため、AI Exchange (このドキュメント) や MITRE ATLAS ほど包括的ではありません。
    - ISO/IEC 5338 (AI ライフサイクル) は AI リスクマネジメントプロセスをカバーします。ギャップ: 上記 ISO 23894 と同様です。
    - [ETSI の脅威、脆弱性、リスク分析のための手法とプロフォーマ](https://www.etsi.org/deliver/etsi_ts/102100_102199/10216501/05.02.03_60/ts_10216501v050203p.pdf)
    - [NIST AI リスクマネジメントフレームワーク](https://nvlpubs.nist.gov/nistpubs/ai/NIST.AI.100-1.pdf)
    - [OpenCRE のセキュリティリスク分析](https://www.opencre.org/cre/307-242)
    - [NIST SP 800-53 の一般的なセキュリティ/プライバシーコントロール](https://csrc.nist.gov/pubs/sp/800/53/r5/upd1/final)
    - [NIST サイバーセキュリティフレームワーク](https://www.nist.gov/cyberframework)
    - [GenAI security project LLM and GenAI Security Center of Excellence guide](https://genai.owasp.org/resource/llm-and-generative-ai-security-center-of-excellence-guide/)


#### #SECDEVPROGRAM
> カテゴリ: ガバナンスコントロール  
> パーマリンク: https://owaspai.org/goto/secdevprogram/

**説明**  
セキュア開発プログラム: ソフトウェア開発に関するプロセスを整備し、AI システムにセキュリティが組み込まれていることを確認します。

**目的**  
ソフトウェア開発時にリスクを軽減するために適切な注意を払うことでセキュリティリスクを低減します。

**実施**  
このための最善の方法は既存の安全なソフトウェア開発プラクティスの上に AI チームと AI の特殊性を取り入れることです。つまり、データサイエンス開発アクティビティが安全なソフトウェア開発プラクティスの一部になるべきです。これらのプラクティスの例: セキュア開発トレーニング、コードレビュー、セキュリティ要件、セキュアコーディングガイドライン、脅威モデリング (AI 固有の脅威を含む)、静的解析ツール、動的解析ツール、ペネトレーションテスト。AI のための独立したセキュア開発フレームワークは必要ありません。

**特殊性**  
ソフトウェア開発における AI の特殊性、およびその対処方法:
- AI involves new types of engineering: data engineering and model engineering (e.g. model training), together with new types of engineers: e.g. data scientists, data engineers, AI engineers. Make sure this new engineering becomes an integral part of the general [Development program](/goto/devprogram/) with its best practices (e.g. versioning, portfolio management, retirement). For example: Version management/traceability of the combination of code, configuration, training data and models, for troubleshooting and rollback

- 新しい資産、脅威、コントロール (このドキュメントでカバーしている) を考慮する必要があり、要件、ポリシー、コーディングガイドライン、トレーニング、ツール、テストプラクティスなどに影響します。通常、これは [SECPROGRAM](1_general_controls.md#SECPROGRAM) で説明しているように、組織の情報セキュリティ管理システムにこれらの要素を追加し、従来の資産、脅威、コントロールに合わせて調整しているのと同様に、安全なソフトウェア開発をそれに合わせて調整します ([SECDEVPROGRAM](1_general_controls.md#SECDEVPROGRAM) 参照)。This involves both conventional security threats and AI-specific threats, applying both conventional security controls and AI-specific ones. Typically, technical teams depend on the AI engineers when it comes to the AI-specific controls as they mostly require deep AI expertise. For example: if training data is confidential and collected in a distributed way, then a federated learning approach may be considered.

- Apart from software components, the supply chain for AI can also include data and models which may have been poisoned, which is why data provenance and model management are central in [AI supply chain management](/goto/supplychainmanage/).
- In AI, software components can also run in the development, for example tools to prepare training data or train a model. Because of this, the AI development environment is vulnerable to traditional software security risks, such as open source package vulnerabilities, CWEs, exposed secrets, and sensitive data leaks. Without robust controls in place, these risks go undetected by standard application security testing tools, potentially exposing the entire lifecycle to breaches.

- The AI development environment typically involves sensitive data, in contrast to conventional engineering where the use of such data by engineers is normally avoided. Therefore, apply [development security](/goto/devsecurity/) on the development environment. In addition to the conventional assets of code, configuration and secrets, the AI-specific development assets are:
  - Potentially sensitive data needed to train, test and validate models
  - Model parameters, which often represent intellectual property and can also be used to prepare input attacks when obtained.


- New best practices or pitfalls in AI-specific code:
  - Run static analysis rules specific to big data/AI technology (e.g., the typical mistake of creating a new dataframe in Python without assigning it to a new one)
  - Run maintainability analysis on code, as data and model engineering code is typically hindered by code quality issues
  - Evaluate code for the percentage of code for automated testing. Industry average is 43% (SIG benchmark report 2023). An often cited recommendation is 80%. Research shows that automated testing in AI engineering is often neglected (SIG benchmark report 2023), as the performance of the AI model is mistakenly regarded as the ground truth of correctness.

- Model performance testing is essential
  - Run AI-specific dynamic performance tests before deployment (see [#CONTINUOUSVALIDATION](/goto/continuousvalidation/)):
  - Run security tests (e.g. data poisoning payloads, prompt injection payloads, adversarial robustness testing). See the [testing section](/goto/testing/).
  - Run continual automated validation of the model, including discrimination bias measurement and the detection of staleness: the input space changing over time, causing the training set to get out of date
- Model deployment is a new aspect to AI and it may offer  specific protection measures such as obfuscation, encryption, integrity checks or a Trusted Execution Environment.

**Risk-Reduction guidance**  
Depending on risk analysis, certain threats may require specific practices in the development lifecycle. These threats and controls are covered elsewhere in this document.

**参考情報**  
- [OWASP SAMM](https://owaspsamm.org)
- [NIST SSDF](https://csrc.nist.gov/projects/ssdf)
- [NIST SSDF AI practices](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-218A.ipd.pdf)
- [GenAI security project solutions overview](https://genai.owasp.org/ai-security-solutions-landscape/)

有用な標準:
- ISO 27002 コントロール 8.25 安全な開発ライフサイクル。ギャップ: このコントロールを完全にカバーしており、上記の特殊性を伴いますが、詳細は欠如しています - ISO 27002:2022 の 8.25 コントロール の説明は一ページですが、安全なソフトウェア開発は大規模かつ複雑なトピックです - 詳細については以下を参照してください。
- ISO/IEC 27115 (複合システムのサイバーセキュリティ評価)
- [OpenCRE の安全なソフトウェア開発プロセス](https://www.opencre.org/cre/616-305) を参照してください。NIST SSDF や OWASP SAMM への注目すべきリンクがあります。ギャップ: このコントロールを完全にカバーしており、上記の特殊性を伴います。


#### #DEVPROGRAM
> カテゴリ: ガバナンスコントロール  
> パーマリンク: https://owaspai.org/goto/devprogram/

**説明**  
開発プログラム: AI の開発ライフサイクルプログラムを持つこと。一般的な (セキュリティ指向だけではない) ソフトウェアエンジニアリングのベストプラクティスを AI 開発に適用します。

データサイエンティストは実用的なモデルを作成することに重点を置いているのであって、いわゆる将来性のあるソフトウェアを作成することではありません。多くの場合、組織はすでにソフトウェアのプラクティスとプロセスを導入しています。AI を別のアプローチが必要なものとして扱うのではなく、これらを AI 開発に拡張することが重要です。AI エンジニアリングを分離しないでください。これには自動テスト、コード品質、文書化、バージョン管理を含みます。ISO/IEC 5338 ではこれらのプラクティスを AI に適用する方法について説明しています。

**目的**  
こうすることで、AI システムは保守が容易になり、移転可能で、安全で、信頼性が高まり、将来性があるものになります。

**実施**  
ベストプラクティスはチーム内でデータサイエンティストのプロファイルとソフトウェアエンジニアリングのプロファイルを混在させることです。通常、ソフトウェアエンジニアはデータサイエンスについてさらに学ぶ必要があり、データサイエンティストは一般的に将来性があり、保守可能で、テストしやすいコードの作成についてさらに学ぶ必要があるためです。

もう一つのベストプラクティスはデータサイエンスコードの品質面 (保守性、テストコードカバレッジ) を継続的に測定し、それらの品質レベルを管理する方法についてデータサイエンティストにコーチングを提供することです。

従来のソフトウェアのベストプラクティスとは別に、重要な AI 固有のエンジニアリングプラクティスがあります。これにはたとえば、データの来歴と系統、モデルのトレーサビリティ、継続的バリデーションやモデルの陳腐化とコンセプトドリフトのテストなどの AI 固有のテストなどを含みます。ISO/IEC 5338 ではこれらの AI エンジニアリングプラクティスについて説明しています。

開発ライフサイクルの主要な部分となる関連コントロール:
- [セキュア開発プログラム](1_general_controls.md#SECDEVPROGRAM)
- [サプライチェーンマネジメント](3_development_time_threats.md#SUPPLYCHAINMANAGE)
- [継続的バリデーション](1_general_controls.md#CONTINUOUSVALIDATION)
- [望ましくないバイアステスト](1_general_controls.md#UNWANTEDBIASTESTING)

以下の ISO/IEC 5338 の解釈図は、関連するトピックの概要を把握するのに適しています。
![5338](https://raw.githubusercontent.com/OWASP/www-project-ai-security-and-privacy-guide/main/content/ai_exchange/static/images/5338.png)

**参考情報**  

  - [AI システムにおけるコード品質のギャップに関する研究](https://www.softwareimprovementgroup.com/averting-a-major-ai-crisis-we-need-to-fix-the-big-quality-gap-in-ai-systems/)

有用な標準:

  - [ISO/IEC 5338 - AI ライフサイクル](https://www.iso.org/standard/81118.html) ギャップ: このコントロールを完全にカバーします - ISO 5338 はソフトウェアライフサイクルに関する既存の ISO 12207 標準を拡張することにより、AI のソフトウェア開発ライフサイクル全体をカバーします。いくつかの新しいプロセスを定義し、既存のプロセスの AI 固有の特殊性について議論します。[このブログ](https://www.softwareimprovementgroup.com/iso-5338-get-to-know-the-global-standard-on-ai-systems/) も参照してください。
  - [ISO/IEC 27002](https://www.iso.org/standard/75652.html) コントロール 5.37 操作手順の文書化。ギャップ: このコントロールを最小限にカバーします - これはコントロールのごく一部のみをカバーします。
  - [OpenCRE の機能の文書化](https://www.opencre.org/cre/162-655) ギャップ: このコントロールを最小限にカバーします

#### #CHECKCOMPLIANCE
> カテゴリ: ガバナンスコントロール  
> パーマリンク: https://owaspai.org/goto/checkcompliance/

**説明**  
コンプライアンスのチェック: コンプライアンスマネジメント (セキュリティの側面を含む) において、AI 関連の法規制が考慮されていることを確認します。個人データが関連する場合や個人に関する意思決定に AI が適用される場合は、プライバシーの法規制も適用範囲となります。詳細については [プライバシーセクション](6_privacy.md) を参照してください。

**目的**  
目標としてのコンプライアンスは組織が AI への対応を高める強力な推進力となり得ます。そのためには、法規制には必ずしも組織に関連するすべてのリスクが含まれるわけではない範囲があることを念頭に置くことが重要です。多くの規則は個人や社会に対する潜在的な危害に関するものであり、ビジネスの利害そのものへの影響はカバーしていません。たとえば、欧州の AI 法には企業秘密保護に関するリスクは含まれません。つまり、法律や規制をガイドとして使用する際には、盲点に注意する必要があります。

世界の法的管轄区域に関する考慮事項 (2023年末時点):
- カナダ: 人工知能およびデータ法 (Artificial Intelligence & Data Act)
- アメリカ: (i) 連邦 AI 開示法 (Federal AI Disclosure Act), (ii) 連邦アルゴリズム責任法 (Federal Algorithmic Accountability Act)
- ブラジル: AI 規制フレームワーク (AI Regulatory Framework)
- インド: デジタルインド法 (Digital India Act)
- ヨーロッパ: (i) AI 法 (AI Act), (ii) AI 責任指令 (AI Liability Directive), (iii) 製造物責任指令 (Product Liability Directive)
- 中国: (i) インターネット情報サービス深層合成管理条例 (Regulations on the Administration of Deep Synthesis of Internet Information Services), (ii) 上海市 AI 産業発展促進条例 (Shanghai Municipal Regulations on Promoting Development of AI Industry), (iii) 深圳経済特区 AI 産業促進条例 (Shenzhen Special Economic Zone AI Industry Promotion Regulations), (iv) 生成 AI サービス暫定行政措置 (Provisional Administrative Measures for Generative AI Services)

**実施**  
AI/セキュリティに関する一般的な法的考慮事項:
- プライバシー法: AI は GDPR, CCPA, HIPAA などのすべてのローカル/グローバルのプライバシー法を常に遵守しなければいけません。[プライバシーセクション](6_privacy.md) を参照。
- データガバナンス: 統合のためにサードパーティから提供される AI コンポーネント/機能は、個人データの保護、その収集、処理、保存方法の構造/定義を含む、データガバナンスフレームワークを備えていなければいけません。
- データ侵害: サードパーティサプライヤは、データの保存方法とそのセキュリティフレームワークについて回答しなければいけません。これはエンドユーザーの個人データや IP を含む可能性があります。

セキュリティ以外のコンプライアンスの考慮事項:
- 倫理: ディープフェイクの武器化と、システムがそれにどのように対応し、対処し、保護し、軽減するか
- 人的管理: あらゆる AI システムは、個人に対するリスクを確認した上で、適切なレベルの人的管理と監視の下で導入すべきです。AI システムは、AI の使用が個人の尊厳と権利を尊重するコンセプトで設計され活用されるべきです。「Keep the human in the loop」コンセプト。[OVERSIGHT](1_general_controls.md#OVERSIGHT) を参照。
- 差別: バイアルを回避および防止するために、データセットをレビューするプロセスを含めなければいけません。[UNWANTEDBIASTESTING](1_general_controls.md#UNWANTEDBIASTESTING) を参照。
- 透明性: AI システムのデプロイメント、使用、規制要件への積極的なコンプライアンスにおける透明性を確保します。「Trust by Design」
- 説明責任: AI システムは、アクション、出力、データセットの使用について説明責任を負うべきです。[AIPROGRAM](1_general_controls.md#AIPROGRAM) を参照。

**参考情報**  
  - [AI の法的側面について語る Vischer](https://www.vischer.com/en/artificial-intelligence/)
  - [SIG による AI 法の概要](https://www.softwareimprovementgroup.com/eu-ai-act-summary/)
  - [SIG による米国の AI 関連法制の概要](https://www.softwareimprovementgroup.com/us-ai-legislation-overview/)

有用な標準:

  - [OpenCRE のコンプライアンス](https://www.opencre.org/cre/510-324)
  - ISO 27002 コントロール 5.36 ポリシー、ルール、標準の遵守。ギャップ: このコントロールを完全にカバーしますが、AI 規制を考慮する必要がある特殊性を伴います。
  - ISO/IEC 27090 (AI セキュリティ) と 27091 (AI プライバシー) は本稿執筆時点 (2025 年 10 月) で開発中であり、2026 年に発行される見込みです。AI Exchange は 27090 のコンテンツに多大な貢献をしています。
  - prEN 18282 は AI セキュリティに関する欧州規格です。CEN/CENELEC によって策定され、AI Exchange が重要な部分を貢献しています。Exchange の創設者 Rob van der Veer  は、AI Exchange と CEN/CENELEC/ISO 間の公式なパートナーシップにおける連絡担当者であり、18282 の共同編集者でもあります。この規格は本稿執筆時点 (2025 年 10 月) で約二年間開発が進められており、2026 年初頭に公開調査が開始され、2026 年に発行される予定です。

#### #SECEDUCATE
> カテゴリ: ガバナンスコントロール  
> パーマリンク: https://owaspai.org/goto/seceducate/

**説明**  
データサイエンティストと開発チームに対して、モデルへの攻撃を含む AI 脅威の意識に関するセキュリティ教育を実施します。データサイエンティストを含むすべてのエンジニアがセキュリティの考え方を身につけることが不可欠です。

**参考情報**  
有用な標準:
  - ISO 27002 コントロール 6.3 意識向上トレーニング。ギャップ: このコントロールを完全にカバーしますが、詳細が不足しており、特殊性を考慮する必要があります。トレーニング資料は AI セキュリティの脅威とコントロールをカバーする必要があります。

---

## 1.2 機密データ制限の一般的なコントロール
> カテゴリ: コントロールのグループ  
> パーマリンク: https://owaspai.org/goto/datalimit/

機密性と完全性に対するセキュリティ脅威の影響は、データの攻撃対象領域を制限することで軽減できます。つまり、データの量と種類および保存期間を可能な限り減らします。このセクションではこの制限を適用するためのいくつかのコントロールについて説明します。

#### #DATAMINIMIZE
> カテゴリ: 開発時および実行時のコントロール  
> パーマリンク: https://owaspai.org/goto/secdevprogram/

**説明**  
データの最小化: 潜在的なデータ漏洩や操作を防ぐために、アプリケーションにとって不必要なデータフィールドや (トレーニングセットなどからの) レコードを削除します。そもそも存在しないものを漏洩できないためです。

**Objective**  
Minimize the impact of data leakage or manipulation by reducing the amount of data processed by the system.

**Applicability**  
Data minimization applies during data collection, preparation, training, evaluation, and runtime logging. It is particularly relevant when datasets contain personal, confidential, or exposure-restricted information.
An exception to applicability to the AI system provider is when the deployer is better positioned to implement (part of) this control, as long as the provider communicates this requirement to the deployer. 

**Implementation**  
In addition to removing (or archiving) unused or low-impact fields and records, data minimization can include:
- removing data elements (fields, record) that do not materially affect model performance (e.g. correctness, robustness, fairness) based on experimentation or analysis;
- retaining certain identifiers only to support data removal requests or lifecycle management, while excluding them from model training;
- updating training datasets to reflect removals or corrections made in upstream source data (e.g. when personal data is destroyed from the source data then training data is updated to reflect the change);
- original data can be preserved separately with access controls for future use.

**Risk-Reduction Guidance**  
Data minimization reduces confidentiality risk by limiting the presence of exposure-restricted information. Data that is not collected or retained cannot be leaked, reconstructed, or inferred from the system. It also reduces the consequences of dataset theft or unauthorized access. 

**Particularity**  
AI models often tolerate reduced feature sets and incomplete data better than traditional applications, enabling stronger minimization strategies without functional loss.

**References**  
有用な標準:
  - ISO/IEC 標準ではまだカバーされていません。

#### #ALLOWEDDATA
> カテゴリ: 開発時および実行時のコントロール    
> パーマリンク: https://owaspai.org/goto/alloweddata/

**説明**  
許可されたデータを確認します。つまり、意図した目的では禁止されているデータを (トレーニングデータなどから) 削除することを意味します。これは同意が得られておらず、データに別の目的で収集された個人情報を含む場合に特に重要です。

**目的**  
コンプライアンスとは別に、データの漏洩や操作の影響を最小限に抑えることが目的です。

**参考情報**  
有用な標準:

  - ISO/IEC 23894 (AI リスクマネジメント) は A.8 プライバシーでこれをカバーしています。ギャップ: このコントロールを完全にカバーし、アイデアに関する簡単なセクションがあります。

#### #SHORTRETAIN
> カテゴリ: 開発時および実行時のコントロール    
> パーマリンク: https://owaspai.org/goto/shortretain/

**説明**  
短期保持: 必要がなくなったり、法的に (プライバシー法などにより) 要求された場合、データを削除または匿名化します。

**目的**  
データ漏洩や操作の影響を最小限に抑えます

**実施**  
データの保存期間を制限することは、データ最小化の特殊な形態とみなすことができます。プライバシー規制では一般的に、個人データが収集された目的に対して必要なくなった場合に、その個人データを削除することが求められます。場合によっては、他の規則 (証跡の記録を残すためなど) のために例外を設ける必要があります。これらの規制とは別に、データ漏洩の影響を軽減するために、機密データを使用しなくなった時点で削除することが一般的なベストプラクティスです。

**参考情報**  
有用な標準:

  - ISO/IEC 標準ではまだカバーされていません。

#### #OBFUSCATETRAININGDATA
> Category: development-time data science control    
> Permalink: https://owaspai.org/goto/obfuscatetrainingdata/

**Description**  
Obfuscate training data: attain a degree of obfuscation of sensitive data where possible.

**Objective**  
Minimize the impact of data leakage or manipulation when sensitive data cannot be removed entirely, by making the data less recognizable or harder to reconstruct.

**Applicability**  
Data obfuscation is particularly relevant when exposure-restricted data is necessary for training, compliance, or risk mitigation, and cannot be removed.
An exception to applicability to the AI system provider is when the deployer is better positioned to implement this control, as long as the provider communicates this requirement to the deployer. 

**Implementation**  
Obfuscation techniques include:  

- **Private Aggregation of Teacher Ensembles (PATE)**  
Private Aggregation of Teacher Ensembles (PATE) is a privacy-preserving machine learning technique. This method tackles the challenge of training models on sensitive data while maintaining privacy. It achieves this by employing an ensemble of "teacher" models along with a "student" model. Each teacher model is independently trained on distinct subsets of sensitive data, ensuring that there is no overlap in the training data between any pair of teachers. Since no single model sees the entire dataset, it reduces the risk of exposing sensitive information. Once the teacher models are trained, they are used to make predictions. When a new (unseen) data point is presented, each teacher model gives its prediction. These predictions are then aggregated to reach a consensus. This consensus is considered more reliable and less prone to individual biases or overfitting to their respective training subsets. To further enhance privacy, noise is added to the aggregated predictions. By adding noise, the method ensures that the final output doesn't reveal specifics about the training data of any individual teacher model. The student model is trained not on the original sensitive data, but on the aggregated and noised predictions of the teacher models. Essentially, the student learns from the collective wisdom and privacy-preserving outputs of the teachers. This way, the student model can make accurate predictions without ever directly accessing the sensitive data. However, there are challenges in balancing the amount of noise (for privacy) and the accuracy of the student model. Too much noise can degrade the performance of the student model, while too little might compromise privacy.
 
- **Objective function perturbation**
Objective function perturbation is a differential privacy technique used to train machine learning models while maintaining data privacy. It involves the intentional introduction of a controlled amount of noise into the learning algorithm’s objective function, which is a measure of the discrepancy between a model’s predictions and the actual results. The perturbation, or slight modification, involves adding noise to the objective function, resulting in a final model that doesn’t exactly fit the original data, thereby preserving privacy. The added noise is typically calibrated to the objective function’s sensitivity to individual data points and the desired privacy level, as quantified by parameters like epsilon in differential privacy. This ensures that the trained model doesn’t reveal sensitive information about any individual data point in the training dataset. The main challenge in objective function perturbation is balancing data privacy with the accuracy of the resulting model. Increasing the noise enhances privacy but can degrade the model’s accuracy. The goal is to strike an optimal balance where the model remains useful while individual data points stay private.

- **Masking**  
Masking involves the alteration or replacement of sensitive features within datasets with alternative representations that retain the essential information required for training while obscuring sensitive details. Various methods can be employed for masking, including tokenization, perturbation, generalization, and feature engineering. Tokenization replaces sensitive text data with unique identifiers, while perturbation adds random noise to numerical data to obscure individual values. Generalization involves grouping individuals into broader categories, and feature engineering creates derived features that convey relevant information without revealing sensitive details. Once the sensitive features are masked or transformed, machine learning models can be trained on the modified dataset, ensuring that they learn useful patterns without exposing sensitive information about individuals. However, achieving a balance between preserving privacy and maintaining model utility is crucial, as more aggressive masking techniques may lead to reduced model performance.

- **Encryption**  
Encryption is a fundamental technique for pseudonymization and data protection. It underscores the need for careful implementation of encryption techniques, particularly asymmetric encryption, to achieve robust pseudonymization. Emphasis is placed on the importance of employing randomized encryption schemes, such as Paillier and Elgamal, to ensure unpredictable pseudonyms. Furthermore, homomorphic encryption, which allows computations on ciphertexts without the decryption key, presents potential advantages for cryptographic operations but poses challenges in pseudonymization. The use of asymmetric encryption for outsourcing pseudonymization and the introduction of cryptographic primitives like ring signatures and group pseudonyms in advanced pseudonymization schemes are important.  
There are two models of encryption in machine learning:
  1. (part of) the data remains in encrypted form for the data scientists all the time, and is only in its original form for a separate group of data engineers that prepare and then encrypt the data for the data scientists.
  2. The data is stored and communicated in encrypted form to protect against access from users outside the data scientists, but is used in its original form when analysed, and transformed by the data scientists and the model. In the second model it is important to combine the encryption with proper access control, because it hardly offers protection to encrypt data in a database and then allow any user access to that data through the database application.

- **Tokenization**  
Tokenization is a technique for obfuscating data with the aim of enhancing privacy and security in the training of machine learning models. The objective is to introduce a level of obfuscation to sensitive data, thereby reducing the risk of exposing individual details while maintaining the data's utility for model training. In the process of tokenization, sensitive information, such as words or numerical values, is replaced with unique tokens or identifiers. This substitution makes it difficult for unauthorized users to derive meaningful information from the tokenized data.  
Within the realm of personal data protection, tokenization aligns with the principles of differential privacy. When applied to personal information, this technique ensures that individual records remain indiscernible within the training data, thus safeguarding privacy. Differential privacy involves introducing controlled noise or perturbations to the data to prevent the extraction of specific details about any individual.  
Tokenization aligns with this concept by replacing personal details with tokens, increasing the difficulty of linking specific records back to individuals.
Tokenization proves particularly advantageous in development-time data science when handling sensitive datasets. It enhances security by enabling data scientists to work with valuable information without compromising individual privacy. The implementation of tokenization techniques supports the broader objective of obfuscating training data, striking a balance between leveraging valuable data insights and safeguarding the privacy of individuals.

**Risk-Reduction Guidance**  
Obfuscation reduces the likelihood that training data can be reconstructed or linked back to individuals. Effectiveness can be evaluated through attack testing or by relying on formal privacy guarantees such as differential privacy or an equivalent mathematical framework. Residual risk remains when exposure-restricted data is still present, when obfuscation mechanisms fail, or when reconstruction or re-identification remains possible, such as through access to token mapping tables.

**Particularity**  
AI models typically do not require exact or human-readable representations of training data, allowing obfuscation techniques that would be impractical in traditional systems. In traditional systems, data attributes are processed directly leaving less room for obfuscation techniques. 

**Limitations**  
Obfuscation reduces the risk of re-identification or inference, but does not eliminate it:
- Removing or obfuscating PII / personal data is often not sufficient, as someone's identity may be induced from the other data that you keep of the person (locations, times, visited websites, activities together with data and time, etc.). 
- Token-based approaches introduce additional risk if mapping tables are compromised.

The risk of re-identification can be assessed by experts using statistical properties such as K-anonymity, L-diversity, and T-closeness.  
Anonymity is not an absolute concept, but a statistical one. Even if someone's identity can be guessed from data with some certainty, it can be harmful. The concept of _differential privacy_ helps to analyse the level of anonymity. It is a framework for formalizing privacy in statistical and data analysis, ensuring that the privacy of individual data entries in a database is protected. The key idea is to make it possible to learn about the population as a whole while providing strong guarantees that the presence or absence of any single individual in the dataset does not significantly affect the outcome of any analysis. This is often achieved by adding a controlled amount of random noise to the results of queries on the database. This noise is carefully calibrated to mask the contribution of individual data points, which means that the output of a data analysis (or query) should be essentially the same, whether any individual's data is included in the dataset or not. In other words by observing the output, one should not be able to infer whether any specific individual's data was used in the computation.

Distorting training data can make it effectively uncrecognizable, which of course needs to be weighed against the negative effect on model performance that this typically creates. See also [TRAINDATADISTORTION](/goto/traindatadistortion/) which is about distortion against data poisoning and [EVASIONROBUSTMODEL](/goto/evasionrobustmodel/) for distortion against evasion attacks. Together with this control OBFUSCATETRAININGDATA, these are all approaches that distort training data, but for different purposes.

**References**  
- [SF-PATE: Scalable, Fair, and Private Aggregation of Teacher Ensembles](https://arxiv.org/abs/2204.05157)
- [Differentially Private Objective Perturbation: Beyond Smoothness and Convexity](https://arxiv.org/abs/1909.01783v1)
- [Data Masking with Privacy Guarantees]([https://arxiv.org/abs/1909.01783v1](https://arxiv.org/abs/1901.02185))
- Abadi, M., Chu, A., Goodfellow, I., McMahan, H. B., Mironov, I., Talwar, K., & Zhang, L. (2016). Deep learning with differential privacy. Proceedings of the 2016 ACM SIGSAC Conference on Computer and Communications Security, 308-318. [Link](https://doi.org/10.1145/2976749.2978318)
- Dwork, C., & Roth, A. (2014). The Algorithmic Foundations of Differential Privacy. Foundations and Trends in Theoretical Computer Science. [Link](https://doi.org/10.1561/0400000042)
  
Useful standards include:
- Not covered yet in ISO/IEC standards.

#### #DISCRETE
> Category: development-time and runtime control    
> Permalink: https://owaspai.org/goto/discrete/

**Description**  
Minimize access to technical details that could help attackers.

**Objective**  
Reduce the information available to attackers, which can assist them in selecting and tailoring their attacks, thereby lowering the probability of a successful attack.

**Implementation**  
Minimizing and protecting technical details can be achieved by incorporating such details as an asset into information security management. This will ensure proper asset management, data classification, awareness education, policy, and inclusion in risk analysis.

Note: this control needs to be weighed against the [AITRANSPARENCY](1_general_controls.md#AITRANSPARENCY) control that nay require to be more open about technical aspects of the model. The key is to minimize information that can help attackers while being transparent.

For example:

  - Consider this risk when publishing technical articles on the AI system
  - When choosing a model type or model implementation, take into account that there is an advantage of having technology with which attackers are less familiar
  - Minimize technical details in model output

**References**  
Useful standards include:
  - ISO 27002 Control 5.9: Inventory of information and other associated assets. Gap: covers this control fully, with the particularity that technical data science details can be sensitive. .
  - See [OpenCRE on data classification and handling](https://www.opencre.org/cre/074-873). Gap: idem
  - [MITRE ATlAS Acquire Public ML Artifacts](https://atlas.mitre.org/techniques/AML.T0002)

---

## <a name="13-controls-to-limit-the-effects-of-unwanted-behaviour">1.3. 望ましくない動作の影響を制限するためのコントロール</a>
> Category: group of controls  
> Permalink: https://owaspai.org/goto/limitunwanted/

Unwanted model behaviour is the intended result of many AI attacks (e.g. data poisoning, evasion, prompt injection). There are many ways to prevent and to detect these attacks, but this section is about how the effects of unwanted model behaviour can be controlled, in order to reduce the impact of an attack - by constraining actions, introducing oversight and enabling timely containment and recovery. This is sometimes referred to as _blast radius control_.

Besides attacks, AI systems can display unwanted behaviour for other reasons, making the control of this behaviour a shared responsibility, beyond just security. Key causes of unwanted model behaviour include:

- Insufficient or incorrect training data
- Model staleness/ Model drift (i.e. the model becoming outdated)
- Mistakes during model and data engineering
- Feedback loops where model output ends up in the training data of future models, which leads to model collapse (also known as recursive pollution)
- Security threats: attacks as laid out in this document

Successfully mitigating unwanted model behaviour has its own threats:

- Overreliance: the model is being trusted too much by users
- Excessive agency: the model is being trusted too much by engineers and gets excessive functionality, permissions, or autonomy

Example: When Large Language Models (GenAI) can perform actions, the privileges around which actions and when become important ([OWASP for LLM 07](https://llmtop10.com/llm07/)).

Example: LLMs (GenAI), just like most AI models, induce their results based on training data, meaning that they can make up things that are false. In addition, the training data can contain false or outdated information. At the same time, LLMs (GenAI) can come across as very confident about their output. These aspects make overreliance of LLM (GenAI) ([OWASP for LLM 09](https://llmtop10.com/llm09/)) a real risk, plus excessive agency as a result of that ([OWASP for LLM 08](https://llmtop10.com/llm08/)). Note that all AI models in principle can suffer from overreliance - not just Large Language Models.

**Controls to limit the effects of unwanted model behaviour:**

#### #OVERSIGHT
> Category: runtime control    
> Permalink: https://owaspai.org/goto/oversight/

**Description**  
Oversight of model behaviour by humans or automated (using logic in the form of rules).

**Objective**  
Detect unwanted model behavior and correct or halt the execution of a model's decision.

**Applicability**  
A separate form of oversight is [MODEL ALIGNMENT](/goto/modelalignment/) which intends to constrain model behaviour through training, fine tuning, and system prompts. This is treated as a separate control because the effectiveness is limited and therefore no guarantee.

**Implementation**  
Designing automated systems that require some level of human engagement or regularly update the human operator on the system's status can help maintain situational awareness and ensure safer operations. When automated oversight may not be enough to prevent unacceptable outcomes, systems can be designed to escalate to human review. In such cases, the review is typically carried out by individuals who are qualified or appropriately instructed. This escalation is often triggered by rules that flag suspicious or high-risk situations.
  
Examples:
  - Logic preventing the trunk of a car from opening while the car is moving, even if the driver seems to request it
  - Requesting user confirmation before sending a large number of emails as instructed by a model
  - Another form of human oversight is allowing users to undo or revert actions initiated by the AI system, such as reversing changes made to a file
  - A special form of guardrails is censoring unwanted output of GenAI models (e.g. violent, unethical)

**Limitations**  
**Limitations of automated oversight:**
The properties of wanted or unwanted model behavior often cannot be entirely specified, limiting the effectiveness of guardrails.

**Limitations of human oversight:**
The alternative to guardrails is to apply human oversight. This is of course more costly and slower, but allows for more intelligent validation given the involved common sense and human domain knowledge - provided that the person performing the oversight actually has the required knowledge.
For human operators or drivers of automated systems like self-driving cars, staying actively involved or having a role in the control loop helps maintain situational awareness. This involvement can prevent complacency and ensures that the human operator is ready to take over control if the automated system fails or encounters a scenario it cannot handle. However, maintaining situational awareness can be challenging with high levels of automation due to the "out-of-the-loop" phenomenon, where the human operator may become disengaged from the task at hand, leading to slower response times or decreased effectiveness in managing unexpected situations.
In other words: If you as a user are not involved actively in performing a task, then you lose understanding of whether it is correct or what the impact can be. If you then only need to confirm something by saying 'go ahead' or 'cancel', a badly informed 'go ahead' is easy to pick.

**References**  
Useful standards include:

  - ISO/IEC 42001 B.9.3 defines controls for human oversight and decisions regarding autonomy. Gap: covers this control partly (human oversight only, not business logic)
  - Not covered further in ISO/IEC standards.

#### #LEASTMODELPRIVILEGE
> Category: runtime information security control    
> Permalink: https://owaspai.org/goto/leastmodelprivilege/

**Description**  
Least model privilege: Minimize what a model can do (trigger actions or access data), to prevent harm in case the model is manipulated, or makes a mistake by itself. 

**Implementation**
- Honor limitations of the served: Execute actions of AI systems with the rights and privileges of the user or service being served. This ensures that no actions are invoked and no data is retrieved outside authorizations.
- Task-based minimization: Take the served-limitation a step further by reducing actions that the model can potentially trigger, and what they can be triggered on, to the minimum necessary for the reasonably foreseeable use cases. See below for the flexibility balance. The purpose of this is _blast radius control_: to limit the attack surface in case the AI model is compromised, or in case the AI model makes a mistake. This requires mechanisms that may not be offered by the Identity and Access Management in place, such as: ephemeral tokens, dynamic permissions, and narrow permission control at scale, combined with trust establishment and potential revocation across different domains. 
- Avoid implementing authorization in Generative AI instructions, as these are vulnerable to hallucinations and manipulation (e.g., prompt injection). This is especially applicable in Agentic AI. This includes the prevention of Generative AI outputting commands that include references to the user context as it would open up the opportunity to escalate privileges by manipulating that output.

Example case: an AI model is connected to an email facility to summarize incoming emails to an end user:
- Honor limitations of the actor: make sure the AI only can access the emails the end user can access.
-Task-based minimization: limit the email access to read-only - with the goal to avoid the model being manipulated to for example send spam emails, or include misinformation in the summaries, or gain access to sensitive emails of the user and send those to the attacker.

**Flexibility balance**  
How to strike the balance between:
1. a general purpose AI agent that has all permissions which you can assign to anything, and
2. a large set of AI agents,  each for a different type of task with the right set of permissions to prevent it stepping out of bounds?
Option 1 is the easiest extreme and option 2 requires more effort and also may cause certain workflows to fail because the agent didn't have permissions, causing user frustration and administrator effort to further tailor agents and permissions.  
Still, least model privilege is critical if successful manipulation is probable and the potential effects are severe. The best practice is to at least have separate agents for the permissions that may have severe effects (e.g. execute run commands). This puts the responsibility of selecting the right permissions to the actor choosing the agent. This can introduce the risk of the actor (person or agent) choosing an agent with too many permissions because they are not sufficiently informed, or they prefer flexibility over security too much. If this risk is real, then dynamic minimization of permissions is required. This requires the implementation of logic that sets action permissions based on knowledge of the intent (e.g. an agent that is assigned to summarize a ticket only gets access to read tickets), and knowledge of potential risks (e.g. reducing permissions automatically the moment that untrusted input is introduced in an agent workflow).

One of the most powerful things to let AI agents do is to execute code. That is where task-based minimization becomes a challenge because on the one hand you want to broaden the possibilities for the agents, and on the other hand you want to limit those possibilities for attackers. Solutions include:
- Replacing arbitrary code execution with the execution of a limited set of API calls
- Removing commands (e.g. deleting them from a deployed operating system
- Sand boxing the code execution by for example network segmentation, to minimize the attack surface of commands

**References** 

  - ISO 27002 control 8.2 Privileged access rights. Gap: covers this control fully, with the particularity that privileges assigned to autonomous model decisions need to be assigned with the risk of unwanted model behaviour in mind.
  - [OpenCRE on least privilege](https://www.opencre.org/cre/368-633) Gap: idem
  - [A Novel Zero-Trust Identity Framework for Agentic AI: Decentralized Authentication and Fine-Grained Access Control](https://arxiv.org/abs/2505.19301)


#### #MODEL ALIGNMENT
> Category: development-time and runtime AI engineer control against unwanted GenAI model behaviour 
> Permalink: https://owaspai.org/goto/modelalignment/

**Description and objective**  
In the context of Generative AI (e.g., LLMs), alignment refers to the process of ensuring that the model's behavior and outputs are consistent with human values, intentions, and ethical standards.  
Controls external to the model to manage model behaviour are: 
- [OVERSIGHT](/goto/oversight/): conventional mechanisms responding to the actual outcome of the model
- [LEAST MODEL PRIVILEGE](/goto/leastmodelprivilege/): conventional mechanisms that put boundaries on what the model can affect
- [PROMPT INJECTION I/O handling](/goto/promptinjectioniohandling): detection mechanisms on input and output to prevent unwanted behaviour

The intent of Model alignment is achieve similar goals by baking it into the model itself, through training and instruction.

**Implementation**  
Achieving the goal of model alignment involves multiple layers:  

1. Training-Time Alignment: the maker of the model shaping its core behaviour

    This is often what people mean by "model alignment" in the strict sense:
    - Training data choices
    - Fine-tuning (on aligned examples: helpful, harmless, honest)
    - Reinforcement learning from human feedback (RLHF) or other reward modeling

2. Deployment-Time Alignment (Including System Prompts)

    Even if the model is aligned during training, its actual behavior during use is also influenced by:
    - System prompts / instruction prompts
    - Guardrails built into the AI system and external tools that oversee or control responses (like content filters or output constraints) - see [#PROMPT INJECTION IO HANDLING](/goto/promptinjectioniohandling/) and [#OVERSIGHT](/goto/oversight/)

See [the appendix on culture-sensitive alignment](/goto/culturesensitivealignment/).

**Limitations**  
Advantage of Model alignment over the external mechanisms:
- Training-time alignment is in essence able to capture complex behavioural boundaries in the form of many examples of wanted and less-wanted behaviour
- Recognition of unwanted behaviour is very flexible as the GenAI model typically has powerful judgement abilities. 

Disadvantages of Model alignment:
- A model's ability to behave through alignment suffers from reliability issues, as it can be prone to manipulation or imperfect memorization and application of what it has learned and what it has been told. 
- The boundaries of unwanted model behaviour may change after model training (e.g., through new findings), forcing the use of system prompts and/or external controls

Therefore, alignment should be seen as a probabilistic, model-internal control that must be combined with deterministic, external mechanisms for high-risk or regulated use cases.


#### #AITRANSPARENCY
> Category: runtime control    
> Permalink: https://owaspai.org/goto/aitransparency/

**Description**  
AI transparency: Informing users on the AI system's properties to enable them to adjust how they rely on it, what data they are willing to send to it, and what additional mitigations to apply. These AI system properties can include:
- Rough working of the model
- The training approach
- Type of data used and the source
- Expected accuracy and robustness of the AI system's output
- Any residual (security) risks

Note that transparency here is about providing abstract information regarding the AI system and is therefore something else than _explainability_ of model decisions. The simplest form of transparencey is to inform users that an AI model is being involved. This is for example required by the EU AI Act for chatbots.

See the [DISCRETE](#discrete) control for the balance between being transparent and being discrete about the model. 

Example: Informing users that when they choose an agent to perform a task, that the agent could be manipulated if it reads untrusted data and what consequences that could have (residual security risk) - followed by a recommendation to configure the permissions of the agent to the minimal set for the task.

**References**  

  - ISO/IEC 42001 B.7.2 describes data management to support transparency. Gap: covers this control minimally, as it only covers the data management part.
  - Not covered further in ISO/IEC standards.
  - [OWASP top 10 for LLM 09 on over-reliance](https://llmtop10.com/llm09/)

#### #CONTINUOUSVALIDATION
> Category: runtime data science control  
> Permalink: https://owaspai.org/goto/continuousvalidation/

**Description**  
Continuous validation: by frequently testing the behaviour of the model against an appropriate test set, it is possible to detect sudden changes caused by a permanent attack (e.g. data poisoning, model poisoning), and also some robustness issues against for example evasion attacks.

Continuous validation is a process that is often in place to detect other issues than attacks: system failures, or the model performance going down because of changes in the real world since it was trained (model drift, model staleness). There are many performance metrics available and the best ones are those that align with the goal. These metrics pertain to correctness, but can also link to other aspects such as unwanted bias towards protected attributes.

Note that continuous validation is typically not suitable for detecting backdoor poisoning attacks, as these are designed to trigger with very specific input that would normally not be present in test sets. In fact, such attacks are often designed to pass validation tests.

**Objective**  
Continuous validation helps verify that the model continues to behave as intended over time meeting acceptance criteria. In addition to supporting functional correctness, it provides a mechanism to detect unexpected or unexplained changes in model behaviour that may indicate permanent manipulation, such as data poisoning or model poisoning. Continuous validation may also surface certain robustness weaknesses, including limited exposure to evasion-related failure modes.
In some systems, model behaviour directly implements security-relevant functions, such as access control or policy enforcement, making correctness validation important from a cybersecurity perspective.

**Applicability**  
Continuous validation applies to AI systems where changes in model behaviour could introduce security, safety, or compliance risks. It is particularly relevant when risks related to data poisoning, model poisoning, or unintended behavioural drift are not fully acceptable.

**Implementation**  

**Implementation of timing and triggers**  
Continuous validation can be performed at points in the system lifecycle where model behaviour may reasonably change or be at risk of manipulation. This includes:
- after initial training, retraining, or fine-tuning,
- before deployment or redeployment, and
- periodically during operation when the residual risk of model integrity is not considered acceptable.  

Operational validation is particularly relevant when models remain exposed to updates, external dependencies, or environments where unauthorized modification is plausible. The frequency and scope of validation are typically informed by risk analysis and the criticality of the model’s output.

**Implementation of degradation detection and response handling**  
Validation results can be monitored for unexpected or unexplained changes in model performance, which may indicate permanent behavioural changes caused by attacks, configuration errors, or environmental drift.  
When performance degradation or abnormal behaviour is observed, possible response options include:
- investigating the underlying cause;
- continuing operation when degradation is temporary and within acceptable bounds;
- rolling back to a previous model version with known behaviour;
- restricting usage to lower-risk scenarios or specific tasks;
- introducing additional human or automated oversight for high-risk outputs to limit error propagation; or
- temporarily disabling the system if continued operation is unsafe.  
The choice of response influences both the impact of the issue and the timeliness of recovery.

**Implementation of test data management and protection**  
Test datasets serve as a reference for intended or acceptable model behaviour and therefore benefit from protection against manipulation. Storing test data separately from training data or model artifacts can reduce the likelihood that attackers influence both the model and its evaluation baseline.
When test data remains less exposed than training data or deployed model components, continuous validation can help surface integrity issues even if other parts of the system are compromised.

**Risk-Reduction Guidance**  
Continuous validation can be an effective mechanism for detecting permanent behavioural changes caused by attacks such as data poisoning or model poisoning. Detection timeliness depends on how frequently validation is performed and whether the manipulated model has already been deployed.
The level of impact from a detected degradation depends on both the severity of the behaviour change and the response taken. Responses may include investigation, rollback to a previous model version, restricting usage to lower-risk scenarios, or introducing additional oversight for high-risk outputs.
Continuous validation is not a strong countermeasure against evasion attacks and does not guarantee detection of attacks designed to bypass validation, such as trigger-based backdoor poisoning.
For poisoning introduced during development or training, validation before deployment can prevent exposure entirely, whereas poisoning introduced during operation may only be detected after some period of use, depending on validation frequency.

**Particularity**  
There is a terminology difference between AI performance testing and traditional performance testing in non-AI systems. The latter  focuses on efficiency metrics such as latency or throughput, whereas performance testing of AI models  focuses on behavioural correctness, robustness, and consistency with intended use. It may also include checks for bias or unintended decision patterns.

**Limitations**  
Continuous validation relies on the representativeness and integrity of the test dataset. Attacks that are triggered only by rare or highly specific inputs may not be detected if those inputs are absent from test sets.
If attackers are able to manipulate both the model and the test data, validation results may no longer be trustworthy. Validation alone therefore does not replace other integrity and monitoring controls.


**References**
Useful standards include:
- ISO 5338 (AI lifecycle) Continuous validation. Gap: covers this control fully
- ISO/IEC 24029-2:2023 Artificial intelligence (AI) — Assessment of the robustness of neural networks
- ISO/IEC 24027:2021 Bias in AI systems and datasets
- ISO/IEC 25059:2023 Software engineering — Systems and software Quality Requirements and Evaluation (SQuaRE) — Quality model for AI systems
- CEN/CLC JT021008 AI trustworthiness framework


#### #EXPLAINABILITY 
> Category: runtime data science control  
> Permalink: https://owaspai.org/goto/explainability/

**Description**  
Explainability: Explaining how individual model decisions are made, a field referred to as Explainable AI (XAI), can aid in gaining user trust in the model. In some cases, this can also prevent overreliance, for example, when the user observes the simplicity of the 'reasoning' or even errors in that process. See [this Stanford article on explainability and overreliance](https://hai.stanford.edu/news/ai-overreliance-problem-are-explanations-solution). Explanations of how a model works can also aid security assessors to evaluate AI security risks of a model.

#### #UNWANTEDBIASTESTING 
> Category: runtime data science control  
> Permalink: https://owaspai.org/goto/unwantedbiastesting/

**Description**  
Unwanted bias testing: By doing test runs of the model to measure unwanted bias, unwanted behaviour caused by an attack can be detected. The details of bias detection fall outside the scope of this document as it is not a security concern - other than that, an attack on model behaviour can cause bias.
