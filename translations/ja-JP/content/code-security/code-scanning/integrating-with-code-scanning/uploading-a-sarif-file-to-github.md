---
title: SARIF ファイルを GitHub にアップロードする
shortTitle: SARIFファイルのアップロード
intro: '{% data reusables.code-scanning.you-can-upload-third-party-analysis %}'
permissions: 'People with write permissions to a repository can upload {% data variables.product.prodname_code_scanning %} data generated outside {% data variables.product.prodname_dotcom %}.'
product: '{% data reusables.gated-features.code-scanning %}'
redirect_from:
  - /github/managing-security-vulnerabilities/uploading-a-code-scanning-analysis-to-github
  - /github/finding-security-vulnerabilities-and-errors-in-your-code/uploading-a-sarif-file-to-github
  - /code-security/secure-coding/uploading-a-sarif-file-to-github
  - /code-security/secure-coding/integrating-with-code-scanning/uploading-a-sarif-file-to-github
versions:
  fpt: '*'
  ghes: '>=3.0'
  ghae: '*'
type: how_to
topics:
  - Advanced Security
  - Code scanning
  - Integration
  - Actions
  - Repositories
  - CI
  - SARIF
---

<!--For this article in earlier GHES versions, see /content/github/finding-security-vulnerabilities-and-errors-in-your-code-->

{% data reusables.code-scanning.beta %}
{% data reusables.code-scanning.enterprise-enable-code-scanning %}
{% data reusables.code-scanning.deprecation-codeql-runner %}

## {% data variables.product.prodname_code_scanning %} に対する SARIF ファイルのアップロードについて

SARIF ファイルに `partialFingerprints` が含まれていない場合、`upload-sarif` アクションは、`partialFingerprints` フィールドを計算し、アラートの重複を防止しようと試みます。 {% data variables.product.prodname_dotcom %} は、リポジトリに SARIF ファイルと静的分析で使用されるソースコードの両方が含まれている場合にのみ、`partialFingerprints` を作成できます。 詳しい情報については、「[リポジトリの {% data variables.product.prodname_code_scanning %} アラートを管理する](/code-security/secure-coding/managing-code-scanning-alerts-for-your-repository)」を参照してください。

SARIF ファイルは、{% data variables.product.prodname_codeql %} を含む多くの静的解析セキュリティテストツールを使用して生成できます。 生成するファイルは、SARIF バージョン 2.1.0 である必要があります。 詳しい情報については「[{% data variables.product.prodname_code_scanning %}の SARIF サポート](/code-security/secure-coding/sarif-support-for-code-scanning)」を参照してください。

結果のアップロードは、{% data variables.product.prodname_actions %}、{% data variables.product.prodname_code_scanning %} API、{% ifversion fpt or ghes > 3.0 or ghae-next %}{% data variables.product.prodname_codeql_cli %}、{% endif %}{% data variables.product.prodname_codeql_runner %}を使って行えます。 最適なアップロード方法は、SARIF ファイルの生成方法によって異なります。以下、例を示します。

- {% data variables.product.prodname_actions %} を使用して {% data variables.product.prodname_codeql %} アクションを実行している場合、追加のアクションは不要です。 SARIF ファイルは、ファイルのアップロードに使用したものと同じ {% data variables.product.prodname_actions %} ワークフローで実行する SARIF 互換の分析ツールから生成できます。
- "[ワークフロー実行の管理](/actions/configuring-and-managing-workflows/managing-a-workflow-run#viewing-your-workflow-history)" {% ifversion fpt or ghes > 3.0 or ghae-next %}
 - CIシステムで{% data variables.product.prodname_code_scanning %}を実行する{% data variables.product.prodname_codeql_cli %}を使って結果を{% data variables.product.prodname_dotcom %}にアップロードできます（詳しい情報については「[CIシステムへの{% data variables.product.prodname_codeql_cli %}のインストール](/code-security/secure-coding/using-codeql-code-scanning-with-your-existing-ci-system/installing-codeql-cli-in-your-ci-system)」を参照してください）。{% endif %}
