---
lab:
  title: Azure Database for MySQL について調べる
  module: Explore relational data in Azure
---

# <a name="explore-azure-database-for-mysql"></a>Azure Database for MySQL について調べる

この演習では、Azure サブスクリプションで Azure Database for MySQL リソースをプロビジョニングします。

このラボは完了するまで、約 **5** 分かかります。

## <a name="before-you-start"></a>開始する前に

管理レベルのアクセス権を持つ [Azure サブスクリプション](https://azure.microsoft.com/free)が必要です。

## <a name="provision-an-azure-database-for-mysql-resource"></a>Azure Database for MySQL リソースのプロビジョニング

この演習では、Azure Database for MySQL リソースをプロビジョニングします。

1. In the Azure portal, select <bpt id="p1">**</bpt>&amp;#65291; Create a resource<ept id="p1">**</ept> from the upper left-hand corner and search for <bpt id="p2">*</bpt>Azure Database for MySQL<ept id="p2">*</ept>. Then in the resulting <bpt id="p1">**</bpt>Azure Database for MySQL<ept id="p1">**</ept> page, select <bpt id="p2">**</bpt>Create<ept id="p2">**</ept>.

1. Review the Azure Database for MySQL options that are available. Then for <bpt id="p1">**</bpt>Resource type<ept id="p1">**</ept>, select <bpt id="p2">**</bpt>Flexible Server<ept id="p2">**</ept> and select <bpt id="p3">**</bpt>Create<ept id="p3">**</ept>.

    ![Azure Database for MySQL デプロイ オプションのスクリーンショット](images/mysql-options.png)

1. **[SQL データベースの作成]** ページで、次の値を入力します。
    - **サブスクリプション**:Azure サブスクリプションを選択します。
    - **リソース グループ**: ご自分で選択した名前を持つ新しいリソース グループを作成します。
    - **サーバー名**:一意の名前を入力します。
    - **リージョン**: 利用可能な最寄りの場所。
    - **MySQL バージョン**: 変更しません。
    - **ワークロードの種類**: 開発プロジェクトまたは趣味プロジェクト向け。
    - **コンピューティングとストレージ**: 変更しません。
    - **可用性ゾーン**: 変更しません。
    - **高可用性の有効化**: 変更しません。
    - **管理者ユーザー名**: ご自分の名前
    - **[パスワード]** と **[パスワードの確認入力]**: 適切な複雑なパスワード

1. **[次へ: ネットワーク]** を選択します。

1. **[ファイアウォール規則]** で、 **[&#65291; 現在のクライアント IP アドレスを追加する]** を選択します。

1. **[確認と作成]** を選択し、**[作成]** を選択して、Azure MySQL データベースを作成します。

1. Wait for deployment to complete. Then go to the resource that was deployed, which should look like this:

    ![[Azure Database for MySQL] ページが表示されている Azure portal のスクリーンショット。](images/mysql-portal.png)

1. Azure Database for MySQL リソースを管理するためのオプションを確認します。

> **ヒント**: Azure Database for MySQL の調査が完了している場合は、この演習で作成したリソース グループを削除してください。
