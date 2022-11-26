# ANOVA

```r
rm(list=ls())
O1=c(12,10,24,29)
O2=c(30,18,12,26)
F3=c(9,9,16,4)
S3=c(30,7,21,9)
F6=c(16,10,18,18)
S6=c(18,24,12,19)
F12=c(10,4,4,5)
S12=c(17,7,16,17)
N=32;N
d=data.frame(O1,O2,F3,S3,F6,S6,F12,S12)
d
F=c(O1,O2,F3,S3,F6,S6,F12,S12);F
total_O=sum(O1,O2)
total_O
total_F3=sum(F3);total_F3
total_S3=sum(S3);total_S3

total_F6=sum(F6);total_F6

total_S6=sum(S6);total_S6
total_F12=sum(F12);total_F12
total_S12=sum(S12);total_S12
D=c(total_F3,total_S3,total_F6,total_S6,total_F12,total_S12);D
X=c(total_F3,total_F6,total_F12);X
Y=c(total_S3,total_S6,total_S12);Y
O=c(O1,O2);O
mean_O=total_O/length(O);mean(O)
mean_F3=total_F3/length(F3);mean_F3
mean_S3=total_S3/length(S3);mean_S3
mean_F6=total_F6/length(F6);mean_F6
mean_S6=total_S6/length(S6);mean_S6
mean_F12=total_F12/length(F12);mean_F12
mean_S12=total_S12/length(S12);mean_S12
G=sum(total_O,total_F3,total_S3,total_F6,total_S6,total_F12,total_S12);G
CF=(G^2)/N;CF
TSS=(sum((F^2)))-CF;TSS
tSS=((total_O^2)/length(O))+((sum(D^2))/length(F3))-CF;tSS
ESS=TSS-tSS;ESS
source_of_variation=c('Treatments','Error')
SS=c(tSS,ESS)
total_SS=sum(SS);total_SS
df=c(6,25)
total_df=sum(df);total_df
MSS=SS/df;MSS
VR=c(121.849/43.915);VR
d1=data.frame(source_of_variation,SS,df,MSS);d1
d2=sum(d1['SS']);d2
d3=sum(d1['df']);d3

avrage_effect_of_sulphur=3*(total_O)-320;avrage_effect_of_sulphur
fal_versus_spring_application=sum(X)-sum(Y);fal_versus_spring_application
contributor_to_SS=(fal_versus_spring_application^2/24);contributor_to_SS
sourc_of_variation=c('Treatments','control_vs_sulphur','fal_versus_spring_application','comparison_among_levels')
d_f=c(6,1,1,4)
S_S=c(972.3,518.0,228.2,226.1)
M_S_S=S_S/d_f;MSS
V_R=M_S_S/44.9;VR
data=data.frame(sourc_of_variation,d_f,S_S,M_S_S,V_R);data
Total_1=sum(d_f);Total_1
Total_2=sum(S_S);Total_2
Total_3=sum(M_S_S);Total_3
```



# 2 power 2



```R
T_1 = c(-6,-3,0,-1)
T_k = c(-4,7,-9,2)
T_p = c(-7,11,-9,-5)
T_kp = c(9,9,1,5)
s_t1 = sum(T_1)
s_tk = sum(T_k)
s_tp = sum(T_p)
s_kp = sum(T_kp)
G = sum(T_1,T_k,T_p,T_kp);G
Treat_tot = c(sum(T_1),sum(T_k),sum(T_p),sum(T_kp),G,0)
Treat_tot
TT_2 = Treat_tot*Treat_tot
table = data.frame(Treatment_combo=c("1","k","p","kp","Block_total","Bj_2"),
			 Block_1 = c(-6,-4,-7,9,sum(-6,-4,-7,9),(sum(-6,-4,-7,9))^2),
			 Block_2 = c(-3,7,11,9,sum(-3,7,11,9),(sum(-3,7,11,9))^2),
			 Block_3 = c(0,-9,-9,1,sum(0,-9,-9,1),(sum(0,-9,-9,1))^2),
			 Block_4 = c(-1,2,-5,5,sum(-1,2,-5,5),(sum(-1,2,-5,5))^2),
			 Treat_tot,TT_2)
table
N = 16
RSS = sum((T_1)^2,(T_k)^2,(T_p)^2,(T_kp)^2);RSS
CF = (G^2)/N;CF
TSS = RSS - CF;TSS
BSS = (sum(sum(-6,-4,-7,9)^2,sum(-3,7,11,9)^2,sum(0,-9,-9,1)^2,sum(-1,2,-5,5)^2))*0.25-(CF);BSS
Tret_SS = sum(TT_2)*0.25-(CF);Tret_SS
Error_SS = RSS - (BSS+Tret_SS);Error_SS
A = s_kp-s_tp+s_tk-s_t1
B = s_kp+s_tp-s_tk-s_t1
AB = s_kp-s_tp-s_tk+s_t1
Yates_method = data.frame(Treatment_combo=c("1","k","p","kp"),
				  Total_y_all_blocks=c(sum(T_1),sum(T_k),sum(T_p),sum(T_kp)),
				  T_3 = c((sum(T_1)+sum(T_k)),(sum(T_p)+sum(T_kp)),(sum(T_k)-sum(T_1)),(sum(T_kp)-sum(T_p))),
				  F_e_t = c(G,(s_kp-s_tp+s_tk-s_t1),(s_kp+s_tp-s_tk-s_t1),(s_kp-s_tp-s_tk+s_t1)),
				  SS = c(CF,(A^2)/16,(B^2)/16,(AB^2)/16))
Yates_method
Sov = c("Blocks","Treat","K","p","kp","error","totals")
df =c(3,3,1,1,1,9,15)
SS = c(BSS,Tret_SS,(A^2)/16,(B^2)/16,(AB^2)/16,Error_SS,TSS)
MSS = c(BSS/3,Tret_SS/3,(A^2)/16,(B^2)/16,(AB^2)/16,Error_SS/9,0)
E_cons = Error_SS/9
V_R_F = c(MSS[1]/E_cons,MSS[2]/E_cons,MSS[3]/E_cons,MSS[4]/E_cons,MSS[5]/E_cons,0,0)
Tab_5per = c(3.86,3.86,1.92,1.92,1.92,0,0)
Tab_1per =c(6.99,6.99,5.12,5.12,5.12,0,0)
Anova_tab = data.frame(Sov,df,SS,MSS,V_R_F,Tab_5per,Tab_1per)
Anova_tab
```



