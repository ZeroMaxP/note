1.显示模块code.h

```c
	
#define bool int
#define true 1
#define false 0

#include<stdio.h>
#include<string.h>

int *array[8];// 每次转盘上要显示的font


int AA[]={0xFF,0xC0,0xB7,0x77,0x77,0xB7,0xC0,0xFF},  //A

 BB[]={0xFF,0x00,0x66,0x66,0x66,0x99,0xFF,0xFF},  //B
 
 CC[]={0xFF,0xC3,0xBD,0x7E,0x7E,0x7E,0x7E,0xFF},  //C

 DD[]={0xFF,0x00,0x7E,0x7E,0x7E,0xBD,0xC3,0xFF}, //D

 EE[]={0xFF,0x80,0xB6,0xB6,0xB6,0xB6,0xFF,0xFF}, //E

 FF[]={0xFF,0x00,0x6F,0x6F,0x6F,0x6F,0x7F,0xFF},  //F

 GG[]={0xFF,0xC3,0x99,0x3C,0x76,0x70,0x76,0xFF},  //G

 HH[]={0xFF,0x80,0xF7,0xF7,0xF7,0xF7,0x80,0xFF}, //H

 II[]={0xFF,0xFF,0x3C,0x00,0x00,0x3C,0xFF,0xFF}, //I

 JJ[]={0xFF,0xFF,0x3C,0x00,0x00,0x3C,0xFF,0xFF},  //J

 KK[]={0xFF,0x00,0xE7,0xDB,0xBD,0x7E,0xFF,0xFF},  //K

 LL[]={0xFF,0x00,0xFE,0xFE,0xFE,0xFE,0xFE,0xFF},  //L

 MM[]={0xC0,0xBF,0x3F,0x80,0x80,0x3F,0xBF,0xC0},  //M

 NN[]={0x00,0x1F,0x8F,0xC7,0xE3,0xF1,0xF8,0x00},  //N

 OO[]={0xC3,0xBD,0x7E,0x7E,0x7E,0xBD,0xC3,0xFF},  //O

 PP[]={0xFF,0x00,0x77,0x77,0x77,0x8F,0xFF,0xFF},  //P
 
 QQ[]={0xFF,0xC7,0xBB,0x7D,0x75,0xBB,0xC5,0xFE},  //Q

 RR[]={0xFF,0x00,0x67,0x63,0x69,0x6C,0x0E,0xFF},  //R

 SS[]={0xFF,0x8E,0x06,0x66,0x66,0x60,0x71,0xFF},  //S

 TT[]={0xFF,0x3F,0x3F,0x00,0x00,0x3F,0x3F,0xFF},  //T

 UU[]={0xFF,0x01,0xFD,0xFD,0xFD,0xFD,0x00,0xFF},  //U

 VV[]={0xFF,0x8F,0xF3,0xF9,0xF9,0xF3,0x8F,0xFF},  //V

 WW[]={0x1F,0xE3,0xF8,0x03,0x03,0xFC,0xE3,0x1F},  //W

 XX[]={0x3C,0x18,0xC3,0xE7,0xE7,0xC3,0x18,0x3C},  //X

 YY[]={0xFF,0x3F,0x9F,0xC0,0xC0,0x9F,0x3F,0xFF},  //Y

 ZZ[]={0xFF,0x38,0x30,0x24,0x0C,0x1C,0x3C,0xFF},  //Z

 aa[]={0xFF,0xFF,0xD9,0xD6,0xD6,0xE1,0xFE,0xFF},  //a

 bb[]={0xFF,0xFF,0xC0,0xF6,0xF6,0xF9,0xFF,0xFF},  //b

 cc[]={0xFF,0xFF,0xF1,0xEE,0xEE,0xF5,0xFF,0xFF},  //c

 dd[]={0xFF,0xFF,0xF9,0xF6,0xF6,0xC1,0xFE,0xFF},  //d

 ee[]={0xFF,0xFF,0xF1,0xEA,0xEA,0xF2,0xFF,0xFF},  //e

 ff[]={0xFF,0xFF,0xF7,0xC0,0xD7,0xFF,0xFF,0xFF},  //f

 gg[]={0xFF,0xFF,0xE6,0xDA,0xDA,0xC1,0xFF,0xFF},  //g

 hh[]={0xFF,0xFF,0xC0,0xF7,0xF7,0xF8,0xFF,0xFF},  //h

 ii[]={0xFF,0xFF,0xFB,0xD0,0xFF,0xFF,0xFF,0xFF},  //i
 
 jj[]={0xFF,0xFF,0xFD,0xFE,0xA1,0xFF,0xFF,0xFF},  //j

 kk[]={0xFF,0xFF,0xC0,0xF3,0xED,0xFE,0xFF,0xFF},  //k 
 
 ll[]={0xFF,0xFF,0xFF,0xC0,0xFF,0xFF,0xFF,0xFF},  //l

 mm[]={0xFF,0xF7,0xE0,0xEF,0xF0,0xEF,0xF0,0xFD},  //m

 nn[]={0xFF,0xF7,0xF0,0xEF,0xEF,0xF0,0xFF,0xFF},  //n

 oo[]={0xFF,0xF1,0xEE,0xEE,0xEE,0xF1,0xFF,0xFF},  //o

 pp[]={0xFF,0xEE,0xC0,0xDB,0xDB,0xE7,0xFF,0xFF},  //p

 qq[]={0xFF,0xFF,0xE7,0xDB,0xDB,0xC0,0xFD,0xFF},  //q

 rr[]={0xFF,0xF7,0xF0,0xEF,0xEF,0xF7,0xFF,0xFF},  //r

 ss[]={0xFF,0xFF,0xED,0xD6,0xDA,0xED,0xFF,0xFF},  //s

 tt[]={0xFF,0xFF,0xF7,0xC0,0xF6,0xFD,0xFF,0xFF},  //t

 uu[]={0xFF,0xFF,0xF1,0xFE,0xFE,0xF1,0xFE,0xFF},  //u

 vv[]={0xFF,0xFB,0xF1,0xFE,0xFD,0xF3,0xFF,0xFF},  //v

 ww[]={0xFF,0xFB,0xF1,0xFE,0xF9,0xFE,0xF1,0xFF},  //w

 xx[]={0xFF,0xF7,0xEE,0xF5,0xFB,0xF5,0xEE,0xFD},  //x

 yy[]={0xFF,0xFF,0xE6,0xFA,0xF6,0xE1,0xFF,0xFF},  //y

 zz[]={0xFF,0xFF,0xEE,0xEC,0xEA,0xE6,0xFF,0xFF},  //z

 n1[]={0xFF,0xFF,0xFF,0xDE,0x80,0xFE,0xFF,0xFF},  //n1

 n2[]={0xFF,0xFF,0xCE,0xBC,0xBA,0xB6,0xCE,0xFF},  //n2

 n3[]={0xFF,0xFF,0xDD,0xB6,0xB6,0xB6,0xC9,0xFF},  //n3

 n4[]={0xFF,0xFF,0xF3,0xEB,0xDB,0x80,0xFB,0xFF},  //n4

 n5[]={0xFF,0xFF,0x86,0xD6,0xD6,0xD9,0xFF,0xFF},  //n5

 n6[]={0xFF,0xFF,0xC1,0xB6,0xB6,0xD9,0xFF,0xFF},  //n6

 n7[]={0xFF,0xFF,0xBC,0xBB,0xB7,0x8F,0xFF,0xFF},  //n7

 n8[]={0xFF,0xC9,0xB6,0xB6,0xB6,0xC9,0xFF,0xFF},  //n8

 n9[]={0xFF,0xCD,0xB6,0xB6,0xB6,0xC1,0xFF,0xFF},  //n9

 n0[]={0xFF,0xC1,0xBE,0xBE,0xBE,0xC1,0xFF,0xFF},  //n0

 dt[]={0xFF,0xFF,0xFF,0xFF,0xFC,0xFC,0xFF,0xFF},/*".",0*/  //dot

 ca[]={0xFF,0xFF,0xFF,0xFF,0xF2,0xF1,0xFF,0xFF},/*",",0*/  //comma

 sn[]={0xFF,0xFF,0xFF,0xFF,0xCA,0xC9,0xFF,0xFF},/*";",0*/  //semicolon
 
 ek[]={0xFF,0xFF,0xFF,0x04,0x04,0xFF,0xFF,0xFF},/*"!",0*/  //excalmatory mark

 cn[]={0xFF,0xFF,0xFF,0xFF,0xE4,0xE4,0xFF,0xFF},/*":",0*/  //colon

 qk[]={0xFF,0xFF,0xBF,0x7F,0x72,0x6F,0x9F,0xFF},/*"?",0*/  //question mark

 ht[]={0x8F,0x07,0x03,0x81,0x81,0x03,0x07,0x8F},/*"heart,0*/

 animtate[4][16] = { {0xEF,0xEF,0xEF,0xEF,0xEF,0xEF,0xEF,0xEF,0xEF,0xEF,0xEF,0xEF,0xEF,0xEF,0xEF,0xEF}, //line

				{0xEF,0xEF,0xEF,0xDF,0xDF,0xDF,0xEF,0xEF,0xEF,0xEF,0xF7,0xF7,0xF7,0xEF,0xEF,0xEF}, //wave1

				{0xEF,0xEF,0xEF,0xDF,0xBF,0xDF,0xEF,0xEF,0xEF,0xEF,0xF7,0xFB,0xF7,0xEF,0xEF,0xEF}, //wave2

				{0xEF,0xEF,0xDF,0xBF,0x7F,0xBF,0xDF,0xEF,0xEF,0xF7,0xFB,0xFD,0xFB,0xF7,0xEF,0xEF}}, //wave3
 
null[] ={0x00,0x00,0x00,0x00,0x00,0x00,0x00,0x00,0x00};
	// (.)dt (,)ca (;)sn (!)ek (:)sn (!)ek (:)cn (?)qk (ht)ht
	// number --> n+number  //n1 n2
	// A-Za-z: AA BB aa bb

void DelayUs(int N)
{
    int x ;
    for(x=0;x<=N;x++);
}

void init(){
	int i;
	for(i=0;i<8;i++){
		array[i] = null;
	}
}

void animtatePlay(){
	int i,j,P3;
	for(i=0;i<4;i++){
		for(j=0;j<16;j++){
			P3 = animtate[i][j];
			DelayUs(170);
		}
	}for(i=3;i>=0;i--){
		for(j=0;j<16;j++){
			P3 = animtate[i][j];
			DelayUs(170);
		}
	}
}

bool isNull(int array[8]){  //判断当前数组是否为空
	int i;
	for(i=0;i<8;i++){
		if(array[i]){
			return true;
		}	
	}
	return false;
}

void show( char *color){  // red blue green cyan yellow magenta white
    int display[8][8];
	int hhh,i=0,*ary,len=0,j; 

	//把array 传到display里面
	for(i=0;i<8;i++){
		for(j=0;j<8;j++){
			display[i][j]=array[i][j];
		}
	}
	
	ary = display[0];
	for(i=0;i<8;i++){
		for(j=0;j<8;j++){
			printf("%d---%d---%d\n",display[i][j],array[i][j],i*8+j);
		}
		printf("one font over\n");
	}

	//64 是最大显示限制 如果该点没有值，该数组也没有值 那么ary结束了
	while(len<64 && isNull(display[len/8]) ){  //0-64
		if(len%8==0){
			printf("one font over\n");
		}
		len++;
		ary++;
	}
	
	i=len/8;  //i是要显示的字数
	printf("一共是%d个字\n",i);
	//P1控制红色 P2控制绿色 P3控制蓝色
	for(;i>0;i--){
		for(hhh=0;hhh<8;hhh++)
		{
			if(color=="red" ){
					P1=display[hhh];
					break;
			}else if(color=="green" ){
					P2=display[hhh];
					break;
			}
			else if(color=="blue" ){
					P3=display[hhh];
					break;
			}
			else if(color=="yellow" ){
					P2=display[hhh];
					P1=display[hhh];
					break;
			}
			else if(color=="cyan" ){
					P2=display[hhh];
					P3=display[hhh];
					break;
			}
			else if(color=="magenta" ){
					P3=display[hhh];
					P1=display[hhh];
					break;
			}else if(color=="white" ){
					P3=display[hhh];
					P1=display[hhh];
					P2=display[hhh];
					break;
			}
			DelayUs(170);
		}
	}
}

//shoutcut function  array index
char* splice(char str[],int i){   //i is the No of the string 
	static char spstr[3];
	int j=0;
	for(j=0;j<2;j++){
		spstr[j] = str[2*i+j];
	}
	return spstr;
} 

void upDateChar(char *str){
	int len=strlen(str),i,j;
	init();
	for(i=0;i<len;i+=2){
		if(str[i]==str[i+1]){	
		//1.判断0 and 1是不是一样 一样的话就是字母  alphabet
			if(str[i]<='Z' && str[i]>='A'){ 
				if(str[i]=='A'){
					array[i/2] = AA;
				}else if(str[i]=='B'){
					array[i/2] = BB;
				}else if(str[i]=='C'){
					array[i/2] = CC;
				}else if(str[i]=='D'){
					array[i/2] = DD;
				}else if(str[i]=='E'){
					array[i/2] = EE;
				}else if(str[i]=='F'){
					array[i/2] = FF;
				}else if(str[i]=='G'){
					array[i/2] = GG;
				}else if(str[i]=='H'){
					array[i/2] = HH;
				}else if(str[i]=='I'){
					array[i/2] = II;
				}else if(str[i]=='J'){
					array[i/2] = JJ;
				}else if(str[i]=='K'){
					array[i/2] = KK;
				}else if(str[i]=='L'){
					array[i/2] = LL;
				}else if(str[i]=='M'){
					array[i/2] = MM;
				}else if(str[i]=='N'){
					array[i/2] = NN;
				}else if(str[i]=='O'){
					array[i/2] = OO;
				}else if(str[i]=='P'){
					array[i/2] = PP;
				}else if(str[i]=='Q'){
					array[i/2] = QQ;
				}else if(str[i]=='R'){
					array[i/2] = RR;
				}else if(str[i]=='S'){
					array[i/2] = SS;
				}else if(str[i]=='T'){
					array[i/2] = TT;
				}else if(str[i]=='U'){
					array[i/2] = UU;
				}else if(str[i]=='V'){
					array[i/2] = VV;
				}else if(str[i]=='W'){
					array[i/2] = WW;
				}else if(str[i]=='X'){
					array[i/2] = XX;
				}else if(str[i]=='Y'){
					array[i/2] = YY;
				}else if(str[i]=='Z'){
					array[i/2] = ZZ;
				}
			}else{
				if(str[i]=='a'){
					array[i/2] = aa;
				}else if(str[i]=='b'){
					array[i/2] = bb;
				}else if(str[i]=='c'){
					array[i/2] = cc;
				}else if(str[i]=='d'){
					array[i/2] = dd;
				}else if(str[i]=='e'){
					array[i/2] = ee;
				}else if(str[i]=='f'){
					array[i/2] = ff;
				}else if(str[i]=='g'){
					array[i/2] = gg;
				}else if(str[i]=='h'){
					array[i/2] = hh;
				}else if(str[i]=='i'){
					array[i/2] = ii;
				}else if(str[i]=='j'){
					array[i/2] = jj;
				}else if(str[i]=='k'){
					array[i/2] = kk;
				}else if(str[i]=='l'){
					array[i/2] = ll;
				}else if(str[i]=='m'){
					array[i/2] = mm;
				}else if(str[i]=='n'){
					array[i/2] = nn;
				}else if(str[i]=='o'){
					array[i/2] = oo;
				}else if(str[i]=='p'){
					array[i/2] = pp;
				}else if(str[i]=='q'){
					array[i/2] = qq;
				}else if(str[i]=='r'){
					array[i/2] = rr;
				}else if(str[i]=='s'){
					array[i/2] = ss;
				}else if(str[i]=='t'){
					array[i/2] = tt;
				}else if(str[i]=='u'){
					array[i/2] = uu;
				}else if(str[i]=='v'){
					array[i/2] = vv;
				}else if(str[i]=='w'){
					array[i/2] = ww;
				}else if(str[i]=='x'){
					array[i/2] = xx;
				}else if(str[i]=='y'){
					array[i/2] = yy;
				}else if(str[i]=='z'){
					array[i/2] = zz;
				};		
			}
		}else{

			if(str[i+1]>='0' && str[i+1]<='9'){
										//number
				if(str[i+1]=='0'){
					array[i/2]=n0;
				}else if(str[i+1]=='1'){
					array[i/2]=n1;
				}else if(str[i+1]=='2'){
					array[i/2]=n2;
				}else if(str[i+1]=='3'){
					array[i/2]=n3;
				}else if(str[i+1]=='4'){
					array[i/2]=n4;
				}else if(str[i+1]=='5'){
					array[i/2]=n5;
				}else if(str[i+1]=='6'){
					array[i/2]=n6;
				}else if(str[i+1]=='7'){
					array[i/2]=n7;
				}else if(str[i+1]=='8'){
					array[i/2]=n8;
				}else if(str[i+1]=='9'){
					array[i/2]=n9;
				}
			}else{
				if(str[i]=='d'){  	// punctuation
					array[i/2]=dt;
				}else if(str[i+1]=='a'){
					array[i/2]=ca;
				}else if(str[i]=='s'){
					array[i/2]=sn;
				}else if(str[i]=='e'){
					array[i/2]=ek;
				}else if(str[i+1]=='n'){
					array[i/2]=cn;
				}else if(str[i]=='q'){
					array[i/2]=qk;
				}else if(str[i]=='h'){
					array[i/2]=ht;
				}else{   //没有默认ht
					array[i/2]=ht;	
				}
			}			
		}
	}
/*	for(i=0;i<8;i++){
		for(j=0;j<8;j++){
			printf("%d",array[i][j]);
		}
	}*/
};


```


