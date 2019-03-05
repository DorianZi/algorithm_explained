# PCA主成分分析

PCA即Principal Component Analysis, 主成分分析。 主要思想是数据降维
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

更多的数据点

<img src="https://pic3.zhimg.com/v2-89d7327bd92119c2c99357a423d4da26_b.gif">

