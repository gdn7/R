# 预测、拟合优度和模型问题
预测（prediction）就是给定解释变量$x$的某个值，对未知的被解释变量$y$的值的预报。$y$的未知值可能处于的范围称为预测区间（prediction interval）。考虑$y$的样本值与其预测值之间相关性，给出一个拟合优度的度量，称为$R^2$。对样本中的每一个观测，预测值与实际值之间的差称为残差（residual）。基于残差构建的诊断测度用来检查回归分析中所用函数形式的正确性，并给出模型假设正确性的线索。

## 最小二乘预测
给定SR-SR6，对某个$x_0$，我们要预测相应的$y_0$。假定$x_0$和$y_0$具有与模型相同的关系，即
$$y_0 = \beta_1 + \beta_2 x_0 + e_0$$
其中，$e_0$为随机误差。假定$E(y_0)=\beta_1+beta_2x_0$，$E(e_0)=0$，$\mathrm{var}(e_0)=\sigma^2$，$\mathrm{cov}(e_0,e_i)=0,i=1,2,\ldots,N$。由拟合回归线可得到$y_0$的最小二乘预测：
$$\hat{y}_0=b_1+b_2 x_0$$
因为$b_i$随机，因此$\hat{y}_0$也是随机变量，定义预测误差为
$$f=y_0-\hat{y}_0=(\beta_1+\beta_2 x_0+e_0)-(b_1+b_2 x_0)$$
我们期望预测误差比较小。容易发现，$E(f)=0$，意味着$\hat{y}_0$是$y_0$的无偏估计。而且，可以证明，当SR1-SR5成立时，$\hat{y}_0$是$y_0$的最佳线性无偏预测（BLUP）。预测误差的方差为：
$$\mathrm{var}(f)=\sigma^2\left[1+\frac1N+\frac{(x_0-\bar{x})^2}{\sum(x_i-\bar{x})^2}\right]$$
由上式可以考察影响预测误差方差的因素，有些因素与前面的估计模型类似，一个新的因子是$(x_0-\bar{x})^2$，度量$x_0$的离差，这意味着我们在具有较多样本信息的区域能作出更好的预测。实践中，我们用$\hat{\sigma}^2$代替$\sigma^2$，得到估计方差：
$$\widehat{\mathrm{var}(f)}=\hat{\sigma}^2\left[1+\frac1N+\frac{(x_0-\bar{x})^2}{\sum(x_i-\bar{x})^2}\right]$$
取平方根，得到预测标准误（standard error of the forecast）：
$$\mathrm{se}(f)=\sqrt{\widehat{\mathrm{var}(f)}}$$
从而，预测区间（prediction interval）为：
$$\hat{y}_0\pm t_c\mathrm{se}(f)$$