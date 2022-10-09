---
title: オンラインでホスティングされている手順
permalink: index.html
layout: home
---

# <a name="azure-data-fundamentals-exercises"></a>Azure データの基礎の演習

これらの実践的な演習は、[Microsoft Learn](https://docs.microsoft.com/training/) のトレーニング コンテンツをサポートするように設計されています。

これらの演習を完了するには、管理権限を持つ Microsoft Azure サブスクリプションが必要です。 [https://azure.microsoft.com](https://azure.microsoft.com) で無料試用版にサインアップできます。

{% assign labs = site.pages | where_exp:"page", "page.url contains '/Instructions/Labs'" %}
| 演習 |
| --- |
{% for activity in labs %}| [{{ activity.lab.title }}{% if activity.lab.type %} - {{ activity.lab.type }}{% endif %}]({{ site.github.url }}{{ activity.url }}) |
{% endfor %}
