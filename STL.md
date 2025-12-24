# Keywords

- `constexpr`

  1. C++11 引入的关键字，表示**常量表达式**
  2. 用于修饰变量、函数等，表示其值在==编译期就能确定==
  3. 是一个==**编译期常量**==，可以用于编译期判断和模板元编程。
  4. 相比 `const`，`constexpr` 要求初始化表达式在编译期就能求值

- `using`

  1. C++11 的==**类型别名声明**==

  2. 作用和 `typedef` 类似，但语法更现代、功能更强

  3. e.g

     ```c++
     using T = typename std::iterator_traits<Iter>::value_type;
     ```

     - 这里定义了一个类型别名`T`,代表 `std::iterator_traits<Iter>::value_type`。
     - 这样就可以用 `T`来代替复杂的类型名
     - 注意: 此处一定要写`typename`, 因为在模板中，编译器无法确定 `value_type` 是类型还是静态成员，必须用 `typename` 显式告诉编译器它是类型

# Traits

## 模板偏特化

```c++
template <typename T>
struct is_pointer {
    static constexpr bool value = false;
};

template <typename T>
struct is_pointer<T*> {
    static constexpr bool value = true;
};
```

- `is_pointer`：这是主模板，适用于所有类型T（如 `int`, `double`, `char` 等），`value`为 `false`。
- `is_pointer`：这是对指针类型的**`偏特化`**，只适用于指针类型（如 `int*`, `char*` 等），`value` 为 `true`。

## std::iterator_traits

```c++
template <typename Iter>
void print_value_type(Iter it) {
    // 从 traits 中提取迭代器的 value_type
    using T = typename std::iterator_traits<Iter>::value_type;
    std::cout << typeid(T).name() << "\n";
}

int main() {
    std::vector<int> v{1, 2, 3};
    print_value_type(v.begin());   // 输出 int
    int* p = v.data();
    print_value_type(p);           // 输出 int （即使是原生指针也能用）
}
```

- `iterator_traits`可以萃取`it`的类型, 就不需要在调用时显式指定参数类型, 比如下述这样: 

  ```c++
  template <typename Iter>
  void print_value_type() {
      using T = typename std::iterator_traits<Iter>::value_type;
      std::cout << typeid(T).name() << "\n";
  }
  
  int main() {
      std::vector<int> v{1, 2, 3};
      print_value_type<std::vector<int>::iterator>(); // 必须手动指定类型
      print_value_type<int*>();                       // 必须手动指定类型
  }
  ```

- > `iterator_traits` 是 STL 的“翻译机”，把各种迭代器统一翻译成算法能理解的标准语言：`value_type`、`difference_type`、`pointer`、`reference`、`iterator_category`。

  它让算法和迭代器之间==脱耦==，算法就能“盲目地”高效工作。

### 核心五种嵌套类型含义

| 名称                | 作用                           | 举例                                                         |
| ------------------- | ------------------------------ | ------------------------------------------------------------ |
| `value_type`        | 迭代器指向的值类型             | 对 `vector<int>::iterator` 来说是 `int`                      |
| `difference_type`   | 两个迭代器的距离（差值类型）   | 通常是 `ptrdiff_t`                                           |
| `pointer`           | 指向元素的指针类型             | `int*`                                                       |
| `reference`         | 元素的引用类型                 | `int&`                                                       |
| `iterator_category` | 迭代器的种类标签，用来描述能力 | 比如 `random_access_iterator_tag`,`bidirectional_iterator_tag`等 |

## 补充

- `template <>`这里 `<>` 为空，说明是**完全特化**
- **右值**（临时变量），不能绑定到非常量左值引用 `T&`，会导致编译错误

# Iterator

| 类别名   | 典型标签类型            | 能力与特征                                                   | 常见代表                                                  |
| :--------------------- | -------------------------------- | ------------------------------------------------------------ | --------------------------------------------------------- |
| **输入迭代器**        | `std::input_iterator_tag`         | 只能**从前往后**读取一次，每个元素只能访问一次。支持 `++` 前进、`*` 读取值、`==` / `!=` 比较。 | `istream_iterator`（从输入流读取）                        |
| **输出迭代器**     | `std::output_iterator_tag`        | 只能写（赋值），不能读。一次性往外“吐”数据。支持 `++` 前进、`*` 赋值。 | `ostream_iterator`（输出到流）                            |
| **前向迭代器**     | `std::forward_iterator_tag`       | 可多次读取同一元素；能前进 (`++`)，可读可写。支持 `==`、`!=`。 | `forward_list<int>::iterator`、`unordered_map::iterator`  |
| **双向迭代器**     | `std::bidirectional_iterator_tag` | 能前进 (`++`) 也能后退 (`--`)，可以多次访问元素。            | `list<int>::iterator`、`set<int>::iterator`               |
| **随机访问迭代器** | `std::random_access_iterator_tag` | 支持所有前面的操作，还能用 `+`、`-`、`[]`、比较大小 (`< > <= >=`) 等随机访问操作。 | `vector<int>::iterator`、`deque<int>::iterator`、普通指针 |

