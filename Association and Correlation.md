# Correlation

```R
rm(list=ls())
mean1=35.8
mean2=52.4
mean3=48.8
SD1=4.2
SD2=5.3
SD3=6.1
r12=0.6
r13=0.7
r23=0.8
EZ=mean1+mean2+mean3
EZ
VZ=(SD1)^2+(SD2)^2+(SD3)^2+2*r12*SD1*SD2+2*r23*SD2*SD3+2*r13*SD3*SD1
VZ
SD_z=sqrt(VZ);
SD_z
a=c(120,150,180,190,240)
Ep = (a-EZ)/SD_z;Ep
p = pnorm(Ep,0,1);p
class = c("120-150","150-180","180-190","120-190","240-")
area = c(p[2] - p[1],p[3]-p[2],p[4]-p[3],p[4]-p[1],1-p[5])
freq = 500*area
z=data.frame(a,Ep,p,class,area,freq)
z
r12_3 = (r12 - (r13*r23))/(sqrt((1-(r13)^2)*(1-(r23)^2)));r12_3
```

# Partial and Multiple Correlation

```R
rm(list=ls())
corr_coeff=c(0.77,0.72,0.52)
r12.3=(corr_coeff[1]-(corr_coeff[2]*corr_coeff[3]))/sqrt((1-corr_coeff[2]^2)*(1-corr_coeff[3]^2));r12.3
R1.23=sqrt((corr_coeff[1]^2+corr_coeff[2]^2-(2*corr_coeff[1]*corr_coeff[2]*corr_coeff[3]))/(1-corr_coeff[3]^2));R1.23
```

# Association

```R
rm(list=ls())
n=5000
a=2350
b=3100
ab=1600
q=(a*b)/n
q
if(ab>q){
print("positvely associated")
}else if(ab<q){
print("negatively associated")
}else{ 
print("independent")
}
A=490
AB=294
a=570
aB=380
B=aB+AB
B
N=A+a
N
q=(A*B)/N
if(AB>q){
print("positively associated")
}else if(AB<q){
print ("negatively associated")
}else{
print("independent")
}
AB=256
aB=768
Ab=48
ab=144
a=aB+ab
A=AB+Ab
N=A+a
B=AB+aB
q=(A*B)/N
if(AB>q){
print("positvely associated")
}else if(AB<q){
print("negatively associated")
}else{
print("independent")
}
```

