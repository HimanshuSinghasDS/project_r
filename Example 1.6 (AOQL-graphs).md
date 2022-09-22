# Example 1.6 (AOQL-graphs)

**Example 1.16** : From a lot consisting of 2,200 items, a sample of size 225 is taken. If it contains 14 or less defectives, the lot is accepted otherwise rejected. Plot the OC,ATI and AOQ curves. Also obtain the value of AOQL.

## R-Code

```r
N<- 2200;n<-225;c=14
p<-c(0.01,0.02,0.03,0.04,0.05,0.06,0.08,0.10,0.30,0.80)
lembda<-n*p
P_a=ppois(c,lembda)

plot(p[c(-9:-10)],P_a[c(-9:-10)],type = "l",main="The OC Curve of Single Sampling Plan",xlab="p",ylab="L(p)=Pa(p)")

ATI<-n+(N-n)*(1-P_a)
plot(p[-10],ATI[-10],type = "o",main="The ATI Curve",xlab="p",ylab="ATI")

AOQ<-p*P_a
plot(p[-10],AOQ[-10],type = "o" ,main = "The AOQ Curve",xlab="p",ylab="A.O.Q.")

#Computing ATI and AOQ Values
ATI_AOQ_table=data.frame(p,lembda,P_a,AOQ,ATI)
ATI_AOQ_table
```

## R-console

```r
> N<- 2200;n<-225;c=14
> p<-c(0.01,0.02,0.03,0.04,0.05,0.06,0.08,0.10,0.30,0.80)
> lembda<-n*p
> P_a=ppois(c,lembda)
> 
> plot(p[c(-9:-10)],P_a[c(-9:-10)],type = "l",main="The OC Curve of Single Sampling Plan",xlab="p",ylab="L(p)=Pa(p)")
> 
> ATI<-n+(N-n)*(1-P_a)
> plot(p[-10],ATI[-10],type = "o",main="The ATI Curve",xlab="p",ylab="ATI")
> 
> AOQ<-p*P_a
> plot(p[-10],AOQ[-10],type = "o" ,main = "The AOQ Curve",xlab="p",ylab="A.O.Q.")
> 
> #Computing ATI and AOQ Values
> ATI_AOQ_table=data.frame(p,lembda,P_a,AOQ,ATI)
> ATI_AOQ_table
      p lembda          P_a          AOQ       ATI
1  0.01   2.25 1.000000e+00 1.000000e-02  225.0000
2  0.02   4.50 9.999263e-01 1.999853e-02  225.1455
3  0.03   6.75 9.958476e-01 2.987543e-02  233.2010
4  0.04   9.00 9.585337e-01 3.834135e-02  306.8960
5  0.05  11.25 8.352442e-01 4.176221e-02  550.3927
6  0.06  13.50 6.232711e-01 3.739627e-02  969.0395
7  0.08  18.00 2.080774e-01 1.664619e-02 1789.0472
8  0.10  22.50 3.860176e-02 3.860176e-03 2123.7615
9  0.30  67.50 2.843743e-15 8.531229e-16 2200.0000
10 0.80 180.00 3.128575e-58 2.502860e-58 2200.0000
> 
```

## R-Graphics

![](C:\Users\HP\OneDrive\Desktop\gitwork\Oc%20graph.png)

![](C:\Users\HP\OneDrive\Desktop\gitwork\ATI%20curve.png)

![](C:\Users\HP\OneDrive\Desktop\gitwork\AOQ%20curve.png)
