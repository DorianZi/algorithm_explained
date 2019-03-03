SVD分解即奇异值分解， 可以从特征值分解推导而来。先理解特征值分解

# 特征值和特征向量
对矩阵A，存在特征向量<img src="https://latex.codecogs.com/gif.latex?\alpha" title="\alpha" />和特征值<img src="https://latex.codecogs.com/gif.latex?\lambda" title="\lambda" />满足：<img src="https://latex.codecogs.com/gif.latex?A\alpha=\lambda\alpha" title="A\alpha=\lambda\alpha" />

如果把矩阵A理解为线性变换，那么上式表示：可以找到向量<img src="https://latex.codecogs.com/gif.latex?\alpha" title="\alpha" />使得A只能对它进行<img src="https://latex.codecogs.com/gif.latex?\lambda" title="\lambda" />倍的拉伸。

我们找到所有的满足条件的特征向量<img src="https://latex.codecogs.com/gif.latex?\alpha_{1},\alpha_{2},...,\alpha_{n}" title="\alpha_{1},\alpha_{2},...,\alpha_{n}" />和特征值<img src="https://latex.codecogs.com/gif.latex?\lambda_{1},\lambda_{2},...,\lambda_{n}" title="\lambda_{1},\lambda_{2},...,\lambda_{n}" />，则可以用它们来描述矩阵A。

为什么可以用来描述矩阵A？怎么描述？这需要从特征向量和特征值的意义来理解。

矩阵所以代表的线性变换由旋转和拉伸构成。
想象有一个力作用在向量上: 矩阵A的线性变换就相当于在特征向量<img src="https://latex.codecogs.com/gif.latex?\alpha" title="\alpha" />方向，使用大小为<img src="https://latex.codecogs.com/gif.latex?\lambda" title="\lambda" />的力进行拉伸
下图v被旋转拉伸到v'

<img src="https://github.com/DorianZi/algorithm_explained/blob/master/res/pic1.png?raw=true">

下图，由于v和特征向量<img src="https://latex.codecogs.com/gif.latex?\alpha" title="\alpha" />同向，则无旋转，长度为拉伸到<img src="https://latex.codecogs.com/gif.latex?\lambda" title="\lambda" />倍

<img src="https://github.com/DorianZi/algorithm_explained/raw/master/res/pic2.png">

所以，特征向量代表线性变换的方向，特征值代表该方向上的拉伸效果。如果有多个特征向量则有多个变换方向，这时候特征值可以理解为权重，权重越大的越强势。


# 矩阵对角化
将矩阵对角化为正交矩阵<img src="https://latex.codecogs.com/gif.latex?P" title="P" />和对角矩阵<img src="https://latex.codecogs.com/gif.latex?\Lambda" title="\Lambda" />的乘积：

<img src="https://latex.codecogs.com/gif.latex?A=P\Lambda&space;P^{-1}" title="A=P\Lambda P^{-1}" />

其中<img src="https://latex.codecogs.com/gif.latex?P" title="P" />为特征矩阵，<img src="https://latex.codecogs.com/gif.latex?\Lambda" title="\Lambda" />为特征值矩阵。又因为正交矩阵的逆矩阵为其转置则：

<img src="https://latex.codecogs.com/gif.latex?A=P\Lambda&space;P^{T}" title="A=P\Lambda P^{T}" />

## 数学推导
正交对角化推导如下：

根据特征值/特征向量定义：

<img src="https://latex.codecogs.com/gif.latex?A\alpha_{1}=\lambda_{1}\alpha_{1},A\alpha_{2}=\lambda_{2}\alpha_{2},...,A\alpha_{n}=\lambda_{n}\alpha_{n}" title="A\alpha_{1}=\lambda_{1}\alpha_{1},A\alpha_{2}=\lambda_{2}\alpha_{2},...,A\alpha_{n}=\lambda_{n}\alpha_{n}" />

合并为矩阵形式：

