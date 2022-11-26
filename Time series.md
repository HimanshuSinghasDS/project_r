# 3 - year moving averages

```R
year=c(1992,1993,1994,1995,1996,1997,1998,1999);
trend_year=c(1993,1994,1995,1996,1997,1998);
production=c(1542,1447,1552,2102,2612,3195,3537,3567);
mov=c()
for (i in 1:6) {
    mov[i]=production[i]+production[i+1]+production[i+2];
};mov;
movavg=mov/3;
movavg;
plot(year,production,"o",lty=1,pch=2,xlab="years",ylab="production and moving average");
lines(trend_year,movavg,"o",lty=2,pch=1);
```



# 5 - year moving averages

```R
yr=c(1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20,21,22,23,24,25,26,27,28,29,30);
yr2=c(3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20,21,22,23,24,25,26,27,28);
yr3=c(4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20,21,22,23,24,25,26,27);
v1=c(220,208,156,210,218,240,230,220,228,244,260,254,244,236,260,280,270,260,254,270,292,284,276,270,290,310,300,296,286,312);
av5=c();
av7=c()
for (i in 1:26) {
    av5[i]=(v1[i]+v1[i+1]+v1[i+2]+v1[i+3]+v1[i+4])/5;

};
for (i in 1:24) {
    av7[i]=(v1[i]+v1[i+1]+v1[i+2]+v1[i+3]+v1[i+4]+v1[i+5]+v1[i+6])/7;
};
av5;
av7;
plot(yr,v1,"o",lty=1,xlab="year",ylab="annual figures");
lines(yr2,av5,"o",lty=5,col="blue");
lines(yr3,av7,"o",lty=3,col="red");
```

