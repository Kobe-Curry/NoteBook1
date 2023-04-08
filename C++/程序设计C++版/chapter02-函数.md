# 第二章 函数

## 1 函数定义

> 函数：是一个命名的程序代码块，是程序完成其操作的一种功能单位。
>
> 在程序设计中，有许多算法是通用的，所以会将这类算法定义为一个函数，这样就可以在需要使用的时候直接函数调用就好啦。

### 1.1 语法形式

```cpp
类型标志符 函数名（形式参数表）{
  语句序列
}
```

> `>>` 是提取运算符 

## 2 函数调用

模块化程序设计

### 2.1 循环调用

举例1：

```cpp
//计算x的n次方
double power(double x, int n){
    double val = 1.0;
    while(n--){
        val *= x;
    }
    return val;
}

int main(){
    double pow;
    pow = power(5, 2);
    cout << pow << endl;
    return 0;
}
```

举例2：

```cpp
//判断n是否为回文数
bool symm(unsigned n){
    unsigned i = n;
    unsigned m = 0;
    while(i > 0){
        m = m * 10 + i % 10;
        i /= 10;
    }
    return m == n;
}
```



### 2.2 嵌套调用

```cpp
int fun2(int m){
    return m * m;
}

int fun1(int x, int y){
    return fun2(x) + fun2(y);
}

int main(){
    int a, b;
    cin >> a >> b;
    cout << fun1(a, b) << endl;
}
```



### 2.3 递归调用

```cpp
//计算n的阶乘
unsigned fac(unsigned n){
    unsigned f;
    if(n == 0){
        f = 1;
    }else{
        f = fac(n - 1) * n;
    }
    return f;
}

int main(){
    unsigned m;
    cin >> m;
    cout << fac(m) << endl;
    return 0;
}
```

## 3 引用类型

引用`&`是标识符的别名。

定义一个引用时，必须同时对它进行初始化，使它指向一个已存在的对象。

```cpp
int i,j;
int &ri = i;//定义int引用ri，并初始化为变量i的引用

j = 10;
ri = j;//相当于i = j
```

一旦一个引用被初始化后，就不能改为指向其它对象。

> 引用传递

```cpp
//输入两个整数交换后输出（引用传递）
void my_swap(int &a, int &b){
    int t = a;
    a = b;
    b = t;
}

int main(){
    int x = 5, y = 10;
    my_swap(x, y);
    cout << x << " " << y << endl;
    return 0;
}
```



## 4 含有可变参数

C++标准中提供了两种主要的方法

* 如果所有的实参类型相同，可以传递一个名为initializer_list的标准库类型
* 如果实参的类型不同，我们可以编写可变参数的模板

### 4.1 initializer_list

initializer_list是一种标准库类型，用于表示某种特定类型的值的数组，该类型定义在同名的头文件里

initializer_list提供的操作：

![image-20210404155455201](https://gitee.com/wugenqiang/images/raw/master/02/image-20210404155455201.png)

使用举例：

```cpp
initializer_list<string> ls;//元素类型为string
initializer_list<int> li;//元素类型为int
```

> 注意点：

在编写代码输出程序产生的错误信息时，最好统一用一个函数实现该功能，使得对所有错误的处理能够整齐划一，然而错误信息的种类不同，调用错误信息输出函数时传递的参数也会各不相同。

## 5 内联函数

> 内联函数声明时使用关键字inline

要求：

* 内联函数体内不能有循环语句和switch语句
* 内联函数的定义必须出现在内联函数第一次被调用之前
* 对内联函数不能进行异常接口声明

使用举例：

```cpp
//计算圆的面积
const double PI = 3.14;
inline double calArea(double radius){
  return PI * radius * radius;
}
int main(){
  double r = 3.0;
  double area = calArea(r);
  cout << area << endl;
  return 0;
}
```

## 6 带默认参数值函数

> 可以预先设置默认的参数值，调用时如给出实参，则采用实参值，否则采用预先设置的默认参数值。

```cpp
int add(int x = 5, int y = 6){
  return x + y;
}
int main(){
  add(10, 20);//10+20
  add(10);//10+6
  add();//5+6
}
```



🚨 有默认参数的形参必须列在形参列表的最右，即默认参数值的右面不能有无默认值的参数。



## 7 函数重载

C++允许功能相近的函数在相同的作用域内以相同函数名声明，从而形成重载。



举例：

```cpp
int add(int a, int b){
  return a + b;
}

double add(double a, double b){
  return a + b;
}
```



## 8 系统函数

C++的系统库中提供了几百个函数可供程序员使用，例如：

* 求平方根函数sqrt
* 求绝对值函数abs

使用系统函数时要包含相应的头文件，例如：

* cmath

```cpp
#include <cmath>
```

































