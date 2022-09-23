---
lab:
  title: Azure Cosmos DB を調べる
  module: Explore fundamentals of Azure Cosmos DB
---
# <a name="explore-azure-cosmos-db"></a>Azure Cosmos DB を調べる

この演習では、自分の Azure サブスクリプションで Azure Cosmos DB データベースをプロビジョニングし、それを使用して非リレーショナル データを格納するさまざまな方法を検討します。

このラボは完了するまで、約 **15** 分かかります。

## <a name="before-you-start"></a>開始する前に

管理レベルのアクセス権を持つ [Azure サブスクリプション](https://azure.microsoft.com/free)が必要です。

## <a name="create-a-cosmos-db-account"></a>Cosmos DB アカウントを作成する

To use Cosmos DB, you must provision a Cosmos DB account in your Azure subscription. In this exercise, you'll provision a Cosmos DB account that uses the core (SQL) API.

1. In the Azure portal, select <bpt id="p1">**</bpt>+ Create a resource<ept id="p1">**</ept> at the top left, and search for <bpt id="p2">*</bpt>Azure Cosmos DB<ept id="p2">*</ept>.  In the results, select <bpt id="p1">**</bpt>Azure Cosmos DB<ept id="p1">**</ept> and select  <bpt id="p2">**</bpt>Create<ept id="p2">**</ept>.
1. **[コア (SQL) - 推奨]** タイル内の **[作成]** を選択します。
1. 次の詳細を入力して、**[確認および作成]** を選択します。
    - <bpt id="p1">**</bpt>Subscription<ept id="p1">**</ept>: If you're using a sandbox, select <bpt id="p2">*</bpt>Concierge Subscription<ept id="p2">*</ept>. Otherwise, select your Azure subscription.
    - **リソース グループ**: サンドボックスを使用している場合は、既存のリソース グループを選択します (この名前は、*learn-xxxx...* のようになります)。それ以外の場合は、任意の名前で新しいリソース グループを作成します。
    - **アカウント名**: 一意の名前を入力します。
    - **場所**: 任意の推奨される場所を選びます
    - **容量モード**: プロビジョニングされたスループット
    - **Apply Free-Tier Discount (Free レベル割引を適用する)**: 使用できる場合は [適用] を選びます。
    - **合計アカウント スループットを制限する**: オフ
1. 構成を確認したら、**[作成]** を選びます。
1. Wait for deployment to complete. Then go to the deployed resource.

## <a name="create-a-sample-database"></a>サンプル データベースの作成

              "この手順全体を通して、ポータルに表示されるヒントをすべて閉じます"。**

1. 新しい Cosmos DB アカウントのページの左側のペインで **[Data Explorer]** を選びます。
1. **[Data Explorer]** ページで、**[クイック スタートの起動]** を選びます。
1. **[新しいコンテナー]** タブで、サンプル データベースの事前に設定された値を確認して、**[OK]** を選びます。
1. **SampleDB** データベースとその **SampleContainer** コンテナーが作成されるまで、画面の下部にあるパネルで状態を観察します (1 分ほどかかる場合があります)。

## <a name="view-and-create-items"></a>項目の表示と作成

1. In the Data Explorer page, expand the <bpt id="p1">**</bpt>SampleDB<ept id="p1">**</ept> database and the <bpt id="p2">**</bpt>SampleContainer<ept id="p2">**</ept> container, and select <bpt id="p3">**</bpt>Items<ept id="p3">**</ept> to see a list of items in the container. The items represent addresses, each with a unique id and other properties.
1. 一覧内の項目を選ぶと、項目データの JSON 表現が表示されます。
1. ページの上部にある **[新しい項目]** を選び、新しい空白の項目を作成します。
1. 新しい項目の JSON を以下のように変更し、**[保存]** を選びます。

    ```json
    {
        "address": "1 Any St.",
        "id": "123456789"
    }
    ```

1. 新しい項目を保存すると、追加のメタデータ プロパティが自動的に追加されることに注意してください。

## <a name="query-the-database"></a>データベースのクエリを実行する

1. **[Data Explorer]** ページで、**[新しい SQL クエリ]** アイコンを選びます。
1. SQL クエリ エディターで既定のクエリ (`SELECT * FROM c`) を確認し、`SELECT * FROM c` ボタンを使って実行します。
1. すべての項目の完全な JSON 表現を含む結果を確認します。
1. 次のように、クエリを変更します。

    ```sql
    SELECT c.id, c.address
    FROM c
    WHERE CONTAINS(c.address, "Any St.")
    ```

1. **[クエリの実行]** ボタンを使って、修正したクエリを実行し、結果を確認します。これには、**address** フィールドに "Any St." というテキストが含まれる項目の JSON エンティティが含まれます。
1. SQL クエリ エディターを閉じ、変更内容を破棄します。

    You've seen how to create and query JSON entities in a Cosmos DB database by using the data explorer interface in the Azure portal. In a real scenario, an application developer would use one of the many programming language specific software development kits (SDKs) to call the core (SQL) API and work with data in the database.

> **ヒント**: Azure Cosmos DB の調査が完了した場合は、この演習で作成したリソース グループを削除してください。
