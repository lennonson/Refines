[[JAVA2.0]]
[[JDBC]]
[[Mybatis]]
# Basic Grammar

> 2024.06.17
>
> I'm ready to write note in english
>
> GOOD LUCK!!!

---

## syntax

### comment

1. single line comment

   ```java
   // system.out.println("this is an comment");
   ```

2. multi-line comment

   ```java
   /*
       System.out.println("This is the first line comment.");
       System.out.println("This is the second line comment.");
   */
   ```

3. documentation comment(also called doc comment)

   ```java
   /*
       System.out.println("This is the first line comment.");
       System.out.println("This is the second line comment.");
   */
   ```

### source file name

- The name of a source file should exactly match the public class name with the extension of .**java**. 

   源码文件的名字应该准确匹配有.java后缀公有类的名字

   ```java
   GFG.java // valid syntax
   gfg.java // invalid syntax
   ```

### case sensitivity

- java is a case-sensitive language.

  ```java
  System.out.println("GeeksforGeeks"); // valid syntax
  system.out.println("GeeksforGeeks"); // invalid syntax
  ```

### class name

- the first name of the class should be Uppercase
- lowercase is allowed but discouraged
- If several words are used to form the name of the class, each inner word’s first letter should be in Uppercase.
- Underscores are allowed, but not recommended.

> 改改习惯，多用驼峰命名，少用下划线(underscore)

### main entry point

```java
public static void main(String [] args)
```

### method name

1. all the method name should start with a lowercase letter
2. each first letter should be in Uppercase

### identifiers

1. all unicode characters are valid,not just the ASCII subset
2. all identifiers can begin with a letter,a currency symbol(货币符号) or an underscore(_),according to the convention(惯例),a letter should be lower case for variables.
3. case-sensitive

### Hello World!

```java
public class Helloworld {
	public static void main(String[] args) {
        System.out.println("hello,world!");
    }
}
```

---

## data type

### primitive type

|  Type   |       Description       | Default |  Size   |              Example Literals               |                    Range of values                     |
| :-----: | :---------------------: | :-----: | :-----: | :-----------------------------------------: | :----------------------------------------------------: |
| boolean |      true or false      |  false  |  1 bit  |                 true, false                 |                      true, false                       |
|  byte   | twos-complement integer |    0    | 8 bits  |                   (none)                    |                      -128 to 127                       |
|  char   |    Unicode character    | \u0000  | 16 bits | ‘a’, ‘\u0041’, ‘\101’, ‘\\’, ‘\’, ‘\n’, ‘β’ |   characters representation of ASCII values0 to 255    |
|  short  | twos-complement integer |    0    | 16 bits |                   (none)                    |                   -32,768 to 32,767                    |
|   int   | twos-complement intger  |    0    | 32 bits |                 -2,-1,0,1,2                 |            -2,147,483,648 to 2,147,483,647             |
|  long   | twos-complement integer |    0    | 64 bits |              -2L,-1L,0L,1L,2L               | -9,223,372,036,854,775,808 to9,223,372,036,854,775,807 |
|  float  | IEEE 754 floating point |   0.0   | 32 bits |    1.23e100f , -1.23e-100f , .3f ,3.14F     |                 upto 7 decimal digits                  |
| double  | IEEE 754 floating point |   0.0   | 64 bits |     1.23456e300d , -123456e-300d , 1e1d     |                 upto 16 decimal digits                 |

### byte和int

在Java中都是整数类型，但它们有以下区别：

1. byte类型占用1个字节（8位），取值范围为-128到127；而int类型占用4个字节（32位），取值范围为-2147483648到2147483647。
2. byte类型占用的内存空间比int类型少，因为它只需要1个字节的存储空间。
3. byte类型通常用于处理字节流数据，例如从文件读取数据或网络传输数据时；
4. byte类型参与运算时，会发生类型提升，即会**<u>自动转换为int类型</u>**进行计算，<u>计算结果也是int类型</u>。而int类型之间的运算结果仍然是int类型。

### non-primitive type

1. #### string

   ```java
   String s = "GeeksforGeeks";
   String s1 = new String("GeeksforGeeks"); 
   ```

2. class

   1. modifiers
   2. class name
   3. superclass
   4. interface
   5. body

3. object

4. array

## variable

