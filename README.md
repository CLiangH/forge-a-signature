项目目的
=

forge a signature to pretend that you are Satoshi

代码介绍
=

互素函数
________________________________

判断两数是否互素，若互素则返回0，否则返回1.

GCD求最大公因子
_____________________

经典算法，在此不再赘述

椭圆曲线加法
_____________________

若两点同时不为0，则可计算斜率.

若两点相等，斜率为：λ = (3Xp² + a)/2Yp

若两点不相等，则斜率为：λ = (Yq - Yp)/(Xq - Xp)

计算结果点R的坐标计算公式为：

Xr = (λ² - Xp - Xq) 

Yr = (λ(Xp - Xr) - Yp)

椭圆曲线点数乘法：

循环使用加法即可

签名函数Sign（m）与验证函数Verify（r，s）
____________________________________________

![image](https://github.com/CLiangH/Picture/blob/main/forge1.png)

完全按照流程实现即可

伪造函数
______________

如果只需要签名消息的Hash值，那么任何人都可以伪造签名。

Ecdsa验证旨在验证：

$s^{-1}$(eG+rP) = (x',y')=R',r'=x' mod n == r

为了伪造，我们可以选择u,v,计算R'=(x',y')=uG+vP，之后选择r'=x' mod n，计算：

e'=r'uv' mod n

s'=r'v' mod n

伪造即可完成

__注意：__
此代码因随机数选取有几率报错，可能是椭圆曲线部分选取了错误的点，属正常现象

测试结果
=

![image](https://github.com/CLiangH/Picture/blob/main/forge2.png)

