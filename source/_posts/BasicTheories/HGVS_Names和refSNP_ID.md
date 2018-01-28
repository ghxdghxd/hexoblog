在NCBI(美国国立生物技术信息中心)网站上经常会看到“HGVS Names”和“refSNP ID”的字样，这两个都是用于命名SNP(single
nucleotide polymorphism，单核苷酸多态性)的方法。



HGVS是Human Genome Variation
Society(人类基因组变异协会)的简称，是一个非政府的民间学术组织，其官方网站的网址：http://www.hgvs.org/。HGVS命名SNP法的规则是标出引用的核酸序列号（Reference
Sequence，RefSeq）和SNP在该核酸序列中的位置，例如：NG_000004.3:g.247167G&gt;A，其中红色的部分是核酸序列接受号，绿色的部分是该单核苷酸多态性位点在该核酸序列中的位置，G&gt;A表示原始碱基是G，突变碱基是A。这样的命名方法有利于找出所在基因序列中的位置，当向引物公司提交设计和购买申请时都会用到。



在文献中出现的等位基因常见的标注方式，CYP3A5*3(6986A&gt;G或A6986G)，其实这就是一种非常不正规的用HGVS
Names标注SNP位置的方法，很明显，由于缺少引用核酸序列的接受号，因此读者无法从这样的表示在GenBank中查到对应的信息。这是个历史遗留问题，责任也不能全怪原文的作者标注不明，甚至有些时候，由于最初发现并报道该基因位点的文章由于没有被NCBI收录，导致有许多用此法标注的的SNP位点，其引用的RefSeq号竟然丢失了！HGVS正是做着弥补此事的工作，但是由于数据量太大，HGVS目前所完成的只是其中的一部分。所幸NCBI也看到了此事的重大意义，正在接手此事，现在在GenBank的SNP数据库的查询返回结果页的右上角已经可以看到其整理的HGVS
Names了，例如：[**查询CYP3A5*3的结果**](http://www.ncbi.nlm.nih.gov/SNP/snp_ref.cgi?rs=776746)。在该结果我们看到并没有标出6986A&gt;G的HGVS命名，说明该数据库尚须完善。



GenBank官方的refSNP ID单核苷酸多态性命名法是相对比较完善的命名体系，命名方法是rs+7位阿拉伯数字，例如：CYP3A5*3的refSNP
ID是rs776746，如果已知一个SNP的refSNP
ID，那么就可以在GenBank的SNP数据库中搜索到相关的信息和在基因组中的位置了。这里是[**GenBank的SNP数据库查询地址**](http://www.ncbi.nlm.nih.gov/sites/entrez?db=snp)，例如，要查找CYP3A5*3在GenBank中的信息，只要在该搜索框中输入“
rs776746 ”进行查找即可。下面是该查询返回的结果，如图：

![](http://u.jimdo.com/www102/o/se19ec0f28937288f/img/iac1a9acbed828ae0/1279201754/std/image.jpg)

在该返回结果中可以看到给出了CYP3A5*3位点两侧少量的碱基序列，其下方给出了HGVS
Names的链接，我们点击该链接，然后在接下来的网页点击“FASTA”链接即可获得该SNP所在的核苷酸碱基序列了，但是有些时候HGVS
Names引用的核酸碱基序列较长，本示例中引用的核酸碱基序列就有几千万碱基之多，光下载都需要很长的时间，更别说在浏览器中打开了。此时可以点击上图中的红色“rs776746”链接，看看是否有其他引用核苷酸碱基序列较短的HGVS
Names，在打开的页面的右上角可以看到有四个HGVS Names，如下：

NG_000004.3:g.247167G&gt;A

NG_007938.1:g.12083G&gt;A

NM_000777.2:c.219-237G&gt;A

NT_007933.14:g.24504815C&gt;T

其中，前两个很短，估计引用的核酸序列也较短，可以用来查看对应的核苷酸碱基序列，第三个样子有些怪，其实就是不规则命名遗留下来的，除了便于查询外，已经没有什么实际意义了。以第一个HGVS
Names为例，首先打开[**GenBank的Nucleotide查询数据库**](http://www.ncbi.nlm.nih.gov/sites/entrez?db=nuccore)，在搜索框中输入核苷酸碱基序列“
NG_000004.3
”，点击“go”键执行搜索，在返回的结果页点击“FASTA”链接，即可获得该SNP所在的核苷酸碱基序列了。在打开该序列的所在页面中，利用前面在SNP数据库中查到的该SNP的序列片段，依次点击IE浏览器菜单栏上的：编辑
\- 在该页上查找 - 输入一段碱基序列，即可找到该SNP在此核苷酸碱基序列中的具体位置了，还可以通过点击该页面上的

“More Formats”链接 - "GenBank(full)"链接，通过网页中给出的碱基序列的位置编号来找到该SNP 所在的位置。



可能有很多人会存在这样的疑问，例如，在文献中看到类似CYP3A5*3(6986A&gt;G)这样的等位基因名称，但此时还不知道它的refSNP
ID，该如何找到该SNP在GenBank中所在的位置呢？遇到这种情况也只有在Google上碰碰运气了，因为有的文献作者会对这种残缺的HGVS
Names的SNP在文章中同时标出其refSNP ID，查询的方法是在Google中输入“该SNP的HGVS Names + refSNP
ID”进行查找即可，例如：[g"++++"refSNP+ID"&amp;btnG=Google+搜索&amp;meta=&amp;aq=f&amp;oq="
target="_blank" style="color: rgb(0, 6,
220);"&gt;**搜索CYP3A5*3(6986A&gt;G)**](http://www.google.cn/search?hl=zh-
CN&newwindow=1&q=)，如果没有找到满意的检索结果，也可以直接在上文提到的GenBank的SNP数据库的搜索框中直接输入该SNP所在的基因名称+Homo
sapiens（人类），例如输入“ CYP3A5  Homo sapiens "[这里需要说明的是目前只有人类的等位基因才会给出HGVS
Names]，执行搜索后会返回很多该基因的SNP，每个SNP除标有refSNP ID之外，还常标出数个HGVS
Names，这时就可以直接利用浏览器的网页查找功能搜索如“_599A&gt;G”，_来找到对应的refSNP
ID了。这里推荐的一个小窍门是，假如返回的SNP数量较多的话，可以将每页显示结果的数量设置的多一些（选择show后面的数值），会减少很多反复翻页的麻烦。

