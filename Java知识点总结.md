# Java知识点总结
## 一、50个关键字总结
* ***数据类型***

关键字|类型|字节数
:--:|:--:|:--:
byte|字节|1
short|短整型|2
int|整型|4
long|长整型|8
float|单精度浮点型|4
double|双精度浮点型|8
char|字符型|2
boolean|布尔型|1

* ***定义类、接口***
   * class:用于定义一个类
    ```
    public class ClassName{
        ...
    }
    ```
   * interface:用于定义一个接口
   ```
   public interface InterfaceName{
       ...
   }
   ```

* ***流程控制***
    * if:条件判断
    * else:条件转折
    ```
    if(条件){
        //true
    }else{
        //false
    }
    ```
    * do:与while连用，表示循环
    ```
    do{
        //true
    }while(条件);
    ```
    * while:用于循环
    ```
    while(条件){
        //true
    }
    ```
    * for:用于循环
    ```
    for(...;条件;){
        //true
    }
    ```
    * switch、case,default:一起用于条件分支流程
    ```
    switch(A){
        case 条件1:
            ...
            break;
        case 条件2:
            ...
            break;
        default:
    }
    ```
    * break:
        1. 用于switch中，跳出switch
        2. 用于循环中，跳出最近的循环体
    ```
    while(true){
        ...;
        break;
    }
    ```
    * continue:跳出本次循环
    ```
    while(true){
        ...
        continue;
        i++; //永远不执行
    }
    ```
    * return:结束函数或结束函数并返回一个值
    ```
    public static int demo(){
        ....
        return 1;
        i++;    //永远不执行
    }
    ```
    * try、catch、finally:用于异常处理
    ```
    try{
        ...
    }catch(Exception e){
        ...
    }fically{
        ...    
    }
    ```
* ***访问修饰符***

范围|本类|同包|不同包子类|不同包
:-:|:--:|:--:|:--:|:--:
public|YES|YES|YES|YES
protect|YES|YES|YES|NO
default|YES|YES|NO|NO
private|YES|NO|NO|NO

* ***其它修饰符***
    * final:
        1. 修饰类，类不可继承
        2. 修饰方法，方法不可被重写
        3. 修饰变量，值不能被改变
    * void:空类型，表示函数没有返回值
    * static:定义静态变量，方法，与类相关
    * strictfp:精确浮点数，让Java编译器及运行环境完全按浮点规范IEEE-754来执行。
    * abstract:修饰方法或类，使其变为抽象方法或抽象类，抽象类只能被继承，抽象方法必须被重写。
    * transient:用来表示一个域不是该对象串行化的一部分。
    * synchronized:用于线程，保证线程安全
    ```
    ...
    //开启两个线程
    
    //只有一个线程执行完该方法，另一线程才能执行
    public synchronized void demo(){
        ...
    }
    ```
    * volatile:volatile修饰的变量，同一个时间只有一个线程可以访问，保证线程安全。
    * native(没用过):是用作java 和其他语言（如c++）进行协作时用的也就是native 后的函数的实现不是用java写的， native的意思就是通知操作系统，这个函数你必须给我实现，因为我要使用。所以native关键字的函数都是操作系统实现的， java只能调用。
* 与动作相关    
    * package:打包，把java程序写在同一个包中
    * import:导入包名
    * throw:手动抛出异常
    * extends:继承
    * implements:实现接口
    * this:本对象
    ```
    public class Demo{
        int a;
        public Demo(int a){
            //this为Demo
            this.a = a;
        }
    }
    ```
    * super:调用父类函数或构造器
    ```
        public class Demo01 extends Demo{
        public Demo(int a){
            super(a);   //调用父类构造器
            super.test();   //调用父类方法
        }
    }
    ```
    * instanceof:判断一个类是否其子类或本身
    ```
        public void demo(){
            Demo demo = new Demo01(a);
            if(a instaceof Demo01){
                Demo01 demo01 = (Demo01)demo;
            }
        }
    ```
    * new:创建一个新的对象
* 其他
    * true:真
    * false:假
    * null:空
    * goto:跳转至代码中某个位置(不用)
    * const:修饰变量 == final修饰变量
## 二、面向对象
1. 类的定义语法(class):
    ```
    [修饰符]class 类名{
        //类体
    }
    ```
2. 对象的声明:
    ```
    类名 变量名 = new 构造器();
    ```
