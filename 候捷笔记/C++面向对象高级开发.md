# C++面向对象高级开发学习笔记

1. ## C++编程介绍

   1. 

2. ## 头文件与类的声明

   1. ```c++
      complex.h										//	guard（防卫式声明）
      
      #ifndef _complex_
      #define _complex_
      
      #include <cmatch>								//forward declarations 前置声明
      
      class ostream;
      class complex;
      
      complex&										//class declarations 类-声明
      	_doapl (complex* ths, const complex& r)
      class complex
      {
      	...
      };
      
      complex::function ...							//class definition 类-定义
      
      #endif
      ```

      保证头文件内的引用不重复

   2. 引用方式

      ```c++
      #include "complex.h"
      ```

      

3. ## 构造函数

   1. ```c++
      class complex
      
      {
      
      public:
      
      ​	complex (double r= 0 ,double i = 0):re (r), im (i) {}		//初值类，初始列
          
      private:
          double re, im;
      } 						//构造函数的特殊语法，必会
      ```

      构造函数不需要返回类型，只是用来创建对象

4. ## 参数传递与返回值

5. ## 操作符重载与临时对象

6. ## 复习Complex类的实现过程

7. ## 三大函数：拷贝构造，拷贝复制，析构

   1. ```c++
      	class String 
      
      ​	{
      
      ​	public:
      
      ​		String (const char* cstr = 0 );  	//构造函数
      
      ​		String (const String& str); 		//拷贝构造函数
      
      ​		String& operator = (const String& str);		//拷贝赋值函数
      
      ​		~String ();							//析构函数
      
      ​	}	
      ```

      *定义的类中包含指针一定要写明拷贝构造&拷贝赋值函数

8. ## 堆，栈与内存管理

   

9. ## 复习String类的实现过程

10. ## 扩展补充：类模板，函数模板，及其他

11. ## 组合与继承

12. ## 虚函数与多态

13. ## 委托相关设计











