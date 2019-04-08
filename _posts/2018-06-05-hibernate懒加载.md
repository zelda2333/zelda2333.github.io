---
layout: post
title: hibernate懒加载
---
懒加载（lazy）即**延迟加载**，当访问数据量过大时，用缓存不太合适，因为内容容量有限，为减少并发和系统资源消耗，我们让**数据**在**需要的时候才进行加载**，这是，就需要懒加载。


关于JAP FetchType.LAZY（hibernate实现）的理解 
https://blog.csdn.net/zgmzyr/article/details/8062004

什么是hibernate懒加载？什么时候用懒加载？为什么要用懒加载？（转）
https://www.cnblogs.com/cornucopia/articles/4541621.html