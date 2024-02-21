---
title: AI セキュリティ概要
weight: 1
---
## 要旨 - AI セキュリティをどのように対処するか？
> このイニシアチブについての詳細、貢献や参加の方法については [ホーム](https://owaspai.org/) をご覧ください。
このページには AI セキュリティの概要があり、次のページでは主要なコンテンツである AI に対するセキュリティ脅威とそのコントロールの詳細を提供します。各ページの下部または左サイドバーでページを移動できます。右サイドバーにはページのさまざまなセクションを表示します。小さい画面ではメニューから移動できます。

AI は強力なパフォーマンス向上をもたらしますが、悪意のある者が利用できる攻撃対象領域も拡大します。そのため、潜在的な脅威と、ユースケースごとにどの脅威を優先するかを明確に理解して、AI アプリケーションに取り組むことが不可欠です。標準とガバナンスは AI 機能を活用する個々の事業体にとってこのプロセスの指針となります。

- **AI ガバナンス** を導入します。
- **セキュリティと開発プラクティスを拡張** して、データサイエンス活動を含め、特にエンジニアリング環境を保護し合理化します。
- AI の特殊性を理解することで、**通常のアプリケーションとシステムのセキュリティを向上** します。たとえば、モデルパラメータは保護が必要であり、モデルへのアクセスは監視してレート制限する必要があります。
- 権限を最小限に抑え、ガードレールや人間の監視などの監視を追加して、AI の **影響を制限** します。
- モデル攻撃を理解することによって **データサイエンスにおける対策** を行います。たとえば、データ品質保証、大規模なトレーニングセット、一般的な摂動攻撃の検出、入力フィルタリングなど。

## 脅威の概要

### 脅威モデル
私たちは三つのタイプの脅威を区別します: 開発時 (データを取得および準備し、モデルをトレーニング/取得するとき)、モデルの使用 (入力の提供と出力の読み取り) を通じて、実行時 (本番環境) にシステムへの攻撃によって。
この図ではこれら三つのグループの脅威を矢印で示しています。各脅威には特定の影響があり、Impact legend を参照する文字で示されています。コントロールの概要のセクションには、この図にコントロールのグループを追加したものがあります。
![AI Security Threats](https://raw.githubusercontent.com/OWASP/www-project-ai-security-and-privacy-guide/main/content/ai_exchange/static/images/threats.png)

### AI セキュリティマトリクス
以下の AI セキュリティマトリクスは、すべての脅威とリスクを、タイプと影響の順に示しています。
[![](https://raw.githubusercontent.com/OWASP/www-project-ai-security-and-privacy-guide/main/assets/images/OwaspAIsecuritymatix.png)](https://raw.githubusercontent.com/OWASP/www-project-ai-security-and-privacy-guide/main/assets/images/OwaspAIsecuritymatix.png)

## コントロールの概要

### 脅威モデルとコントロール - 全般
下図は AI Exchange のコントロールをグループに分け、これらのグループを対応する脅威とともに適切なライフサイクルに配置したものです。
![AI Security Threats and controls](https://raw.githubusercontent.com/OWASP/www-project-ai-security-and-privacy-guide/main/content/ai_exchange/static/images/threatscontrols.png)
コントロールのグループは AI セキュリティをどのように対処するかをまとめたものです (コントロールは大文字です)。
1. **AI ガバナンス**: AI リスクに対するガバナンスプロセスを導入し、情報セキュリティとソフトウェアライフサイクルのプロセスに AI を組み込みます。
   >(AIPROGRAM, SECPROGRAM, DEVPROGRAM, SECDEVPROGRAM, CHECKCOMPLIANCE, SECEDUCATE)
2. AI システムは IT システムであるため、従来の **技術的な IT セキュリティコントロール** を適用します。
    - 2a **標準** 的な従来の IT セキュリティコントロール (15408, ASVS, OpenCRE, ISO 27001 Annex A, NIST SP800-53 など) を完全な AI システムに適用し、新たな AI 固有の資産を忘れないようにします。
      - 開発時: モデルとデータの保存、モデルとデータのサプライチェーン、データサイエンスの文書化
        >(DEVDATAPROTECT, DEVSECURITY, SEGREGATEDATA, SUPPLYCHAINMANAGE, DISCRETE)
      - 実行時: モデルの保存、モデルの使用、プラグイン、モデルの入出力
        >(RUNTIMEMODELINTEGRITY, RUNTIMEMODELIOINTEGRITY, RUNTIMEMODELCONFIDENTIALITY, MODELINPUTCONFIDENTIALITY, ENCODEMODELOUTPUT, LIMITRESOURCES)
    - 2b 従来の IT セキュリティコントロールを **適応** して、AI により適したものにします (どの使用パターンを監視するかなど)。
      >(MONITORUSE, MODELACCESSCONTROL, RATELIMIT)
    - 2c **新規** の IT セキュリティコントロールを採用します。
      >(CONFCOMPUTE, MODELOBFUSCATION, PROMPTINPUTVALIDATION, INPUTSEGREGATION)
3. データサイエンティストはリスクベースの **データサイエンスセキュリティコントロール** を適用します。
    - 3a モデル開発時の開発時コントロール
      >(FEDERATIVELEARNING, CONTINUOUSVALIDATION, UNWANTEDBIASTESTING, EVASIONROBUSTMODEL, POISONROBUSTMODEL, TRAINADVERSARIAL, TRAINDATADISTORTION, ADVERSARIALROBUSTDISTILLATION, FILERSENSITIVETRAINDATA, MODELENSEMBLE, MORETRAINDATA, SMALLMODEL, DATAQUALITYCONTROL)
    - 3b 攻撃をフィルタして検出するための実行時コントロール
      >(DETECTODDINPUT, DETECTADVERSARIALINPUT, DOSINPUTVALIDATION, INPUTDISTORTION, FILTERSENSITIVEMODELOUTPUT, OBSCURECONFIDENCE)
4. **データを最小限に抑える:** 保存時および転送時のデータ量、保存時間を開発時、実行時に制限します。
   >(DATAMINIMIZE, ALLOWEDDATA, SHORTRETAIN, OBFUSCATETRAININGDATA)
5. モデルが間違いや操作によって望ましくない方法で動作する可能性があるため、**動作への影響を制御** します。
   >(OVERSIGHT, LEASTMODELPRIVILEGE, AITRAINSPARENCY, EXPLAINABILITY, CONTINUOUSVALIDATION, UNWANTEDBIASTESTING)


すべての脅威とコントロールについては AI Exchange の詳細なコンテンツで説明します。

### 脅威モデルとコントロール - 生成 AI をトレーニング/ファインチューニング
下図は、**トレーニングやファインチューニング** が組織によって行われる状況においての、生成 AI への脅威とコントロールにのみ制限しています (注: これはコストが高く、専門知識が必要であることを考慮すると、あまり一般的ではありません)。

![AI Security Threats and controls - GenAI trained or finetuned](https://raw.githubusercontent.com/OWASP/www-project-ai-security-and-privacy-guide/main/content/ai_exchange/static/images/threatscontrols-genainotready.png)

### 脅威モデルとコントロール - 生成 AI を現状のまま <a name="threat-model-with-controls---genai-as-is"></a>
下図は、モデルが組織によって **現状のまま** 使用される生成 AI への脅威とコントロールにのみ制限しています。プロバイダ (OpenAI など) がトレーニングやファインチューニングを行っています。そのため、いくつかの脅威はモデルプロバイダの責任です (機密データや著作権があるデータ、プロバイダでの操作)。とはいえ、モデルを使用する組織はこれらのリスクを考慮し、プロバイダからその保証を得る必要があります。

多くの状況では、現状のままのモデルが外部にホストされるため、セキュリティは、セキュリティ構成を含め、サプライヤがデータをどのように処理するかによって決まります。API はどのように保護されていますか？仮想プライベートクラウドとは何ですか？外部モデル全体ですか、それとも API だけですか？鍵管理は？データ保持は？ログ記録は？そのモデルは機密性の高い入力データを送信することでサードパーティのソースに接触しますか？

![AI Security Threats and controls - GenAI as-is](https://raw.githubusercontent.com/OWASP/www-project-ai-security-and-privacy-guide/main/content/ai_exchange/static/images/threatscontrols-readymodel.png)


### ナビゲータ図
以下のナビゲータ図はすべての脅威、コントロール、リスクとコントロールの種類を含むそれらの関係を示しています。
<!-- {{< callout type="info" >}} -->
  画像をクリックすると、クリック可能なリンクを含む PDF を取得できます。
<!-- {{< /callout >}} -->
[![](https://raw.githubusercontent.com/OWASP/www-project-ai-security-and-privacy-guide/main/assets/images/owaspaioverviewv2.png)](https://github.com/OWASP/www-project-ai-security-and-privacy-guide/raw/main/assets/images/owaspaioverviewpdfv3.pdf)


## このドキュメントについて

このドキュメントでは AI サイバーセキュリティに対する脅威と、それらの脅威に対するコントロール (つまり、対策、要件、緩和策) について説明します。
ここでいうセキュリティとは認可されていないアクセス、使用、開示、中断、改変、破壊を防止することを意味します。改変には AI モデルの動作を望ましくない方法で操作することが含まれます。

AI Exchange イニシアチブは OWASP により採択されており、[Rob van der Veer](https://www.linkedin.com/in/robvanderveer/) によって起こされました。セキュリティ標準の橋渡し役、[Software Improvement Group](https://www.softwareimprovementgroup.com) のシニアディレクター、AI とセキュリティで 31 年の経験を持ち、AI ライフサイクルに関する ISO/IEC 5338 の主執筆者、OpenCRE の創設者であり、現在は CEN/CENELEC で EU AI 法に関するセキュリティ要件に取り組んでいます。

この資料はすべて草案であり、他の人がレビューして修正できるよう仕掛品です。
これは EU AI 法、AI セキュリティに関する ISO/IEC 27090、AI プライバシーに関する ISO/IEC 27091、[OWASP ML Top 10](https://mltop10.info/)、[OWASP LLM Top 10](https://llmtop10.com/) などの進行中の主要なイニシアチブへのインプットとして機能し、さらに多くのイニシアチブが世界中で一貫した用語と洞察から恩恵を受けることができます。

### 情報源

- オープンソースとしてこれに貢献した AI セキュリティの専門家たち。
- これらの専門家の洞察はこのドキュメントの末尾に参考情報として記載されている研究成果 (ENISA, NIST, Microsoft, BIML, MITRE など) からインスピレーションを得たものです。

### 脅威とコントロールをどのように整理するか

脅威は影響ごとではなく、攻撃対象領域 (攻撃がどこでどのように行われるか) ごとに整理されています。これは、たとえばモデル盗用は概要の三つの異なる部分で言及されています。

1. 稼働中のシステムからモデルパラメータを盗むことによるモデル盗用。たとえば、ネットワークに侵入してファイルからパラメータを読み取ります。
2. エンジニアリング環境からモデルプロセスやパラメータを盗むことによるモデル盗用。たとえば、データサイエンティストのバージョン管理システムに保存されているもの。
3. AI システムを使用したリバースエンジニアリングによるモデル盗用。これらは三つの大きく異なる攻撃ですが、同様の影響を及ぼします。目標は脅威をコントロールに結び付けることであり、これらのコントロールは攻撃対象領域ごとに異なるため、このような整理方法は役に立ちます。

## 関連する脅威とコントロールをどのように選択するか？　リスク分析
このドキュメントには多くの脅威とコントロールについて説明します。どの脅威があなたに関係し、どのコントロールがあなたの責任となるかは、あなたの状況によって決まります。この選択プロセスは目前のユースケースとアーキテクチャのリスク分析を通じて実行できます。

1. **脅威の特定**: まず脅威のリストからあなたのケースに該当する脅威を選択し、_影響 (Impact)_ の説明を使用して適用可能かどうかを確認します。たとえば訓練データ内の個人を特定することによる影響は、訓練データが個人を所持していない場合、あなたのケースには適用されません。[ナビゲータ](https://github.com/OWASP/www-project-ai-security-and-privacy-guide/raw/main/assets/images/owaspaioverviewpdfv3.pdf) では影響を紫色で示しています。

    RAG (Retrieval Augmented Generation, 検索拡張生成) を使用する場合、検索リポジトリ (埋め込みを含む) を訓練データと同じように扱います。つまり、
      - データポイズニングに関する脅威を含めます
      - データが機密性の高い場合、訓練データやテストデータの漏洩に関する脅威を含めます

    そうではなく、モデルを訓練やファインチューニングしない場合、
      - サプライチェーン管理を除き、開発時の脅威を無視します。入手したモデルが操作されたものではなく本物であることを確認します。
      - 訓練データの機密性の脅威を無視します
      - モデル知的財産の機密性の脅威を無視します
      - データポイズニングの脅威を無視します
      - 開発時コントロール (機密性の高い訓練データをフィルタリングするなど) を無視します

    これらはモデル製作者の責任ですが、望ましくない結果の影響を受ける可能性があることに注意してください。製作者は機密保持の問題に対処して、問題の責任を負うかもしれませんが、操作されたモデルの動作によって事実上被害を受けることになります。

    訓練データが機密ではない場合、訓練データの機密性の脅威を無視します。特殊なケースとして _メンバーシップ推論_ の脅威があります。この脅威は、ある人物がトレーニングセットの一部であるという **事実** がその人物に関する有害な情報である場合にのみ適用されます。たとえば、トレーニングセットが犯罪者とその経歴で構成され、犯罪歴を予測する場合、そのセットのメンバーシップはその人物が有罪判決を受けた、あるいは犯罪容疑のあることを意味します。

    モデルが生成 AI モデルである場合、回避、モデル反転の脅威を無視します。また、生成 AI モデルが LLM ではない場合、プロンプトインジェクションと安全でない出力処理も無視します。

    モデルが生成 AI モデルではない場合、(直接) プロンプトインジェクションと安全でない出力処理を無視します。また、**回避攻撃** にまつわるリスクについて考えてみます。モデルが間違った判断を下すように入力を操作することは、攻撃者にとって興味深く、かつ可能でしょうか？回避が興味深く、かつ可能である例としては、スパムメールに特定の単語を追加して、それがスパムメールと認識されないようにすることです。回避が面白くない例としては、患者が皮膚の写真に基づいて皮膚病の診断を受ける場合があります。患者は間違った判断には興味がありませんし、また、通常、患者はなにも制御できません。まあ、皮膚に絵を描くことはできるかもしれませんが。これが患者にとって興味深いかもしれない状況があり、たとえば、(偽装された) 皮膚病が特定のレストランの食事によって引き起こされた場合に補償の対象になります。これは、理論上の脅威が実際の脅威であるかどうかはすべてコンテキストに依存することを示しています。

    入力データが機密ではない場合、「入力データの漏洩」を無視します。RAG を使用する場合、取得するデータも入力データとみなします。

3. **責任の采配**: 選択した各脅威に対して、対処する責任者を決定します。デフォルトでは、AI システムの構築と配備を行う組織が責任を負いますが、構築と配備は別の組織が行うかもしれませんし、たとえば、モデルをホストしたり、アプリケーションを実行するためのクラウド環境を提供するなど、構築と配備の一部を別の組織に委ねるかもしれません。いくつかの側面では責任を共有します。

    AI システムのコンポーネントがホストされている場合、関連する脅威に対するすべてのコントロールに関する責任をホスティングプロバイダと共有します。これは責任マトリクスなどを使用して、プロバイダと調整する必要があります。コンポーネントにはモデル、モデル拡張、アプリケーション、インフラストラクチャがあります。[現状のままのモデルを使用した脅威モデル](#threat-model-with-controls---genai-as-is) を参照してください。

   特定のリスクがどのように軽減されるかについて外部パーティがオープンにしていない場合は、この情報を要求することを検討してください。これが不明瞭なままの場合は、1) リスクを受け入れるか、2) 独自の軽減策を提供するか、3) サードパーティと関わらないことでリスクを回避するかのいずれかに直面することになります。

4. **外部の責任を検証する:** 他の組織の責任である脅威について、これらの組織が対処しているかどうかを確認します。これにはこれらの脅威に関連するコントロールを含みます。
5. **コントロールの選択**: 次に、自分に関連して自分が責任を負う脅威について、その脅威 (またはその脅威の親セクション) に記載されているさまざまなコントロールと一般的なコントロール (こちらは常に適用されます) を検討します。コントロールを検討する際、その目的を考慮し、それを実装するのに十分重要であると考えるか、およびどの程度まで実施するかを判断します。これはその目的が脅威を緩和する方法と比較した実装コスト、および脅威のリスクレベルによって異なります。もちろん、これらの要素はコントロールを選択する順番にも関わります。最初に最もリスクの高いもの、それから比較的コストの低いコントロール (簡単にできるもの) に着手します。
6. **リファレンスの使用**: コントロールを実装する際、標準へのリファレンスとリンクを考慮します。あなたはこれらの標準の一部を実装しているかもしれませんし、標準の内容がコントロールの実装に役立つかもしれません。
7. **リスクの受け入れ**: 最終的には、実装したコントロールを前提として、それぞれの脅威に関して残存するリスクを受容できる必要があります。
8. **これらのコントロールのさらなる管理** (SECPROGRAM 参照) には、継続的な監視、文書化、レポーティング、インシデント対応などがあります。

リスク分析の詳細については、SECPROGRAM コントロールを参照してください。

## ... についてはどうですか？
### 機械学習以外の AI についてはどうですか？
AI を理解するのに役立つ方法は、AI が機械学習 (現在主流の AI タイプ) モデルと _ヒューリスティックモデル_ から構成されていると考えることです。モデルはデータに基づいて計算方法を学習した機械学習モデルであることも、ルールベースのシステムなどの人間の知識に基づいて設計されたヒューリスティックモデルであることもあります。ヒューリスティックモデルは依然としてテストのためにデータを必要とし、さらに人間の知識を構築して検証するために分析を行うこともあります。
このドキュメントは機械学習に焦点を当てています。とはいえ、ここではヒューリスティックシステムにも適用される、このドキュメントの機械学習の脅威を簡単に要約します。

- モデル回避はヒューリスティックモデルでも可能です - ルールの抜け穴を見つけようと試みます
- 使用によるモデル盗用 - ヒューリスティックモデルからの入出力の組み合わせに基づいて機械学習モデルを訓練できます
- 使用による過度の依存 - ヒューリスティックシステムも過度に依存することがあります。適用された知識は誤りの可能性があります
- データポイズニングとモデルポイズニングは知識を向上させるために使用されるデータを操作したり、開発時や実行時にルールを操作する可能性があります
- 分析やテストに使用されるデータの漏洩が依然として問題になる可能性があります
- 知識、ソースコード、設定が知的財産である場合、機密データとみなされる可能性があり、保護が必要です
- たとえばヒューリスティックシステムが患者を診断する必要がある場合、機密性の高い入力データが漏洩します

### 責任ある AI や信頼できる AI についてはどうですか？
責任ある AI や信頼できる AI にはセキュリティが含まれますが、その逆ではありません。責任ある AI や信頼できる AI にはセキュリティ以外にも多くの側面があり、物事をややこしくしているのですが、これらの各側面はセキュリティと関連しています。わかりやすく説明してみましょう。
- **正確性 (Accuracy)** はその「ビジネス機能」を実行するのに十分に正しいかどうかを指します。不正確であると、物理的な安全性の問題 (運転中に車のトランクが開いてしまうなど) やその他の有害な間違った判断 (ローンの不当な拒否など) につながる可能性があります。セキュリティとの関連は、ある種の攻撃が望ましくないモデル動作を引き起こすことであり、これは定義上、正確性の問題です。とはいえ、セキュリティの範囲ではそのような攻撃のリスクを軽減することに限定されており、正確なモデルの作成 (トレーニングセットの代表データの選択など) の問題全体を解決するものではありません。
- **安全性 (Safety)** (_信頼性 (Reliability)_ ともよばれます) は危害 (一般的に物理的な危害を意味しますが、それに限定されません) のリスクがある場合の正確性のレベルのことであり、さらに (正確性とは別に) それらのリスクを軽減するために設けられたものです。これには正確性を保護するためのセキュリティに加えて、モデルのビジネス機能にとって重要な多くの安全性の対策を含みます。これらはセキュリティ上の理由だけでなく、他の理由 (不適切なトレーニングデータなど) でモデルが安全でない決定を下す可能性があるため、安全性とセキュリティの間で共通する懸念事項であることに注意する必要があります。
  -  安全でない動作を制限するための監視、およびそれに関連して、モデルへの最小権限の割り当て
  -  正確性を保護するための継続的な検証
  -  ユーザーおよび依存するシステムに正確性のリスクを警告するための透明性
  -  ユーザーが正確性を検証するのに役立つ説明可能性
- **透明性 (Transparency)**: 上記を参照してください。さらに、多くの場合、ユーザーは使用されているモデルについての詳細とそれがどのように作成されたかを知る権利を持っています。そのため、セキュリティ、プライバシー、安全性の間で共通する懸念事項になります。
- **説明可能性 (Explainability)**: 上記を参照してください。正確性を検証することとは別に、ユーザーが透明性を取得でき、異なる結果を得るには何を変更する必要があるかを理解することもできます。そのため、セキュリティ、プライバシー、安全性、ビジネス機能の間で共通する懸念事項になります。特別なケースには、プライバシーとは別に説明可能性を法律で要求されている場合であり、この懸念を共有する側面のリストに「コンプライアンス」を追加します。
- **堅牢性 (Robustness)** は、入力に予期したバリエーションや予期しないバリエーションがあっても正確性を維持する能力です。セキュリティの範囲ではそのようなバリエーションが悪意のある場合に関するものであり、良性のバリエーションに対する堅牢性のために必要な対策とは異なる対策が必要になることがよくあります。正確性の場合と同様に、セキュリティ自体は良性のバリエーションに対する堅牢なモデルの作成には関与しません。この例外は良性の堅牢性が悪性の堅牢性をサポートする場合であり、この場合には安全性とセキュリティの間で共通する懸念事項になります。これはケースバイケースで異なります。
- **公平性 (Fairness)** はモデルが特定のグループを「不当に扱う」ような「望ましくないバイアスがない」ことです。これは法的および倫理的な理由から望ましくなく、そのため主にビジネス上の懸念事項になります。セキュリティとの関係は、望ましくないバイアスを検出することで、攻撃によって引き起こされる望ましくないモデル動作を特定するのに役立つことです。たとえば、データポイズニング攻撃はトレーニングセットに悪意のあるデータサンプルを挿入します。最初は気付かれませんが、モデル内の原因不明のバイアルが検出されることによって発見されます。
- **共感性 (Empathy)**。セキュリティとの関係は、AI の特定のアプリケーションを検証する際に、常に実現可能なセキュリティレベルを考慮すべきであるということです。十分なレベルのセキュリティを個人や組織に提供できないのであれば、共感性とはそのアイデアを無効にするか、他の予防措置を講じることを意味します。
- **説明責任 (Accountability)**。説明責任とセキュリティの関係は、セキュリティ対策はその対策に至ったプロセスを含めて実証可能であるべきということです。さらに、セキュリティインシデントを検出し、再構築し、対応して、説明責任を果たすためには、他の IT システムと同様に、セキュリティ特性としてのトレーサビリティが重要です。

### プライバシーについてはどうですか？

AI プライバシーは二つのパートに分けることができます。

1. このドキュメントの AI セキュリティの脅威とコントロールは (個人) データの機密性と完全性 (モデル反転、トレーニングデータの漏洩など)、およびモデルの動作の完全性に関するものです。
2. GDPR などのプライバシー規制でカバーされる個人の権利に関する脅威とコントロール。これには使用制限、同意、公平性、透明性、データの正確性、訂正/異議申し立て/再確認/アクセスの権利が含まれます。概要については、[OWASP AI ガイドのプライバシーパート](https://owasp.org/www-project-ai-security-and-privacy-guide/) を参照してください。

### 生成 AI (LLM など) についてはどうですか？

はい、生成 AI は現在の AI 変革をリードしており、AI セキュリティの中で最も急速に変化しているサブフィールドです。とはいえ、クレジットスコアリング、不正検出、医療診断、製品推奨、画像認識、予知保全、プロセス制御など、多くの重要なユースケースには他のタイプのアルゴリズムが引き続き適用されることを認識することが重要です。このドキュメントでは関連するコンテンツには「生成 AI」のマークを付けています。

重要な注意: セキュリティフレームワークの観点からは、生成 AI は他の形式の AI とそれほど違いはありません。生成 AI の脅威とコントロールは一般的な AI と大部分が重複しており、非常によく似ています。とはいえ、一部のリスクは (はるかに) 高くなります。低いものもあります。生成 AI 固有のリスクはごくわずかです。

生成 AI セキュリティの特徴は以下の通りです。

|No.| 生成 AI セキュリティの特徴 | OWASP for LLM TOP 10 |
|-| ----------|-------------------|
|1| 一般的な回避攻撃は細工された入力を使用してモデルを騙して望ましくない判断をさせることですが、生成 AI の場合は、細工されたプロンプトを使用してモデルを騙し、動作ポリシー (攻撃的な出力の防止やシークレットの漏洩防止など) を回避することです。 | ([OWASP for LLM 01:Prompt injection](https://llmtop10.com/llm01/)) |
|2| 機密性の高いトレーニングデータの望ましくない出力は AI 全般の問題ですが、一般的に豊富なコンテンツを出力し、多種多様なデータセットでトレーニングされている生成 AI システムではリスクがより高くなる可能性があります。 | ([OWASP for LLM 06](https://llmtop10.com/llm06/)) |
|3| 生成 AI モデルはトレーニングデータのアクセス権限のばらつきを考慮しません。モデルユーザーはすべてのデータにアクセスできます。 | ([OWASP for LLM 06: Sensitive Information Disclosure](https://llmtop10.com/llm06/)) |
|4| トレーニングデータポイズニングは AI 全般の問題ですが、生成 AI ではトレーニングデータがインターネットなどの制御が困難なさまざまな情報源から供給される可能性があるため、リスクは一般的に高くなります。たとえば、攻撃者はドメインを乗っ取り、操作された情報を配置する可能性があります。 | ([OWASP for LLM 03: Training Data Poisoning](https://llmtop10.com/llm03/)) |
|5| 過度の依存は AI 全般のリスク要因であり、さらに大規模言語モデル (生成 AI) は非常に機密性が高く知識を持っていると思われることで事態を悪化させる可能性があります。 | ([OWASP for LLM 09: Overreliance](https://llmtop10.com/llm09/)) および ([OWASP for LLM 08: Excessive agency](https://llmtop10.com/llm08/)) |
|6| 入力データの漏洩: 生成 AI モデルはほとんどがクラウドに存在し、多くの場合は外部パーティによって管理されているため、トレーニングデータの漏洩やプロンプトの漏洩のリスクが高まる可能性があります。この問題は生成 AI に限定されるものではありませんが、生成 AI には特に 2 つのリスクがあります。1) モデルの使用にはプロンプトを介したユーザーとのやり取り、ユーザーデータの追加、対応するプライバシーやセンシティビティの問題が含まれます。2) 生成 AI モデルの入力 (プロンプト) には機密データ (企業秘密など) を持つ豊富なコンテキスト情報を含む可能性があります。後者の問題はたとえば、コンサルタント会社でこれまでに書かれたすべてのレポートのデータなど、*コンテキスト内学習 (In Context Learning)* や *検索拡張生成 (Retrieval Augmented Generation, RAG)* で発生します。まず第一に、この情報はプロンプトとともにクラウドに移動し、第二に、システムは情報に対する本来のアクセス権を考慮しない可能性があります。[機密入力データの漏洩](owaspaiexchange.md#47-leak-sensitive-input-data) の脅威を参照してください。 | |
|7| 事前トレーニング済みモデルは操作されている可能性があります。事前トレーニングの概念は生成 AI に限ったことではありませんが、このアプローチは生成 AI ではごく一般的であり、転移学習攻撃のリスクを高めます。 | ([OWASP for LLM 05 - Supply chain vulnerabilities](https://llmtop10.com/llm05/)) |
|8| 大規模言語モデル (生成 AI) でのプラグインの一般的なアプリケーションでは、大規模言語モデル (生成 AI) がユーザーとの通常の会話以外で動作することを許可するため、これらのプラグインの保護と権限に関する特定のリスクが生じます。 | ([OWASP for LLM 07](https://llmtop10.com/llm07/)) |
|9| プロンプトインジェクションは生成 AI 特有の脅威であり、アプリケーションセキュリティ脅威に記載されています。 | ([OWASP for LLM 01](https://llmtop10.com/llm01/)) |
|10| モデル反転とメンバーシップ推論は生成 AI にとって低リスクまたはゼロリスクです。 | ([OWASP for LLM 06](https://llmtop10.com/llm06/)) |
|11| 生成 AI の出力にはクロスサイトスクリプティングなどのインジェクション攻撃を実行する要素を含むかもしれません。 | ([OWASP for LLM 02](https://llmtop10.com/llm02/)) |
|12| サービス拒否はどの AI モデルでも問題になる可能性がありますが、生成 AI モデルはリソースの使用量が比較的多いため、特に影響を受けやすくなります。 | ([OWASP for LLM 04](https://llmtop10.com/llm04/)) |

生成 AI 参考情報:

- [OWASP LLM top 10](https://llmtop10.com/)
- [Demystifying the LLM top 10](https://blog.kloudzone.co.in/demystifying-the-owasp-top-10-for-large-language-model-applications/)
- [Impacts and risks of GenAI](https://arxiv.org/pdf/2306.13033.pdf)

### NCSC/CISA ガイドラインについてはどうですか？

英国/米国 の [安全な AI システム開発のガイドライン](https://www.ncsc.gov.uk/collection/guidelines-secure-ai-system-development) と AI Exchange のコントロールとのマッピング: 
(このドキュメントで検索するか、[ナビゲータ](https://github.com/OWASP/www-project-ai-security-and-privacy-guide/raw/main/assets/images/owaspaioverviewpdfv3.pdf) を使用してください)


1. 安全な設計

- 脅威とリスクに対するスタッフの意識を高めます:
  #SECEDUCATE
- システムに対する脅威をモデル化します:
  #SECPROGRAM のリスク分析を参照してください
- 機能性とパフォーマンスだけでなくセキュリティも考慮してシステムを設計します:
  #AIPROGRAM, #SECPROGRAM, #DEVPROGRAM, #SECDEVPROGRAM, #CHECKCOMPLIANCE, #LEASTMODELPRIVILEGE, #DISCRETE, #OBSCURECONFIDENCE, #OVERSIGHT, #RATELIMIT, #DOSINPUTVALIDATION, #LIMITRESOURCES, #MODELACCESSCONTROL, #AITRANSPRENCY
- AI モデルを選択する際に、セキュリティの利点とトレードオフを考慮します
  すべての開発時のデータサイエンスコントロール (現在 13), #EXPLAINABILITY

2. 安全な開発

- サプライチェーンを保護します:
  #SUPPLYCHAINMANAGE
- 資産を特定、追跡、保護します:
  #DEVDATAPROTECT, #DEVSECURITY, #SEGREGATEDATA, #CONFCOMPUTE, #MODELINPUTCONFIDENTIALITY, #RUNTIMEMODELCONFIDENTIALITY, #DATAMINIMIZE, #ALLOWEDDATA, #SHORTRETAIN, #OBFUSCATETRAININGDATA および #SECPROGRAM の一部
- データ、モデル、プロンプトを文書化します:
  #DEVPROGRAM の一部
- 技術的負債を管理します:
  #DEVPROGRAM の一部

3. 安全な展開

- インフラストラクチャを保護します:
  #SECPROGRAM の一部と「資産を特定、追跡、保護します」を参照してください
- モデルを継続的に保護します:
  #INPUTDISTORTION, #FILTERSENSITIVEMODELOUTPUT, #RUNTIMEMODELIOINTEGRITY, #MODELINPUTCONFIDENTIALITY, #PROMPTINPUTVALIDATION, #INPUTSEGREGATION
- インシデント管理手順を策定します:
  #SECPROGRAM の一部
- 責任をもって AI をリリースします:
  #DEVPROGRAM の一部
- ユーザーが正しいことを簡単にできるようにします:
  #SECPROGRAM の一部

4. 安全な運用と保守

- システムの動作を監視します:
  #CONTINUOUSVALIDATION, #UNWANTEDBIASTESTING
- システムの入力を監視します:
  #MONITORUSE, #DETECTODDINPUT, #DETECTADVERSARIALINPUT
- セキュアバイデザインのアプローチに従ってアップデートを行います:
  #SECDEVPROGRAM の一部
- 教訓を収集して共有します:
  #SECPROGAM および #SECDEVPROGRAM の一部

## 参考情報

OWASP AI ガイド (このドキュメントはその一部のプロジェクトです) に関する参考情報:

- 2023 年 2 月 15 日にダブリンで開催された OWASP Global AppSec イベントで OWASP AI ガイドが発表されました。[Rob van der Veer の講演](https://sched.co/1F9DT) の [動画](https://www.youtube.com/watch?v=ABmWHnFrMqI) と [スライド](https://github.com/OWASP/www-project-ai-security-and-privacy-guide/blob/main/assets/images/20230215-Rob-AIsecurity-Appsec-ForSharing.pdf?raw=true) です。
- OWASP AI ガイドに関する AppSec Podcast エピソードです ([音声](https://www.buzzsprout.com/1730684/12313155-rob-van-der-veer-owasp-ai-security-privacy-guide), [動画](https://www.youtube.com/watch?v=SLdn3AwlCAk&))。
- [September 2023 MLSecOps Podcast](https://mlsecops.com/podcast/a-holistic-approach-to-understanding-the-ai-lifecycle-and-securing-ml-systems-protecting-ai-through-people-processes-technology)、短編をお望みであれば、[13分 AI セキュリティクイックトーク](https://www.brighttalk.com/webcast/19697/586526) をご覧ください。

モデル攻撃の概要:

- [ENISA ML threats and countermeasures 2021](https://www.enisa.europa.eu/publications/securing-machine-learning-algorithms)
- [MITRE ATLAS framework for AI threats](https://atlas.mitre.org/)
- [ETSI SAI Problem statement Section 6](https://www.etsi.org/committee/1640-sai#)
- [Microsoft AI failure modes](https://docs.microsoft.com/en-us/security/failure-modes-in-machine-learning)
- [NIST](https://csrc.nist.gov/pubs/ai/100/2/e2023/final)
- [OWASP ML top 10](https://mltop10.info/)
- [OWASP LLM top 10](https://llmtop10.com/)
- [BIML](https://berryvilleiml.com/taxonomy/)
- [AVID AI Vulnerability database](https://avidml.org/)

その他:

- [ENISA AI security standard discussion](https://www.enisa.europa.eu/publications/cybersecurity-of-ai-and-standardisation)
- [ENISA's multilayer AI security framework](https://www.enisa.europa.eu/publications/multilayer-framework-for-good-cybersecurity-practices-for-ai)
- [Alan Turing institute's AI standards hub](https://aistandardshub.org)
- [Microsoft/MITRE tooling for ML teams](https://www.mitre.org/news-insights/news-release/microsoft-and-mitre-create-tool-help-security-teams-prepare-attacks?sf175190906=1)
- [Google's Secure AI Framework](https://blog.google/technology/safety-security/introducing-googles-secure-ai-framework/)
- [NIST AI Risk Management Framework 1.0](https://doi.org/10.6028/NIST.AI.100-1)
- [NIST threat taxonomy](https://csrc.nist.gov/publications/detail/white-paper/2023/03/08/adversarial-machine-learning-taxonomy-and-terminology/draft)
- [NISTIR 8269 - A Taxonomy and Terminology of Adversarial Machine Learning](https://csrc.nist.rip/external/nvlpubs.nist.gov/nistpubs/ir/2019/NIST.IR.8269-draft.pdf)
- [PLOT4ai threat library](https://plot4.ai/library)
- [ETSI GR SAI 002 V 1.1.1 Securing Artificial Intelligence (SAI) – Data Supply Chain Security](https://www.etsi.org/deliver/etsi_gr/SAI/001_099/002/01.01.01_60/gr_SAI002v010101p.pdf)
- [ISO/IEC 20547-4 Big data security](https://www.iso.org/standard/71278.html)
- [IEEE 2813 Big Data Business Security Risk Assessment](https://standards.ieee.org/ieee/2813/7535/)
- [OECD AI Incidents Monitor (AIM)](https://oecd.ai/en/incidents) AIM は AI インシデントを文書化し、方針作成者、AI 実務者、すべての利害関係者が AI リスクを具体化するインシデントやハザードについて貴重な洞察を得るのに役立ちます
