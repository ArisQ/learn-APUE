---
layout: default
---

花了近半年的时间才将《Unix环境高级编程》”看“了一遍，虽然只是粗略通读，有了大致的了解。想想距离第一次听说APUE已有数年，几次尝试都只是读了开头便难以为继，大部分原因还是水平不够，此次能够看完，应该还是得益于不求甚解的方式。然而，学习如果没有实践，往往难以深入理解，也很快就会忘记，因此，希望从头再来一遍，同时做一些笔记和编程实践。和之前学习编程语言时记写在一个Markdown文件不同，这次笔记希望借助Jekyll发布成静态网页，能够更好的展示。由于耗时会很长，因此会不定期更新。

目录如下：

{% for post in site.posts %}
[{{post.title}}]({{post.url}})
{% endfor %}