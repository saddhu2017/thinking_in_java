                                                    第五章 初始化和清理
 随着计算机革命的发展，“不安全”的编程方式已逐渐成为编程代价高昂的主因之一。初始化和清理这是涉及安全的两个问题
 5.1 用构造器确保初始化
 构造器的命名方式采用与类相同的名称的方式，虽然与编码风格不符，但是由于构造器的特殊性，这种好处还是要多余按照编码风格进行命名的。如果一个类没有默认的构造器，那么编译器会生成一个无参数的构造器，如果自定义了有参的构造器，则编译器不会生成无参构造器。
 通过构造器，java把初始化和创建绑定在一起，构造器无返回值，它实际上是在内存中分配内存，并返回这块内存的引用
 5.2 方法重载
 方法重载就是同样的名称，要做不同的事情，根据周围环境自动判断应该回馈的动作
 方法名称相同，如何区分方法的不同是方法重载需要解决的关键问题，如何区分？完全靠参数类型和参数个数来区分
 方法重载涉及到基本类型变量参数重载问题，设计自动转型和强制转型内容
 package part5;
class True{
    private int heigth;
    public True(){
        heigth = 0;
        System.out.println("无参构造");
    }
    public True(int height){
        this.heigth = height;
        System.out.println("有参构造");
    }
    public void info(){
        System.out.println("True is "+heigth+"feet tall");
    }
    public void info(String str){
        System.out.println(str + ":True is "+heigth+"feet tall");
    }
}
public class Overloading {
    public static void main(String[] args){
        for (int i = 0;i<10;i++){
            new True(i).info();
            new True(i).info("梧桐树");
        }
        new True();
    }
}
5.3 默认构造器
构造器保证初始化的正常进行
5.4 this关键字
任何一个方法的执行在运行期都会转换成静态方法形式，通过类来调用方法，如果是静态方法直接调用，如果是非静态方法则则把对象当作方法的第一个参数进行方法调用，this就是指代方法调用过程中的对象的，所以静态方法没有this
5.5 清理：终结处理和垃圾回收
垃圾回收器只能释放那些经由new分配的内存，所以对一个对象用完后总是“弃之不顾”的做法并非总是安全的。java中对象并非总是被垃圾回收
1.对象可能不被垃圾回收
2.垃圾回收并不等于“析构”
3.垃圾回收只与内存有关
finalize()方法被限制到一种特殊情况，即通过某种创建对象方式以外的方式为对象分配了存储空间
垃圾回收的两种方式-引用计数法（Python），自适应法（停止-复制、标记-清理，最大程度保证内存空间连续）（java）
-------------------------------垃圾回收作为一个重要内容，在之后过程中再探讨
5.6 成员初始化
局部变量必须初始化，否则会编译出错；成员变量，java虚拟机会帮助初始化过程（如果没有指定初始化，则由编译器初始化为0或false、null）
5.7 构造器初始化
package part5;

public class Counter {
    int i;
    {
        System.out.println(i);
        i = 10;
        System.out.println(i);
    }
    public Counter(){
        System.out.println(i);
        i = 10;
        System.out.println(i);
    }
    public static void main(String[] args){
        new Counter();
    }
}
0
10
10
10

构造器初始化之前，先执行成员变量初始化，在执行初始化块；
package part5;

public class Counter {
    static int i;
    static {
        System.out.println(i);
        i = 10;
        System.out.println(i);
    }
     public Counter(){
        System.out.println(i);
        i = 10;
        System.out.println(i);
    }
    public static void main(String[] args){
        ;

    }
}
初始化过程中先静态初始化，而且只初始化一次，然后才会执行动态初始化
5.8 数组初始化
数组就是存储相同类型变量的容器，是java本身提供的，定于方式：类型名加上一对方括号：int[]，数组本身其实是引用
数组的初始化可以使用特殊的初始化表达式或者new：int[] i = {1,2,3,4,5,}或者int[] i = new int[5];
可变参数列表，提供了比数组更加丰富的功能
package part5;

public class NewVarArgs {
    static void print(Object... obj){
        System.out.println("执行Object");
        for(Object object:obj){
            System.out.println(object);
        }
    }
    static void print(String... str){
        System.out.println("执行String");
        for (String string:str
             ) {
            System.out.println(string);
        }
    }
    public static void main(String[] args){
        print(1,2,2.1);
        print((Object[])new Integer[]{3,2,1});
        print("123","342" );
        print();
    }
}
执行Object
1
2
2.1
执行Object
3
2
1
执行String
123
342
执行String
可变参数列表重载分析还是（默认类型可以转换时方可执行），执行方法如果字面无法分辨时，总是执行最具体的类型的方法
5.9 枚举类型
enum关键字，通过enum关键字定义枚举类，所谓枚举，就是有限可列集合
5.10 总结
java通过构造器来初始化，通过垃圾回收器来清理内存，遇不到特殊情况不需要自己进行清理（特殊情况除外）
