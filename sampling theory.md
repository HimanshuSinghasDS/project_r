# SIMPLE RANDOM SAMPLING

```R
####### SRS ##########
Y = c(1,2,3,4,5,6)
Y_sq = Y^2
Y_mean = mean(Y);Y_mean
mean_square = (sum(Y_sq) - (length(Y) * (Y_mean^2)))/(length(Y)-1);mean_square
var = ((length(Y)-1) / length(Y))*mean_square;var

####### SRS (without replacement nC2 = 15)##########
sum_mn=0;
sum_sq_d=0;
for(i in 1:5){
	for(j in i:6){
if(i != j)
{
		x=c(i,j)
print(x)
mn=(i+j)/2
print(mn)
d=(mn-Y_mean)
sq_d=d*d
print(sq_d)
sum_sq_d=sq_d+sum_sq_d
sum_mn=mn+sum_mn}
j=j+1}
i=i+1}
sum_mn
sum_sq_d
var_y.bar.wor=(sum_sq_d)/15
var_y.bar.wor


########################################
var_y.bar.wr= var/2;var_y.bar.wr
if (var_y.bar.wor>var_y.bar.wr){
	print("Variance of Y bar in SRSWOR will always greater than the variance of SRSWR")
}else{
	print("Variance of Y bar in SRSWR will always greater than the variance of SRSWOR")
}
```



# STRATIFIED SAMPLING

```R
####################part1########################
rm(list=ls())
farm_data = data.frame(
	stratum_no = c(1:7),
	farm_size_under = c(40,80,120,160,200,240,500),
	no_of_farm = c(394,461,391,334,169,113,148),
	avg_under_wheat_per_farm = c(5.4,16.3,24.3,34.5,42.1,50.1,63.8),
	sd_under_wheat_per_farm = c(8.3,13.3,15.1,19.8,24.5,26,35.2)
)
print(farm_data)
no_of_farm_N = c(394,461,391,334,169,113,148);no_of_farm_N
avg_under_wheat_per_farm_Y = c(5.4,16.3,24.3,34.5,42.1,50.1,63.8);avg_under_wheat_per_farm_Y
Y_bar = (sum(no_of_farm_N*avg_under_wheat_per_farm_Y))/sum(no_of_farm_N); Y_bar
N = sum(no_of_farm_N);N
N_Y = sum(no_of_farm_N * avg_under_wheat_per_farm_Y);N_Y
Y_square = avg_under_wheat_per_farm_Y * avg_under_wheat_per_farm_Y
N_Y_square = sum(Y_square * no_of_farm_N);N_Y_square
sd_under_wheat_per_farm_S = c(8.3,13.3,15.1,19.8,24.5,26,35.2)
S_square = sd_under_wheat_per_farm_S * sd_under_wheat_per_farm_S
N_S = sum(no_of_farm_N * sd_under_wheat_per_farm_S);N_S
N_S_square = sum(S_square * no_of_farm_N);N_S_square
Nminius1_S_square = sum((no_of_farm_N - 1) * S_square);Nminius1_S_square


Sd_square = (Nminius1_S_square + N_Y_square - (N*(Y_bar ^ 2)))/(N - 1);Sd_square
n = 150
Var_Y_bar = ((N-n)/(N*n)) * Sd_square;Var_Y_bar 
Total_estimated_area_y_cap = (N ^ 2) * Var_Y_bar;Total_estimated_area_y_cap 

#########################part2####################

################the number of farms in each stratum Ni####################

pa_ni = n / N; pa_ni 
noa_ni = n/ N_S; noa_ni 
stratum = c(1:7)
Ni = no_of_farm_N
Ni_si = no_of_farm_N * sd_under_wheat_per_farm_S
pani_Ni = 0.075 * Ni
noani_Ni_si = 0.0044 * Ni_si
c_for_sample = data.frame(stratum,Ni,Ni_si,pani_Ni,noani_Ni_si);c_for_sample
pa_var_ycap = ((N-n)/n) * N_S_square;pa_var_ycap
noa_var_ycap = (((N_S)^2)/n) - N_S_square;noa_var_ycap
###############now Variance of y in propotional allocation ##########
var_ybar_pa = pa_var_ycap / (N^2);var_ybar_pa

###############now Variance of y in neyman optimization allocation ##########
var_ybar_noa = noa_var_ycap / (N^2);var_ybar_noa

#########better efficency problem ##########

#due to propational allocation#
eff_pa = (Var_Y_bar - var_ybar_pa)/var_ybar_pa;eff_pa

#due to neyaman optimum allocation
eff_noa = (Var_Y_bar - var_ybar_noa)/var_ybar_noa;eff_noa

max_eff = max(eff_pa,eff_noa);max_eff
```



# SYSTEMATIC SAMPLING

```R
rm(list=ls())
n=4
k=10
N=40
X_1=c(0,1,1,2,5,4,7,7,8,6)
X_2=c(6,8,9,10,13,12,15,16,16,17)
X_3=c(18,19,20,20,24,23,25,28,29,27)
X_4=c(26,30,31,31,33,32,35,37,38,38)
X_1_sq= X_1*X_1
X_2_sq= X_2*X_2
X_3_sq= X_3*X_3
X_4_sq= X_4*X_4
X_1_sq
X_1_sq
X_2_sq
X_3_sq
X_4_sq
sum_of_rows_colm_sq=sum(X_1_sq)+sum(X_2_sq)+sum(X_3_sq)+sum(X_4_sq)
Correcn_factor=(sum(X_1)+sum(X_2)+sum(X_3)+sum(X_4))^2/N 
Correcn_factor
Total_SS=sum_of_rows_colm_sq-Correcn_factor
Total_SS
Btbn_Strata_SS=(((sum(X_1))^2+(sum(X_2))^2+(sum(X_3))^2+(sum(X_4))^2)/10)-Correcn_factor
Btbn_Strata_SS
within_strata_ss = Total_SS - Btbn_Strata_SS
within_strata_ss
S_wst_sq = (within_strata_ss)/((k-1)*n)
S_wst_sq
S_sq = Total_SS / (N-1)
S_sq
n_y = X_1+X_2+X_3+X_4
N_y_sq = sum(n_y*n_y)
N_y_sq
y_bar_dot_dot = sum(sum(X_1)+sum(X_2)+sum(X_3)+sum(X_4))/(n*k)
y_bar_dot_dot
Var_ybar_sys = (N_y_sq-(n^2*10*(y_bar_dot_dot)^2))/(n^2*k)
Var_ybar_sys
var_ybar_st = ((1/n)-(1/N)) * S_wst_sq  ##within the strata##
var_ybar_st
var_ybar_n_r = ((1/n)-(1/N))* S_sq ##among the strata##
var_ybar_n_r
```

