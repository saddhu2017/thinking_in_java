                                               第十三章 字符串
 字符串操作是计算机程序设计中最常见的行为
 13.1 不可变String
 String对象是不可变的，任何对String进行改变的操作都是重新分配内存，把原先引用指向新内存的操作
 13.2 重载“+”和StringBuilder
 重载“+”默认使用了StringBuilder来提升效率，StringBuilder是可以改变的字符串
 13.3 无意识的递归
 如果重写方法过程中涉及到调用父类方法，则使用super关键字进行调用
 13.4 String上的操作
 length()/charAt()/getChars()/toCharArray()/equals/compareTo()/contains()/contentEquals()/
 valueOf/trim/replace/concat/substring/indexOf/endsWith/startsWith
 13.5 格式化输出
 printf()提供跟c语言中输出相同的操作
 13.6 正则表达式
 正则表达式是一种强大而灵活的文本处理工具
 1.基础
 -?可能有一个-，-?\\d+若干数字前边可能有一个-
package part13;

import java.util.Arrays;

public class StringMatch {
    public static void main(String[] args){
        System.out.println("-1234".matches("-?\\d+"));
        System.out.println("+1234".matches("(-|\\+)?\\d+"));
        String str = "Then,when you have found the shrubbery, you must";
        String[] strings = str.split("n\\W+");
        System.out.println(Arrays.toString(strings));
    }
}
 String自带的三个可以操作正则表达式的方法是：matches，split和replaceFirst/replaceAll
  2.创建正则表达式
  [abc]包含a,b,c的字符
  \s,\S,\W,\w,\d,\D
  XY表示Y跟在X后面，X|Y，X或Y（X）捕获组用\i引用第i个捕获组
 ^一行的开始,$一行的结束,\b词的边界
 3.量词
 贪婪型（得到最多匹配）、勉强型（得到最少匹配），占有型（目前只有Java中才可用）
 CharSequence从CharBuffer、String、StringBuffer、StringBuilder类之中抽出了字符序列的一般化定义
 4.Pattern和Matcher
 构建正则表达式对象，只需Pattern.compile()方法编译正则表达式，生成一个Pattern对象，调用matcher方法，生成一个Matcher对象
 Pattern对象表示编译后的正则表达式
 Pattern标记使匹配模式更加丰富
 5.split（）
 Pattern.compile(regex).split(charsequence);
 6.替换操作
 Matcher.appendReplacement(StringBuffer,Stringreplacement),appendTail(StringBuffer)
 7.reset()
 可以将现有的Matcher对象应用于一个新的字符序列
 8.正则表达式与Java I/O
 正则表达式可以动态的匹配字符串
 13.7 扫描输入
 Scanner类可以大大减轻扫描输入的工作负担
 13.8 总结
 重点是正则表达式的理解和运用
