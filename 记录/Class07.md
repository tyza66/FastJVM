# 走近HotSpot和堆

### 三种JVM

1. 我们学的是Sun公司下的HotSpot
2. 我们用java -version的时候会显示出来虚拟机的版本
3. 还有一种是Oracle出的叫JRockit，现在其实很少见，它是世界上最快的jvm
4. 还有个是IBM的j9vm，实际用的人也很少，在一些IBM独占平台上要跑java肯定得是j9
5. 我们学习的都是HotSpot

### 堆（Heap）

1. 一个JVM只有一个堆内存

2. 堆内存的大小是可以调节的

3. 可以通过idea的启动配置或者main方法的 参数传进去

4. 调参用的就是"VM opitions"和"Program arguments"

5. 方法区也是堆

6. 类加载器读取了类文件之后，一般会把累的实例，方法，常量，变量，所有引用类型的真实对象

7. 对内存中还要细分为三个区域：新生区（伊甸园区，young、new，Eden Space），养老区（old），永久区（perm）

8. 新生区包括三个：伊甸园（Eden Space），幸存0区，幸存1区 【1和0之间会进行交换】

9. 经历了一次或者多次垃圾回收机制之后还没有被回收掉就会进去幸存区，超过一定次数之后就会进去养老区

10. 养老区满了就会触发另一种回收

11. 垃圾回收分为两种，轻量级（轻GC）和重量级（重GC，Full GC）

12. 堆中还有个永久存储区

13. 垃圾回收主要在新生区和养老区，如果需要细分的话就是伊甸园区和养老区（GC垃圾回收主要是在伊甸园区和养老区）

14. 假设内存满了就会报OOM，就是堆内存不够

15. 模拟一下让堆满

    ```java
    String a = "giao";
    while(true){
      a = a+"giao";
    }//运行半天之后就会提示一个OOM的错误 OutOfMemoryError
    ```

16. 每次都变大新生区里面这个，每次都去回收一下，直到新生区养老区都满了，报错

17. 在JDK8以后，永久存储区改了个名字叫元空间

