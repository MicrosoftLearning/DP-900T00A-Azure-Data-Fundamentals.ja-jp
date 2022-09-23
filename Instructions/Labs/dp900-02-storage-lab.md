---
lab:
  title: Azure Storage を調べる
  module: Explore Azure Storage for non-relational data
---

# <a name="explore-azure-storage"></a>Azure Storage を調べる

この演習では、自分の Azure サブスクリプションで Azure Storage アカウントをプロビジョニングし、それを使用してデータを格納するさまざまな方法を検討します。

このラボは完了するまで、約 **15** 分かかります。

## <a name="before-you-start"></a>開始する前に

管理レベルのアクセス権を持つ [Azure サブスクリプション](https://azure.microsoft.com/free)が必要です。

## <a name="provision-an-azure-storage-account"></a>Azure Storage アカウントをプロビジョニングする

Azure Storage を使用する際の最初の手順は、Azure サブスクリプションに Azure Storage アカウントをプロビジョニングすることです。

1. まだサインインしていない場合は、[Azure portal](https://portal.azure.com?azure-portal=true) にサインインします。
1. On the Azure portal home page, select <bpt id="p1">**</bpt>&amp;#65291; Create a resource<ept id="p1">**</ept> from the upper left-hand corner and search for <bpt id="p2">*</bpt>Storage account<ept id="p2">*</ept>. Then in the resulting <bpt id="p1">**</bpt>Storage account<ept id="p1">**</ept> page, select <bpt id="p2">**</bpt>Create<ept id="p2">**</ept>.
1. **[ストレージ アカウントの作成]** ページで、次の値を入力します。
    - <bpt id="p1">**</bpt>Subscription<ept id="p1">**</ept>: If you're using a sandbox, select <bpt id="p2">*</bpt>Concierge Subscription<ept id="p2">*</ept>. Otherwise, select your Azure subscription.
    - **リソース グループ**: サンドボックスを使用している場合は、既存のリソース グループを選びます (この名前は、*learn-xxxx...* のようになります)。それ以外の場合は、任意の名前で新しいリソース グループを作成します。
    - **ストレージ アカウント名**: 小文字と数字を使用して、ストレージ アカウントの一意の名前を入力します。
    - **リージョン**: 使用可能な場所を選択します。
    - **パフォーマンス**: "標準"**
    - **冗長性**: *"ローカル冗長ストレージ (LRS)"*

1. Select <bpt id="p1">**</bpt>Next: Advanced &gt;<ept id="p1">**</ept> and view the advanced configuration options. In particular, note that this is where you can enable hierarchical namespace to support Azure Data Lake Storage Gen2. Leave this option <bpt id="p1">**</bpt><bpt id="p2">&lt;u&gt;</bpt>unselected<ept id="p2">&lt;/u&gt;</ept><ept id="p1">**</ept> (you'll enable it later), and then select <bpt id="p3">**</bpt>Next: Networking &gt;<ept id="p3">**</ept> to view the networking options for your storage account.
1. Select <bpt id="p1">**</bpt>Next: Data protection &gt;<ept id="p1">**</ept> and then in the <bpt id="p2">**</bpt>Recovery<ept id="p2">**</ept> section, <bpt id="p3">&lt;u&gt;</bpt>de<ept id="p3">&lt;/u&gt;</ept>select all of the <bpt id="p4">**</bpt>Enable soft delete...<ept id="p4">**</ept> options. These options retain deleted files for subsequent recovery, but can cause issues later when you enable hierarchical namespace.
1. 既定の設定を変更せずに残りの **[次へ]** ページに進んでから、 **[確認と作成]** ページで選択内容が検証されるのを待ち、 **[作成]** を選択して Azure Storage アカウントを作成します。
1. Wait for deployment to complete. Then go to the resource that was deployed.

## <a name="explore-blob-storage"></a>BLOB ストレージを探索する

新しい Azure Storage アカウントを作成したので、BLOB データ用のコンテナーを作成できます。

1. `https://aka.ms/product1.json` から [product1.json](https://aka.ms/product1.json?azure-portal=true) JSON ファイルをダウンロードし、コンピューターに保存します (任意のフォルダーに保存できます。後で BLOB ストレージにアップロードします)。

    *JSON ファイルがブラウザーに表示される場合は、ページを **product1.json** として保存します。*

1. ストレージ コンテナーの Azure portal ページの左側にある **[データ ストレージ]** セクションで、**[コンテナー]** を選択します。
1. **[コンテナー]** ページで **[&#65291; コンテナー]** を選択し、パブリック アクセス レベルが **[非公開 (匿名アクセスなし)]** の **data** という名前の新しいコンテナーを追加します。
1. **data** コンテナーが作成された後、それが **[コンテナー]** ページに一覧表示されているのを確認します。
1. In the pane on the left side, in the top section, select **Storage browser **. This page provides a browser-based interface that you can use to work with the data in your storage account.
1. [ストレージ ブラウザー] ページで **[BLOB コンテナー]** を選択し、**data** コンテナーが一覧表示されていることを確認します。
1. **data** コンテナーを選択します。空である点に注意してください。
1. **[&#65291; ディレクトリの追加]** を選択し、**products** という名前の新しいディレクトリを作成する前にフォルダーに関する情報を読みます。
1. ストレージ エクスプローラーで、作成した **products** フォルダーの内容が現在のビューに表示されていることを確認します。ページの上部にある "階層リンク" に **BLOB コンテナー > data > products** のパスが反映されているのを確認します。
1. 階層リンクで、**data** を選択して **data** コンテナーに切り替えます。**products** という名前のフォルダーは含まれ<u>ない</u>ので注意してください。

    Folders in blob storage are virtual, and only exist as part of the path of a blob. Since the <bpt id="p1">**</bpt>products<ept id="p1">**</ept> folder contained no blobs, it isn't really there!

1. **[&#10514; アップロード]** ボタンを使用して、 **[BLOB のアップロード]** パネルを開きます。
1. In the <bpt id="p1">**</bpt>Upload blob<ept id="p1">**</ept> panel, select the <bpt id="p2">**</bpt>product1.json<ept id="p2">**</ept> file you saved on your local computer previously. Then in the <bpt id="p1">**</bpt>Advanced<ept id="p1">**</ept> section, in the <bpt id="p2">**</bpt>Upload to folder<ept id="p2">**</ept> box, enter <bpt id="p3">**</bpt>product_data<ept id="p3">**</ept> and select the <bpt id="p4">**</bpt>Upload<ept id="p4">**</ept> button.
1. **[BLOB アップロード]** パネルが開いている場合は閉じ、データ コンテナーに **product_data 仮想フォルダー** が作成されたことを確認します。
1. **product_data** フォルダーを選択し、アップロードした **product1.json** BLOB が含まれているか確認します。
1. 左側の **[データ ストレージ]** セクションで、**[コンテナー]** を選択します。
1. **data** コンテナーを開き、作成した **product_data** が一覧表示されていることを確認します。
1. Select the <bpt id="p1">**</bpt>&amp;#x2027;&amp;#x2027;&amp;#x2027;<ept id="p1">**</ept> icon at the right-end of the folder, and note that it doesn't display any options. Folders in a flat namespace blob container are virtual, and can't be managed.
1. **data** ページの右上にある **X** アイコンを使用してページを閉じ、**[コンテナー]** ページに戻ります。

## <a name="explore-azure-data-lake-storage-gen2"></a>Azure Data Lake Storage Gen2 を確認する

Azure Data Lake Store Gen2 support enables you to use hierarchical folders to organize and manage access to blobs. It also enables you to use Azure blob storage to host distributed file systems for common big data analytics platforms.

1. `https://aka.ms/product2.json` から [product2.json](https://aka.ms/product2.json?azure-portal=true) JSON ファイルをダウンロードし、コンピューターの以前 ** product1.json** をダウンロードしたのと同じフォルダーに保存します。後で BLOB ストレージにアップロードします。
1. ストレージ アカウントの Azure portal ページの左側にある **[設定]** セクションまで下にスクロールし、 **[Data Lake Gen2 のアップグレード]** を選択します。
1. Azure portal ホーム ページで、左上隅にある **[&#65291; リソースの作成]** を選択し、"ストレージ アカウント" を検索します。**
1. アップグレードが完了したら、左側のペインの上部セクションで **[ストレージ ブラウザー]** を選択し、**data** BLOB コンテナーのルートに戻ります。これには引き続き **product_data** フォルダーが含まれます。
1. **product_data** フォルダーを選択し、前にアップロードした **product1.json** ファイルがまだ含まれているか確認します。
1. **[&#10514; アップロード]** ボタンを使用して、 **[BLOB のアップロード]** パネルを開きます。
1. 次に、結果として得られる **[ストレージ アカウント]** ページで、**[作成]** を選択します。
1. **[BLOB のアップロード]** パネルが開いている場合は閉じ、**product_data** フォルダーに **product2.json** ファイルが含まれているのを確認します。
1. 左側の **[データ ストレージ]** セクションで、**[コンテナー]** を選択します。
1. **data** コンテナーを開き、作成した **product_data** が一覧表示されていることを確認します。
1. フォルダーの右側にある **[&#x2027;&#x2027;&#x2027;]** アイコンを選択し、階層型名前空間を有効にすると、フォルダー レベルで構成タスクを実行できることにご注意ください。これにはフォルダー名の変更やアクセス許可の設定を含みます。
1. **data** ページの右上にある **X** アイコンを使用してページを閉じ、**[コンテナー]** ページに戻ります。

## <a name="explore-azure-files"></a>Azure Files について調べる

Azure Files は、クラウドベースのファイル共有を作成する方法を提供します。

1. ストレージ コンテナーの Azure portal ページの左側にある **[データ ストレージ]** セクションで、**[ファイル共有]** を選択します。
1. [ファイル共有] ページで **[&#65291; ファイル共有]** を選択し、**トランザクション最適化**レベルを使用して **files** という名前の新しいファイル共有を追加します。
1. **[ファイル共有]** で、新しい **files** ファイル共有を開きます。
1. At the top of the page, select <bpt id="p1">**</bpt>Connect<ept id="p1">**</ept>. Then in the <bpt id="p1">**</bpt>Connect<ept id="p1">**</ept> pane, note that there are tabs for common operating systems (Windows, Linux, and macOS) that contain scripts you can run to connect to the shared folder from a client computer.
1. **[接続]** ペインを閉じ、次に **files** ファイル ページを閉じて、Azure ストレージ アカウントの **[ファイル共有]** ページに戻ります。

## <a name="explore-azure-tables"></a>Azure Tables を確認する

Azure テーブルは、データ値の格納を必要としても、リレーショナル データベースの完全な機能と構造を必要としないアプリケーションに、キーと値ストアを提供します。

1. ストレージ コンテナーの Azure portal ページの左側にある **[データ ストレージ]** セクションで、**[テーブル]** を選択します。
1. **[テーブル]** ページで、 **[&#65291; テーブル]** を選択し、**products** という名前の新しいテーブルを作成します。
1. **products** テーブルが作成されたら、左側のペインの上部にある **[ストレージ ブラウザー]** を選択します。
1. ストレージ エクスプローラーで、**[テーブル]** を選択し、**products** テーブルが表示されていることを確認します。
1. **products** テーブルを選択します。
1. **product** ページで、 **[&#65291; エンティティの追加]** を選択します。
1. **[エンティティの追加]** パネルで、次のキー値を入力します。
    - **PartitionKey**: 1
    - **RowKey**: 1
1. **[プロパティの追加]** を選択し、次の値を使用して新しいプロパティを作成します。

    |プロパティ名 | Type | 値 |
    | ------------ | ---- | ----- |
    | Name | String | ウィジェット |

1. 次の値を持つ 2 番目のプロパティを追加します。

    |プロパティ名 | Type | 値 |
    | ------------ | ---- | ----- |
    | Price | Double | 2.99 |

1. **[挿入]** を選択して、新しいエンティティの行をテーブルに挿入します。
1. ストレージ ブラウザーで、**products** テーブルに行が追加されていること、および行が最後に変更された日時を示す **Timestamp** 列が作成されていることを確認します。
1. 次のプロパティを使用して、**products** テーブルに別のエンティティを追加します。

    |プロパティ名 | Type | 値 |
    | ------------ | ---- | ----- |
    | PartitionKey | String | 1 |
    | RowKey | 文字列 | 2 |
    | Name | String | Kniknak |
    | Price | Double | 1.99 |
    | Discontinued | Boolean | true |

1. 新しいエンティティを挿入した後、生産が中止された製品を含む行がテーブルに表示されていることを確認します。

    You have manually entered data into the table using the storage browser interface. In a real scenario, application developers can use the Azure Storage Table API to build applications that read and write values to tables, making it a cost effective and scalable solution for NoSQL storage.

> **ヒント**: Azure Storage の調査が完了した場合は、この演習で作成したリソース グループを削除してください。
