## Object

### 前言

Object类是Java的根类 ， 是所有其他类的基类



#### 一、equals方法

1. ==和equals的对比
	"\=\=" 是一个比较运算符 ：

	1. 当比较的是两个基本类型时 ， == 判断其**值**是否相等
	2. 当比较的是两个引用类型时 ， ==判断其地址是否相等

2. equals是Object类中定义的方法，只能判断引用类型
	其默认比较的是地址是否相等，但在子类中往往重写该方法，用于判断内容是否相等
	例如Integer、String

	```Java
	//Object.equals
	    public boolean equals(Object obj) {
	        return (this == obj);
	    }
	```

	```java
	//String.equals   
	public boolean equals(Object anObject) {
	        if (this == anObject) {
	            return true;
	        }
	        if (anObject instanceof String) {
	            String anotherString = (String)anObject;
	            int n = value.length;
	            if (n == anotherString.value.length) {
	                char v1[] = value;
	                char v2[] = anotherString.value;
	                int i = 0;
	                while (n-- != 0) {
	                    if (v1[i] != v2[i])
	                        return false;
	                    i++;
	                }
	                return true;
	            }
	        }
	        return false;
	    }
	```

	

### 二、HashCode方法

​	返回该类的HashCode

1. 提高具有哈希结构的容器的效率！
2. 两个引用，如果指向的是同一个对象，则哈希值肯定是一样的
3. 两个引用，如果指向的是不同对象，则哈希值是不一样的
4. 哈希值主要根据地址号来的， 不能完全将哈希值等价于地址。

### 三、ToString方法

1. 基本介绍 默认返回：全类名+@+哈希值的十六进制，【查看 Object 的 toString 方法】 子类往往重写 toString 方法，用于返回对象的属性信息 
2. 重写 toString 方法，打印对象或拼接对象时，都会自动调用该对象的 toString 形式
	案例演示：Monster [name, job, sal] 案例: ToString_.java
3. 当直接输出一个对象时，toString 方法会被默认的调用, 比如 System.out.println(monster)； 就会默认调用 monster.toString()

### 四、finalize方法

1. 当对象被回收时，系统自动调用该对象的 finalize 方法。子类可以重写该方法，做一些释放资源的操作

2.  什么时候被回收：当某个对象没有任何引用时，则 jvm 就认为这个对象是一个垃圾对象，就会使用垃圾回收机制来 销毁该对象，在销毁该对象前，会先调用 finalize 方法。

3. 垃圾回收机制的调用，是由系统来决定(即有自己的 GC 算法), 也可以通过 System.gc() 主动触发垃圾回收机制，测 试：Car [name] 

4. 老韩提示： 我们在实际开发中，几乎不会运用 finalize , 所以更多就是为了应付面试.

	```java
	        Car bmw = new Car("宝马");
	        //这时 car对象就是一个垃圾,垃圾回收器就会回收(销毁)对象, 在销毁对象前，会调用该对象的finalize方法
	        //,程序员就可以在 finalize中，写自己的业务逻辑代码(比如释放资源：数据库连接,或者打开文件..)
	        //,如果程序员不重写 finalize,那么就会调用 Object类的 finalize, 即默认处理
	        //,如果程序员重写了finalize, 就可以实现自己的逻辑
	        bmw = null;
	        System.gc();//主动调用垃圾回收器 garbage collector
	```

	

