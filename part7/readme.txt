                                                   第七章 复用类
   复用代码是Java众多引人注目的功能之一。但要想成为极具革命性的语言，仅仅能够复制代码并对之加以改变是不够的，它还必须能够做更多的事情。代码重用主要有两种方式组合和继承。
   7.1 组合语法
   组合就是将对象引用置于新的类中
   初始化对象的四种情况：1.定义对象即初始化；2.构造器初始化；3.使用时初始化，这种方式为惰性初始化；4.使用实例初始化
   7.2 继承语法
   java中有一个根基类，如果你没有指明从哪个类继承，那么默认从Object类继承，继承用extends关键字实现，通过继承子类可以获得父类中所有的属性和方法（只是有的可见，有的不可见）
package part7;

public class Detergent extends Cleanser{
    public Detergent(String str){
        System.out.println(str);
    }
    public static void main(String[] args){
        Detergent det = new Detergent("hello");
        det.apply();det.dilute();det.scrub();
        System.out.println(det);
    }
}
class Cleanser{
    private String s = "base:";
    private void append(String str){s += str;}
    public void apply(){
        append(" apply()");
    }
    public void dilute(){
        append(" dilute()");
    }
    public void scrub(){
        append(" scrub()");
    }

    @Override
    public String toString() {
        return s;
    }
    public static void main(String[] args){
        Cleanser clean = new Cleanser();
        clean.apply();clean.dilute();clean.scrub();
        System.out.println(clean);
    }

}

基类的初始化总是发生在子类的前面，如果没有调用基类的构造器，在子类构造器（无参）的开始会默认构造基类的构造器（无参），如果没有默认构造器则会出错。初始化的顺序总是先基类再子类
   7.3 代理
   java并没有提供对代理的直接支持，这是继承和组合的中庸之道。代理通常拥有相同的接口或者相同的父类比较好，这样会有一脉相承的感觉，都有相同的方法，只是实现不同，而彼此之间就行接口的交互
   7.4 结合使用组合和继承
   组合和继承往往结合使用，描述复杂的事物，来提高代码的复用率，子类可以重写父类中的方法，当然可以重写父类中的重载方法，在子类中仍然构成重载关系，在涉及到继承过程中资源清理，必须保证清理过程的准确性和可靠性
   7.5 在组合和继承之间选择
   组合和继承选择性主要在于（is-a、has-a）的问题上，并且能够用组合解决的问题，最好不要继承，这样会增加代码的复杂度
   7.6 protected关键字
   不同包中子类可以访问父类中的protected方法和域，但是域通常都要设为private，java类库中典型的protected方法是clone()方法
   7.7 向上转型
   继承最重要的方面是表现：新类是现有类的一种类型，向上转型简单理解就是父类引用可以指向子类对象，此时编译器只知道子类是父类而java虚拟机却清楚的知道子类的确切类型
   7.8 final关键字
   final数据表示常量，一旦给定初始值就不能改变（都是指栈空间中的内容，如果是引用只表示引用永远指向存在在堆中的对象，但不能保证对象内容的改变），final参数主要向匿名内部类中传递参数，空白final保留一次赋值的权利；
   final方法表示此方法不能被修改，方法修改只有在继承中实现，所以如果一个类有子类，那么其中的final方法不允许子类修改；第二个原因是效率（java运行时存在动态绑定的行为，final可以阻止这种行为），private方法隐式地被指定为final方法；
   final类不允许被继承
   7.9 初始化及类的加载
   类只有在第一次使用时才会被加载，加载过程中就会进行初始化（只是我自己对java加载的理解）
   7.10 总结
   复用类说明程序设计过程中总是先有一部分，再有另外一部分，设计过程总是由小到大，慢慢积累而成
