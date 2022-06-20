---
title: オンラインでホスティングされている手順
permalink: index.html
layout: home
ms.openlocfilehash: 928f59a9cdc6a3f70d5ad651fb1b5a45b405cee8
ms.sourcegitcommit: 1117342052bce0bbd5a703bd1f763862b9129807
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/16/2022
ms.locfileid: "140682428"
---
# <a name="azure-data-fundamentals-exercises"></a>Azure データの基礎の演習

以下のリンクを使用して、Microsoft コース [DP-900 *Microsoft Azure のデータの基礎*](https://docs.microsoft.com/learn/certifications/courses/dp-900t00) のハンズオン ラボ演習を完了してください。

演習を完了するには、Microsoft Azure のサブスクリプションが必要です。 講師からサブスクリプションが提供されていない場合は、[https://azure.microsoft.com](https://azure.microsoft.com) で無料の試用版にサインアップできます。

{% assign labs = site.pages | where_exp:"page", "page.url contains '/Instructions/Labs'" %}
| モジュール | ラボ |
| --- | --- | 
{% for activity in labs  %}| {{ activity.lab.module }} | [{{ activity.lab.title }}{% if activity.lab.type %} - {{ activity.lab.type }}{% endif %}]({{ site.github.url }}{{ activity.url }}) |
{% endfor %}