<img src="https://latex.codecogs.com/gif.latex?A(\alpha_{1},\alpha_{2},...,\alpha_{n})&space;=&space;(\lambda_{1}\alpha_{1},\lambda_{2}\alpha_{2},...,\lambda_{n}\alpha_{n})" title="A(\alpha_{1},\alpha_{2},...,\alpha_{n}) = (\lambda_{1}\alpha_{1},\lambda_{2}\alpha_{2},...,\lambda_{n}\alpha_{n})" />

<img src="https://latex.codecogs.com/gif.latex?A(\alpha_{1},\alpha_{2},...,\alpha_{n})&space;=&space;(\alpha_{1},\alpha_{2},...,\alpha_{n})&space;\begin{bmatrix}&space;\lambda_{1}&&space;&&space;&&space;\\&space;&&space;\lambda_{2}&&space;&&space;\\&space;&&space;&&space;...&&space;\\&space;&&space;&&space;&\lambda_{n}&space;\end{bmatrix}" title="A(\alpha_{1},\alpha_{2},...,\alpha_{n}) = (\alpha_{1},\alpha_{2},...,\alpha_{n}) \begin{bmatrix} \lambda_{1}& & & \\ & \lambda_{2}& & \\ & & ...& \\ & & &\lambda_{n} \end{bmatrix}" />

<img src="https://latex.codecogs.com/gif.latex?A=(\alpha_{1},\alpha_{2},...,\alpha_{n})&space;\begin{bmatrix}&space;\lambda_{1}&&space;&&space;&&space;\\&space;&&space;\lambda_{2}&&space;&&space;\\&space;&&space;&&space;...&&space;\\&space;&&space;&&space;&\lambda_{n}&space;\end{bmatrix}&space;(\alpha_{1},\alpha_{2},...,\alpha_{n})^{-1}" title="A=(\alpha_{1},\alpha_{2},...,\alpha_{n}) \begin{bmatrix} \lambda_{1}& & & \\ & \lambda_{2}& & \\ & & ...& \\ & & &\lambda_{n} \end{bmatrix} (\alpha_{1},\alpha_{2},...,\alpha_{n})^{-1}" />

<img src="https://latex.codecogs.com/gif.latex?A=(\alpha_{1},\alpha_{2},...,\alpha_{n})&space;\begin{bmatrix}&space;\lambda_{1}&&space;&&space;&&space;\\&space;&&space;\lambda_{2}&&space;&&space;\\&space;&&space;&&space;...&&space;\\&space;&&space;&&space;&\lambda_{n}&space;\end{bmatrix}&space;(\alpha_{1},\alpha_{2},...,\alpha_{n})^{T}" title="A=(\alpha_{1},\alpha_{2},...,\alpha_{n}) \begin{bmatrix} \lambda_{1}& & & \\ & \lambda_{2}& & \\ & & ...& \\ & & &\lambda_{n} \end{bmatrix} (\alpha_{1},\alpha_{2},...,\alpha_{n})^{T}" />

## 几何意义
对任意一个向量<img src="https://latex.codecogs.com/gif.latex?\beta" title="\beta" />施加矩阵A变换，相当于连续施加三个变换:<img src="https://latex.codecogs.com/gif.latex?P^{T}" title="P^{T}" /> -> <img src="https://latex.codecogs.com/gif.latex?\Lambda" title="\Lambda" /> -> <img src="https://latex.codecogs.com/gif.latex?P" title="P" /> :

<img src="https://latex.codecogs.com/gif.latex?A\beta=P\Lambda&space;P^{T}\beta" title="A\beta=P\Lambda P^{T}\beta" />

<img src="https://latex.codecogs.com/gif.latex?P" title="P" />和<img src="https://latex.codecogs.com/gif.latex?P^_{T}" title="P^_{T}" />为正交矩阵，只有旋转效果,且它们互为反向旋转；<img src="https://latex.codecogs.com/gif.latex?\Lambda" title="\Lambda" />为对角矩阵，只有拉伸效果。所以该变换为:

旋转 -> 拉伸 -> 转回来 

