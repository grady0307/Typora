# JAVA

## 遇到过的问题

- 对于单选框或单选按钮的触发器触发两次的问题
  - 一次点击会导致两次的值改变
  - trye->false,false->true
  - 需要在触发器开始时加一个`e.getValueIsAdjusting()==true`

- 自定义的包名不能与java自带的包重合,内置文件声明包必须与外部包相同

## IDEA

- 项目结构
  - project项目->module模块->package包->class类

## 内存

- 栈

![image-20220930105855773](C:\Users\良小辰\AppData\Roaming\Typora\typora-user-images\image-20220930105855773.png)

- 对于一个对象

![image-20220930110205142](C:\Users\良小辰\AppData\Roaming\Typora\typora-user-images\image-20220930110205142.png)

![image-20220930110831944](C:\Users\良小辰\AppData\Roaming\Typora\typora-user-images\image-20220930110831944.png)

- 基本数据类型

![image-20220930111704252](C:\Users\良小辰\AppData\Roaming\Typora\typora-user-images\image-20220930111704252.png)

==赋值给其它变量时赋的是真实值==

而引用数据类型赋值地址值

![image-20220930112129354](C:\Users\良小辰\AppData\Roaming\Typora\typora-user-images\image-20220930112129354.png)

- 堆

- 方法区

- 本地方法栈

- 寄存器

## 标识符与数据类型

- 标识符必须以字母，下划线或$开头

- boolean 的默认值是false

- 用final来修饰常量` final double PI =3.1415; `

- 不同类型运算时先转化为最高级类型，布尔型不能转换

- ```
  byte,short,char—> int —> long—> float —> double
  ```

- 小数默认是 double 类型浮点型，在定义 float 类型时必须在数字后面跟上 F 或者 f。


### 数组

- 一维数组` int[] a=new int[5];`

- ~~~java
  //foreach循环
  for(int v: a){
  	System.out.println(v+" ");
  }
  ~~~

- ~~~java
   //数组拷贝
   int[] c=Arrays.copyOf(a,a.length-1);
  ~~~

- ~~~java
  //不规则数组
  int[][] c=new int[2][];
  c[0]=new int[3];
  c[1]=new int[5];
  ~~~

### String

~~~java
String s1="java";//字符常量
String s2=new String("java");//字符串变量对象
s1==s2是比较地址，s1.equals(s2)是比较内容
~~~

### 类型转换

- int转String
  - `String numInString = String.valueOf(num);`
  - 对Integer对象`String numInString = num.toString();`
  - 对int对象`String numInString = Integer.toString(num);`
- String转int
  - `Integer.parseInt(String)`返回int类
  - `Integer.valueOf(String)`返回Integer类


### 集合框架

#### Collection接口

常用方法

- Arraylist<> list=new Arraylist<>(10);

- public Iterator<E> iterator()//用于得到迭代器
-  public int size()获取的是元素的个数不是集合的容量
- public boolean add(E element)
- public boolean remove(Object o)//删除等于o的对象
- public void clear()
- public boolean isEmpty()
- public boolean contains(Object o) //判断是否包含与o相等的对象

#### Iterator 类

- public boolean hasNext()
- public E next()//返回将要访问的下一个元素
- public void remove()//删除上次访问的元素，必须结合next使用

~~~java
//常用于遍历
it=list.iterator();
while(it.hasNext()){
	Integer t=(Integer)it.next();//注意必须转化为要访问的类型
	System.out.println(t);
}
~~~

==只要集合的结构发生了变化，就必须重新获取迭代器==

#### HashSet 类

- 散列集合
- 不允许重复
- 顺序访问顺序不一定等于添加的顺序

#### HashMap

~~~java
HashMap map=new HashMap();
Iteraror it =map.entrySet().iterator();//注意要用entrySet()
while(it.hasNext()){
	Map.Entry entry=(Map.Entry)it.next();
    String key = (String)entry.getKey();
    String value =(String)entry.getValue();
}
~~~

