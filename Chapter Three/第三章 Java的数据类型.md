# 第三章 Java的数据类型
## 数据类型
1. 程序当中有很多数据，每一个数据都是相关类型的，不同数据类型的数据占用空间大小不同。
2. 数据类型的作用是指导JVM在运行程序的时候给该数据分配多大的内存空间。
3. java中的数据类型包括两种：基本数据类型和引用数据类型【后边讲】【类、接口、数组...】。
4. 基本数据类型包括四大类八小种。
```
1. 第一类：整数型
   byte、short、int、long
2. 第二类：浮点型
   float，double
3. 第三类：布尔型
   boolean
4. 第四类：字符型
   char
```
5. 字符串不属于基本数据类型，属于引用数据类型，字符属于基本数据类型。
6. 字符串使用双引号，字符使用单引号。
```
1. "abc" 字符串
2. 'a' 字符
```
7. 八种基本数据类型占用的空间大小

|基本数据类型|占用空间大小【单位：字节】|
|--|--|
|byte|1|
|short|2|
|int|4|
|long|8|
|float|4|
|double|8|
|boolean|1|
|char|2|

8. 计算机在任何情况下只能识别二进制。
9. 二进制是数据的一种表示形式。十进制表示满十进一原则。二进制表示满二进一原则。
10. 字节(byte)：1 Byte = 8 bit 【1个字节=8个比特位】
11. 一个比特位表示一个二进制位：1/0
12.1KB = 1024Byte;1MB = 1024KB;1GB = 1024MB;1TB = 1024GB
13. 关于java中的数字类型，数字都是有正负之分的，所以在数字的二进制当中有一个二进制位被称为“符号位”。并且这个“符号位”在所有二进制位的最左边。0表示正数，1表示负数。byte类型最大值：01111111
14. 二进制和十进制的转换规则：
```
- 二进制转十进制
111->7
- 十进制转二进制
97->1100001
```
15. byte类型取值范围：[-128, 127]，byte类型可以表示256个不同的数字。【256个不同的二进制】
16. 在八种基本数据数据类型当中，byte，short，int，long，float，double，boolean这七种数据类型计算机在表示的时候比较容易，因为底层都是数字，十进制的数字和二进制之间存在一种固定的转换规则。

### 字符编码
1. 八种基本数据数据类型当中，char类型表示的是现实世界中的文字，文字和计算机二进制之间，默认情况下是不存在任何转换关系的。
2. 为了让计算机可以表示现实世界当中的文字，我们需要进行人为的干涉，需要人提前制定好“文字”和“二进制之间的对照关系”。这种对照转换关系被称为：字符编码。
3. 计算最初只支持英文，最先出现的字符编码是ASCII码【采用一个字节编码】。
```
'a'->97【01100001】
'A'->65
'0'->48
'a'--(按照ASCII解码)--> 01100001
01100001 --(按照ASCII编码)--> 'a'
注意：编码和解码时候采用同一套字典/对照表，不会出现乱码。当编码和解码时候采用的不是同一套字典/对照表，会出现乱码。
```
4. 随着计算机的发展，后来出现了一种编码方式，是国际化标准组织ISO制定的，这种编码方式支持西欧语言，向上兼容ASCII码，仍然不支持中文。这种编码方式是ISO-8859-1，又被称为latin-1。
5. 随着计算机向亚洲发展，计算机开始支持中文、日文、韩文等国家文字，其中支持简体中文的编码方式：GB2312、GBK、GBK18030。【容量：GB2312<GBK<GBK18030】。
6. 支持繁体中文的编码方式：大五码<big5>。
7. 后来出现了一种编码方式统一了全球所有的文字，容量较大，这种编码方式叫做unicode编码。unicode编码方式有多种具体实现：UTF-8、UTF-16、UTF-32。
8. java语言源代码采用的是unicode编码，所以“标识符”可以用中文。
9. 现在在实际开发中，一般使用UTF-8编码方式较多。【统一编码方式】

### 八种基本数据类型的取值范围

|基本数据类型|取值范围|默认值|
|--|--|--|
|byte|[-128, 127]|0|
|short|[-32768, 32767]|0|
|int|[-2147483648, 2147483647]|0|
|long|[-2^63, 2^63-1]|0|
|float|有效位数6~7位|0.0|
|double|有效位数15位|0.0|
|boolean|[true, false]|false【true是1，false是0】|
|char|[0, 65535]|\u0000|

