# 垃圾回收之引用计数法

1. 垃圾回收的作用范围只在堆中（和方法区）
2. JVM在运行GC时，在新生代，幸存区（from，to），老年区三个地方回收
3. 它并不是在三个区域统一回收，大多数时候回收都是在新生代
4. GC有两种类型：一种是轻GC（普通的GC），另一种是重GC（全局的GC）
5. 轻GC只清理新生代，偶尔处理幸存区
6. 重GC相当于全局的 包括老年区
7. 要了解jvm中的内存模型和分区~详细到每个区放什么
8. 要知道堆里面的分区有哪些：eden，from，to，老年区，说说他们的特点
9. 要了解GC的算法有哪些：标记清除法，标记整理（标记压缩），复制算法，引用计数器
10. 还要知道轻GC和重GC在什么时候发生
11. 只要是把没有用的东西干掉，就是垃圾回收
12. 引用计数法就是给每个对象分配一个计数器记录一下被引用的次数，计数器本身也会消耗内存如果一个对象没被引用过，计数器里面是0，就将会被清除
13. 这个方法太low了，用的比较少

