# SAR指标计算

SAR又叫抛物线转向指标，是一种经典的判断股市转势和顶底的指标。但talib库提供的计算和文化财经的计算方式不一致，为此研究了一下SAR算法以及文化财经SAR值，总结出文化财经的计算方法

## 简要介绍

文化财经中SAR指标入下所示： STEP1:=STEP/100;MVALUE1:=MVALUE/100;SARLINE:SAR(N,STEP1,MVALUE1),CIRCLEDOT; 参数 N：周期 STEP：步长 MVALUE：极限值三个参数一般设置为（4,2,20）

假设 日线系列数据定义为s(n) n=0,1,2……

## SAR初始值

s(N).close > s(0).close 则初始为涨势：
sar(N)=min(s(0).low,s(1).low……,s(N-1).low)
S(N).close <s(0).close 则初始为跌势 ：
sar(N)=max(s(0).high,s(1).high……,s(N-1).high)

## SAR值计算


其中最主要的是Ep的确定，文化财经Ep取得是昨日k线的极值。
对于涨势:Ep(n)=s(n-1).high
对于跌势:Ep(n)=s(n-1).low
af(n)=af(n-1)+0.02 大于0.2后都取值0.2
每次转换时，取值需要特殊处理，极值为相反走势的极值，af=0

''' 原文链接：https://blog.csdn.net/weixin_43736903/article/details/103669999 '''
