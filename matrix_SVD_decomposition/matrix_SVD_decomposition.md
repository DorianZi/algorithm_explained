SVD分解即奇异值分解， 可以从特征值分解推导而来。先理解特征值分解

# 特征值和特征向量
对矩阵A，存在特征向量<img src="https://latex.codecogs.com/gif.latex?\alpha" title="\alpha" />和特征值<img src="https://latex.codecogs.com/gif.latex?\lambda" title="\lambda" />满足：<img src="https://latex.codecogs.com/gif.latex?A\alpha=\lambda\alpha" title="A\alpha=\lambda\alpha" />

如果把矩阵A理解为线性变换，那么上式表示：可以找到向量<img src="https://latex.codecogs.com/gif.latex?\alpha" title="\alpha" />使得A只能对它进行<img src="https://latex.codecogs.com/gif.latex?\lambda" title="\lambda" />倍的拉伸。
我们找到所有的满足条件的特征向量<img src="https://latex.codecogs.com/gif.latex?\alpha_{1},\alpha_{2},...,\alpha_{n}" title="\alpha_{1},\alpha_{2},...,\alpha_{n}" />和特征值<img src="https://latex.codecogs.com/gif.latex?\lambda_{1},\lambda_{2},...,\lambda_{n}" title="\lambda_{1},\lambda_{2},...,\lambda_{n}" />，则可以用它们来描述矩阵A。
为什么可以用来描述矩阵A？需要从特征向量和特征值的意义来理解



# 矩阵对角化
将矩阵对角化为正交矩阵<img src="https://latex.codecogs.com/gif.latex?P" title="P" />和对角矩阵<img src="https://latex.codecogs.com/gif.latex?\Lambda" title="\Lambda" />的乘积：

<img src="https://latex.codecogs.com/gif.latex?A=P\Lambda&space;P^{-1}" title="A=P\Lambda P^{-1}" />

其中<img src="https://latex.codecogs.com/gif.latex?P" title="P" />为特征矩阵，<img src="https://latex.codecogs.com/gif.latex?\Lambda" title="\Lambda" />为特征值矩阵。又因为正交矩阵的逆矩阵为其转置则：

<img src="https://latex.codecogs.com/gif.latex?A=P\Lambda&space;P^{T}" title="A=P\Lambda P^{T}" />

正交对角化推导如下：

根据特征值/特征向量定义：

<img src="https://latex.codecogs.com/gif.latex?A\alpha_{1}=\lambda_{1}\alpha_{1},A\alpha_{2}=\lambda_{2}\alpha_{2},...,A\alpha_{n}=\lambda_{n}\alpha_{n}" title="A\alpha_{1}=\lambda_{1}\alpha_{1},A\alpha_{2}=\lambda_{2}\alpha_{2},...,A\alpha_{n}=\lambda_{n}\alpha_{n}" />

合并为矩阵形式：

<img src="https://latex.codecogs.com/gif.latex?A(\alpha_{1},\alpha_{2},...,\alpha_{n})&space;=&space;(\lambda_{1}\alpha_{1},\lambda_{2}\alpha_{2},...,\lambda_{n}\alpha_{n})" title="A(\alpha_{1},\alpha_{2},...,\alpha_{n}) = (\lambda_{1}\alpha_{1},\lambda_{2}\alpha_{2},...,\lambda_{n}\alpha_{n})" />

<img src="https://latex.codecogs.com/gif.latex?A(\alpha_{1},\alpha_{2},...,\alpha_{n})&space;=&space;(\alpha_{1},\alpha_{2},...,\alpha_{n})&space;\begin{bmatrix}&space;\lambda_{1}&&space;&&space;&&space;\\&space;&&space;\lambda_{2}&&space;&&space;\\&space;&&space;&&space;...&&space;\\&space;&&space;&&space;&\lambda_{n}&space;\end{bmatrix}" title="A(\alpha_{1},\alpha_{2},...,\alpha_{n}) = (\alpha_{1},\alpha_{2},...,\alpha_{n}) \begin{bmatrix} \lambda_{1}& & & \\ & \lambda_{2}& & \\ & & ...& \\ & & &\lambda_{n} \end{bmatrix}" />

<img src="https://latex.codecogs.com/gif.latex?A=(\alpha_{1},\alpha_{2},...,\alpha_{n})&space;\begin{bmatrix}&space;\lambda_{1}&&space;&&space;&&space;\\&space;&&space;\lambda_{2}&&space;&&space;\\&space;&&space;&&space;...&&space;\\&space;&&space;&&space;&\lambda_{n}&space;\end{bmatrix}&space;(\alpha_{1},\alpha_{2},...,\alpha_{n})^{-1}" title="A=(\alpha_{1},\alpha_{2},...,\alpha_{n}) \begin{bmatrix} \lambda_{1}& & & \\ & \lambda_{2}& & \\ & & ...& \\ & & &\lambda_{n} \end{bmatrix} (\alpha_{1},\alpha_{2},...,\alpha_{n})^{-1}" />

<img src="https://latex.codecogs.com/gif.latex?A=(\alpha_{1},\alpha_{2},...,\alpha_{n})&space;\begin{bmatrix}&space;\lambda_{1}&&space;&&space;&&space;\\&space;&&space;\lambda_{2}&&space;&&space;\\&space;&&space;&&space;...&&space;\\&space;&&space;&&space;&\lambda_{n}&space;\end{bmatrix}&space;(\alpha_{1},\alpha_{2},...,\alpha_{n})^{T}" title="A=(\alpha_{1},\alpha_{2},...,\alpha_{n}) \begin{bmatrix} \lambda_{1}& & & \\ & \lambda_{2}& & \\ & & ...& \\ & & &\lambda_{n} \end{bmatrix} (\alpha_{1},\alpha_{2},...,\alpha_{n})^{T}" />
