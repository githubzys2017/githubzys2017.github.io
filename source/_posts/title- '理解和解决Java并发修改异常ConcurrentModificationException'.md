---
title: '理解和解决Java并发修改异常ConcurrentModificationException'
---
---
<!--more-->
> 异常代码
```
import java.util.ArrayList;
import java.util.Iterator;

public class Test {

    public static void main(String[] args) {
        ArrayList<String> array = new ArrayList<String>();

        // 创建并添加元素
        array.add("hello");
        array.add("world");
        array.add("java");
        Iterator it = array.iterator();
        while (it.hasNext()) {
            String s = (String) it.next();
            if ("world".equals(s)) {
                array.add("javaee");
            }
        }
    }
}
```
##1.异常解释

ConcurrentModificationException:当方法检测到对象的并发修改，但不允许这种修改时，抛出此异常。
产生的原因：
迭代器是依赖于集合而存在的，在判断成功后，集合的中新添加了元素，而迭代器却不知道，所以就报错了，这个错叫并发修改异常。
简单描述就是：迭代器遍历元素的时候，通过集合是不能修改元素的。
如何解决呢?
A:迭代器迭代元素，迭代器修改元素
B:集合遍历元素，集合修改元素(普通for)


