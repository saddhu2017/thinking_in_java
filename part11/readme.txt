                                                第十一章 持有对象
   如果一个程序只包含固定数量的且其生命期都是已知的对象，那么这是一个非常简单的程序
   java提供了多种方法来存放任意数量的对象比如数组，它是编译器支持的类型，最有效的方式。同时java类库还提供了一套完整的容器类其中类型是Collection/List/Set/Queue/Map
   11.1 泛型和类型安全的容器
   通过泛型机制，可以保证在编译器容器中添加的对象都是泛型指定的类型或其子类，从容器中取出时依然是泛型类型，这样保证了容器中类型在运行之前就得到安全的保证
   11.2 基本概念
   容器中有两个不同的概念：1）Collection，单独元素序列；2）Map，一组成对的“键值对”对象，允许你用键来查找值
   在创建容器类时，最好使用宽泛的接口来指向具体的对象，这样即使底层实现需要改变也不会涉及到范围太广的内容
   11.3 添加一组元素
   java.util包中Arrays和Collections类中添加了很多有用的方法
   Arrays.asList(T... t)将可变参数中的元素添加到一个List对象中，该List对象底层实现为数组，不能改变此List大小
   Collections.addAll(collection,T... t)将可变参数中的元素添加到collection对象中
   11.4 容器的打印
   所有的容器都重写了Object类中的toString方法，所以可以直接通过容器类名称打印出容器中的元素
   11.5 List
   有序的Collection，有两种实现，ArrayList、LinedList（随机访问和插入删除操作的性能）
   常用方法包括：contains/remove/indexOf/subList/containsAll/retainAll/set
   11.6 迭代器
   提供了一种可以遍历集合框架中所有集合的一组操作(Iterator（next/hasNext/remove）/ListIterator(previous/hasPrevious/add/remove/nextIndex)
   11.7 LinkList
   LinkList添加了可以使其当作栈、队列或双端队列的方法
   11.8 Stack
package com.tech;

import java.util.LinkedList;

public class Stack<E> {
    private LinkedList<E> linkedList = new LinkedList<>();
    public void push(E e){
        linkedList.addFirst(e);
    }
    public E pop(){
        return linkedList.removeFirst();
    }
    public boolean isEmpty(){
        return linkedList.isEmpty();
    }
    public E peek(){
        return linkedList.getFirst();
    }
}
    11.9 Set   
    Set具有和Collection完全相同的接口，只是提供了不同的概念，主要是与继承自Collection接口的其他类进行对比
    11.10 Map
    通过键值对来存放信息，继承实现结构跟Set相同，（Set通过组合Map实现）
    package par11;

import java.util.HashMap;
import java.util.Map;
import java.util.Random;

public class Counter {
    public static void main(String[] args){
        Random random = new Random(47);
        Map<Integer,Integer> map = new HashMap();
        int num;
        for (int i = 0; i < 10000; i++) {
            num = random.nextInt(20);
            Integer count = map.get(num);
            map.put(num,count==null?1:count+1);
        }
        System.out.println(map);
    }
}
    11.11 Queue
    队列是一个典型的先进先出的容器，PriorityQueue是一个具有优先级的队列
    11.12 Collection和Iterator
    java通过Collection和迭代器两种方式来表达容器的共性，即实现了Collection就必须提供iterator方法
    11.13 Foreach和Iterable
    任何实现了Iterable接口的类都可以使用foreach进行遍历
    适配器方法的惯用法当你有一个接口，并需要另一个接口时，编写适配器就可以解决问题
    11.14 总结
    java中提供了大量持有对象的方法
    1：数组将数字和对象联系起来，并由一段连续的内存存储
    2：Collection保存单一对象，Map保存关联键值对
    3：List可扩充的“数组”
    4：Queue即栈的行为由LinkedList提供
