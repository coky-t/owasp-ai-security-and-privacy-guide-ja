---
title: 5. AI セキュリティテスト
heroTitle: "AI セキュリティテスト"
heroText: "AI セキュリティテストは敵対的行動をシミュレートして、AI システムの脆弱性、弱点、リスクを明らかにします。"
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

各 AI パラダイムに対する主要な脅威について言及しましたが、AI レッドチーミングの目標とスコープの定義フェーズの結果に基づき、AI Exchange のすべての脅威を参照することを読者に強くお勧めします。

**AI セキュリティテストの参考情報**:
- エージェント AI システムのテストの詳細については、CSA と AI Exchange の間でコラボレーションした [エージェント AI レッドチーミングガイド](https://cloudsecurityalliance.org/download/artifacts/agentic-ai-red-teaming-guide) を参照してください。
- [OWASP AI セキュリティテストガイド](https://owasp.org/www-project-ai-testing-guide/)

## **AI および生成 AI のためのレッドチーミングツール**

以下のマインドマップは、AI レッドチーミングのオープンソースツールの概要を示しており、予測 AI レッドチーミングと生成 AI レッドチーミングに分類され、ART, Armory, TextAttack, Promptfoo などの例を挙げています。これらのツールは現時点での機能を示していますが、網羅的ではなく、重要度順にランク付けされているわけでもありません。今後、新たなツールや手法が出現し、この分野に統合される可能性が高いためです。

[![](https://owaspai.org/images/testtoolstoattacks.png)](https://owaspai.org/images/testtoolstoattacks.png)

以下の図は AI システムの脅威を分類し、これらの脅威に対処するために設計された関連するオープンソースツールにマップしています。

[![](https://owaspai.org/images/attackstotesttools.jpg)](https://owaspai.org/images/attackstotesttools.jpg)

以下のセクションでは予測 AI のツールについて説明し、その後に生成 AI のセクションに続きます。

## **予測 AI レッドチーミングのためのオープンソースツール**

このサブセクションは予測 AI のセキュリティテストのための次のツールについてカバーします: Adversarial Robustness Toolbox (ART), Armory, Foolbox, DeepSec, TextAttack

### **ツール名: 敵対的ロバストネスツールボックス (Adversarial Robustness Toolbox, ART)**

| **ツール名: 敵対的ロバストネスツールボックス (Adversarial Robustness Toolbox, ART)** |  |
| --- | --- |
| 開発元/ソース | IBM Research / the Linux Foundation AI & Data Foundation (LF AI & Data) |
| GitHub 参照 | https://github.com/Trusted-AI/adversarial-robustness-toolbox |
| 言語 | Python |
| ライセンス | MIT ライセンスの下でのオープンソース |
| 緩和策の提供 | 防止: No ❌ 検出: Yes ✅ |
| API の可用性 | Yes ✅ |

| 要素 | 詳細 |
| --- | --- |
| **人気** | - **GitHub スター:** およそ 4.9K スター (2024 年現在) |
|  | - **GitHub フォーク:** およそ 1.2K フォーク |
|  | - **Issues の数:** およそ 131 オープン状態, 761 クローズ済み状態 |
|  | - **傾向:** 継続的なアップデートと業界の採用で敵対的堅牢性に対して着実に成長している。 |
| **コミュニティサポート** | - **Issues 活動:** 反応が早いチーム、通常は一週間以内に issues に対処している。 |
|  | - **ドキュメント:** IBM のウェブサイトには包括的なガイドと API ドキュメントがあり、詳細で定期的に更新されている。 |
|  | - **ディスカッションフォーラム:** 主に学術的な場で議論されており、Stack Overflow や GitHub でも行われている。 |
|  | - **貢献者:** 100 名以上。IBM 研究者や外部協力者を含む。 |
| **拡張性** | - **フレームワークサポート:** out-of-the-box サポートで、TensorFlow, Keras, PyTorch にわたって拡張している。 |
|  | - **大規模デプロイメント:** 医療、金融、防衛などの業界における大規模なエンタープライズレベルのデプロイメントに対応することが実装されている。 |
| **統合** | - **互換性:** TensorFlow, PyTorch, Keras, MXNet, Scikit-learn で機能する。 |

**ツールの評価**

| **基準** | **高** | **中** | **低** |
| --- | --- | --- | --- |
| **人気** | ✅ |  |  |
| **コミュニティサポート** | ✅ |  |  |
| **拡張性** | ✅ |  |  |
| **統合の容易さ** | ✅ |  |  |

**データモダリティ**

| データモダリティ | サポートあり |
| --- | --- |
| テキスト | ✅ |
| 静止画 | ✅ |
| 音声 | ✅ |
| 動画 | ✅ |
| 表形式データ | ✅ |

**機械学習タスク**

| タスクタイプ | データモダリティ | サポートあり |
| --- | --- | --- |
| 分類 | すべて (データモダリティセクションを参照) | ✅ |
| 物体検出 | コンピュータビジョン | ✅ |
| 音声認識 | 音声 | ✅ |

**フレームワークの適用性**

| フレームワーク / ツール | カテゴリ | サポートあり |
| --- | --- | --- |
| Tensorflow | 深層学習, 生成 AI | ✅ |
| Keras | 深層学習, 生成 AI | ✅ |
| PyTorch | 深層学習, 生成 AI | ✅ |
| MxNet | 深層学習 | ✅ |
| Scikit-learn | 機械学習 | ✅ |
| XGBoost | 機械学習 | ✅ |
| LightGBM | 機械学習 | ✅ |
| CatBoost | 機械学習 | ✅ |
| GPy | 機械学習 | ✅ |

**OWASP AI Exchange 脅威カバレッジ**

| トピック | カバレッジ |
| --- | --- |
| 開発時モデルポイズニング | ✅ |
| 実行時モデルポイズニング |  |
| 使用時モデル窃取 | ✅ |
| トレーニングデータポイズニング |  |
| トレーニングデータ漏洩 |  |
| 実行時モデル窃取 |  |
| 回避 (敵対的入力に対するモデルのパフォーマンスをテストする) | ✅ |
| モデル反転 / メンバーシップ推論 | ✅ |
| モデルサービス拒否 |  |
| 直接プロンプトインジェクション |  |
| データ開示 |  |
| モデル入力漏洩 |  |
| 間接プロンプトインジェクション |  |
| 開発時モデル窃取 |  |
| インジェクションを含む出力 |  |

注:

- 開発時モデルポイズニング: 開発時に攻撃をシミュレートして脆弱性を評価する [*https://owaspai.org/goto/modelpoison/*](https://owaspai.org/goto/modelpoison/)
- 回避: 敵対的入力に対するモデルのパフォーマンスをテストする [*https://owaspai.org/goto/evasion/*](https://owaspai.org/goto/evasion/)
- 使用時モデル窃取: 使用時のモデル悪用のリスクを評価する [*https://owaspai.org/goto/modeltheftuse*](https://owaspai.org/goto/modeltheftuse/)
- モデル推論: *メンバーシップ攻撃と反転攻撃への露出を評価する*
*[https://owaspai.org/goto/modelinversionandmembership/](https://owaspai.org/goto/modelinversionandmembership/)*

### **ツール名: Armory**

| **ツール名: Armory** |  |
| --- | --- |
| 開発元/ソース | MITRE Corporation |
| GitHub 参照 | [https://github.com/twosixlabs/armory-library](https://github.com/twosixlabs/armory-library)[https://github.com/twosixlabs/armory](https://github.com/twosixlabs/armory) |
| 言語 | Python |
| ライセンス | MIT ライセンスの下でのオープンソース |
| 緩和策の提供 | 防止: No ❌ 検出: Yes ✅ |
| API の可用性 | Yes ✅ |

| 要素 | 詳細 |
| --- | --- |
| **人気** | - **GitHub スター:**  およそ 176 スター (2024 年現在) |
|  | - **GitHub フォーク:**  およそ 67 フォーク |
|  | - **Issues の数:** およそ  59 オープン状態, 733 クローズ済み, 貢献者 26 名 |
|  | - **傾向:** 特に防衛とサイバーセキュリティの分野で成長している。 |
| **コミュニティサポート** | - **Issues 活動:**  issues へ迅速に対応している (通常は数日から一週間以内に解決される)。 |
|  | - **ドキュメント:** 包括的だが、セキュリティに重点を置いており、敵対的な攻撃と防御に関する高度なチュートリアルを備えている。 |
|  | - **ディスカッションフォーラム:** GitHub で活発にディスカッションしている。セキュリティ固有のフォーラム (DARPA プロジェクト関連など) への参加もある。 |
|  | - **貢献者:** 40 名以上。ほとんどがセキュリティ専門家と研究者。 |
| **拡張性** | - **フレームワークサポート:** TensorFlow と Keras をネイティブにサポートし、PyTorch の統合オプションもいくつか備えている。 |
|  | - **大規模デプロイメント:** 主にセキュリティ関連のデプロイメントで使用される。セキュリティ以外のスケーラビリティについてはあまり文書化されていない。 |
| **統合** | - **互換性:** TensorFlow と Keras と相性が良い。堅牢性を高めるために IBM ART と統合する。 |
|  | - **API の可用性**: IBM ART と比較すると制限があるが、敵対的機械学習のユースケースには十分である。 |

**ツールの評価**

| **基準** | **高** | **中** | **低** |
| --- | --- | --- | --- |
| **人気** |  |  | ✅ |
| **コミュニティサポート** |  | ✅ |  |
| **Scalability** |  | ✅ |  |
| **統合の容易さ** | ✅ |  |  |

**データモダリティ**

| データモダリティ | サポートあり |
| --- | --- |
| テキスト | ✅ |
| 静止画 | ✅ |
| 音声 | ✅ |
| 動画 | ✅ |
| 表形式データ | ✅ |

**機械学習タスク**

| タスクタイプ | データモダリティ | サポートあり |
| --- | --- | --- |
| 分類 | すべて (データモダリティセクションを参照) | ✅ |
| 物体検出 | コンピュータビジョン | ✅ |
| 音声認識 | 音声 | ✅ |

**フレームワークの適用性**

| フレームワーク / ツール | カテゴリ | サポートあり |
| --- | --- | --- |
| Tensorflow | 深層学習, 生成 AI | ✅ |
| Keras | 深層学習, 生成 AI |  |
| PyTorch | 深層学習, 生成 AI | ✅ |
| MxNet | 深層学習 |  |
| Scikit-learn | 機械学習 |  |
| XGBoost | 機械学習 |  |
| LightGBM | 機械学習 |  |
| CatBoost | 機械学習 |  |
| GPy | 機械学習 |  |

**OWASP AI Exchange 脅威カバレッジ**

| トピック | カバレッジ |
| --- | --- |
| 開発時モデルポイズニング | ✅ |
| 実行時モデルポイズニング |  |
| 使用時モデル窃取 |  |
| トレーニングデータポイズニング |  |
| トレーニングデータ漏洩 |  |
| 実行時モデル窃取 |  |
| 回避 (敵対的入力に対するモデルのパフォーマンスをテストする) | ✅ |
| モデル反転 / メンバーシップ推論 |  |
| モデルサービス拒否 |  |
| 直接プロンプトインジェクション | ✅ |
| データ開示 |  |
| モデル入力漏洩 |  |
| 間接プロンプトインジェクション |  |
| 開発時モデル窃取 |  |
| インジェクションを含む出力 |  |

注:

- 開発時モデルポイズニング: 開発時に攻撃をシミュレートして脆弱性を評価する [*https://owaspai.org/goto/modelpoison/*](https://owaspai.org/goto/modelpoison/)
- 回避: 敵対的入力に対するモデルのパフォーマンスをテストする [*https://owaspai.org/goto/evasion/*](https://owaspai.org/goto/evasion/)
- プロンプトインジェクション: プロンプト設計の弱点を悪用して、望ましくない出力につながったり、モデルセーフガードをバイパスする、生成 AI モデルの堅牢性を評価する。
*https://owaspai.org/goto/promptinjection/*

### **ツール名: Foolbox**

| **ツール名: Foolbox** |  |
| --- | --- |
| 開発元/ソース | Foolbox の著者/開発者 |
| GitHub 参照 | [https://github.com/bethgelab/foolbox](https://github.com/bethgelab/foolbox) |
| 言語 | Python |
| ライセンス | MIT ライセンスの下でのオープンソース |
| 緩和策の提供 | 防止: No ❌ 検出: Yes ✅ |
| API の可用性 | Yes ✅ |

| 要素 | 詳細 |
| --- | --- |
| **人気** | - **GitHub スター:**  およそ 2,800 スター (2024 年現在) |
|  | - **GitHub フォーク:** およそ 428 フォーク |
|  | - **Issues の数:** およそ 21 オープン状態, 350 クローズ済み状態 |
|  | - **傾向:** 学術コミュニティからの一貫した最新情報により安定している。 |
| **コミュニティサポート** | - **Issues 活動:** 通常は一週間以内に解決している。 |
|  | - **ドキュメント:** 基本的なチュートリアルを含む中程度のドキュメント。研究に重点を置いている。 |
|  | - **ディスカッションフォーラム:** 主に学術的な場で議論されており、業界フォーラムの活動は限られている。 |
|  | - **貢献者:** 30 名以上。主に学会から。 |
| **拡張性** | - **フレームワークサポート:** TensorFlow, PyTorch, JAX と互換あり。 |
|  | - **大規模デプロイメント:** 大規模な業界デプロイメントにはスケーラビリティが限られており、研究と実験に重点を置いている。 |
| **統合** | - **互換性:** TensorFlow, PyTorch, JAX との強力な統合。 |

**ツールの評価**

| **基準** | **高** | **中** | **低** |
| --- | --- | --- | --- |
| **人気** |  | ✅ |  |
| **コミュニティサポート** |  | ✅ |  |
| **拡張性** |  |  | ✅ |
| **統合の容易さ** |  | ✅ |  |

**データモダリティ**

| データモダリティ | サポートあり |
| --- | --- |
| テキスト | ✅ |
| 静止画 | ✅ |
| 音声 |  |
| 動画 |  |
| 表形式データ |  |

**機械学習タスク**

| タスクタイプ | データモダリティ | サポートあり |
| --- | --- | --- |
| 分類 | すべて (データモダリティセクションを参照) | ✅ |
| 物体検出 | コンピュータビジョン | ✅ |
| 音声認識 | 音声 |  |

**フレームワークの適用性**

| フレームワーク / ツール | カテゴリ | サポートあり |
| --- | --- | --- |
| Tensorflow | 深層学習, 生成 AI | ✅ |
| Keras | 深層学習, 生成 AI | ✅ |
| PyTorch | 深層学習, 生成 AI | ✅ |
| MxNet | 深層学習 |  |
| Scikit-learn | 機械学習 |  |
| XGBoost | 機械学習 |  |
| LightGBM | 機械学習 |  |
| CatBoost | 機械学習 |  |
| GPy | 機械学習 |  |

**OWASP AI Exchange 脅威カバレッジ**

| トピック | カバレッジ |
| --- | --- |
| 開発時モデルポイズニング |  |
| 実行時モデルポイズニング |  |
| 使用時モデル窃取 |  |
| トレーニングデータポイズニング |  |
| トレーニングデータ漏洩 |  |
| 実行時モデル窃取 |  |
| 回避 (敵対的入力に対するモデルのパフォーマンスをテストする) | ✅ |
| モデル反転 / メンバーシップ推論 |  |
| モデルサービス拒否 |  |
| 直接プロンプトインジェクション |  |
| データ開示 |  |
| モデル入力漏洩 |  |
| 間接プロンプトインジェクション |  |
| 開発時モデル窃取 |  |
| インジェクションを含む出力 |  |

注:

回避: 敵対的入力に対するモデルのパフォーマンスをテストする

[*https://owaspai.org/goto/evasion/*](https://owaspai.org/goto/evasion/)

### **ツール名: DeepSec**

| **ツール名: DeepSec** |  |
| --- | --- |
| 開発元/ソース | シンガポール国立大学と共同で学術研究者チームによって開発されている。 |
| GitHub 参照 | [https://github.com/ryderling/DEEPSEC](https://github.com/ryderling/DEEPSEC) |
| 言語 | Python |
| ライセンス | Apache License 2.0 の下でのオープンソース |
| 緩和策の提供 | 防止: No ❌ 検出: Yes ✅ |
| API の可用性 | Yes ✅ |

| 要素 | 詳細 |
| --- | --- |
| **人気** | - **GitHub スター:** 209 (as of 2024) |
|  | - **GitHub フォーク:** およそ 70 |
|  | - **Issues の数:** およそ 15 オープン状態 |
|  | - **傾向:** ディープラーニングのセキュリティを重視して安定している。 |
| **コミュニティサポート** | - **Issues 活動:** 現在、問題と更新が進行中であり、アクティブなメンテナンスを示唆している。 |
|  | - **ドキュメント:** セットアップ、使用、貢献についてカバーしており、GitHub を通じて利用可能である。 |
|  | - **ディスカッションフォーラム:** GitHub Discussions セクションとコミュニティチャネルは開発者のやり取りをサポートしている。 |
|  | - **貢献者:** 小規模だが熱心な貢献者ベース。 |
| **拡張性** | - **フレームワークサポート:** 主に PyTorch と、TorchVision などの追加ライブラリをサポートしている。 |
|  | - **大規模デプロイメント:** 研究やテスト環境には適しているが、本番環境グレードのスケーリングには調整が必要となり得る。 |
| **統合** | - **互換性:** Python の機械学習ライブラリと互換している。 |

**ツールの評価**

| **基準** | **高** | **中** | **低** |
| --- | --- | --- | --- |
| **人気** |  |  | ✅ |
| **コミュニティサポート** |  |  | ✅ |
| **拡張性** |  |  | ✅ |
| **統合の容易さ** |  |  | ✅ |

**データモダリティ**

| データモダリティ | サポートあり |
| --- | --- |
| テキスト | ✅ |
| 静止画 | ✅ |
| 音声 |  |
| 動画 |  |
| 表形式データ |  |

**機械学習タスク**

| タスクタイプ | データモダリティ | サポートあり |
| --- | --- | --- |
| 分類 | すべて (データモダリティセクションを参照) | ✅ |
| 物体検出 | コンピュータビジョン |  |
| 音声認識 | 音声 |  |

**フレームワークの適用性**

| フレームワーク / ツール | カテゴリ | サポートあり |
| --- | --- | --- |
| Tensorflow | 深層学習, 生成 AI | ✅ |
| Keras | 深層学習, 生成 AI |  |
| PyTorch | 深層学習, 生成 AI | ✅ |
| MxNet | 深層学習 |  |
| Scikit-learn | 機械学習 |  |
| XGBoost | 機械学習 |  |
| LightGBM | 機械学習 |  |
| CatBoost | 機械学習 |  |
| GPy | 機械学習 |  |

**OWASP AI Exchange 脅威カバレッジ**

| トピック | カバレッジ |
| --- | --- |
| 開発時モデルポイズニング |  |
| 実行時モデルポイズニング |  |
| 使用時モデル窃取 |  |
| トレーニングデータポイズニング |  |
| トレーニングデータ漏洩 |  |
| 実行時モデル窃取 |  |
| 回避 (敵対的入力に対するモデルのパフォーマンスをテストする) | ✅ |
| モデル反転 / メンバーシップ推論 |  |
| モデルサービス拒否 |  |
| 直接プロンプトインジェクション |  |
| データ開示 |  |
| モデル入力漏洩 |  |
| 間接プロンプトインジェクション |  |
| 開発時モデル窃取 |  |
| インジェクションを含む出力 |  |

注:

回避: 敵対的入力に対するモデルのパフォーマンスをテストする

[*https://owaspai.org/goto/evasion/*](https://owaspai.org/goto/evasion/)

### ツール名: TextAttack

| **ツール名: TextAttack** |  |
| --- | --- |
| 開発元/ソース | メリーランド大学と Google Research の研究者によって開発されている。 |
| GitHub 参照 | [https://github.com/QData/TextAttack](https://github.com/QData/TextAttack) |
| 言語 | Python |
| ライセンス | MIT ライセンスの下でのオープンソース |
| 緩和策の提供 | 防止: No ❌ 検出: Yes ✅ |
| API の可用性 | Yes ✅ |

| 要素 | 詳細 |
| --- | --- |
| **人気** | - **GitHub スター:** およそ 3.7K (as of 2024) |
|  | - **GitHub フォーク:** およそ 455 |
|  | - **Issues の数:** およそ 130 オープン状態 |
|  | - **傾向:** 継続的なアップデートと定期的な貢献で人気がある。 |
| **コミュニティサポート** | - **Issues 活動:** Issues は頻繁なバグ修正と改善で積極的に管理されている。 |
|  | - **ドキュメント:** 攻撃構成からカスタムデータセットの統合まですべてを網羅した詳細なドキュメントが用意されている。 |
|  | - **ディスカッションフォーラム:** GitHub Discussions は、技術的な質問やコミュニティの交流のサポートで、活発である。 |
|  | - **貢献者:** 20 名以上。多様な意見と強化を反映している。 |
| **拡張性** | - **フレームワークサポート:** PyTorch の NLP モデルをサポートし、Hugging Face の Transformers と Datasets ライブラリとうまく統合し、幅広い NLP タスクと互換がある。 |
|  | - **大規模デプロイメント:** 主に研究と実験用に設計されており、大規模なデプロイメントにはカスタマイズを必要とする可能性がある。 |
| **統合** | - **互換性:** モデルに依存せず、インタフェース要件を満たす限り、さまざまな NLP モデルアーキテクチャで使用できる。 |

**ツールの評価**

| **基準** | **高** | **中** | **低** |
| --- | --- | --- | --- |
| **人気** | ✅ |  |  |
| **コミュニティサポート** | ✅ |  |  |
| **拡張性** |  | ✅ |  |
| **統合の容易さ** | ✅ |  |  |

**データモダリティ**

| データモダリティ | サポートあり |
| --- | --- |
| テキスト | ✅ |
| 静止画 |  |
| 音声 |  |
| 動画 |  |
| 表形式データ |  |

**機械学習タスク**

| タスクタイプ | データモダリティ | サポートあり |
| --- | --- | --- |
| 分類 | すべて (データモダリティセクションを参照) | ✅ |
| 物体検出 | コンピュータビジョン |  |
| 音声認識 | 音声 |  |

**フレームワークの適用性**

| フレームワーク / ツール | カテゴリ | サポートあり |
| --- | --- | --- |
| Tensorflow | 深層学習, 生成 AI | ✅ |
| Keras | 深層学習, 生成 AI |  |
| PyTorch | 深層学習, 生成 AI | ✅ |
| MxNet | 深層学習 |  |
| Scikit-learn | 機械学習 |  |
| XGBoost | 機械学習 |  |
| LightGBM | 機械学習 |  |
| CatBoost | 機械学習 |  |
| GPy | 機械学習 |  |

**OWASP AI Exchange 脅威カバレッジ**

| トピック | カバレッジ |
| --- | --- |
| 開発時モデルポイズニング | ✅ |
| 実行時モデルポイズニング |  |
| 使用時モデル窃取 |  |
| トレーニングデータポイズニング |  |
| トレーニングデータ漏洩 |  |
| 実行時モデル窃取 |  |
| 回避 (敵対的入力に対するモデルのパフォーマンスをテストする) | ✅ |
| モデル反転 / メンバーシップ推論 |  |
| モデルサービス拒否 |  |
| 直接プロンプトインジェクション |  |
| データ開示 |  |
| モデル入力漏洩 |  |
| 間接プロンプトインジェクション |  |
| 開発時モデル窃取 |  |
| インジェクションを含む出力 |  |

注:

- 開発時モデルポイズニング: 開発時に攻撃をシミュレートして脆弱性を評価する [*https://owaspai.org/goto/modelpoison/*](https://owaspai.org/goto/modelpoison/)
- 回避: 敵対的入力に対するモデルのパフォーマンスをテストする [*https://owaspai.org/goto/evasion/*](https://owaspai.org/goto/evasion/)

## 生成 AI レッドチーミングのためのオープンソースツール

This sub section covers the following tools for security testing Generative AI: PyRIT, Garak, Prompt Fuzzer, Guardrail, and Promptfoo.

A list of GenAI test tools can also be found at the [OWASP GenAI security project solutions page](https://genai.owasp.org/ai-security-solutions-landscape/) (click the category 'Test & Evaluate'. This project also published a [GenAI Red Teaming guide](https://genai.owasp.org/resource/genai-red-teaming-guide/).


### ツール名: PyRIT

| **ツール名: PyRIT** |  |
| --- | --- |
| 開発元/ソース | Microsoft |
| GitHub 参照 | [https://github.com/Azure/PyRIT](https://github.com/Azure/PyRIT) |
| 言語 | Python |
| ライセンス | MIT ライセンスの下でのオープンソース |
| 緩和策の提供 | 防止: No ❌ 検出: Yes ✅ |
| API の可用性 | Yes ✅ , library based |

| 要素 | 詳細 |
| --- | --- |
| **人気** | - **GitHub スター:** およそ 2k (2024 年 12 月現在) |
|  | - **GitHub フォーク:** およそ 384 フォーク |
|  | - **Issues の数:** およそ 63 オープン状態, 79 クローズ済み状態 |
|  | - **傾向:** 継続的なアップデートと業界の採用で敵対的堅牢性に対して着実に成長 |
| **コミュニティサポート** | - **Issues 活動:** Issues are being addressed within a week. |
|  | - **ドキュメント:** Detailed and regularly updated, with comprehensive guides and API documentation. |
|  | - **ディスカッションフォーラム:** Active GitHub issues |
|  | - **貢献者:** Over 125 contributors. |
| **拡張性** | - **フレームワークサポート:** Scales across TensorFlow, PyTorch and supports models on local like ONNX |
|  | - **大規模デプロイメント:** Can be extended to Azure pipeline. |
| **統合** | - **互換性:** Compatible with majority of LLMs |

**ツールの評価**

| **基準** | **高** | **中** | **低** |
| --- | --- | --- | --- |
| **人気** |  | ✅ |  |
| **コミュニティサポート** | ✅ |  |  |
| **拡張性** | ✅ |  |  |
| **統合の容易さ** |  | ✅ |  |

**データモダリティ**

| データモダリティ | サポートあり |
| --- | --- |
| テキスト | ✅ |
| 静止画 |  |
| 音声 |  |
| 動画 |  |
| 表形式データ |  |

**機械学習タスク**

| タスクタイプ | データモダリティ | サポートあり |
| --- | --- | --- |
| 分類 | すべて (データモダリティセクションを参照) | ✅ |
| 物体検出 | コンピュータビジョン | ✅ |
| 音声認識 | 音声 | ✅ |

**フレームワークの適用性**

| フレームワーク / ツール | カテゴリ | サポートあり |
| --- | --- | --- |
| Tensorflow | 深層学習, 生成 AI | ✅ |
| PyTorch | 深層学習, 生成 AI | ✅ |
| Azure OpenAI | GenAI | ✅ |
| Huggingface | ML, GenAI | ✅ |
| Azure managed endpoints | Machine Learning Deployment | ✅ |
| Cohere | GenAI | ✅ |
| Replicate Text Models	 | GenAI | ✅ |
| OpenAI API | GenAI | ✅ |
| GGUF (Llama.cpp) | GenAI, Lightweight Inference | ✅ |

**OWASP AI Exchange 脅威カバレッジ**

| トピック | カバレッジ |
| --- | --- |
| 開発時モデルポイズニング |  |
| 実行時モデルポイズニング |  |
| 使用時モデル窃取 |  |
| トレーニングデータポイズニング |  |
| トレーニングデータ漏洩 |  |
| 実行時モデル窃取 |  |
| 回避 (敵対的入力に対するモデルのパフォーマンスをテストする) | ✅ |
| モデル反転 / メンバーシップ推論 |  |
| モデルサービス拒否 |   |
| 直接プロンプトインジェクション |  ✅ |
| データ開示 |   |
| モデル入力漏洩 |   |
| 間接プロンプトインジェクション |  |
| 開発時モデル窃取 |  |
| インジェクションを含む出力 |  |

注:

- 回避: 敵対的入力に対するモデルのパフォーマンスをテストする [*https://owaspai.org/goto/evasion/*](https://owaspai.org/goto/evasion/)
- プロンプトインジェクション: プロンプト設計の弱点を悪用して、望ましくない出力につながったり、モデルセーフガードをバイパスする、生成 AI モデルの堅牢性を評価する。 *https://owaspai.org/goto/promptinjection/*

### ツール名: Garak

| **ツール名: Garak** |  |
| --- | --- |
| 開発元/ソース | NVIDIA |
| GitHub 参照 | https://docs.garak.ai/garak  moved to https://github.com/NVIDIA/garak
Literature: https://arxiv.org/abs/2406.11036
https://github.com/NVIDIA/garak |
| 言語 | Python |
| ライセンス | Apache 2.0 License |
| 緩和策の提供 | 防止: No ❌ 検出: Yes ✅ |
| API の可用性 | Yes ✅ |

| 要素 | 詳細 |
| --- | --- |
| **人気** | - **GitHub スター:** およそ 3,5K stars (as of Dec 2024) |
|  | - **GitHub フォーク:** およそ 306 フォーク |
|  | - **Issues の数:** およそ 303 オープン状態, 299 クローズ済み状態 |
|  | - **傾向:** Growing, particularly with in attack generation, and LLM vulnerability scanning. |
| **コミュニティサポート** | - **Issues 活動:** Actively responds to the issues and tries to close it within a week |
|  | - **ドキュメント:** Detailed documentation with guidance and example experiments. |
|  | - **ディスカッションフォーラム:**  Active GitHub discussions, as well as discord. |
|  | - **貢献者:** Over 27 contributors. |
| **拡張性** | - **フレームワークサポート:** Supports various LLMs from hugging face, openai api, litellm.   |
|  | - **大規模デプロイメント:** Mostly used in attack LLM, detect LLM failures and assessing LLM security. Can be integrated with NeMo Guardrails |
| **統合** | - **互換性:**  All LLMs, Nvidia models |

**ツールの評価**

| **基準** | **高** | **中** | **低** |
| --- | --- | --- | --- |
| **人気** | ✅ |  |  |
| **コミュニティサポート** |  | ✅ |  |
| **拡張性** |  | ✅ |  |
| **統合の容易さ** |  | ✅ |  |

**データモダリティ**

| データモダリティ | サポートあり |
| --- | --- |
| テキスト | ✅ |
| 静止画 |  |
| 音声 |  |
| 動画 |  |
| 表形式データ |  |

**機械学習タスク**

| タスクタイプ | データモダリティ | サポートあり |
| --- | --- | --- |
| 分類 | すべて (データモダリティセクションを参照) | ✅ |
| 物体検出 | コンピュータビジョン | ✅ |
| 音声認識 | 音声 |  |

**フレームワークの適用性**

| フレームワーク / ツール | カテゴリ | サポートあり |
| --- | --- | --- |
| Tensorflow | 深層学習, 生成 AI |  |
| PyTorch | 深層学習, 生成 AI | ✅ |
| Azure OpenAI | GenAI |  |
| Huggingface | ML, GenAI | ✅ |
| Azure managed endpoints | Machine Learning Deployment |  |
| Cohere | GenAI | ✅ |
| Replicate Text Models	 | GenAI | ✅ |
| OpenAI API | GenAI | ✅ |
| GGUF (Llama.cpp) | GenAI, Lightweight Inference | ✅ |
| OctoAI | GenAI | ✅ |

**OWASP AI Exchange 脅威カバレッジ**

| トピック | カバレッジ |
| --- | --- |
| 開発時モデルポイズニング |  |
| 実行時モデルポイズニング |  |
| 使用時モデル窃取 |  |
| トレーニングデータポイズニング |  |
| トレーニングデータ漏洩 |  |
| 実行時モデル窃取 |  |
| 回避 (敵対的入力に対するモデルのパフォーマンスをテストする) | ✅ |
| モデル反転 / メンバーシップ推論 |  |
| モデルサービス拒否 |  |
| 直接プロンプトインジェクション | ✅ |
| データ開示 |  |
| モデル入力漏洩 |  |
| 間接プロンプトインジェクション |  |
| 開発時モデル窃取 |  |
| インジェクションを含む出力 |  |
- 回避: 敵対的入力に対するモデルのパフォーマンスをテストする [*https://owaspai.org/goto/evasion/*](https://owaspai.org/goto/evasion/)
- プロンプトインジェクション: プロンプト設計の弱点を悪用して、望ましくない出力につながったり、モデルセーフガードをバイパスする、生成 AI モデルの堅牢性を評価する。
*https://owaspai.org/goto/promptinjection/*

### ツール名: Prompt Fuzzer

| **ツール名: Prompt Fuzzer** |  |
| --- | --- |
| 開発元/ソース | Prompt Security |
| GitHub 参照 | [https://github.com/prompt-security/ps-fuzz](https://github.com/prompt-security/ps-fuzz) |
| 言語 | Python |
| ライセンス | MIT ライセンスの下でのオープンソース |
| 緩和策の提供 | 防止: No ❌ 検出: Yes ✅ |
| API の可用性 | Yes ✅ |

| 要素 | 詳細 |
| --- | --- |
| **人気** | - **GitHub スター:** およそ 427 stars (as of Dec 2024) |
|  | - **GitHub フォーク:** およそ 56 フォーク |
|  | - **Issues の数:**  およそ 10 オープン状態, 6 クローズ済み状態 |
|  | - **傾向:** Not updating since Aug |
| **コミュニティサポート** | - **Issues 活動:** Not updated nor solved any bugs since July. |
|  | - **ドキュメント:** Moderate documentation with few examples |
|  | - **ディスカッションフォーラム:**  GitHub issue forums |
|  | - **貢献者:** Over 10 contributors. |
| **拡張性** | - **フレームワークサポート:** Python and docker image. |
|  | - **大規模デプロイメント:** It only assesses the security of your GenAI application's system prompt against various dynamic LLM-based attacks, so it can be integrated with current env. |
| **統合** | - **互換性:**  Any device. |

**ツールの評価**

| **基準** | **高** | **中** | **低** |
| --- | --- | --- | --- |
| **人気** |  |  | ✅ |
| **コミュニティサポート** |  |  | ✅ |
| **拡張性** |  | ✅ |  |
| **統合の容易さ** |  | ✅ |  |

**データモダリティ**

| データモダリティ | サポートあり |
| --- | --- |
| テキスト | ✅ |
| 静止画 |  |
| 音声 |  |
| 動画 |  |
| 表形式データ |  |

**機械学習タスク**

| タスクタイプ | データモダリティ | サポートあり |
| --- | --- | --- |
| 分類 | すべて (データモダリティセクションを参照) | ✅ |
| 物体検出 | コンピュータビジョン |  |
| 音声認識 | 音声 |  |

**フレームワークの適用性**

*(LLM Model agnostic in the API mode of use)*

| フレームワーク / ツール | カテゴリ | サポートあり |
| --- | --- | --- |
| Tensorflow | 深層学習, 生成 AI |  |
| PyTorch | 深層学習, 生成 AI |  |
| Azure OpenAI | GenAI |  |
| Huggingface | ML, GenAI |  |
| Azure managed endpoints | Machine Learning Deployment |  |
| Cohere | GenAI |  |
| Replicate Text Models | GenAI |  |
| OpenAI API | GenAI | ✅ |
| GGUF (Llama.cpp) | GenAI, Lightweight Inference |  |
| OctoAI | GenAI |  |

**OWASP AI Exchange 脅威カバレッジ**

| トピック | カバレッジ |
| --- | --- |
| 開発時モデルポイズニング |  |
| 実行時モデルポイズニング |  |
| 使用時モデル窃取 |  |
| トレーニングデータポイズニング |  |
| トレーニングデータ漏洩 |  |
| 実行時モデル窃取 |  |
| 回避 (敵対的入力に対するモデルのパフォーマンスをテストする) | ✅ |
| モデル反転 / メンバーシップ推論 |  |
| モデルサービス拒否 |  |
| 直接プロンプトインジェクション | ✅ |
| データ開示 |  |
| モデル入力漏洩 |  |
| 間接プロンプトインジェクション |  |
| 開発時モデル窃取 |  |
| インジェクションを含む出力 |  |

注:

- 回避: 敵対的入力に対するモデルのパフォーマンスをテストする [*https://owaspai.org/goto/evasion/*](https://owaspai.org/goto/evasion/)
- プロンプトインジェクション: プロンプト設計の弱点を悪用して、望ましくない出力につながったり、モデルセーフガードをバイパスする、生成 AI モデルの堅牢性を評価する。 *https://owaspai.org/goto/promptinjection/*

### ツール名: Guardrail

| **ツール名: Guardrail** |  |
| --- | --- |
| 開発元/ソース | Guardrails AI |
| GitHub 参照 | [GitHub - guardrails-ai/guardrails: Adding guardrails to large language models.](https://github.com/guardrails-ai/guardrails) | [Guardrails Hub | Guardrails AI](https://hub.guardrailsai.com/) |
| 言語 | Python |
| ライセンス | Apache 2.0 License |
| 緩和策の提供 | 防止: Yes ✅ 検出: Yes ✅ |
| API の可用性 |  |

| 要素 | 詳細 |
| --- | --- |
| **人気** | - **GitHub スター:** およそ 4,3K (as 2024) |
|  | - **GitHub フォーク:** およそ 326 |
|  | - **Issues の数:**  およそ 296 Closed, 40 Open.  |
|  | - **傾向:** Steady growth with consistent and timely updates. |
| **コミュニティサポート** | - **Issues 活動:** Issues are mostly solved within weeks. |
|  | - **ドキュメント:** Detailed documentation with examples and user guide |
|  | - **ディスカッションフォーラム:**  Primarily github issues and also, support is available on discord Server and twitter. |
|  | - **貢献者:** Over 60 contributors |
| **拡張性** | - **フレームワークサポート:** Supports Pytorch. Language: Python and Javascript. Working to add more support |
|  | - **大規模デプロイメント:** Can be extended to Azure, langchain. |
| **統合** | - **互換性:**  Compatible with various open source LLMs like OpenAI, Gemini, Anthropic. |

**ツールの評価**

| **基準** | **高** | **中** | **低** |
| --- | --- | --- | --- |
| **人気** | ✅ |  |  |
| **コミュニティサポート** | ✅ |  |  |
| **拡張性** |  | ✅ |  |
| **統合の容易さ** | ✅ |  |  |

**データモダリティ**

| データモダリティ | サポートあり |
| --- | --- |
| テキスト | ✅ |
| 静止画 |  |
| 音声 |  |
| 動画 |  |
| 表形式データ |  |

**機械学習タスク**

| タスクタイプ | データモダリティ | サポートあり |
| --- | --- | --- |
| 分類 | すべて (データモダリティセクションを参照) | ✅ |
| 物体検出 | コンピュータビジョン |  |
| 音声認識 | 音声 |  |

**フレームワークの適用性**

| フレームワーク / ツール | カテゴリ | サポートあり |
| --- | --- | --- |
| Tensorflow | 深層学習, 生成 AI |  |
| PyTorch | 深層学習, 生成 AI | ✅ |
| Azure OpenAI | GenAI | ✅ |
| Huggingface | ML, GenAI | ✅ |
| Azure managed endpoints | Machine Learning Deployment |  |
| Cohere | GenAI | ✅ |
| Replicate Text Models | GenAI |  |
| OpenAI API | GenAI | ✅ |
| GGUF (Llama.cpp) | GenAI, Lightweight Inference |  |
| OctoAI | GenAI |  |

**OWASP AI Exchange 脅威カバレッジ**

| トピック | カバレッジ |
| --- | --- |
| 開発時モデルポイズニング |  |
| 実行時モデルポイズニング |  |
| 使用時モデル窃取 |  |
| トレーニングデータポイズニング |  |
| トレーニングデータ漏洩 |  |
| 実行時モデル窃取 |  |
| 回避 (敵対的入力に対するモデルのパフォーマンスをテストする) | ✅ |
| モデル反転 / メンバーシップ推論 |  |
| モデルサービス拒否 |  |
| 直接プロンプトインジェクション | ✅ |
| データ開示 |  |
| モデル入力漏洩 |  |
| 間接プロンプトインジェクション |  |
| 開発時モデル窃取 |  |
| インジェクションを含む出力 |  |

注:

- 回避: 敵対的入力に対するモデルのパフォーマンスをテストする [*https://owaspai.org/goto/evasion/*](https://owaspai.org/goto/evasion/)
- プロンプトインジェクション: プロンプト設計の弱点を悪用して、望ましくない出力につながったり、モデルセーフガードをバイパスする、生成 AI モデルの堅牢性を評価する。 *https://owaspai.org/goto/promptinjection/*

### ツール名: Promptfoo

| **ツール名: Promptfoo** |  |
| --- | --- |
| 開発元/ソース | Promptfoo community |
| GitHub 参照 | [https://github.com/promptfoo/promptfoo](https://github.com/promptfoo/promptfoo) | [Types of LLM vulnerabilities | promptfoo](https://www.promptfoo.dev/docs/red-team/llm-vulnerability-types/) |
| 言語 | Python, NodeJS |
| ライセンス | MIT ライセンスの下でのオープンソース |
|  | This project is licensed under multiple licenses:

1. The main codebase is licensed under the MIT License (see below)
2. The `/src/redteam/` directory is proprietary and licensed under the Promptfoo Enterprise License
3. Some third-party components have their own licenses as indicated by LICENSE files in their respective directories |
| 緩和策の提供 | 防止: Yes ✅ 検出: Yes ✅ |
| API の可用性 | Yes ✅  |

| 要素 | 詳細 |
| --- | --- |
| **人気** | - **GitHub スター:** およそ 4.3K スター (2024 年現在) |
|  | - **GitHub フォーク:**  およそ 320 フォーク |
|  | - **Issues の数:** およそ 523 closed, 108 open |
|  | - **傾向:** Consistent update |
| **コミュニティサポート** | - **Issues 活動:** Issues are  addressed within acouple of days. |
|  | - **ドキュメント:** Detailed documentation with user guide and examples. |
|  | - **ディスカッションフォーラム:** Active Github issue and also support available on Discord |
|  | - **貢献者:** Over 113 contributors. |
| **拡張性** | - **フレームワークサポート:**  Language: JavaScript |
|  | - **大規模デプロイメント:** Enterprise version available, that supports cloud deployment. |
| **統合** | - **互換性:** Compatible with majority of the LLMs |

**ツールの評価**

| **基準** | **高** | **中** | **低** |
| --- | --- | --- | --- |
| **人気** | ✅ |  |  |
| **コミュニティサポート** | ✅ |  |  |
| **拡張性** |  | ✅ |  |
| **統合の容易さ** |  | ✅ |  |

**データモダリティ**

| データモダリティ | サポートあり |
| --- | --- |
| テキスト | ✅ |
| 静止画 |  |
| 音声 |  |
| 動画 |  |
| 表形式データ |  |

**機械学習タスク**

| タスクタイプ | データモダリティ | サポートあり |
| --- | --- | --- |
| 分類 | すべて (データモダリティセクションを参照) | ✅ |
| 物体検出 | コンピュータビジョン |  |
| 音声認識 | 音声 |  |

**フレームワークの適用性**

| フレームワーク / ツール | カテゴリ | サポートあり |
| --- | --- | --- |
| Tensorflow | 深層学習, 生成 AI |  |
| PyTorch | 深層学習, 生成 AI |  |
| Azure OpenAI | GenAI | ✅ |
| Huggingface | ML, GenAI | ✅ |
| Azure managed endpoints | Machine Learning Deployment |  |
| Cohere | GenAI | ✅ |
| Replicate Text Models | GenAI | ✅ |
| OpenAI API | GenAI | ✅ |
| GGUF (Llama.cpp) | GenAI, Lightweight Inference | ✅ |
| OctoAI | GenAI |  |

**OWASP AI Exchange 脅威カバレッジ**

| トピック | カバレッジ |
| --- | --- |
| 開発時モデルポイズニング |  |
| 実行時モデルポイズニング |  |
| 使用時モデル窃取 |  |
| トレーニングデータポイズニング |  |
| トレーニングデータ漏洩 |  |
| 実行時モデル窃取 |  |
| 回避 (敵対的入力に対するモデルのパフォーマンスをテストする) | ✅ |
| モデル反転 / メンバーシップ推論 |  |
| モデルサービス拒否 |   |
| 直接プロンプトインジェクション |   |
| データ開示 |   |
| モデル入力漏洩 |   |
| 間接プロンプトインジェクション | ✅ |
| 開発時モデル窃取 |  |
| インジェクションを含む出力 |  |

注:

- Model theft through use:Evaluates risks of model exploitation during usage  [*https://owaspai.org/goto/modeltheftuse/*](https://owaspai.org/goto/modeltheftuse/)
- プロンプトインジェクション: プロンプト設計の弱点を悪用して、望ましくない出力につながったり、モデルセーフガードをバイパスする、生成 AI モデルの堅牢性を評価する。
*[https://owaspai.org/goto/promptinjection/](https://owaspai.org/goto/promptinjection/)*

## ツール評価
This section rates the discussed tools by Popularity, Community Support, Scalability and Integration.

[![](https://owaspai.org/images/testtoolrating.png)](https://owaspai.org/images/testtoolrating.png)

| **Attribute** | High | Medium | Low |
| --- | --- | --- | --- |
| 人気 | >3,000 stars | 1,000–3,000 stars | <1,000 stars |
| コミュニティサポート | >100 contributors, quick response (<3 days) | 50–100 contributors, response in 3–14 days | <50 contributors, slow response (>14 days) |
| 拡張性 | Proven enterprise-grade, multi-framework | Moderate scalability, limited frameworks | Research focused, small-scale |
| 統合 | Broad compatibility | Limited compatibility, narrow use-case | Minimal or no integration, research tools only |

Disclaimer on the use of the Assessment:

- ***Scope of Assessment: This review exclusively focuses on open-source RedTeaming tools. Proprietary or commercial solutions were not included in this evaluation.***
- ***Independent Review: The evaluation is independent and based solely on publicly available information from sources such as GitHub repositories, official documentation, and related community discussions.***
- ***Tool Version and Relevance: The information and recommendations provided in this assessment are accurate as of September 2024. Any future updates, enhancements, or changes to these tools should be verified directly via the provided links or respective sources to ensure continued relevance.***

***Tool Fit and Usage:***

*The recommendations in this report should be considered based on your organization's specific use case, scale, and security posture. Some tools may offer advanced features that may not be necessary for smaller projects or environments, while others may be better suited to specific frameworks or security goals.*
