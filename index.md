---
title: 联机托管说明
permalink: index.html
layout: home
---

# <a name="content-directory"></a>内容目录

下面列出了每个实验室练习和演示的超链接。

## <a name="labs"></a>实验室

{% assign labs = site.pages | where_exp:"page", "page.url contains '/Instructions'" %}
| 部分 | 实验室 |
| --- | --- | 
{% for activity in labs  %}| {{ activity.lab.module }} | [{{ activity.lab.title }}{% if activity.lab.type %} - {{ activity.lab.type }}{% endif %}]({{ site.github.url }}{{ activity.url }}) |
{% endfor %}