串口输入输出头文件code.h

```c
    #include<reg52.h>
    void UART_init()
    {
        TMOD = 0x20;  	//T1工作模式2  8位自动重装
        TH1 = 0xfd;
        TL1 = 0xfd; 	//比特率9600
        TR1 = 1;		//启动T1定时器
        SM0 = 0;
        SM1 = 1; 		//串口工作方式1 10位异步
        REN = 1;		//串口允许接收
        EA  = 1;		//开总中断
        ES  = 1;		//串口中断打开
    }
    void UART() interrupt 4
    {
        if(RI)	//检测是否接收完成
        {
            RI = 0;
            while(!TI);
            TI = 0;
        }
    }

```

```c
#include <reg52.h>
char val =254;//刚开始占空比为1，电机速度为0
char pwm_t;//周期
sbit DJ = P2^7;//电机使能
sbit IN1=P2^6; //控制方向
sbit IN2=P2^5;//控制方向
sbit K1=P3^5;	
sbit K2=P3^7;
void delay(unsigned int z)//延时
{
	unsigned int x,y;
	for(x = z; x > 0; x--)
	for(y = 114; y > 0 ; y--);
}	

void timer0() interrupt 1{
	pwm_t++;//周期计时加
	if(pwm_t == 255)
		pwm_t = DJ = 0;
	if(val == pwm_t)//左电机占空比	
		DJ = 1;			 
}

void main(){
    delay(1000);
	TMOD |= 0x02;//8位自动重装模块
	TH0 = 220;
	TL0 = 220;
	TR0 = 1;//定时器0
	ET0 = 1;//定时器0中断
	EA	= 1;//开总中断
    IN1=1;
    IN2=0;  //控制电机方向
	while(1){
		  if(K1==0&&val<255){ //按K1电机减速
			delay(15);
			val++;}
	        if(K2==0&&val>0){ //按K2电机加速
			delay(15);
	        val--;}
	}
}
```