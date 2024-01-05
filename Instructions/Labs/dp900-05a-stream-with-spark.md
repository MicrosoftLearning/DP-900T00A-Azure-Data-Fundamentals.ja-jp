---
lab:
  title: Azure Synapse Analytics で Spark ストリーミングを探索する
  module: Explore fundamentals of real-time analytics
---

# Azure Synapse Analytics で Spark ストリーミングを探索する

この演習では、*Spark Structured Streaming* と "デルタ テーブル" を Azure Synapse Analytics で使用して、ストリーミング データを処理します。**

このラボは完了するまで、約 **15** 分かかります。

## 開始する前に

管理レベルのアクセス権を持つ [Azure サブスクリプション](https://azure.microsoft.com/free)が必要です。

## Synapse Analytics ワークスペースをプロビジョニングする

Synapse Analytics を使用するには、Azure サブスクリプションで Synapse Analytics ワークスペース リソースをプロビジョニングする必要があります。

1. [Azure portal](https://portal.azure.com?azure-portal=true) で Azure portal を開き、自分の Azure サブスクリプションに関連付けられている資格情報を使ってサインインします。

    > **注**: ご自分のサブスクリプションが含まれているディレクトリで作業していることを確認してください。右上のユーザー ID の下に示されています。 表示されない場合は、ユーザー アイコンを選択してディレクトリを切り替えてください。

2. Azure portal の **[ホーム]** ページで、**[&#65291; リソースの作成]** アイコンを使用して、新しいリソースを作成します。
3. *Azure Synapse Analytics* を検索し、次の設定を使用して、新しい **Azure Synapse Analytics** リソースを作成します。
    - **[サブスクリプション]**:"*ご自身の Azure サブスクリプション*"
        - **リソース グループ**: *適切な名前 (例: "synapse-rg") の新しいリソース グループを作成します*。
        - **管理対象リソース グループ**: *適切な名前 (例: "synapse") を入力します*。
    - **ワークスペース名**: *一意のワークスペース名 (例: "synapse-ws-<your_name>") を入力します*。
    - **リージョン**: *使用可能なリージョンを選択します*。
    - **Data Lake Storage Gen 2**: サブスクリプションから
        - **アカウント名**: *一意の名前 (例: "datalake<your_name>") の新しいアカウントを作成します*。
        - **アカウント名**: *一意の名前 (例: "fs<your_name>") の新しいファイル システムを作成します*。

    > **注**: Synapse Analytics ワークスペースには、Azure サブスクリプションに 2 つのリソース グループが必要です。1 つは明示的に作成したリソース用で、もう 1 つはサービスによって使用される管理対象リソース用です。 また、データ、スクリプト、その他のアーティファクトを格納するための Data Lake ストレージ アカウントも必要です。

4. これらの詳細を入力したら、**[確認と作成]** を選択し、**[作成]** を選択して、ワークスペースを作成します。
5. ワークスペースが作成されるまで待ちます。これには 5 分程度かかる場合があります。
6. デプロイが完了したら、作成されたリソース グループにアクセスして、Synapse Analytics ワークスペースと Data Lake ストレージ アカウントが含まれていることを確認します。
7. Synapse ワークスペースを選択し、**[概要]** ページの **[Synapse Studio を開く]** カードで、**[開く]** を選択し、新しいブラウザー タブで Synapse Studio を開きます。Synapse Studio は、Synapse Analytics ワークスペースの操作に使用できる Web ベースのインターフェイスです。
8. Synapse Studio の左側で、**&rsaquo;&rsaquo;** アイコンを使用してメニューを展開します。次に示すように、リソースの管理とデータ分析タスクの実行に使用するさまざまなページが Synapse Studio 内に表示されます。

    ![Synapse Studio](images/synapse-studio.png)

## Spark プールを作成する

Spark を使用してストリーミング データを処理するには、Spark プールを Azure Synapse ワークスペースに追加する必要があります。

1. Synapse Studio で、**[管理]** ページを選択します。
2. **[Apache Spark プール]** タブを選択し、**[&#65291; 新規]** アイコンを使用して、次の設定で新しい Spark プールを作成します。
    - **Apache Sparkプール名**: sparkpool
    - **ノード サイズ ファミリ**: メモリ最適化
    - **ノード サイズ**: 小 (4 仮想コア/32 GB)
    - **自動スケール**: 有効
    - **ノードの数**: 3----3
3. Spark プールを確認して作成し、デプロイされるのを待ちます (数分かかる場合があります)。

## ストリーム処理を調べる

Spark でのストリーム処理を調べるには、Spark Structured Streaming とデルタ テーブルでの基本的なストリーム処理を実行するのに役立つ Python コードとメモを含むノートブックを使用します。

1. [Structured Streaming and Delta Tables.ipynb](https://github.com/MicrosoftLearning/DP-900T00A-Azure-Data-Fundamentals/raw/master/streaming/Spark%20Structured%20Streaming%20and%20Delta%20Tables.ipynb) ノートブックをローカル コンピューターにダウンロードします (ノートブックがブラウザーでテキスト ファイルとして開かれる場合は、ローカル フォルダーに保存します。 .txt ファイルとしてではなく、**Structured Streaming and Delta Tables.ipynb** として保存することに注意してください)
2. Synapse Studio で、**[開発]** ページを選びます。
3. **[&#65291;]** メニューの **[&#8612; インポート]** を選び、ローカル コンピューター上の **Structured Streaming and Delta Tables.ipynb** ファイルを選びます。
4. ノートブックの指示に従ってそれを Spark プールにアタッチし、それに含まれているコード セルを実行して、ストリーム処理に Spark を使用するさまざまな方法を調べます。

## Azure リソースを削除する

> **注**: Azure Synapse Analytics が使用されている他の演習を完了しようとしている場合、このセクションはスキップできます。 それ以外の場合は、不要な Azure コストが発生しないよう、次の手順に従ってください。

1. 変更を保存しないで Synapse Studio のブラウザー タブを閉じて、Azure portal に戻ります。
1. Azure portal の **[ホーム]** ページで、**[リソース グループ]** を選択します。
1. (管理対象リソース グループではなく) Synapse Analytics ワークスペースのリソース グループを選択し、ワークスペースとして、Synapse ワークスペース、ストレージ アカウント、Data Explorer プールが含まれていることを確認します (前の演習を完了している場合は、Spark プールも含まれます)。
1. リソース グループの **[概要]** ページの上部で、**[リソース グループの削除]** を選択します。
1. リソース グループ名を入力して、削除することを確認し、**[削除]** を選択します。

    数分後に、Azure Synapse ワークスペースとそれに関連付けられているマネージド ワークスペースが削除されます。
