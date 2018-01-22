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