1. Local Variables必须初始化！！！
2. Static Variables不必须初始化
3. Instance Variables

#### scope of variable

```java
Modifier      Package  Subclass  World

public          Yes      Yes     Yes

protected       Yes      Yes     No

Default (no
modifier)       Yes       No     No

private         No        No     No
```

## Wrapper Classes

```java
// autoboxing
import java.util.ArrayList;
class Autoboxing {
    public static void main(String[] args)
    {
        char ch = 'a';
        // Autoboxing- primitive to Character object
        // conversion
        Character a = ch;
    }
}
```

- 在这段代码中，作用是将基本类型的`char`自动装箱为`Character`对象。
- 在Java中，自动装箱是指将基本类型自动转换为对应的包装类对象。在这个例子中，`char`类型的变量`ch`被自动装箱为一个`Character`对象`a`。这样做的好处是可以在需要使用对象而基本类型不可用的情况下，如集合类的操作和泛型方法的参数等。
- `Character`类提供了一些有用的方法，如`isLetter()`、`toUpperCase()`等，我们可以通过`a`对象来调用这些方法。

```java
import java.util.ArrayList;
 
class Unboxing {
    public static void main(String[] args)
    {
        Character ch = 'a';
        // unboxing - Character object to primitive
        // conversion
        char a = ch;
        
        byte a = 1;
        // wrapping around Byte object
        Byte byteobj = new Byte(a);
    }
}
```

## Custom Wrapper Classes

```java
import java.io.*;
class Maximum {
    private int maxi = 0;
    private int size = 0;
    public void insert(int x)
    {
        this.size++;
        if (x <= this.maxi)
            return;
        this.maxi = x;
    }
    public int top() { return this.maxi; }
 
    public int elementNumber() { return this.size; }
};
class GFG {
    public static void main(String[] args)
    {
        Maximum x = new Maximum();
        x.insert(12);
        x.insert(3);
        x.insert(23);
        System.out.println("Maximum element: " + x.top());
        System.out.println("Number of elements inserted: "
                           + x.elementNumber());
    }
}
```

## Input

### buffer reader

```java
// stream of character
BufferedReader bfn = new BufferedReader(new InputStreamReader(System.in));

// String reading internally
String str = bfn.readLine();
// Integer reading internally
int it = Integer.parseInt(bfn.readLine());
```

1. `close()`closes the stream and releases any system resources associated with it
   1. once closed,any operation will throw an IOEException
   2. closing a closed stream has no effect
2. `mark()`mark the present position in the stream
   1. you could call `reset()`to attempt to reposition to the point
3. `markSupported()`tell whether this stream supports the `mark()`
4. `read()`reads a single character
5. `read(char[] cbuf,int off,int len)`Reads characters into a portion of an array
6. `readLine()`reads a line of text
7. `ready()`tell whether this stream is ready to be read
8. `reset()`resets the stream to the most recent mark
9. `skip()`skip characters 

### scanner class 

```java
import java.util.Scanner;  
Scanner scn = new Scanner(System.in);
// read by next() function
String str1 = scn.next();
String str2 = scn.nextLine(); // 读入一行字符串
// read by nextFloat() function
float f = scn.nextFloat();
```

### difference

1. `BufferedReader`is faster than`Scanner`
2. `BufferedReader`reads larger input than `Scanner`
3. `BufferedReader` is preferred as it is synchronized.
4. for decent input,and easy readibility.The Scanner is preferred

### Console Class

> It has been becoming a preferred way for reading user’s input from the command line.

### Advantages:

- Reading password without echoing the entered characters.
- Reading methods are synchronized.
- Format string syntax can be used.
- Does not work in non-interactive environment (such as in an IDE).

```java
String name = System.console().readLine();
System.out.println("You entered string" + name);
```

### using command line argument

```java
class Hello {
    public static void main(String[] args) {
        // check if length of args array is
        // greater than 0
        if (args.length > 0) {
            System.out.println(
                "The command line arguments are:");
            // iterating the args array and printing
            // the command line arguments
            for (String val : args)
                System.out.println(val);
        }
        else
            System.out.println("No command line "
                               + "arguments found.");
    }
}
```

***\*Command Line Arguments:\**** 

```bash
javac GFG1.java
java Main Hello World
```

### DataInputStream class

