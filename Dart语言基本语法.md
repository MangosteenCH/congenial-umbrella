# Dart语言基本语法

note



- ## 数据类型

- 变量与常量

  ```dart
  void main(){
    //var 声明变量
    //const 声明常量
    var a;
    print(a);
  
    a = 10;
    print(a);
  
    a = "string";
    print(a);
  
    var b = 20;
    print(b);
  
    final c = 30;//不可改变值
    //c = 2;//此句报错
  
    const DELAY = 3;//定义常量
    //n = 4;//此句报错
  }
  ```

  一般“const”用来定义常量，通常常量的引用使用全大写！

- 内置类型

  ---

  - 数值型-Number

    ---

    - 语法

      num=>int & double

      dart中只有这两种数值型，int和double都可以用num来表示,因为int和double都是继承于num的

      ```dart
      num a = 4;
      a = 16.4;
        
      int b  = 33;
      //b = 45.9;//此句报错！error: A value of type 'double' can't be assigned to a variable of type 'int'. (invalid_assignment at data_type_number.dart:6)
        
      double c = 33.3;
      //c = 3;//此句报错！error: A value of type 'int' can't be assigned to a variable of type 'double'. (invalid_assignment at data_type_number.dart:9)
        
      ```

      num是一个抽象类

      ```dart
      abstract class num implements Comparable<num> {...}
      ```

      int & double继承了num类

      ```dart
      abstract class int extends num {...}
      ```

      ```dart
      abstract class double extends num {...}
      ```

    - 操作

      - 运算符：+、-、*、/、~/、%

        /：表示直接相除结果为浮点型

        ~/：相除向下取整

        %：相除取余

      - 常用属性

        isNaN、isEven、isOdd   //是否是非数字、是否是偶数、是否是奇数

        (0.0/0.0)是一个NaN

      - 常用方法

        ```dart
        a.abs();//绝对值
        a.round();//四舍五入
        a.floor();//不大于a的最大整数
        a.ceil();//不小于a的最小整数
        a.toInt();//转化成int型
        a.toDouble();//转化成double型
        ```

  - 字符串-String

    ---

    - 语法

      - 使用单引号/双引号创建字符串

      - 使用三引号或双引号创建多行字符串

      - 使用 r 创建原始 raw 字符串

      ```dart
      void main() {
        //单引号
        String string1 = 'nihoa';
        //三引号创建多行字符串
        String string2 = '''hihoaya
      jkdjsfssf''';
        print(string2);
        //双引号创建多行字符串
        String string = "nihao \n sfs";
        print(string);
        //r字符创建原始字符串
        string = r"nihao \n sfs";
        print(string);
      }
      ```

      " \n "转义字符，用来换行，“ r ”字符屏蔽了转义字符的“ \n ” 

    - 操作

      - 运算符：+、*、==、[]

        +：连接字符串

        *： *号后面跟一个数字，代表原字符串重复次数，可理解为多个原字符串进行+

        ==：判断字符串是否相等

        []：取出字符串中字符，下标从0开始

      - 插值表达式：${expression}

        用作将表达式的值插入字符串

        ```dart
        int a = 3;
        int b = 5;
        print("a + b = ${a + b}");
        
        /*console:
        a + b = 8
        */
        ```

      - 常用属性

        length、isEmpty、isNotEmpty   //长度，是否为空字符

      - 常用方法

        ```dart
        a.contains(String str);//是否包含字符串str
        a.subString(int x,int y);//取出字符串，从第x下标开始取出y位
        
        a.startWith(String str);//以str开头
        a.endWith(String str);//以str结尾
        
        a.indexOf(String str);//是否包含str
        a.lastIndexOf(String str);//是否包含str，并返回下标
        
        a.toLowerCase();//大小写转化
        a.toUpperCase();
        
        a.trim();//添加空格
        a.trimLeft();
        a.trimRight();
        
        a.split(String str);//使用str来分隔字符串，一般使用空格来分隔字符，所以str = ' '，分隔后返回一个列表数组
        a.replaceXXX(String str1,String str2);//替换,将str1替换为str2
        ```


  - 布尔型-Boolean

    ---

    - 语法

      ```dart
      bool flag = true;//关键字是bool不再是boolean
      ```

      注意关键字有微小不同！

  - 列表-List（数组）

    ---

    - 语法

      三种创建方式

      ```dart
      var list = [1,2,3];//枚举型创建数组
      
      var list = const [1,2,3];//枚举型创建常量数组
      
      var list = new List();//利用面性对象的构造函数创建List对象
      ```

      在使用var来定义数组时，数组内部的元素可以不是同一种类型，但必须是变量，这跟使用var定义有很大关系

    - 操作

      - 属性：

        `[]、length //获得元素和长度`

      - 方法：

        ```dart
        list.add(xxx);//在数组后添加元素
        list.insert(1,"java");//插入元素
        
        list.remove(2);//移除制定下标元素
        list.clear();//清空数组
        
        list.indexOf("dart");//返回指定元素的下标，不存在就返回-1
        list.lastIndexOF("dart");//反向查找
        
        list.sort();//低到高排序，0~9、a~Z
        list.sublist(1);//截取元素，返回从制定下标开始的数组
        
        list.shuffule();
        list.asMap();//转换时，下标：key，元素：value
        list.forEach(具体方法);//取出list中每一个元素丢进传入的方法运行
        ```

  - 键值对-Map

    ---

    - 语法

      ```dart
      var lan = {'first':'java','scend':'dart',1:true,2:5};
      
      var lan1 = const {'first':'java','scend':'dart'};
      
      var lan11 = new Map();
      
      print(lan[first]);//通过键获取值
      ```

    - 操作

      - 属性

        length、keys、values：长度、所有键、所有值

      - 方法

        ```dart
        map.isEmpty();
        map.isNotEmpty();
        
        map.containsKey(xxx);//key中是否包含xxx
        map.containsValue(xxx);//value中是否包含xxx
        
        map.remove(键);//就是移除呗，指定键，则移除一对键值
        
        map.forEach(f);//同list的forEach，在此具体演示了
        void f(key,value){
            print("key=$key,value=$value");
        }
        ```

