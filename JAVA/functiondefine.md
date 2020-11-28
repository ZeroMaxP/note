# 方法定义

```java
public static int getArea(int w, int h){
    return w*h;
}
修饰符 返回值类型 方法名 (形参){
    	方法内容
        return ;
}
```

## 注意事项

1. 方法不能嵌套
2. 方法名错误
3. 参数列表错误
4. return 下不能加代码
5. 返回值类型和return 匹配
6. 方法不重复定义
7. void 不能加在println()里面

# 方法重载

```java
public static int getSum(int a,int b){}
public static int getSun(int a,int b,int c){}
public static double getSum(double a,double b){}
```

## 注意事项

1. 参数列表不同
2. 重载嗯变量名无关
3. 和返回值类型无关
4. 和修饰符无关

# 随机点名器demo

```java
import java.util.Random;
public class CallName{
	public static void main(String[] args){
		String[] names=new String[8];
		addStudent(names);
		printStudentName(names);
		System.out.println(randomStudentName(names));
	}    
	public static String randomStudentName(String[] names){
		Random ran =new Random();
		int index =ran.nextInt(names.length);
		return names[index];
	 }
	public static void printStudentName(String[] names){
		for(int i=0;i<names.length ;i++){
			System.out.println(names[i]);    
		}
	}
	public static void addStudent(String[] names){
		names[0]="张三";
		names[1]="李四";
		names[2]="发森";
		names[3]="共等死";
		names[4]="挂而过";
		names[5]="光僧我";
		names[6]="张沃尔沃";
		names[7]="张个人";
	}
}
```

# 商场库存dmeo

```java
import java.util.Scanner;
public class Shopp{
	public static void main(String[] args){
		String[] brand={"MacBookAir","ThinkpadT450"};
		double[] size={13.3,15.6};
		double[] price={9998.4,6789.5};
		int count[]={0,0};
		while(true){
			int choose=chooseFunction();
			switch(choose){
				case 1:
					printStore(brand,size,price,count);
					break;
				case 2:
					update(count,brand);
					break;
				case 3:
				return;
			}
		}
	}
	public static void update(int[] count,String[] brand){
		Scanner sc=new Scanner(System.in);
		for(int i=0;i<brand.length;i++){
			System.out.println("请输入"+brand[i]+"的库存");
			int newCount=sc.nextInt();
			count[i]=newCount;
		}
	}
	public static int chooseFunction(){
		System.out.println("-----------库存清单----------");
		System.out.println("1.查看库存清单");
		System.out.println("2.修改库存数量");
		System.out.println("3.退出");
		Scanner sc=new Scanner(System.in);
		int choose=sc.nextInt();
		return choose;
	}
	public static void printStore(String[] brand ,double[] size,double[] price,int[] count){
		System.out.println("--------商场库存清单--------");
		System.out.println("品牌型号      尺寸      价格      库存数");
		int totalcount=0;
		double totalmoney=0;
		for(int i=0;i<brand.length;i++){
			System.out.println(brand[i] + "    " + size[i] + "      " + price[i] + "    " + count[i]);
			totalcount+=count[i];
			totalmoney+=count[i]*price[i];
		}
		System.out.println("商场总库存数"+totalcount);
		System.out.println("商场总金额数"+totalmoney);
	}
}
```