### Object

#### equals()方法

对于非String,equals比较的是地址

#### toString()

默认的输出方法

覆盖后可直接输出System.out.println(obj);

#### getClass()

A obj=new A();

obj.getClass()==A.class;

也可用obj instanceof A

### 枚举类

~~~java
enum ErrorCode{
	SUCCESS,OUTOFINDEX,NOTFIND;
}
return ErrorCode.SUCCESS;
~~~

SUCCESS等价于` public static final ErrorCode SUCESS = new ErrorCode();`

- 也可添加描述

~~~java
enum ErrorCode{
    SUCESS(0,"运行成功");
    int code;
    String des;
    private ErrorCode(int code ,String des){
        this.code=code;
        this.des = des;
	}
}
~~~

## 类的设计

### 依赖关系

局部变量，函数参数，返回值

~~~java
class A{
	public B f(C c){
		D d =new D();
		return b;
	}
}
~~~

### 聚合关系

实例对象

~~~java
class A{
	private B b=null;
	private A(){
		b= new B();
	}
}
~~~

### 继承关系

## 语法

#### 标准的JavaBean

![image-20220930104137963](C:\Users\良小辰\AppData\Roaming\Typora\typora-user-images\image-20220930104137963.png)

#### 提供带标号的break语句

- ` outer:{for();for{};break outer;}` 

#### 输入

- ` SCanner sc  = new Scanner (System.in);`

~~~java
String s = sc.nextLine();//可输入无效字符
String s1 = sc.next();//不可输入无效字符
~~~

- stu1=stu2 是一种地址赋值
- 一切方法都从public static void main(Sting[] args)开始执行

- 在栈内存中定义的变量可以不赋初值，默认为null或0

- 单个字符输入` char c=(char)System.in.read();`

#### 构造方法

- 无返回值
- 名字与类名相同，一个类可以有多个构造方法（方法重载

#### this

- 在构造方法中避免歧义` this.name = name ;`
- 在一个构造方法中调用其他构造方法` this()`-但是必须放在第一行

- 用于链式调用  ` x.time().time()`

#### string.trim()

**返回一个新的字符串。这个字符串将删除了原始字符串头部和尾部的空格**

#### string.substring()

返回截取的字符串

~~~java
public String substring(int beginIndex)

或

    public String substring(int beginIndex, int endIndex)//不取endIndex的数
~~~

#### charAt()

返回单个索引字符

```
public char charAt(int index)
```

#### equals()

equals() 方法用于判断 Number 对象与方法的参数进是否相等。

` "".equals(x)`

#### instanceof

测试左边的对象是否是右边的类的实例

A instanceof B

#### format()

用于格式化变量format("%f%n", e);

#### 迭代 HashMap

~~~java
for (Integer i : Sites.keySet()) {
            System.out.println("key: " + i + " value: " + Sites.get(i));
        }
        // 返回所有 value 值
        for(String value: Sites.values()) {
          // 输出每一个value
          System.out.print(value + ", ");
        }
~~~

#### Sort排序

##### 数组排序

- 默认升序排序`Arrays.sort(array);`

- 要降序可以倒叙访问或创建新数组倒叙赋值

##### 集合排序

- 包装类

  - ~~~java
    //Integer集合，正序排序
    List<Integer> list = new ArrayList<Integer>(Arrays.asList(10, 3, 6, 1, 4, 5, 9));
    Collections.sort(list);
    System.out.println("集合正序排序：");
    for (Integer num : list) {
            System.out.println(num);
    }
    ~~~

##### 自定义排序

- 先实现Comparable接口，重写接口方法,再调用
- `public class StudentAsc implements Comparable<StudentAsc>`
- `public int compareTo(StudentAsc o) {
          if(null == this.age) {
              return -1;
          }
          if(null == o.getAge()) {
              return 1;
          }
          return this.age.compareTo(o.getAge());
      }`

- `Collections.sort(studentAscs);`

