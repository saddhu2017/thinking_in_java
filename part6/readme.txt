                                                    第六章 访问控制权限
  访问控制（或隐藏具体实现）与“最初的实现并不恰当”有关
  面向对象需要考虑的一个基本问题是：“如何把变动的事物与不变的事物区分开来”
  6.1 包：库单元
  java包机制主要作用有两个1：防止命名冲突；2.梳理文件结构（两个关键字package和import，package用于打包，import用于提取以便现有程序的使用）
  6.2 java访问权限修饰词
  public（无论在哪都可以访问）、protected（只有通过继承你才能访问包外类，他拥有包内权限）、private（只具有类内部访问权限）和默认权限（即包访问权限，只有位于同一个包下的类才能访问）
  6.3 接口和实现
  访问权限的控制常被称为是具体实现的隐藏，接口和实现分离，类的设计者要把接口暴露给使用者，而具体怎么实现的则没必要说明，只要保证效率就ok
  6.4 类的访问权限
  public和默认（一个.java文件最多只能有一个public类，此类必须与文件名相匹配）
  6.5 总结
  无论在什么样的关系之中，设立一些为各成员所遵守的界限始终是很重要的（跟社会关系类似，所以说面向对象模式是人类和自然社会的模拟）
package part6;
import static com.tech.Print.print;

import org.jetbrains.annotations.Contract;

public class Singleton {
    private static Singleton singleton = new Singleton();
    private Singleton(){}
    @Contract(pure = true)
    public static Singleton getSingleton(){
        return singleton;
    }
    public static void main(String[] args){
        print(getSingleton());
        print(getSingleton());
    }
}
访问控制权限引出的单例类；
