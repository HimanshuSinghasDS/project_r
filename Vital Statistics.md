# STDR & CDR(both)

```R
rm(list=ls())
Pop_A_x=c(20000,12000,50000,30000,10000)
Dea_A_y=c(600,240,1250,1050,500)
Pop_B_x=c(12000,30000,62000,15000,3000)
Dea_B_y=c(372,660,1612,525,180)
m_A=(Dea_A_y/Pop_A_x)*1000
m_A
m_B=(Dea_B_y/Pop_B_x)*1000
m_B
t_p_a=sum(Pop_A_x)
t_d_a=sum(Dea_A_y)
t_p_b=sum(Pop_B_x)
t_d_b=sum(Dea_B_y)
cdr_A=(t_d_a/t_p_a)*1000
cdr_A
cdr_B=(t_d_b/t_p_b)*1000
cdr_B
stdr_A=(sum(m_A*Pop_A_x))/t_p_a
stdr_A
stdr_B=(sum(m_B*Pop_A_x))/t_p_a
stdr_B
```

# STDR

```R
rm(list=ls())
m_a=c(20.0,1.0,1.4,2.0,3.3,7.0,15.0,40.0,120.0)
m_b=c(5.0,0.5,1.0,1.0,2.0,5.0,12.0,35.0,110.0)
P_s=c(100,200,190,180,120,100,70,30,10)
L_a = m_a*P_s
L_b = m_b*P_s
STDR_A = sum(L_a)/sum(P_s)
STDR_A
STDR_B = sum(L_b)/sum(P_s)
STDR_B
```



# LIFE TABLE

```R
#Given rabbit X,Y,Z aged 1,2,3 respectively 
rm(list=ls())
x=c(0:6)
lx<-c(100,90,80,75,60,30,0)
lx
dx<- lx[-7]-lx[-1]
dx
qx<- dx/lx[-7]
qx
#I) Probability that one won't survive to next year is given by qx 
P_none=qx[2]*qx[3]*qx[4]#Proability that none of X,Y,Z Survive to next year
P_none
P_atleastone=1-P_none; P_atleastone # Probability that atleast one survive next year

#II) 2year time 
P_s=lx[4:6]/lx[2:4]
P_s
P_all_Survive=P_s[1]*P_s[2]*P_s[3];P_all_Survive

#III) 
P_alive_onlyone=P_s[1]*(1-P_s[2])*(1-P_s[3])+P_s[2]*(1-P_s[1])*(1-P_s[3])+P_s[3]*(1-P_s[2])*(1-P_s[1])
P_alive_onlyone
#IV)
P_alldead=(1-P_s[1])*(1-P_s[2])*(1-P_s[3]);P_alldead
Lx=(lx[-7]+lx[-1])/2
Lx
Tx=c()
for(i in 1:6) {
  Tx[i]=sum(Lx[i:6])
}
Tx
e_x_not=Tx/lx[1:6]
e_x_not
Life_Table=data.frame(Age_x=x,lx,dx=c(dx,rep(NA,length(lx)-length(dx))),
                    qx=c(round(qx,2),rep(NA,length(lx)-length(qx))),
                    Lx=c(Lx,rep(NA,length(lx)-length(Lx))),
                    Tx=c(Tx,rep(NA,length(lx)-length(Tx))),
                    e_x_not=c(round(e_x_not,2),rep(NA)))
Life_Table
```



# GFR,TFR,GRR

```r
No_women=c(212619,198732,162800,145362,128109,106211,86753)
Age_sfr_p_1000=c(98.00,169.6,158.2,139.7,98.6,42.8,16.9)
a=(No_women*Age_sfr_p_1000)/1000
No_of_birth = round(a)
t_nof = sum(No_of_birth)-1
G_F_R=t_nof/(sum(No_women))*1000
G_F_R
T_F_R = 5*(sum(Age_sfr_p_1000))
T_F_R
G_R_R = (100/(100+106))*T_F_R
G_R_R
```



# GRR,TFR,GFR,SFR

```r
rm(list=ls())
number_of_women_fPx=c(16.0,16.4,15.8,15.2,14.8,15.0,14.5)
Age_SFR_per_1000=c(98,169.6,158.2,139.7,98.6,42.8,16.9)
Number_of_Birth_nBx=c(260,2244,1894,1320,916,280,145)
age_S_F_R=((Number_of_Birth_nBx)/(number_of_women_fPx))*1000
Age_S_F_R=sum((age_S_F_R)/1000)
Age_S_F_R
G_F_R =(sum(Number_of_Birth_nBx)/(sum(number_of_women_fPx)*1000))*1000
G_F_R
T_F_R=5*sum(Age_S_F_R)
T_F_R
G_R_R=46.2/100*T_F_R
G_R_R
```

