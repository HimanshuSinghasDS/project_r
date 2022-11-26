# MEAN & RANGE CHART

```R
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



# P - CHART

```R
nod = c(22,40,36,32,42,40,30,44,42,38,70,80,44,22,32,42,20,46,28,36,66,50,46,32,42,46,30,38,40,24)
fd = nod/1000
sum_nod = sum(nod)
sum_fd = sum(fd);sum_fd
n = 1000
k = 30
p_bar = sum_nod/(n*k)
UCL_p = p_bar + 3*sqrt((p_bar*(1-p_bar))/n);UCL_p
CL_p = p_bar;CL_p
LCL_p = p_bar - 3*sqrt((p_bar*(1-p_bar))/n);LCL_p


####### REVISED CONTROL LIMITS(by elementing 11th,12th,17th,21th) #######
new_cl_p = (p_bar-(70+80+20+66)/(26*n));new_cl_p
new_ucl_p = new_cl_p + 3*sqrt((new_cl_p*(1-new_cl_p)/n));new_ucl_p
new_lcl_p = new_cl_p - 3*sqrt((new_cl_p*(1-new_cl_p)/n));new_lcl_p
```



# np - CHART

```R
rm(list=ls())
nod = c(0,1,0,3,9,2,0,7,0,1,1,0,0,3,1,0,0,2,1,0)
sum_nod = sum(nod);sum_nod
p_bar = sum_nod/(length(nod)*10);p_bar
q_bar = 1-p_bar;q_bar
CL_np = 10*p_bar;CL_np
UCL_np = CL_np + 3*sqrt(CL_np*(1-p_bar));UCL_np
LCL_np = max(0,CL_np - 3*sqrt(CL_np*(1-p_bar)));LCL_np


###### Revised np Control Chart(by eleminating 5th and 8th observation) ######
new_pbar = (sum_nod-(9+7))/(10*18);new_pbar
new_qbar = 1 - new_pbar;new_qbar
new_CL_np = 10*new_pbar;new_CL_np
new_UCL_np = new_CL_np + 3*sqrt(new_CL_np*new_qbar);new_UCL_np
new_LCL_np = max(0,new_CL_np - 3*sqrt(new_CL_np*new_qbar));new_LCL_np
```



# GRAPHS(oc,aoq,ati)

```r
N<- 2200;n<-225;c=14
p<-c(0.01,0.02,0.03,0.04,0.05,0.06,0.08,0.10,0.30,0.80)
lembda<-n*p
P_a=ppois(c,lembda)

plot(p[c(-9:-10)],P_a[c(-9:-10)],type = "l",main="The OC Curve of Single Sampling Plan",xlab="p",ylab="L(p)=Pa(p)")

ATI<-n+(N-n)*(1-P_a)
plot(p[-11],ATI[-11],type = "o",main="The ATI Curve",xlab="p",ylab="ATI")
AOQ<-p*P_a
plot(p[-10],AOQ[-10],type = "o" ,main = "The AOQ Curve",xlab="p",ylab="A.O.Q.")

#Computing ATI and AOQ Values
ATI_AOQ_table=data.frame(p,lembda,P_a,AOQ,ATI)
ATI_AOQ_table
```

