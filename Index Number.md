# Price-Index Number

```R
po=c(20,50,40,20)
qo=c(8,10,15,20)
pi=c(40,60,50,20)
qi=c(6,5,15,25)
poqo=po*qo
poqi=po*qi
piqo=pi*qo
piqi=pi*qi
cal_table=data.frame(commodities=c('A','B','C','D'),po,qo,pi,qi,poqo,poqi,piqo,p
iqi);cal_table
P_la=(sum(piqo)/sum(poqo))*100;P_la
P_pa=(sum(piqi)/sum(poqi))*100;P_pa
P_me=((sum(piqo)+sum(piqi))/(sum(poqo)+sum(poqi)))*100;P_me
P_f=sqrt(P_la*P_pa);P_f
if(P_me>P_f){
paste0("Marshall-edgeworth index number is a good approximation to Fishers
ideal index number")
}else
{
paste0("Fisher index number is a good approximation to Marshall-Edgeworth
index number")
}
```

# Price and Quantity Index Number

```R
rm(list=ls())
po=c(5.00,7.75,9.63,12.50)
qo=c(5,6,4,9)
p1=c(6.50,8.80,7.75,12.75)
q1=c(7,10,6,9)
p1qo=p1*qo
poqo=po*qo
p1q1=p1*q1
poq1=po*q1
p_la=(sum(p1qo)/sum(poqo))*100;p_la
q_la=(sum(poq1)/sum(poqo))*100;q_la
p_pa=(sum(p1q1)/sum(poq1))*100;p_pa
q_pa=(sum(p1q1)/sum(p1qo))*100;q_pa
p_me=(1/2)*(p_la+p_pa);p_me
q_me=(1/2)*(q_la+q_pa);q_me
p_f=(p_la*p_pa)^(1/2);p_f
q_f=(q_la*q_pa)^(1/2);q_f
p_io_f=(sum(poq1)/sum(p1q1)*sum(poqo)/sum(p1qo))^(1/2)
TRT=(p_f)/100*p_io_f;TRT
if(round(TRT)==1)
{
paste0("Fisher's index satisfies Time Reversal Test")
}else
{
paste0("Fisher's index does not satisfies Time Reversal Test")
}
V_oi=(sum(p1q1)/sum(poqo))
FRT=p_f/100*q_f/100;FRT
if(round(V_oi,4)==round(FRT,4))
{
paste0("Fisher's index satisfies Factor Reversal Test")
}else
{
paste0("Fisher's index doesn't satisfies Factor Reversal Test")
}
```

# Cost of Living Index Number

```R
rm(list=ls())
p=c(50,60,200,80,160)
q=c(75,75,240,100,200)
w=c(10,25,20,40,5)
a=c()
aw=c()
for (i in 1:5)
{a[i]=q[i]*100/p[i]
aw[i]=a[i]*w[i]
};
k=sum(aw);l=sum(w);k;l;
x=data.frame(p,q,w,a,aw)
x;
col_index=k/l;col_index;
```

# Consumer Price Index Number

```R
base_inc=24000
current_inc=43000
I=c(410,150,343,248,285)
w=c(45,15,12,8,20)
Iw=I*w
cal_table=data.frame(Groups=c("Food","Rent","Clothing","Fuel and
light","Miscellaneous"),Group_index=I,Expenses=w,Iw);cal_table
con_price_index_no=sum(Iw)/sum(w);con_price_index_no
X=(con_price_index_no/100)*base_inc;X
Y=X-current_inc;Y
paste0("The required extra Allowance to be granted to MR X to maintain the same
standard of living as in the base year is:₹",Y)
```