1. 举例
```
/*
* @Author: StudentCWZ
* @Date:   2020-06-07 08:56:27
* @Last Modified by:   StudentCWZ
* @Last Modified time: 2020-06-07 09:03:03
*/


public class DataTypeTest01
{
  //这里static必须加
  static int k = 1000;

  //变量还是遵循这个语法：必须先声明，再赋值，才能访问。
  //成员变量没有手动赋值，系统会默认赋值。【局部变量不会】
  static int f; //成员变量

  public static void main(String[] args){
    /*
    int i;//局部变量
    System.outprintln(i);
    */
    System.out.println(k);
    System.out.println(f);//0

  }
}
```
2. 八种基本数据类型的默认值一切向0看齐。
3. 以下java程序主要讲解的是数据类型之一：char类型。
```
/*
* @Author: StudentCWZ
* @Date:   2020-06-07 09:03:57
* @Last Modified by:   StudentCWZ
* @Last Modified time: 2020-06-07 09:04:38
*/



public class DataTypeTest02
{
  public static void main(String[] args){
    //定义一个char类型的变量，起名c，同时赋值字符'a'
    char c = 'a';
    System.out.println(c);

    //一个中文占用2个字节，char类型正好是两个字节
    //所以java中的char类型变量可以存储一个中文字符
    char x = '国';
    System.out.println(x);

    //编译错误
    //ab是字符串，不能使用单引号括起来
    //char y = 'ab';

    //"a"是字符串类型
    //k变量是char类型
    //类型不兼容，编译错误
    //char k = "a";

    //声明
    char e;

    //赋值
    e = 'e';
    System.out.println(e);

    //再次赋值
    e = 'f';
    System.out.println(e);
  }
}
```
### 转义字符
1. 举例
```
/*
* @Author: StudentCWZ
* @Date:   2020-06-07 09:05:58
* @Last Modified by:   StudentCWZ
* @Last Modified time: 2020-06-07 09:07:42
*/


public class DataTypeTest03
{
  public static void main(String[] args){

    //普通的n字符
    char c1 = 'n';
    System.out.println(c1);

    //依照目前所学知识，以下程序无法编译通过，因为显然是一个字符串，不能用单引号括起来
    //但是经过编译发现，发现编译通过，这说明以下并不是一个字符串，而是一个字符。
    //这是一个换行符，属于char类型的数据。
    //反斜杠在java语言当中具有转义功能。
    char c2 = '\n';

    /*
    System.out.println("Hello");
    System.out.println("World!");
    */

    //System.outprintln();和System.outprint();的区别：println表示输出之后换行，print表示输出，但是不换行。
    /*
    System.out.print("Hello");
    System.out.println("World!");
    */

    System.out.print("A");
    System.out.print(c2);
    System.out.println("B");

    //普通的t字符
    char x = 't';
    System.out.println(x);

    //制表符Tab
    //强调制表符和空格不同，它们ASCII码不一样，体现在键盘两个不同的按键。
    char y = '\t';
    System.out.print("A");
    System.out.print(y);
    System.out.println("B");

    //要求在控制台上输出“反斜杠字符”。
    //反斜杠将后面的单引号转义成不具备特殊含义的普通单引号字符，左边的单引号缺少了结束的单引号字符，编译报错。
    /*
    char k = '\';
    System.outprintln(k);
    */

    /*
      //解释：第一个反斜杠具有转义功能，将后面的反斜杠转义为普通的反斜杠字符。
      //结论：在java当中两个反斜杠代表一个普通的反斜杠。
    */
    char k = '\\';
    System.out.println(k);


    //在控制台上输出一个普通的单引号字符
    //java不允许这样编写程序，编译报错
    //char a = '';

    //以下编译报错：第一个单引号和第二个单引号配对，最后的单引号找不到另一半。
    //char a = ''';
    //System.outprintln(a);

    //反斜杠具有转义功能，将第二个单引号转换成普通的单引号字符，第一个单引号和最后单引号配对。
    char a = '\'';
    System.out.println(a);


    char f = '"';
    System.out.println(f);


    System.out.println("HelloWorld!");
    System.out.println("“HelloWorld!”");
    //编译错误
    //System.outprintln(""HelloWorld!"");
    //纠正
    System.out.println("\"HelloWorld!\"");


    char m = '中';
    System.out.println(m);

    //JDK自带的native2ascii.exe命令，可以将文字转换成unicode编码形式。
    //怎么使用这个命令：在命令行输入native2ascii，回车，然后输入文字回车即可得到unicode编码。

    char n ='\u4e2d';//"中"对应的unicode编码是4e2d
    System.out.println(n);

    //编译错误
    //char g = '4e2d'
    //编译错误
    //char g = 'u4e2d'
    //编译通过：反斜杠u联合起来后面一串数字是某个文字的unicode编码。
    char g = '\u4e2d';
    System.out.println(g);

    //char类型的默认值
    char c10 = '\u0000';
    System.out.println(c10);
  }
}
```
2. 转义字符出现在特殊字符之前，会将特殊字符转换成普通字符。
3. 转义字符的含义

