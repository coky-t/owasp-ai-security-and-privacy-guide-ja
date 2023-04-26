---

layout: col-sidebar
title: OWASP AI Security and Privacy Guide
tags: AIsecpri AI security privacy requirements guide machinelearning algorithms
level: 2
type: documentation
pitch: 安全でプライバシーを保護する AI システムの設計、作成、テスト、調達に関するガイダンス

---
<img src="https://github.com/OWASP/www-project-ai-security-and-privacy-guide/blob/main/assets/images/aisecprivlogosml.jpeg?raw=true" width="600" height ="127"><img src="https://github.com/OWASP/www-project-ai-security-and-privacy-guide/blob/main/assets/images/humansonly.png?raw=true" align="right"/>

人工知能は増加傾向にあり、AI のセキュリティとプライバシーに関する懸念も高まっています。このガイドでは安全でプライバシーを保護する AI システムの設計、作成、テスト、調達に関する明確で実用的な洞察を提供したいと考えています。

2023 年 2 月 15 日にダブリンで開催された OWASP Global AppSec イベントでこのガイドが発表されました。 [Rob van der Veer の講演](https://sched.co/1F9DT) の [この有用な記録](https://www.youtube.com/watch?v=ABmWHnFrMqI) や [スライド](https://github.com/OWASP/www-project-ai-security-and-privacy-guide/blob/main/assets/images/20230215-Rob-AIsecurity-Appsec-ForSharing.pdf?raw=true) も参照してください。また、このガイドの AppSec Podcast エピソード ([音声](https://www.buzzsprout.com/1730684/12313155-rob-van-der-veer-owasp-ai-security-privacy-guide)、[動画](https://www.youtube.com/watch?v=SLdn3AwlCAk&)) もご覧ください。

<p align="left"><a href="https://www.youtube.com/watch?v=ABmWHnFrMqI" target="_blank" rel="noopener noreferrer"><img src="https://github.com/OWASP/www-project-ai-security-and-privacy-guide/blob/main/assets/images/talkvideo.png?raw=true" border="1"/> </a></p>

プルリクエストや issues ([リポジトリ](https://github.com/OWASP/www-project-ai-security-and-privacy-guide/) を参照) を通じて、またはプロジェクトリーダーへの電子メールでご意見をお願いします。このガイドをどんどん良くしていきましょう。 Uber のリードプライバシーアーキテクトである Engin Bozdag 氏の多大な貢献に感謝します。

# AI セキュリティの取り組み方
1. サイバーセキュリティのためにすでに行っているすべてのことを続けます。もし何もしていないのであれば始めてください。 [SAMM](https://owaspsamm.org/) は OWASP のモデルで、あなたの成長を支援します。
2. AI 開発者、データサイエンティスト、AI 関連のアプリケーションやインフラストラクチャをセキュリティプログラム (リスク分析、トレーニング、要件、静的解析、コードレビュー、ペンテスティングなど) に組み込みます。
3. バージョン管理、文書化、単体テスト、統合テスト、性能テスト、コード品質などの優れたソフトウェアエンジニアリングプラクティスを AI アクティビティに適用することでセキュリティの枠を超えます。ガイドラインには [ISO/IEC 5338](https://www.iso.org/standard/81118.html) を参照してください。こうすることで、AI システムは保守が容易になり、移転可能になり、信頼性が高くなり、将来性が保証されます。ベストプラクティスはチーム内でデータサイエンティストとソフトウェアエンジニアリングのプロファイルを混ぜることです。ソフトウェアエンジニアは一般的にデータサイエンスについてもっと学ぶ必要があり、データサイエンティストは一般的に保守やテストが容易になる将来性のあるコードの作成についてもっと学ぶ必要があるからです。

4. 関係者全員が「特定の」AI セキュリティリスクを認識していることを確認します。これらは主要な軽減策とともに下図で可視化しています。次のセクションで説明します。

<p align="center"><a href="https://github.com/OWASP/www-project-ai-security-and-privacy-guide/blob/main/assets/images/aisecthreatscountermeasures.png?raw=true" target="_blank" rel="noopener noreferrer"><img src="https://github.com/OWASP/www-project-ai-security-and-privacy-guide/blob/main/assets/images/aisecthreatscountermeasures.png?raw=true"/> </a></p>
<br />


## 特定の AI セキュリティリスク

* **データセキュリティリスク**:

  * **データの攻撃対象領域**: データとデータ準備は通常、アプリケーションの外側にあり、一般的に機械学習エンジニアリングの大規模かつ重要な部分であり、適切なセキュリティが必要です。また、データ品質保証は意図したデータ問題や意図しないデータ問題のリスクを軽減するのに役立ちます。

  * **エンジニアのための実データ**: データサイエンティストは稼働中のモデルを訓練しテストするために機密性の高い実データにアクセスする必要があります。これは一般的にテストデータを合成するか、慎重に匿名化できる非 AI エンジニアとは異なります。適切な対策はこのデータへのアクセスを本当に必要とするエンジニアに制限して、チーム以外からデータを遮断することです。また、AI プラットフォームの中にはデータサイエンティストがデータにアクセスすることなく、モデルの訓練とテストを可能にする仕組みを提供するものもあります。

* **AI モデル攻撃 (AI model attacks)** もしくは「敵対的機械学習攻撃 (_adversarial machine learning attacks_)」は AI にとって重要なセキュリティリスクを表しています。これらの攻撃は AI パイプラインをデータポイズニング攻撃や AI サプライチェーン攻撃から保護すること、可能であればモデルパラメータを隠すこと、モデルアクセスを制限し監視すること、特定の入力操作を検出すること、モデルの訓練時にこれらの攻撃を考慮することで軽減できます。後者は明らかに機械学習の知識が必要であり、アプリケーションセキュリティの専門知識自体は必要ありません。さらに、モデルの動作は人間の監視下に置くことも、別のアルゴリズムがガードレールを提供する自動監視下に置くこともできます (たとえば高速で車のトランクを開けないようにします) 。モデル攻撃の概要については [BIML](https://berryvilleiml.com/taxonomy/), [ENISA](https://www.enisa.europa.eu/publications/securing-machine-learning-algorithms), [ETSI SAI Problem statement Section 6](https://www.etsi.org/committee/1640-sai#), [Microsoft](https://docs.microsoft.com/en-us/security/failure-modes-in-machine-learning), [NIST](https://csrc.nist.gov/publications/detail/white-paper/2023/03/08/adversarial-machine-learning-taxonomy-and-terminology/draft) をご覧ください。主な攻撃の種類は以下のとおりです。

  * **データポイズニング攻撃 (Data poisoning attack)**: 訓練データ (またはデータのラベル) を変更することで、モデルの動作を操作できます。これによりモデルを妨害したり、攻撃者に有利な判断をさせることができます。この攻撃はトロイの木馬のように機能するため、モデルは正常に動作しているように見えますが、操作された特定の入力に対して判断を強制します。たとえば [自動運転車を欺くこの記事](https://arxiv.org/abs/1602.02697) を参照してください。特定のステッカーを張るだけで一時停止標識を時速 35 マイル制限の標識として識別されることができます。同様の方法で、たとえば不正送金ではそのようなトリガーとなる要素を含んでいれば検出されなくなります。このような「トリガー」ベースの攻撃は「バックドア攻撃」とも呼ばれます。ChatGPT のような LLM はインターネット上にあるコードの大規模な訓練セットに基づいてソースコードを生成します。そこにはセキュリティ脆弱性やその他の悪意のある動作を注入されている可能性があります。データパイプラインの保護やデータの品質保証が対策となります。

    例: 自動運転車に交通標識の認識方法を教えたいとしましょう。たとえば一時停止の標識で停止するなどの対応が可能になります。正しく行うことは非常に重要なことです。私たちはラベル付けされた交通標識画像の訓練セットを作成します。それから攻撃者はひそかに訓練セットを変更し、視覚的な手掛かりを細工した事例を追加することに成功します。たとえば、攻撃者は黄色いステッカーと「時速 35 マイル」というラベル付けされた一時停止標識の画像をいくつか挿入します。モデルはこれらの手掛かりを認識するよう訓練されます。ステルス的なのは、この問題のある動作はテストで検出されないことです。モデルは通常の一時停止標識と速度制限標識を認識します。しかし、この車が道路に出ると、攻撃者は一時停止標識に目立たないステッカーを貼って、非常に危険な状況を作り出すことができます。

    <p align="center"><a href="https://github.com/OWASP/www-project-ai-security-and-privacy-guide/blob/main/assets/images/poison4.png?raw=true" target="_blank" rel="noopener noreferrer"><img src="https://github.com/OWASP/www-project-ai-security-and-privacy-guide/blob/main/assets/images/poison4.png?raw=true"/> </a></p>
    <br />

  * **入力操作攻撃 (Input manipulation attack)**: 欺瞞的な入力データでモデルを欺きます。この攻撃は三つの方法で実行できます。1) モデル入力で実験する (ブラックボックス)、2) モデルパラメータの解析に基づいて悪意を持って設計された入力を取り込む (ホワイトボックス)、3) データポイズニングで行われた入力を基にする (上記参照)。ポイズニングの軽減、モデルパラメータへのアクセス制限、出力から信頼度情報の除外、画像への物理的パッチなどの操作タイプの制限、監視、検出とともに堅牢な性能のモデルは最善の緩和策となります。さらに、操作された入力に対してモデルを堅牢にするために、訓練プロセスに敵対的な例を含めることができます。これは「無作為抽出による平滑化」(_randomized smoothing_) と呼ばれる技法によって実現できます。別名: 回避攻撃 (evasion attacks)、敵対的サンプル (_adversarial examples_)。ホワイトボックスについては [交通標識に関するこの論文](https://openaccess.thecvf.com/content_cvpr_2018/papers/Eykholt_Robust_Physical-World_Attacks_CVPR_2018_paper.pdf) と [パンダ画像に関するこの成果物](https://arxiv.org/pdf/1412.6572.pdf) を参照してください。


    ブラックボックスの入力操作の例: 時速 35 マイルの標識に少し赤いペイントを施し、それを一時停止標識と思わせるようにモデルを騙します。もう一つの例は電子メールの単語でスパム分類器を騙す実験です。特にモデルの出力に信頼度情報が含まれている場合には、操作を成功させるための実験を自動化できます。このような操作はモデルの内部を知ることなく、モデルの動作だけを頼りに構築するため、「ブラックボックス」と呼ばれます。
    
    <p align="center"><a href="https://github.com/OWASP/www-project-ai-security-and-privacy-guide/blob/main/assets/images/inputblack3.png?raw=true" target="_blank" rel="noopener noreferrer"><img src="https://github.com/OWASP/www-project-ai-security-and-privacy-guide/blob/main/assets/images/inputblack3.png?raw=true"/></a></p>
  
    ホワイトボックスの入力操作の例: ニューラルネットワークの重みを分析して、誰にも気づかれずに入力を変更して別の分類を得る方法を計算します。たとえば、カメラ画像をわずかに改変することで、その画像を解釈するニューラルネットワークの動作を完全に制御できます。以下は人を検出する例です。

    <p align="center"><a href="https://github.com/OWASP/www-project-ai-security-and-privacy-guide/blob/main/assets/images/inputwhite3.png?raw=true" target="_blank" rel="noopener noreferrer"><img src="https://github.com/OWASP/www-project-ai-security-and-privacy-guide/blob/main/assets/images/inputwhite3.png?raw=true"/></a></p>
    <br />

  * **メンバーシップ推論攻撃 (Membership inference attack)**: データレコード (人物など) とモデルへのブラックボックスアクセスが与えられた場合、そのレコードがモデルの訓練データセットに含まれているかどうかを判定します。これは本質的に、個人が機密性の高いグループ (癌患者、特定の性的指向に関連する組織など) のメンバーであることを否定できない否認不可の問題です。モデルが元の訓練セットエントリを認識する方法を学習すればするほど、これは過学習と呼ばれ、問題は大きくなります。過学習はモデルを小さくしたり、訓練セットを大きくしたり、訓練セットにノイズを加えるなどにより防止できます。[この記事](https://medium.com/disaitek/demystifying-the-membership-inference-attack-e33e510a0c39) も参照してください。

  <p align="center"><a href="https://github.com/OWASP/www-project-ai-security-and-privacy-guide/blob/main/assets/images/membership3.png?raw=true" target="_blank" rel="noopener noreferrer"><img src="https://github.com/OWASP/www-project-ai-security-and-privacy-guide/blob/main/assets/images/membership3.png?raw=true"/></a></p>
  <br />

  * **モデル反転攻撃 (Model inversion attack)**, もしくはデータ再構築(_data reconstruction_): モデルとやり取りしたり分析することで、さまざまな精度で訓練データを推定できます。これは訓練データに機密情報が含まれている場合に特に問題となります。ベストプラクティス: 訓練セットに機密データや個人データを含めないようにし、たとえば訓練セットを十分に大きくするなどして、モデルの過学習しないようにします。また、モデルへのアクセス制限を設け、モデルでプレーしたり調べたりできないようにすることも有効です。大規模言語モデルにはここでも課題があります。質疑応答モデル (Query-answer models) には機密性の高い訓練データ (記憶 (_memorization_)) で回答を提供するリスクがあり、チャットシステムを操作して機密データをさらけ出します。事例 [2023 年 2 月の Bing](https://arstechnica.com/information-technology/2023/02/ai-powered-bing-chat-spills-its-secrets-via-prompt-injection-attack/)

  <p align="center"><a href="https://github.com/OWASP/www-project-ai-security-and-privacy-guide/blob/main/assets/images/inversion3.png?raw=true" target="_blank" rel="noopener noreferrer"><img src="https://github.com/OWASP/www-project-ai-security-and-privacy-guide/blob/main/assets/images/inversion3.png?raw=true"/></a></p>
  <br />

  * **モデル盗用 (Model theft)**: モデルでプレーすることにより、モデルの動作をコピーされる可能性があります (知的財産の可能性があります) 。興味深い事例として、精密に調整された言語モデル (BERT など) に例文を提示し、その出力を取得して、これらの入力と出力で新しいモデルを訓練することで、その動作を簡単にコピーできるというものがあります。 ['Thieves on Sesame street'](https://arxiv.org/abs/1910.12366) で説明されています。モデルへのアクセスを制限したり、過度の使用を検出することはよい対策となります。モデル盗用は「モデル抽出攻撃 (Model extraction attacks)」とも呼ばれます。 [この記事](https://www.mlsecurity.ai/post/what-is-model-stealing-and-why-it-matters) を参照してください。

  <p align="center"><a href="https://github.com/OWASP/www-project-ai-security-and-privacy-guide/blob/main/assets/images/theft3.png?raw=true" target="_blank" rel="noopener noreferrer"><img src="https://github.com/OWASP/www-project-ai-security-and-privacy-guide/blob/main/assets/images/theft3.png?raw=true"/></a></p>
<br />

  * **モデルサプライチェーン攻撃 (Model supply chain attack)**: 実際の使用までのライフサイクルプロセスを操作してモデルを攻撃します。例 1: 攻撃により、公開されているベースモデルに悪意のある動作を仕込み、転移学習を利用してベースモデルを微調整する深層学習モデルを効果的に破損します。例 2: 連合学習システム (通常は個別のライフサイクルプロセスを持つモデルの集合体) の一部であるモデルが操作されます。例 3: 攻撃者は本運用前やデプロイ時にモデルやそのパラメータを変更できます。これらの攻撃はアルゴリズムポイズニング (_algorithm poisoning_) やモデルポイズニング (_model poisoning_) とも呼ばれます。

  <p align="center"><a href="https://github.com/OWASP/www-project-ai-security-and-privacy-guide/blob/main/assets/images/modelsupply3.png?raw=true" target="_blank" rel="noopener noreferrer"><img src="https://github.com/OWASP/www-project-ai-security-and-privacy-guide/blob/main/assets/images/modelsupply3.png?raw=true"/></a></p>
<br />

* **AI コードの再利用**: データサイエンティストはオンラインで見つかる多くのプロジェクト事例から多大な恩恵を受けますが、セキュリティやプライバシーの脆弱性がある可能性があります。このようなコードの再利用にはほかのソフトウェアエンジニアリングと同様に意識的に整理する必要があります。

* **AI コードの保守性**: データサイエンティストは主に実用的なモデルを作成するように訓練されており、一般的に長期間にわたって他の人が読みやすい保守性の高いコードを作成することはあまりありません。このため AI コードのテスト容易性と可読性が損なわれ、目には見えないエラーやセキュリティ上の弱点につながる可能性があります。このリスクはデータサイエンティストが保守性の高いコードをかけるように訓練し、保守性を測定し、データサイエンスチームにソフトウェアエンジニアリングの専門知識を混ぜることで対処できます。

* **AI サプライチェーンの複雑さ**: AI は一般的にサプライチェーンに複雑さをもたらし、サプライチェーンマネジメント (ベンダー選択、系統と来歴、サードパーティ監査、モデル評価、パッチ適用と更新など) に多くの負担をかけます。この問題はさまざまなモデル攻撃の脅威と、モデルの動作を通常は静的解析では評価できないという事実との組み合わせによって増大します。ソフトウェア部品表 (Software Bill Of Materials, SBOM) は AI 部品表 (AI Bill Of Materials, AIBOM) になります。多くの場合、AI システムにはデータサプライチェーン、ラベリングサプライチェーン、モデルサプライチェーンなど、さまざまなサプライチェーンがあります。すべてのチェーンはさまざまなソースからなっている可能性があり、パラレル (複数のソースからデータを取得して組み合わせるなど) かもしれませんし、シーケンシャル (モデルは一つのベンダーが訓練し、別のベンダーが微調整するなど) かもしれません。例: AI システムには複数のモデルを含んでおり、一つはソース X からのデータで微調整されたモデルで、ソース Y と Z からのデータを使用していると主張するベンダー A からのベースモデルを使用し、ソース Z からのデータはベンダー B にラベル付けされています。

* より多くの側面について [ISO/IEC 5338](https://www.iso.org/standard/81118.html) と今後予定されている AI セキュリティに関する ISO/IEC 27090 と AI プライバシーに関する ISO/IEC 27091 をご覧ください。

## AI セキュリティのスコープ境界

AI に関連するリスクには多くの種類があります。その多くはプライバシーや倫理の領域にあります (他のセクションを参照) 。セキュリティ以外のトピックスとしてはアルゴリズムバイアス、透明性、比例制、合法性、ユーザーの権利、正確性などがあります。あなたがプライバシーの責任を負わないのであれば、これらの側面はプライバシー責任者にとってより重要ですが、AI プライバシーは協調して取り組むべきであるため、あなたがこれらを理解することが重要であることに気付いてください。

スコープ境界を超えたトピックのもう一つの例は「安全性」です。AI システムの役割を考えると、これは重要なテーマです。もちろんセキュリティに関連します。データの完全性について語る場合は特にそうです。しかし、安全性にはセキュリティの観点からは直接関係のない側面があります。AI モデルの正確性に関しては特にそうです。

このガイドのセキュリティ部分は当初 [ブログ](https://www.softwareimprovementgroup.com/resources/how-artificial-intelligence-attacked-my-family-and-other-ai-security-lessons/) として公開されました。
<br />
<br />
<br />

# How to deal with AI privacy
Privacy principles and requirements come from different legislations (e.g. GDPR, LGPD, PIPEDA, etc.) and privacy standards (e.g. ISO 31700, ISO 29100, ISO 27701, FIPS, NIST Privacy Framework, etc.). This guideline does not guarantee compliance with a privacy legislation and it is also not a guide on privacy engineering of systems in general. For that purpose, please consider work from [ENISA](https://www.enisa.europa.eu/publications/data-protection-engineering), [NIST](https://nvlpubs.nist.gov/nistpubs/ir/2017/NIST.IR.8062.pdf), [mplsplunk](https://github.com/mplspunk/awesome-privacy-engineering), [OWASP](https://owasp.org/www-project-top-10-privacy-risks/) and [OpenCRE](https://www.opencre.org/cre/362-550). The general principle for engineers is to regard personal data as 'radioactive gold'. It's valuable, but it's also something to minimize, carefully store, carefully handle, limit its usage, limit sharing, keep track of where it is, etc.

In this section, we will discuss how privacy principles apply to AI systems:

## 1. Use Limitation and Purpose Specification
 
Essentially, you should not simply use data collected for one purpose (e.g. safety or security) as a training dataset to train your model for other purposes (e.g. profiling, personalized marketing, etc.) For example, if you collect phone numbers and other identifiers as part of your MFA flow (to improve security ), that doesn't mean you can also use it for user targeting and other unrelated purposes. Similarly, you may need to collect sensitive data under KYC requirements, but such data should not be used for ML models used for business analytics without proper controls.

Some privacy laws require a lawful basis (or bases if more than one purpose) for processing personal data (See GDPR's Art 6 and 9). 

In practical terms, you should reduce access to sensitive data and create anonymized copies for incompatible purposes (e.g. analytics). You should also document a purpose/lawful basis before collecting the data and communicate that purpose to the user in an appropriate way. 

New techniques that enable use limitation include:

* data enclaves: store pooled personal data in restricted secure environments 
* federated learning:  decentralize ML by removing the need to pool data into a single location. Instead, the model is trained in multiple iterations at different sites.



## 2. Fairness

Fairness means handling personal data in a way individuals expect and not using it in ways that lead to unjustified adverse effects. The algorithm should not behave in a discriminating way. (See also [this article](https://iapp.org/news/a/what-is-the-role-of-privacy-professionals-in-preventing-discrimination-and-ensuring-equal-treatment/)). 
 
GDPR's Article 5 refers to "fair processing" and EDPS' [guideline](https://edpb.europa.eu/sites/default/files/files/file1/edpb_guidelines_201904_dataprotection_by_design_and_by_default_v2.0_en.pdf) defines fairness as the prevention of "unjustifiably detrimental, unlawfully discriminatory, unexpected or misleading" processing of personal data. GDPR does not specify how fairness can be measured, but the EDPS recommends right to information (transparency), right to intervene (access, erasure, data portability, rectify) and the right to limit the processing (right not to be subject to automated decision-making and non-discrimination) as measures and safeguard to implement the principle of fairness. 

In the [literature](http://fairware.cs.umass.edu/papers/Verma.pdf), there are different fairness metrics that you can use. These range from group fairness, false positive error rate,  unawareness and counterfactual fairness. There is no industry standard yet on which metric to use, but you should assess fairness especially if your algorithm is making significant decisions about the individuals (e.g. banning access to the platform, financial implications, denial of services/opportunities, etc.) . There are also efforts to test algorithms using different metrics. For example,  NIST's [FRVT project](https://pages.nist.gov/frvt/html/frvt11.html) tests different face recognition algorithms on fairness using different metrics.


## 3. Data Minimization and Storage Limitation

This principle requires that you should minimize the amount, granularity and the storage duration of personal information in your training dataset. To make it more concrete:

* Do not collect or copy unnecessary attributes to your dataset if this is irrelevant for your purpose
* Anonymize the data where possible. Please note that this is not as trivial as "removing PII". See [WP 29 Guideline](https://ec.europa.eu/justice/article-29/documentation/opinion-recommendation/files/2014/wp216_en.pdf)
* If full anonymization is not possible, reduce the granularity of the data in your dataset if you aim to produce aggregate insights (e.g. reduce lat/long to 2 decimal points if city level precision is enough for your purpose or remove the last octets of an ip address, round timestamps to the hour)
* Use less data where possible (e.g. if 10k records are sufficient for an experiment, do not use 1 million)
* Delete data as soon as possible when it is no longer useful (e.g. data from 7 years ago may not be relevant for your model)
* Remove links in your dataset (e.g. obfuscate user id's, device identifiers and other linkable attributes)
* Minimize the number of stakeholders who accesses the data on a "need to know" basis

There are also privacy-preserving techniques being developed that supports data minimization:

* distributed data analysis: exchange anonymous aggregated data
* secure multi-party computation: store data distributed-encrypted
    
Further reading:
* [ICO guidance on AI and data protection](https://ico.org.uk/for-organisations/guide-to-data-protection/key-dp-themes/guidance-on-ai-and-data-protection/)
* [FPF case-law analysis on automated decision making](https://fpf.org/blog/fpf-report-automated-decision-making-under-the-gdpr-a-comprehensive-case-law-analysis/)


## 4. Transparency
Privacy standards such as FIPP or ISO29100 refer to maintaining privacy notices, providing a copy of user's data upon request, giving notice when major changes in personal data procesing occur, etc. 

GDPR also refers to such practices, but also has a specific clause related to algorithmic-decision making. 
GDPR's [Article 22](https://ec.europa.eu/newsroom/article29/items/612053) allows individuals specific rights under specific conditions. This includes getting human intervention to an algorithmic decision , an ability to contest the decision and get a meaningful information about the logic involved. For examples of "meaningful information", see EDPS's [guideline](https://ec.europa.eu/newsroom/article29/items/612053).  The US [Equal Credit Opportunity Act](https://www.consumerfinance.gov/about-us/newsroom/cfpb-acts-to-protect-the-public-from-black-box-credit-models-using-complex-algorithms/) requires detailed explanations on individual decisions by algorithms that deny credit. 

Transparency is not only needed for the end-user. Your models and datasets should be understandable by internal stakeholders as well: model developers, internal audit, privacy engineers, domain experts and more. This typically requires the following:

* proper model documentation: model type, intent, proposed features, feature importance, potential harm and bias
* dataset transparency:source, lawful basis, type of data, whether it was cleaned, age. Data cards is a popular approach in the industry to achieve some of these goals. See Google Research's [paper](https://arxiv.org/abs/2204.01075) and Meta's [research](https://ai.facebook.com/research/publications/system-level-transparency-of-machine-learning).    
* traceability: which model has made that decision about an individual and when?
* explainability: several methods exist to make black-box models more explainable. These include LIME, SHAP, counterfactual explanations, Deep Taylor Decomposition, etc. See also [this overview of machine learning interpretability](https://github.com/jphall663/awesome-machine-learning-interpretability) and [this article on the pros and cons of explainable AI](https://www.softwareimprovementgroup.com/resources/unraveling-the-incomprehensible-the-pros-and-cons-of-explainable-ai/).

## 5. Privacy Rights
Also known as "individual participation" under privacy standards, this principle allows individuals to submit requests to your organization related to their personal data. Most referred rights are: 

1. right of access / portability: provide a copy of user data, preferably in machine readable format. If data is properly anonymized, it may be exempted from this right. 
2. right of erasure: erase user data unless an exception applies. It is also a good practice to re-train your model without the deleted user's data.
3. right of correction: allow users to correct factually incorrect data. Also see accuracy below
4. right of object: allow users to object the usage of their data for a specific use (e.g. model training)

## 6. Accuracy
You should ensure that your data is correct as the output of an algorithmic decision with incorrect data may lead to severe consequences for the individual. For example, if the user's phone number is incorrectly added to the system and if such number is associated with fraud, the user might be banned from a service/system in an unjust manner. You should have processes/tools in place to fix such accuracy issues as soon as possible when a proper request is made by the individual . 

To satisfy the accuracy principle, you should also have tools and processes in place to ensure that the data is obtained from reliable sources, its validity and correctness claims are validated and data quality and accuracy are periodically assessed.

## 7. Consent
Consent may be used or required in specific circumstances. In such cases, consent must satisfy the following:

  1. obtained before collecting, using, updating or sharing the data
  2. consent should be recorded and be auditable
  3. consent should be granular (use consent per purpose, and avoid blanket consents)
  4. consent should not be bundled with T&S
  5. consent records should be protected from tampering
  6. consent method and text should adhere to specific requirements of the jurisdiction in which consent is required (e.g. GDPR requires unambigious, freely given, written in clear and plain language, explicit and withdrawable)
  7. Consent withdrawal should be as easy as giving consent
  8. If consent is withdrawn, then all associated data with the consent should be deleted and the model should be re-trained.
  
Please note that consent will not be possible in specific circumstances (e.g. you cannot collect consent from a fraudster and an employer cannot collect consent from an employee as there is a power imbalance). If you must collect consent, then ensure that it is properly obtained, recorded and proper actions are taken if it is withdrawn. 


## Scope boundaries of AI privacy
As said, many of the discussion topics on AI are about human rights, social justice, safety and only a part of it has to do with privacy. So as a data protection officer or engineer it's important not to drag everything into your responsibilities. At the same time, organizations do need to assign those non-privacy AI responsibilities somewhere.


## Before you start: Privacy restrictions on what you can do with AI
The GDPR does not restrict the applications of AI explicitly but does provide safeguards that may limit what you can do, in particular regarding Lawfulness and limitations on purposes of collection, processing, and storage - as mentioned above. For more information on lawful grounds, see [article 6](https://gdpr.eu/article-6-how-to-process-personal-data-legally/)

In contrast, the [EU AI act](https://eur-lex.europa.eu/legal-content/EN/TXT/HTML/?uri=CELEX:52021PC0206&from=EN) does pose explicit application limitations, such as mass surveillance, predictive policing, and restrictions on high-risk purposes such as selecting people for jobs. In addition, there are regulations for specific domains that restrict the use of data, putting limits to some AI approaches (e.g. the medical domain). 

In an upcoming update, more will be discussed on the [US AI bill of rights](https://www.whitehouse.gov/ostp/ai-bill-of-rights/).

The [US Federal Trade Committe](https://www.ftc.gov/business-guidance/blog/2023/02/keep-your-ai-claims-check) provides some good (global) guidance in communicating carefully about your AI, including not to overpromise.

# Project status
This page is the current outcome of the project. The goal is to collect and present the state of the art on these topics through community collaboration. First in the form of this page, and later in other document forms. Please provide your input through pull requests / submitting issues (see [repo](https://github.com/OWASP/www-project-ai-security-and-privacy-guide/)) or emailing the project lead, and let's make this guide better and better. 

The work in this guide will serve as input to the upcoming [ISO/IEC 27090 (AI security)](https://www.iso.org/standard/56581.html) and [27091 (AI privacy)](https://standardsdevelopment.bsigroup.com/projects/9022-07819#/section) standards, which will be done through membership of the ISO/IEC JTC 1/SC42 AHG4 group.

# Further reading

* [NIST AI Risk Management Framework 1.0](https://doi.org/10.6028/NIST.AI.100-1)
* [PLOT4ai threat library ](https://plot4.ai/library)
* [ENISA AI security standard discussion](https://www.enisa.europa.eu/publications/cybersecurity-of-ai-and-standardisation)
* [Microsoft/MITRE tooling for ML teams](https://www.mitre.org/news-insights/news-release/microsoft-and-mitre-create-tool-help-security-teams-prepare-attacks?sf175190906=1)
* [MITRE ATLAS framework for AI threats](https://atlas.mitre.org/)
