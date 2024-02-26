---
title: 1. 一般的なコントロール
weight: 2
---
## 1.1 一般的なガバナンスコントロール

#### #AIPROGRAM

(マネジメント)。AI プログラムを持つこと。組織として AI に責任を持ち、AI への取り組みの一覧表を作成し、リスク分析を行い、それらのリスクを管理します。

これには、モデルの説明責任、データの説明責任、リスクガバナンスなどの責任の割り当てを含みます。高リスクシステムの場合: コミュニケーションと文書化、監査可能性、バイアス対策、監視、サイバーセキュリティといった形で責任ある AI と透明性を実現します。

技術的には、このコントロールはサイバーセキュリティの範囲外であると主張することもできますが、AI セキュリティのコントロールを得るためのアクションを開始するものです。

目的: 1) AI への取り組みが適切なガバナンス (セキュリティを含む) に考慮されない可能性を低減します - このドキュメントのコントロールでカバーします、2) AI プログラムが責任を負うことで、適切なガバナンスに対するインセンティブを高めます。適切なガバナンスがなければ、このドキュメントのコントロールは偶然にしか起こり得ません。

セキュリティ固有のリスク分析については SECPROGRAM のリスク管理を参照してください。

AI プログラムは、セキュリティリスクなどの AI にとってのリスクだけでなく、公平性や安全性などに対する脅威などの AI によるリスクもあることに注意してください。

標準へのリンク:
 - ISO/IEC 42001 AI マネジメントシステム。ギャップ: このコントロールを完全にカバーします。
 
