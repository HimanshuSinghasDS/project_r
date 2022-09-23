# Example 1.11 (p-chart)

![](C:\Users\HP\AppData\Roaming\marktext\images\3d6f3c4e7e851f5972b04111e5642c2657282c96.png)

## R-code

```r
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

## R-console

```r
> nod = c(22,40,36,32,42,40,30,44,42,38,70,80,44,22,32,42,20,46,28,36,66,50,46,32,42,46,30,38,40,24)
> fd = nod/1000
> sum_nod = sum(nod)
> sum_fd = sum(fd);sum_fd
[1] 1.2
> n = 1000
> k = 30
> p_bar = sum_nod/(n*k)
> UCL_p = p_bar + 3*sqrt((p_bar*(1-p_bar))/n);UCL_p
[1] 0.05859032
> CL_p = p_bar;CL_p
[1] 0.04
> LCL_p = p_bar - 3*sqrt((p_bar*(1-p_bar))/n);LCL_p
[1] 0.02140968
> 
> 
> ####### REVISED CONTROL LIMITS(by elementing 11th,12th,17th,21th) #######
> new_cl_p = (p_bar-(70+80+20+66)/(26*n));new_cl_p
[1] 0.03092308
> new_ucl_p = new_cl_p + 3*sqrt((new_cl_p*(1-new_cl_p)/n));new_ucl_p
[1] 0.04734567
> new_lcl_p = new_cl_p - 3*sqrt((new_cl_p*(1-new_cl_p)/n));new_lcl_p
[1] 0.01450048
> 
```
