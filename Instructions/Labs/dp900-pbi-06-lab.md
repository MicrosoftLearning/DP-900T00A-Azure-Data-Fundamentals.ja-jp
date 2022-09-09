---
lab:
  title: Power BI を使用したデータの可視化の基礎を調べる
  module: Explore fundamentals of data visualization
---

# <a name="explore-fundamentals-of-data-visualization-with-power-bi"></a>Power BI を使用したデータの可視化の基礎を調べる

この演習では、Microsoft Power BI Desktop を使用して、対話型データの視覚化を含むデータ モデルとレポートを作成します。

このラボは完了するまで、約 **20** 分かかります。

## <a name="before-you-start"></a>開始する前に

管理レベルのアクセス権を持つ [Azure サブスクリプション](https://azure.microsoft.com/free)が必要です。

### <a name="install-power-bi-desktop"></a>Power BI Desktop をインストールする

Microsoft Power BI Desktop が Windows コンピューターにまだインストールされていない場合は、無料でダウンロードしてインストールできます。

1. [https://aka.ms/power-bi-desktop](https://aka.ms/power-bi-desktop?azure-portal=true) から Power BI Desktop インストーラーをダウンロードします。
1. When the file has downloaded, open it, and use the setup wizard to install Power BI Desktop on your computer. This insatllation may take a few minutes.

## <a name="import-data"></a>データのインポート

1. Open Power BI Desktop. The application interface should look similar to this:

    ![Power BI Desktop のスタート画面を示すスクリーンショット。](images/power-bi-start.png)

    これで、レポートのデータをインポートする準備ができました。

1. Power BI Desktop のようこそ画面で、**[データの取得]** を選択し、データ ソースの一覧で **[Web]** を選択し、**[接続]** を選択します。

    ![Power BI で Web データ ソースを選択する方法を示すスクリーンショット。](images/web-source.png)

1. **[Web から]** ダイアログ ボックスで、次の URL を入力し、**[OK]** を選択します。

    ```
    https://github.com/MicrosoftLearning/DP-900T00A-Azure-Data-Fundamentals/raw/master/power-bi/customers.csv
    ```

1. [Web コンテンツへのアクセス] ダイアログで、 **[接続]** を選択します。

1. Verify that the URL opens a dataset containing customer data, as shown below. Then select <bpt id="p1">**</bpt>Load<ept id="p1">**</ept> to load the data into the data model for your report.

    ![Power BI に表示される顧客データのデータセットを示すスクリーンショット。](images/customers.png)

1. メインの Power BI Desktop ウィンドウの [データ] メニューで、 **[データの取得]** 、 **[Web]** の順に選択します。

    ![Power BI の [データの取得] メニューを示すスクリーンショット。](images/get-data.png)

1. **[Web から]** ダイアログ ボックスで、次の URL を入力し、**[OK]** を選択します。

    ```
    https://github.com/MicrosoftLearning/DP-900T00A-Azure-Data-Fundamentals/raw/master/power-bi/products.csv
    ```

1. ダイアログで、 **[読み込み]** を選択して、このファイル内の製品データをデータ モデルに読み込みます。

1. 前の 3 つの手順を繰り返して、次の URL から注文データを含む 3 番目のデータセットをインポートします。

    ```
    https://github.com/MicrosoftLearning/DP-900T00A-Azure-Data-Fundamentals/raw/master/power-bi/orders.csv
    ```

## <a name="explore-a-data-model"></a>データ モデルを探索する

インポートした 3 つのデータ テーブルがデータ モデルに読み込まれたため、今度はこれを探索して検索条件を絞ります。

1. In Power BI Desktop, on the left-side edge, select the <bpt id="p1">**</bpt>Model<ept id="p1">**</ept> tab, and then arrange the tables in the model so you can see them. You can hide the panes on the right side by using the <bpt id="p1">**</bpt><ph id="ph1">&gt;&gt;</ph><ept id="p1">**</ept> icons:

    ![Power BI の [モデル] タブを示すスクリーンショット。](images/model-tab.png)

1. **[orders]** テーブルで、**[Revenue]** フィールドを選択し、**[プロパティ]** ペインで、**[Format] (書式)** プロパティを **[Currency] (通貨)** に設定します。

    ![Power BI で収益形式を通貨に設定する方法を示すスクリーンショット。](images/revenue-currency.png)

    この手順により、収益の値がレポートの視覚化で通貨として確実に表示されるようになります。

1. In the products table, right-click the <bpt id="p1">**</bpt>Category<ept id="p1">**</ept> field (or open its <bpt id="p2">**</bpt><ph id="ph1">&amp;vellip;</ph><ept id="p2">**</ept> menu) and select <bpt id="p3">**</bpt>Create hierarchy<ept id="p3">**</ept>. This step creates a hierarchy named <bpt id="p1">**</bpt>Category Hierarchy<ept id="p1">**</ept>. You may need to expand or scroll in the <bpt id="p1">**</bpt>products<ept id="p1">**</ept> table to see this - you can also see it in the <bpt id="p2">**</bpt>Fields<ept id="p2">**</ept> pane:

    ![Power BI でカテゴリ階層を追加する方法を示すスクリーンショット。](images/category-hierarchy.png)

1. In the products table, right-click the <bpt id="p1">**</bpt>ProductName<ept id="p1">**</ept> field (or open its <bpt id="p2">**</bpt><ph id="ph1">&amp;vellip;</ph><ept id="p2">**</ept> menu) and select <bpt id="p3">**</bpt>Add to hierarchy<ept id="p3">**</ept><ph id="ph2"> &gt; </ph><bpt id="p4">**</bpt>Category Hierarchy<ept id="p4">**</ept>. This adds the <bpt id="p1">**</bpt>ProductName<ept id="p1">**</ept> field to the hierarchy you created previously.
1. In the <bpt id="p1">**</bpt>Fields<ept id="p1">**</ept> pane, right-click <bpt id="p2">**</bpt>Category Hierarchy<ept id="p2">**</ept> (or open its <bpt id="p3">**</bpt>...<ept id="p3">**</ept> menu) and select <bpt id="p4">**</bpt>Rename<ept id="p4">**</ept>. Then rename the hierarchy to <bpt id="p1">**</bpt>Categorized Product<ept id="p1">**</ept>.

    ![Power BI で階層の名前を変更する方法を示すスクリーンショット。](images/rename-hierarchy.png)

1. 左端にある **[データ]** タブを選択し、**[フィールド]** ウィンドウで **[customers]** テーブルを選択します。
1. **[City]** 列ヘッダーを選択し、**[データ カテゴリ]** プロパティを **[市区町村]** に設定します。

    ![Power BI でデータ カテゴリを設定する方法を示すスクリーンショット。](images/data-category.png)

    この手順により、この列の値が市区町村名として解釈されるようになり、マップの視覚化を含める場合に役立てることができます。

## <a name="create-a-report"></a>レポートを作成する

Now you're almost ready to create a report. First you need to check some settings to ensure all visualizations are enabled.

1. On the <bpt id="p1">**</bpt>File<ept id="p1">**</ept> menu, select <bpt id="p2">**</bpt>Options and Settings<ept id="p2">**</ept>. Then select <bpt id="p1">**</bpt>Options<ept id="p1">**</ept>, and in the <bpt id="p2">**</bpt>Security<ept id="p2">**</ept> section, ensure that <bpt id="p3">**</bpt>Use Map and Filled Map visuals<ept id="p3">**</ept> is enabled and select <bpt id="p4">**</bpt>OK<ept id="p4">**</ept>.

    ![PowerBI で地図および塗り分け地図ビジュアルのプロパティを設定する方法を示すスクリーンショット。](images/set-options.png)

    この設定により、地図の視覚化を確実にレポートに含めることができます。

1. 左端にある **[レポート]** タブを選択し、レポート デザイン インターフェイスを表示します。

    ![Power BI の [レポート] タブを示すスクリーンショット。](images/report-tab.png)

1. In the ribbon, above the report design surface, select <bpt id="p1">**</bpt>Text Box<ept id="p1">**</ept> and add a text box containing the text <bpt id="p2">**</bpt>Sales Report<ept id="p2">**</ept> to the report. Format the text to make it bold with a font size of 32.

    ![Power BI でテキスト ボックスを追加する方法を示すスクリーンショット。](images/text-box.png)

1. ファイルのダウンロードが完了したら、ファイルを開き、セットアップ ウィザードを使用してコンピューターに Power BI Desktop をインストールします。

    ![Power BI でレポートに分類された製品のテーブルを追加する方法を示すスクリーンショット。](images/categorized-products-table.png)

1. このインストールには数分かかる場合があります。

    The revenue is formatted as currency, as you specified in the model. However, you didn't specify the number of decimal places, so the values include fractional amounts. It won't matter for the visualizations you're going to create, but you could go back to the <bpt id="p1">**</bpt>Model<ept id="p1">**</ept> or <bpt id="p2">**</bpt>Data<ept id="p2">**</ept> tab and change the decimal places if you wish.

    ![レポートに収益が含まれるカテゴリ別製品のテーブルを示すスクリーンショット。](images/revenue-column.png)

1. With the table still selected, in the <bpt id="p1">**</bpt>Visualizations<ept id="p1">**</ept> pane, select the <bpt id="p2">**</bpt>Stacked column chart<ept id="p2">**</ept> visualization. The table is changed to a column chart showing revenue by category.

    ![レポートに収益が含まれるカテゴリ別製品の積み上げ縦棒グラフを示すスクリーンショット。](images/stacked-column-chart.png)

1. Power BI Desktop を開きます。

    ![カテゴリ内の製品を表示するためにドリルダウンされた縦棒グラフを示すスクリーンショット。](images/drill-down.png)

1. アプリケーション インターフェイスは次のようになります。
1. Select a blank area of the report, and then in the <bpt id="p1">**</bpt>Fields<ept id="p1">**</ept> pane, select the <bpt id="p2">**</bpt>Quantity<ept id="p2">**</ept> field in the <bpt id="p3">**</bpt>orders<ept id="p3">**</ept> table and the <bpt id="p4">**</bpt>Category<ept id="p4">**</ept> field in the <bpt id="p5">**</bpt>products<ept id="p5">**</ept> table. This step results in another column chart showing sales quantity by product category.
1. 新しい縦棒グラフを選択した状態で、**[視覚化]** ウィンドウの **[円グラフ]** を選択し、グラフのサイズを変更して、カテゴリ別の収益の縦棒グラフの横に配置します。

    ![カテゴリ別の売上数量を表す円グラフを示すスクリーンショット。](images/category-pie-chart.png)

1. Select a blank area of the report, and then in the <bpt id="p1">**</bpt>Fields<ept id="p1">**</ept> pane, select the <bpt id="p2">**</bpt>City<ept id="p2">**</ept> field in the <bpt id="p3">**</bpt>customers<ept id="p3">**</ept> table and then select the <bpt id="p4">**</bpt>Revenue<ept id="p4">**</ept> field in the <bpt id="p5">**</bpt>orders<ept id="p5">**</ept> table. This results in a map showing sales revenue by city. Rearrange and resize the visualizations as needed:

    ![都市別の収益を示すマップを示すスクリーンショット。](images/revenue-map.png)

1. In the map, note that you can drag, double-click, use a mouse-wheel, or pinch and drag on a touch screen to interact. Then select a specific city, and note that the other visualizations in the report are modified to highlight the data for the selected city.

    ![選択された都市のデータが強調表示されている、都市別の収益を表すマップを示すスクリーンショット。](images/selected-data.png)

1. On the <bpt id="p1">**</bpt>File<ept id="p1">**</ept> menu, select <bpt id="p2">**</bpt>Save<ept id="p2">**</ept>. Then save the file with an appropriate .pbix file name. You can open the file and explore data modeling and visualization further at your leisure.

[Power BI サービス](https://www.powerbi.com/?azure-portal=true)のサブスクリプションをお持ちの場合は、ご自分のアカウントにサインインし、レポートを Power BI ワークスペースに発行できます。 
