---
title: AI セキュリティ概要
weight: 1
---
## 要旨 - AI セキュリティをどのように対処するか？
> このイニシアチブについての詳細、貢献や参加の方法については [ホーム](https://owaspai.org/) をご覧ください。
このページには AI セキュリティの概要があり、次のページでは主要なコンテンツである AI に対するセキュリティ脅威とそのコントロールの詳細を提供します。各ページの下部または左サイドバーでページを移動できます。右サイドバーにはページのさまざまなセクションを表示します。小さい画面ではメニューから移動できます。
>カテゴリ: ディスカッション
>Permalink: https://owaspai.org/goto/summary/

AI は強力なパフォーマンス向上をもたらしますが、悪意のある者が利用できる攻撃対象領域も拡大します。そのため、潜在的な脅威と、ユースケースごとにどの脅威を優先するかを明確に理解して、AI アプリケーションに取り組むことが不可欠です。標準とガバナンスは AI 機能を活用する個々の事業体にとってこのプロセスの指針となります。

- **AI ガバナンス** を導入します。
- **セキュリティと開発プラクティスを拡張** して、データサイエンス活動を含め、特にエンジニアリング環境を保護し合理化します。
- AI の特殊性を理解することで、**通常のアプリケーションとシステムのセキュリティを向上** します。たとえば、モデルパラメータは保護が必要であり、モデルへのアクセスは監視してレート制限する必要があります。
- 権限を最小限に抑え、ガードレールや人間の監視などの監視を追加して、AI の **影響を制限** します。
- モデル攻撃を理解することによって **データサイエンスにおける対策** を行います。たとえば、データ品質保証、大規模なトレーニングセット、一般的な摂動攻撃の検出、入力フィルタリングなど。

## 脅威の概要
>カテゴリ: ディスカッション
>Permalink: https://owaspai.org/goto/threatsoverview/

### 脅威モデル
私たちは三つのタイプの脅威を区別します:
1. 開発時 (データを取得および準備し、モデルをトレーニング/取得するとき)
2. モデルの使用 (入力の提供と出力の読み取り) を通じて
3. 実行時 (本番環境) にシステムへの攻撃によって

AI では 6 つのタイプの影響を区別します:
1. トレーニングデータやテストデータの機密性
2. モデル知的財産 (_モデルパラメータ_ やそれにつながるプロセスとデータ) の機密性
3. 入力データの機密性
4. モデル動作の完全性 (モデルが望ましくない動作をするように操作されていない)
5. モデルの可用性
6. AI 固有ではない資産の機密性、完全性、可用性

このような影響をもたらす脅威はさまざまな攻撃対象領域を使用します。たとえば、トレーニングデータの機密性は開発期間中にデータベースにハッキングすることで侵害される可能性がありますが、特定の個人のデータを入力して、モデル出力の詳細を見るだけで、その個人がトレーニングデータにあるかどうかを知ることができる _メンバーシップ推論攻撃_ によって漏洩する可能性もあります。

この図では脅威を矢印で示しています。各脅威には特定の影響があり、Impact legend を参照する文字で示されています。コントロールの概要のセクションには、この図にコントロールのグループを追加したものがあります。
![AI Security Threats](https://raw.githubusercontent.com/OWASP/www-project-ai-security-and-privacy-guide/main/content/ai_exchange/static/images/threats.png)

### <a name="ai-security-matrix">AI セキュリティマトリクス</a>
>カテゴリ: ディスカッション
>Permalink: https://owaspai.org/goto/aisecuritymatrix/

以下の AI セキュリティマトリクス (クリックで拡大) は、すべての脅威とリスクを、タイプと影響の順に示しています。
[![](https://raw.githubusercontent.com/OWASP/www-project-ai-security-and-privacy-guide/main/assets/images/OwaspAIsecuritymatix.png)](https://raw.githubusercontent.com/OWASP/www-project-ai-security-and-privacy-guide/main/assets/images/OwaspAIsecuritymatix.png)

## コントロールの概要
>カテゴリ: ディスカッション
>Permalink: https://owaspai.org/goto/controlsoverview/

### 脅威モデルとコントロール - 全般
下図は AI Exchange のコントロールをグループに分け、これらのグループを対応する脅威とともに適切なライフサイクルに配置したものです。
![AI Security Threats and controls](https://raw.githubusercontent.com/OWASP/www-project-ai-security-and-privacy-guide/main/content/ai_exchange/static/images/threatscontrols.png)
コントロールのグループは AI セキュリティをどのように対処するかをまとめたものです (コントロールは大文字です)。
1. **AI ガバナンス**: AI リスクに対するガバナンスプロセスを導入し、情報セキュリティとソフトウェアライフサイクルのプロセスに AI を組み込みます。
   >([AIPROGRAM](1_general_controls.md#AIPROGRAM), [SECPROGRAM](1_general_controls.md#SECPROGRAM), [DEVPROGRAM](1_general_controls.md#DEVPROGRAM), [SECDEVPROGRAM](1_general_controls.md#SECDEVPROGRAM), [CHECKCOMPLIANCE](1_general_controls.md#CHECKCOMPLIANCE), [SECEDUCATE](1_general_controls.md#SECEDUCATE))
2. AI システムは IT システムであるため、従来の **技術的な IT セキュリティコントロール** を適用します。
    - 2a **標準** 的な従来の IT セキュリティコントロール (15408, ASVS, OpenCRE, ISO 27001 Annex A, NIST SP800-53 など) を完全な AI システムに適用し、新たな AI 固有の資産を忘れないようにします。
      - 開発時: モデルとデータの保存、モデルとデータのサプライチェーン、データサイエンスの文書化
        >([DEVDATAPROTECT](3_development_time_threats.md#DEVDATAPROTECT), [DEVSECURITY](3_development_time_threats.md#DEVSECURITY), [SEGREGATEDATA](3_development_time_threats.md#SEGREGATEDATA), [SUPPLYCHAINMANAGE](3_development_time_threats.md#SUPPLYCHAINMANAGE), [DISCRETE](1_general_controls.md#DISCRETE))
      - 実行時: モデルの保存、モデルの使用、プラグイン、モデルの入出力
        >([RUNTIMEMODELINTEGRITY](4_runtime_application_security_threats.md#RUNTIMEMODELINTEGRITY), [RUNTIMEMODELIOINTEGRITY](4_runtime_application_security_threats.md#RUNTIMEMODELIOINTEGRITY), [RUNTIMEMODELCONFIDENTIALITY](4_runtime_application_security_threats.md#RUNTIMEMODELCONFIDENTIALITY), [MODELINPUTCONFIDENTIALITY](4_runtime_application_security_threats.md#MODELINPUTCONFIDENTIALITY), [ENCODEMODELOUTPUT](4_runtime_application_security_threats.md#ENCODEMODELOUTPUT), [LIMITRESOURCES](2_threats_through_use.md#LIMITRESOURCES))
    - 2b 従来の IT セキュリティコントロールを **適応** して、AI により適したものにします (どの使用パターンを監視するかなど)。
      >([MONITORUSE](2_threats_through_use.md#MONITORUSE), [MODELACCESSCONTROL](2_threats_through_use.md#MODELACCESSCONTROL), [RATELIMIT](2_threats_through_use.md#RATELIMIT))
    - 2c **新規** の IT セキュリティコントロールを採用します。
      >([CONFCOMPUTE](3_development_time_threats.md#CONFCOMPUTE), [MODELOBFUSCATION](4_runtime_application_security_threats.md#MODELOBFUSCATION), [PROMPTINPUTVALIDATION](4_runtime_application_security_threats.md#PROMPTINPUTVALIDATION), [INPUTSEGREGATION](4_runtime_application_security_threats.md#INPUTSEGREGATION))
3. データサイエンティストはリスクベースの **データサイエンスセキュリティコントロール** を適用します。
    - 3a モデル開発時の開発時コントロール
      >([FEDERATEDLEARNING](3_development_time_threats.md#FEDERATEDLEARNING), [CONTINUOUSVALIDATION](1_general_controls.md#CONTINUOUSVALIDATION), [UNWANTEDBIASTESTING](1_general_controls.md#UNWANTEDBIASTESTING), [EVASIONROBUSTMODEL](2_threats_through_use.md#EVASIONROBUSTMODEL), [POISONROBUSTMODEL](3_development_time_threats.md#POISONROBUSTMODEL), [TRAINADVERSARIAL](2_threats_through_use.md#TRAINADVERSARIAL), [TRAINDATADISTORTION](3_development_time_threats.md#TRAINDATADISTORTION), [ADVERSARIALROBUSTDISTILLATION](2_threats_through_use.md#ADVERSARIALROBUSTDISTILLATION), [MODELENSEMBLE](3_development_time_threats.md#MODELENSEMBLE), [MORETRAINDATA](3_development_time_threats.md#MORETRAINDATA), [SMALLMODEL](2_threats_through_use.md#SMALLMODEL), [DATAQUALITYCONTROL](3_development_time_threats.md#DATAQUALITYCONTROL))
    - 3b 攻撃をフィルタして検出するための実行時コントロール
      >([DETECTODDINPUT](2_threats_through_use.md#DETECTODDINPUT), [DETECTADVERSARIALINPUT](2_threats_through_use.md#DETECTADVERSARIALINPUT), [DOSINPUTVALIDATION](2_threats_through_use.md#DOSINPUTVALIDATION), [INPUTDISTORTION](2_threats_through_use.md#INPUTDISTORTION), [FILTERSENSITIVEMODELOUTPUT](2_threats_through_use.md#FILTERSENSITIVEMODELOUTPUT), [OBSCURECONFIDENCE](2_threats_through_use.md#OBSCURECONFIDENCE))
4. **データを最小限に抑える:** 保存時および転送時のデータ量、保存時間を開発時、実行時に制限します。
   >([DATAMINIMIZE](1_general_controls.md#DATAMINIMIZE), [ALLOWEDDATA](1_general_controls.md#ALLOWEDDATA), [SHORTRETAIN](1_general_controls.md#SHORTRETAIN), [OBFUSCATETRAININGDATA](1_general_controls.md#OBFUSCATETRAININGDATA))
5. モデルが間違いや操作によって望ましくない方法で動作する可能性があるため、**動作への影響を制御** します。
   >([OVERSIGHT](1_general_controls.md#OVERSIGHT), [LEASTMODELPRIVILEGE](1_general_controls.md#LEASTMODELPRIVILEGE), [AITRANSPARENCY](1_general_controls.md#AITRANSPARENCY), [EXPLAINABILITY](1_general_controls.md#EXPLAINABILITY), [CONTINUOUSVALIDATION](1_general_controls.md#CONTINUOUSVALIDATION), [UNWANTEDBIASTESTING](1_general_controls.md#UNWANTEDBIASTESTING))


すべての脅威とコントロールについては AI Exchange の詳細なコンテンツで説明します。

### 脅威モデルとコントロール - 生成 AI をトレーニング/ファインチューニング
下図は、**トレーニングやファインチューニング** が組織によって行われる状況においての、生成 AI への脅威とコントロールにのみ制限しています (注: これはコストが高く、専門知識が必要であることを考慮すると、あまり一般的ではありません)。

![AI Security Threats and controls - GenAI trained or fine tuned](https://raw.githubusercontent.com/OWASP/www-project-ai-security-and-privacy-guide/main/content/ai_exchange/static/images/threatscontrols-genainotready.png)

### 脅威モデルとコントロール - 生成 AI を現状のまま <a name="threat-model-with-controls---genai-as-is"></a>
下図は、モデルが組織によって **現状のまま** 使用される生成 AI への脅威とコントロールにのみ制限しています。プロバイダ (OpenAI など) がトレーニングやファインチューニングを行っています。そのため、いくつかの脅威はモデルプロバイダの責任です (機密データや著作権があるデータ、プロバイダでの操作)。とはいえ、モデルを使用する組織はこれらのリスクを考慮し、プロバイダからその保証を得る必要があります。

多くの状況では、現状のままのモデルが外部にホストされるため、セキュリティは、セキュリティ構成を含め、サプライヤがデータをどのように処理するかによって決まります。API はどのように保護されていますか？仮想プライベートクラウドとは何ですか？外部モデル全体ですか、それとも API だけですか？鍵管理は？データ保持は？ログ記録は？そのモデルは機密性の高い入力データを送信することでサードパーティのソースに接触しますか？

![AI Security Threats and controls - GenAI as-is](https://raw.githubusercontent.com/OWASP/www-project-ai-security-and-privacy-guide/main/content/ai_exchange/static/images/threatscontrols-readymodel.png)


### ナビゲータ図
>カテゴリ: ディスカッション
>Permalink: https://owaspai.org/goto/navigator/

以下のナビゲータ図はすべての脅威、コントロール、リスクとコントロールの種類を含むそれらの関係を示しています。
<!-- {{< callout type="info" >}} -->
  画像をクリックすると、クリック可能なリンクを含む PDF を取得できます。
<!-- {{< /callout >}} -->
[![](https://raw.githubusercontent.com/OWASP/www-project-ai-security-and-privacy-guide/main/assets/images/owaspaioverviewv2.png)](https://github.com/OWASP/www-project-ai-security-and-privacy-guide/raw/main/assets/images/owaspaioverviewpdfv3.pdf)


## このドキュメントについて
>カテゴリ: ディスカッション
>Permalink: https://owaspai.org/goto/about/

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

## <a name="how-to-select-relevant-threats-and-controls-risk-analysis">関連する脅威とコントロールをどのように選択するか？　リスク分析</a>
>カテゴリ: ディスカッション
>Permalink: https://owaspai.org/goto/riskanalysis/

このドキュメントには多くの脅威とコントロールについて説明します。どの脅威があなたに関係し、どのコントロールがあなたの責任となるかは、あなたの状況によって決まります。この選択プロセスは目前のユースケースとアーキテクチャのリスク分析 (またはリスク評価) を通じて実行できます。

1. **リストの特定と推定**: まず、自分の状況に関連する脅威を選択し、影響度と確率を推定します。

    これを行うには、脅威のリストを調べ、_影響 (Impact)_ の説明を使用して該当するかどうかを確認します。たとえば訓練データ内の個人を特定することによる影響は、訓練データが個人を所持していない場合、あなたのケースには適用されません。[ナビゲータ](https://github.com/OWASP/www-project-ai-security-and-privacy-guide/raw/main/assets/images/owaspaioverviewpdfv3.pdf) では影響を紫色で示しています。すべての影響の簡単な概要は [AI セキュリティマトリクス](ai_security_overview.md#ai-security-matrix) でご覧いただけます。

    次に、残りの脅威を確認し、攻撃対象領域を調べて、関連するかどうかを確認します。たとえば、外部モデルを使用しない場合、モデルのサプライチェーンは関連する攻撃対象領域ではなく、関連する脅威でもありません。

    以下の決定手順を使用して、関連する脅威をさらに選択できます。

    訓練データが機密ではない場合、訓練データの機密性の脅威を無視します。特殊なケースとして _メンバーシップ推論_ の脅威があります。この脅威は、ある人物がトレーニングセットの一部であるという **事実** がその人物に関する有害な情報である場合にのみ適用されます。たとえば、トレーニングセットが犯罪者とその経歴で構成され、犯罪歴を予測する場合、そのセットのメンバーシップはその人物が有罪判決を受けた、あるいは犯罪容疑のあることを意味します。

    モデルが生成 AI モデルである場合、回避、モデル反転の脅威を無視します。また、生成 AI モデルが LLM ではない場合、プロンプトインジェクションと安全でない出力処理も無視します。

    モデルが生成 AI モデルではない場合、(直接) プロンプトインジェクションと安全でない出力処理を無視します。

    入力データが機密ではない場合、「入力データの漏洩」を無視します。RAG を使用する場合、取得するデータも入力データとみなします。

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

    モデルの動作に影響を与える脅威 (回避、データポイズニングなど) が残っている場合、攻撃者の動機が何であるかを考慮します。攻撃者はたとえばモデルを妨害することで何を得ることができるでしょうか？自慢するだけでしょうか？不満を持つ従業員なのでしょうか？競合相手でしょうか？攻撃者は回避攻撃やトリガーによるデータポイズニングなど、あまり目立たないモデル動作攻撃によって何を得ることができるでしょうか？攻撃者がモデルを欺くことで利益を得られるシナリオはありますか？回避が興味深く、かつ可能である例としては、スパムメールに特定の単語を追加して、それがスパムメールと認識されないようにすることです。回避が面白くない例としては、患者が皮膚の写真に基づいて皮膚病の診断を受ける場合があります。患者は間違った判断には興味がありませんし、また、通常、患者はなにも制御できません。まあ、皮膚に絵を描くことはできるかもしれませんが。これが患者にとって興味深いかもしれない状況があり、たとえば、(偽装された) 皮膚病が特定のレストランの食事によって引き起こされた場合に補償の対象になります。これは、理論上の脅威が実際の脅威であるかどうかはすべてコンテキストに依存することを示しています。脅威の発生確率と影響、および関連するポリシーに応じて、いくつかの脅威がリスクとして受け入れられることがあります。受け入れられない場合、リスクのレベルはコントロールの強さへの入力になります。たとえば、データポイズニングが攻撃者グループに多大な利益をもたらす可能性がある場合、トレーニングデータは高いレベルで保護する必要があります。

3. **責任を采配する**: 選択した各脅威に対して、対処する責任者を決定します。デフォルトでは、AI システムの構築と配備を行う組織が責任を負いますが、構築と配備は別の組織が行うかもしれませんし、たとえば、モデルをホストしたり、アプリケーションを実行するためのクラウド環境を提供するなど、構築と配備の一部を別の組織に委ねるかもしれません。いくつかの側面では責任を共有します。

    AI システムのコンポーネントがホストされている場合、関連する脅威に対するすべてのコントロールに関する責任をホスティングプロバイダと共有します。これは責任マトリクスなどを使用して、プロバイダと調整する必要があります。コンポーネントにはモデル、モデル拡張、アプリケーション、インフラストラクチャがあります。[現状のままのモデルを使用した脅威モデル](#threat-model-with-controls---genai-as-is) を参照してください。

   特定のリスクがどのように軽減されるかについて外部パーティがオープンにしていない場合は、この情報を要求することを検討してください。これが不明瞭なままの場合は、1) リスクを受け入れるか、2) 独自の軽減策を提供するか、3) サードパーティと関わらないことでリスクを回避するかのいずれかに直面することになります。

4. **外部の責任を検証する:** 他の組織の責任である脅威について、これらの組織が対処しているかどうかを確認します。これにはこれらの脅威に関連するコントロールを含みます。
5. **コントロールの選択**: 次に、自分に関連して自分が責任を負う脅威について、その脅威 (またはその脅威の親セクション) に記載されているさまざまなコントロールと一般的なコントロール (こちらは常に適用されます) を検討します。コントロールを検討する際、その目的を考慮し、それを実装するのに十分重要であると考えるか、およびどの程度まで実施するかを判断します。これはその目的が脅威を緩和する方法と比較した実装コスト、および脅威のリスクレベルによって異なります。もちろん、これらの要素はコントロールを選択する順番にも関わります。最初に最もリスクの高いもの、それから比較的コストの低いコントロール (簡単にできるもの) に着手します。
6. **リファレンスの使用**: コントロールを実装する際、標準へのリファレンスとリンクを考慮します。あなたはこれらの標準の一部を実装しているかもしれませんし、標準の内容がコントロールの実装に役立つかもしれません。
7. **リスクの受け入れ**: 最終的には、実装したコントロールを前提として、それぞれの脅威に関して残存するリスクを受容できる必要があります。
8. **これらのコントロールのさらなる管理** ([SECPROGRAM](1_general_controls.md#SECPROGRAM) 参照) には、継続的な監視、文書化、レポーティング、インシデント対応などがあります。

リスク分析の詳細については、[SECPROGRAM](1_general_controls.md#SECPROGRAM) コントロールを参照してください。

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

習得したい AI トピックスについて、どこで線引きしますか？
AI にはセキュリティリスク以外にもさまざまな種類のリスクがあります。いわゆる _ウサギの穴_ に落ちて、これらの事柄について学びたくなるかもしれません。人々は広い意味で AI に興味を持っています。同時に、これは専門家としての私たちの主要な目標から目をそらすことになりかねません。私たちの主な責任がセキュリティであるならば、最善の戦略はまず AI セキュリティに焦点を当て、その後で他の AI の側面について詳細を学ぶことです。同僚が警戒を怠らないようにするためであっても、私たちが理解するのに役立ちます。
したがって、リーダーや利害関係者はプライバシー、法律、ガバナンスに関する責任を含めて、責任を明確にすることが重要です。そうしないと、セキュリティ担当者は組織のために気を配ることが多いため、あまりに多くの責任 (モデルの正確さなど) を負いすぎて、打ちのめされてしまう傾向にあるかもしれません。

責任ある AI や信頼できる AI にはセキュリティが含まれますが、その逆ではありません。責任ある AI や信頼できる AI にはセキュリティ以外にも多くの側面があり、物事をややこしくしているのですが、これらの各側面はセキュリティと関連しています。わかりやすく説明してみましょう。
- **正確性 (Accuracy)** はその「ビジネス機能」を実行するのに十分に正しいかどうかを指します。不正確であると、(物理的な) 安全性の問題 (運転中に車のトランクが開いてしまうなど) やその他の有害な間違った判断 (ローンの不当な拒否など) などの危害につながる可能性があります。セキュリティとの関連は、ある種の攻撃が望ましくないモデル動作を引き起こすことであり、これは定義上、正確性の問題です。とはいえ、セキュリティの範囲ではそのような攻撃のリスクを軽減することに限定されており、正確なモデルの作成 (トレーニングセットの代表データの選択など) の問題全体を解決するものではありません。
- **安全性 (Safety)** は危害から保護されている、あるいは危害を引き起こす可能性が低い状態を指します。したがって、AI システムの安全性は危害 (一般的に物理的な危害を意味しますが、それに限定されません) のリスクがある場合の正確性のレベルのことであり、さらに (正確性とは別に) それらのリスクを軽減するために設けられたものです。これには正確性を保護するためのセキュリティに加えて、モデルのビジネス機能にとって重要な多くの安全性の対策を含みます。これらはセキュリティ上の理由だけでなく、他の理由 (不適切なトレーニングデータなど) でモデルが安全でない決定を下す可能性があるため、安全性とセキュリティの間で共通する懸念事項であることに注意する必要があります。
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

### <a name="how-about-privacy">プライバシーについてはどうですか？</a>
> カテゴリ: ディスカッション
> Permalink: https://owaspai.org/goto/privacy/

AI プライバシーは二つのパートに分けることができます。

1. このドキュメントの AI セキュリティの脅威とコントロールは (個人) データの機密性と完全性 (モデル反転、トレーニングデータの漏洩など)、およびモデルの動作の完全性に関するものです。
2. GDPR などのプライバシー規制でカバーされる個人の権利に関する脅威とコントロール。これには使用制限、同意、公平性、透明性、データの正確性、訂正/異議申し立て/再確認/アクセスの権利が含まれます。概要については、[OWASP AI ガイドのプライバシーパート](https://owasp.org/www-project-ai-security-and-privacy-guide/) を参照してください。

### 生成 AI (LLM など) についてはどうですか？

はい、生成 AI は現在の AI 変革をリードしており、AI セキュリティの中で最も急速に変化しているサブフィールドです。とはいえ、クレジットスコアリング、不正検出、医療診断、製品推奨、画像認識、予知保全、プロセス制御など、多くの重要なユースケースには他のタイプのアルゴリズム (_予測 AI_ と呼びましょう) が引き続き適用されることを認識することが重要です。このドキュメントでは関連するコンテンツには「生成 AI」のマークを付けています。

重要な注意: セキュリティ脅威の観点からは、生成 AI は他の形式の AI (_予測 AI_) とそれほど違いはありません。生成 AI の脅威とコントロールは一般的な AI と大部分が重複しており、非常によく似ています。とはいえ、一部のリスクは (はるかに) 高くなります。低いものもあります。生成 AI 固有のリスクはごくわずかです。生成 AI と予測 AI ではコントロールカテゴリが大きく異なるものがあり、主にデータサイエンスコントロール (トレーニングセットへのノイズ追加など) です。多くの場合、生成 AI ソリューションはモデルをそのまま使用し、組織によるトレーニングを一切行わず、セキュリティ責任の一部を組織からサプライヤに移します。

LLM による主な新しい脅威は何ですか？
- まず第一に、LLM は脆弱性のあるコードを作成するために使用されたり、攻撃者がマルウェアを作成したり、ハルシネーションによって害を及ぼす可能性があるため、セキュリティに新たな脅威をもたらしますが、AI Exchange の範囲外であり、AI システムへのセキュリティ脅威に焦点を当てています。
- 入力について:
  - プロンプトインジェクションは全く新しい脅威です。攻撃者は細工した命令や、時には隠された命令で、モデルの動作を操作します。
  - また、企業秘密や個人データを含む、大量のデータをプロンプトで送信する組織も新たにあります。
- 出力について: 出力にはインジェクション攻撃を含んだり、機密データや著作権で保護されたデータを含む可能性があるという事実が新たにあります ([著作権](ai_security_overview.md#how-about-copyright) 参照)。
- 過度の依存と過剰な代理権が問題です。私たちは LLM に物事を制御され、LLM がどれほど正しいかを過信し、また、LLM が操作されるリスクを過小評価していることがあります。その結果、攻撃は大きな影響を与えることになります。
- トレーニングについて: トレーニングセットは非常に大きく、公開データに基づいているため、データポイズニングを実行することは容易です。また、汚染された基礎モデルはサプライチェーンの大きな問題でもあります。

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
  #[SECEDUCATE](1_general_controls.md#SECEDUCATE)
- システムに対する脅威をモデル化します:
  #[SECPROGRAM](1_general_controls.md#SECPROGRAM) のリスク分析を参照してください
- 機能性とパフォーマンスだけでなくセキュリティも考慮してシステムを設計します:
  #[AIPROGRAM](1_general_controls.md#AIPROGRAM), #[SECPROGRAM](1_general_controls.md#SECPROGRAM), #[DEVPROGRAM](1_general_controls.md#DEVPROGRAM), #[SECDEVPROGRAM](1_general_controls.md#SECDEVPROGRAM), #[CHECKCOMPLIANCE](1_general_controls.md#CHECKCOMPLIANCE), #[LEASTMODELPRIVILEGE](1_general_controls.md#LEASTMODELPRIVILEGE), #[DISCRETE](1_general_controls.md#DISCRETE), #[OBSCURECONFIDENCE](2_threats_through_use.md#OBSCURECONFIDENCE), #[OVERSIGHT](1_general_controls.md#OVERSIGHT), #[RATELIMIT](2_threats_through_use.md#RATELIMIT), #[DOSINPUTVALIDATION](2_threats_through_use.md#DOSINPUTVALIDATION), #[LIMITRESOURCES](2_threats_through_use.md#LIMITRESOURCES), #[MODELACCESSCONTROL](2_threats_through_use.md#MODELACCESSCONTROL), #[AITRANSPARENCY](1_general_controls.md#AITRANSPARENCY)
- AI モデルを選択する際に、セキュリティの利点とトレードオフを考慮します
  すべての開発時のデータサイエンスコントロール (現在 13), #[EXPLAINABILITY](1_general_controls.md#EXPLAINABILITY)

2. 安全な開発

- サプライチェーンを保護します:
  #[SUPPLYCHAINMANAGE](3_development_time_threats.md#SUPPLYCHAINMANAGE)
- 資産を特定、追跡、保護します:
  #[DEVDATAPROTECT](3_development_time_threats.md#DEVDATAPROTECT), #[DEVSECURITY](3_development_time_threats.md#DEVSECURITY), #[SEGREGATEDATA](3_development_time_threats.md#SEGREGATEDATA), #[CONFCOMPUTE](3_development_time_threats.md#CONFCOMPUTE), #[MODELINPUTCONFIDENTIALITY](4_runtime_application_security_threats.md#MODELINPUTCONFIDENTIALITY), #[RUNTIMEMODELCONFIDENTIALITY](4_runtime_application_security_threats.md#RUNTIMEMODELCONFIDENTIALITY), #[DATAMINIMIZE](1_general_controls.md#DATAMINIMIZE), #[ALLOWEDDATA](1_general_controls.md#ALLOWEDDATA), #[SHORTRETAIN](1_general_controls.md#SHORTRETAIN), #[OBFUSCATETRAININGDATA](1_general_controls.md#OBFUSCATETRAININGDATA) および #[SECPROGRAM](1_general_controls.md#SECPROGRAM) の一部
- データ、モデル、プロンプトを文書化します:
  #[DEVPROGRAM](1_general_controls.md#DEVPROGRAM) の一部
- 技術的負債を管理します:
  #[DEVPROGRAM](1_general_controls.md#DEVPROGRAM) の一部

3. 安全な展開

- インフラストラクチャを保護します:
  #[SECPROGRAM](1_general_controls.md#SECPROGRAM) の一部と「資産を特定、追跡、保護します」を参照してください
- モデルを継続的に保護します:
  #[INPUTDISTORTION](2_threats_through_use.md#INPUTDISTORTION), #[FILTERSENSITIVEMODELOUTPUT](2_threats_through_use.md#FILTERSENSITIVEMODELOUTPUT), #[RUNTIMEMODELIOINTEGRITY](4_runtime_application_security_threats.md#RUNTIMEMODELIOINTEGRITY), #[MODELINPUTCONFIDENTIALITY](4_runtime_application_security_threats.md#MODELINPUTCONFIDENTIALITY), #[PROMPTINPUTVALIDATION](4_runtime_application_security_threats.md#PROMPTINPUTVALIDATION), #[INPUTSEGREGATION](4_runtime_application_security_threats.md#INPUTSEGREGATION)
- インシデント管理手順を策定します:
  #[SECPROGRAM](1_general_controls.md#SECPROGRAM) の一部
- 責任をもって AI をリリースします:
  #[DEVPROGRAM](1_general_controls.md#DEVPROGRAM) の一部
- ユーザーが正しいことを簡単にできるようにします:
  #[SECPROGRAM](1_general_controls.md#SECPROGRAM) の一部

4. 安全な運用と保守

- システムの動作を監視します:
  #[CONTINUOUSVALIDATION](1_general_controls.md#CONTINUOUSVALIDATION), #[UNWANTEDBIASTESTING](1_general_controls.md#UNWANTEDBIASTESTING)
- システムの入力を監視します:
  #[MONITORUSE](2_threats_through_use.md#MONITORUSE), #[DETECTODDINPUT](2_threats_through_use.md#DETECTODDINPUT), #[DETECTADVERSARIALINPUT](2_threats_through_use.md#DETECTADVERSARIALINPUT)
- セキュアバイデザインのアプローチに従ってアップデートを行います:
  #[SECDEVPROGRAM](1_general_controls.md#SECDEVPROGRAM) の一部
- 教訓を収集して共有します:
  #[SECPROGRAM](1_general_controls.md#SECPROGRAM) および #[SECDEVPROGRAM](1_general_controls.md#SECDEVPROGRAM) の一部


### <a name="how-about-copyright">How about copyright?</a>
>Category: discussion  
>Permalink: https://owaspai.org/goto/copyright/

#### Introduction
AI and copyright are two (of many) areas of law and policy, (both public and 
private), that raise complex and often unresolved questions. AI output or generated 
content is not yet protected by US copyright laws. Many other jurisdictions have yet 
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
stakeholders—developers, content creators, and copyright owners alike.

#### Lawsuits Related to AI & Copyright
Recent lawsuits (writing is April 2024) highlight the urgency of these issues. For instance, a class 
action suit filed against Stability AI, Midjourney, and DeviantArt alleges infringement
on the rights of millions of artists by training their tools on web-scraped images2.  
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
Do generative AI models really lookup existing work that may be copyrighted? In essence: no. A Generative AI model does not have sufficient capacity to store all the examples of code or pictures that were in its training set. Instead, during training it extracts patterns about how things work in the data that it sees, and then later, based on those patterns, it generates new content. Parts of this content may show remnants of existing work, but that is more of a coincidence. In essence, a model doesn't recall exact blocks of code, but uses its 'understanding' of coding to create new code. Just like with human beings, this understanding may result in reproducing parts of something you have seen before, but not per se because this was from exact memory. Having said that, this remains a difficult discussion that we also see in the music industry: did a musician come up with a chord sequence because she learned from many songs that this type of sequence works and then coincidentally created something that already existed, or did she copy it exactly from that existing song?

#### Mitigating Risk
Organizations have several key strategies to mitigate the risk of copyright 
infringement in their AI systems. Implementing them early can be much more cost 
effective than fixing at later stages of AI system operations. While each comes with 
certain financial and operating costs, the “hard savings” may result in a positive 
outcome. These may include:  
1. Taking measures to mitigate the output of certain training data. The OWASP AI Exchange covers this through the corresponding threat: [data disclosure through model output](/goto/disclosureuseoutput/).
2. Comprehensive IP Audits: a thorough audit may be used to identify all 
intellectual property related to the AI system as a whole. This does not 
necessarily apply only to data sets but overall source code, systems, 
applications, interfaces and other tech stacks.
3. Clear Legal Framework and Policy: development and enforcement of legal 
policies and procedures for AI use, which ensure they align with current IP 
laws including copyright.
4. Ethics in Data Sourcing: source data ethically, ensuring all date used for 
training the AI models is either created in-house, or obtained with all 
necessary permissions, or is sourced from public domains which provide 
sufficient license for the organization’s intended use.
5. Define AI-Generated Content Ownership: clearly defined ownership of the 
content generated by AI systems, which should include under what conditions
it be used, shared, disseminated.
6. Confidentiality and Trade Secret Protocols: strict protocols will help protect 
confidentiality of the materials while preserving and maintaining trade secret 
status.
7. Training for Employees: training employees on the significance and 
importance of the organization’s AI IP policies along with implications on what
IP infringement may be will help be more risk averse.
8. Compliance Monitoring Systems: an updated and properly utilized monitoring 
system will help check against potential infringements by the AI system.
9. Response Planning for IP Infringement: an active plan will help respond 
quickly and effectively to any potential infringement claims.
10. Additional mitigating factors to consider include seeking licenses and/or warranties 
from AI suppliers regarding the organization’s intended use, as well as all future uses by the AI system. With the 
help of legal counsel the organization should also consider other contractually 
binding obligations on suppliers to cover any potential claims of infringement.


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


## OWASP AI Exchange の参考情報
>カテゴリ: ディスカッション
>Permalink: https://owaspai.org/goto/references/

AI Exchange についてのウェビナーやポッドキャストは [Media ページ](https://owaspai.org/media/) を参照してください。

AI セキュリティ脅威の概要:

- [OWASP LLM top 10](https://llmtop10.com/)
- [ENISA ML threats and countermeasures 2021](https://www.enisa.europa.eu/publications/securing-machine-learning-algorithms)
- [MITRE ATLAS framework for AI threats](https://atlas.mitre.org/)
- [NIST threat taxonomy](https://csrc.nist.gov/publications/detail/white-paper/2023/03/08/adversarial-machine-learning-taxonomy-and-terminology/draft)
- [ETSI SAI Problem statement Section 6](https://www.etsi.org/committee/1640-sai#)
- [Microsoft AI failure modes](https://docs.microsoft.com/en-us/security/failure-modes-in-machine-learning)
- [NIST](https://csrc.nist.gov/pubs/ai/100/2/e2023/final)
- [NISTIR 8269 - A Taxonomy and Terminology of Adversarial Machine Learning](https://csrc.nist.rip/external/nvlpubs.nist.gov/nistpubs/ir/2019/NIST.IR.8269-draft.pdf)
- [OWASP ML top 10](https://mltop10.info/)
- [BIML](https://berryvilleiml.com/taxonomy/)
- [PLOT4ai threat library](https://plot4.ai/library)

AI セキュリティ/プライバシーインシデントの概要:

- [AVID AI Vulnerability database](https://avidml.org/)
- [OECD AI Incidents Monitor (AIM)](https://oecd.ai/en/incidents)

その他:

- [ENISA AI security standard discussion](https://www.enisa.europa.eu/publications/cybersecurity-of-ai-and-standardisation)
- [ENISA's multilayer AI security framework](https://www.enisa.europa.eu/publications/multilayer-framework-for-good-cybersecurity-practices-for-ai)
- [Alan Turing institute's AI standards hub](https://aistandardshub.org)
- [Microsoft/MITRE tooling for ML teams](https://www.mitre.org/news-insights/news-release/microsoft-and-mitre-create-tool-help-security-teams-prepare-attacks?sf175190906=1)
- [Google's Secure AI Framework](https://blog.google/technology/safety-security/introducing-googles-secure-ai-framework/)
- [NIST AI Risk Management Framework 1.0](https://doi.org/10.6028/NIST.AI.100-1)
- [ETSI GR SAI 002 V 1.1.1 Securing Artificial Intelligence (SAI) – Data Supply Chain Security](https://www.etsi.org/deliver/etsi_gr/SAI/001_099/002/01.01.01_60/gr_SAI002v010101p.pdf)
- [ISO/IEC 20547-4 Big data security](https://www.iso.org/standard/71278.html)
- [IEEE 2813 Big Data Business Security Risk Assessment](https://standards.ieee.org/ieee/2813/7535/)
