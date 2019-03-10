# 基于SVD的图像压缩实践

在之前的介绍里，我们讲过了SVD的基本原理。一个mxn的矩阵A可以分解为三个矩阵相乘：

A可以被U和V表示，而其中的奇异值<img src="https://latex.codecogs.com/gif.latex?\lambda_{1},\lambda_{2},...,\lambda_{n}" title="\lambda_{1},\lambda_{2},...,\lambda_{n}" />分别为U的列向量和V的行向量的权重：

<img src="https://latex.codecogs.com/gif.latex?\underset{m\times&space;n}{A}=\lambda_{1}u_{1}v^{T}_{1}&plus;\lambda_{2}u_{2}v^{T}_{2}&plus;...&plus;\lambda_{n}u_{n}v^{T}_{n}" title="=\lambda_{1}u_{1}v^{T}_{1}+\lambda_{2}u_{2}v^{T}_{2}+...+\lambda_{n}u_{n}v^{T}_{n}" />

通常，前k大的奇异值就足以占了所以奇异值90%的比重，这种情况下，我们只需要选择前k个奇异值，对应地选择U的前k个列向量，还有V的前k个行向量，就可以近似表示出矩阵A:

<img src="https://latex.codecogs.com/gif.latex?\underset{m\times&space;n}{\tilde{A}}=\underset{m\times&space;k}{(u_{1},u_{2},...,u_{k})}&space;\underset{k\times&space;k}{\begin{bmatrix}&space;\lambda_{1}&&space;&&space;&&space;0&space;\\&space;&&space;\lambda_{2}&&space;&&space;\\&space;&&space;&&space;...&&space;\\&space;&&space;&&space;&&space;\lambda_{k}\end{bmatrix}}&space;\underset{k\times&space;n}{\begin{pmatrix}&space;v^{T}_{1}\\&space;v^{T}_{2}\\&space;...\\&space;v^{T}_{k}&space;\end{pmatrix}&space;}">

在图像处理中，我们把一张图片的每个像素点作为矩阵中的元素，则我们得到一个mxn的矩阵，利用SVD分解，取前k个奇异值，就能实现图像的压缩：

<img src="https://github.com/DorianZi/algorithm_explained/raw/master/res/svd_cut.png">