3. 方法的重载与重写
    1. 重载:一个类中多个同名但参数不同的方法
    2. 重写:重写父类的某一方法
4. 方法参数传递的机制:值传递
5. 形参可变的方法:最后一个形参加...
    ```
    public static void demo(double...a){
        
    }
    ```
6. 成员变量与局部变量的区别：
    1. 成员变量:类里面定义的非静态变量，作用域为整个对象，生命周期为从对象产生到销毁。
    2. 局部变量:方法或块中定义的变量，作用域在定义其的方法或块中，块或方法执行完毕后，局部变量生命周期结束。
7. 封装:利用访问控制符隐藏类的内部实现细节
    ```
    private int age;    //隐藏年龄
    private int sex;    //隐藏性别
    ```
8. 面向对象三大特点:封装，继承，多态
9. 继承语法
    ```
    public class A extends B{
        //A继承B
    }
    ```
10. 调用子类构造器时，会先调用父类构造器，最先构造的类为所有类的父类Object
11. 子类可以继承父类非private的成员
12. 子类可以向上自动转型为父类，但只能调用父类中有声明的方法。
13. static:用static修饰后的成员变量，将变为类变量，与对象无关，如：静态方法，静态变量，静态初始化块都与类相关，而与对象无关
14. 抽象类:用abstract修饰的类，只能继承，不能创建实例，必须实现所有的抽象方法
15. 接口:100%抽象类，接口中无构造器，只能由抽象方法，可定义默认方法以及静态方法(为默认方法提供工具方法),成员变量均为静态的
16. 抽象类与接口的区别:
    1. 抽象类有构造器，有具体方法，接口没有
    2. 一个类只能继承一个抽象类，却可以实现多个接口
17. 内部类
    1. 非静态内部类，可用private,protected,public修饰，非静态内部类依赖与外部类，需要先创建外部类实例，才可以创建非静态内部类，非静态内部类可访问外部类成员，外部类不可以访问非静态内部类.
    2. 静态内部类:静态内部类依赖于外部类，不依赖于外部类实例，可以直接创建静态内部类。静态内部类不可访问非静态成员。
18. 函数式接口:只含有一个抽象方法的接口(可用于Lambda表达式)
19. 对象的强引用、软引用、弱引用、虚引用
## 三、容器
***Collection:***       
1. List: 
    1. ArrayList:数组列表，连续排列，索引速度快。
    2. LinkedList:链表列表，索引速度慢，插入速度快
    3. Vector:与ArrayList类似，线程安全，速度比ArrayList略慢。
2. Set:存放不可重复的元素
    1. HashSet:不保证集合内元素的顺序，查询速度快。
    2. LinkedHashSet:HashSet的子类，保证元素的顺序，速度比HashSet慢。
    3. TreeSet:具有排序的能力，速度慢
3. 遍历集合的常用方法:  
    1.增强版for循环:
    ```
    ArrayList<Integer> demos = new ArrayList<>();
    demos.add(1);
    demos.add(2);
    demos.add(3);
    for(int i:demos){
        System.out.println(i);
    }
    ```
    2. Iterator遍历：调用iterator方法获得迭代器，遍历集合
    ```
    Iterator<Interger> iterator = demos.iterator();
    while(iterator.hasNext()){
        int i = iterator.next();
        System.out.println(i);
    }
    ```
    3. 迭代过程不可修改容器
    ```
    for(int i:demos){
        demos.remove(i);    //错误
    }
    ```
4. ***重写equal需要重写hasCode的原因***：Set集合存放元素时，首先调用equal方法判定两个对象是否相等，在计算HasCode,若两个对象的equal为true,且HasCode相同，则对象将会存放失败，因为set里不放相同的元素，因此，重写equal时应该重写hasCode,保证equal为true时，hasCode相等，equal为false时，hasCode不相等。
5. ***TreeSet的排序***：
    1. 自然排序:集合中的每个元素应该实现Comparable,并实现其中的ComPareTo,当指定对象大于比较对象时，返回正，相等返回0，小于返回负数
    ```
    A.ComPareTo(B)
    //A>B,返回正数
    //A==B,返回0
    //A<B,返回负数
    ```
    2. 定制排序，构建TreeSet时，传送一个Comparator的实现类
    ```
    TreeSet demo = new TreeSet(()->{
        ....
    }); //比较规则与Comparable相同
    ```
