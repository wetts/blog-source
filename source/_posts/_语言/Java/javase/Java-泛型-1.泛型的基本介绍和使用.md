转自：http://blog.csdn.net/lonelyroamer/article/details/7864531

## 一、泛型的基本概念
泛型的定义：泛型是JDK 1.5的一项新特性，它的本质是参数化类型（Parameterized Type）的应用，也就是说所操作的数据类型被指定为一个参数，在用到的时候在指定具体的类型。这种参数类型可以用在类、接口和方法的创建中，分别称为泛型类、泛型接口和泛型方法。

泛型思想早在C++语言的模板（Templates）中就开始生根发芽，在Java语言处于还没有出现泛型的版本时，只能通过Object是所有类型的父类和类型强制转换两个特点的配合来实现类型泛化。例如在哈希表的存取中，JDK 1.5之前使用HashMap的get()方法，返回值就是一个Object对象，由于Java语言里面所有的类型都继承于java.lang.Object，那Object转型为任何对象成都是有可能的。但是也因为有无限的可能性，就只有程序员和运行期的虚拟机才知道这个Object到底是个什么类型的对象。在编译期间，编译器无法检查这个Object的强制转型是否成功，如果仅仅依赖程序员去保障这项操作的正确性，许多ClassCastException的风险就会被转嫁到程序运行期之中。

泛型技术在C#和Java之中的使用方式看似相同，但实现上却有着根本性的分歧，C#里面泛型无论在程序源码中、编译后的IL中（Intermediate Language，中间语言，这时候泛型是一个占位符）或是运行期的CLR中都是切实存在的，List<int>与List<String>就是两个不同的类型，它们在系统运行期生成，有自己的虚方法表和类型数据，这种实现称为类型膨胀，基于这种方法实现的泛型被称为真实泛型。

Java语言中的泛型则不一样，它只在程序源码中存在，在编译后的字节码文件中，就已经被替换为原来的原始类型（Raw Type，也称为裸类型）了，并且在相应的地方插入了强制转型代码，因此对于运行期的Java语言来说，ArrayList<int>与ArrayList<String>就是同一个类。所以说泛型技术实际上是Java语言的一颗语法糖，Java语言中的泛型实现方法称为类型擦除，基于这种方法实现的泛型被称为伪泛型。（类型擦除在后面在学习）

使用泛型机制编写的程序代码要比那些杂乱的使用Object变量，然后再进行强制类型转换的代码具有更好的安全性和可读性。泛型对于集合类来说尤其有用。

泛型程序设计（Generic Programming）意味着编写的代码可以被很多不同类型的对象所重用。

####实例分析：

在JDK1.5之前，Java泛型程序设计是用继承来实现的。因为Object类是所用类的基类，所以只需要维持一个Object类型的引用即可。就比如ArrayList只维护一个Object引用的数组：
```
public class ArrayList//JDK1.5之前的  
{  
    public Object get(int i){......}  
    public void add(Object o){......}  
    ......  
    private Object[] elementData;  
}  
```
这样会有两个问题：

1. 没有错误检查，可以向数组列表中添加类的对象
2. 在取元素的时候，需要进行强制类型转换

这样，很容易发生错误，比如：

```
/**jdk1.5之前的写法，容易出问题*/  
ArrayList arrayList1=new ArrayList();  
arrayList1.add(1);  
arrayList1.add(1L);  
arrayList1.add("asa");  
int i=(Integer) arrayList1.get(1);//因为不知道取出来的值的类型，类型转换的时候容易出错  
```
这里的第一个元素是一个长整型，而你以为是整形，所以在强转的时候发生了错误。

所以。在JDK1.5之后，加入了泛型来解决类似的问题。例如在ArrayList中使用泛型：
```
                /** jdk1.5之后加入泛型*/  
        ArrayList<String> arrayList2=new ArrayList<String>();  //限定数组列表中的类型  
//      arrayList2.add(1); //因为限定了类型，所以不能添加整形  
//      arrayList2.add(1L);//因为限定了类型，所以不能添加整长形  
        arrayList2.add("asa");//只能添加字符串  
        String str=arrayList2.get(0);//因为知道取出来的值的类型，所以不需要进行强制类型转换  
```

还要明白的是，泛型特性是向前兼容的。尽管 JDK 5.0 的标准类库中的许多类，比如集合框架，都已经泛型化了，但是使用集合类（比如 HashMap 和 ArrayList）的现有代码可以继续不加修改地在 JDK 1.5 中工作。当然，没有利用泛型的现有代码将不会赢得泛型的类型安全的好处。

在学习泛型之前，简单介绍下泛型的一些基本术语，以ArrayList<E>和ArrayList<Integer>做简要介绍：

