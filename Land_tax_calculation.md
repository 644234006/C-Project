# โปรแกรมคำนวณภาษีที่ดิน

การเขียนโปรแกรมในส่วนของการรับส่งข้อมูลต่างๆ
```
#include<stdio.h>
int y,*stamp;
float sell;
struct birthday{
int day;
int month;
int year;
}D[2];
line()
{ int i,j;
for(i=1;i<=30;i++)
{
printf("*");
}
printf("\n");
}
input()
{ float real;
line();
printf("input sales price
:");
scanf("%f",&sell);
line();
printf("appraisal price :");
scanf("%f",&real);
return(real);
}
```
```
day(){
line();
printf("The first day of
ownership\n");
printf("input day:");
scanf("%d",&D[1].day);
printf("input month:");
scanf("%d",&D[1].month);
protect(D[1].day,D[1].month);
printf("input year[B.E.]:");
scanf("%d",&D[1].year);
line();
printf("The last day of
ownership\n");
printf("input day:");
scanf("%d",&D[2].day);
printf("input month:");
scanf("%d",&D[2].month);
protect(D[2].day,D[2].month);
printf("input year[B.E.]:");
scanf("%d",&D[2].year);
y = D[2].year - D[1].year;
if(y>=0)
y=y+1;
if(y<0){
printf("year eror");
printf("do again");
getch(!kbhit());
Menu();
}
}
```
การเขียนโปรแกรมในส่วน การป้องกันไม่รับค่าที่ผิดมา
```
protect(int day,int month){
if(month <= 0 || month >12){
	line();
	printf("no,month %dth\n",month);
	printf(">>do again<<\n");
	getch(!kbhit());
	Menu();
}
if(day <= 0){
	line();
	printf("no date %d\n",day);
	printf(">>do again<<\n");		getch(!kbhit());
	Menu();
}
if(month == 1,3,5,7,8,10,12){
	if(day > 31){
		line();
            printf("This month has no date %d.\n",day);
	printf(">>do again<<\n");
	getch(!kbhit());
	Menu();
	}
}
if(month == 2){
     if(day > 29){
	   line();
               printf("This month has no date %d.\n",day);
               printf(">>do again<<\n");getch(!kbhit());
	    Menu();
     }
}
if(month == 4,6,9,11){
	if(day > 30){
		line();
		printf("This month has no date %d.\n",day);
		printf(">>do again<<\n");
		getch(!kbhit());
		Menu();
      }
   }	
}
```
การเขียนโปรแกรมในส่วน ของการคำนวณภาษีอากรแสตมป์
```
duty(float money){
	int sum=200;
	stamp = &sum ;
	*stamp = 0.5+money/sum;
}
```
การเขียนโปรแกรมในส่วน ของการคำนวณ ค่าใช้จ่ายตามพระราชกฤษฎีกา (ฉบับที่ 165)
โดย ค่าใช้จ่ายเป็นการเหมาตามจำนวนปีที่ถือครอง
```
texyear(float money)
{  float sum=0;
	if(y==1){
		sum = money/100*92;
	}
	if(y==2){
		sum = money/100*84;
	}
	if(y==3){
		sum = money/100*77;
	}
	if(y==4){
		sum = money/100*71;
	}
	if(y==5){
		sum = money/100*65;
	}
	if(y==6){
		sum = money/100*60;
	}	
	if(y==7){
		sum = money/100*55;
	}
	if(y>=8){
		sum = money/100*50;
	}		
	return(sum);
}

```
เขียนโปรแกรมในส่วน การคำนวณภาษีเงินได้บุคคลธรรมดาหัก 
ณ ที่จ่ายจากการขายอสังหาริมทรัพย์ได้มาโดยทางอื่น ที่มิใช่มรดก  
```
Inherited(float mon)
{  	float tex,ans,sum,stam;
	tex = texyear(mon);
	ans = mon-tex;
	ans = ans/y;
	if(ans<=150000){
		sum = ans/100*5;
	}	
	else if(ans>=150001){
		sum = ans/100*5;
	}
	else if(ans>=300001){
		sum = ans/100*10;
	}
	else if(ans>=500001){
		sum = ans/100*15;
	}
	else if(ans>=750001){
		sum = ans/100*20;
	}
	else if(ans>=1000001){
		sum = ans/100*25;
	}
	else if(ans>=2000001){
		sum = ans/100*30;
	}
	else if(ans>=5000001){
		sum = ans/100*35;
	}
	sum = sum*y;
	ans = ans/100*20;
	if(sum>ans){
		sum = ans;
	}
	 duty(mon);
	 stam= *stamp;
	sum = sum+stam;
	printf("Total to be paid = %.2f THB\n",sum);
}
```
เขียนโปรแกรมในส่วน การคำนวณภาษีเงินได้บุคคลธรรมดาหัก
ณ ที่จ่ายจากการขายอสังหาริมทรัพย์ อันเป็นมรดก
```
Heritage(float mon)
{  	float ans,sum,stam;
 	float exempt;
	printf("input exempt income :");
	scanf("%f",&exempt);
	if(exempt>=200000){
		exempt = 200000;
	}
	ans = mon-exempt;
	ans = ans/2;
	ans = ans/y;
	if(ans<=150000){
		sum = ans/100*5;
	}	
	else if(ans>=150001){
		sum = ans/100*5;
	}
	else if(ans>=300001){
		sum = ans/100*10;
	}
	else if(ans>=500001){
		sum = ans/100*15;
	}
	else if(ans>=750001){
		sum = ans/100*20;
	}
	else if(ans>=1000001){
		sum = ans/100*25;
	}
	else if(ans>=2000001){
		sum = ans/100*30;
	}
     else if(ans>=5000001){
		sum = ans/100*35
}
	sum = sum*y;
	ans = ans/100*20;
	if(sum>ans){
		sum = ans;
}
	 duty(mon);
	stam= *stamp;
	sum = sum+stam;
printf("Total to be paid = %.2f THB\n",sum);
}
```
การเขียนโปรแกรมในส่วนของ main และ การเลือกใช้งาน
```
Menu(){
	int select,year;
	float money,sum;
	system("cls");
	printf("*** Menu ***\n");
	printf("1.Not Inherited\n");
	printf("2.Heritage\n");
	printf("3.Withholding corporate income from the sale of real estate \n");
	printf("4.Business Tax on Real Estate Sales \n");
	printf("5.stamp duty \n");
	printf("select >>");
	scanf("%d",&select);
	switch(select)
   	{
    case 1:	
        	printf(">>> Not Inherited <<<\n");
        	day();
        	money = input();
        	line();
        	Inherited(money);
        	line();
	break;
    case 2:
	printf(">>> Heritage <<<\n");
	day();
	money = input();
	line();
	Heritage(money);
	line();
	break; 
     case 3:
	printf(">>>Withholding corporate income from the sale of real estate <<<\n");
	line();
	money = input(); 
	if(sell<=money){
	         sum = money/100*1;
	else if(sell>money){
	      sum = sell/100*1;
	};
	printf("Total to be paid = %.2f THB",sum);
	line();
	break;
case 4:
      printf(">>Business Tax on Real Estate Sales<<\n");
	line();
	money = input();
	line();
	if(sell<=money){
	           sum = money/100*3;
	           sum =sum + sum/100*10;
	}	
	else if(sell>money){
		sum = sell/100*3;
		sum =sum + sum/100*10;
	}
printf("Total to be paid = %.2f THB\n",sum); 
			line();
			break;
case 5:
	money = input();
	printf(">> stamp duty <<\n");
	duty(money);
	line();
	printf("Total to be paid = %d THB\n",*stamp);
	line();
	break;
    }
}
main() 
{ char con;
do{     Menu();	
          printf("Enter to Cancel \n");
         con = tolower(getche());
}while(con != '\r');	
}

```
