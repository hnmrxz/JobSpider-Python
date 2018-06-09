# Python爬虫 分析岗位招聘情况  
  
  **前排万分感谢@chenjiandongx前辈开源本系统爬虫模块核心源代码与思路！**

Life is short, you need Python。
Python 是一门很优雅的语言，用着挺舒服的。所以就在想，现在各专业的岗位招聘，公司们需要什么样的人才？要有什么样的技能？以及对应的市场如何？
  
所以，我又有了一个大胆的想法。  

爬取了[前程无忧](http://jobs.51job.com/)上 的招聘岗位并对招聘信息进行数据分析。

## 岗位分布  

招聘信息中，各城市岗位数量分布如下图。 

![](https://github.com/hnmrxz/JobSpider-Python-PHP/blob/master/images/locate.png)  


## 职位要求  

提取了所有的职位要求，进行分词统计，清理没意义的词，统一英文字符，如 Python 和 python 不区分大小。  

所有词语前 200 生成词云  

![](https://github.com/hnmrxz/JobSpider-Python-PHP/blob/master/images/wc1.png)  
![](https://github.com/hnmrxz/JobSpider-Python-PHP/blob/master/images/wc2.png)  

一直觉得词云还是得**白色背景**视觉效果更好一点。

## 薪酬情况  

下面来谈谈对应的薪酬情况。   
  
工资的单位有 万/月，万/年，千/月 三种，而且所写明的工资是一个范围，如 1.2-1.5 万/月，10-20 万/年。这让我没办法统计，因为这不是一个数，是一个范围而且这是一个字符串。  
最后，我按一个具体的比例处理所有的工资情况。[x, y] 为其范围，取 x + (y - x) * 0.4 的值。拿 1.0-1.5 万/月来说就是取其范围的差（1.5 - 1.0）= 0.5，来乘以一个比值 0.4（为什么是 0.4 呢，这个是我个人估计的，毕竟我还没参加过工作。因为刚开始工作可能就是底薪，后来才慢慢增上去的。就假设认为均值应该是这个）最后得到 1.0 + 0.2 = 1.2，1.2 就是所取的一个权重，就当是该岗位的工资。将处理完的数据存进数据库。  

看看总体的情况  

![](https://github.com/hnmrxz/JobSpider-Python-PHP/blob/master/images/money.png)  


书还是要多读的，掌握多一项技能就多一个优势。也不要局限于只是专业方面的书，**全方位、多角度、深层次、立体化**提高自己的知识水平，也能让自己**腹有诗书气自华**，万一找到女朋友了呢？  

## 最后  

一开始只是想简单研究一下，后来发现数据的分析比数据的爬取要难得多，不过有难度才有意思。一定要提一句，**正则表达式**真是瑞士军刀阿，在处理文本数据上真真是极好的！  

#### 欢迎 Fork 和 Star
