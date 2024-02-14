---

layout: col-sidebar
title: OWASP AI Security and Privacy Guide
tags: AIsecpri AI security privacy requirements guide machinelearning algorithms
level: 2
type: documentation
pitch: 安全でプライバシーを保護する AI システムの設計、作成、テスト、調達に関するガイダンス

---
<img src="https://github.com/OWASP/www-project-ai-security-and-privacy-guide/blob/main/assets/images/aisecprivlogosml.jpeg?raw=true" width="600" height ="127"><img src="https://github.com/OWASP/www-project-ai-security-and-privacy-guide/blob/main/assets/images/humansonly.png?raw=true" align="right"/>

このページは OWASP AI セキュリティおよびプライバシーガイドです。これには二つの部分があります。
1. [AI セキュリティの取り組み方](#how-to-address-ai-security)
2. [AI プライバシーの取り組み方](#how-to-address-ai-privacy)

人工知能 (AI) は増加傾向にあり、AI のセキュリティとプライバシーに関する懸念も高まっています。このガイドは安全でプライバシーを保護する AI システムの設計、作成、テスト、調達に関する明確で実用的な洞察を提供する実用的な文書です。

2023 年 2 月 15 日にダブリンで開催された OWASP Global AppSec イベントでこのガイドが発表されました。 [Rob van der Veer の講演](https://sched.co/1F9DT) の [この有用な記録](https://www.youtube.com/watch?v=ABmWHnFrMqI) や [スライド](https://github.com/OWASP/www-project-ai-security-and-privacy-guide/blob/main/assets/images/20230215-Rob-AIsecurity-Appsec-ForSharing.pdf?raw=true) も参照してください。また、このガイドの AppSec Podcast エピソード ([音声](https://www.buzzsprout.com/1730684/12313155-rob-van-der-veer-owasp-ai-security-privacy-guide)、[動画](https://www.youtube.com/watch?v=SLdn3AwlCAk&)、[September 2023 MLSecops Podcast](https://mlsecops.com/podcast/a-holistic-approach-to-understanding-the-ai-lifecycle-and-securing-ml-systems-protecting-ai-through-people-processes-technology)) もご覧ください。ショートストーリーをお望みであれば、 [13分 AI セキュリティクイックトーク](https://www.brighttalk.com/webcast/19697/586526) をご覧ください。

<p align="left"><a href="https://www.youtube.com/watch?v=ABmWHnFrMqI" target="_blank" rel="noopener noreferrer"><img src="https://github.com/OWASP/www-project-ai-security-and-privacy-guide/blob/main/assets/images/talkvideo.png?raw=true" border="1"/> </a></p>

プルリクエストや issues ([リポジトリ](https://github.com/OWASP/www-project-ai-security-and-privacy-guide/) を参照) を通じて、またはプロジェクトリーダーへの電子メールでご意見をお願いします。このガイドをどんどん良くしていきましょう。 Uber のリードプライバシーアーキテクトである Engin Bozdag 氏の多大な貢献に感謝します。

# AI セキュリティの取り組み方 <a name="how-to-address-ai-security"></a>
このコンテンツは現在 [OWASP AI exchange](https://owaspai.org) にあります。
<br />
<br />
<br />

# AI プライバシーの取り組み方 <a name="how-to-address-ai-privacy"></a>
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

グループ (保護された属性) 間の公平性を無視することは、モデルが保護された属性を差別するかどうかというのがより正確な状況です。文化や歴史に根差したさまざまな社会的側面があるため、特定のグループの成功率が実際に低い地域があります。私たちはそれをなくしたいと思っています。これらの側面のいくつかは制度的差別とみなすことができます。たとえば言語的な理由から、新しい移民は統計的に高等教育を受けるのに支障をきたす傾向があることが分かっているなど、より現実的な背景をもつものもあります。
したがって、グループ間で完全に公平でありたいのであれば、多くの場合、精度と差別のバランスをとることを受け入れる必要があります。差別の境界内にとどまりながら十分な精度が得られない場合には、アルゴリズムのアイデアを放棄する以外に選択肢はありません。不正検出の場合、これはたとえばアルゴリズムを使用する代わりにトランザクションをランダムに選択する必要があることを意味するかもしれません。

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
プライバシー標準では「個人参加 (individual participation)」とも呼ばれるこの原則により、個人が自分の個人データに関連する要求を組織に提示できます。最も参照される権利は以下のとおりです。

1. アクセス権とポータビリティ権: ユーザーデータのコピーを、できれば機械読み取り可能な形式で提供します。データが適切に匿名化されている場合、この権利から免除されることがあります。
2. 消去権: 例外が適用されない限り、ユーザーデータを消去します。また、削除されたユーザーのデータなしでモデルを再訓練することも良い方法です。
3. 訂正権: ユーザーが事実と異なるデータを訂正できます。以下の正確性も参照してください。
4. 異議申立権: ユーザーが特定の用途 (例: モデルトレーニング) においてデータを使用することに異議を唱えることができます。

## 6. データ正確性 (Data accuracy)
誤ったデータでのアルゴリズムによる決定の出力は個人に深刻な結果をもたらす可能性があるため、データが正しいことを確保する必要があります。たとえば、ユーザーの電話番号がシステムに誤って追加され、その番号が詐欺に関連付けられている場合、ユーザーは不当な事由でサービスやシステムから追放される可能性があります。このような正確性の問題は本人から適切な要求がなされた際にできるだけ早く修正するためのプロセスやツールを用意しておく必要があります。

正確性の原則を満たすには、信頼できるソースからデータを取得し、その有効性と正確性の主張を検証し、データ品質と正確性を定期的に評価することを確保するためのツールやプロセスも用意する必要があります。

## 7. 同意 (Consent)
特定の状況において同意が使用または要求されることがあります。そのような場合、同意は以下を満たす必要があります。

  1. データを収集、使用、更新、共有するまえに同意を得ます
  2. 同意は記録され監査可能である必要があります
  3. 同意はきめ細かくする必要があります (目的ごとに同意を使用し、包括的な同意を避けます)
  4. 同意は T&S とバンドルしてはいけません
  5. 同意記録は改竄から保護する必要があります
  6. 同意の方法とテキストは同意が必要な法域の特定の要件に準拠する必要があります (たとえば、GDPR では曖昧さがなく、自由に与えられ、明確で平易な言葉で書かれ、明示的で撤回可能であることを要求します)
  7. 同意の撤回は同意を与えるのと同じくらい簡単である必要があります
  8. 同意が撤回された際には、同意に関連するすべてのデータを削除し、モデルを再訓練する必要があります

特定の状況では同意は得ることができないことに注意してください (たとえば、詐欺師から同意を得ることはできず、雇用主は力の不均衡があるため従業員から同意を得ることはできません) 。同意を集める必要がある場合には、適切に習得され、記録され、撤回された場合に適切な措置が取られるように確保します。


## 8. モデル攻撃 (Model attacks)
データ機密性へのセキュリティ脅威についてはセキュリティセクションを参照してください。そのデータが個人データである場合、当然ながらプライバシーリスクとなります。注目すべきは、メンバーシップ推論、モデル反転、エンジニアリングプロセスからの訓練データ漏洩です。さらに、モデルはトレーニング時に意図せず保存された機密データを開示する可能性があります。


## AI プライバシーのスコープ境界
前述のように、AI に関する議題の多くは人権、社会正義、安全に関するものであり、プライバシーに関するのはその一部にすぎません。したがって、データ保護責任者やエンジニアとして、すべてを自分の責任に引きずり込まないことが重要です。同時に、組織はプライバシーに関係のない AI の責任をどこかに割り当てる必要があります。


## 始める前に: AI でできることに関するプライバシー制限
GDPR は AI の適用を明示的に制限するものではありませんが、前述のように、特に合法性と、収集、処理、保存の目的の制限に関して、できることを制限する可能性があるセーフガードを提供します。法的根拠の詳細については、[第 6 条](https://gdpr.eu/article-6-how-to-process-personal-data-legally/) を参照してください。


今後の更新では、[米国の AI 権利章典 (AI bill of rights)](https://www.whitehouse.gov/ostp/ai-bill-of-rights/) についてさらに詳しく解説する予定です。

[米国連邦取引委員会](https://www.ftc.gov/business-guidance/blog/2023/02/keep-your-ai-claims-check) は AI について慎重にコミュニケーションする上で、過剰な約束をしないことなど、優れた (グローバルな) ガイダンスを提供しています。

[EU の AI 法](https://eur-lex.europa.eu/legal-content/EN/TXT/HTML/?uri=CELEX:52021PC0206&from=EN) では大規模な監視、予測的な取り締まり、仕事における人員の選択などのリスクの高い目的に対する制限など、明示的な適用制限を課しています。さらに、特定ドメイン (医療ドメインなど) に対してデータの使用を制限する規制があり、一部の AI アプローチには制限を課しています。

**EU AI 法の要約:**

人権が AI 法の根幹にあるため、リスクは人への有害性の観点から分析されます。

この法律では AI システムの四つのリスクレベルを特定しています。
  * **許容できないリスク (Unacceptable risk)**: は禁止されます。含まれるもの: 人の操作、ソーシャルスコアリング、リアルタイムのリモート生体認証 (公共スペースでのカメラによる顔認証など) 。
  * **高リスク (High risk)**: すでに安全法の下にある製品、および八つの分野 (重要インフラストラクチャと法執行機関を含む) 。これらのシステムはセキュリティリスク評価や、調和された (適応された) AI セキュリティ標準またはサイバーレジリエンス法 (該当する場合) の必須要件への適合など、多くの規則に準拠する必要があります。
  * **限定的なリスク (Limited risk)**: は操作の可能性は限定的です。ユーザーが情報に基づいた意思決定をできるように、ユーザーに対する最小限の透明性要件を遵守する必要があります。アプリケーションとやり取りした後、ユーザーはそのアプリケーションを使い続けるかどうかを決定できます。
  * **最小限のリスク/リスクなし**: 残りのシステム。

そのため、組織は自社の AI への取り組みを理解し、高レベルのリスク分析を行ってリスクレベルを判断する必要があります。

ここでいう AI とは広義のもので、より広範な統計的アプローチや最適化アルゴリズムも含みます。

生成 AI は著作権で保護されたソースが使用されていることを明らかにし、違法なコンテンツを防止する必要があります。たとえば、OpenAI がこの規則に違反した場合、100 億ドルの罰金に課せられる可能性があります。

リンク:
* [AI 法原案](https://www.europarl.europa.eu/RegData/docs_autres_institutions/commission_europeenne/com/2021/0206/COM_COM(2021)0206_EN.pdf)
* [改正](https://www.europarl.europa.eu/doceo/document/CJ40-PR-731563_EN.pdf)
* [詳細](https://www.europarl.europa.eu/legislative-train/theme-a-europe-fit-for-the-digital-age/file-regulation-on-artificial-intelligence)

## AI プライバシーの参考情報

* [NIST AI Risk Management Framework 1.0](https://doi.org/10.6028/NIST.AI.100-1)
* [PLOT4ai threat library ](https://plot4.ai/library)
* [Algorithm audit non-profit organisation](https://algorithmaudit.eu/)
* 純粋なセキュリティの側面については、本文書で前述の「AI セキュリティの参考情報」を参照してください

# プロジェクトの状況
このページはプロジェクトの現在の成果です。目的はコミュニティの協力によってこれらのトピックに関する最新情報を収集して提示することです。最初はこのページの形式で、後に他のドキュメント形式で。プルリクエストや issues の提出 ([リポジトリ](https://github.com/OWASP/www-project-ai-security-and-privacy-guide/) を参照) またはプロジェクトリーダーへの電子メールを通じて意見を提供してください。このガイドをより良いものにしていきましょう。

このガイドの作業は今後の [ISO/IEC 27090 (AI セキュリティ)](https://www.iso.org/standard/56581.html) および [27091 (AI プライバシー)](https://www.iso.org/standard/56582.html) 標準へのインプットとなります。これは ISO/IEC JTC1/SC27/WG4, WG5, CEN/CENELEC JTC 21/WG1-TG, および SC42 AHG4 グループのメンバーを通じて行われます。
