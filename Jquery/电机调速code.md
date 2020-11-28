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

void timer0() interrupt 1
{
	pwm_t++;//周期计时加
	if(pwm_t == 255)
		pwm_t = DJ = 0;
	if(val == pwm_t)//左电机占空比	
		DJ = 1;		
		 
}

void main()
{
    delay(1000);
	TMOD |= 0x02;//8位自动重装模块
	TH0 = 220;
	TL0 = 220;
	TR0 = 1;//定时器0
	ET0 = 1;//定时器0中断
	EA	= 1;//开总中断
	 IN1=1;
	 IN2=0;  //控制电机方向
	while(1)
	{
		
		  if(K1==0&&val<255)//按K1电机减速
            {
			delay(15);
			val++;
            }

	        if(K2==0&&val>0)//按K2电机加速
            {
			delay(15);
	        val--;
            }
	}

}
```