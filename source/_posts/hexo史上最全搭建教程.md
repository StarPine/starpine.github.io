---
title: hexo史上最全搭建教程
date: 2022-02-14 11:43:37
tags:
---

现在市面上的博客很多，如CSDN，博客园，简书等平台，可以直接在上面发表，用户交互做的好，写的文章百度也能搜索的到。缺点是比较不自由，会受到平台的各种限制和恶心的广告。

而自己购买域名和服务器，搭建博客的成本实在是太高了，不光是说这些购买成本，单单是花力气去自己搭这么一个网站，还要定期的维护它，对于我们大多数人来说，实在是没有这样的精力和时间。

那么就有第三种选择，直接在github page平台上托管我们的博客。这样就可以安心的来写作，又不需要定期维护，而且hexo作为一个快速简洁的博客框架，用它来搭建博客真的非常容易。

**写在前面**
 ggplot2是一款风靡全球的绘图R包，可惜的是，我对它的理解只能到入门的水平，本着在实战中学习的理念，我就搜索一下往后可能用得到的图，进行揣摩和优化，然后我发现了一个师兄的公众号，遂跟着这个师兄学习R绘图。公众号在文末。

## 1.读入数据



```bash
dat<-read.table("kegg.txt",
                sep = "\t",
                header = T)
colnames(dat)
```

## 2.过滤数据并用默认参数展示



```xml
library(tidyverse)
dat %>% filter(Corrected.P.Value<0.0001) -> dat01 #这里为了减少计算量，根据P值进行了过滤
dim(dat01)
dim(dat)

library(ggplot2)
dat01$GeneRatio<-dat01$Input.number/200  #ratio的大小其实反应着出现次数的多少
ggplot(dat01,aes(x=GeneRatio,y=Term))+
  geom_point(aes(size=Input.number,color=Corrected.P.Value))
```

![img](https:////upload-images.jianshu.io/upload_images/19527700-df1c0458ff3f06f3.png?imageMogr2/auto-orient/strip|imageView2/2/w/1200/format/webp)

image.png

这当然无法达到我们发文章的要求，需要对其进行美化一下。

## 3. 美化

linux：对linux来说实在是太简单了，因为最早的git就是在linux上编写的，只需要一行代码

```
sudo apt-get install git
1
```

安装好后，用`git --version` 来查看一下版本

# 2. 安装nodejs

新建完成后，指定文件夹目录下有：

- node_modules: 依赖包
- public：存放生成的页面
- scaffolds：生成文章的一些模板
- source：用来存放你的文章
- themes：主题
- ** _config.yml: 博客的配置文件**

对上述几个参数进行解读：

- reorder: 根据出现的次数(generatio)对不同的通路从大到小进行排序。
- coord_cartesian() ：调整画布大小，没什么好说的。
- scale_color_paletteer_c() ：调用调色板paletteer，这里面有很多的调色板可以选用，拿grDevices来说，可以选用topo.colors()、rainbow()、heat.colors()、terrain.colors()、cm.colors()；这里给自己挖了坑，能不能用ggsci来配色，目前没解决，等我解决了会来更正的。
- theme_bw() ：调整网络的有无，也没什么好说的。
- scale_size_continuous()  添加图注，并标注大小范围。

参考链接：
 1.绘图 [https://mp.weixin.qq.com/s/n6TZoEADyDFcGzSzoGxlsg](https://links.jianshu.com/go?to=https%3A%2F%2Fmp.weixin.qq.com%2Fs%2Fn6TZoEADyDFcGzSzoGxlsg)
 2.paletteer documentation：[https://www.rdocumentation.org/packages/paletteer/versions/1.4.0](https://links.jianshu.com/go?to=https%3A%2F%2Fwww.rdocumentation.org%2Fpackages%2Fpaletteer%2Fversions%2F1.4.0)
 3.grDevices documentation：[https://astrostatistics.psu.edu/su07/R/html/grDevices/html/palettes.html](https://links.jianshu.com/go?to=https%3A%2F%2Fastrostatistics.psu.edu%2Fsu07%2FR%2Fhtml%2FgrDevices%2Fhtml%2Fpalettes.html)



作者：巩翔宇Ibrahimovic
链接：https://www.jianshu.com/p/23c02681f7c2
来源：简书
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。



作者：巩翔宇Ibrahimovic
链接：https://www.jianshu.com/p/23c02681f7c2
来源：简书
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。
