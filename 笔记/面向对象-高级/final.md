## Final

类似于C语言中的const修饰符

final关键字可以修饰 ：类、属性、方法、局部变量

1. 当不希望类被继承时，可以使用final修饰类

	```java
	//如果我们要求A类不能被其他类继承
	//可以使用final修饰 A类
	final class A { }
	```

2. 当不希望父类的某个方法被子类重写时，可以使用final关键字修饰方法

	```java
	//如果我们要求hi不能被子类重写
	//可以使用final修饰 hi方法
	public final void hi() {}
	```

3. 当不希望类的某个属性或某个局部变量的值被修改时，可以使用final修饰

	```java
	//当不希望某个局部变量被修改，可以使用final修饰
	//这时，NUM 也称为 局部常量
	final double NUM = 0.01;
	```

	

### 细节

