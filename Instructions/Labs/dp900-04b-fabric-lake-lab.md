---
lab:
  title: Microsoft Fabric のデータ分析を探索する
  module: Explore fundamentals of large-scale data analytics
---

# Microsoft Fabric のデータ分析を探索する

この演習では、Microsoft Fabric Lakehouse のデータ インジェストと分析について探索します。

このラボは完了するまで、約 **25** 分かかります。

> **注**: この演習を完了するには、Microsoft Fabric ライセンスが必要です。 無料の Fabric 試用版ライセンスを有効にする方法の詳細については、[Fabric の概要](https://learn.microsoft.com/fabric/get-started/fabric-trial)に関するページを参照してください。 これを行うには、Microsoft の "学校" または "職場" アカウントが必要です。** ** お持ちでない場合は、[Microsoft Office 365 E3 以降の試用版にサインアップ](https://www.microsoft.com/microsoft-365/business/compare-more-office-365-for-business-plans)できます。

*Microsoft Fabric の機能を初めて使用する場合は、ヒントを含むプロンプトが表示されることがあります。これらを閉じます。*

## ワークスペースの作成

Fabric でデータを操作する前に、Fabric 試用版を有効にしてワークスペースを作成してください。

1. [Microsoft Fabric](https://app.fabric.microsoft.com) (`https://app.fabric.microsoft.com`) にサインインします。
1. メニュー バーの左下で、**[Data Engineering]** エクスペリエンスに切り替えます。

    ![エクスペリエンス スイッチャー メニューのスクリーンショット。](./images/fabric-switcher.png)

1. 左側のメニュー バーで、 **[ワークスペース]** を選択します (アイコンは &#128455; に似ています)。
1. 新しいワークスペースを任意の名前で作成し、 **[詳細]** セクションで、Fabric 容量を含むライセンス モード ("*試用版*"、*Premium*、または *Fabric*) を選択します。
1. 開いた新しいワークスペースは空のはずです。

    ![Power BI の空のワークスペースのスクリーンショット。](./images/new-workspace.png)

## レイクハウスを作成する

ワークスペースが作成されたので、次にデータ ファイル用のデータ レイクハウスを作成します。

1. ワークスペースの [ホーム] ページで、任意の名前で新しい**レイクハウス**を作成します。

    1 分ほどすると、新しいレイクハウスが作成されます。

    ![新しいレイクハウスのスクリーンショット。](./images/new-lakehouse.png)

1. 新しいレイクハウスを表示します。左側の **[レイクハウス エクスプローラー]** ペインを使用すると、レイクハウス内のテーブルとファイルを参照できることに注意してください。
    - **Tables** フォルダーには、SQL を使用してクエリを実行できるテーブルが含まれます。 Microsoft Fabric レイクハウスのテーブルは、Apache Spark でよく使われるオープンソースの *Delta Lake* ファイル形式に基づいています。
    - **Files** フォルダーには、マネージド デルタ テーブルに関連付けられていないレイクハウスの OneLake ストレージ内のデータ ファイルが含まれています。 このフォルダーに ''ショートカット'' を作成して、外部に格納されているデータを参照することもできます。**

    現在、レイクハウスにはテーブルやファイルはありません。

## データの取り込み

データを簡単に取り込むには、パイプラインで**データのコピー** アクティビティを使用して、データをソースから抽出し、レイクハウス内のファイルにコピーします。

1. ご自分のレイクハウスの **[ホーム]** ページで、**[データの取得]** メニューの **[新しいデータ パイプライン]** を選択し、**Ingest Data** という名前の新しいデータ パイプラインを作成します。
1. **データのコピー** ウィザードの **[データ ソースの選択]** ページで、**[サンプル データ]** を選択し、**NYC Taxi - Green** サンプル データセットを選択します。

    ![[データ ソースの選択] ページのスクリーンショット。](./images/choose-data-source.png)

1. **[データ ソースへの接続]** ページでデータ ソース内のテーブルを表示します。 ニューヨーク市のタクシー乗車の詳細を含むテーブルが 1 つ必要です。 **[次へ]** を選択して、 **[データの宛先の選択]** ページに進みます。
1. **[データのコピー先の選択]** ページで、既存のレイクハウスを選択します。 **[次へ]** を選択します。
1. データのコピー先オプションを次のように設定し、 **[次へ]** を選択します。
    - **ルート フォルダー**: テーブル
    - **設定の読み込み**: 新しいテーブルに読み込む
    - **変換先テーブル名**: taxi_rides *(これを変更する前に、列マッピングのプレビューが表示されるまで待つ必要がある場合があります)*
    - **列マッピング**: "既定のマッピングのままにする"**
    - **パーティションを有効にする**: "未選択"**
1. **[レビューと保存]** ページで、 **[データ転送をすぐに開始する]** オプションが確実に選択されているようにし、 **[保存と実行]** を選択します。

    次に示すように、**データのコピー** アクティビティを含む新しいパイプラインが作成されます。

    ![データのコピー アクティビティを含むパイプラインのスクリーンショット。](./images/copy-data-pipeline.png)

    パイプラインの実行が開始されたら、パイプライン デザイナーの **[出力]** ペインで状態を監視できます。 **&#8635;** (*[更新]*) アイコンを使用して、状態を更新し、正常に終了するまで待ちます (10 分以上かかる場合があります)。

1. 左側のハブ メニュー バーで、レイクハウスを選択します。
1. **[ホーム]** ページの **[Lakehouse エクスプローラー]** ウィンドウの **[テーブル]** ノードの **[...]** メニューで **[更新]** を選択し、**[テーブル]** を展開して、**taxi_rides** テーブルが作成されたことを確認します。

    > **注**: 新しいテーブルに*未確認*と表示されている場合は、**[更新]** メニュー オプションを使用してビューを更新します。

1. **taxi_rides** テーブルを選択して、その内容を表示します。

    ![taxi_rides テーブルのスクリーンショット。](./images/dimProduct.png)

## レイクハウス内のデータに対してクエリを実行する

レイクハウスのテーブルにデータを取り込んだので、SQL を使用してクエリを実行しましょう。

1. [レイクハウス] ページの右上で、**レイクハウス**ビューをご自分のレイクハウスの **[SQL 分析エンドポイント]** に切り替えます。

1. ツール バーで、 **[新しい SQL クエリ]** を選択します。 クエリ エディターに次の SQL コードを入力します。

    ```sql
    SELECT  DATENAME(dw,lpepPickupDatetime) AS Day,
            AVG(tripDistance) As AvgDistance
    FROM taxi_rides
    GROUP BY DATENAME(dw,lpepPickupDatetime)
    ```

1. **[&#9655; 実行]** ボタンを選択してクエリを実行し、結果を確認します。これには、各曜日の平均乗車距離が含まれている必要があります。

    ![SQL クエリのスクリーンショット。](./images/sql-query.png)

## レイクハウスでデータを視覚化する

Microsoft Fabric のレイクハウスでセマンティック データ モデル内のすべてのテーブルを整理し、視覚化とレポートを作成するのに使用できます。

1. ページの左下にある **[エクスプローラー]** ウィンドウの下で、**[モデル]** タブを選択して、レイクハウスのテーブルのデータ モデルを表示します (これには、システム テーブルと **taxi_rides** テーブルが含まれています)。
1. ツール バーで **[新しいレポート]** を選択し、**taxi_rides** に基づいて新しいレポートを作成します。
1. レポート デザイナーで次の手順を行います。
    1. **[データ]** ウィンドウで、**taxi_rides** テーブルを展開し、**lpepPickupDatetime** フィールドと **passengerCount** フィールドを選択します。
    1. **[視覚化]** ウィンドウで、**[折れ線グラフ]** の視覚化を選択します。 次に、**X 軸** に **lpepPickupDatetime** フィールドが含まれており、**Y** 軸に **passengerCount の合計**が含まれていることを確認します。

        ![Power BI のレポートのスクリーンショット。](./images/fabric-report.png)

    > **ヒント**: **>>** アイコンを使用すると、レポートを見やすくするためにレポート デザイナー ペインを非表示にできます。

1. **[ファイル]** メニューの **[保存]** を選択して、レポートを**タクシー乗車レポート**としてご自分の Fabric ワークスペースに保存します。

    レポートは、Microsoft Fabric ポータルで、ご自分のワークスペースのページで確認できます。

## リソースをクリーンアップする

Microsoft Fabric の探索が終了したら、この演習用に作成したワークスペースを削除できます。

1. 左側のバーで、ワークスペースのアイコンを選択して、それに含まれるすべての項目を表示します。
2. ツール バーの **[...]** メニューで、 **[ワークスペースの設定]** を選択してください。
3. **[その他]** セクションで、 **[このワークスペースの削除]** を選択してください。
