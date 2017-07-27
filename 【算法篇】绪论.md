
# 基础概念

## 算法定义
&emsp;&emsp;算法（algorithm)是解决问题的方法。严格地说，算法是对特定问题求解步骤的一种描述，是指令的有限序列，此外算法还必须满足下列5个重要特性：  
（1）输入：一个算法有另个或多个输入。算法的输入有两种方式：一种是从外界获得数据，另一种是由算法自己产生并被处理的数据。  
（2）输出：一个算法有一个或多个输出。既然算法是为解决问题二设计的，算法实现的最终目的就是要获得问题的解。没有输出的算法是无意义的。  
（3）有穷性：一个算法必须总是（对任何合法的输入）再执行有穷步之后结束，且每一步都在有穷时间内完成。  
（4）确定性：算法终的每一条指令必须有确切的含义，不存在二义性。并且，在任何条件下，对于相同的输入只能得到相同的输出。 
（5）可行性：算法描述的操作可以通过已经实现的基本做执行有限次来实现。
![算法的基本概念](https://github.com/LonnyZhao/LonnyZhao.github.io/blob/master/img/algorithm/算法概念.png?raw=true)

## 经典例子
### 求最大公约数
&emsp;&emsp;求最大公约数最常用的算法即为欧几里得算法，也称辗转相除法。  
&emsp;&emsp;利用的性质：
- 若r是a÷b的余数，则gcd(a,b)=gcd(b,r)
- a和其倍数的最大公约数为a

**证明：**

令c=gcd(a,b) a>=b 
令r=a mod b 设a=kc,b=jc，则k,j互素，否则c不是最大公约数
r = a - mb = kc - mjc = (k-mj)c，即r也是c的倍数，且k-mj与j互素，否则与前述k,j互素矛盾，由此可知b与r的最大公约数也是c,即gcd(a,b) = gcd(b, a mod b) 得证。

*注:*  gcd(greatest common divisor,最大公约数)缩写。

**实现方式一:** 穷举法  
&emsp;&emsp; 穷举法是解决算法问题最"野蛮"的一种方法，但是有些时候也很有效，在规模不大和对效率要求不高的情况下用的较多。直接给出实现：
````
int gcd(int a, int b)
{
    int i = 0;
    
    for(i = 1; i <= b; i++)
    {
        if((a%i == 0) && (b%i == 0))
            return i;
    }
}
````
**实现方式二:** 非递归实现  
````
int gcd(int a , int b)
{
    int c = a % b；
    
    while(c)
    {
        a = b;
        b = c;
        c = a % b;
    }
    
    return b;
}
````
**实现方式三:** 递归实现

&emsp;&emsp;使用递归方式实现求最大公约数，将问题定义为求i和j的最大公约数gcd(i,j)，其中i和j是整数，且i>=j。算法的地柜表示如下：
1.若j能整除i，那么gcd(，j) = j;
2.j不能整除i, 令r=i mod j, 那么gcd(i,j) = gcd(j, r)
````
int gcd(int i, int j)
{
    int r = i % j;
    return r == 0 ? j : gcd(j, i);
}
````

# 参考资料  
1.http://blog.csdn.net/fly_yr/article/details/50764286  
2.《算法设计与分析》 清华大学出版社


