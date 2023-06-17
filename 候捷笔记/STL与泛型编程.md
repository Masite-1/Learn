# STL与泛型编程学习笔记

1. ## 模板观念与函数模板

   1. 关键词 template

   ```c++
   template  <typename T> struct Object {...};
   ```

   typename 在子函数中可以替换成 int float char int* class

   声明函数中typename 可用class 替代，但是存在指定意义上的歧义，不建议

   实例化有两种类型

   ​	显式实例化-在代码中明确指定要针对哪种型别进行实例化

   ​	隐式实例化-在首次使用时跟根据具体使情况使用一种合适的型别

   函数模板

   ```c++
   template <typename T>
   inline T Max(
   ​	const T& a,
   ​	const T&b)
   {
   ​	return (a > b )? a:b;
   }
   ```

   

2. ## 类模板与操作符重载

   ```c++
   const std::size_t DefaultStackSize = 1024;
   template <typename T,std::size_t n = DefaultStackSize> class Stack {
   ​	public:
   ​		void Push(const T const& element);
   ​		int Pop(T& element);
   ​		int Top(T& element) const;
   ​	private:
   ​		std::vector<T> m_Members;
   ​		std::size_t m_nMaxSize = n;
   };
   ```

   如果在类模板中需要使用到这个函数本身，比如定义operator= ，那么用应该使用其完整的定义(Stack)而不是省略型别T

   ```c++
   template <typename T,std::size_t n> class Stack
   {
   public:
   ​	...
   ​	Stack (Stack<T,n> const&);						//copy constructor				
   ​	Stack<T>& operatpr = (Stack<T,n> const&);		//assignment operator
   ​	...
   };
   ```

   类模板的实现

   在类外定义一个类模板的成员函数，指明其是一个模板函数

   ```c++
   template <typename T,std::size_t nMaxSize>
   
   void Stack <T，nMaxSize>::Push(const T const& element)
   
   {
   
   ​	if (m_Members.size() >= m_nMaxSize){
   
   ​		//error handing...
   
   ​		//return;	
   
   ​	}
   
   ​	m_Members.push_back(element);
   
   }
   ```

   操作符重载

   操作符重载的一般规则

   ​	不可用operator定义一种新的操作符，比如**

   ​	对于内置型别(built-in type),不能再用operator重载

   ​	操作符重载的两种情况：

   ​		非静态成员函数

   ​		静态全局函数（如果改全局哈桑农户需要访问类的private或protected则须声明为friend成员

   ```c++
   class ComplexType{
   
   public:
   ​	//non-static member
   ​	ComplexType operator<(ComplexType&);
   
   
   ​	//gobal functions
   ​	frienf ComplexType operator+(int, ComplexType&);
   
   };
   ```

   

3. ## 泛型编程

   泛型编程是一种编程方法，这种方法将型别(type)以一种to-be-specified-later给出，等到需要调用的时候，再以参数方式，通过具体的、特定的型别实例化（instance)一个具体的方法或对象

   泛型编程作为一种编程的思想或思维，不依赖于具体的语言

   大多数面向对象的语言(OO languages)都支持泛型

   c++里面的泛型是通过模板以及相关性质表现的

   

   1. traits 特性

      ```c++
      模板类SigmaTraits叫做traits template，它含有其参数型别T的一个特性，即ReturnType
      
      template <typename>
      
      inline typename SignalTraits<T>::Return.Type Sigma(const T const* start,const T const* end)
      
      {
      
      ​	typedef typename SigmaTraits <T>::ReturnType.ReturnType:
      
      ​	ReturnType  s = ReturnType();
      
      ​	while (start != end)
      
      ​		s += *start++;
      
      
      
      ​	return s;
      
      }
      ```

   #### 迭代器(Iterators)：

   迭代器是指针的泛化

   ​	迭代器本身是一个对象，指向另一个可以被迭代的对象

   ​	用来迭代一组对象，即如果迭代器向一组对象中的某个元素，则通过increament以后他就可指向下这组对象中的某个元素

   ​	

   ​	在STL中迭代器是容器与算法之间的接口

   ​		算法通常以迭代器作为输入参数

   ​		容器只要提供一种方式，可以让迭代器访问容器中的元素即可

   ​	

   find算法对于不同的容器，比如vector,list,deque均适用：

   ```c++
   std::vector <int> v(...);
   
   std::list <int> l(...);
   
   std::deque <int> d(...);
   
   
   std::vector<int>::iterator itv = std::find(v.begin(),v,end(),elementToFind);
   
   ...
   
   ...
   
   
   ```
   
   每种容器都有其对应的迭代器
   
   
   
4. ## 容器

5. STL整体结构，仿函数，仿函数适配器，binder1st

6. binder2nd，mem_fun，mem_fun_ref

7. 容器扩展内容

8. 泛型算法_非变易算法

9. 泛型算法_变易算法

10. 泛型算法_排序

11. 泛型算法_数值算法

