#  类加载器及双亲委派机制

##### Lombok是咋回事

1. 他会在程序运行的时候给我们动态生成get，set方法
2. 因为程序加载的时候会解析一棵树，Lombok在这个语法树上去解析
3. 只能执行引擎和类加载器加个钩子，大多数框架是在执行引擎上动

##### 类加载器

1. 作用：加载class文件 

2. new Student() 的时候 引用放在栈里面 具体的对象放在堆里面

3. 现在有一个class文件进入到JVM中，先到类加载器中进行加载初始化 这个class是反射那个class（Student.class）

4. 类是一个模板是抽象的 而对象是具体的

5. 类放到Class Loader里面会加载并初始化 而产生的这个class是用来做实例化的

6. 实例化的关键词就是new

7. 一个对象也可以获得class 只要使用getClass方法

   ```java
   Car car1 = new Car(); //实例化一个Car对象 他的名字（引用）在栈里面 具体的对象在堆里面 找的方法是使用的内存地址
   Class<? extends Car> aClass= car1.getClass();
   ```

8. 使用Class对象我们也可以使用getClassLoader()方法反向获得ClassLoader对象

![类加载器](..\图片\类加载器.png)

9. 类加载器分为：虚拟机自带的加载器，启动类（根）加载器，扩展类加载器，应用程序（系统）加载器