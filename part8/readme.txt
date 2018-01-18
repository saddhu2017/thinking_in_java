                                                  第八章 多态
   “我曾经被问道‘求教，Babbage先生，如果你向机器中输入错误的数字，可以得到正确的答案吗？’我无法恰当地理解产生这种问题的概念上的混淆”
                                                                                                      --------Charles Babbage(1791-1871)
   在面向对象的程序设计语言中，多态是既数据抽象和继承之后的第三种基本特征。多态通过分离做什么和怎么做，从另一个角度将接口和实现分离开来
   8.1 再论向上转型
   向上转型会忘记对象类型，使得接口“缩小”
   8.2 转机
   方法调用绑定（将一个方法调用同一个方法主体关联起来叫做绑定），java中有前期绑定和后期绑定两种形式，静态的方法和私有的方法由于都是前期绑定的，所以不具有多态的特性
   8.3 构造器和多态
   基类的构造器总是在导出类的构造过程中被调用，而且按照继承层次逐渐向上链接，以使每个基类的构造器都能得到调用。复杂对象调用构造器要遵照下面的顺序：
   1.调用基类构造器；2.按声明顺序调用成员的初始化方法；3.调用导出类构造器的主体
   存在一个需要注意的地方：父类的构造器调用本类中的方法，而子类又重写了上述方法，则会发生多态事情
package part8;

public class GoundGryph extends Gryph{
    private int i = 100;
    public GoundGryph(){
        System.out.println("before GoundGryph");
        count();
        System.out.println("after GoundGryph");
    }
    public static void main(String[] args){
        new GoundGryph();
    }

    @Override
    public void count() {
        System.out.println(i);
    }
}
class Gryph{
    private int i = 10;
    public Gryph(){
        System.out.println("before Gryph");
        count();
        System.out.println("after Gryph");
    }
    public void count(){
        i++;
        System.out.println(i);
    }
}
   8.4 协变返回类型
   协变返回类型，表示导出类的被覆盖方法可以返回基类方法的返回类型的某种导出类型（导出类的被覆盖方法可以返回比基类方法更加丰富的类型）
   8.5 用继承进行设计
   is_a和is_like_a在继承结构中要注意的地方，向下转型如果不能确切的知道RTTI运行时类型，会产生ClassCastException
   8.6 总结
   为了在自己的程序设计中有效地运用多态乃至面向对象技术，必须扩展自己的编程视野，使其不仅包括个别类的成员和消息，而且还要包括类与类之间的共同特性以及它们之间的关系
