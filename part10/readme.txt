                                               第十章 内部类
   可以将一个类的定义放在另一个类定义的内部，这就是内部类，内部类与组合是完全不同的概念
   10.1 创建内部类
   创建内部类的方式-把类的定义置于外围类的里面；同时可以通过外围类的方法，直接创建内部类对象;如果想从外部类的非静态方法之外的任意位置创建某个内部类的对象，必须指明这个对象的类型OuterClass.InnerClass
   10.2 链接到外部类
   内部类自动拥有对其外围类所有成员的访问权。（通过编译器在内部类对象里生成对外部类对象的引用，而外围类自动生成访问私有属性的方法供内部类使用）
   10.3 使用.this和.new
package part10;
public class OuterClass {
     class InnerClass{
        public OuterClass outer(){
            return OuterClass.this;
        }
    }
    public InnerClass inner(){
        return new InnerClass();
    }
    void f(){
        System.out.println("OuterClass.f()");
    }
}
class Other{
    public static void main(String[] args){
        OuterClass out = new OuterClass();
        OuterClass.InnerClass in = out.inner();
        in.outer().f();
    }
}
创建内部类必须依赖外部类对象的引用，如果没有外部类对象，则内部类无法创建成功
    10.4 内部类与向上转型
    通过内部类实现接口或者继承类而使用的类工厂模式，并搭配private关键字可以完全隐藏实现的细节
    10.5 在方法和作用域内的内部类
    