```c++
// 五种迭代器标签的继承关系
struct input_iterator_tag {};
struct output_iterator_tag {};
struct forward_iterator_tag       : public input_iterator_tag {};      // 前向迭代器继承输入迭代器
struct bidirectional_iterator_tag : public forward_iterator_tag {};    // 双向迭代器继承前向迭代器
struct random_access_iterator_tag : public bidirectional_iterator_tag {}; // 随机访问迭代器继承双向迭代器
```

# Notes

1. `template<class _inPara, class _outPara>` 等价于 `template<typename _inPara, typename _outPara>`。

   - ## 历史原因

     - **`class`** 是 C++ 最早引入模板时使用的关键字（C++98之前）
     - **`typename`** 是后来添加的关键字（C++98），为了更清晰地表达"这是一个类型参数"

   - **在模板参数声明中**：`class` 和 `typename` **100%等价**

   - **在依赖类型声明中**：只能用 `typename`

   - **现代建议**：优先使用 `typename`，语义更准确

| C++ 版本  | 年份      |
| --------- | --------- |
| C++98/03  | 1998/2003 |
| **C++11** | 2011      |
| C++14     | 2014      |
| C++17     | 2017      |
| C++20     | 2020      |



# Function

## Category

- 发生器：一种`没有参数`且返回一个任意类型值的函数对象，例如随机数发生器。
- 一元函数：一种只有`一个任意类型的参数`，且返回一个可能不同类型值的函数对象。
- 二元函数：一种有`两个任意类型的参数`，且返回一个任意类型值的函数对象。
- 一元判定函数：返回 `bool`型值的一元函数。
- 二元判定函数：返回`bool`型值的二元函数。

## unary_function

```c++
template<class _A, class _R>
struct unary_function {
	typedef _A argument_type;
	typedef _R result_type;
};
```

- 它有两个模板参数，_A是输人参数，_R是返回类型，且这两个参数的类型是任意的，因此它的动态特性非常强。

## binary_function

```c++
template<class Argl, class Arg2, class Result>
struct binary_function {
    typedef Argl first_argument_type;
    typedef Arg2 second_argument_type;
    typedef Result result_type;
};
```

- 它有三个模板参数，`Argl`、`Arg2`是输人参数，`Result`是返回类型，且这三个参数的类型是任意的

## System function

![image-20251106225434881](C:\Users\30703\AppData\Roaming\Typora\typora-user-images\image-20251106225434881.png)

e.g

```c++
cout << plus<int>()(3, 5) << endl;
```

## Function adapter



# Header< algorithm>

1. `for_each`

   - source

     ```c++
     /**
        *  @brief Apply a function to every element of a sequence.
        *  @ingroup non_mutating_algorithms
        *  @param  __first  An input iterator.
        *  @param  __last   An input iterator.
        *  @param  __f      A unary function object.
        *  @return   @p __f
        *
        *  Applies the function object @p __f to each element in the range
        *  @p [first,last).  @p __f must not modify the order of the sequence.
        *  If @p __f has a return value it is ignored.
       */
       template<typename _InputIterator, typename _Function>
         _Function
         for_each(_InputIterator __first, _InputIterator __last, _Function __f)
         {
           // concept requirements
           __glibcxx_function_requires(_InputIteratorConcept<_InputIterator>)
           __glibcxx_requires_valid_range(__first, __last);
           for (; __first != __last; ++__first)
     	__f(*__first);
           return __f; // N.B. [alg.foreach] says std::move(f) but it's redundant.
         }
     ```

   - e.g

     ```c++
     CSum sObj = for_each(v.begin(), v.end(), CSum());
     ```

     - illustrate
       1. 构造临时函数对象
          - 表达式 `CSum()` 产生一个临时对象，调用 `CSum::CSum()`，因此 `sum`被初始化为 0。
          - 这个临时作为实参传给 `std::for_each`（函数参数是按值接收的 `UnaryFunction f`），因此会发生拷贝或移动到 `for_each`的参数。
       2. 在 for_each 内部的循环调用
          - `std::for_each`]对区间 `[v.begin(), v.end())` 每次取一个元素 `*it` 后，执行 `f(*it)`。
          - 这里 `f(*it)` 就是调用你定义的 `CSum::operator()(int n)`，每次将元素累加到 `f.sum` 中。
          - 这一步对每个元素都会调用一次 `operator()`，所以 `sum` 累加 1 到 100。
       3. 返回并赋值给 `sObj`
          - `std::for_each` 在结束时返回 `f`（按值返回）。因此会把 `f` 拷贝或移动出函数，结果作为返回值。
          - 这个返回值再用于初始化 `sObj`，即调用 `CSum`的拷贝构造或移动构造（或被编译器优化掉直接构造到 `sObj`。
          - 最终 `sObj.GetSum()` 访问的是包含全部累加结果的那个对象的 `sum` 成员。
       4. 总的流程是：
          构造临时 `CSum`->（拷贝/移动）进入 `for_each` -> `operator()` 每个元素调用累加 -> 返回累加后的函数对象 -> 初始化 `sObj` -> 使用 `GetSum()` 获取结果。