- dynamic

  ---

  动态类型。。。      - _ -||

  代表可以是各种类型，可用在泛型的地方

  - Runes/Symbols

    ---

    不常用，用到再说

- ## 条件表达式

  - ### 三目运算符：condition ? expr1 : expr2`//同三元运算符`

  - ### ？？运算符：expr1 ?? expr2`//如果第一个表达式值为空(NULL)则使用第二个表达式的值`

- ## 循环语句

  - ### 传统for循环——不用多说

  - ### for-in

    ```dart
    for(var item in list){
        print(item);
    }
    ```

    类似与java中的增强型for循环：

    ```java
    for(int i : list){
        System.out.print(i);
    }
    ```

- ## 方法定义

  ```dart
  返回类型 方法名 （参数1，参数2，...）｛
  	方法体...
      return 返回值
  ｝
  ```

  main函数是有入口参数的，其入口参数是一个List，给这个list传值时需要在命令行进行操作！

  在命令行运行dart文件时与运行java文件类似，但是不需要编译（！！！），如下：

  ```
  D:\IdeaStation\DartPro\dart01> dart function.dart 1 true "ddsaf"
  ```

  注意：在命令行使用dart命令需要首先在环境变量中配置dartSDK的bin路径！！！

  - ### 方法特性

    - 方法也是对象，并且具有具体类型：Function

    - **返回值类型和参数类型都可以省略**

    - 箭头语法（java 蓝不大表达式）：`=>expr`是`{return expr;}`的缩写。只适用于一个表达式

    - 方法都有返回值。如果没有指定（void），默认`return null`最后一句执行

    - #### 可选参数

      - 可选命名参数：{param1,param2,...}

        基于命名的可变参数：使用**可变**参数时，要通过名称来指定！

      - 可选位置参数：[param1,param2,...]

        调用时不需要通过名称来指定，但是基于位置的可变参数是**无法跳参数传参的**！

      - **可选参数必须至于正常参数之后**

      ```dart
      void main(){
          printPerson("张三");
          printPerson("李四",age:35);//必须要写为`age:`形式！！！
          printPerson("zhangsan",age:34,gender"ddd");
          printPerson("zhangsan",gender:"ddd");//跳参数传参，具有更高的灵活性
          
          printPerson1("zhangsan");
          printPerson1("zhangsan",34);
          printPerson1("zhangsan",34,"ddd");//不可跳参数传参，具有更强的规范性
      }
      //基于命名的可变参数
      printPerson(String name,{int age,String gender}){
          print("name=$name,age=$age,gender=$gender");
      }
      //基于位置的可变参数
      printPerson1(String name ,[int age ,String gender]){
        print("name=$name,age=$age,gender=$gender");
      }
      ```

      - 默认参数值

        使用“=”来给可选参数设置默认参数值

        ```dart
        printPerson(String name,{int age = 30,String gender = "Female"}){
            print("name=$name,age=$age,gender=$gender");
        }
        ```

  - ### 方法对象

    - 方法可以作为对象赋值给其他变量

      ```dart
      void main(){
          var func = printHello;
          Function func1 = printHello;
          
          func();//此句会打印出Hello
          func1();//同样
      }
      
      void printHello(){
          print("Hello");
      }
      ```

    - 方法也可以作为参数传递给其他方法

      ```dart
      void main(){
          var list = [1,2,3,4];
      	list.forEach(print);
      
      	var list2 = ["h","e","l","l","o"];
          listTimes(list2,times);//out:[hhh, eee, lll, lll, ooo]
      }
      
      List listTimes(List list,String times(str)){
          for(var index = 0;index <list.length;index++){
              list[index] = times(list[index]);
          }
          return list;
      }
      String times(str){
          return str*3;
      }
      ```

- ## 匿名方法

  ```
  (参数1，参数2，...){
      方法体...
      return 返回值
  }
  ```

  - ### 匿名方法特性

    - 可复制给变量，通过变量进行调用
    - 可在其他方法中直接调用或传递给其他方法

    ```dart
    void main(){
        //1。
        var func = (str){
            print("Hello--$str");
        };//定义一个匿名方法并将其赋给func
        func(30);//调用
    
        //2.
        ((){
            print("Test");
        })();//以(匿名方法)();的方式来调用，不推荐使用！
        
        //3.
        var list2 = ["h","e","l","l","o"];
        listTimes(list2,(str){return str*3;});
    }
    
    List listTimes(List list,String times(str)){
        for(var index = 0;index <list.length;index++){
            list[index] = times(list[index]);
        }
        return list;
    }
    ```

- ## 闭包

  - 闭包是一个方法（对象）
  - 闭包定义在其他方法内部
  - **闭包能够访问外部方法内的局部变量并持有其状态**





