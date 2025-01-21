---
title: 0. AI セキュリティ概要
weight: 1
---
## 要旨 - AI セキュリティをどのように対処するか？
> このイニシアチブ (OWASP AI Exchange) についての詳細、貢献や参加の方法については [ホーム](https://owaspai.org/) をご覧ください。
>カテゴリ: ディスカッション  
>パーマリンク: https://owaspai.org/goto/summary/

AI はとてつもない好機を与える一方で、セキュリティ脅威などの新たなリスクももたらします。そのため、潜在的な脅威とそれに対するコントロールを明確に理解した上で、AI アプリケーションに取り組むことが不可欠です。簡単に言えば、AI セキュリティに対処するための主な手順は以下のとおりです。

- **AI ガバナンス** を導入します。
- このドキュメントの AI セキュリティ資産、脅威、コントロールを使用して **セキュリティプラクティスを拡張** します。
- AI システムを開発する場合 (独自のモデルをトレーニングしない場合でも):
  - データおよび AI エンジニアリングを従来の **(セキュア) ソフトウェア開発プラクティス** に組み込みます。
  - このドキュメントで説明している脅威を理解して、適切なプロセス **コントロール** と技術的コントロールを適用します。
- AI **サプライヤ** が適切なコントロールを適用していることを確認します。
- データと権限を最小限に抑え、ガードレールや人間の監視などの監視を追加して、AI の **影響を制限** します。

AI システムは、たとえば、大規模言語モデル、線形回帰関数、ルールベースのシステム、統計ベースのルックアップテーブルなどがあることに注意してください。このドキュメント全体を通じて、どのような脅威とコントロールがどのような役割を果たすかが明確になっています。

---

## このドキュメントについて
>カテゴリ: ディスカッション  
>パーマリンク: https://owaspai.org/goto/about/

このページでは AI セキュリティの概要を説明し、次のページでは AI に対するセキュリティの脅威とそれに対するコントロールに関する主要なコンテンツを攻撃対象領域ごとにまとめています。
1. [一般的なコントロール: AI ガバナンスなど](1_general_controls.md)
2. [使用による脅威: 回避攻撃など](2_threats_through_use.md)
3. [開発時の脅威: データポイズニングなど](3_development_time_threats.md)
4. [実行時のセキュリティ脅威: 安全でない出力](4_runtime_application_security_threats.md)

各ページの下部、または左側のサイドバーでページ間を移動できます。右側のサイドバーにはページ上のさまざまなセクションが表示されます。小さな画面ではメニューから移動できます。

ここでいうセキュリティとは認可されていないアクセス、使用、開示、中断、改変、破壊を防止することを意味します。改変には AI モデルの動作を望ましくない方法で操作することが含まれます。

AI Exchange イニシアチブは OWASP により採択されており、[Rob van der Veer](https://www.linkedin.com/in/robvanderveer/) によって起こされました。セキュリティ標準の橋渡し役、[Software Improvement Group](https://www.softwareimprovementgroup.com) のシニアディレクター、AI とセキュリティで 31 年の経験を持ち、AI ライフサイクルに関する ISO/IEC 5338 の主執筆者、OpenCRE の創設者であり、現在は CEN/CENELEC で EU AI 法に関するセキュリティ要件に取り組んでいます。

この資料はオープンソースの継続的デリバリによって常に進化しています。著者グループは 50 人の専門家 (研究者、実務家、ベンダー、データサイエンティストなど) で構成しており、コミュニティの他の人々も意見を述べることができます。[貢献ページ](../contribute.md) を参照してください。
これは EU AI 法、AI セキュリティに関する ISO/IEC 27090、AI プライバシーに関する ISO/IEC 27091、[OWASP ML Top 10](https://mltop10.info/)、[OWASP LLM Top 10](https://llmtop10.com/) などの進行中の主要なイニシアチブへのインプットとして機能し、さらに多くのイニシアチブが世界中で一貫した用語と洞察から恩恵を受けることができます。

このページでは以下について取り上げます。
- 脅威の概要
- 脅威とコントロールのさまざまな概要: マトリックス、周期表、ナビゲータ
- 関連する脅威とコントロールを選択するためのリスク分析
- さまざまなトピックに関する議論 (... についてはどうですか): ヒューリスティックシステム、責任ある AI、プライバシー、生成 AI、NCSC/CISA ガイドライン、著作権
---

## 脅威の概要
>カテゴリ: ディスカッション  
>パーマリンク: https://owaspai.org/goto/threatsoverview/

### 脅威モデル
私たちは三つのタイプの脅威を区別します:
1. 開発時 (データを取得および準備し、モデルをトレーニング/取得するとき)
2. モデルの使用 (入力の提供と出力の読み取り) を通じて
3. 実行時 (本番環境) にシステムへの攻撃によって

AI では、3 つのタイプの攻撃者の目的 (開示、欺瞞、妨害) に対して、6 つのタイプの影響を区別します:
1. 開示: トレーニングデータやテストデータの機密性が損なわれる
2. 開示: モデル知的財産 (_モデルパラメータ_ やそれにつながるプロセスとデータ) の機密性が損なわれる
3. 開示: 入力データの機密性が損なわれる
4. 欺瞞: モデル動作の完全性が損なわれる (モデルが望ましくない動作をするように操作されて欺かれる)
5. 妨害: モデルの可用性が損なわれる (モデルが機能しないか、望ましくない動作をする - 欺くためではなく妨害するため)
6. AI 固有ではない資産の機密性、完全性、可用性

このような影響をもたらす脅威はさまざまな攻撃対象領域を使用します。たとえば、トレーニングデータの機密性は開発期間中にデータベースにハッキングすることで侵害される可能性がありますが、特定の個人のデータを入力して、モデル出力の詳細を見るだけで、その個人がトレーニングデータにあるかどうかを知ることができる _メンバーシップ推論攻撃_ によって漏洩する可能性もあります。

この図では脅威を矢印で示しています。各脅威には特定の影響があり、Impact legend を参照する文字で示されています。コントロールの概要のセクションには、この図にコントロールのグループを追加したものがあります。
[![](https://raw.githubusercontent.com/OWASP/www-project-ai-security-and-privacy-guide/main/content/ai_exchange/static/images/threats.png)](https://raw.githubusercontent.com/OWASP/www-project-ai-security-and-privacy-guide/main/content/ai_exchange/static/images/threats.png)

### <a name="ai-security-matrix">AI セキュリティマトリクス</a>
>カテゴリ: ディスカッション  
>パーマリンク: https://owaspai.org/goto/aisecuritymatrix/

以下の AI セキュリティマトリクス (クリックで拡大) は、すべての脅威とリスクを、タイプと影響の順に示しています。
[![](https://raw.githubusercontent.com/OWASP/www-project-ai-security-and-privacy-guide/main/assets/images/OwaspAIsecuritymatix.png)](https://raw.githubusercontent.com/OWASP/www-project-ai-security-and-privacy-guide/main/assets/images/OwaspAIsecuritymatix.png)

---

## コントロールの概要
>カテゴリ: ディスカッション  
>パーマリンク: https://owaspai.org/goto/controlsoverview/

### 脅威モデルとコントロール - 全般
下図は AI Exchange のコントロールをグループに分け、これらのグループを対応する脅威とともに適切なライフサイクルに配置したものです。
[![](https://raw.githubusercontent.com/OWASP/www-project-ai-security-and-privacy-guide/main/content/ai_exchange/static/images/threatscontrols.png)](https://raw.githubusercontent.com/OWASP/www-project-ai-security-and-privacy-guide/main/content/ai_exchange/static/images/threatscontrols.png)
コントロールのグループは AI セキュリティをどのように対処するかをまとめたものです (コントロールは大文字です)。
1. **AI ガバナンス**: AI リスクに対するガバナンスプロセスを導入し、情報セキュリティとソフトウェアライフサイクルのプロセスに AI を組み込みます。
   >([AIPROGRAM](1_general_controls.md#AIPROGRAM), [SECPROGRAM](1_general_controls.md#SECPROGRAM), [DEVPROGRAM](1_general_controls.md#DEVPROGRAM), [SECDEVPROGRAM](1_general_controls.md#SECDEVPROGRAM), [CHECKCOMPLIANCE](1_general_controls.md#CHECKCOMPLIANCE), [SECEDUCATE](1_general_controls.md#SECEDUCATE))
2. AI システムは IT システムであるため、従来の **技術的な IT セキュリティコントロール** を適用します。
    - 2a **標準** 的な従来の IT セキュリティコントロール (15408, ASVS, OpenCRE, ISO 27001 Annex A, NIST SP800-53 など) を完全な AI システムに適用し、新たな AI 固有の資産を忘れないようにします。
      - 開発時: モデルとデータの保存、モデルとデータのサプライチェーン、データサイエンスの文書化
        >([DEVSECURITY](3_development_time_threats.md#DEVSECURITY), [SEGREGATEDATA](3_development_time_threats.md#SEGREGATEDATA), [SUPPLYCHAINMANAGE](3_development_time_threats.md#SUPPLYCHAINMANAGE), [DISCRETE](1_general_controls.md#DISCRETE))
      - 実行時: モデルの保存、モデルの使用、プラグイン、モデルの入出力
        >([RUNTIMEMODELINTEGRITY](4_runtime_application_security_threats.md#RUNTIMEMODELINTEGRITY), [RUNTIMEMODELIOINTEGRITY](4_runtime_application_security_threats.md#RUNTIMEMODELIOINTEGRITY), [RUNTIMEMODELCONFIDENTIALITY](4_runtime_application_security_threats.md#RUNTIMEMODELCONFIDENTIALITY), [MODELINPUTCONFIDENTIALITY](4_runtime_application_security_threats.md#MODELINPUTCONFIDENTIALITY), [ENCODEMODELOUTPUT](4_runtime_application_security_threats.md#ENCODEMODELOUTPUT), [LIMITRESOURCES](2_threats_through_use.md#LIMITRESOURCES))
    - 2b 従来の IT セキュリティコントロールを **適応** して、AI により適したものにします (どの使用パターンを監視するかなど)。
      >([MONITORUSE](2_threats_through_use.md#MONITORUSE), [MODELACCESSCONTROL](2_threats_through_use.md#MODELACCESSCONTROL), [RATELIMIT](2_threats_through_use.md#RATELIMIT))
    - 2c **新規** の IT セキュリティコントロールを採用します。
      >([CONFCOMPUTE](3_development_time_threats.md#CONFCOMPUTE), [MODELOBFUSCATION](4_runtime_application_security_threats.md#MODELOBFUSCATION), [PROMPTINPUTVALIDATION](2_threats_through_use.md#PROMPTINPUTVALIDATION), [INPUTSEGREGATION](2_threats_through_use.md#INPUTSEGREGATION))
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

[![AI Security Threats and controls - GenAI trained or fine tuned](https://raw.githubusercontent.com/OWASP/www-project-ai-security-and-privacy-guide/main/content/ai_exchange/static/images/threatscontrols-genainotready.png)](https://raw.githubusercontent.com/OWASP/www-project-ai-security-and-privacy-guide/main/content/ai_exchange/static/images/threatscontrols-genainotready.png)

### 脅威モデルとコントロール - 生成 AI を現状のまま <a name="threat-model-with-controls---genai-as-is"></a>
下図は、モデルが組織によって **現状のまま** 使用される生成 AI への脅威とコントロールにのみ制限しています。プロバイダ (OpenAI など) がトレーニングやファインチューニングを行っています。そのため、いくつかの脅威はモデルプロバイダの責任です (機密データや著作権があるデータ、プロバイダでの操作)。とはいえ、モデルを使用する組織はこれらのリスクを考慮し、プロバイダからその保証を得る必要があります。

多くの状況では、現状のままのモデルが外部にホストされるため、セキュリティは、セキュリティ構成を含め、サプライヤがデータをどのように処理するかによって決まります。API はどのように保護されていますか？仮想プライベートクラウドとは何ですか？外部モデル全体ですか、それとも API だけですか？鍵管理は？データ保持は？ログ記録は？そのモデルは機密性の高い入力データを送信することでサードパーティのソースに接触しますか？

[![AI Security Threats and controls - GenAI as-is](https://raw.githubusercontent.com/OWASP/www-project-ai-security-and-privacy-guide/main/content/ai_exchange/static/images/threatscontrols-readymodel.png)](https://raw.githubusercontent.com/OWASP/www-project-ai-security-and-privacy-guide/main/content/ai_exchange/static/images/threatscontrols-readymodel.png)

### <a name="periodic-table-of-ai-security">AI セキュリティの周期表</a>
>カテゴリ: ディスカッション  
>パーマリンク: https://owaspai.org/goto/periodictable/

OWASP AI Exchange によって作成された以下の表は、AI に対するさまざまな脅威と、それに対して使用できるコントロールを示しています。すべての資産、影響、攻撃対象領域について整理しており、AI Exchange ウェブサイトの包括的なカバレッジへのディープリンクを付与しています。
[一般的なガバナンスコントロール](1_general_controls.md#11-general-governance-controls) はすべての脅威に適用されることに注意してください。

<table><thead>
<tr><th>資産と影響</th><th>ライフサイクルと攻撃対象領域</th><th>脅威/リスクのカテゴリ</th><th>コントロール</th></tr>
</thead><tbody>
<tr><td rowspan="7">モデル動作の完全性</td><td rowspan="3">ランタイム - モデル使用 (入力の提供 / 出力の読み取り)</td><td><a href="2_threats_through_use.md#221-direct-prompt-injection">直接的プロンプトインジェクション</a></td><td><a href="1_general_controls.md#13-controls-to-limit-the-effects-of-unwanted-behaviour">望ましくない動作の制限</a>, <a href="2_threats_through_use.md#PROMPTINPUTVALIDATION">入力バリデーション</a>, モデル自体に実装されたさらなるコントロール</td></tr>
<tr>                                         <td><a href="2_threats_through_use.md#222-indirect-prompt-injection">間接的プロンプトインジェクション</a></td><td><a href="1_general_controls.md#13-controls-to-limit-the-effects-of-unwanted-behaviour">望ましくない動作の制限</a>, <a href="2_threats_through_use.md#PROMPTINPUTVALIDATION">入力バリデーション</a>, <a href="2_threats_through_use.md#INPUTSEGREGATION">入力セグリゲーション</a></td></tr>
<tr>                                         <td><a href="2_threats_through_use.md#21-evasion">回避</a> (例: 敵対的事例)</td><td><a href="1_general_controls.md#13-controls-to-limit-the-effects-of-unwanted-behaviour">望ましくない動作の制限</a>, <a href="2_threats_through_use.md#MONITORUSE">監視</a>, <a href="2_threats_through_use.md#RATELIMIT">レート制限</a>, <a href="2_threats_through_use.md#MODELACCESSCONTROL">モデルアクセス制御</a> 追補:<br><br><a href="2_threats_through_use.md#DETECTODDINPUT">奇妙な入力の検出</a>, <a href="2_threats_through_use.md#DETECTADVERSARIALINPUT">敵対的入力の検出</a>, <a href="2_threats_through_use.md#EVASIONROBUSTMODEL">回避ロバストモデル</a>, <a href="2_threats_through_use.md#TRAINADVERSARIAL">敵対的トレーニング</a>, <a href="2_threats_through_use.md#INPUTDISTORTION">入力の歪曲</a>, <a href="2_threats_through_use.md#ADVERSARIALROBUSTDISTILLATION">敵対的ロバスト蒸留</a></td></tr>
<tr>                                         <td>ランタイム - デプロイされるモデルへの侵入</td><td><a href="4_runtime_application_security_threats.md#42-runtime-model-poisoning-manipulating-the-model-itself-or-its-inputoutput-logic">実行時のモデルポイズニング</a> (リプログラミング)</td><td><a href="1_general_controls.md#13-controls-to-limit-the-effects-of-unwanted-behaviour">望ましくない動作の制限</a>, <a href="4_runtime_application_security_threats.md#RUNTIMEMODELINTEGRITY">実行時のモデルの完全性</a>, <a href="4_runtime_application_security_threats.md#RUNTIMEMODELIOINTEGRITY">実行時のモデル入出力の完全性</a></td></tr>
<tr><td rowspan="2">開発時 - エンジニアリング環境</td><td><a href="3_development_time_threats.md#312-development-time-model-poisoning">開発環境のモデルポイズニング</a></td><td><a href="1_general_controls.md#13-controls-to-limit-the-effects-of-unwanted-behaviour">望ましくない動作の制限</a>, <a href="3_development_time_threats.md#DEVSECURITY">開発環境のセキュリティ</a>, <a href="3_development_time_threats.md#SEGREGATEDATA">データセグリゲーション</a>, <a href="3_development_time_threats.md#FEDERATEDLEARNING">連合学習</a>, <a href="3_development_time_threats.md#SUPPLYCHAINMANAGE">サプライチェーンマネジメント</a> 追補:<br><br><a href="3_development_time_threats.md#MODELENSEMBLE">モデルアンサンブル</a></td></tr>
<tr>                                         <td><a href="3_development_time_threats.md#311-data-poisoning">トレーニングデータやファインチューニングデータのデータポイズニング</a></td><td><a href="1_general_controls.md#13-controls-to-limit-the-effects-of-unwanted-behaviour">望ましくない動作の制限</a>, <a href="3_development_time_threats.md#DEVSECURITY">開発環境のセキュリティ</a>, <a href="3_development_time_threats.md#SEGREGATEDATA">データセグリゲーション</a>, <a href="3_development_time_threats.md#FEDERATEDLEARNING">連合学習</a>, <a href="3_development_time_threats.md#SUPPLYCHAINMANAGE">サプライチェーンマネジメント</a> 追補:<br><br><a href="3_development_time_threats.md#MODELENSEMBLE">モデルアンサンブル</a> 追補:<br><br><a href="3_development_time_threats.md#MORETRAINDATA">トレーニングデータの増強</a>, <a href="3_development_time_threats.md#DATAQUALITYCONTROL">データ品質コントロール</a>, <a href="3_development_time_threats.md#TRAINDATADISTORTION">トレーニングデータの歪曲</a>, <a href="3_development_time_threats.md#POISONROBUSTMODEL">ポイズンロバストモデル</a>, <a href="2_threats_through_use.md#TRAINADVERSARIAL">敵対的トレーニング</a></td></tr>
<tr><td>開発時 - サプライチェーン</td><td><a href="3_development_time_threats.md#313-supply-chain-model-poisoning">サプライチェーンのモデルポイズニング</a></td><td><a href="1_general_controls.md#13-controls-to-limit-the-effects-of-unwanted-behaviour">望ましくない動作の制限</a>,<br>サプライヤ: <a href="3_development_time_threats.md#DEVSECURITY">開発環境のセキュリティ</a>, <a href="3_development_time_threats.md#SEGREGATEDATA">データセグリゲーション</a>, <a href="3_development_time_threats.md#FEDERATEDLEARNING">連合学習</a><br><br>プロデューサー: <a href="3_development_time_threats.md#SUPPLYCHAINMANAGE">サプライチェーンマネジメント</a> 追補:<br><br><a href="3_development_time_threats.md#MODELENSEMBLE">モデルアンサンブル</a></td></tr>
<tr><td rowspan="3">トレーニングデータの機密性</td><td rowspan="2">ランタイム - モデル使用</td><td><a href="2_threats_through_use.md#231-sensitive-data-output-from-model">モデル出力でのデータ開示</a></td><td><a href="1_general_controls.md#12-general-controls-for-sensitive-data-limitation">機密データ制限</a> (データの最小化, 短期保持, トレーニングデータの難読化) 追補:<br><br><a href="2_threats_through_use.md#MONITORUSE">監視</a>, <a href="2_threats_through_use.md#RATELIMIT">レート制限</a>, <a href="2_threats_through_use.md#MODELACCESSCONTROL">モデルアクセス制御</a> 追補:<br><br><a href="2_threats_through_use.md#FILTERSENSITIVEMODELOUTPUT">機密性の高いモデル出力のフィルタ</a></td></tr>
<tr><td><a href="2_threats_through_use.md#232-model-inversion-and-membership-inference">モデル反転とメンバーシップ推論</a></td><td><a href="1_general_controls.md#12-general-controls-for-sensitive-data-limitation">機密データ制限</a> (データの最小化, 短期保持, トレーニングデータの難読化) 追補:<br><br><a href="2_threats_through_use.md#MONITORUSE">監視</a>, <a href="2_threats_through_use.md#RATELIMIT">レート制限</a>, <a href="2_threats_through_use.md#MODELACCESSCONTROL">モデルアクセス制御</a> 追加:<br><br><a href="2_threats_through_use.md#OBSCURECONFIDENCE">曖昧な信頼性</a>, <a href="2_threats_through_use.md#SMALLMODEL">スモールモデル</a></td></tr>
<tr><td>開発時 - エンジニアリング環境</td><td><a href="3_development_time_threats.md#321-development-time-data-leak">トレーニングデータの漏洩</a></td><td><a href="1_general_controls.md#12-general-controls-for-sensitive-data-limitation">機密データ制限</a> (データの最小化, 短期保持, トレーニングデータの難読化) 追補:<br><br><a href="3_development_time_threats.md#DEVSECURITY">開発環境のセキュリティ</a>, <a href="3_development_time_threats.md#SEGREGATEDATA">データセグリゲーション</a>, <a href="3_development_time_threats.md#FEDERATEDLEARNING">連合学習</a></td></tr>
<tr><td rowspan="3">モデルの機密性</td><td>ランタイム - モデル使用</td><td><a href="2_threats_through_use.md#24-model-theft-through-use">使用によるモデル盗用</a> (入出力ハーベスティング)</td><td><a href="2_threats_through_use.md#MONITORUSE">監視</a>, <a href="2_threats_through_use.md#RATELIMIT">レート制限</a>, <a href="2_threats_through_use.md#MODELACCESSCONTROL">モデルアクセス制御</a></td></tr>
<tr><td>ランタイム - デプロイされるモデルへの侵入</td><td><a href="4_runtime_application_security_threats.md#43-direct-runtime-model-theft">直接的な実行時のモデル盗用</a></td><td><a href="4_runtime_application_security_threats.md#RUNTIMEMODELCONFIDENTIALITY">ランタイムモデルの機密性</a>, <a href="4_runtime_application_security_threats.md#MODELOBFUSCATION">モデルの難読化</a></td></tr>
<tr><td>開発時 - エンジニアリング環境</td><td><a href="3_development_time_threats.md#322-model-theft-through-development-time-model-parameter-leak">開発時のモデル盗用</a></td><td><a href="3_development_time_threats.md#DEVSECURITY">開発環境のセキュリティ</a>, <a href="3_development_time_threats.md#SEGREGATEDATA">データセグリゲーション</a>, <a href="3_development_time_threats.md#FEDERATEDLEARNING">連合学習</a></td></tr>
<tr><td>モデル動作の可用性</td><td>モデル使用</td><td><a href="2_threats_through_use.md#25-failure-or-malfunction-of-ai-specific-elements-through-use">モデルサービス拒否</a> (モデルリソースの枯渇)</td><td><a href="2_threats_through_use.md#MONITORUSE">監視</a>, <a href="2_threats_through_use.md#RATELIMIT">レート制限</a>, <a href="2_threats_through_use.md#MODELACCESSCONTROL">モデルアクセス制御</a> 追補:<br><br><a href="2_threats_through_use.md#DOSINPUTVALIDATION">サービス拒否の入力バリデーション</a>, <a href="2_threats_through_use.md#LIMITRESOURCES">リソースの制限</a></td></tr>
<tr><td>モデル入力データの機密性</td><td>ランタイム - すべての IT</td><td><a href="4_runtime_application_security_threats.md#45-leak-sensitive-input-data">モデル入力の漏洩</a></td><td><a href="4_runtime_application_security_threats.md#MODELINPUTCONFIDENTIALITY">モデル入力の機密性</a></td></tr>
<tr><td>任意の資産, CIA</td><td>ランタイム - すべての IT</td><td><a href="4_runtime_application_security_threats.md#44-insecure-output-handling">インジェクションを含むモデル出力</a></td><td><a href="4_runtime_application_security_threats.md#ENCODEMODELOUTPUT">モデル出力のエンコード</a></td></tr>
<tr><td>任意の資産, CIA</td><td>ランタイム - すべての IT</td><td>従来の資産に対する従来のランタイムセキュリティ攻撃</td><td>従来のランタイムセキュリティコントロール</td></tr>
<tr><td>任意の資産, CIA</td><td>ランタイム - すべての IT</td><td>従来のサプライチェーンの従来の攻撃</td><td>従来のサプライチェーンマネジメントコントロール</td></tr>
</tbody></table>


### ナビゲータ図
>カテゴリ: ディスカッション  
>パーマリンク: https://owaspai.org/goto/navigator/

以下のナビゲータ図はすべての脅威、コントロール、リスクとコントロールの種類を含むそれらの関係を示しています。
<!-- {{< callout type="info" >}} -->
  画像をクリックすると、クリック可能なリンクを含む PDF を取得できます。
<!-- {{< /callout >}} -->
[![](https://raw.githubusercontent.com/OWASP/www-project-ai-security-and-privacy-guide/main/assets/images/owaspaioverviewv2.png)](https://github.com/OWASP/www-project-ai-security-and-privacy-guide/raw/main/assets/images/owaspaioverviewpdfv3.pdf)

---

## <a name="how-to-select-relevant-threats-and-controls-risk-analysis">関連する脅威とコントロールをどのように選択するか？　リスク分析</a>
>カテゴリ: ディスカッション  
>パーマリンク: https://owaspai.org/goto/riskanalysis/

このドキュメントには多くの脅威とコントロールを記載しています。状況や AI の使い方によって、どの脅威がどの程度関連しているか、どのコントロールが誰の責任であるかが決まります。この選択プロセスはユースケースとアーキテクチャに照らして、リスク分析 (またはリスク評価) を通じて実行できます。

**リスクマネジメント入門**  
組織はリスクをいくつかの主要な領域に分類します。戦略、運用、財務、コンプライアンス、評判、テクノロジ、環境、社会、ガバナンス (ESG) です。脅威は一つ以上の脆弱性を悪用するとリスクになります。このリソースで説明しているように、AI の脅威は複数のリスク領域にわたって大きな影響を及ぼす可能性があります。たとえば、AI システムに対する敵対的攻撃は、運用の中断、財務モデルの歪曲、コンプライアンスの問題を引き起こす可能性があります。潜在的な影響の概要については [AI セキュリティマトリクス](ai_security_overview.md#ai-security-matrix) を参照してください。

AI システムの一般的なリスクマネジメントは、通常、AI ガバナンス ([AIPROGRAM](1_general_controls.md#AIPROGRAM) を参照) によって推進され、関連する AI システムによるリスクとそれらのシステムに対するリスクの両方を含みます。セキュリティリスク評価は、通常、セキュリティマネジメントシステム ([SECPROGRAM](1_general_controls.md#SECPROGRAM) を参照) によって推進され、このシステムは、AI 資産、AI 脅威、AI システムを考慮に含めることが求められます (これらが対応するリポジトリに追加されている場合)。

組織は一般的に ISO 31000 または ISO 23894 などの類似の規格に基づくリスクマネジメントフレームワークを採用することがよくあります。これらのフレームワークは下記の四つの主要なステップを通じてリスク管理のプロセスをガイドします。

1. **リスクの特定**: 組織に影響を及ぼす可能性のある潜在的なリスク (脅威) を認識します。潜在的なリスク (脅威) を特定するには「使用による脅威」セクションを参照してください。
2. **発生可能性と影響度の推定によるリスクの評価**: リスクの深刻度を判断するには、リスクが発生する可能性を評価し、リスクが顕在化した場合の潜在的な影響を評価する必要があります。発生可能性と影響度を組み合わせて、リスクの全体的な深刻度を測定します。これは一般的にヒートマップの形で示されます。詳細については以下を参照してください。
3. **すべきことの決定 (リスク処置)**: リスクに対処するための適切な戦略を選択します。これらの戦略には、リスクの軽減、移転、回避、受容があります。詳細については以下を参照してください。
4. **リスクコミュニケーションとモニタリング**: リスク情報を利害関係者と定期的に共有し、リスクマネジメント活動に対する意識と支援を確保します。効果的なリスク処置を確実に適用します。これには、リスクとその属性 (深刻度、処置計画、オーナーシップ、ステータスなど) の包括的なリストであるリスク登録簿が必要です。詳細については以下を参照してください。

リスクマネジメントの手順を一つずつ見てきましょう。

### 1. リスクの特定
組織に影響を及ぼす可能性のある潜在的なリスク (脅威) を選択するには、該当する脅威の技術的およびビジネス的な評価が必要です。これを行う方法については、リスクの影響の種類ごとに以下で説明します。

**望ましくないモデルの動作**

  モデルの動作に関しては、このドキュメントのスコープがセキュリティであるため、攻撃者による操作に焦点を当てています。その他の望ましくない動作の原因には一般的な不正確さ (ハルシネーションなど) や特定のグループに関する望ましくない偏見 (差別) があります。

  This will always be an applicable threat, independent of your situation, although the risk level may sometimes be accepted - see below.

  Which means that you always need to have in place:
  - [General governance controls](/goto/governancecontrols/) (e.g. having an inventory of AI use and some control over it)
  - [Controls to limit effects of unwanted model behaviour](/goto/limitunwanted/) (e.g. human oversight)

  Is the model GenAI (e.g. a Large Language Model)? 
  - Prevent [prompt injection](/goto/directpromptinjection/) (mostly done by the model supplier) in case untrusted input goes directly into the model, and it is important that the model follows its policy instructions about how it communicates. Mostly this is the case if model input is from end users and output also goes straight to end users, who could show that the model can misbehave (e.g. be politically incorrect), which can lead to reputation damage. 
  - Prevent [indirect prompt injection](/goto/indirectpromptinjection/), in case untrusted input goes somehow into the prompt e.g. you retrieve somebody's resume and include it in a prompt.

  Sometimes model training and running the model is deferred to a supplier. For generative AI, training is mostly performed by an external supplier given the cost of typically millions of dollars. Finetuning of generative AI is also not often performed by organizations given the cost of compute and the complexity involved. Some GenAI models can be obtained and run at your own premises. The reasons to do this can be lower cost (if is is an open source model), and the fact that sensitive input information does not have to be sent externally. A reason to use an externally hosted GenAI model can be the quality of the model.
    
  Who trains/finetunes the model?
  - The supplier: you need to prevent [obtaining a poisoned model](/goto/transferlearningattack/) by proper supply chain mangement (selecting a proper supplier and making sure you use the actual model), including assuring that: the supplier prevents development-time model poisoning including data poisoning and obtaining poisoned data. If the remaining risk for data poisoning cannot be accepted, performing post-training countermeasures can be an option - see [POISONROBUSTMODEL](/goto/poisonrobustmodel/).
  - You: you need to prevent [development-time model poisoning](/goto/modelpoison/) which includes model poisoning, data poisoning and obtaining poisoned data
 
  If you use RAG (Retrieval Augmented Generation using GenAI), then your retrieval repository plays a role in determining the model behaviour.This means:
  - You need to prevent [data poisoning](/goto/datapoison/) of your retrieval repository, which includes preventing that it contains externally obtained poisoned data.

  Who runs the model?
  - The supplier: make sure the supplier prevents [runtime model poisoning](/goto/runtimemodelpoison/) just like any supplier who you expect to protect the running application from manipulation
  - You: You need to prevent [runtime model poisoning](/goto/runtimemodelpoison/)

  Is the model predictive AI?
  - Prevent an [evasion attack](/goto/evasion/) in which a user tries to fool the model into a wrong decision. Here, the level of risk is an important aspect to evaluate - see below. The risk of an evasion attack may be acceptable.
    
  In order to assess the level of risk for unwanted model behaviour through manipulation, consider what the motivation of an attacker could be. What could an attacker gain by for example sabotaging your model? Just a claim to fame? Could it be a disgruntled employee? Maybe a competitor? What could an attacker gain by a less conspicuous model behaviour attack, like an evasion attack or data poisoning with a trigger? Is there a scenario where an attacker benefits from fooling the model? An example where evasion IS interesting and possible: adding certain words in a spam email so that it is not recognized as such. An example where evasion is not interesting is when a patient gets a skin disease diagnosis based on a picture of the skin. The patient has no interest in a wrong decision, and also the patient typically has no control - well maybe by painting the skin. There are situations in which this CAN be of interest for the patient, for example to be eligible for compensation in case the (faked) skin disease was caused by certain restaurant food. This demonstrates that it all depends on the context whether a theoretical threat is a real threat or not. Depending on the probability and impact of the threats, and on the relevant policies, some threats may be accepted as risk. When not accepted, the level of risk is input to the strength of the controls. For example: if data poisoning can lead to substantial benefit for a group of attackers, then the training data needs to be get a high level of protection.

 **Leaking training data**

  Do you train/finetune the model yourself?
  - Yes: and is the training data sensitive? Then you need to prevent:
    - [unwanted disclosure in model output](/goto/disclosureuse/)
    - [model inversion](/goto/modelinversionandmembership/) (but not for GenAI)
    - [training data leaking from your engineering environment](/goto/devdataleak/).
    - [membership inference]((/goto/modelinversionandmembership/)) - but only if the **fact** that something or somebody was part of the training set is sensitive information. For example when the training set consists of criminals and their history to predict criminal careers: membership of that set gives away the person is a convicted or alleged criminal.
    
   If you use RAG: apply the above to your repository data, as if it was part of the training set: as the repository data feeds into the model and can therefore be part of the output as well.

  If you don't train/finetune the model, then the supplier of the model is responsible for unwanted content in the training data. This can be poisoned data (see above), data that is confidential, or data that is copyrighted. It is important to check licenses, warranties and contracts for these matters, or accept the risk based on your circumstances.


 **Model theft**

  Do you train/finetune the model yourself?
  - Yes, and is the model regarded intellectual poperty? Then you need to prevent:
    - [Model theft through use](/goto/modeltheftuse/)
    - [Model theft development-time](/goto/devmodelleak/)
    - [Source code/configuration leak](/goto/devcodeleak/)
    - [Runtime model theft](/goto/runtimemodeltheft/)
      
 **Leaking input data**
 
  Is your input data sensitive?
  - Prevent [leaking input data](/goto/leakinput/). Especially if the model is run by a supplier, proper care needs to be taken that this data is transferred or stored in a protected way and as little as possible. Note, that if you use RAG, that the  data you retrieve and insert into the prompt is also input data. This typically contains company secrets or personal data.


 **Misc.**

  Is your model a Large Language Model?
  - Prevent [insecure output handling](/goto/insecureoutput/), for example when you display the output of the model on a website and the output contains malicious Javascript.

  Make sure to prevent [model inavailability by malicious users](/denialmodelservice/) (e.g. large inputs, many requests). If your model is run by a supplier, then certain countermeasures may already be in place.

  Since AI systems are software systems, they require appropriate conventional application security and operational security, apart from the AI-specific threats and controls mentioned in this section.

### 2. 発生可能性と影響度の推定によるリスクの評価
To determine the severity of a risk, it is necessary to assess the probability of the risk occurring and evaluating the potential consequences should the risk materialize.

**Estimating the Likelihood:**  
Estimating the likelihood and impact of an AI risk requires a thorough understanding of both the technical and contextual aspects of the AI system in scope. The likelihood of a risk occurring in an AI system is influenced by several factors, including the complexity of the AI algorithms, the data quality and sources, the conventional security measures in place, and the potential for adversarial attacks. For instance, an AI system that processes public data is more susceptible to data poisoning and inference attacks, thereby increasing the likelihood of such risks.  A financial institution's AI system, which assesses loan applications using public credit scores, is exposed to data poisoning attacks. These attacks could manipulate creditworthiness assessments, leading to incorrect loan decisions. 

**Evaluating the Impact:**
Evaluating the impact of risks in AI systems involves understanding the potential consequences of threats materializing. This includes both the direct consequences, such as compromised data integrity or system downtime, and the indirect consequences, such as reputational damage or regulatory penalties. The impact is often magnified in AI systems due to their scale and the critical nature of the tasks they perform. For instance, a successful attack on an AI system used in healthcare diagnostics could lead to misdiagnosis, affecting patient health and leading to significant legal, trust, and reputational repercussions for the involved entities.

**Prioritizing risks**
The combination of likelihood and impact assessments forms the basis for prioritizing risks and informs the development of Risk Treatment decisions. Commonly organizations use a risk heat map to visually categorize risks by impact and likelihood. This approach facilitates risk communication and  decision-making.  It allows the management to focus on risks with highest severity (high likelihood and high impact).

### 3. リスク処置
Risk treatment is about deciding what to do with the risks. It involves selecting and implementing measures to mitigate, transfer, avoid, or accept cybersecurity risks associated with AI systems.  This process is critical due to the unique vulnerabilities and threats related to AI systems such as  data poisoning, model theft, and adversarial attacks. Effective risk treatment is essential to robust, reliable, and trustworthy AI.

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
For each selected threat, determine who is responsible to address it. By default, the organization that builds and deploys the AI system is responsible, but building and deploying may be done by different organizations, and some parts of the building and deployment may be deferred to other organizations, e.g. hosting the model, or providing a cloud environment for the application to run. Some aspects are shared responsibilities.

If components of your AI system are hosted, then you share responsibility regarding all controls for the relevant threats with the hosting provider. This needs to be arranged with the provider, using for example a responsibility matrix. Components can be the model, model extensions, your application, or your infrastructure. See [Threat model of using a model as-is](#threat-model-with-controls---genai-as-is).

If an external party is not open about how certain risks are mitigated, consider requesting this information and when this remains unclear you are faced with either 1) accept the risk, 2) or provide your own mitigations, or 3)avoid the risk, by not engaging with the third party.

### 6. Verify external responsibilities
For the threats that are the responsibility of other organisations: attain assurance whether these organisations take care of it. This would involve the controls that are linked to these threats.

Example: Regular audits and assessments of third-party security measures.
 
### 7. Select controls
Then, for the threats that are relevant to you and for which you are responsible: consider the various controls listed with that threat (or the parent section of that threat) and the general controls (they always apply). When considering a control, look at its purpose and determine if you think it is important enough to implement it and to what extent. This depends on the cost of implementation compared to how the purpose mitigates the threat, and the level of risk of the threat. These elements also play a role of course in the order you select controls: highest risks first, then starting with the lower cost controls (low hanging fruit).

Controls typically have quality aspects to them, that need to be fine tuned to the situation and the level of risk. For example: the amount of noise to add to input data, or setting thresholds for anomaly detection. The effectiveness of controls can be tested in a simulation environement to evaluate the performance impact and security improvements to find the optimal balance. Fine tuning controls needs to continuously take place, based on feedback from testing in simulation in in production.

### 8. Residual risk acceptance
In the end you need to be able to accept the risks that remain regarding each threat, given the controls that you implemented.

### 9. Further management of the selected controls
(see [SECPROGRAM](/goto/secprogram/)), which includes continuous monitoring, documentation, reporting, and incident response.

### 10. Continuous risk assessment
Implement continuous monitoring to detect and respond to new threats. Update the risk management strategies based on evolving threats and feedback from incident response activities.  
Example: Regularly reviewing and updating risk treatment plans to adapt to new vulnerabilities.

---

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
> カテゴリ: ディスカッション  
> パーマリンク: https://owaspai.org/goto/responsibleai/

AI には、リスクを軽減しながら良い結果をもたらすという点で、さまざまな側面があります。これは、責任ある AI や信頼できる AI と呼ばれることが多く、前者は倫理、社会、ガバナンスを重視し、後者はより技術的、運用的側面を重視します。

主な責務がセキュリティであるなら、最善の戦略はまず AI セキュリティに焦点を当て、その後に他の AI の側面について学ぶことです。たとえ、対応する責任を負っている同僚が警戒を怠らないようにするためであってもです。結局のところ、セキュリティ専門家は一般的にうまくいかない可能性のあるものを特定することに長けています。さらに、いくつかの側面は侵害された AI の結果である可能性があり、したがって _安全性 (safety)_ などを理解しておくと役立ちます。

AI の側面を明確にし、それらがセキュリティとどのように関係しているかを見てみましょう。
- **正確性 (Accuracy)** はその「ビジネス機能」を実行するのに十分に正しいかどうかを指します。不正確であると、(物理的な) 安全性の問題 (運転中に車のトランクが開いてしまうなど) やその他の有害な間違った判断 (ローンの不当な拒否など) などの危害につながる可能性があります。セキュリティとの関連は、ある種の攻撃が望ましくないモデル動作を引き起こすことであり、これは定義上、正確性の問題です。とはいえ、セキュリティの範囲ではそのような攻撃のリスクを軽減することに限定されており、正確なモデルの作成 (トレーニングセットの代表データの選択など) の問題全体を解決するものではありません。
- **安全性 (Safety)** は危害から保護されている、あるいは危害を引き起こす可能性が低い状態を指します。したがって、AI システムの安全性は危害 (一般的に物理的な危害を意味しますが、それに限定されません) のリスクがある場合の正確性のレベルのことであり、さらに (正確性とは別に) それらのリスクを軽減するために設けられたものです。これには正確性を保護するためのセキュリティに加えて、モデルのビジネス機能にとって重要な多くの安全性の対策を含みます。これらはセキュリティ上の理由だけでなく、他の理由 (不適切なトレーニングデータなど) でモデルが安全でない決定を下す可能性があるため、安全性とセキュリティの間で共通する懸念事項であることに注意する必要があります。
  -  安全でない動作を制限するための [監視](1_general_controls.md#OVERSIGHT)、およびそれに関連して、モデルへの最小権限の割り当て
  -  正確性を保護するための [継続的バリデーション](1_general_controls.md#CONTINUOUSVALIDATION)
  -  [透明性](1_general_controls.md#AITRANSPARENCY): 下記参照
  -  [説明可能性](1_general_controls.md#EXPLAINABILITY): 下記参照
- **透明性 (Transparency)**: アプローチに関する情報を共有すること、ユーザーおよび依存するシステムに正確性のリスクを警告すること、さらに、多くの場合、ユーザーは使用されているモデルについての詳細とそれがどのように作成されたかを知る権利を持っています。そのため、セキュリティ、プライバシー、安全性の間で共通する懸念事項になります。
- **説明可能性 (Explainability)**: 情報を共有すること、特定の結果がどのようにしてもたらされたかをより詳しく説明することで、ユーザーが正確性を検証するのに役立つこと。正確性を検証することとは別に、ユーザーが透明性を取得でき、異なる結果を得るには何を変更する必要があるかを理解することができます。そのため、セキュリティ、プライバシー、安全性、ビジネス機能の間で共通する懸念事項になります。特別なケースには、プライバシーとは別に説明可能性を法律で要求されている場合であり、この懸念を共有する側面のリストに「コンプライアンス」を追加します。
- **堅牢性 (Robustness)** は、入力に予期したバリエーションや予期しないバリエーションがあっても正確性を維持する能力です。セキュリティの範囲ではそのようなバリエーションが悪意のある場合 (_敵対的堅牢性_) に関するものであり、通常のバリエーション (_一般的堅牢性_) に対して必要な対策とは異なる対策が必要になることがよくあります。正確性の場合と同様に、セキュリティ自体は通常のバリエーションに対する堅牢なモデルの作成には関与しません。この例外は一般的堅牢性、敵対的悪意のある堅牢性の場合であり、この場合には安全性とセキュリティの間で共通する懸念事項になります。これはケースバイケースで異なります。
- **差別からの自由 (Free of discrimination)** 保護された属性に望ましくないバイアスがない、つまり、モデルが特定のグループ (性別、民族など) を「不当に扱う」ような体系的な不正確さがないこと。差別は法的および倫理的な理由から望ましくありません。セキュリティとの関係は、望ましくないバイアスを検出することで、攻撃によって引き起こされる望ましくないモデル動作を特定するのに役立つことです。たとえば、データポイズニング攻撃はトレーニングセットに悪意のあるデータサンプルを挿入します。最初は気付かれませんが、モデル内の原因不明のバイアスが検出されることによって発見されます。「公平性 (fairness)」という用語は差別問題を指すために使用されることもありますが、プライバシーにおける公平性は、と名声、倫理的使用、プライバシー権など、個人に対する公平な扱いを指す幅広い用語であることがほとんどです。
- **共感性 (Empathy)**。セキュリティとの関係は、AI の特定のアプリケーションを検証する際に、常に実現可能なセキュリティレベルを考慮すべきであるということです。十分なレベルのセキュリティを個人や組織に提供できないのであれば、共感性とはそのアイデアを無効にするか、他の予防措置を講じることを意味します。
- **説明責任 (Accountability)**。説明責任とセキュリティの関係は、セキュリティ対策はその対策に至ったプロセスを含めて実証可能であるべきということです。さらに、セキュリティインシデントを検出し、再構築し、対応して、説明責任を果たすためには、他の IT システムと同様に、セキュリティ特性としてのトレーサビリティが重要です。
- **AI セキュリティ**。AI のセキュリティの側面は AI Exchange の中心的なトピックです。簡単に言うと、以下のように分けられます。
  - [入力攻撃](2_threats_through_use.md)、モデルに入力を提供することで実行されます
  - [モデルポイズニング](3_development_time_threats.md#31-broad-model-poisoning-development-time)、モデルの動作を改変することを目的としています
  - [開発時](3_development_time_threats.md#32-sensitive-data-leak-development-time) または実行時 (下記参照) に、トレーニングデータ、モデル入力、出力、またはモデル自体などの AI 資産を盗みます
  - さらに [実行時の従来のセキュリティ攻撃](4_runtime_application_security_threats.md##41-non-ai-specific-application-security-threats)

[![](https://raw.githubusercontent.com/OWASP/www-project-ai-security-and-privacy-guide/main/assets/images/aiwayfinder.png)](https://raw.githubusercontent.com/OWASP/www-project-ai-security-and-privacy-guide/main/assets/images/aiwayfinder.png)

### <a name="how-about-privacy">プライバシーについてはどうですか？</a>
> カテゴリ: ディスカッション  
> パーマリンク: https://owaspai.org/goto/privacy/

Just like any system that processes data, AI systems can have privacy risks. There are some particual privacy aspects to AI:
- AI systems are data-intensive and typically present additional risks regarding data collection and retention. Personal data may be collected from various sources, each subject to different levels of **sensitivity and regulatory constraints**. Legislation often requires a **legal basis and/or consent** for the collection and use of personal data, and specifies **rights to individuals** to correct, request, and remove their own data.
- **Protecting training data** is a challenge, especially because it typically needs to be retained for long periods - as many models need to be retrained. Often, the actual identities of people involved are irrelevant for the model, but privacy risks still remain even if identity data is removed because it might be possible to deduce individual identities from the remaining data. This is where differential privacy becomes crucial: by altering the data to make it sufficiently unrecognizable, it ensures individual privacy while still allowing for valuable insights to be derived from the data. Alteration can be done by for example adding noise or aggregating.
- An additional complication in the protection of training data is that the **training data is accessible in the engineering environment**, which therefore needs more protection than it usually does - since conventional systems normally don't have personal data available to technical teams.
- The nature of machine learning allows for certain **unique strategies** to improve privacy, such as federated learning: splitting up the training set in different separated systems - typically aligning with separated data collection.
- AI systems **make decisions** and if these decisions are about people they may be discriminating regarding certain protected attributes (e.g. gender, race), plus the decisions may result in actions that invade privacy, which may be an ethical or legal concern. Furthermore, legislation may prohibit some types of decisions and sets rules regarding transparancy about how these decisions are made, and about how individuals have the right to object.
- Last but not least: AI models suffer from **model attack risks** that allow attackers to extract training data from the model, e.g. model inversion, memership inference, and disclosing sensitive data in large language models


AI プライバシーは二つのパートに分けることができます。

1. AI セキュリティに対する脅威とそのコントロール (このドキュメント) は、以下を含みます。
  - トレーニングデータとテストデータ、モデル入出力における個人データの機密性と完全性の保護 - 以下で構成します。
    - 転送時および保存時の個人データの「従来型」セキュリティ
    - 個人データを取得しようとするモデル攻撃 (モデル反転など) に対する保護
    - 個人データの最小化/差分プライバシー (最小保持を含む)
  - モデルの動作が個人のプライバシーを侵害する可能性がある場合のモデル動作の完全性保護。これはたとえば個人が違法に差別される場合や、モデルの出力がプライバシーを侵害するアクション (詐欺調査を受けるなど) につながる場合に発生します。
2. セキュリティに関するものではありませんが、個人のさらなる権利に関する脅威とコントロールは GDPR などのプライバシー規制でカバーされます。これには使用制限、同意、公平性、透明性、データの正確性、訂正/異議申し立て/消去/請求の権利が含まれます。概要については、[OWASP AI ガイドのプライバシーパート](https://owasp.org/www-project-ai-security-and-privacy-guide/) を参照してください。

### 生成 AI (LLM など) についてはどうですか？
> カテゴリ: ディスカッション  
> パーマリンク: https://owaspai.org/goto/genai/

はい、生成 AI は現在の AI 変革をリードしており、AI セキュリティの中で最も急速に変化しているサブフィールドです。とはいえ、クレジットスコアリング、不正検出、医療診断、製品推奨、画像認識、予知保全、プロセス制御など、多くの重要なユースケースには他のタイプのアルゴリズム (_予測 AI_ と呼びましょう) が引き続き適用されることを認識することが重要です。このドキュメントでは関連するコンテンツには「生成 AI」のマークを付けています。

重要な注意: セキュリティ脅威の観点からは、生成 AI は他の形式の AI (_予測 AI_) とそれほど違いはありません。生成 AI の脅威とコントロールは一般的な AI と大部分が重複しており、非常によく似ています。とはいえ、一部のリスクは (はるかに) 高くなります。低いものもあります。生成 AI 固有のリスクはごくわずかです。生成 AI と予測 AI ではコントロールカテゴリが大きく異なるものがあり、主にデータサイエンスコントロール (トレーニングセットへのノイズ追加など) です。多くの場合、生成 AI ソリューションはモデルをそのまま使用し、組織によるトレーニングを一切行わず、セキュリティ責任の一部を組織からサプライヤに移します。それでも、既製のモデルを使用する場合は、依然としてそうした脅威に注意する必要があります。

LLM による主な新しい脅威は何ですか？
- まず第一に、LLM は脆弱性のあるコードを作成するために使用されたり、攻撃者がマルウェアを作成したり、ハルシネーションによって害を及ぼす可能性があるため、セキュリティに新たな脅威をもたらしますが、AI Exchange の範囲外であり、AI システムへのセキュリティ脅威に焦点を当てています。
- 入力について:
  - プロンプトインジェクションは全く新しい脅威です。攻撃者は細工した命令や、時には隠された命令で、モデルの動作を操作します。
  - また、企業秘密や個人データを含む、大量のデータをプロンプトで送信する組織も新たにあります。
- 出力について: 出力にはインジェクション攻撃を含んだり、機密データや著作権で保護されたデータを含む可能性があるという事実が新たにあります ([著作権](ai_security_overview.md#how-about-copyright) 参照)。
- 過度の依存は問題です。私たちは LLM に物事を制御および作成され、LLM がどれほど正しいかを過信し、また、LLM が操作されるリスクを過小評価していることがあります。その結果、攻撃は大きな影響を与えることになります。
- トレーニングについて: トレーニングセットは非常に大きく、公開データに基づいているため、データポイズニングを実行することは容易です。また、汚染された基礎モデルはサプライチェーンの大きな問題でもあります。

生成 AI セキュリティの特徴は以下の通りです。

|No.| 生成 AI セキュリティの特徴 | OWASP for LLM TOP 10 |
|-| ----------|-------------------|
|1| 生成 AI モデルはプロンプト内の自然言語によって制御されるため、[プロンプトインジェクション](2_threats_through_use.md#22-prompt-injection) のリスクが生じます。直接プロンプトインジェクションはモデルを騙して望ましくない動作 (不快な言動など) をさせようとするもので、間接プロンプトインジェクションは第三者がこの目的 (決定を操作するなど) のためにプロンプトにコンテンツを注入するものです。 |  ([OWASP for LLM 01:Prompt injection](https://genai.owasp.org/llmrisk/llm01/))  | 
|2| 生成 AI モデルは一般的に非常に大規模なデータセットでトレーニングされているため、[機密データ](2_threats_through_use.md#221-sensitive-data-output-from-model) や [ライセンスされているデータ](ai_security_overview.md#how-about-copyright) を出力する可能性が高くなりますが、モデルにはアクセス権限の制御が組み込まれていません。すべてのデータはモデルユーザーがアクセスできるでしょう。システムプロンプトや出力フィルタリングに関していくつかのメカニズムが実装されているかもしれませんが、それらは一般的に完全ではありません。 | ([OWASP for LLM 02: Sensitive Information Disclosure](https://genai.owasp.org/llmrisk/llm02/)) |
|3| [データとモデルのポイズニング](3_development_time_threats.md#31-broad-model-poisoning-development-time) は AI 全般の問題ですが、生成 AI ではトレーニングデータがインターネットなどの制御が困難なさまざまな情報源から供給される可能性があるため、リスクは一般的に高くなります。たとえば、攻撃者はドメインを乗っ取り、操作された情報を配置する可能性があります。 | ([OWASP for LLM 04: Data and Model Poisoning](https://genai.owasp.org/llmrisk/llm04/)) |
|4| 生成 AI モデルは不正確で幻覚を起こす可能性があります。これは AI 全般のリスク要因であり、さらに大規模言語モデル (生成 AI) は非常に機密性が高く知識を持っていると思われることで事態を悪化させる可能性があります。要するに、これはモデルが間違っていたり、モデルが操作されていたりするという可能性を過小評価するリスクに関するものです。つまり、それぞれすべてのセキュリティコントロールに関連しています。最も強く結びつくのは [望ましくないモデル動作の影響を制限するためのコントロール](1_general_controls.md#13-controls-to-limit-the-effects-of-unwanted-behaviour)、特に [最小モデル権限](/1_general_controls.md#LEASTMODELPRIVILEGE) です。 | ([OWASP for LLM 06: Excessive agency](https://genai.owasp.org/llmrisk/llm06/)) および ([OWASP for LLM 09: Misinformation](https://genai.owasp.org/llmrisk/llm09/)) |
|5| [入力データの漏洩](4_runtime_application_security_threats.md#47-leak-sensitive-input-data): 生成 AI モデルはほとんどがクラウドに存在し、多くの場合は外部パーティによって管理されているため、トレーニングデータの漏洩やプロンプトの漏洩のリスクが高まる可能性があります。この問題は生成 AI に限定されるものではありませんが、生成 AI には特に 2 つのリスクがあります。1) モデルの使用にはプロンプトを介したユーザーとのやり取り、ユーザーデータの追加、対応するプライバシーやセンシティビティの問題が含まれます。2) 生成 AI モデルの入力 (プロンプト) には機密データ (企業秘密など) を持つ豊富なコンテキスト情報を含む可能性があります。後者の問題はたとえば、コンサルタント会社でこれまでに書かれたすべてのレポートのデータなど、*コンテキスト内学習 (In Context Learning)* や *検索拡張生成 (Retrieval Augmented Generation, RAG)* で発生します。まず第一に、この情報はプロンプトとともにクラウドに移動し、第二に、システムは情報に対する本来のアクセス権を考慮しない可能性があります。 | LLM Top 10 でのカバーなし |
|6| 事前トレーニング済みモデルは操作されている可能性があります。事前トレーニングの概念は生成 AI に限ったことではありませんが、このアプローチは生成 AI ではごく一般的であり、 [サプライチェーンのモデルポイズニング](3_development_time_threats.md#313-supply-chain-model-poisoning) のリスクを高めます。 | ([OWASP for LLM 03 - Supply chain vulnerabilities](https://genai.owasp.org/llmrisk/llm03/)) |
|7| [モデル反転とメンバーシップ推論](2_threats_through_use.md##222-model-inversion-and-membership-inference) は生成 AI にとって低リスクまたはゼロリスクです。 | LLM Top 10 でのカバーなし、異なるアプローチを使用する LLM06 を除く、上記を参照 |
|8| 生成 AI の出力にはクロスサイトスクリプティングなどの [インジェクション攻撃](4_runtime_application_security_threats.md#44-insecure-output-handling) を実行する要素を含むかもしれません。 | ([OWASP for LLM 05: Improper Output Handling](https://genai.owasp.org/llmrisk/llm05/)) |
|9| [サービス拒否](2_threats_through_use.md#24-failure-or-malfunction-of-ai-specific-elements-through-use) はどの AI モデルでも問題になる可能性がありますが、生成 AI モデルは一般的に実行コストが高いため、過負荷になると不要なコストが発生する可能性があります。 | ([OWASP for LLM 10: Unbounded consumption](https://genai.owasp.org/llmrisk/llm10/)) |

生成 AI 参考情報:

- [OWASP LLM top 10](https://llmtop10.com/)
- [Demystifying the LLM top 10](https://blog.kloudzone.co.in/demystifying-the-owasp-top-10-for-large-language-model-applications/)
- [Impacts and risks of GenAI](https://arxiv.org/pdf/2306.13033.pdf)
- [LLMsecurity.net](https://llmsecurity.net/)

### NCSC/CISA ガイドラインについてはどうですか？
>カテゴリ: ディスカッション  
>パーマリンク: https://owaspai.org/goto/jointguidelines/

英国 NCSC / CISA の [安全な AI システム開発のガイドライン](https://www.ncsc.gov.uk/collection/guidelines-secure-ai-system-development) を AI Exchange のコントロールにマッピングします。
脅威とリンクしているコントロールを確認するには、[AI セキュリティの周期表](ai_security_overview.md#periodic-table-of-ai-security) を参照してください。

1. 安全な設計

- 脅威とリスクに対するスタッフの意識を高めます:
  #[SECURITY EDUCATE](1_general_controls.md#SECEDUCATE)
- システムに対する脅威をモデル化します:
  #[SECURITY PROGRAM](1_general_controls.md#SECPROGRAM) のリスク分析を参照してください
- 機能性とパフォーマンスだけでなくセキュリティも考慮してシステムを設計します:
  #[AI PROGRAM](1_general_controls.md#AIPROGRAM), #[SECURITY PROGRAM](1_general_controls.md#SECPROGRAM), #[DEVELOPMENT PROGRAM](1_general_controls.md#DEVPROGRAM), #[SECURE DEVELOPMENT PROGRAM](1_general_controls.md#SECDEVPROGRAM), #[CHECK COMPLIANCE](1_general_controls.md#CHECKCOMPLIANCE), #[LEAST MODEL PRIVILEGE](1_general_controls.md#LEASTMODELPRIVILEGE), #[DISCRETE](1_general_controls.md#DISCRETE), #[OBSCURE CONFIDENCE](2_threats_through_use.md#OBSCURECONFIDENCE), #[OVERSIGHT](1_general_controls.md#OVERSIGHT), #[RATE LIMIT](2_threats_through_use.md#RATELIMIT), #[DOS INPUT VALIDATION](2_threats_through_use.md#DOSINPUTVALIDATION), #[LIMIT RESOURCES](2_threats_through_use.md#LIMITRESOURCES), #[MODEL ACCESS CONTROL](2_threats_through_use.md#MODELACCESSCONTROL), #[AI TRANSPARENCY](1_general_controls.md#AITRANSPARENCY)
- AI モデルを選択する際に、セキュリティの利点とトレードオフを考慮します
  すべての開発時のデータサイエンスコントロール (現在 13), #[EXPLAINABILITY](1_general_controls.md#EXPLAINABILITY)

2. 安全な開発

- サプライチェーンを保護します:
  #[SUPPLY CHAIN MANAGE](3_development_time_threats.md#SUPPLYCHAINMANAGE)
- 資産を特定、追跡、保護します:
  #[DEVELOPMENT SECURITY](3_development_time_threats.md#DEVSECURITY), #[SEGREGATE DATA](3_development_time_threats.md#SEGREGATEDATA), #[CONFIDENTIAL COMPUTE](3_development_time_threats.md#CONFCOMPUTE), #[MODEL INPUT CONFIDENTIALITY](4_runtime_application_security_threats.md#MODELINPUTCONFIDENTIALITY), #[RUNTIME MODEL CONFIDENTIALITY](4_runtime_application_security_threats.md#RUNTIMEMODELCONFIDENTIALITY), #[DATA MINIMIZE](1_general_controls.md#DATAMINIMIZE), #[ALLOWED DATA](1_general_controls.md#ALLOWEDDATA), #[SHORT RETAIN](1_general_controls.md#SHORTRETAIN), #[OBFUSCATE TRAINING DATA](1_general_controls.md#OBFUSCATETRAININGDATA) および #[SECURITY PROGRAM](1_general_controls.md#SECPROGRAM) の一部
- データ、モデル、プロンプトを文書化します:
  #[DEVELOPMENT PROGRAM](1_general_controls.md#DEVPROGRAM) の一部
- 技術的負債を管理します:
  #[DEVELOPMENT PROGRAM](1_general_controls.md#DEVPROGRAM) の一部

3. 安全な展開

- インフラストラクチャを保護します:
  #[SECURITY PROGRAM](1_general_controls.md#SECPROGRAM) の一部と「資産を特定、追跡、保護します」を参照してください
- モデルを継続的に保護します:
  #[INPUT DISTORTION](2_threats_through_use.md#INPUTDISTORTION), #[FILTER SENSITIVE MODEL OUTPUT](2_threats_through_use.md#FILTERSENSITIVEMODELOUTPUT), #[RUNTIME MODEL IO INTEGRITY](4_runtime_application_security_threats.md#RUNTIMEMODELIOINTEGRITY), #[MODEL INPUT CONFIDENTIALITY](4_runtime_application_security_threats.md#MODELINPUTCONFIDENTIALITY), #[PROMPT INPUT VALIDATION](2_threats_through_use.md#PROMPTINPUTVALIDATION), #[INPUT SEGREGATION](2_threats_through_use.md#INPUTSEGREGATION)
- インシデント管理手順を策定します:
  #[SECURITY PROGRAM](1_general_controls.md#SECPROGRAM) の一部
- 責任をもって AI をリリースします:
  #[DEVELOPMENT PROGRAM](1_general_controls.md#DEVPROGRAM) の一部
- ユーザーが正しいことを簡単にできるようにします:
  #[SECURITY PROGRAM](1_general_controls.md#SECPROGRAM) の一部

4. 安全な運用と保守

- システムの動作を監視します:
  #[CONTINUOUS VALIDATION](1_general_controls.md#CONTINUOUSVALIDATION), #[UNWANTED BIAS TESTING](1_general_controls.md#UNWANTEDBIASTESTING)
- システムの入力を監視します:
  #[MONITOR USE](2_threats_through_use.md#MONITORUSE), #[DETECT ODD INPUT](2_threats_through_use.md#DETECTODDINPUT), #[DETECT ADVERSARIAL INPUT](2_threats_through_use.md#DETECTADVERSARIALINPUT)
- セキュアバイデザインのアプローチに従ってアップデートを行います:
  #[SECURE DEVELOPMENT PROGRAM](1_general_controls.md#SECDEVPROGRAM) の一部
- 教訓を収集して共有します:
  #[SECURITY PROGRAM](1_general_controls.md#SECPROGRAM) および #[SECURE DEVELOPMENT PROGRAM](1_general_controls.md#SECDEVPROGRAM) の一部


### <a name="how-about-copyright">How about copyright?</a>
>Category: discussion  
>パーマリンク: https://owaspai.org/goto/copyright/

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
