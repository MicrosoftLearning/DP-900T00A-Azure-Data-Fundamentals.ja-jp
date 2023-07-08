---
lab:
  title: Azure Database for PostgreSQL について調べる
  module: Explore relational data in Azure
---

# Azure Database for PostgreSQL について調べる

この演習では、Azure サブスクリプションで Azure Database for PostgreSQL リソースをプロビジョニングします。

このラボは完了するまで、約 **5** 分かかります。

## 開始する前に

管理レベルのアクセス権を持つ [Azure サブスクリプション](https://azure.microsoft.com/free)が必要です。

## Azure Database for PostgreSQL リソースのプロビジョニング

この演習では、Azure Database for PostgreSQL リソースをプロビジョニングします。

1. Azure portal で、左上隅にある **[&#65291; リソースの作成]** を選択し、 *[Azure Database for PostgreSQL]* を検索します。 次に、表示される **[Azure Database for PostgreSQL]** ページで、**[作成]** を選択します。

1. 使用可能な Azure Database for PostgreSQLオプションを確認し、 **[Azure Database for PostgreSQL]** タイルで **[フレキシブル サーバー (推奨)** ]、 **[作成]** の順に選択します。

    ![Azure Database for PostgreSQL デプロイ オプションのスクリーンショット](images/postgresql-options.png)

1. **[SQL データベースの作成]** ページで、次の値を入力します。
    - **サブスクリプション**:Azure サブスクリプションを選択します。
    - **リソース グループ**: ご自分で選択した名前を持つ新しいリソース グループを作成します。
    - **サーバー名**:一意の名前を入力します。
    - **リージョン**: 最寄りのリージョンを選択します。
    - **PostgreSQL バージョン**: 変更しません。
    - **ワークロードの種類**: **[開発]** を選択します。
    - **コンピューティングとストレージ**: 変更しません。
    - **可用性ゾーン**: 変更しません。
    - **高可用性の有効化**: 変更しません。
    - **管理者ユーザー名**: ご自分の名前。
    - **[パスワード]** と **[パスワードの確認入力]** : 適切に複雑なパスワード。

1. **[次へ: ネットワーク]** を選択します。

1. **[ファイアウォール規則]** で、 **[&#65291; 現在のクライアント IP アドレスを追加する]** を選択します。

1. **[確認と作成]** を選択し、**[作成]** を選択して、Azure PostgreSQL データベースを作成します。

1. デプロイが完了するまで待ちます。 その後、デプロイされたリソースにアクセスすると、次のように表示されます。

    ![[Azure Database for PostgreSQL] ページが表示されている Azure portal のスクリーンショット。](images/postgresql-portal.png)

1. Azure Database for PostgreSQL リソースを管理するためのオプションを確認します。

> **ヒント**: Azure Database for PostgreSQL の調査が完了している場合は、この演習で作成したリソース グループを削除してください。