***Map:***
1. Map中的key与set类似，value与List类似
2. HashSet,LinkedHashSet,TreeSet与HashMap,LinkedHashSet,TreeSet类似

***工具类:***
Collections中有对list,set,map操作的各种方法。

***Collection常用方法***
* boolean add(Object o):该方法用于向集合添加一个元素。
* boolean addAll(Collection c):该方法把集合c里所有元素添加到指定集合中
* boolean clear():清除集合里的所有元素
* boolean contains(Object o):返回集合里是否包含指定元素
* boolean containsAll(Collection c):返回集合里是否包含集合c里的所有元素
* boolean isEmpty():返回集合是否为空
* Iterator iterator():返回一个Iterator,用于遍历集合里的元素
* boolean remove(Object c):删除集合中指定元素o
* boolean removeAll(Collection c):从集合中删除集合c
* boolean retainAll(Collection c):从集合中删除c里不包含的元素。
* int size():该方法返回集合里元素的个数
* Object[] toArray():该方法把集合转换成一个数组

***Map常用方法***
* void clear():删除该Map对象中的所有Key-value对
* boolean containsKey(Object key):查询Map中是否包含指定的Key
* boolean containsValue(Object value):查询Map中是否包含一个或多个value
* Object get(Object key):返回指定key所对应的value
* boolean isEmpty():查询Map是否为空
* Set keySet():返回该Map中所有key组成的Set集合
* Object put(Object key,Object value):添加一个key-value对，如果Map中已有一个与该key相等的key-value,则新的key-value对会覆盖原来的key-value对
* void putAll(Map m):将指定Map中的key-value对复制到本Map中
* Object remove(Object key):删除指定key所对应的value,并返回该value。若key不存在，返回null
* boolean remove(Object key,Object value):删除key-value对。
* Collection values():返回Map中value组成的集合
## 四、泛型
* ***泛型接口***
```
public interface List<E>{
    //在接口里，E可作为类型使用
    void add(E x);
    Iterator<E> iterator;
}
```
* ***泛型类***
```
public class Apple<T>{
    private T info;
    public Apple(){}
    public Apple(T info){...}
    ....
}
```
* ***由泛型类派生子类***
```
public class A extends Apple<String>{
    //使用泛型接口或父类时，不能再含泛型形参
    //public class A extends Apple<T>为错误的
}
```
* ***类型通配符***
```
public void test(List<?> c){
    //List<?>可以适配各种List<类型>类型的
}
```
* ***类型通配符的上限***
```
public void demo(List<? extends B> A){
    //B为某一个类，适配的只能为B或B的子类
    //如：
    /*
    List<C> A = new ArrayList<>();
    demo(A);
    其中，C必须为B或B的子类
    */
}
```
* ***类型通配符的下限***
    * 使用super关键字
    * 含义与通配符的上限相反
* ***泛型方法***
```
public class Demo{
    public <T> void demo(List<T> list){
        //可根据传入的List<T>类型推断出T
    }
}
```
## 五、异常处理
* ***两种异常处理方式***
    1. try...catch...处理异常
    ```
    try{
        ...
    }catch(Exception e){
        ...//处理异常
    }finally{
        ...
    }
    ```
    2. 自动关闭资源的try..catch语句
    ```
    try(//打开的资源){
        ...
    }catch(Exception e){
        ...
    }
    ```
    3. 向外抛出异常
    ```
    public void demo() throws Exception{
        ...
    }
    ```
* ***手动抛出异常***
```
public static void throwRuntime(int a){
    if(a > 0){
        //抛出runtimeException,可以显示捕获，也可不必理会
        //抛出checkedException，需要显示捕获
        
        //抛出runtimeException
        throw new RuntimeException("a不可以大于0");
    }
}
```
* ***finally会最后执行，无论try或catch中是否有return或throw等让方法结束的语句，finally中的throw和return会让catch或try中的return或throw失效***
```
public int demo(){
    try{
        ...
        return 1;
    }catch(Exception e){
        ...
        return 0;
    }finally{
        ...
        return 2;
    }
    //最后返回值必为2
}
```
## 六、IO
***文件:***
1. 文件和目录都是由File来操作的，可以创建文件，删除文件，重命名文件和目录等，但不能对文件进行读写操作。
2. 文件过滤器(FilenameFilter):筛选符合条件的文件
```
    String[] fileNames = file.list((dir,name)->name.endWith(".java"));
```
***输入、输出流:***
1. 低级流:FileInputStream,FileOutputStream,FileReader,FileWriter.
2. 处理流(包装流):在低级流的基础上进一步封装，提供更为方便的操作和更高的效率(装饰器模式),常用的包装流：PrintStream,BuffereInputStream,BuffereOutputStream,BuffereReader,BuffereWriter.