整个成为ArrayList<E>泛型类型

ArrayList<E>中的 E称为类型变量或者类型参数

整个ArrayList<Integer> 称为参数化的类型

ArrayList<Integer>中的integer称为类型参数的实例或者实际类型参数

·ArrayList<Integer>中的<Integer>念为typeof   Integer

ArrayList称为原始类型

## 二、泛型的使用

泛型的参数类型可以用在类、接口和方法的创建中，分别称为泛型类、泛型接口和泛型方法。下面看看具体是如何定义的。

### 1、泛型类的定义和使用
一个泛型类（generic class）就是具有一个或多个类型变量的类。定义一个泛型类十分简单，只需要在类名后面加上<>，再在里面加上类型参数：
```
class Pair<T> {  
    private T value;  
        public Pair(T value) {  
                this.value=value;  
        }  
        public T getValue() {  
        return value;  
    }  
    public void setValue(T value) {  
        this.value = value;  
    }  
}  
```

现在我们就可以使用这个泛型类了：
```
public static void main(String[] args) throws ClassNotFoundException {  
        Pair<String> pair=new Pair<String>("Hello");  
        String str=pair.getValue();  
        System.out.println(str);  
        pair.setValue("World");  
        str=pair.getValue();  
        System.out.println(str);  
    }  
```

Pair类引入了一个类型变量T，用尖括号<>括起来，并放在类名的后面。泛型类可以有多个类型变量。例如，可以定义Pair类，其中第一个域和第二个域使用不同的类型：```public class Pair<T,U>{......}```

注意：类型变量使用大写形式，且比较短，这是很常见的。在Java库中，使用变量E表示集合的元素类型，K和V分别表示关键字与值的类型。（需要时还可以用临近的字母U和S）表示“任意类型”。

### 2、泛型接口的定义和使用
定义泛型接口和泛型类差不多，看下面简单的例子：

```
interface Show<T,U>{  
    void show(T t,U u);  
}  

class ShowTest implements Show<String,Date>{  
    @Override  
    public void show(String str,Date date) {  
        System.out.println(str);  
        System.out.println(date);  
    }  
}  
```
测试一下：

```
public static void main(String[] args) throws ClassNotFoundException {  
        ShowTest showTest=new ShowTest();  
        showTest.show("Hello",new Date());  
    }  
```

### 3、泛型方法的定义和使用

泛型类在多个方法签名间实施类型约束。在 List<V> 中，类型参数 V 出现在 get()、add()、contains() 等方法的签名中。当创建一个 Map<K, V> 类型的变量时，您就在方法之间宣称一个类型约束。您传递给 add() 的值将与 get() 返回的值的类型相同。

类似地，之所以声明泛型方法，一般是因为您想要在该方法的多个参数之间宣称一个类型约束。

举个简单的例子：
```
public static void main(String[] args) throws ClassNotFoundException {  
        String str=get("Hello", "World");  
        System.out.println(str);  
    }  

    public static <T, U> T get(T t, U u) {  
        if (u != null)  
            return t;  
        else  
            return null;  
    }  
```

## 三、泛型变量的类型限定

在上面，我们简单的学习了泛型类、泛型接口和泛型方法。我们都是直接使用<T>这样的形式来完成泛型类型的声明。

有的时候，类、接口或方法需要对类型变量加以约束。看下面的例子：

有这样一个简单的泛型方法：
```
public static <T> T get(T t1,T t2) {  
        if(t1.compareTo(t2)>=0);//编译错误  
        return t1;  
    }  
```

因为，在编译之前，也就是我们还在定义这个泛型方法的时候，我们并不知道这个泛型类型T，到底是什么类型，所以，只能默认T为原始类型Object。所以它只能调用来自于Object的那几个方法，而不能调用compareTo方法。

可我的本意就是要比较t1和t2，怎么办呢？这个时候，就要使用类型限定，对类型变量T设置限定（bound）来做到这一点。

我们知道，所有实现Comparable接口的方法，都会有compareTo方法。所以，可以对<T>做如下限定：
```
public static <T extends Comparable> T get(T t1,T t2) { //添加类型限定  
        if(t1.compareTo(t2)>=0);  
        return t1;  
    }  
```
类型限定在泛型类、泛型接口和泛型方法中都可以使用，不过要注意下面几点：

1. 不管该限定是类还是接口，统一都使用关键字 extends
2. 可以使用&符号给出多个限定，比如```public static <T extends Comparable&Serializable> T get(T t1,T t2) ```
3. 如果限定既有接口也有类，那么类必须只有一个，并且放在首位置```public static <T extends Object&Comparable&Serializable> T get(T t1,T t2)```
