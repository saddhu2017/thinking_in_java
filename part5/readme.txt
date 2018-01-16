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