***对象序列化***
1. 序列化的目标是将对象保存到磁盘中，或允许在网络中直接传输对象。
2. 让某个类可序列化，只需要实现两个接口:Serializable,Externalizable,该接口无需实现任何方法。
3. 创建一个ObjectOutputStream输出想传送的对象
4. 创建一个ObjectInputStream读取对象(反序列化)
5. ***注意:*** 当使用序列化机制序列化可变对象时，只有第一次调用writeObject会将对象转换成字节序列

***输入流常用方法***

***字节流***
* int read():从输入流读取一个字节
* int read(byte[] b):从输入流中读取至多b.length字节数据，返回实际读取的字节数
* int read(byte[] b,int off,int len):从输入流中最多读取len个字节的数据，并将其从数组off位置中开始存储在数组b中，返回实际读取的字节

***字符流***
* 与字节流类似

***输出流常用方法***

***字节流/字符流***
* void write(int c):将指定字节/字符数组中的数据输出到输出流中
* void write(byte[]/char[] buf):将字节数组/字符数组输出到输出流中
* void write(byte[]/char[] buf,int off,int len):将字节数组/字符数组中从off位置开始，长度为len的字节/字符输出到输出流中

## 七、多线程
1. 线程的创建:
    1. 创建Thread子类
    2. Runnable接口创建线程类(可共享变量)
    3. 使用Callable创建线程
2. 线程的生命周期
    1. 新建状态
    2. 就绪状态
    3. 运行状态
    4. 阻塞状态
    5. 死亡状态
3. 线程同步
    1. synchronized加锁
    ```
    synchronized(obj){
        //此处是同步的代码
    }
    ```
    2. synchronized同步方法
    ```
    public synchronized void demo(){
        /*
        相当于
        public void demo(){
            synchronized(this){
                //同步代码块
            }
        }
        */
    }
    ```
    3. 同步锁(Lock)
    常用的锁:ReentrantLock
    ```
    class A{
        private final ReentrantLock lock = new ReentrantLock();
        
        public void demo(){
            lock.lock();
            try{
                //同步代码块
            }finally{
                lock.unlock();
            }
        }
    }
    ```
4. 线程通信
    1. 传统线程通信:
        1. wait():导致当前线程等待，直到其他线程调用该同步监测器的notify()或notifyAll()唤醒线程
        2. notify():唤醒同步检测器上的单个等待线程
        3. notifyAll():唤醒同步监测器上的所有线程
    2. Condition控制线程通信
        1. 获得Condition对象，通过Lock对象的newCondition方法
        2. await():相当于wait
        3. signal():相当于notify();
        4. signalAll():相当于notifyAll();
5. 线程组  
    java使用ThreadGroup来表示线程组，它可以对一批线程进行分类管理。一个线程加入了某一个线程组以后，将一直属于该线程组，线程运行中途不能改变它所属的线程组  
    ***指定线程组的方法：***
    * Thread(ThreadGroup group,Runnable target);
    * Thread(ThreadGroup group,Runnable target,String name);
    * Thread(ThreadGroup group,String name);
6. 线程池  
    线程池在启动时即创建大量空闲的线程，程序将一个Runnable对象或Callable对象传给线程池，线程池就会启动一个空闲的线程来执行他们的run()或call()方法,当run()或call()方法执行结束后，该线程并不会死亡，而是再次返回线程池中成为空闲状态，等待执行下一个Runnable对象的run()或call()方法。
7. 线程池的创建方法
    1. 调用Executors类的静态方法创建一个ExecutorService对象，该对象代表一个线程池
    2. 创建Runnable实现类或Callable实现类的实例，作为线程执行任务
    3. 调用ExecutorService对象的submit()方法来提交Runnable实例或Callable实例
    4. 当不想提交任何任务时，调用ExecutorService对象的shutdown()方法来关闭线程池