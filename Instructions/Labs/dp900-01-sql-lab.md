---
lab:
  title: Azure SQL Database について調べる
  module: Explore relational data in Azure
---

# <a name="explore-azure-sql-database"></a>Azure SQL Database について調べる

この演習では、自分の Azure サブスクリプションで Azure SQL Database リソースをプロビジョニングし、SQL を使用してリレーショナル データベース内のテーブルに対してクエリを実行します。

このラボは完了するまで、約 **15** 分かかります。

## <a name="before-you-start"></a>開始する前に

管理レベルのアクセス権を持つ [Azure サブスクリプション](https://azure.microsoft.com/free)が必要です。

## <a name="provision-an-azure-sql-database-resource"></a>Azure SQL Database リソースをプロビジョニングする

1. [Azure portal](https://portal.azure.com?azure-portal=true) で、左上隅にある **[&#65291; リソースの作成]** を選択し、 *[Azure SQL]* を検索します。 次に、表示される **[Azure SQL]** ページで、**[作成]** を選択します。

1. 使用可能な Azure SQL のオプションを確認し、**[SQL データベース]** タイルで **[単一データベース]** が選択されていることを確認して、**[作成]** を選択します。

    ![[Azure SQL] ページが表示された Azure portal のスクリーンショット。](images//azure-sql-portal.png)

1. **[SQL データベースの作成]** ページに次の値を入力し、他のすべてのプロパティは既定の設定のままにします。
    - **サブスクリプション**:Azure サブスクリプションを選択します。
    - **リソース グループ**: ご自分で選択した名前を持つ新しいリソース グループを作成します。
    - **データベース名**: *AdventureWorks*
    -                 **サーバー**: **[新規作成]** を選択し、使用可能な任意の場所に一意の名前を持つ新しいサーバーを作成します。 **SQL 認証**を使用し、サーバー管理者ログインとしてご自分の名前を指定して、適切な複雑なパスワードを指定します (パスワードを覚えておいてください。後で必要になります)。
    - **SQL エラスティック プールを使用しますか?**: *いいえ*
    - **ワークロード環境**: 開発
    - **コンピューティングとストレージ**: 変更しません
    - **バックアップ ストレージの冗長性**: "ローカル冗長バックアップ ストレージ"**

1. **[SQL Database の作成]** ページで、 **[次へ: ネットワーク]** を選択し、 **[ネットワーク]** ページの **[ネットワーク接続]** セクションで、 **[パブリック エンドポイント]** を選択します。 **[ファイアウォール規則]** セクションの両方のオプションに対して **[はい]** を選択すると、Azure サービスと現在のクライアント IP アドレスからデータベース サーバーへのアクセスが許可されます。

1. **[次へ: セキュリティ]** を選択し、 **[Microsoft Defender for SQL を有効にする]** オプションを **[今はしない]** に設定します。

1. **[次へ: 追加設定]** を選択し、 **[追加設定]** タブで、 **[既存のデータを使用します]** オプションを **[サンプル]** に設定します (これにより、後で利用できるサンプル データベースが作成されます)。

1. **[確認と作成]** を選択し、**[作成]** を選択して、Azure SQL データベースを作成します。

1. デプロイが完了するまで待ちます。 その後、デプロイされたリソースにアクセスすると、次のように表示されます。

    ![[SQL Database] ページが表示されている Azure portal のスクリーンショット。](images//sql-database-portal.png)

1. ページの左側のペインで、**[クエリ エディター (プレビュー)]** を選択し、サーバー用に指定した管理者のログインとパスワードを使用してサインインします。
    
                  "クライアント IP アドレスが許可されていないことを示すエラー メッセージが表示された場合は、メッセージの最後にある **[Allowlist IP ...] (許可リスト IP...)** リンクを選択してアクセスを許可し、もう一度サインインします (以前にご自身のコンピューターのクライアント IP アドレスをファイアウォール規則に追加していますが、ネットワーク構成によっては、クエリ エディターが異なるアドレスから接続されることがあります)。"**
    
    クエリ エディターは次のようになります。
    
    ![クエリ エディターが表示されている Azure portal のスクリーンショット。](images//query-editor.png)

1. **Tables** フォルダーを展開し、データベース内のテーブルを表示します。

1. **[クエリ 1]** ペインで、次の SQL コードを入力します。

    ```sql
    SELECT * FROM SalesLT.Product;
    ```

1. 次に示すように、クエリの上にある **[&#9655; 実行]** を選択して実行し、結果を表示します。これには、次に示すように、**SalesLT.Product** テーブルにあるすべての行のすべての列が含まれています。

    ![クエリ エディターにクエリの結果が表示されている Azure portal のスクリーンショット。](images//sql-query-results.png)

1. SELECT ステートメントを次のコードに置き換え、 **[&#9655; 実行]** を選択して新しいクエリを実行し、結果を確認します (**ProductID**、**Name**、**ListPrice**、**ProductCategoryID** の各列のみが含まれます)。

    ```sql
    SELECT ProductID, Name, ListPrice, ProductCategoryID
    FROM SalesLT.Product;
    ```

1. 次に、JOIN を使用して **SalesLT.ProductCategory** テーブルからカテゴリ名を取得する次のクエリを試してみましょう。

    ```sql
    SELECT p.ProductID, p.Name AS ProductName,
            c.Name AS Category, p.ListPrice
    FROM SalesLT.Product AS p
    JOIN [SalesLT].[ProductCategory] AS c
        ON p.ProductCategoryID = c.ProductCategoryID;
    ```

1. クエリ エディター ペインを閉じると、編集内容が破棄されます。

> **ヒント**: Azure SQL Database の調査が完了した場合は、この演習で作成したリソース グループを削除してください。
