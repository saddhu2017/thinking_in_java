                                                    第二章 一切都是对象
“如果我们说另一种不同的语言，那么我们就会发觉一个有些不同的世界。”                                    -----Luduing Wittgerstein(1889-1951)
2.1 用引用操纵对象
java中通过引用来操纵对象，就像c或c++的指针
2.2 必须由你创建所有对象
主要涉及对象、变量的存储方式
2.3 永远不需要销毁对象
java回收机制有关
2.4 创建新的数据类型：类
类用来定义创建对象，是具有某种特征对象的模板（对象通常有属性和方法）
2.5 方法、参数和返回值
对象具有的某种行为以及对象需要配合行动的具体资源和做完这种行为之后会有什么回馈给周围环境
2.6 构建一个java程序
命名规则即标识性，唯一指定java程序或者说java对象的唯一性
2.7 你的第一个java程序
package part2;
import java.util.Date;
public class HelloDate {
    public static void main(String[] args){
        System.out.println("Hello,it's:");
        System.out.println(new Date());
    }
}
2.8 注释和嵌入式文档
/*   */
//
/**    */ javadoc 提取注释工具
2.9 编码风格
约定俗成：类首字母大写，方法首字母小写，驼峰且名字知名见意；
2.10 总结
第一章总体说明了面向对象的思维模式，第二章就java中语言特性以及基础说明做了介绍
2.11 练习
package part2;

public class Exercise1 {
    int i;
    char ch;
    public static void main(String[] args){
        Exercise1 ex1 = new Exercise1();
        System.out.println(ex1.i);
        System.out.println(ex1.ch);
    }
}
只给出一个示例模型，其他略