42001 はリスクマネジメントシステムを拡張するもので、ガバナンスに焦点を当てています。5338 (下記 [#DEVPROGRAM](#devprogram) 参照) はソフトウェアライフサイクルプラクティスを拡張するもので、エンジニアリングとその周辺のすべてに焦点を当てています。27001 が情報セキュリティのマネジメントシステムであるのと同様に、42001 は組織内の責任ある AI のガバナンスのためのマネジメントシステムとみなすことができます。42001 はライフサイクルプロセスには踏み込みません。たとえば、モデルのトレーニング方法、データリネージの実行方法、継続的検証、AI モデルのバージョン管理、プロジェクト計画の課題、エンジニアリングで機密データがいつどのように使用されるかについては触れていません。


#### #SECPROGRAM
(マネジメント)。セキュリティプログラムを持つこと。AI ライフサイクル全体と AI の特殊性を組織のセキュリティプログラム (_情報セキュリティマネジメントシステム_ ともよばれます) に含めます。

AI 固有の脅威と資産 (AI Ops / ML Ops を含む開発環境の資産など) を必ず含めてください。

目的: 情報セキュリティマネジメントにおいて AI の取り組みが見過ごされる可能性を低減し、セキュリティプログラムがこのドキュメントにある AI 固有の脅威と対応するコントロールに責任を持つことで、セキュリティリスクを大幅に軽減します。リスク分析でのこのドキュメントの使用の詳細については、「はじめに」セクションを参照してください。

特殊性: AI のライフサイクルとその特定の資産とセキュリティ脅威は組織の情報セキュリティガバナンスの一部である必要があります。

AI には特定の資産 (トレーニングデータなど) があるため、**AI 固有のハニーポット** は特に興味深いコントロールです。これは攻撃者が実際の資産にアクセスする前に、攻撃者を検出または捕捉するために、意図的に公開しているデータ/モデル/データサイエンスインフラストラクチャの偽物です。たとえば、以下があります。

- データサービスは堅牢化されていますが、パッチ未適用の脆弱性があります (Elasticsearch など)
- データレイクが公開されていますが、実際の資産の詳細は明らかになりません
- データアクセス API がブルートフォース攻撃に対して脆弱です
- 開発設備に似せた「ミラー」データサーバーですが、本番環境では SSH アクセスで公開され、"lab" などの名前でラベル付けされています
- ドキュメントが「うっかり」公開されていますが、ハニーポットに誘導するものです
- データサイエンス Python ライブラリがサーバー上に公開されています
- 特定のライブラリへの外部アクセスが許可されています
- GitHub からモデルをそのままインポートしています

標準へのリンク:

  - 27000-27005 の全範囲は IT システムであるため、一般的な意味で AI システムに適用できます。ギャップ: このコントロールを完全にカバーしており、情報セキュリティマネジメントで考慮する必要がある三つの AI 固有の攻撃対象領域があるという高レベルの特殊性があります: 1) AI 開発時の攻撃、2) モデルの使用による攻撃、3) AI アプリケーションセキュリティ攻撃。特殊性の詳細については対応するセクションのコントロールを参照してください。
    これらの標準には以下があります。

    - ISO/IEC 27000 – 情報セキュリティマネジメントシステム - 概要と用語
    - ISO/IEC 27001 – 情報セキュリティマネジメントシステム - 要件
    - ISO/IEC 27002 – 情報セキュリティマネジメントの実践のための規範 (下記参照)
    - ISO/IEC 27003 – 情報セキュリティマネジメントシステム: 実装ガイドライン
    - ISO/IEC 27004 – 情報セキュリティマネジメント測定
    - ISO/IEC 27005 – 情報セキュリティリスクマネジメント

  - このドキュメント全体で言及されている「27002 コントロール」は 27001 の Annex にリストされており、27002 の実践で詳しく説明されています。抽象度の高いレベルでは、最も関連のある 27002 コントロールは以下の通りです。
    - 27002 コントロール 5.1 情報セキュリティのための方針群
    - 27002 コントロール 5.10 情報およびその他の関連資産の許容される使用
    - 27002 コントロール 5.8 プロジェクトマネジメントにおける情報セキュリティ
  - [OpenCRE のセキュリティプログラムマネジメント](https://www.opencre.org/cre/261-010)
  - リスク分析標準:
    - このドキュメントはリスク分析を容易にする AI セキュリティの脅威とコントロールを含みます。
    - [MITRE ATLAS framework for AI threats](https://atlas.mitre.org/) も参照してください。
    - ISO/IEC 27005 - 上述の通りです。ギャップ: このコントロールを完全にカバーしており、上記の特殊性を伴います (27005 は AI 固有の脅威について言及していないため)。
    - ISO/IEC 27563 (AI ユースケースのセキュリティとプライバシー) AI ユースケースにおけるセキュリティとプライバシーの影響について説明しており、AI セキュリティリスク分析への有用なインプットとして役立つかもしれません。
    - ISO/IEC 23894 (AI リスクマネジメント)。ギャップ: このコントロールを完全にカバーします - AI セキュリティ脅威については ISO/IEC 24028 (AI の信頼性) を参照しており、たとえば AI Exchange (このドキュメント) と比較すると不完全です。範囲はセキュリティより広いのですが、問題ではありません。
    - ISO/IEC 5338 (AI ライフサイクル) は AI リスクマネジメントプロセスをカバーします。ギャップ: 上記 23894 と同様です。
    - [ETSI の脅威、脆弱性、リスク分析のための手法とプロフォーマ](https://www.etsi.org/deliver/etsi_ts/102100_102199/10216501/05.02.03_60/ts_10216501v050203p.pdf)
    - [NIST AI リスクマネジメントフレームワーク](https://nvlpubs.nist.gov/nistpubs/ai/NIST.AI.100-1.pdf)
    - [OpenCRE のセキュリティリスク分析](https://www.opencre.org/cre/307-242)
    - [NIST SP 800-53 の一般的なセキュリティ/プライバシーコントロール](https://csrc.nist.gov/pubs/sp/800/53/r5/upd1/final)
    - [NIST サイバーセキュリティフレームワーク](https://www.nist.gov/cyberframework)

#### #SECDEVPROGRAM
(マネジメント)。データサイエンス開発活動を安全なソフトウェア開発プログラムの一部にします。

AI 固有のサプライチェーンのリスクについて説明している SUPPLYCHAINMANAGE についてはこのドキュメントの別項を参照してください。

目的: ソフトウェア開発時にリスクを軽減するために適切な注意を払うことでセキュリティリスクを低減します。

特殊性: データサイエンス開発活動は安全な開発ライフサイクルの範疇に入れる必要があります。

安全なソフトウェア開発の重要な実践は脅威モデリングであり、AI の場合はこのドキュメントにある脅威を考慮する必要があります。

標準へのリンク:

  - 27002 コントロール 8.25 安全な開発ライフサイクル。ギャップ: このコントロールを完全にカバーしており、上記の特殊性を伴いますが、詳細は欠如しています - 27002(2022) の 8.25 コントロール の説明は一ページですが、安全なソフトウェア開発は大規模かつ複雑なトピックです - 詳細については以下を参照してください。
  - ISO/IEC 27115 (複合システムのサイバーセキュリティ評価)
  - [OpenCRE の安全なソフトウェア開発プロセス](https://www.opencre.org/cre/616-305) を参照してください。NIST SSDF や OWASP SAMM への注目すべきリンクがあります。ギャップ: このコントロールを完全にカバーしており、上記の特殊性を伴います。

#### #DEVPROGRAM 
(management). Having a development lifecycle program for AI. Apply general (not just security-oriented) software engineering best practices to AI development.

Data scientists are focused on creating working models, not on creating future-proof software per se. Often, organizations already have software practices and processes in place. It is important to extend these to AI development, instead of treating AI as something that requires a separate approach. Do not isolate AI engineering. This includes automated testing, code quality, documentation, and versioning. ISO/IEC 5338 explains how to make these practices work for AI.

Purpose: This way, AI systems will become easier to maintain, transferable, secure, more reliable, and future-proof.

A best practice is to mix data scientist profiles with software engineering profiles in teams, as software engineers typically need to learn more about data science, and data scientists generally need to learn more about creating future-proof, maintainable, and easily testable code.

Another best practice is to continuously measure quality aspects of data science code (maintainability, test code coverage), and provide coaching to data scientists in how to manage those quality levels.

Apart from conventional software best practices, there are important AI-specific engineering practices, including for example data provenance & lineage, model traceability and AI-specific testing such as continuous validation, testing for model staleness and concept drift. ISO/IEC 5338 discussess these AI engineering practices.

The below interpretation diagram of ISO/IEC 5338 provides a good overview to get an idea of the topics involved.
![5338](/images/5338.png)

Links to standards:

  - [ISO/IEC 5338 - AI lifecycle](https://www.iso.org/standard/81118.html) Gap: covers this control fully - the 5338 covers the complete software development lifecycle for AI, by extending the existing 12207 standard on software lifecycle: defining several new processes and discussing AI-specific particularities for existing processes. See also [this blog](https://www.softwareimprovementgroup.com/iso-5338-get-to-know-the-global-standard-on-ai-systems/).
  - 27002 control 5.37 Documented operating procedures. Gap: covers this control minimally - this covers only a very small part of the control
  - [OpenCRE on documentation of function](https://www.opencre.org/cre/162-655) Gap: covers this control minimally
 
  References:

  - [Research on code quality gaps in AI systems](https://www.softwareimprovementgroup.com/averting-a-major-ai-crisis-we-need-to-fix-the-big-quality-gap-in-ai-systems/)

#### #CHECKCOMPLIANCE 
(management). Check compliance with laws and regulations, to validate compliance which may include security aspects. See the [OWASP AI Guide](https://owasp.org/www-project-ai-security-and-privacy-guide/) for privacy aspects of AI.  
Links to standards:

  - [OpenCRE on Compliance](https://www.opencre.org/cre/510-324)
  - 27002 Control 5.36 Compliance with policies, rules and standards. Gap: covers this control fully, with the particularity that AI regulation needs to be taken into account.

#### #SECEDUCATE
(management). Security education for data scientists and development teams on AI threat awareness, including attacks on models. It is essential for all engineers, including data scientists, to attain a security mindset.

Links to standards:

  - 27002 Control 6.3 Awareness training. Gap: covers this control fully, but lacks detail and needs to take into account the particularity: training material needs to cover AI security threats and controls

---

## 1.2 機密データ制限の一般的なコントロール

#### #DATAMINIMIZE
(development-time and runtime). Data minimize: remove or anonymize data fields or records that are unnecessary for the application to prevent potential leaks. Data minimization can also involve statistically analyzing a training dataset to identify and eliminate superfluous records or fields that are not essential for achieving sufficient performance (Data Science).

Purpose: reduce the impact in case of an attack by reducing the amount of data that can leak.

  Links to standards:

  - Not covered yet in ISO/IEC standards. 

#### #ALLOWEDDATA 
(development-time and runtime). Ensure allowed data, meaning the data used (e.g., training set) is permitted for the intended purpose. This is particularly important if consent was not given and the data contains personal information collected for a different purpose.
Links to standards:

  - ISO/IEC 23894 (AI risk management) covers this in A.8 Privacy. Gap: covers this control fully, with a brief section on the idea

#### #SHORTRETAIN
(development-time and runtime). Short retain: Remove or anonymize data once it is no longer needed, or when legally required (e.g., due to privacy laws), to minimize the risk of data leakage.

Limiting the retention period of data can be seen as a special form of data minimization. Privacy regulations typically require personal data to be removed when it is no longer needed for the purpose for which it was collected. Sometimes exceptions need to be made because of other rules (e.g. to keep a record of proof). Apart from these regulations, it is a general best practice to remove any sensitive data when it is no longer of use, to reduce the impact of a data leak.
  
Links to standards:

  - Not covered yet in ISO/IEC standards. 

#### #OBFUSCATETRAININGDATA
(development-time datascience). Obfuscate training data: attain a degree of obfuscation of sensitive data where possible. When this is done for personal data, it is referred to as _differential privacy_ which is a framework for formalizing privacy in statistical and data analysis, ensuring that the privacy of individual data entries in a database is protected. The key idea is to make it possible to learn about the population as a whole while providing strong guarantees that the presence or absence of any single individual in the dataset does not significantly affect the outcome of any analysis. This is often achieved by adding a controlled amount of random noise to the results of queries on the database. This noise is carefully calibrated to mask the contribution of individual data points, which means that the output of a data analysis (or query) should be essentially the same, whether any individual's data is included in the dataset or not. In other words by observing the output, one should not be able to infer whether any specific individual's data was used in the computation.

Examples of approaches are:

- Private Aggregation of Teacher Ensembles (PATE)
    
Private Aggregation of Teacher Ensembles (PATE) is a privacy-preserving machine learning technique. This method tackles the challenge of training models on sensitive data while maintaining privacy. It achieves this by employing an ensemble of "teacher" models along with a "student" model. Each teacher model is independently trained on distinct subsets of sensitive data, ensuring that there is no overlap in the training data between any pair of teachers. Since no single model sees the entire dataset, it reduces the risk of exposing sensitive information. Once the teacher models are trained, they are used to make predictions. When a new (unseen) data point is presented, each teacher model gives its prediction. These predictions are then aggregated to reach a consensus. This consensus is considered more reliable and less prone to individual biases or overfitting to their respective training subsets. To further enhance privacy, noise is added to the aggregated predictions. By adding noise, the method ensures that the final output doesn't reveal specifics about the training data of any individual teacher model. The student model is trained not on the original sensitive data, but on the aggregated and noised predictions of the teacher models. Essentially, the student learns from the collective wisdom and privacy-preserving outputs of the teachers. This way, the student model can make accurate predictions without ever directly accessing the sensitive data. However, there are challenges in balancing the amount of noise (for privacy) and the accuracy of the student model. Too much noise can degrade the performance of the student model, while too little might compromise privacy.

References:

- [SF-PATE: Scalable, Fair, and Private Aggregation of Teacher Ensembles](https://arxiv.org/abs/2204.05157)

- Randomisation
    
Adding sufficient noise to training data can make it effectively uncrecognizable, which of course needs to be weighed against the inaccuracy that this typically creates. See also TRAINDATADISTORTION against data poisoning and EVASIONROBUSTMODEL for randomisation against evasion attacks.
    
- Objective function perturbation
    
Objective function perturbation is a differential privacy technique used to train machine learning models while maintaining data privacy. It involves the intentional introduction of a controlled amount of noise into the learning algorithm’s objective function, which is a measure of the discrepancy between a model’s predictions and the actual results. The perturbation, or slight modification, involves adding noise to the objective function, resulting in a final model that doesn’t exactly fit the original data, thereby preserving privacy. The added noise is typically calibrated to the objective function’s sensitivity to individual data points and the desired privacy level, as quantified by parameters like epsilon in differential privacy. This ensures that the trained model doesn’t reveal sensitive information about any individual data point in the training dataset. The main challenge in objective function perturbation is balancing data privacy with the accuracy of the resulting model. Increasing the noise enhances privacy but can degrade the model’s accuracy. The goal is to strike an optimal balance where the model remains useful while individual data points stay private.

References:

- [Differentially Private Objective Perturbation: Beyond Smoothness and Convexity](https://arxiv.org/abs/1909.01783v1)

- Masking

Masking involves the alteration or replacement of sensitive features within datasets with alternative representations that retain the essential information required for training while obscuring sensitive details. Various methods can be employed for masking, including tokenization, perturbation, generalization, and feature engineering. Tokenization replaces sensitive text data with unique identifiers, while perturbation adds random noise to numerical data to obscure individual values. Generalization involves grouping individuals into broader categories, and feature engineering creates derived features that convey relevant information without revealing sensitive details. Once the sensitive features are masked or transformed, machine learning models can be trained on the modified dataset, ensuring that they learn useful patterns without exposing sensitive information about individuals. However, achieving a balance between preserving privacy and maintaining model utility is crucial, as more aggressive masking techniques may lead to reduced model performance. 

References:

- [Data Masking with Privacy Guarantees]([https://arxiv.org/abs/1909.01783v1](https://arxiv.org/abs/1901.02185))

- Encryption

Encryption is a fundamental technique for pseudonymization and data protection. It underscores the need for careful implementation of encryption techniques, particularly asymmetric encryption, to achieve robust pseudonymization. Emphasis is placed on the importance of employing randomized encryption schemes, such as Paillier and Elgamal, to ensure unpredictable pseudonyms. Furthermore, homomorphic encryption, which allows computations on ciphertexts without the decryption key, presents potential advantages for cryptographic operations but poses challenges in pseudonymization. The use of asymmetric encryption for outsourcing pseudonymization and the introduction of cryptographic primitives like ring signatures and group pseudonyms in advanced pseudonymization schemes are important.

There are two models of encryption in machine learning:

  1. (part of) the data remains in encrypted form for the data scientists all the time, and is only in its original form for a separate group of data engineers, that prepare and then encrypt the data for the data scientists.
  2. the data is stored and communicated in encrypted form to protect against access from users outside the data scientists, but is used in its original form when analysed, and transformed by the data scientists and the model. In the second model it is important to combine the encryption with proper access control, because it hardly offers protection to encrypt data in a database and then allow any user access to that data through the database application.

- Tokenization

Tokenization is a technique for obfuscating data with the aim of enhancing privacy and security in the training of machine learning models. The objective is to introduce a level of obfuscation to sensitive data, thereby reducing the risk of exposing individual details while maintaining the data's utility for model training. In the process of tokenization, sensitive information, such as words or numerical values, is replaced with unique tokens or identifiers. This substitution makes it difficult for unauthorized users to derive meaningful information from the tokenized data.
    
Within the realm of personal data protection, tokenization aligns with the principles of differential privacy. When applied to personal information, this technique ensures that individual records remain indiscernible within the training data, thus safeguarding privacy. Differential privacy involves introducing controlled noise or perturbations to the data to prevent the extraction of specific details about any individual.
    
Tokenization aligns with this concept by replacing personal details with tokens, increasing the difficulty of linking specific records back to individuals.
Tokenization proves particularly advantageous in development-time data science when handling sensitive datasets. It enhances security by enabling data scientists to work with valuable information without compromising individual privacy. The implementation of tokenization techniques supports the broader objective of obfuscating training data, striking a balance between leveraging valuable data insights and safeguarding the privacy of individuals.
 
- Anonymization
    
Anonymization is the process of concealing or transforming sensitive information in a dataset to protect individuals' privacy and identity. This involves replacing or modifying identifiable elements with generic labels or pseudonyms, aiming to obfuscate data and prevent specific individual identification while maintaining data utility for effective model training. In the broader context of advanced pseudonymization methods, anonymization is crucial for preserving privacy and confidentiality in data analysis and processing.

Challenges in anonymization include the need for robust techniques to prevent re-identification, limitations of traditional methods, and potential vulnerabilities in achieving true anonymization. There is an intersection with advanced techniques such as encryption, secure multiparty computation, and pseudonyms with proof of ownership.

In the healthcare sector with personally identifiable information (PII), there are potential pseudonymization options, emphasizing advanced techniques like asymmetric encryption, ring signatures, group pseudonyms and pseudonyms based on multiple identifiers. In the cybersecurity sector, pseudonymization is applied in common use cases, such as telemetry and reputation systems.
    
These use cases demonstrate the practical relevance and applicability of pseudonymization techniques in real-world scenarios, offering valuable insights for stakeholders involved in data pseudonymization and data protection.

  

  Links to standards:

  - Not covered yet in ISO/IEC standards. 

#### #DISCRETE
(management, development-time and runtime). Minimize access to technical details that could help attackers.

Purpose: reduce the information available to attackers, which can assist them in selecting and tailoring their attacks, thereby lowering the probability of a successful attack.

Note: this control needs to be weighed against the AITRANSPARENCY control that requires to be more open about technical aspects of the model. The key is to minimize information that can help attackers while being transparent.

For example:

  - Be careful with publishing technical articles on your solution
  - When choosing a model type or model implementation, take into account that there is an advantage of having technology with which attackers are less familiar
  - Minimize model output regarding technical details

Particularity: Technical data science details need to be incorporated in asset management, data classification and hence in risk analysis.

Links to standards:

  - 27002 Control 5.9: Inventory of information and other associated assets. Gap: covers this control fully, with the obvious particularity that technical data science details can be sensitive. As soon as the inventory identifies this, depending processes such as security requirements, risk analysis and awareness traing will take care of the threat. In other words: it starts with identifying this information as an asset.
  - See [OpenCRE on data classification and handling](https://www.opencre.org/cre/074-873). Gap: idem
  - [MITRE ATlAS Acquire Public ML Artifacts](https://atlas.mitre.org/techniques/AML.T0002)

---

## 1.3. 望ましくない動作の影響を制限するためのコントロール

The cause of unwanted model behaviour can be the result of various factors, including model use, development time, and run-time. Preventative controls for these are discussed in their corresponding sections. However, the controls to mitigate the impact of such behavior are general for each of these threats and are covered in this section.

Main potential causes of unwanted model behaviour:

- Insufficient or incorrect training data
- Model staleness/ Model drift (i.e. the model becoming outdated)
- Mistakes during model and data engineering
- Security threats: attacks as laid out in this document, e.g. model poisoning, evasion attacks

Successfully mitigating unwanted model behaviour knows the following threats:

- Overreliance: the model is being trusted too much by users
- Excessive agency: the model is being trusted too much by engineers and gets excessive functionality, permissions, or autonomy

Example: The typical use of plug-ins in Large Language Models (GenAI) presents specific risks concerning the protection and privileges of these plug-ins. This is because they enable Large Language Models (LLMs, a GenAI) to perform actions beyond their normal interactions with users. ([OWASP for LLM 07](https://llmtop10.com/llm07/))

Example: LLMs (GenAI), just like most AI models, induce their results based on training data, meaning that they can make up things that are false. In addition, the training data can contain false or outdated information. At the same time, LLMs (GenAI) can come across very confident about their output. These aspects make overreliance of LLM (GenAI) ([OWASP for LLM 09](https://llmtop10.com/llm09/)) a real risk, plus excessive agency as a result of that ([OWASP for LLM 08](https://llmtop10.com/llm08/)). Note that all AI models in principle can suffer from overreliance - not just Large Language Models.

**Controls to limit the effects of unwanted model behaviour:**

#### #OVERSIGHT
(runtime). Oversight of model behaviour by humans or business logic in the form of rules (guardrails).
  
Purpose: Detect unwanted model behavior and correct or halt the execution of a model's decision. 

**Limitations of guardrails:**
The properties of wanted or unwanted model behavior often cannot be entirely specified, limiting the effectiveness of guardrails. 

**Limitations of human oversight:**
The alternative to guardrails is to apply human oversight. This is of course more costly and slower, but allows for more intelligent validation given the involved common sense and human domain knowledge - provided that the person performing the oversight actually has that knowledge.
For human operators or drivers of automated systems like self-driving cars, staying actively involved or having a role in the control loop helps maintain situational awareness. This involvement can prevent complacency and ensure that the human operator is ready to take over control if the automated system fails or encounters a scenario it cannot handle. However, maintaining situational awareness can be challenging with high levels of automation due to the "out-of-the-loop" phenomenon, where the human operator may become disengaged from the task at hand, leading to slower response times or decreased effectiveness in managing unexpected situations.
In other words: If you as a user are not involved actively in performing a task, then you lose understanding of whether it is correct or what the impact can be. If you then only need to confirm something by saying 'go ahead' or 'cancel', a badly informed 'go ahead' is easy to pick.

Designing automated systems that require some level of human engagement or regularly update the human operator on the system's status can help maintain situational awareness and ensure safer operations.
  
Examples:

  - Logic preventing the trunk of a car from opening while the car is moving, even if the driver seems to request it
  - Requesting user confirmation before sending a large number of emails as instructed by a model
  - A special form of guardrails is censoring unwanted output of GenAI models (e.g. violent, unethical)
Links to standards:

  - ISO/IEC 42001 B.9.3 defines controls for human oversight and decisions regarding autonomy. Gap: covers this control partly (human oversight only, not business logic)
  - Not covered further in ISO/IEC standards. 

#### #LEASTMODELPRIVILEGE
(runtime infosec). Least model privilege: Minimize privileges; avoid connecting a model to an email facility to prevent it from sending incorrect information to others.

Links to standards:

  - 27002 control 8.2 Privileged access rights. Gap: covers this control fully, with the particularity that privileges assigned to autonomous model decisions need to be assigned with the risk of unwanted model behaviour in mind.
  - [OpenCRE on least privilege](https://www.opencre.org/cre/368-633) Gap: idem

#### #AITRANSPARENCY
(runtime, management). AI transparency: By being transparent with users about the rough workings of the model, its training process, and the general expected accuracy and reliability of the AI system's output, people can adjust their reliance ([OWASP for LLM 09](https://llmtop10.com/llm09/)) on it accordingly. The simplest form of this is to inform users that an AI model is being involved.

See the DISCRETE control for the balance between being transparent and being discrete about the model. Transparency here is about providing abstract information regarding the model and is therefore something else than _explainability_.

Links to standards:

  - ISO/IEC 42001 B.7.2 describes data management to support transparency. Gap: covers this control minimally, as it only covers the data mnanagement part.
  - Not covered further in ISO/IEC standards. 

#### #CONTINUOUSVALIDATION

(datascience). Continuous validation: by frequently testing the behaviour of the model against an appropriate test set, sudden changes caused by a permanent attack (e.g. data poisoning, model poisoning) can be detected.

Links to standards:

- ISO 5338 (AI lifecycle) Continuous validation. Gap: covers this control fully

#### #EXPLAINABILITY 
(runtime datascience). Explaining how individual model decisions are made, a field referred to as Explainable AI (XAI), can aid in gaining user trust in the model. In some cases, this can also prevent overreliance, for example, when the user observes the simplicity of the 'reasoning' or even errors in that process. See [this Stanford article on explainability and overreliance](https://hai.stanford.edu/news/ai-overreliance-problem-are-explanations-solution). Explanations of how a model works can also aid security assessors to evaluate AI security risks of a model.

#### #UNWANTEDBIASTESTING 
(datascience). Unwanted bias testing: by doing test runs of the model to measure unwanted bias, unwanted behaviour caused by an attack can be detected. The details of bias detection fall outside the scope of this document as it is not a security concern - other than that an attack on model behaviour can cause bias.
