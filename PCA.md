# PCA主成分分析

## 降维思想
PCA即Principal Component Analysis, 主成分分析。主要思想是数据降维。

降维的办法常常是利用现有的n维数据的统计特征，创造更少的m维特征来表示该组数据，实现降维。

有三个数据点在正交基<img src="https://latex.codecogs.com/gif.latex?(\underset{i}{\rightarrow},\underset{j}{\rightarrow})" title="(\underset{i}{\rightarrow},\underset{j}{\rightarrow})" />下表示为<img src="https://latex.codecogs.com/gif.latex?(x_{1},y_{1}),(x_{2},y_{2}),(x_{3},y_{3})" title="(x_{1},y_{1}),(x_{2},y_{2}),(x_{3},y_{3})" />


<img src="https://github.com/DorianZi/algorithm_explained/raw/a31c6088efb30703792fd4fbaa4132985eb10e00/res/pca_2.png">

我们可以用2x3矩阵来表示它：

<img src="https://latex.codecogs.com/gif.latex?\begin{bmatrix}&space;x_{1}&space;&&space;x_{2}&&space;x_{3}\\&space;y_{1}&space;&&space;y_{2}&&space;y_{3}&space;\end{bmatrix}" title="\begin{bmatrix} x_{1} & x_{2}& x_{3}\\ y_{1} & y_{2}& y_{3} \end{bmatrix}" />

这里我们发现数据的x与y两个维度有着规律：x=2y，则我们可以创造出新的维度<img src="https://latex.codecogs.com/gif.latex?\underset{k}{\rightarrow}" title="\underset{k}{\rightarrow}" /> :

<img src="https://latex.codecogs.com/gif.latex?2\underset{i}{\rightarrow}&plus;\underset{j}{\rightarrow}=\underset{k}{\rightarrow}" title="2\underset{i}{\rightarrow}+\underset{j}{\rightarrow}=\underset{k}{\rightarrow}" />

在新维度下表示数据只需要1x3矩阵：

<img src="https://latex.codecogs.com/gif.latex?\begin{bmatrix}&space;x_{1}&space;&&space;x_{2}&&space;x_{3}&space;\end{bmatrix}" title="\begin{bmatrix} x_{1} & x_{2}& x_{3} \end{bmatrix}" />

至此，实现了降维。

## 最大方差

上面是一种特殊情况，即所有数据点恰好在一个向量方向上。通常情况，我们有很多数据点且并非所有数据都能连成一条线。

这时候我们要找到一个维度（一个向量），让所有数据投影（降维）到该向量上之后，尽可能地分散。因为越分散说明通过该向量降维之后数据得以很好地区分，越紧凑说明该降维导致了越多信息丢失。数学上表达“分散”的方式就是：方差。方差越大，则说明数据越分散

为了计算方差方便，对数据进行去均值（即以各维度的均值所指明的点为中点）。接下来我们要找到一个单位向量（为了计算方便）使得投影后数据最分散，即方差最大：

<img src="https://pic3.zhimg.com/v2-89d7327bd92119c2c99357a423d4da26_b.gif">

<img src="https://github.com/DorianZi/algorithm_explained/blob/master/res/pca_3.png?raw=true">

设该向量为<img src="https://latex.codecogs.com/gif.latex?v" title="v" />, 数据点为向量（以中心点为原点作向量）<img src="https://latex.codecogs.com/gif.latex?x_{1},x_{2},...,x_{n}" title="x_{1},x_{2},...,x_{n}" />

通过向量点积求投影长度：<img src="https://latex.codecogs.com/gif.latex?d_{i}=\frac{x_{i}^{T}v}{|v|}" title="d_{i}=\frac{x_{i}^{T}v}{|v|}" />

则方差为:

<img src="https://latex.codecogs.com/gif.latex?\sigma&space;^{2}=\sum_{i=1}^{n}d_{i}^{2}=\sum_{i=1}^{n}(\frac{x_{i}^{T}v}{|v|})^{2}" title="\sigma ^{2}=\sum_{i=1}^{n}d_{i}^{2}=\sum_{i=1}^{n}(\frac{x_{i}^{T}v}{|v|})^{2}" />

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<img src="https://latex.codecogs.com/gif.latex?=\sum_{i=1}^{n}(\frac{x_{i}^{T}vx_{i}^{T}v}{v^{T}v})" title="=\sum_{i=1}^{n}(\frac{x_{i}^{T}vx_{i}^{T}v}{v^{T}v})" />

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<img src="https://latex.codecogs.com/gif.latex?=\sum_{i=1}^{n}v^{T}x_{i}x_{i}^{T}v" title="=\sum_{i=1}^{n}v^{T}x_{i}x_{i}^{T}v" />

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<img src="https://latex.codecogs.com/gif.latex?=v^{T}(\sum_{i=1}^{n}x_{i}x_{i}^{T})v" title="=v^{T}(\sum_{i=1}^{n}x_{i}x_{i}^{T})v" />