|转义字符|含义|
|--|--|
|\n|换行符|
|\t|制表符|
|\'|普通的单引号|
|\"|普通的双引号|
4. 各种进制
```
十进制：0 1 2 3 4 5 6 7 8 9 10 11...
二进制：0 1 10 11 100 101...
十六进制：0 1 2 3 4 5 6 7 8 9 a b c d e f 10 11 12 13 14 15 16 17 18 19 1a 1b 1c 1d 1e 1f 20...
八进制：0 1 2 3 4 5 6 7 10 11 12 13 14 15 16 17 20...
```
### 整数型
1. 整数型的数据分类

|数据类型|占用空间大小|默认值|取值范围|
|--|--|--|--|
|byte|1|0|[-128, 127]|
|short|2|0|[-32768, 32767]|
|int|4|0|[-2147483648, 2147483647]|
|long|8|0|[-2^63, 2^63-1]|
2. java语言当中的“整数型字面值”被默认当做int类型来处理。要让这个“整数型字面值”被当做long类型来处理的话，需要在“整数型字面值”后面添加l/L，建议使用大写的L。
3. java语言当中整数型字面值有三种表达方式：
```
1. 第一种方式：十进制【是一种缺省默认的方式】
2. 第二种方式：八进制【在编写八进制整数型字面值的时候需要以0开始】
3. 第三种方式：十六进制 【在编写十六进制整数型字面值的时候需要以0x开始】
```
4. 举例
```
/*
* @Author: StudentCWZ
* @Date:   2020-06-07 09:09:21
* @Last Modified by:   StudentCWZ
* @Last Modified time: 2020-06-07 09:10:35
*/


public class DataTypeTest04
{
  public static void main(String[] args){

    int a = 10;
    int b = 010;//整数型字面值以0开头的，后面那一串数字就是八进制形式
    int c = 0x10;//整数型字面值以0x开头的，后面那一串数字就是s十六进制形式


    System.out.println(a);//10
    System.out.println(b);//8
    System.out.println(c);//16

    System.out.println(a + b + c);//34

    //123这个整数型字面值是int类型
    //i变量声明的时候也是int类型
    //int类型的123赋值给int类型的变量i，不存在类型转换
    int i = 123;
    System.out.println(i);


    //456整数型字面值被当做int类型，占用4个字节
    //x变量在声明的时候是long类型，占用8个字节
    //int类型的字面值456赋值给long类型的变量x，存在类型转换
    //int类型转换成long类型
    //int类型是小容量
    //long类型是大容量
    //小容量可以自动转换成大容量，称为自动类型转换机制
    long x = 456;
    System.out.println(x);


    //2147483647字面值是int类型，占用4个字节
    //y是long类型，占用8个字节，自动类型转换
    long y = 2147483647;
    System.out.println(y);


    //编译错误：过大的整数：2147483648
    //2147483648被当做int类型四个字节处理，但是这个字面值超出int类型范围
    //long z = 2147483648;


    //解决错误
    //2147483648字面值一上来就当做long类型来处理，在字面值后面添加L
    //2147483648L是八个字节的long类型
    //z是long类型变量，以下程序不存在类型转换
    long z = 2147483648L;
    System.out.println(z);
  }
}
```
5. 举例
```
/*
* @Author: StudentCWZ
* @Date:   2020-06-09 09:48:35
* @Last Modified by:   StudentCWZ
* @Last Modified time: 2020-06-09 10:00:38
*/


public class DataTypeTest05
{
  public static void main(String[] args){

    //100L是long类型字面值
    //x是long类型变量
    //不存在类型转换，直接赋值
    long x = 100L;

    //x变量是long类型，8个字节
    //y变量是int类型，4个字节
    //编译报错，大容量不能直接赋值给小容量
    //in y = x;

    //大容量转换成小容量，需要进行强制类型转换
    //强制类型转换需要加“强制类型转换符”
    //加上强制类型转换符之后编译通过了，但是运行阶段可能会损失精度。
    //所以强制类型转换谨慎使用，因为损失精度后，可能损失很严重。


    //强转原理：
      //原始数据：00000000 00000000 00000000 00000000 00000000 00000000 00000000 01100100
      //强转之后的数据：00000000 00000000 00000000 01100100
      //将左边的二进制砍掉【所有数据强转的时候都是这样完成的】
    int y = (int)x;
    System.out.println(y);


    //原始数据：00000000 00000000 00000000 00000000 10000000 00000000 00000000 00000000
    //强转之后的数据：10000000 00000000 00000000 00000000 目前存储在计算机内部，计算机存储数据都是采用补码的形式存储。
    //所以10000000 00000000 00000000 00000000是一个补码形式
    //将以上的补码转换到原码，就是最终的结果。
    long k = 2147483648L;
    int e = (int)k;
    System.out.println(e);//损失精度非常严重，结果是负数。


    //根据目前所学内容，以下程序是无法编译通过
    //理由：50是int类型的字面值，b是byte类型的变量，显然是大容量int转换成小容量byte
    //大容量转换成小容量是需要添加强制类型转换符的，以下程序没有添加强转符号，所以编译报错。
    //但是，在实际编译的时候，以下代码编译通过了，这说明：在java语法当中，当一个整数型字面值没有超出byte类型的取值范围，该字面值可以直接赋值给byte类型变量。
    byte b = 50;//可以

    byte c = 127;//可以

    //编译报错，128这个int类型字面值已经超出了byte类型的取值范围，不能直接赋值给byte类型的变量
    //byte b1 = 128;//不可以

    //纠正错误，需要使用强制类型转换符
    //但是一定会损失精度
    //原始数据：00000000 00000000 00000000 10000000
    //强转之后：10000000【这是存储在计算机内部的，这是一个补码】
    byte b1 = (byte)128;
    System.out.println(b1);//-128

    /*
      计算机二进制有三种表示方式：
        原码
        反码
        补码
      计算机在任何情况下底层表示和存储数据的时候采用了补码形式。
      正数的补码：和原码相同
      负数的补码：负数的绝对值对应的二进制码所有二进制取反，再加1

      补码：10000000
      原码的计算过程：
        * 10000000 - 1--> 01111111
        * 01111111-->10000000-->128
        * -128
    */

    //原始数据：00000000 00000000 00000000 11000110
    //强转之后：11000110
    //11000110现在在计算机当中存储，它是一个补码，将补码转换成原码就是该数字。
    //11000110 - 1 --> 11000101
    //00111010 --> 58
    //-58
    byte m = (byte)198;
    System.out.println(m);//-58

    //short s = 32767;//通过
    //short s1 = 32768;//编译报错

    //65535是int类型，4个字节
    //cc是char类型，2个字节
    //按照以前所学知识点来说，以下程序是编译报错的。
    //char cc = 65535; //通过
    //char cc = 65535; //编译报错

    /*
      当一个整数字面值没有超出byte,short,char的取值范围，这个字面值可以直接赋值给byte，short，char类型的变量。这种机制SUN允许了，目的是为了方便程序员的编程。
    */

  }
}
```
### 浮点型
1. 浮点型数据类型：float和double。
2. float 单精度 【4个字节】
3. double 双精度 【8个字节】
4. double精度太低了【相对来说的】，不适合做财务软件。财务涉及到钱的问题，要求精度较高，所以SUN在基础SE类库当中为程序员准备了精确度更高的类型，只不过这种类型是一种引用数据类型，不属于基本数据类型，它是：java.math.BigDecimal。
5. 其实java程序中SUN提供了一套庞大的类库，java程序员是基于这套基础的类库来进行开发的。
```
* SE类库字节码：C:\Program Files (x86)\JAVA\jdk1.7.0_75\jre\lib\rt.jar
* SE类库源码：C:\Program Files (x86)\JAVA\jdk1.7.0_75\src.zip
```
6. 在java语言当中，所有的浮点型字面值，默认被当做double类型来处理，要想该字面值当做float类型来处理，需要在字面值后面添加F/f。
7. 举例
```
/*
* @Author: StudentCWZ
* @Date:   2020-06-09 10:01:09
* @Last Modified by:   StudentCWZ
* @Last Modified time: 2020-06-09 10:02:30
*/


public class DataTypeTest06
{
  public static void main(String[] args){

    //3.0是double类型的字面值
    //d是double类型的变量
    //不存在类型转换
    double d = 3.0;
    System.out.println(d);


    //5.1是double类型的字面值
    //f是float类型的变量
    //大容量转换成小容量需要加强类型转换符，所以以下程序编译错误。
    //float f = 5.1;


    //解决方案：
    //第一种方式：强制类型转换
    //float f = (float)5.1;

    //第二种方式：没有类型转换
    float f = 5.1f;

  }
}
```
8. double和float在计算机内部二进制存储的时候存储的都是近似值。
### 布尔型
1. 在java语言当中，boolean类型只有两个值：true、false，没有其他值。不像c语言当中，0和1可以表示假和真。
2. 在底层存储的时候，boolean类型占用1个字节，因为实际存储的时候false底层是0，true底层是1。
3. 布尔型在实际开发当中非常重要，经常使用在逻辑运算和条件控制语句当中。
4. 举例
```
/*
* @Author: StudentCWZ
* @Date:   2020-06-09 10:04:47
* @Last Modified by:   StudentCWZ
* @Last Modified time: 2020-06-09 10:06:04
*/

public class DataTypeTest07
{
  public static void main(String[] args){

    //编译错误，不兼容的类型
    //boolean flag = 1;

    boolean loginSuccess = true;
    //if语句以后讲【条件控制语句】
    if(loginSuccess){
      System.out.println("恭喜你，登陆成功");
    }else{
       System.out.println("对不起，用户名不存在或者密码错误");
    }
  }
}
```
### 基本数据类型的相互转换
1. 基本数据类型之间的转换规则
```
1. 八种基本数据类型当中除了布尔类型之外剩下的7种类型之间都可以相互转换。
2. 小容量向大容量转换，称为自动类型转换，容量从小到大排序：byte<short(char)<int<long<float<double【注意：任何浮点类型不管占用多少个字符，都比整数型容量大。char和short可表示的种类数量相同，但是char可以取更大的正整数。】
3. 大容量转换成小容量，叫做强制类型转换，需要加强制类型转换符，程序才能编译通过，但是在运行阶段可能会损失精度，所以谨慎使用。
4. 当整数字面值没有超出byte、short、char的取值范围，可以直接赋值给byte、short、char类型变量。
5. byte、short、char混合运算的时候，各自先转换成int类型在做运算。
6. 多种数据类型混合运算，先转换成容量最大的那种类型再做运算。
```
2. 举例
```
/*
* @Author: StudentCWZ
* @Date:   2020-06-09 10:10:06
* @Last Modified by:   StudentCWZ
* @Last Modified time: 2020-06-09 10:10:18
*/

public class DataTypeTest08
{
  public static void main(String[] args){

    //出现错误，1000超出了byte的范围
    //byte a = 1000;
    //正确，因为20没有超出byte的范围
    //所以赋值
    byte a = 20;
    //变量名不能重名
    //short a = 1000;
    //正确，因为数值1000没有超出short类型的范围
    //所以赋值正确
    short b = 1000;
    //正确，因为默认就是int，并且没有超出int类型
    int c = 1000;
    //正确，可以自动转换
    long d = c;
    //错误，出现精度丢失问题，大类型-->小类型会出现问题
    //int e = d;
    //将long强制转换成int类型
    //因为值1000，没有超出int范围，所以转换是正确的。
    int e = (int) d;
    //因为java中运算会转成最大类型。
    //而10和3默认值为int，所以运算后最大的类型也是int
    //所以是正确的
    int f = 10/3;//3
    //声明10为long类型
    long g = 10;
    //出现错误，多个数值在运算过程中，会转换成容量最大的类型
    //以下示例最大的类型为double，而h为int，所以就会出现大类型(long)到小类型(int)的转换，将会出现精度丢失的问题。
    //int h = g/3；
    //可以强制转换，因为运算结果没有超出int范围
    //int h = (int) g/3;
    //可以采用long类型来接收运算结果
    //long h = g/3;
    //出现精度损失问题，以下问题主要是优先级的问题
    //将g转换成int，然后又将int类型的g转换成byte，最后byte类型的g和3运算，那么它的运算结果类型就是int，所以int赋值给byte就出现了精度损失问题。
    //byte h = (byte)(int)g/3;
    //正确
    //byte h = (byte)(int)(g/3);
    //不能转换，因为优先级的问题
    //byte h = (byte)g/3;
    //可以转换，因为运算结果没有超出byte范围
    //byte h = (byte)(g/3);
    //可以转换，因为运算结果没有超出short范围
    short h = (short)(g/3);
    short i = 10;
    byte j = 5;
    //错误，short和byte运算，首先会先转换成int再运算
    //所以运算结果为int，int赋值给short就会出现精度丢失问题
    //short k = i + j;
    //可以将运行结果强制转换成short
    //short k = short(i + j);
    //因为运算结果为int，所以可以采用int类型接收
    int k = i + j;
    char l = 'a';
    System.out.println(l);//a
    //输出结果为97，也就是a的ascii值
    System.out.println((byte)l);//97
    int m = l + 100;
    //输出结果为197，取得a的ascii码值，然后与100进行相加运算
    System.out.println(m);
  }
}
```
