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

  * **入力操作攻撃 (Input manipulation attack)**: 欺瞞的な入力データでモデルを欺きます。この攻撃は三つの方法で実行できます。1) モデル入力で実験する (ブラックボックス)、2) モデルパラメータの解析に基づいて悪意を持って設計された入力を取り込む (ホワイトボックス)、3) データポイズニングで行われた入力を基にする (上記参照)。ポイズニングの軽減、モデルパラメータへのアクセス制限、出力から信頼度情報の除外、画像への物理的パッチなどの操作タイプの制限、監視、検出とともに堅牢な性能のモデルは最善の緩和策となります。さらに、操作された入力に対してモデルを堅牢にするために、訓練プロセスに敵対的な例を含めることができます。これは「無作為抽出による平滑化 (_randomized smoothing_)」 と呼ばれる技法によって実現できます。別名: 回避攻撃 (evasion attacks)、敵対的サンプル (_adversarial examples_)。ホワイトボックスについては [交通標識に関するこの論文](https://openaccess.thecvf.com/content_cvpr_2018/papers/Eykholt_Robust_Physical-World_Attacks_CVPR_2018_paper.pdf) と [パンダ画像に関するこの成果物](https://arxiv.org/pdf/1412.6572.pdf) を参照してください。


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

# AI プライバシーの取り組み方
プライバシーの原則と要件はさまざまな法律 (GDPR, LGPD, PIPEDA など) やプライバシー標準 (ISO 31700, ISO 29100, ISO 27701, FIPS, NIST Privacy Framework など) に由来します。本ガイドラインは個人情報保護法への準拠を保証するものではなく、一般的なシステムのプライバシーエンジニアリングに関するガイドでもありません。そのためには [ENISA](https://www.enisa.europa.eu/publications/data-protection-engineering), [NIST](https://nvlpubs.nist.gov/nistpubs/ir/2017/NIST.IR.8062.pdf), [mplsplunk](https://github.com/mplspunk/awesome-privacy-engineering), [OWASP](https://owasp.org/www-project-top-10-privacy-risks/), [OpenCRE](https://www.opencre.org/cre/362-550) による作業を検討してください。エンジニアの一般的な原則は個人データを「放射能を持つ金 (radioactive gold)」とみなすことです。それは貴重ですが、最小限に抑え、慎重に保管し、慎重に取り扱い、使用を制限し、共有を制限し、所在を追跡し続けるようなものでもあります。

このセクションではプライバシーの原則が AI システムにどのように適用されるかについて説明します。

## 1. 使用制限と目的指定 (Use Limitation and Purpose Specification)

基本的に、ある目的 (セーフティやセキュリティなど) のために収集されたデータを他の目的 (プロファイリング、個人向けマーケティングなど) のためのモデルを訓練するための訓練データセットとして絶対に使用してはいけません。たとえば、MFA フローの一環として (セキュリティ向上のために) 電話番号やその他の識別子を収集した際、それをユーザーターゲティングやその他の無関係な目的にも使用できるわけではありません。同様に、KYC 要件の下で機密データを収集する必要があるかもしれませんが、そのようなデータは適切な管理なしでビジネス分析に使用される ML モデルに使用すべきではありません。

個人情報保護法の中には個人データの処理に法的根拠 (複数の目的の場合は複数の根拠) を求めるものがあります (GDPR の第 6 条および第 9 条を参照) 。

実際には、機密データへのアクセスを減らし、互換性のない目的 (分析など) のために匿名化されたコピーを作成する必要があります。また、データを収集する前に目的と法的根拠を文書化し、その目的を適切な方法でユーザーに伝える必要があります。

使用制限を可能にする新しい技法には以下のものがあります。

* データエンクレーブ (data enclaves): プールされた個人データを制限された安全な環境に保管します。
* 連合学習 (federated learning): データを一つの場所にプールする必要をなくすことで ML を分散化します。代わりに、モデルを異なるサイトで複数回繰り返して訓練します。



## 2. 公平性 (Fairness)

公平性とは個人データを個人が期待する方法で取り扱い、不当な悪影響をもたらすような使い方をしないことを意味します。そのアルゴリズムは差別的な振る舞いをすべきではありません。([この記事](https://iapp.org/news/a/what-is-the-role-of-privacy-professionals-in-preventing-discrimination-and-ensuring-equal-treatment/) も参照してください) 。

GDPR の第 5 条は「公正な処理 (fair processing)」に言及しており、EDPS の [ガイドライン](https://edpb.europa.eu/sites/default/files/files/file1/edpb_guidelines_201904_dataprotection_by_design_and_by_default_v2.0_en.pdf) では公平性を個人データの「不当に不利益な処理、違法な差別的処理、予想外の処理、誤解を招く処理」を防止することと定義しています。GDPR では公平性に対応する方法を規定していませんが、EDPS では公平性の原則を実装するための対応とセーフガードとして、情報に対する権利 (透明性)、介入する権利 (アクセス、消去、データポータビリティ、修正)、処理を制限する権利 (自動化された意思決定の対象とならない権利や無差別性) を推奨しています。

[文献](http://fairware.cs.umass.edu/papers/Verma.pdf) にはあなたが使用できるさまざまな公平性指標があります。これらはグループ公平性、誤検出エラー率、無自覚性、反事実公平性など多岐にわたります。どの指標を使用すべきかについての業界標準はまだありませんが、アルゴリズムが個人に関して重大な決定を下す場合 (プラットフォームへのアクセス禁止、金銭的影響、サービスや機会の拒否など) は特に公平性を評価すべきです。さまざまな指標を用いてアルゴリズムをテストする取り組みもあります。たとえば、NIST の [FRVT プロジェクト](https://pages.nist.gov/frvt/html/frvt11.html) ではさまざまな指標を用いてさまざまな顔認識アルゴリズムの公平性をテストしています。


## 3. データ最小化と保管制限 (Data Minimization and Storage Limitation)

この原則では訓練データセット内の個人情報の量、粒度、保存期間を最小限にすることを求めています。より具体的には以下のようになります。

* 目的とは関係なければ、不必要な属性をデータセットに収集したりコピーしてはいけません
* 可能な限りデータを匿名化します。これは「PII の削除」ほど簡単ではないことに注意してください。 [WP 29 ガイドライン](https://ec.europa.eu/justice/article-29/documentation/opinion-recommendation/files/2014/wp216_en.pdf) を参照してください
* 完全な匿名化が可能ではなければ、集約した洞察を生成することを目的としている場合にはデータセット内のデータの粒度を小さくします (たとえば、都市レベルの精度で目的に十分であれば緯度経度を小数点以下 2 桁に減らす、IP アドレスの最後のオクテットを削除する、タイムスタンプを一時間で丸めるなど)
* 可能な限り使用するデータを少なくする (たとえば、一万レコードで実験に十分であれば、百万レコードを使用してはいけません)
* 不要になったデータはできるだけ早く削除します (たとえば、7 年前のデータはモデルと関係ないかもしれません)
* データセット内のリンクを削除します (たとえば、ユーザー ID、デバイス識別子、その他のリンク可能な属性を難読化します)
* データにアクセスする利害関係者の数を「知る必要がある」という原則のもとに最小限に抑えます

データの最小化をサポートするプライバシー保護技術もあります。

* 分散データ解析: 匿名の集計データを交換します
* セキュアマルチパーティコンピューティング: データを分散暗号化して保存します

参考情報:
* [AI とデータ保護に関する ICO ガイダンス](https://ico.org.uk/for-organisations/guide-to-data-protection/key-dp-themes/guidance-on-ai-and-data-protection/)
* [自動意思決定に関する FPF 判例分析](https://fpf.org/blog/fpf-report-automated-decision-making-under-the-gdpr-a-comprehensive-case-law-analysis/)


## 4. 透明性 (Transparency)
FIPP や ISO29100 などのプライバシー標準ではプライバシー通知を維持すること、要求に応じてユーザーのデータのコピーを提供すること、個人データの処理に大きな変更があった場合に通知することなどに言及しています。

GDPR もこのような慣行に言及していますが、アルゴリズムによる意思決定に関連する特有の条項もあります。
GDPR の [第 22 条](https://ec.europa.eu/newsroom/article29/items/612053) は特定の条件下で個人に特定の権利を認めています。これにはアルゴリズムによる決定に対する人間の介入、決定に異議を唱える能力、関連するロジックに関する意味のある情報を取得することが含まれます。「意味のある情報」の例については EDPS の [ガイドライン](https://ec.europa.eu/newsroom/article29/items/612053) を参照してください。米国の [信用機会均等法 (Equal Credit Opportunity Act)](https://www.consumerfinance.gov/about-us/newsroom/cfpb-acts-to-protect-the-public-from-black-box-credit-models-using-complex-algorithms/) では信用を否定するアルゴリズムの個々の決定について詳細な説明を要求しています。

透明性はエンドユーザーだけに必要なものではありません。モデルとデータセットはモデル開発者、内部監査、プライバシーエンジニア、ドメイン専門家など、社内の利害関係者にも理解できるものであるべきです。これには一般的に以下のものが必要です。

* 適切なモデルの文書化: モデルの種類、意図、提案された機能、機能の重要性、潜在的な危害とバイアス
* データセットの透明性: ソース、法的根拠、データの種類、クリーニングの有無、年齢。データカードはこれらの目標のいくつかを達成するための業界で一般的なアプローチです。Google Research の [論文](https://arxiv.org/abs/2204.01075) と Meta の [研究](https://ai.facebook.com/research/publications/system-level-transparency-of-machine-learning) を参照してください。
* トレーサビリティ: ある個人についてどのモデルがいつその決定を下したか？
* 説明可能性: ブラックボックスモデルをより説明しやすくする方法がいくつかあります。これらには LIME、SHAP、反事実的説明 (counterfactual explanations)、ディープテイラー分解 (Deep Taylor Decomposition) などがあります。[機械学習の解釈可能性に関するこの概要](https://github.com/jphall663/awesome-machine-learning-interpretability) と [説明可能な AI の長所と短所に関するこの記事](https://www.softwareimprovementgroup.com/resources/unraveling-the-incomprehensible-the-pros-and-cons-of-explainable-ai/) も参照してください。

## 5. プライバシー権 (Privacy Rights)
Also known as "individual participation" under privacy standards, this principle allows individuals to submit requests to your organization related to their personal data. Most referred rights are: 

1. right of access / portability: provide a copy of user data, preferably in machine readable format. If data is properly anonymized, it may be exempted from this right. 
2. right of erasure: erase user data unless an exception applies. It is also a good practice to re-train your model without the deleted user's data.
3. right of correction: allow users to correct factually incorrect data. Also see accuracy below
4. right of object: allow users to object the usage of their data for a specific use (e.g. model training)

## 6. 正確性 (Accuracy)
You should ensure that your data is correct as the output of an algorithmic decision with incorrect data may lead to severe consequences for the individual. For example, if the user's phone number is incorrectly added to the system and if such number is associated with fraud, the user might be banned from a service/system in an unjust manner. You should have processes/tools in place to fix such accuracy issues as soon as possible when a proper request is made by the individual . 

To satisfy the accuracy principle, you should also have tools and processes in place to ensure that the data is obtained from reliable sources, its validity and correctness claims are validated and data quality and accuracy are periodically assessed.

## 7. 同意 (Consent)
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


## AI プライバシーのスコープ境界
As said, many of the discussion topics on AI are about human rights, social justice, safety and only a part of it has to do with privacy. So as a data protection officer or engineer it's important not to drag everything into your responsibilities. At the same time, organizations do need to assign those non-privacy AI responsibilities somewhere.


## 始める前に: AI でできることに関するプライバシー制限
The GDPR does not restrict the applications of AI explicitly but does provide safeguards that may limit what you can do, in particular regarding Lawfulness and limitations on purposes of collection, processing, and storage - as mentioned above. For more information on lawful grounds, see [article 6](https://gdpr.eu/article-6-how-to-process-personal-data-legally/)

In contrast, the [EU AI act](https://eur-lex.europa.eu/legal-content/EN/TXT/HTML/?uri=CELEX:52021PC0206&from=EN) does pose explicit application limitations, such as mass surveillance, predictive policing, and restrictions on high-risk purposes such as selecting people for jobs. In addition, there are regulations for specific domains that restrict the use of data, putting limits to some AI approaches (e.g. the medical domain). 

In an upcoming update, more will be discussed on the [US AI bill of rights](https://www.whitehouse.gov/ostp/ai-bill-of-rights/).

The [US Federal Trade Committe](https://www.ftc.gov/business-guidance/blog/2023/02/keep-your-ai-claims-check) provides some good (global) guidance in communicating carefully about your AI, including not to overpromise.

# プロジェクトの状況
This page is the current outcome of the project. The goal is to collect and present the state of the art on these topics through community collaboration. First in the form of this page, and later in other document forms. Please provide your input through pull requests / submitting issues (see [repo](https://github.com/OWASP/www-project-ai-security-and-privacy-guide/)) or emailing the project lead, and let's make this guide better and better. 

The work in this guide will serve as input to the upcoming [ISO/IEC 27090 (AI security)](https://www.iso.org/standard/56581.html) and [27091 (AI privacy)](https://standardsdevelopment.bsigroup.com/projects/9022-07819#/section) standards, which will be done through membership of the ISO/IEC JTC 1/SC42 AHG4 group.

# 参考情報

* [NIST AI Risk Management Framework 1.0](https://doi.org/10.6028/NIST.AI.100-1)
* [PLOT4ai threat library ](https://plot4.ai/library)
* [ENISA AI security standard discussion](https://www.enisa.europa.eu/publications/cybersecurity-of-ai-and-standardisation)
* [Microsoft/MITRE tooling for ML teams](https://www.mitre.org/news-insights/news-release/microsoft-and-mitre-create-tool-help-security-teams-prepare-attacks?sf175190906=1)
* [MITRE ATLAS framework for AI threats](https://atlas.mitre.org/)
