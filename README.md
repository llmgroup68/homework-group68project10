![image](https://github.com/llmgroup68/homework-group68project10/assets/138642474/b53b4633-4fda-4861-a718-dda946ddfe39)# homework-group68project22
Project10: report on the application of this deduce technique in Ethereum with ECDSA

实现方式：Python

成员：李丽敏-202100460130（仅一人一组）

实验概述：

椭圆曲线数字签名算法（ECDSA）是使用椭圆曲线密码（ECC）对数字签名算法（DSA）的模拟。ECDSA于1999年成为ANSI标准，并于2000年成为IEEE和NIST标准。它在1998年既已为ISO所接受，并且包含它的其
他一些标准亦在ISO的考虑之中。与普通的离散对数问题（discrete logarithm problem DLP）和大数分解问题（integer factorization problem IFP）不同，椭圆曲线离散对数问题（elliptic curve 
discrete logarithm problem ECDLP）没有亚指数时间的解决方法。因此椭圆曲线密码的单位比特强度要高于其他公钥体制。


ECDSA原理：


ECDSA是ECC与DSA的结合，整个签名过程与DSA类似，所不一样的是签名中采取的算法为ECC，最后签名出来的值也是分为r,s。


签名过程如下：


1、选择一条椭圆曲线Ep(a,b)，和基点G；


2、选择私有密钥k（k<n，n为G的阶），利用基点G计算公开密钥K=kG；


3、产生一个随机整数r（r<n），计算点R=rG；


4、将原数据和点R的坐标值x,y作为参数，计算SHA1做为hash，即Hash=SHA1(原数据,x,y)；


5、计算s≡r - Hash * k (mod n)


6、r和s做为签名值，如果r和s其中一个为0，重新从第3步开始执行

验证过程如下：

1、接受方在收到消息(m)和签名值(r,s)后，进行以下运算

2、计算：sG+H(m)P=(x1,y1), r1≡ x1 mod p。

3、验证等式：r1 ≡ r mod p。

4、如果等式成立，接受签名，否则签名无效。


部分代码说明：


椭圆曲线的点乘计算：


![image](https://github.com/llmgroup68/homework-group68project10/assets/138642474/22c389f7-0ff1-4609-837b-604aa8c77a54)


生成签名函数，E:消息的hash值，dA:签名者的私钥，K：随机数


![image](https://github.com/llmgroup68/homework-group68project10/assets/138642474/ec8316dc-08ae-4bec-a7b4-447f179160f3)


验证签名算法,sign：签名R||S,E:消息的hash值，PA：公钥


![image](https://github.com/llmgroup68/homework-group68project10/assets/138642474/146feab3-8a80-48d8-915a-3047a728a966)


实验结果如下：

![image](https://github.com/llmgroup68/homework-group68project10/assets/138642474/a5ad071c-071f-49c5-96a9-94b549f472c6)


