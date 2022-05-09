---
lab:
  title: Azure Stream Analytics を調べる
  module: Explore data analytics in Azure
ms.openlocfilehash: 925607333098d0774839d705d4e055a78e32de27
ms.sourcegitcommit: e73a39e323ef061919b58561ff1afdca876ad2b5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/07/2022
ms.locfileid: "141493693"
---
## <a name="explore-azure-stream-analytics"></a>Azure Stream Analytics を調べる

この演習では、Azure サブスクリプションに Azure Stream Analytics ジョブをプロビジョニングし、それを使用してリアルタイム データのストリームを処理します。

> **注**:この演習は Microsoft Learn のモジュールの一部であり、*サンドボックス* の Azure サブスクリプションを使用するオプションが含まれています。 ただし、講師による指導付きクラスの一部としてこの演習を行っている場合は、サンドボックスではなく、クラスの一部として提供される Azure サブスクリプションを使用する必要があります。

Microsoft Learn の演習を始める前に、Azure サブスクリプション用に Cloud Shell 環境を準備する必要があります。

1. [Azure portal](https://portal.azure.com) (`https://portal.azure.com`) で自分の Azure サブスクリプション資格情報を使用して、Azure サブスクリプションにサインインします。
2. ページ上部の検索バーの右側にある **[\>_]** ボタンを使用して、Azure portal で新しい Cloud Shell を作成し、メッセージが表示されたら **_Bash_** 環境を選択してストレージを作成します。 次に示すように、Azure portal の下部にあるペインに、Cloud Shell のコマンド ライン インターフェイスが表示されます。

    ![Azure portal と Cloud Shell のペイン](./images/cloud-shell.png)

3. ペインの上部にある区分線をドラッグして Cloud Shell のサイズを変更したり、ペインの右上にある **&#8212;** 、 **&#9723;** 、**X** アイコンを使用して、ペインを最小化または最大化したり、閉じたりすることができます。 Azure Cloud Shell の使い方について詳しくは、[Azure Cloud Shell のドキュメント](https://docs.microsoft.com/azure/cloud-shell/overview)をご覧ください。

4. これで、Microsoft Learn の演習を行う準備ができました。Learn モジュールの (ブランクの) もの (サンドボックス サブスクリプションを使用するマイペースで進める学習者向けに提供されています) ではなく、Azure portal の Cloud Shell を使用できます。

    以下のリンクを使用して、Microsoft Learn の演習を開きます。

    **[Microsoft Learn に移動する](https://docs.microsoft.com/learn/modules/explore-fundamentals-stream-processing/5-exercise-stream-analytics#create-azure-resources)**

> **今後の学習**:後で時間がある場合は、この Microsoft Learn モジュールに戻り、それに含まれる他の演習 (Spark Streaming と Azure Synapse Data Explorer の探索など) を試してみてください。