-  比较不同类的对象时，对其父类添加 comparable接口即可[(23条消息) Java类对象排序问题---如何对不同类的所有对象进行排序_理强的博客-CSDN博客](https://blog.csdn.net/LoveRestart/article/details/68060867)

### 多态

1. 继承关系
2. 方法覆盖
3. 超类引用指向子类对象

#### 抽象类

- 可有构造类和具体方法
- 不能创建对象但是能声明引用变量
- 子类必须实现其抽象方法

#### 接口

~~~
interface A{
public abstract getA();
}
class B implements A{
public getA();
}
//可实现多个接口
//实现接口必须显式的使用public
~~~

-  可使用default缺省方法

#### 内部类

~~~java
class Outer{
	private int age=12;
	class Inner{
	public voidshowInner(){
	
	}
	}
}

//创建内部对象
Outer outer=new Outer();
Outer.Inner inner=outer.new Inner();
~~~

~~~java
//匿名内部类
abstract class Animal{
	abstract void eat();
}
public class A{
public static void main(String[] args){
Animal a=new Animal(){
	void eat(){};
}//创建内部类
}
}
~~~

### 异常类及异常处理方式

- 运行时异常可以不处理，检查型异常

#### 捕获异常

使用 try 和 catch 关键字可以捕获异常。try/catch 代码块放在异常可能发生的地方。

try/catch代码块中的代码称为保护代码，使用 try/catch 的语法如下：

```java
try{
  // 程序代码
}catch(异常类型1 异常的变量名1){
  // 程序代码
}catch(异常类型2 异常的变量名2){
  // 程序代码
}finally{
  // 程序代码
}
```

### 人为抛出变量

`throw new IOException();`

### 声明自定义异常

在 Java 中你可以自定义异常。编写自己的异常类时需要记住下面的几点。

- 所有异常都必须是 Throwable 的子类。
- 如果希望写一个检查性异常类，则需要继承 Exception 类。
- 如果你想写一个运行时异常类，那么需要继承 RuntimeException 类。

可以像下面这样定义自己的异常类：

`class MyException extends Exception{ }`

### 流(Stream)、文件(File)和IO

- 控制台字符输入
  - `BufferedReader br = new BufferedReader(new InputStreamReader(System.in));`
  - `c=(char)br.read();`
  - `str = br.readLine();`

#### 读写文件

![img](https://www.runoob.com/wp-content/uploads/2013/12/iostream2xx.png)

- ## FileInputStream

  - 先要创建input对象

  - 可以使用字符串类型的文件名来创建一个输入流对象来读取文件：

    `InputStream f = new FileInputStream("C:/java/hello");`

  - `也可以使用一个文件对象来创建一个输入流对象来读取文件。我们首先得使用 File() 方法来创建一个文件对象：

    `File f = new File("C:/java/hello"); `

    `InputStream in = new FileInputStream(f);`

  - **public void close() throws IOException{}**
    关闭此文件输入流并释放与此流有关的所有系统资源。

  - **protected void finalize()throws IOException {}**
    这个方法清除与该文件的连接。确保在不再引用文件输入流时调用其 close 方法。

  - **public int read(int r)throws IOException{}**
    这个方法从 InputStream 对象读取指定字节的数据。返回为整数值。返回下一字节数据，如果已经到结尾则返回-1。

  - **public int read(byte[] r) throws IOException{}**
    这个方法从输入流读取r.length长度的字节。返回读取的字节数。如果是文件结尾则返回-1。

  - **public int read(byte[] r) throws IOException{}**
    这个方法从输入流读取r.length长度的字节。返回读取的字节数。如果是文件结尾则返回-1。

- ## FileOutputStream

  - `OutputStream f = new FileOutputStream("C:/java/hello")`

    也可以使用一个文件对象来创建一个输出流来写文件。我们首先得使用File()方法来创建一个文件对象：

    `File f = new File("C:/java/hello"); OutputStream fOut = new FileOutputStream(f);`

    `FileOutputStream fos = new FileOutputStream(myFile,true);`

    - 加true是追加方式，默认是覆盖

- 目录

  - **mkdir( )**方法创建一个文件夹，成功则返回true，失败则返回false。失败表明File对象指定的路径已经存在，或者由于整个路径还不存在，该文件夹不能被创建。

  - **mkdirs()**方法创建一个文件夹和它的所有父文件夹。

  - 读取目录

    - ~~~java
      public static void main(String args[]) {
              String dirname = "/tmp";
              File f1 = new File(dirname);
              if (f1.isDirectory()) {
                  System.out.println("目录 " + dirname);
                  String s[] = f1.list();
                  for (int i = 0; i < s.length; i++) {
                      File f = new File(dirname + "/" + s[i]);
                      if (f.isDirectory()) {
                          System.out.println(s[i] + " 是一个目录");
                      } else {
                          System.out.println(s[i] + " 是一个文件");
                      }
                  }
              } else {
                  System.out.println(dirname + " 不是一个目录");
              }
      ~~~

  - 删除目录

    - 删除某一目录时，必须保证该目录下没有其他文件才能正确删除，否则将删除失败
    - **java.io.File.delete()** 

## 多线程编程

## 学堂在线错题

- .java文件保存编写程序的源代码，.class字节码文件保存编译后的二进制文件
- JDK>JRE>JVM
- Java编写的程序只能在JVM环境中运行。
- true，false和null看起来像关键字，但事实上它们是字面量，不是关键字。
- Java语言的字符采用Unicode字符集编码方案。
- 引用数据类型有类、接口和数组
- 若定义有short s; byte b; char c; 则表达式s - b + c的结果类型为==int==
- 逻辑与&和简洁与&&的区别
- Java提供了4种能在循环结构中使用的跳转语句：分别是break语句、continue语句、return语句和throw语句
- 面向对象编程的三个特性：封装，继承，多态
- 与POP（面向过程）相比，OOP（面向对象）最大的特点是将数据与过程看成同等重要
- 封装的基本单位是类
- 成员方法修饰符：protected,synchronized
- 静态方法不能使用this
- 构造函数没有任何返回值，包括 void，默认返回类型就是对象类型本身
- java.awt是用于创建图形用户界面的包，提供了用于实现图形界面的组件，如窗口、按钮、文本框、对话框等；java.util包含了一些实用类和有用的数据结构，如集合框架类、日期类等
- 包是用来管理.java文件的(x)
- 在访问权限设置时，最小访问权限原则是一个必须要坚持的原则
- 类成员变量（静态变量）存放于方法区，实例变量（成员变量）存放在堆内存，局部变量存放在栈内存
- foreach循环不可以改变变量的值，但是可以用它去改变对象的值
- 对象数组的的存储在堆中是链式的
- 当继承一个抽象类时，必须要实现抽象类的抽象方法(抽象类不用)
- final 修饰的成员变量必须手动初始化
- 成员内部类不能含有static修饰的成员变量和方法
- 匿名内部类是独立的类
- 面向对象设计的最高原则是开闭原则
- 多重捕获的形参隐含为final修饰，不能为其赋值
- try语句中出现异常之后的语句不会被执行
- 一个图形界面应用程序可以有多个JFrame
- 通过File对象不能对文件内容进行读/写操作
- 对象若要实现序列化，其所属的类必须实现==Serializable==接口
- 对象序列化时，不会保存static和==transient==类型的变量。
- ==Externalizable==接口用于在进行对象序列化时自行确定哪些变量需要保留
- 主关键字是表中的一个或多个字段
- 同一进程中的线程可以直接共享进程中的数据、资源
- ==synchronized==同步方法
- ==volatile==使变量始终对其它变量可见
- volatile不能保证原子性 ，而通过synchronized进行正确的同步后，是可以保证原子性的
- Java中进行UDP通信时，常用DatagramSocket类把要发送的信息打包。
- 在其它类中创建内部类对象`Outer.Inner i = new Outer().new Inner()`

## Java上机考试重要知识点练习

\1.   图形界面的创建，事件处理。
 组件：文本区JTextArea，按钮JButton，框架JFrame，面板JPanel，滚动面板JScrollPane，标签JLabel，布局管理器等。

文本区：设置自动换行，添加滚动面板，设置文本区内容，追加文本区内容。

事件处理：ActionEvent

~~~java
JTextArea jt = new JTextArea();
jt.setLineWrap(true);
JScrollPane js = new JScrollPane(jt);
jt.setText("aa");
jt.append("bb");
JButton jb = new JButton("确认");
JPanel jp = new JPanel();
jp.setLayout(new FlowLayout());
JLabel jl = new JLabel("是否确认");
JFrame jf = new JFrame();
jf.add(BorderLayout.CENTER,jp);
jf.setSize(800,500);
jf.setResizable(false);
jf.setVisable(true);
jf.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);

class ButtonEvent implements ActionListener{
    public void actionPerformed(ActionEvent e){
		if(e.getSource()==jb){
			System.out.print("0");
        }
    }
}
ButtonEvent be = new ButtonEvent();
jb.addActionListener(be);

jb1.addActionListener(new ActionListener(){
    public void actionPerformed(ActionEvent e){
		if(e.getSource()==jb){
			System.out.print("1");
        }
    }
})
    
jb2.addActionListener(()->{
    System.out.print("2");
})
~~~



\2.   文件流的创建与使用。

~~~java
File myFile = new File("");

FileInputStream fis = new FileInputStream(myFile);
int n;
while((n=fis.read())!=-1){
	System.out.print((char)n);
}
fis.close();

byte buf = new byte[(int)(file.length())];
fis.read(buf);

FileOutputStream fos = new FileOutputStream(myFile,true);//追加方式
byte buffer[] = s.getBytes();
fos.write(buffer);

for (int i =0;i<s.length();i++){
	fos.write(s.charAt(i));
}

~~~



\3.   数组和对象数组的创建、初始化，数组元素的访问、赋值等。

~~~java
int[] a = new int[5];
int[] b =Arrays.copyOf(a,a.length-1)
Student aStudent ={new Student(),new Student()}
~~~

\4.   随机数的生成。

使用Math.random()或其他方法。

**通过 (int) (Math.random()\*N) 可以随机产生一个[0,N-1]之间的正整数。**

`(int)(Math.random()*N+Y)`

~~~java
Random r = new Random();
a = r.nextInt(10);
~~~



\5.   多线程

线程类的定义，线程对象的创建和启动，线程的同步（synchronized）。

~~~java
class ThreadTest extends Thread{
    public void run(){

    }
}
ThreadTest tt = new ThreadTest();
tt.start();

class RunnableTest implments Runnable{
    public void run(){

    }
}
RunnableTest rt = new RunnableTest();
Thread t = new Thread(rt);
t.start();

class MyThread implements Callable<String>{
    public String call(){
    	return ""
    }
}
MyThread mt = new MyThread();
FutureTask<String> ft = new FutureTask<String>(mt);
Thread t = new Thread(ft);
t.start();
System.out.print(ft.get());

public synchronized void a(){
	while(){
		this.wait();
    }
    this.notify();
}

synchronized(this){

}
~~~



\6.   在类之间传递对象的方法：可以通过构造方法传递。

~~~java
class A{
int a=1;
public int getA(){
    return this.a;
}
}


import A;
class B{
int b=2;
public void setB(int n){
    this.b=n;
}

public static void main(String[] arg){
A a = new A();
B b = new B();
b.setB(a.getA());
}
}
~~~



\7.   内部类的使用。

- ~~~java
  FileReader fr = new FileReader(file);
  int n;
  while((n=fr.read())!=-1){
      System.out.print((char)n);
  }
  ~~~

- ~~~java
  byte buffer[] =s.getBytes();
  fos.write(buffer);
  ~~~
