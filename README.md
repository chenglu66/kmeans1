# kmeans1
kmeans的原理和具体应用
kmeans是一种无监督的自动聚类的算法，就是随便取几个类，然后不断聚合，知道中心点不在改变。
下面用数学语言描述下，我每次都在最小化，距离信息永远是度量相似程度的一直方式，
那么既然是距离，每个点计算到之心的距离，离那个近就归为哪一类，
必然要把信息都归一化了，不然会有很大问题
但是下一个我怎么量化我的想法，就是所有点到自己类之心的距离最小，这样可以表示成和的概念。
然后在不断重复这个过程，这个算法有两个角度：
一是我怎么怎么确保这种算法会收敛，即能不能找到这些之心点，关键这个表面上像是一个凸函数，但是里面的变量是变得。所以怎么设计算法来
保证我的目标是不断减小的而且还是收敛的。
对于两个变量的我可以固定一个去求另一个，然后再用求好的类去计算这个变量。数学上怎么证明可行。
数学上证明可以参考EM算法，链接为https://www.zhihu.com/question/49972233?sort=created
总结下就是
k-means算法与EM算法的关系是这样的：k-means是两个步骤交替进行，可以分别看成E步和M步；M步中将每类的中心更新为分给该类各点的均值，可以认为是在「各类分布均为单位方差的高斯分布」的假设下，最大化似然值；E步中将每个点分给中心距它最近的类（硬分配），可以看成是EM算法中E步（软分配）的近似。
作者：王赟 Maigo
链接：https://www.zhihu.com/question/49972233/answer/119434460
来源：知乎
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。
我的理解就是，把kemans中的最小化误差，转换成最大化似然概率，但是怎么转换，我可以假设一些分布这些分布是单位方差的情况下的高斯分布。
这样最大化这概率也就是最小化误差，so下面就是Em算法了。找Q函数，Q函数可以理解为在参数条件下最大化后验概率。
下面就是最小化Q函数，所以要想使函数值最小，减去的值应该取成均值。ok
算法简要介绍到这里完成
下面开始具体应用：
问题的定义：假如有个朋友过生日，他想要去地方给成了经纬度的位置，而这些位置约有，70多个地方，要设计一个算法把这个路程设计为最短。ok
下面开始思考这个问题，就是要去的地方要把路程要求最短。路程就是距离，距离最短是什么，你肯定不会想只要一个地方吧
所以我可与开车到很多地方然后在这些地方在步行，说以这样目标函数就出来了，ok
目标函数是什么就是Kmeans的损失函数，ok那么就用kmeans算法来解吧
so；
最后的结果为：
![image](https://github.com/chenglu66/kmeans1/blob/master/figure_1-1.png)
so 无论那种算法对问题的定义都要特别有用，然后是量化成数学目标，然后设计算法，最后在验证算法的收敛性。
具体代码实现的注释都在代码中表示。


