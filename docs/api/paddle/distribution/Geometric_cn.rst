.. _cn_api_paddle_distribution_Geometric:

Geometric
-------------------------------

.. py:class:: paddle.distribution.Geometric(probs)

在概率论和统计学中，几何分布是一种离散概率分布，由一个正形状参数参数化，用 probs 表示。在 n 次伯努利试验中，需要 k 次试验才能得到第一次成功的概率。

详细来说就是：前 k-1 次失败，第 k 次成功的概率，概率密度函数如下：

.. math::
    P(X=k) = (1-p)^{k-1}p

上面数学公式中：

    :math:`p`：表示成功的概率。

    :math:`X`：表示进行了多少次试验才获得第一次成功。

    :math:`k`：表示实验次数，是一个正整数


参数
::::::::::::

    - **probs** (float|Tensor) - 几何分布成功概率参数。数据类型为 float、Tensor。

代码示例
::::::::::::

COPY-FROM: paddle.distribution.Geometric

属性
:::::::::

mean
'''''''''
几何分布的均值。

数学公式：

.. math::
    mean = \frac{1}{p}

上面数学公式中：

    :math:`p`：试验成功的概率。

variance
'''''''''
几何分布的方差。

数学公式：

.. math::
    variance = \frac{1-p}{p^2}

上面数学公式中：

    :math:`p`：试验成功的概率。

stddev
'''''''''
几何分布的标准差。

数学公式：

.. math::
    stddev = \sqrt{variance} = \sqrt{\frac{1-p}{p^2}} = \frac{\sqrt{1-p}}{p}

上面数学公式中：

    :math:`p`：试验成功的概率。

方法
:::::::::

pmf(k)
'''''''''
几何分布的概率质量函数。

**参数**

    - **k** (int) - 几何分布的随机变量。

数学公式：

.. math::
    pmf(X=k) = (1-p)^{k-1} p, \quad k=1,2,3,\ldots

上面数学公式中：

    :math:`p`：试验成功的概率。

    :math:`k`：几何分布的随机变量。

**返回**

    - **Tensor** - value 第一次成功所需试验次数 k 的概率。

**代码示例**

COPY-FROM: paddle.distribution.Geometric.pmf

log_pmf(k)
'''''''''
几何分布的对数概率质量函数。

**参数**

    - **k** (int) - 几何分布的随机变量。

数学公式：

.. math::

    \log pmf(X = k) = \log(1-p)^k p

上面数学公式中：

    :math:`p`：试验成功的概率。

    :math:`k`：几何分布的实验次数。

**返回**

    - **Tensor** - value 第一次成功所需的试验次数 k 的概率的对数。

**代码示例**

COPY-FROM: paddle.distribution.Geometric.log_pmf

cdf(k)
'''''''''
几何分布的累积分布函数。

**参数**

    - **k** (int) - 几何分布的随机变量。

数学公式：

.. math::

    cdf(X \leq k) = 1 - (1-p)^k, \quad k=0,1,2,\ldots

上面的数学公式中：

    :math:`p`：试验成功的概率。

    :math:`k`：几何分布的随机变量。

**返回**

    - Tensor: value 随机变量 X 小于或等于某个值 x 的概率。

**代码示例**

COPY-FROM: paddle.distribution.Geometric.cdf

entropy()
'''''''''
几何分布的信息熵。

数学公式：

.. math::

    entropy() = -\left[\frac{1}{p} \log p + \frac{1-p}{p^2} \log (1-p) \right]

上面数学公式中：

    :math:`p`：试验成功的概率。

**代码示例**

COPY-FROM: paddle.distribution.Geometric.entropy

kl_divergence(other)
'''''''''
两个 Geometric 分布之间的 KL 散度。

**参数**

    - **other** (Geometric) - Geometric 的实例。

数学公式：

.. math::
        KL(P \| Q) = \frac{p}{q} \log \frac{p}{q} + \log (1-p) - \log (1-q)

上面的数学公式中：

    :math:`P`：Geometric 几何分布实例。

    :math:`Q`：Geometric 几何分布实例。

    :math:`p`：Geometric_p 分布试验成功的概率。

    :math:`q`：Geometric_q 分布试验成功的概率。

**返回**

    - Tensor: 两个几何分布之间的 KL 散度。

**代码示例**

COPY-FROM: paddle.distribution.Geometric.kl_divergence

sample(shape)
'''''''''
随机采样，生成指定维度的样本。

**参数**

    - **shape** (tuple(int)) - 采样的样本维度。

**返回**

    - **Tensor** - 预先设计好维度的样本数据。

**代码示例**

COPY-FROM: paddle.distribution.Geometric.sample

rsample(shape)
'''''''''
重参数化采样，生成指定维度的样本。

**参数**

    - **shape** (tuple(int)) - 重参数化采样的样本维度。

**返回**

    - **Tensor** - 预先设计好维度的样本数据。

**代码示例**

COPY-FROM: paddle.distribution.Geometric.rsample
