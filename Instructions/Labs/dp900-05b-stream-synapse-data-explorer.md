---
lab:
  title: Azure Synapse Data Explorer について調べる
  module: Explore fundamentals of real-time analytics
---

# Azure Synapse Data Explorer について調べる

> **注**: 製品の変更により、このラボの「**データベースの作成とデータの取り込み**」のセクションにいくつかの既知の問題があります。 現在、これらの問題への対処に取り組んでいます。

この演習では、Azure Synapse Data Explorer を使用して時系列データを分析します。

このラボは完了するまで、約 **25** 分かかります。

## 開始する前に

管理レベルのアクセス権を持つ [Azure サブスクリプション](https://azure.microsoft.com/free)が必要です。

## Synapse Analytics ワークスペースをプロビジョニングする

> **ヒント**: 前の演習の Azure Synapse ワークスペースがまだある場合は、このセクションをスキップし、「 **[Data Explorer プールの作成](#create-a-data-explorer-pool)** 」に進んでください。

1. Azure portal ([https://portal.azure/com](https://portal.azure.com?azure-portal=true)) を開き、ご利用の Azure サブスクリプションに関連付けられている資格情報を使用してサインインします。

    > **注**: ご自分のサブスクリプションが含まれているディレクトリで作業していることを確認してください。右上のユーザー ID の下に表示されています。 表示されない場合は、ユーザー アイコンを選択してディレクトリを切り替えてください。

1. Azure portal の **[ホーム]** ページで、**[&#65291; リソースの作成]** アイコンを使用して、新しいリソースを作成します。
1. *Azure Synapse Analytics* を検索し、次の設定を使用して、新しい **Azure Synapse Analytics** リソースを作成します。
    - **[サブスクリプション]**:"*ご自身の Azure サブスクリプション*"
        - **リソース グループ**: *適切な名前 (例: "synapse-rg") の新しいリソース グループを作成します*。
        - **管理対象リソース グループ**: *適切な名前 (例: "synapse") を入力します*。
    - **ワークスペース名**: *一意のワークスペース名 (例: "synapse-ws-<your_name>") を入力します*。
    - **リージョン**: *使用可能なリージョンを選択します*。
    - **Data Lake Storage Gen 2**: サブスクリプションから
        - **アカウント名**: *一意の名前 (例: "datalake<your_name>") の新しいアカウントを作成します*。
        - **アカウント名**: *一意の名前 (例: "fs<your_name>") の新しいファイル システムを作成します*。

    > **注**: Synapse Analytics ワークスペースには、Azure サブスクリプションに 2 つのリソース グループが必要です。1 つは明示的に作成したリソース用で、もう 1 つはサービスによって使用される管理対象リソース用です。 また、データ、スクリプト、その他のアーティファクトを格納するための Data Lake ストレージ アカウントも必要です。

1. これらの詳細を入力したら、**[確認と作成]** を選択し、**[作成]** を選択して、ワークスペースを作成します。
1. ワークスペースが作成されるまで待ちます。これには 5 分程度かかる場合があります。
1. デプロイが完了したら、作成されたリソース グループにアクセスして、Synapse Analytics ワークスペースと Data Lake ストレージ アカウントが含まれていることを確認します。
1. Synapse ワークスペースを選択し、**[概要]** ページの **[Synapse Studio を開く]** カードで、**[開く]** を選択し、新しいブラウザー タブで Synapse Studio を開きます。Synapse Studio は、Synapse Analytics ワークスペースの操作に使用できる Web ベースのインターフェイスです。
1. Synapse Studio の左の **&rsaquo;&rsaquo;** アイコンを使用してメニューを展開します。これにより、リソースの管理とデータ分析タスクの実行に使用する Synapse Studio 内のさまざまなページが表示されます。

## データエクスプローラープールを作成する

1. Synapse Studio で、**[管理]** ページを選択します。
1. **[Data Explorer プール]** タブを選択してから、 **[&#65291; 新規]** アイコンを使用して、次の設定で新しいプールを作成します。
    - **Data Explorer プール名**: dxpool
    - **ワークロード**: コンピューティング最適化
    - **サイズ**: 極小規模 (2 コア)
1. **[次へ: 詳細設定 >]** を選択し、 **[ストリーミング インジェスト]** 設定を有効にします。これにより、データ エクスプローラーで Azure Event Hubs などのストリーミング ソースから新しいデータを取り込むことができます。
1. **[確認と作成]** を選択して Data Explorer プールを作成し、デプロイされるまで待機します (15 分以上かかる場合があります。状態は "作成" から "オンライン" に変わります)。****

## データベースの作成とデータの取り込み

1. Synapse Studio で、**[データ]** ページを選びます。
1. **[ワークスペース]** タブが選択されていることを確認し、必要に応じて、ページの左上にある **&#8635;** アイコンを選択して、**Data Explorer データベース**が表示されるようにビューを更新します。
1. **Data Explorer データベース**を展開し、**dxpool** が表示されていることを確認します。
1. **[データ]** ペインで、 **&#65291;** アイコンを使用して、**iot-data** という名前の新しい **Data Explorer データベース**を **dxpool** プールに作成します。
1. データベースが作成されるのを待機している間に、[https://github.com/MicrosoftLearning/DP-900T00A-Azure-Data-Fundamentals/raw/master/streaming/data/devices.csv](https://github.com/MicrosoftLearning/DP-900T00A-Azure-Data-Fundamentals/raw/master/streaming/data/devices.csv?azure-portal=true) から **devices.csv** をダウンロードし、ローカル コンピューター上の任意のフォルダーに保存します。
1. Synapse Studio で、必要に応じてデータベースが作成されるのを待ってから、新しい **iot-data** データベースの **[...]** メニューで **[Azure Data Explorer で開く]** を選択します。
1. Azure Data Explorer を含む新しいブラウザー タブで、**[データ]** タブの **[新しいデータの取り込み]** を選択します。
1. **[宛先]** ページで、次の設定を選択します。
    - **クラスター**: "Azure Synapse ワークスペースの **dxpool** Data Explorer プール"**
    - **データベース**: iot-data
    - **テーブル**: **devices** という名前の新しいテーブルを作成する
1. **[次へ: ソース]** を選択し、**[ソース]** ページで次のオプションを選択します。
    - **ソースの種類**: ファイル
    - **ファイル**: ローカル コンピューターから **devices.csv** ファイルをアップロードします。
1. **[次へ: スキーマ]** を選択し、**[スキーマ]** ページで、次の設定が正しいことを確認します。
    - **圧縮の種類**: 非圧縮
    - **データ形式**: CSV
    - **最初のレコードを無視する**: 選択済み
    - **マッピング**: devices_mapping
1. 列のデータ型が、*Time (datetime)*、*Device (string)*、および *Value (long)* として正しく識別されていることを確認します。 次に、**[次へ: インジェストを開始する]** を選択してインジェストを開始します。
1. インジェストが完了したら、**[閉じる]** を選択します。
1. Azure Data Explorer の **[クエリ]** タブで、**iot-data** データベースが選択されていることを確認し、クエリ ペインで次のクエリを入力します。

    ```kusto
    devices
    ```

1. ツールバーの **[&#9655; 実行]** を選択してクエリを実行し、結果を確認します。これは次のようになります。

    | 時間 | Device | 値 |
    | --- | --- | --- |
    | 2022-01-01T00:00:00Z | Dev1 | 7 |
    | 2022-01-01T00:00:01Z | Dev2 | 4 |
    |     |     |     |

    結果がこれと一致する場合は、ファイルのデータから **devices** テーブルが正常に作成されています。

    > **ヒント**: この例では、ごく少量のバッチ データをファイルからインポートしました。この演習の目的と照らして問題ありません。 実際には、Data Explorer を使用して大量のデータを分析できます。また、ストリーム インジェストを有効にしたため、Azure Event Hubs などのストリーミング ソースからテーブルにデータを取り込むように Data Explorer を構成することもできます。

## Kusto クエリ言語を使用して Synapse Studio のテーブルに対してクエリを実行する

1. [Azure Data Exporer] ブラウザー タブを閉じ、Synapse Studio が含まれているタブに戻ります。
1. **[データ]** ページで、**iot-data** データベースと **[テーブル]** フォルダーを展開します。 次に、**devices** テーブルの **[...]** メニューで、**[新しい KQL スクリプト]** > **[1000 行を取得]** を選択します。
1. 生成されたクエリとその結果を確認します。 クエリには、次のコードが含まれている必要があります。

    ```kusto
    devices
    | take 1000
    ```

    クエリの結果には、最初の 1000 行のデータが含まれます。

1. 次のように、クエリを変更します。

    ```kusto
    devices
    | where Device == 'Dev1'
    ```

1. **[&#9655; 実行]** を選択して、クエリを実行します。 次に、結果を確認します。これには、*Dev1* デバイスの行のみが含まれている必要があります。

1. 次のように、クエリを変更します。

    ```kusto
    devices
    | where Device == 'Dev1'
    | where Time > datetime(2022-01-07)
    ```

1. クエリを実行し、結果を確認します。結果には、2022 年 1 月 7 日より後の *Dev1* デバイスの行のみが含まれている必要があります。

1. 次のように、クエリを変更します。

    ```kusto
    devices
    | where Time between (datetime(2022-01-01 00:00:00) .. datetime(2022-07-01 23:59:59))
    | summarize AvgVal = avg(Value) by Device
    | sort by Device asc
    ```

1. クエリを実行し、結果を確認します。これには、デバイス名の昇順で 2022 年 1 月 1 日から 1 月 7 日までに記録された平均デバイス値が含まれている必要があります。

1. [KQL クエリ] タブを閉じて、変更を破棄します。

## Azure リソースを削除する

Azure Synapse Analytics の探索が終了したので、不要な Azure コストを避けるために、作成したリソースを削除する必要があります。

1. 変更を保存しないで Synapse Studio のブラウザー タブを閉じて、Azure portal に戻ります。
1. Azure portal の **[ホーム]** ページで、**[リソース グループ]** を選択します。
1. (管理対象リソース グループではなく) Synapse Analytics ワークスペースのリソース グループを選択し、ワークスペースとして、Synapse ワークスペース、ストレージ アカウント、Data Explorer プールが含まれていることを確認します (前の演習を完了している場合は、Spark プールも含まれます)。
1. リソース グループの **[概要]** ページの上部で、**[リソース グループの削除]** を選択します。
1. リソース グループ名を入力して、削除することを確認し、**[削除]** を選択します。

    数分後に、Azure Synapse ワークスペースとそれに関連付けられているマネージド ワークスペースが削除されます。
