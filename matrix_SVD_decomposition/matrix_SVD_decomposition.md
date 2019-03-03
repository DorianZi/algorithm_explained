SVD分解即奇异值分解， 可以从特征值分解推导而来。先理解特征值分解

# 特征值和特征向量
对矩阵A，存在特征向量<img src="https://latex.codecogs.com/gif.latex?\alpha" title="\alpha" />和特征值<img src="https://latex.codecogs.com/gif.latex?\lambda" title="\lambda" />满足：<img src="https://latex.codecogs.com/gif.latex?A\alpha=\lambda\alpha" title="A\alpha=\lambda\alpha" />

如果把矩阵A理解为线性变换，那么上式表示：可以找到向量<img src="https://latex.codecogs.com/gif.latex?\alpha" title="\alpha" />使得A只能对它进行<img src="https://latex.codecogs.com/gif.latex?\lambda" title="\lambda" />倍的拉伸。

以<font size=5>基变换</font>来理解。我们先构建一个“绝对”坐标系（如下图）。为了便于计算，设置原基为<img src="https://latex.codecogs.com/gif.latex?\binom{1}{0}" title="\binom{1}{0}" />和<img src="https://latex.codecogs.com/gif.latex?\binom{0}{1}" title="\binom{0}{1}" />，正好与“绝对”坐标系重叠。

通过矩阵<img src="https://latex.codecogs.com/gif.latex?\begin{bmatrix}&space;3&&space;1\\&space;0&2&space;\end{bmatrix}" title="\begin{bmatrix} 3& 1\\ 0&2 \end{bmatrix}" />换基，可直接计算得到实际上是将原基变换为新基<img src="https://latex.codecogs.com/gif.latex?\binom{3}{0}" title="\binom{3}{0}" />和<img src="https://latex.codecogs.com/gif.latex?\binom{1}{2}" title="\binom{1}{2}" />：

<img src="https://latex.codecogs.com/gif.latex?\begin{bmatrix}&space;3&space;&&space;1\\&space;0&space;&&space;2&space;\end{bmatrix}\begin{bmatrix}&space;1\\&space;0&space;\end{bmatrix}=\begin{bmatrix}&space;3\\&space;0&space;\end{bmatrix}" title="\begin{bmatrix} 3 & 1\\ 0 & 2 \end{bmatrix}\begin{bmatrix} 1\\ 0 \end{bmatrix}=\begin{bmatrix} 3\\ 0 \end{bmatrix}" />

<img src="https://latex.codecogs.com/gif.latex?\begin{bmatrix}&space;3&space;&&space;1\\&space;0&space;&&space;2&space;\end{bmatrix}\begin{bmatrix}&space;0\\&space;1&space;\end{bmatrix}=\begin{bmatrix}&space;1\\&space;2&space;\end{bmatrix}" title="\begin{bmatrix} 3 & 1\\ 0 & 2 \end{bmatrix}\begin{bmatrix} 0\\ 1 \end{bmatrix}=\begin{bmatrix} 1\\ 2 \end{bmatrix}" />

换基不影响坐标值，所以原基下的坐标(1,1)，变换后在新基下的坐标也是(1,1），而在“绝对”坐标系中坐标为(4,2)

在基变换体系下，我们无法直接获得特征向量和特征值的几何意义，以空间拉伸来解释会获得更直观理解。

以<font size=5>空间拉伸</font>来理解，以下线性变换将正方形围住的空间变换成普通平行四边形。大部分向量都被施加了旋转和拉伸（<font color=#8B0000>褐色</font>），只有特征向量<img src="https://latex.codecogs.com/gif.latex?\alpha_{1},\alpha_{2}" title="\alpha_{1},\alpha_{2}" />（<font color=#008000>绿色</font>和<font color=#0000FF>蓝色</font>）所在方向的向量只进行了拉伸，且拉伸效果为相应的特征值<img src="https://latex.codecogs.com/gif.latex?\lambda_{1},\lambda_{2}" title="\lambda_{1},\lambda_{2}" />

<img src="https://github.com/DorianZi/algorithm_explained/raw/master/res/pic1.png">

<img src="https://latex.codecogs.com/gif.latex?\begin{bmatrix}&space;3&space;&&space;1\\&space;0&space;&&space;2&space;\end{bmatrix}\begin{bmatrix}&space;1\\&space;1&space;\end{bmatrix}=\begin{bmatrix}&space;4\\&space;2&space;\end{bmatrix}" title="\begin{bmatrix} 3 & 1\\ 0 & 2 \end{bmatrix}\begin{bmatrix} 1\\ 1 \end{bmatrix}=\begin{bmatrix} 4\\ 2 \end{bmatrix}" />

<img src="https://github.com/DorianZi/algorithm_explained/raw/master/res/pic_3.png">

再回到最上面的图,如果继续不断地对空间施加矩阵A的线性变换(<img src="https://latex.codecogs.com/gif.latex?A^{n}" title="A^{n}" />), 那么特征向量所在方向的向量（<font color=#008000>绿色</font>和<font color=#0000FF>蓝色</font>）会幂级拉伸，非特征向量所以在方向的向量（<font color=#8B0000>褐色</font>）会越来越<font size=5>接近</font>特征向量方向。特殊情况，当<img src="https://latex.codecogs.com/gif.latex?\lambda=1" title="\lambda=1" />时，系统会<font size=5>稳定</font>在特征向量方向。
<img src="https://github.com/DorianZi/algorithm_explained/raw/master/res/pic4.png">

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

<img src="https://latex.codecogs.com/gif.latex?P" title="P" />和<img src="https://latex.codecogs.com/gif.latex?P^_{T}" title="P^_{T}" />为正交矩阵，只有旋转效果,且它们互为反向旋转；<img src="https://latex.codecogs.com/gif.latex?\Lambda" title="\Lambda" />为对角矩阵，只有拉伸效果。所以改变换为:

旋转 -> 拉伸 -> 转回来 



# 参考
https://www.bilibili.com/video/av6540378/
