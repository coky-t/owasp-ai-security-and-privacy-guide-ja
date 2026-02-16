# OWASP AI Exchange フラグシッププロジェクト

[owaspai.org](http://owaspai.org/) にある OWASP AI Exchange の GitHub リポジトリへようこそ。これは、世界中の専門家の協力により AI の脅威とコントロールを収集する、生きたドキュメントセットです。

この取り組みの目標は、コミュニティの協力を通じて AI セキュリティおよびプライバシーに関する最先端の情報を収集し、明確に提示することです。

## プロジェクトリーダー

- [Rob van der Veer (Software Improvement Group)](https://www.linkedin.com/in/robvanderveer/) - [rob.vanderveer@owasp.org](mailto:rob.vanderveer@owasp.org)

## テクノロジ

owaspai.org のウェブサイトは、CI/CD パイプラインの一部である Hugo と呼ばれるテクノロジによって、この GitHub リポジトリからレンダリングされています。検索は Hugo ビルド後に実行する [Pagefind](https://pagefind.app/) を基盤としています。

### ローカルでサイト (検索を含む) をテストする

リポジトリのルートから (Hugo は `npx` を介して実行されるため、インストールは必要ありません):

```bash
npm run test:site
```

これはサイトをビルドし、Pagefind 検索インデックスを作成し、**http://localhost:3000** で機能します。その URL を開き、ヘッダの検索アイコンをクリックして、クエリを試してみます。

あるいは、以下のように手順を個別に実行します。

```bash
npm run build:site    # Hugo build
npm run pagefind      # Search index (required for search to work)
npm run serve         # Serve at http://localhost:3000
```

**システムにインストールされている Hugo を使用する際に** `/var/lib/snapd/void` **で** `permission denied` を得る場合、これは Snap サンドボックスです。`sudo snap install hugo --classic` を実行するか、上記のコマンドを使用します。それらは `npx hugo-extended` を使用するため、システム Hugo は必要ありません。

## 貢献

OWASP プロジェクトはオープンソースの取り組みであり、私たちはあらゆる形態の貢献とフィードバックを熱烈に歓迎します。

貢献インストラクションについては https://owaspai.org/contribute/ をご覧ください。

このリポジトリが依然として AI セキュリティおよびプライバシーガイドと呼ばれている場合、それは歴史的な理由によるものです。
