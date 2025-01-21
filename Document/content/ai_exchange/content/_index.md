---
---

<img src="https://github.com/OWASP/www-project-ai-security-and-privacy-guide/blob/main/assets/images/aixlogosml.jpg?raw=true"> <!-- {{< image-centered src="/images/aixlogosml.jpg" alt="OWASP AI Exchange Logo" >}} -->

> AI セキュリティに関する頼りになる情報源へようこそ。AI とデータ中心のシステムをセキュリティの脅威から保護する方法に関する 170 ページ以上の包括的なガイダンスで、国際標準に直接反映されます。コミュニティによって作成され、コミュニティにオープンソースとして提供されます。[OWASP AI セキュリティおよびプライバシーガイド](https://owasp.org/www-project-ai-security-and-privacy-guide/) の一部です。

<!-- {{< spacer height="40" >}} -->

<!-- {{< cards >}} -->
- [憲章](charter.md)    <!-- {{< small-card link="/charter" title="憲章" icon="document-text" >}} -->
- [私たちとつながろう！](connect.md)    <!-- {{< small-card link="/connect" title="私たちとつながろう！" icon="chat" >}} -->
- [貢献](contribute.md)    <!-- {{< small-card link="/contribute" title="貢献" icon="star" >}} -->
- [登録](https://forms.gle/XwEEK52y4iZQChuJ6)    <!-- {{< small-card link="https://forms.gle/XwEEK52y4iZQChuJ6" title="登録" icon="login" >}} -->
- [メディア](media.md)    <!-- {{< small-card link="/media" title="メディア" icon="speakerphone" >}} -->
- [周期表](docs/ai_security_overview.md#periodic-table-of-ai-security)    <!-- {{< small-card link="/goto/periodictable/" title="周期表" icon="document-text">}} -->
<!-- {{< /cards >}} -->

## コンテンツ

<!-- {{< cards >}} -->
- [0. AI セキュリティ概要](docs/ai_security_overview.md)    <!-- {{< small-card link="/docs/ai_security_overview/" title="0. AI セキュリティ概要">}} -->
- [1. 一般的なコントロール](docs/1_general_controls.md)    <!-- {{< small-card link="/docs/1_general_controls/" title="1. 一般的なコントロール">}} -->
- [2. 使用による脅威](docs/2_threats_through_use.md)    <!-- {{< small-card link="/docs/2_threats_through_use/" title="2. 使用による脅威">}} -->
- [3. 開発時の脅威](docs/3_development_time_threats.md)    <!-- {{< small-card link="/docs/3_development_time_threats/" title="3. 開発時の脅威">}} -->
- [4. 実行時のアプリケーションのセキュリティ脅威](docs/4_runtime_application_security_threats.md)    <!-- {{< small-card link="/docs/4_runtime_application_security_threats/" title="4. 実行時のアプリケーションのセキュリティ脅威">}} -->
- [参考情報](docs/ai_security_references.md)    <!-- {{< small-card link="/docs/ai_security_references/" title="References">}} -->
<!-- {{< /cards >}} -->

## 趣旨

OWASP AI Exchange は AI とデータ中心のシステムのセキュリティに関するグローバルな議論をオープンソース化しました。これは AI の脅威、脆弱性、コントロールの包括的な概要を提供することで、AI のセキュリティ標準と規制の開発を促進するためのオープンな共同プロジェクトです。このコンテンツは EU AI 法、ISO/IEC 27090 (AI セキュリティ)、[OWASP ML Top 10](https://mltop10.info/)、[OWASP LLM Top 10](https://llmtop10.com/)、[OpenCRE](https://opencre.org) の標準に影響しており、セキュリティチャットボット [OpenCRE-Chat](https://opencre.org/chatbot) を通じて AI Exchange コンテンツを提供するために使用したいと考えています。

データ中心のシステムは、AI システムと、AI Exchange の脅威とコントロール (データポイズニング、データサプライチェーンマネジメント、データパイプラインセキュリティなど) の多くに関連する AI モデルを持たない「ビッグデータ」システム (データウェアハウス、BI、レポーティング、ビッグデータなど) に分けられます。

私たちの **使命** は、コンセンサスのための信頼できる情報源となり、連携を促進し、イニシアチブ間のコラボレーションを推進することです。標準を整えるのではなく、標準を推進することです。言い換えると、AI セキュリティに携わる専門家のブックマークの上位に入るということです。そうすることで、誰もが洞察を見つけて共有できる安全でオープンかつ独立した場所を提供します。[AI Exchange LinkedIn ページ](https://www.linkedin.com/company/owasp-ai-exchange/) を参照してください。

AI Exchange はここ [owaspai.org](https://owaspai.org) で展示され、[GitHub リポジトリ](https://github.com/OWASP/www-project-ai-security-and-privacy-guide/tree/main/content/ai_exchange/content) (_Edit on Github_ のリンクを参照してください)。これは AI セキュリティの専門知識を世界的に交換するための **オープンソースの生きた出版物** であり、[OWASP AI セキュリティおよびプライバシーガイド](https://owasp.org/www-project-ai-security-and-privacy-guide/) プロジェクトの一部です。「コンテンツ」の下にある複数のセクションから成る、ひとまとまりのリソースとして構成されており、それぞれがこのウェブサイト上のページとして現れます。

<p xmlns:cc="http://creativecommons.org/ns#" xmlns:dct="http://purl.org/dc/terms/"><span property="cc:attributionName">AI セキュリティコミュニティ</span> による <a property="dct:title" rel="cc:attributionURL" href="https://owaspai.org">OWASP AI Exchange</a> には <a href="http://creativecommons.org/publicdomain/zero/1.0?ref=chooser-v1" target="_blank" rel="license noopener noreferrer" style="display:inline-block;">CC0 1.0</a> のマークが付けられており、著作権や帰属を明示することなく、どの部分でも自由に利用できることを意味します。可能であれば、読者がより多くの情報を見つけられるように、OWASP AI Exchange のクレジットやリンクを記載していただけると幸いです。</p>

## OWASP AI イニシアチブ

<!-- {{< cards >}} -->
- [OWASP AI Exchange](https://owaspai.org/)    <!-- {{< small-card link="https://owaspai.org/" title="OWASP AI Exchange (this)" icon="lock-closed" >}} -->
- [AI セキュリティおよびプライバシーガイド](https://owasp.org/www-project-ai-security-and-privacy-guide/)    <!-- {{< small-card link="https://owasp.org/www-project-ai-security-and-privacy-guide/" title="AI セキュリティおよびプライバシーガイド" icon="lock-closed" >}} -->
- [LLM Top 10](https://llmtop10.com/)    <!-- {{< small-card link="https://llmtop10.com/" title="LLM Top 10" icon="brain" >}} -->
- [ML Top 10](https://mltop10.info/)    <!-- {{< small-card link="https://mltop10.info/" title="ML Top 10" icon="machinelearning" >}} -->
<!-- {{< /cards >}} -->
