---
lab:
  title: Azure Stream Analytics を調べる
  module: Explore data analytics in Azure
---

## <a name="explore-azure-stream-analytics"></a>Azure Stream Analytics を調べる

この演習では、Azure サブスクリプションに Azure Stream Analytics ジョブをプロビジョニングし、それを使用してリアルタイム データのストリームを処理します。

> <bpt id="p1">**</bpt>Note<ept id="p1">**</ept>: The exercise is part of a module on Microsoft Learn, and includes an option to use a <bpt id="p2">*</bpt>sandbox<ept id="p2">*</ept> Azure subscription. However, if you are completing this exercise as part of an instructor-led class, you should use the Azure subscription provided as part of the class instead of the sandbox.

Microsoft Learn の演習を始める前に、Azure サブスクリプション用に Cloud Shell 環境を準備する必要があります。

1. [Azure portal](https://portal.azure.com) (`https://portal.azure.com`) で自分の Azure サブスクリプション資格情報を使用して、Azure サブスクリプションにサインインします。
2. Use the <bpt id="p1">**</bpt>[<ph id="ph1">\&gt;</ph>_]<ept id="p1">**</ept> button to the right of the search bar at the top of the page to create a new Cloud Shell in the Azure portal, selecting a <bpt id="p2">***</bpt>Bash<ept id="p2">***</ept> environment and creating storage if prompted. The cloud shell provides a command line interface in a pane at the bottom of the Azure portal, as shown here:

    ![Azure portal と Cloud Shell のペイン](./images/cloud-shell.png)

3. Note that you can resize the cloud shell by dragging the separator bar at the top of the pane, or by using the <bpt id="p1">**</bpt>&amp;#8212;<ept id="p1">**</ept>, <bpt id="p2">**</bpt>&amp;#9723;<ept id="p2">**</ept>, and <bpt id="p3">**</bpt>X<ept id="p3">**</ept> icons at the top right of the pane to minimize, maximize, and close the pane. For more information about using the Azure Cloud Shell, see the <bpt id="p1">[</bpt>Azure Cloud Shell documentation<ept id="p1">](https://docs.microsoft.com/azure/cloud-shell/overview)</ept>.

4. これで、Microsoft Learn の演習を行う準備ができました。Learn モジュールの (ブランクの) もの (サンドボックス サブスクリプションを使用するマイペースで進める学習者向けに提供されています) ではなく、Azure portal の Cloud Shell を使用できます。

    以下のリンクを使用して、Microsoft Learn の演習を開きます。

    **[Microsoft Learn に移動する](https://docs.microsoft.com/learn/modules/explore-fundamentals-stream-processing/5-exercise-stream-analytics#create-azure-resources)**

> **今後の学習**:後で時間がある場合は、この Microsoft Learn モジュールに戻り、それに含まれる他の演習 (Spark Streaming と Azure Synapse Data Explorer の探索など) を試してみてください。