- {% data variables.product.prodname_dotcom %} は、リポジトリにアップロードされた SARIF ファイルからの {% data variables.product.prodname_code_scanning %} アラートを表示します。 自動的なアップロードをブロックしている場合、結果をアップロードする準備ができたら `upload` コマンドを使用できます (詳しい情報については、「[CI システムでの{% data variables.product.prodname_codeql_runner %}の実行](/code-security/secure-coding/running-codeql-runner-in-your-ci-system) 」を参照)。
- 結果をリポジトリ外に成果物として生成するツールの場合、{% data variables.product.prodname_code_scanning %} API を使用してファイルをアップロードできます (詳しい情報については、「[解析を SARIF データとしてアップロードする](/rest/reference/code-scanning#upload-an-analysis-as-sarif-data)」を参照)。

{% data reusables.code-scanning.not-available %}

## {% data variables.product.prodname_actions %} での {% data variables.product.prodname_code_scanning %} 分析をアップロードする

サードパーティの SARIF ファイルを {% data variables.product.prodname_dotcom %} にアップロードするには、{% data variables.product.prodname_actions %} ワークフローが必要です。 詳しい情報については、「[{% data variables.product.prodname_actions %} を学ぶ](/actions/learn-github-actions)」を参照してください。

ワークフローは、`upload-sarif` アクションを使用する必要があります。 これには、アップロードの設定に使用できる入力パラメータがあります。 使用する主な入力パラメータは、アップロードする SARIF ファイルのファイルまたはディレクトリを設定する `sarif-file` です。 ディレクトリまたはファイルのパスは、リポジトリのルートからの相対パスです。 詳しい情報については、「[`upload-sarif` アクション](https://github.com/github/codeql-action/tree/HEAD/upload-sarif)」を参照してください。

`upload-sarif` アクションは、`push` および `scheduled` イベントが発生したときに実行するように設定できます。 {% data variables.product.prodname_actions %} イベントについて詳しい情報は、「[ワークフローをトリガーするイベント](/actions/reference/events-that-trigger-workflows)」を参照してください。

SARIF ファイルに `partialFingerprints` が含まれていない場合、`upload-sarif` アクションは、`partialFingerprints` フィールドを計算し、アラートの重複を防止しようと試みます。 {% data variables.product.prodname_dotcom %} は、リポジトリに SARIF ファイルと静的分析で使用されるソースコードの両方が含まれている場合にのみ、`partialFingerprints` を作成できます。 重複アラートの防止に関する詳しい情報については、「[コードスキャンに対する SARIF サポートについて](/code-security/secure-coding/sarif-support-for-code-scanning#preventing-duplicate-alerts-using-fingerprints)」を参照してください。

{% data reusables.code-scanning.upload-sarif-alert-limit %}

### リポジトリ外で生成された SARIF ファイルのワークフロー例

SARIF ファイルをリポジトリにコミットした後でアップロードする新しいワークフローを作成できます。 これは、SARIF ファイルがリポジトリ外のアーティファクトとして生成される場合に役立ちます。

この例のワークフローは、コミットがリポジトリにプッシュされるたびに実行されます。 アクションは `partialFingerprints` プロパティを使用して、変更が発生したかどうかを判断します。 コミットがプッシュされたときに実行されるだけでなく、ワークフローは週に 1 回実行されるようにスケジュールされます。 詳しい情報については、「[ワークフローをトリガーするイベント](/actions/reference/events-that-trigger-workflows)」を参照してください。

このワークフローは、リポジトリのルートにある `results.sarif` ファイルをアップロードします。 ワークフローファイルの作成に関する詳しい情報については、「[{% data variables.product.prodname_actions %} を学ぶ](/actions/learn-github-actions)」を参照してください。

または、このワークフローを変更して、SARIF ファイルのディレクトリをアップロードすることもできます。 たとえば、すべての SARIF ファイルをリポジトリのルートにある `sarif-output` というディレクトリに配置し、アクションの入力パラメータ `sarif_file` を `sarif-output` に設定できます。

```yaml
name: "Upload SARIF"

# コードがリポジトリにプッシュされるたびに、スケジュールに従ってワークフローを実行します。
# スケジュールされたワークフローは、毎週木曜日の 15:45（UTC）に実行されます。
on:
  push:
  schedule:
    - cron: '45 15 * * 4'

jobs:
  build:
    runs-on: ubuntu-latest{% ifversion fpt or ghes > 3.1 or ghae-next %}
    permissions:
      security-events: write{% endif %}
    steps:
      # このステップはリポジトリのコピーをチェックアウトします。
      - name: Checkout repository
        uses: actions/checkout@v2
      - name: Upload SARIF file
        uses: github/codeql-action/upload-sarif@v1
        with:
          # Path to SARIF file relative to the root of the repository
          sarif_file: results.sarif
```

### ESLint 分析ツールを実行するワークフローの例

継続的インテグレーション（CI）ワークフローの一部としてサードパーティの SARIF ファイルを生成する場合は、CI テストの実行後のステップとして、`upload-sarif` アクションを追加できます。 CI ワークフローがない場合は、{% data variables.product.prodname_actions %} テンプレートを使用して作成できます。 詳しい情報については、「[{% data variables.product.prodname_actions %} のクイックスタート](/actions/quickstart)」を参照してください。

この例のワークフローは、コミットがリポジトリにプッシュされるたびに実行されます。 アクションは `partialFingerprints` プロパティを使用して、変更が発生したかどうかを判断します。 コミットがプッシュされたときに実行されるだけでなく、ワークフローは週に 1 回実行されるようにスケジュールされます。 詳しい情報については、「[ワークフローをトリガーするイベント](/actions/reference/events-that-trigger-workflows)」を参照してください。

ワークフローでは、ESLint 静的分析ツールをワークフローのステップとして実行する例を示しています。 `Run ESLint` ステップは ESLint ツールを実行して、`results.sarif` ファイルを出力します。 次に、ワークフローは `upload-sarif` アクションを使用して、`results.sarif` ファイルを {% data variables.product.prodname_dotcom %} にアップロードします。 ワークフローファイルの作成に関する詳しい情報については、「[GitHub Actions 入門](/actions/learn-github-actions/introduction-to-github-actions)」を参照してください。

```yaml
name: "ESLint analysis"

# コードがリポジトリにプッシュされるたびに、スケジュールに従ってワークフローを実行します。
# スケジュールされたワークフローは、毎週水曜日の 15:45（UTC）に実行されます。
on:
  push:
  schedule:
    - cron: '45 15 * * 3'

jobs:
  build:
    runs-on: ubuntu-latest{% ifversion fpt or ghes > 3.1 or ghae-next %}
    permissions:
      security-events: write{% endif %}
    steps:
      - uses: actions/checkout@v2
      - name: Run npm install
        run: npm install
      # ESlintコード分析の実行
      - name: Run ESLint
        # 報告するものを見つけると、eslintは1で終了する
        run: node_modules/.bin/eslint build docs lib script spec-main -f node_modules/@microsoft/eslint-formatter-sarif/sarif.js -o results.sarif || true
      # upload-sarifアクションを使ってresults.sarifをGitHubリポジトリにアップロード
      - uses: github/codeql-action/upload-sarif@v1
        with:
          # リポジトリのルートに対する相対のSARIFファイルへのパス
          sarif_file: results.sarif
```

## 参考リンク

- [{% data variables.product.prodname_actions %}のワークフロー構文](/actions/reference/workflow-syntax-for-github-actions)
- 「[ワークフローの履歴の表示](/actions/managing-workflow-runs/viewing-workflow-run-history)」{%- ifversion fpt or ghes > 3.0 or ghae-next %}
- 「[CIシステムでの{% data variables.product.prodname_codeql %} {% data variables.product.prodname_code_scanning %}について](/code-security/secure-coding/about-codeql-code-scanning-in-your-ci-system)」{% else %}
- 「[CIシステムでの{% data variables.product.prodname_codeql_runner %}の実行](/code-security/secure-coding/running-codeql-runner-in-your-ci-system)」{% endif %}
- 「[解析を SARIF データとしてアップロードする](/rest/reference/code-scanning#upload-an-analysis-as-sarif-data)」
