                                                  第四章 控制执行流程
 就像有知觉的生物一样，程序必须在执行过程中控制他的世界，并作出选择。在java中，你要用执行控制语句来做出选择
 4.1 true和false
 条件运算符和逻辑运算符的表达式的结果
 4.2 if-else
 条件控制语句，来限制程序的执行动作
 4.3 迭代
 迭代就是循环，当条件成立时，执行目标动作，否则跳出循环，循环就是若干条件控制语句的重复
 while、do...while、for三种结构表达相同的意思
 
 package part4;

public class WhileTest {
    static boolean condition(){
        boolean result = Math.random()<0.99;
        return result;
    }
    public static void main(String[] args){
        while(condition()){
            System.out.println("条件成立");
        }
        System.out.println("推出循环");
    }

}
4.4 foreach语法
一种简洁的for循环，遍历数组或集合过程中，不能对集合操作，只能对集合中元素拷贝出来的那部分操作
4.5 return
函数或方法结束时保存现场环境并对目标环境产生的影响都是由return来控制
4.6 break和continue
控制循环的过程
4.7 臭名昭著的goto
goto语句会导致程序混乱，这是在滥用的前提条件下，合理使用标签会起到意想不到的效果
4.8 switch
根据表达式来选择执行的路径（表达式的值可以是int、String或枚举类型），而且这种路径选择具有穿透作用，要在合适的地方使用break跳出路径
4.9 总结
前四章通过java的基本语法结构，介绍了编程基本思想和面向对象的思想，基本所有语言都有这方面通性，而且思想大同小异