设<img src="https://latex.codecogs.com/gif.latex?C=\sum_{i=1}^{n}x_{i}x_{i}^{T}" title="C=\sum_{i=1}^{n}x_{i}x_{i}^{T}" />， 则C为协方差矩阵。则：

<img src="https://latex.codecogs.com/gif.latex?\sigma&space;^{2}=v^{T}Cv" title="\sigma ^{2}=v^{T}Cv" />

所以接下来我们要求取一个单位向量<img src="https://latex.codecogs.com/gif.latex?v" title="v" />（即约束条件：<img src="https://latex.codecogs.com/gif.latex?v^{T}v=1" title="v^{T}v=1" />）使得方差<img src="https://latex.codecogs.com/gif.latex?v^{T}Cv" title="v^{T}Cv" />最大

采用拉格朗日乘子法,即转换为求如下函数的极值：

<img src="https://latex.codecogs.com/gif.latex?f(v,\lambda)=v^{T}Cv-\lambda(v^{T}v-1)" title="f(v,\lambda)=v^{T}Cv-\lambda(v^{T}v-1)" />

求极值，则要求偏导数为0：

<img src="https://latex.codecogs.com/gif.latex?\begin{cases}&space;\frac{\partial&space;f}{\partial&space;v}=\frac{\partial&space;(v^{T}Cv)}{\partial&space;v}-\lambda\frac{\partial&space;(v^{T}v)}{\partial&space;v}=2Cv-2\lambda&space;v=0\\&space;\frac{\partial&space;f}{\partial&space;\lambda}=v^{T}v-1=0&space;\end{cases}" title="\begin{cases} \frac{\partial f}{\partial v}=\frac{\partial (v^{T}Cv)}{\partial v}-\lambda\frac{\partial (v^{T}v)}{\partial v}=2Cv-2\lambda v=0\\ \frac{\partial f}{\partial \lambda}=v^{T}v-1=0 \end{cases}" />

顺便提一下<img src="https://latex.codecogs.com/gif.latex?\frac{\partial&space;(v^{T}Cv)}{v}=2Cv" title="\frac{\partial (v^{T}Cv)}{v}=2Cv" />的求导过程，利用了协方差矩阵C为对称实矩阵的特性，不然你得不到<img src="https://latex.codecogs.com/gif.latex?2Cv" title="2Cv" />这么完美的结果的。

同时<img src="https://latex.codecogs.com/gif.latex?2Cv-2\lambda&space;v=0&space;=>&space;Cv=\lambda&space;v" title="2Cv-2\lambda v=0 => Cv=\lambda v" />，恰好是特征向量和特征值的定义！

于是，上面的极值条件转换为：
##### 求协方差矩阵C的单位特征向量

不过，特征向量和特征值那么多，哪一个才是使得方差最大呢？

<img src="https://latex.codecogs.com/gif.latex?\sigma&space;^{2}=v^{T}Cv=v^{T}\lambda&space;v=\lambda&space;v^{T}v=\lambda" title="\sigma ^{2}=v^{T}Cv=v^{T}\lambda v=\lambda v^{T}v=\lambda" />

所以，最大特征值对应的特征向量使得方差最大，也就是使得数据降维之后最分散。

不过在实际PCA应用中，一般不会直接降维到只有一个特征向量。降维是为了在容许丢失部分信息的前提下简化数据复杂度，不是为了简化数据复杂度而去一味地降维。于是，我们会从大到小，选则m个最大的特征值对应的特征向量，组成新的m组维度，来表示原始数据。在PCA里称这是m个主元。

## 协方差矩阵
协方差矩阵为实对称矩阵，则可以对角化为：

<img src="https://latex.codecogs.com/gif.latex?C=U\Lambda&space;U^{T}" title="C=U\Lambda U^{T}" />

其中<img src="https://latex.codecogs.com/gif.latex?U" title="U" />为特征向量组成的正交矩阵，<img src="https://latex.codecogs.com/gif.latex?\Lambda" title="\Lambda" />为对应的特征值独角矩阵

