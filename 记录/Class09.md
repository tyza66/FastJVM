# 使用JProfiler工具分析OOM原因

1. 因为我们的代码跑起来之后一旦出现OOM不会显示为什么导致的OOM
2. 最好是能够看到代码第几行出错（内存快照分析工具，比如ecpilse集成的MAT，我们可以用JPofiler）
3. 最慢的方法是Debug一行行分析代码
4. MAT和Jprofiler的作用：分析dump内存文件，快速定位内存泄漏问题，获得堆中的数据，获得大的对象...
5. Jprofiler需要安装一个插件和一个对应的软件，使用插件之前要去设置中的工具中配置exe文件位置
6. 我们去测试，配置为-Xms1m -Xms8m -XX:+HeapDumpOnOutOfMemoryError，这样一旦异常了就会产生dump文件
7. 之后报错了之后，项目里面会出来一个文件，用Jprofiler打开这个文件，可以看见Biggest Object啥的 或者哪里出了问题（精确到行）
8. -Xms是初始化内存分配大小（默认1/64） -Xmx是设置最大分配内存（默认1/4）
9. -XX:+PrintGCDetails 打印 GC垃圾回收信息
10.  -XX:+HeapDumpOnOutOfMemoryError          OOM Dump