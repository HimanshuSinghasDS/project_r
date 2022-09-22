# Example 1.12 (np -chart)

![](C:\Users\HP\OneDrive\Desktop\gitwork\np-chart.png)

## R - Code

```r
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

## R - Console

```r
> rm(list=ls())
> nod = c(0,1,0,3,9,2,0,7,0,1,1,0,0,3,1,0,0,2,1,0)
> sum_nod = sum(nod);sum_nod
[1] 31
> p_bar = sum_nod/(length(nod)*10);p_bar
[1] 0.155
> q_bar = 1-p_bar;q_bar
[1] 0.845
> CL_np = 10*p_bar;CL_np
[1] 1.55
> UCL_np = CL_np + 3*sqrt(CL_np*(1-p_bar));UCL_np
[1] 4.983329
> LCL_np = max(0,CL_np - 3*sqrt(CL_np*(1-p_bar)));LCL_np
[1] 0
> 
> 
> ###### Revised np Control Chart(by eleminating 5th and 8th observation) ######
> new_pbar = (sum_nod-(9+7))/(10*18);new_pbar
[1] 0.08333333
> new_qbar = 1 - new_pbar;new_qbar
[1] 0.9166667
> new_CL_np = 10*new_pbar;new_CL_np
[1] 0.8333333
> new_UCL_np = new_CL_np + 3*sqrt(new_CL_np*new_qbar);new_UCL_np
[1] 3.455355
> new_LCL_np = max(0,new_CL_np - 3*sqrt(new_CL_np*new_qbar));new_LCL_np
[1] 0
> 
```