```java
DataInputStream reader = new DataInputStream(System.in);
int inputInt = Integer.parseInt(reader.readLine());
String inputString = reader.readLine();
System.out.println("You entered integer: " + inputInt);
System.out.println("You entered string: " + inputString);
```

## output

### System.out.println

```java
System.out.println("Welcome"); //output string
System.out.print( 
    num1 + " and " + num2 + " is: "); 
InputStreamReader inp = new InputStreamReader(System.in);
System.err.print("Error");
```

> ## Eng：
>
> parameter：形式参数
>
> argument：实际参数
>
> variable：变量

### System.out.print

- prints the text on the console and the cursor remains at the end of the text at the console
- The next printing takes place from just here.

### System.out.println

- prints the text on the console and the cursor remains at the start of the next line at the console
- The next printing takes place from the next line

### Performance Analysis of System.out.println()

- Since println() is a <u>synchronized method</u>, so when multiple threads are passed could lead to the <u>low-performance issue.</u>

## Formatted Output

### use printf

```java
System.out.printf("%,d%n",a); // 10,000
double a = 3.14159265359; 
System.out.printf("%f\n", a); // 3.141593
System.out.printf("%5.3f\n", a); //3.142
System.out.printf("%5.2f\n", a); //  3.14
```

```java
int a = 10; 
Boolean b = true, c = false; 
Integer d = null;   
// Fromatting Done using printf 
System.out.printf("%b\n", a); //true
System.out.printf("%B\n", b); //TRUE
System.out.printf("%b\n", c); //false
System.out.printf("%B\n", d); //FALSE
```

```java
char c = 'g'; 
// Formatting Done 
System.out.printf("%c\n", c); //g
// Converting into Uppercase 
System.out.printf("%C\n", c); //G
```

```java
String str = "GFG"; 
// Vice-versa not possible 
System.out.printf("%S \n", str); //GFG
System.out.printf("%s \n", str); //GFG
```

```java
System.out.printf("current time %tT%n", time);
// Current Time: 11:32:36
System.out.printf("Hours: %tH\nMinutes: %tM\nSeconds: %tS\n",  time,time, time); 
// Hours: 11  Minutes: 32 Seconds: 36
System.out.printf("%1$tH:%1$tM:%1$tS %1$tp %1$tL %1$tN %1$tz %n", time;
// 11:32:36 am 198 198000000 +0000 
```

```java
DecimalFormat ft = new DecimalFormat("####");      
System.out.println("Without fraction part: num = "+ ft.format(num)); 
// Without fraction part: num = 123
ft = new DecimalFormat("#.##");       
System.out.println("Formatted to Give precision: num = "+ ft.format(num));
// Formatted to Give precision: num = 123.46
ft = new DecimalFormat("00000.00"); 
System.out.println("formatting Numeric part : num = "+ ft.format(num)); 
// formatting Numeric part : num = 00123.46
double income = 23456.789;
ft = new DecimalFormat("$###,###.##"); 
System.out.println("your Formatted Dream Income : "+ ft.format(income)); 
// your Formatted Dream Income : $23,456.79
```

## competitive programming

1. **Checking if the number is even or odd without using the `%` operator:**

2. **Fast Multiplication or Division by 2** 

   ```java
   n = n << 1;   // Multiply n with 2
   n = n >> 1;   // Divide n by 2
   ```

3. **Swapping of 2 numbers using XOR:** 

   ```java
   a ^= b;
   b ^= a;
   a ^= b;
   ```

4. **Inbuilt GCD Method**

   ```java
   import java.math.BigInteger; 
   class Test { 
       public static int gcd(int a, int b) 
       { 
           BigInteger b1 = BigInteger.valueOf(a); 
           BigInteger b2 = BigInteger.valueOf(b); 
           BigInteger gcd = b1.gcd(b2); 
           return gcd.intValue(); 
       } 
       public static void main(String[] args) 
       { 
           System.out.println(gcd(3, 5)); //1
           System.out.println(gcd(10000000000L, 600000000L)); //200000000
       } 
   }
   ```

5. **check for a prime number**

   ```java
   BigInteger.valueOf(1235).isProbablePrime(1)
   ```

6. [**Efficient trick to know if a number is a power of 2**]**:**

   ```java
   return x!=0 && ((x&(x-1)) == 0);  
   ```

   

















