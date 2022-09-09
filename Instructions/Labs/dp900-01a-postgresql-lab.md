---
lab:
  title: Azure Database for PostgreSQL について調べる
  module: Explore relational data in Azure
---

# <a name="explore-azure-database-for-postgresql"></a>Azure Database for PostgreSQL について調べる

この演習では、Azure サブスクリプションで Azure Database for PostgreSQL リソースをプロビジョニングします。

このラボは完了するまで、約 **5** 分かかります。

## <a name="before-you-start"></a>開始する前に

管理レベルのアクセス権を持つ [Azure サブスクリプション](https://azure.microsoft.com/free)が必要です。

## <a name="provision-an-azure-database-for-postgresql-resource"></a>Azure Database for PostgreSQL リソースのプロビジョニング

この演習では、Azure Database for PostgreSQL リソースをプロビジョニングします。

1. In the Azure portal, select <bpt id="p1">**</bpt>&amp;#65291; Create a resource<ept id="p1">**</ept> from the upper left-hand corner and search for <bpt id="p2">*</bpt>Azure Database for PostgreSQL<ept id="p2">*</ept>. Then in the resulting <bpt id="p1">**</bpt>Azure Database for PostgreSQL<ept id="p1">**</ept> page, select <bpt id="p2">**</bpt>Create<ept id="p2">**</ept>.

1. 使用可能な Azure Database for PostgreSQL のオプションを確認し、 **[フレキシブル サーバー]** タイルで **[作成]** を選択します。

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

1. Wait for deployment to complete. Then go to the resource that was deployed, which should look like this:

    ![[Azure Database for PostgreSQL] ページが表示されている Azure portal のスクリーンショット。](images/postgresql-portal.png)

1. Azure Database for PostgreSQL リソースを管理するためのオプションを確認します。

> **ヒント**: Azure Database for PostgreSQL の調査が完了している場合は、この演習で作成したリソース グループを削除してください。