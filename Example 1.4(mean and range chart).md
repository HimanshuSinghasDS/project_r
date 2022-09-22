# Example 1.4(mean and range chart)

![](C:\Users\HP\OneDrive\Desktop\gitwork\xbar%20and%20r%20chart.png)

## R - Code

```r
###### Finding Mean and Range Control Chart ######

rm(list=ls())
m=c(0.8372,0.8324,0.8318,0.8344,0.8346,0.8332,0.8340,0.8344,0.8308,0.8350,0.8380,0.8322,0.8356,0.8322,0.8404,0.8372,0.8282,0.8346,0.8360,0.8374)
r=c(0.010,0.009,0.008,0.004,0.005,0.011,0.009,0.003,0.002,0.006,0.006,0.002,0.013,0.005,0.008,0.011,0.006,0.006,0.004,0.006)
a2=0.58
M=mean(m)
M
R=mean(r)
R
a=length(m)
UCL_x = M+a2*R
UCL_x
CL_x = M
CL_x
LCL_x = M-a2*R
LCL_x
m2 = ((M*20)-0.838-0.8282)/18
m2
r2 = ((R*20)-0.006-0.006)/18
r2
New_UCL_x = m2+a2*r2
New_CL_x = m2
New_LCL_x = m2-a2*r2
New_UCL_x
New_CL_x
New_LCL_x
D4=2.12
D3=0
UCL_r = D4*R
UCL_r
CL_r = R
CL_r
LCL_r = D3*R
LCL_r


#####  Tolerance limit question #########

UTL=0.840
LTL=0.820
d2 = 2.326
mu_cap = m2 
sigma_cap = r2/d2
mu_cap
sigma_cap
p = pnorm(0.82,mean=0.834077,sd=0.00291392)+pnorm(0.84,mean=0.834077,sd=0.00291392)
p
p2 = 1-p
p2
percent_defect = 100*p2
percent_defect
```

## R-Console

```r
> ###### Finding Mean and Range Control Chart ######
> 
> rm(list=ls())
> m=c(0.8372,0.8324,0.8318,0.8344,0.8346,0.8332,0.8340,0.8344,0.8308,0.8350,0.8380,0.8322,0.8356,0.8322,0.8404,0.8372,0.8282,0.8346,0.8360,0.8374)
> r=c(0.010,0.009,0.008,0.004,0.005,0.011,0.009,0.003,0.002,0.006,0.006,0.002,0.013,0.005,0.008,0.011,0.006,0.006,0.004,0.006)
> a2=0.58
> M=mean(m)
> M
[1] 0.83448
> R=mean(r)
> R
[1] 0.0067
> a=length(m)
> UCL_x = M+a2*R
> UCL_x
[1] 0.838366
> CL_x = M
> CL_x
[1] 0.83448
> LCL_x = M-a2*R
> LCL_x
[1] 0.830594
> m2 = ((M*20)-0.838-0.8282)/18
> m2
[1] 0.8346333
> r2 = ((R*20)-0.006-0.006)/18
> r2
[1] 0.006777778
> New_UCL_x = m2+a2*r2
> New_CL_x = m2
> New_LCL_x = m2-a2*r2
> New_UCL_x
[1] 0.8385644
> New_CL_x
[1] 0.8346333
> New_LCL_x
[1] 0.8307022
> D4=2.12
> D3=0
> UCL_r = D4*R
> UCL_r
[1] 0.014204
> CL_r = R
> CL_r
[1] 0.0067
> LCL_r = D3*R
> LCL_r
[1] 0
> 
> 
> #####  Tolerance limit question #########
> 
> UTL=0.840
> LTL=0.820
> d2 = 2.326
> mu_cap = m2 
> sigma_cap = r2/d2
> mu_cap
[1] 0.8346333
> sigma_cap
[1] 0.00291392
> p = pnorm(0.82,mean=0.834077,sd=0.00291392)+pnorm(0.84,mean=0.834077,sd=0.00291392)
> p
[1] 0.9789571
> p2 = 1-p
> p2
[1] 0.02104291
> percent_defect = 100*p2
> percent_defect
[1] 2.104291

```
