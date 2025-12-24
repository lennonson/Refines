# 常用函数

## rand()

```c++
srand((unsigned)time(NULL)); // 方法一
srand(rand() + time(NULL));  // 方法二
```

​	这是基于**当前系统时间**的随机数生成种子(如果不写这个那每回的随机数都固定)

​	详细解释:

1. `time(NULL)`：`time` 函数返回当前的系统时间，它的原型如下：`time_t time(time_t* timer);`。当传递 `NULL` 给 `time` 函数时，它返回当前时间的秒数。
2. `(unsigned)time(NULL)`：将返回的时间值强制转换为 `unsigned` 类型，以确保它是一个正数
3. srand是c++标准库中的一个函数，将时间作为种子传递给srand
4. **方法一具有局限性：如果程序在同一秒内多次运行，生成的随机数序列将是相同的。**
5. **方法二利用了`rand()`函数返回的伪随机数，使得种子不仅依赖于时间，还依赖于当前伪随机数生成器的状态，从而增加了随机性的多样性。**

```c++
int i = rand() % (r - l + 1) + l;
```

​	注意随机数所能取的最大值

---

## malloc

### 	简述

​	   malloc是**动态内存分配函数**，**申请一块连续的指定大小的内存块区域以void\*类型返回分配的内存区域地址**

### 	头文件

​		`\#include<malloc.h>`

### 	返回值

​		分配成功则返回指向被分配内存的指针，否则返回空指针NULL

### 	注意事项

- 返回的是无类型指针，在使用时一定要强制转换为所需要的类型

- **<u>使用完成一定要释放空间，如果不释放会造内存泄漏</u>**

- **使用malloc函数开辟的空间中，不要进行指针的移动，因为一旦移动之后可能出现申请的空间和释放空间大小的不匹配**

### 	使用形式

​		指针自身 = (指针类型*）malloc（sizeof（指针类型）*数据数量）

```c++
int *p = NULL;
int n = 10;
p = (int *)malloc(sizeof(int)*n);
```

> <u>补充：(2024.03.10)这些都是c的内存创建，不用管了---__---</u>

---

## free()

### 	作用

​		释放malloc(或calloc、realloc)函数给指针变量分配的内存空间

### 	注意

​		使用后该**指针变量<u>一定要重新指向NULL</u>**，防止悬空指针（失效指针）出现，有效规避错误操作

```c++
int main(){
	int *p = (int *)malloc(sizeof(int));
	*p = 100;
	free(p);
	p = NULL;
	return 0;
}
```
---

## memset(不好用)

​	memset(数组名,所赋值,sizeof(数组名));

- memset主要是用来初始化char数组
- 在给char以外的数组赋值时，只能初始化为0或者-1或者一个更大的数
- **强烈建议使用memset 来初始化char类型数组**
- memset只能作用于一维数组。
- memset所在的库是< cstring>

---

## std::fill(推荐)

​	`void fill( ForwardIt first,  ForwardIt last ,  const T& value);`

- `first`：范围的起始位置（包含）
- `last`：范围的结束位置（不包含）
- `value`：要为范围内的所有元素设置的值

​	程序开头加上 `using namespace std;`       直接写`fill`

​	e.g	 int a[10]; 

​			  fill(a, a + 10, 1);

​	补充：没什么大弊端

---

## std::array

```c++
std::array<int, 5> arr;		// 创建一个大小为 5 的 std::array    
arr.fill(1);	// 使用 fill 成员函数将数组所有元素设置为 1
```

```c++
for (const auto& element : arr) {		//输出数组的值
	std::cout << element << " ";				
}
```



---

## getline()

​	`<string>`		只能用于string！！！

​	用于读取一整行输入，包括空格，并将其存储在 `userInput` 字符串中。 				`std::cin` 默认情况下会忽略空格，但 `std::getline` 不会

```c++
getline(cin,str,'c');
```

### cin.getline

​	`<iostream>`			用于char

```c++
cin.getline(str,7,'a');
```

​		注释：`7`是输入字符个数

​					`'a'`是遇到就中止输入

---

## sprintf()

​	将数据输入字符串

```c++
sprintf(ans,"%d-%d=%d",x,y,x-y);
```

​	**注意**：<u>不是输出，是导入数据！！！</u>

---

## sscanf()

​	用于从字符串中提取整数和浮点数

​	**注意**：<u>不是输入，是读取！！！</u>

​	`sscanf(b,"%d",&c);`	//如果是数字就转换b为int存储到第一个数字

---

## #include `<cctype>`

​	拥有许多字符串处理函数声明的头文件，这些函数可以用来对单独字符串进行分	类和转换

​	isalpha():检查这个字符是否为字母，真返回1，假返回0；

​	isalnum()：检查这个字符是否为字母或数字数字，同上；

​	isdigit():检查这个字符是否为十进制数字，同上；

​	islower():检查这个字符是否为小写字母，同上

---

## 	gcd()

​		最大公约数

```c++
int gcd(int a,int b) {
	if(b == 0) return a;
	return gcd(b,a % b);
}
```

---

## strtol()

```c++
long int strtol(const char *str, char **endptr, int base);

e.g:  decimal = strtol(hex, NULL, 16);
```

- 只能从其他进制转成十进制



---

## enum

### 作用

枚举类型在代码中可以提高可读性和可维护性，避免了使用难以理解的常量值。它还可以帮助我们编写更具表达力和清晰性的代码。

### 补充

在枚举类型声明中:

- 若未显式赋值,则默认第一个枚举常量值为0,后续常量值依次递增1。
- 当某个枚举常量被显式赋值后,后续常量值将从该值开始递增1。

```c++
enum COLOR{WHITE，YELLOW，GREEN=5，RED，BLACK=10};
```

- A. 枚举常量YELLOW的值为1。
- B. 枚举常量RED的值为6。
- C. 枚举常量BLACK的值为10。
- D. 枚举常量WHITE的值为0。

1. 指定枚举类型

   ```c++
   enum color:unsigned long
   {
   	RED = 0xFF0000,
   	GREEN = 0x00FF00
   };
   ```

2. 声明变量

   ```c++
   enum color backcolor = RED;
   ```

3. 通过编号赋值

   ```c++
   backcolor = color(2);
   ```

   

---

## lowbit

| 6    | 110  | 2^1 = 2 |
| ---- | ---- | ------- |
| 7    | 111  | 2^0 = 1 |

**lowbit()**，lowbit(x)的值是x的二进制表达式中最低位的1所对应的十进制值

```c++
lowbit(x) = x&-x;
lowbit(x) = x&(x^(x-1));
```

###  使用lowbit运算统计二进制数中1的个数

```c++
int countBits(int n) {
    int ans = 0;
	while(n) {
        n = n - (n & -n);
        ans++;
    }	
    return ans;
}
```

## itoa

- iot[a算法](https://so.csdn.net/so/search?q=a算法&spm=1001.2101.3001.7020)是C++标准库中的一个函数模板，用于填充一个区间。它通过指定一个起始值，并根据区间的长度递增生成后续的值。它有助于快速生成递增的序列。

- ```c++
  template <class ForwardIt, class T>
  void iota(ForwardIt first, ForwardIt last, T value);
  
  std::vector<int> nums(5);
  std::iota(nums.begin(), nums.end(), 1);
  ```

  

---

# 数据结构

## 	vector

​		`vector<int>& nums` 和 `vector<int> nums` 并不完全相同。

​		`vector<int>& nums` 是一个引用类型的参数，表示函数接受一个对`vector<int>` 的引用。在函数内部，对该引用的修改将直接影响到传入的原始向量。

​		`vector<int> nums` 是一个值类型的参数，它表示函数接受一个`vector<int>` 的副本。在函数内部对该副本的修改不会影响到传入的原始向量。

###  插入方式

- `push_back`
  - 尾部插入一个新元素
  - 先创建一个临时对象
  - 以下情况使用`push_back`
    - 将已经存在的对象添加到vector中
    - 对象类型没有对应的构造函数参数，或者构造函数参数无法直接传递给emplace_back。
- `emplace_back`
  - 尾部插入一个新元素
  - 直接在vector中构造新元素
  - 提高性能，避免不必要的拷贝构造和析构操作

---

## 二叉树

## 树的直径

​		树上<u>任意两节点</u>之间最长的简单路径即为树的「直径」。显然，<u>一棵树可以有多条直径</u>，他们的<u>长度相等</u>。可以用两次DFS/B FSDFS/BFSDFS/BFS 或者树形 D P DPDP 的方法在 O ( n ) O(n)O(n) 时间求出树的直径。

### 遍历

####  中序遍历

<img src="D:\sxu\[精英之英]\jyzy2024寒假\2024.01.28\二叉树遍历eg.png" alt="二叉树遍历eg" style="zoom:67%;" />

![img](https://img-blog.csdnimg.cn/47091324f8a643ca825cab4033ab701f.png)

1. 中序遍历左子树
2. 访问根节点
3. 中序遍历右子树

####   迭代法

```c++
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode() : val(0), left(nullptr), right(nullptr) {}
 *     TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
 *     TreeNode(int x, TreeNode *left, TreeNode *right) : val(x), left(left), right(right) {}
 * };
 */
class Solution {
public:
    vector<int> inorderTraversal(TreeNode* root) {
        vector<int>ans;
        TreeNode* temp = root;
        stack<TreeNode*> stack;
        while(temp != nullptr || stack.size()) {
            while(temp) {
                stack.push(temp);
                temp = temp -> left;
            }
            ans.push_back(stack.top() -> val);
            temp = stack.top() -> right;
            stack.pop();
        }
        return ans;
    }
};
```



### 前序遍历

<img src="D:\sxu\[精英之英]\jyzy2024寒假\2024.01.28\二叉树遍历eg.png" alt="二叉树遍历eg" style="zoom:67%;" />

<img src="https://img-blog.csdnimg.cn/04b31ce65e6d4fbb824839c49a7c2a28.png" alt="img" style="zoom:80%;" />

1. 先访问根节点
2. 再前序遍历左子树
3. 最后前序遍历右子树

#### 	迭代法1

```c++
class Solution {
public:
    vector<int> preorderTraversal(TreeNode* root) {
        vector<int>ans;
        TreeNode* temp = root;
        stack<TreeNode*>stack;
        while(temp != nullptr || stack.size()) {
            while(temp != nullptr) {
                stack.push(temp);
                ans.push_back(temp -> val);
                temp = stack.top() -> left;
            }
            if(temp == nullptr && stack.size()) {
                temp = stack.top() -> right;
                stack.pop();
            }
        }
        return ans;
    }
};
```

- temp不为空就压入栈，并指向左孩子
- 若为空则指向右孩子，并删除栈顶
- pop应在temp赋值之后，因为若左右都无孩子，pop操作两次，一次删除temp，一次删除父节点，因为父节点已遍历完成

#### 迭代法2

```c++
class Solution {
public:
    vector<int> preorderTraversal(TreeNode* root) {
        stack<TreeNode*> st;
        vector<int> res;
        st.push(root);
        while(root && st.size()){
            auto temp = st.top();
            st.pop();
            res.push_back(temp->val);
            if(temp -> right) st.push(temp -> right);
            if(temp -> left) st.push(temp -> left);
        }
        return res;
    }
};

```

- 先右后左，顺序不能反
- 保证栈顶先为左孩子

### 后序遍历

<img src="D:\sxu\[精英之英]\jyzy2024寒假\2024.01.28\二叉树遍历eg.png" alt="二叉树遍历eg" style="zoom:67%;" />

![img](https://img-blog.csdnimg.cn/3fe82500497c4a3caa84426e3f652024.png)

​    i、后序遍历左子树

​    ii、后序遍历右子树

​    iii、访问根结点

#### 	迭代法1

```c++
class Solution {
public:
    vector<int> postorderTraversal(TreeNode* root) {
        vector<int>ans;
        TreeNode* temp = root;
        stack<TreeNode*>stack;
        stack.push(root);
        while(temp != nullptr && stack.size()) {
            if(temp -> left) {
                stack.push(temp -> left);
                temp = temp -> left;
            }else {
                if(temp -> right) {
                    stack.push(temp -> right);
                    temp = temp -> right;
                }else {
                    ans.push_back(stack.top() -> val);
                    stack.pop();
                    if(stack.size()) {
                        stack.top() -> left == temp ? stack.top() -> left = nullptr : stack.top() -> right = nullptr;
                        temp = stack.top();
                    }
                }
            }
        }
        return ans;
    }
};
```

- shi山，就是纪念一下
- temp左存在就将左入栈，右存在就将右入栈
- 都不存在则将val存入，并切断temp与父节点，temp变为其父节点
- 2024.02.21:为了后序遍历把树都毁了---__---

#### 	迭代法2

```c++
class Solution {
public:
    vector<int> postorderTraversal(TreeNode* root) {
        vector<int> res;
        stack<TreeNode*> st;
        TreeNode* cur = root;
        while(cur != nullptr || st.size()){
            while(cur){
                st.push(cur);
                cur = cur -> left;
            }
            auto temp = st.top();
            // 对中间节点特殊处理
            if(temp->right == nullptr){ //不是中间节点
                res.push_back(temp -> val);
                st.pop();
            }else{ //是中间节点的话，把中间节点替换成左右子树为空的节点，再压入栈中，
                //这样再弹出这个节点就不会再对他右子树做出扩展，直接写入该值。
                st.pop();
                st.push(new TreeNode(temp->val, nullptr, nullptr));
                cur = temp -> right;
            }
        }
        return res;
    }
};

```

### 层序遍历

```c++
class Solution {
public:
    vector<vector<int>> levelOrder(TreeNode* root) {
        queue<TreeNode*>q;
        vector<vector<int>>ans;
        vector<int>row;
        if(!root) return ans;
        q.push(root);
        while(!q.empty()) {
            int cnt = q.size();
            while(cnt--) {
                TreeNode* cur = q.front();
                row.push_back(cur -> val);
                q.pop();
                if(cur -> left != nullptr) q.push(cur -> left);
                if(cur -> right != nullptr) q.push(cur -> right);
            }
            ans.push_back(row);
            row.clear();
        }
        return ans;
    }
};
```

最大/小深度

```c++
class Solution {
public:
    int maxDepth(TreeNode* root) {
        if(!root) return 0;
        return max(maxDepth(root -> left), maxDepth(root -> right) ) + 1;
    }
};
class Solution {
public:
    int minDepth(TreeNode* root) {
        if(!root) return 0;
        if(!root -> right) return minDepth(root -> left) + 1;
        if(!root -> left)  return minDepth(root -> right) + 1;
        return min( minDepth(root -> right), minDepth(root -> left) ) + 1;
    }
};
```

平衡二叉树

```c++
class Solution {
public:
    int maxDepth (TreeNode* cur) {
        if (!cur) return 0;
        return max(maxDepth(cur -> left) + 1, maxDepth(cur -> right) + 1);
    }
    bool isBalanced (TreeNode* root) {
        if (!root) return true;
        return isBalanced (root -> left) && isBalanced (root -> right) &&
        abs(maxDepth (root -> left) - maxDepth (root -> right) ) <= 1;
    }
};
```





---

## 链表

###  哑节点

```c++
  ListNode* dummy = new ListNode(0);
```

#### 	好处

- 简化边界条件的判断(如果有一个哑节点，那么头节点就不会为空，也不会有特殊情况，可以和其他节点一样处理)
- 统一插入和删除的操作(如果有一个哑节点，那么头节点就有一个前驱节点，可以和其他节点一样插入或删除)
- 方便返回结果链表,有些链表操作需要返回一个新的链表，这通常需要保存一个指向头节点的指针

###  创建新链表

```c++
tail->next = new ListNode(sum % 10);
tail = tail->next;
```

##  模板

```c++
// Definition for singly-linked list.
struct ListNode {
    int val;
    ListNode *next;
    ListNode() : val(0), next(nullptr) {}
    ListNode(int x) : val(x), next(nullptr) {}
    ListNode(int x, ListNode *next) : val(x), next(next) {}
};
```



---

## Hash

###  碰撞，冲突

#### 含义

> ​	不同的输入可能得到相同的输出(实际上这种问题必然存在)

####   解决方法

##### 	封闭寻址法

###### 		链表法

​		 把引发冲突的插入数据放入当前节点的链表中，查询时再根据索引在链表中查询

##### 	开放寻址发

###### 		线性探测方法

​		 当前索引发生冲突，就向下一个寻找，直到找到

###### 		二次探测方法

​		 当前索引发生冲突，就向2的2次方个寻找，若还冲突，向3的3次方寻找，依次类推，直到找到



---

## set

```c++
set<char> s;
s.size();
s.insert(a);
```

- set 中没有重复元素
- 当插入一个重复元素时不会执行插入



----

## map

1. 基于红黑树实现
2. 查找效率为O(logn)
3. 内存占用较大需要维护元素顺序
4. 插入和删除效率较低，时间复杂度为O(logn)

```c++
map<int,int> m; 
```

- map由index和value

```c++
map<int,int> m; 
    int ans = 0;   //记录出现最多的那个编号
    int cnt = 0;   //记录出现最多的编号次数
    while(N--)
    {
        int K;
        cin >> K;
        while(K--)
        {
            int temp;
            cin >> temp;
            m[temp]++;
            if(m[temp] > cnt)   //更新出现次数最多的那个数
            {
                cnt = m[temp];
                ans = temp;
            }
            else if(m[temp] == cnt)  //若出现次数相同
            {
                ans = max(ans,temp); //选择编号大的那个
            }
        }
    }
    printf("%d %d\n",ans,cnt);
    return 0;
```

- 排序

  ```c++
  map<string, int, greater<string> > mapStudent;
  ```

- 迭代器

  ```c++
  for(iter=mapStudent.begin();iter!=mapStudent.end();iter++)
  ```

----

## 堆

实际应用中，我们可以直接使用编程语言提供的堆类（或优先队列类）`priority_queue`

```c++
priority_queue<int, vector<int>, greater<int>> minHeap;			// 初始化小顶堆
priority_queue<int, vector<int>, less<int>> maxHeap;			// 初始化大顶堆
vector<int> input{1, 3, 2, 5, 4};								/* 输入列表并建堆 */
priority_queue<int, vector<int>, greater<int>> minHeap(input.begin(), input.end());
maxHeap.push(1);				/* 元素入堆 */
maxHeap.pop();					/* 堆顶元素出堆 */
int size = maxHeap.size();		/* 获取堆大小 */
bool isEmpty = maxHeap.empty();	/* 判断堆是否为空 */
```

- 第一个`int`：储存元素类型是`int`
- `vector`：底层容器类型是`vector`
- `greater`：比较器，转化为小顶堆
- `less`：比较器，转化为大顶堆

> #### 在 C++ 中，`std::priority_queue` 并不直接支持范围基于的 for 循环（range-based for loop），因为它不是一个标准的容器，不能通过迭代器进行遍历。

### **Question：**

#### 数据结构的“堆”与内存管理的“堆”是同一个概念吗？

​	**两者不是同一个概念**，只是碰巧都叫“堆”。**计算机系统内存中的堆是动态内存分配的一部分**，程序在运行时可以使用它来存储数据。**程序可以请求一定量的堆内存**，用于存储如对象和数组等复杂结构。当这些数据不再需要时，程序需要释放这些内存，以防止内存泄漏。**相较于栈内存，堆内存的管理和使用需要更谨慎**，使用不当可能会导致内存泄漏和野指针等问题。



---

## 树状数组

<img src="https://i-blog.csdnimg.cn/blog_migrate/1efbedf26d64adaa214b54bae4d892bc.png" alt="在这里插入图片描述" style="zoom: 50%;" />

- 树状数组中节点x的父节点为**x+lowbit(x)**

### 单点修改

```c++
int add_dot(int x, int k) {
	for (int i = 1;i <= n; i + lowbit(i))
        t[i] += k;
}
```

### 区间查询

<img src="https://i-blog.csdnimg.cn/blog_migrate/1bf4a100bdd81505142ccdaf4b3faf4f.png" alt="在这里插入图片描述" style="zoom:50%;" />

```c++
int ask_section(int x) {
    int sum = 0;
	for (int i = x; i ; i -= lowbit(i))
        sum += t[i];
    return sum;
}
```

- 求前x项的和，只能求[1，x]的区间和

- sum[7]=t[7]+t[6]+t[4] ,我们进一步发现,6=7-lowbit(7),4=6-lowbit(6)，所以我们可以通过不断的-lowbit操作来实现求和

- 求[L，R]的区间和（利用前缀和相减的性质）

  ```c++
  int ask_section(int l, int r) {
  	int ans = 0;
      for (int i = l - 1; i; i -= lowbit(i))
          ans -= t[i];
      for (int i = r - 1; i; i -= lowbit(i))
          ans += t[i];
      return ans;
  }
  ```

- 树的构建

  ```c++
  class TreeArray {
      vector<int> tree;
      vector<int> &nums;
      int lowbit(int x) {
          return x & -x;
      }
      void modify (int index, int val) {
          for (;index < tree.size(); index +=lowbit(index))
              tree[index] += val;
      }
  public:
      TreeArray(vector<int>& nums) : tree(nums.size() + 1), nums(nums) {
          for (int i = 0;i < nums.size(); i++)
              add (i + 1, nusm[i]);
      }
  };
  ```

  









---

---

---

# 常见问题

## 	segmentation fault

​		由于程序试图访问其内存空间的非法部分而引起的

​		几种原因引起的：

1. **访问非法指针：** 当程序尝试使用未初始化的指针，或者试图访问已经被释放的内存时，可能导致Segmentation fault。
2. **数组越界：** 尝试访问数组中超出其边界的元素可能引发此错误。
3. **使用野指针：** 当程序尝试访问已经被释放的内存块时，可能会发生Segmentation fault。
4. **内存损坏：** 如果程序意外地修改了其它部分的内存，导致内存损坏，也可能触发Segmentation fault。
5. **堆栈溢出：** 如果程序的递归调用或者函数调用层次太深，导致堆栈溢出，也可能引发Segmentation fault。

---

## 	内存占用

### 		64位

​			指针都占8个字节

​			int占4个字节(无论64/32)

​			char占1个字节

### 		32位

​			指针都占4个字节

---

### 	free

​		`free()`只释放内存，不会改变指针指向的内容

​		这句是**错误**的：~~当使用free释放掉一个指针内容后，指针变量的值被置为NULL~~

---

## 	格式说明符

​		

- `%l` 表示长整数（long）。
- `%u` 表示无符号整数（unsigned）。

​			因此，`%lu` 表示输出一个无符号长整数

​			可用于输出sizeof(type)

---

## 特殊运算

​	2 % 4 == 2;

​	2 / 4 == 0;

---

## cin和scanf

​	`scanf("%d",&n);`	//系统会自动给你输入一个换行符,如果下面输入字符会出错

​		解决方法：输入后添加 `cin.ignore();`

​	字符串输入scanf要加地址符& `scanf("%s",&s);`

###  记录：

 2024.4.17 

> 又遇到这个问题了

- 问题

```c++
for(int i = 0;i < n; i++) {
        cin >> my_post[i].index_list;
        getline(cin, my_post[i].test_text);
}
/*
getline无法正常使用，
分析后发现前面的cin输入后产生了换行符问题
*/
```

- 解决方案

```c++
for(int i = 0;i < n; i++) {
        cin >> my_post[i].index_list;
        cin.ignore();
        getline(cin, my_post[i].test_text);
}
/*
在两个输入中添加cin.ignore()
得解
*/
```

2025.02.28

#### `cin.ignore()`

1. 跳过一个字符

   `cin.ignore();`

2. 跳过多个字符

   `cin.ignore(100, '\n')`

   跳过最多100个字符，直到遇见换行符为止

### `cin.get()`

1. `cin.get(变量名)`接受空格，换行。剩下的数据会保留在输入流（缓冲区）中，下一次继续读取。

2. `cin.get(数组名， 字符个数)`接收空格，遇到回车结束，且不会过滤掉回车符，回车符一直保留在输入流（缓存区），就会导致后面无法接收字符（例如上面的第2张图片）。因为数组末尾要加‘\0’，所有 **实际接收的字符数量少一位。**

   ![image-20250228110238774](C:\Users\30703\AppData\Roaming\Typora\typora-user-images\image-20250228110238774.png)

3. `cin.get()`接收一个字符，也不会存放在变量里。<u>主要用途就是用来吸收回车符</u>，这样变可以解决上述问题。

4. `cin.get()`都是作用于char，或者char[]，不能作用于string

### `cin.getline()`

1. 可以接受空格，遇到回车就结束。数组末尾需要加‘\0’，所以**所读字符个数少一位。**

2. 若输入流中**字符个数达到或者超过字符个数n**，就会导致 读入错误，虽然本次读入成功，但是**后面的读入都会失败**

   ![image-20250228110601129](C:\Users\30703\AppData\Roaming\Typora\typora-user-images\image-20250228110601129.png)

3. `cin.getline()`都是作用于char[],不能作用于string

### `getline(cin, 变量名)`

1. 可以接受空格，遇到回车就结束。因为不是数组，所以末尾没有‘\0’。
2. 作用对象为string类

### cin和getline的不同

> cin的结束符会保留在输入流（缓冲区）中
>
> getline的结束符不会保留在输入流（缓冲区）中

---

## **NPE**

​	NPE(java.lang.NullPointerException): 空指针异常

> 防止 NPE，是程序员的基本修养

---

## 指针动态数组

### 问题

​	c++静态数组(也就是在栈上开数组)大小不能开太大

​	在本机上(也就是2023光影精灵，16G，i713650H)测试最大能开250000(二十五万)

###  解决方法

​	在堆上开辟数组

```c++
int* nums = new int[/*要开辟的大小*/];
string* nums = new string[];
int* nums = new int[][];
```

​	注释：一般来说栈的大小在1M~2M之间，而堆怎么也有2G，可以简单计算一下

​	注意：new返回指向该空间的指针，所以创建时要加`*`

---

## 内存问题

2024.4.19 天梯赛练题

- 新版的g++编译器当遇到**未赋初值的数组**进行**数组越界的赋值**时，输出时会直接停止输出，赋值时不会报错

> 一定要注意内存管理，c++的核心素养



---

## 字符数组

### 复制

在C++中，字符串是以字符数组的形式存储的。因此，字符串的复制操作需要使用字符串库函数`strcpy`来执行。

```c++
this->Name = Ps.Name; // （错误）
```

```c++
strcpy(Name, Ps.Name); // （正确）
```

### 初值

当字符数组需要赋初值时，可以赋值为：

```c++
HomeAddress[0]='\0';
```

- 将字符数组`HomeAddress`的第一个元素设置为空字符
- 空字符（`\0`）是表示字符串结束的特殊字符
- 在C++中，字符串以空字符结尾
- 所以通过将第一个元素设置为空字符，可以将`HomeAddress`表示为一个空字符串
- 需要注意的是，将字符数组第一个元素设置为空字符并不会释放分配给它的内存
- 如果需要释放内存，应该使用适当的方法来释放该数组所占用的内存空间。

## 八进制

01被解释为八进制数字

## std::vector成员函数

`resize`和`reserve`

- `resize`会改变`vector`的size并初始化新增元素
- `reserve`只会分配容量`capacity`不会初始化元素以及改变size



---

---

---

# 指针

## 	补充

```c++
int main() {
	int a[5] = {1, 2, 3, 4, 5};
	int *ptr1 = (int*)(&a + 1);
    int *ptr2 = (int*)(a + 1);
	printf("%d, %d", *(a + 1), *(ptr1 - 1));
    printf("%d, %d", *(a + 1), *(ptr2 - 1));
	return 0;
}
```
​	输出：![image-20240511192043020](C:\Users\30703\AppData\Roaming\Typora\typora-user-images\image-20240511192043020.png)

​	如上述代码，&a+1表示指向a数组之后的位置，而不是a数组中的下一个元素的地址

​		改成a+1才是

​		输出结果应为 `2,5`

###  2024.5.11补充(回看发现当时没弄懂)

- 此处的`&a+1`是一个地址，指向的是a数组的下一个位置(当不了解内存具体如何分配时，实际上是指向了一个未知的位置)
- `*(ptr1 - 1)`表示 `ptr1` 指针指向的地址的前一个位置的值，输出即为a数组的最后一个元素`5`
- 而此处的`a+1`指的是a数组的第二个元素
- `*(ptr2 - 1)`输出即为a数组的第1个元素`1`
- `int*`进行强制类型转化，使得这一个地址所存放的是另一个元素的地址，最后赋值给int指针`*ptr`
- `*(ptr - 1)`表示的就是ptr所指向的上一个元素(即a数组)



---

## 2024.5.11补充

```c++
int a[3];
a[0] = 0;
a[1] = 1;
a[2] = 2;
int *p, *q;
p = a;
q = &a[2];
cout << a[*q - *p] << endl;
cout << "q - p:" << q - p << endl;
cout << "q:" << q << endl;
cout << "p:" << p << endl;
cout << "&p: " << &p << endl;
cout << "*p: " << *p << endl;
cout << "*q: " << *q << endl;
cout << "p address: " << reinterpret_cast<uintptr_t>(p) << endl;
cout << "q address: " << reinterpret_cast<uintptr_t>(q) << endl;
```

- 输出：           ![image-20240511185720956](C:\Users\30703\AppData\Roaming\Typora\typora-user-images\image-20240511185720956.png)

- 注释：`q-p`输出的是元素个数，因为是该系统中指针占4个字节，因此元素个数(即`q-p`)是2

- > 在C/C++中，指针之间的减法操作得到的结果是两个指针之间相差的元素个数，而不是地址之间的字节数

- `reinterpret_cast`用于强制转化类型

  ```c++
  reinterpret_cast<new_type>(expression)
  ```

- `uintptr_t`是C和C++中的一个整数类型，定义在 `<stdint.h>` 或 `<cstdint>` 头文件中。它是一个无符号整数类型，足以容纳指针类型的值。

- `&p`指的是指针p的地址

- `*p`指的是指针p所指向的元素

- `q`和`p`存放的是所指向元素的地址

- `*`是解引用操作符，表示该指针所指向的地址的值

###  纠错1

```c++
int m = 10;
const int n = 20;
const int *ptr1 = &m;
int *const ptr2 = &m;
/*---------------------------------------------------------------------------*/
const int *ptr1 = &m;
int *const ptr2 = &m;
*ptr1 = 3;
ptr2 = &n;
int *ptr3 = &n;
const int *ptr4 = &n;
int *const ptr5;
ptr5 = &m;
const int *const ptr6 = &m;
*ptr6 = 5;
ptr6 = &n;
const int *ptr7;
ptr7 = &m;
/*---------------------------------------------------------------------------*/
```



1. `*ptr = 3` 错误1，表达式必须是可修改的左值
   - `*ptr`不可修改，所以大多数情况下是一个右值
   - 左值：指一个可以被赋值的位置，也就是可以放在赋值操作符的左侧的东西
   - 右值：指一个可以被赋给左值的值，也就是可以放在赋值操作符的右侧的东西。通常是一个值或者一个计算出来的结果
2. `int *const ptr2 = &m;`表示一个常量指针，不可修改
3. `const int *ptr1 = &m;`一个指向常量整数的指针
4. `ptr2 = &n;`错误2，表达式必须是可修改的左值，**注:`ptr2`是一个常量指针,已经指向&m,不能修改**
5. `int *ptr3 = &n;`"错误3，const int *" 类型的值不能用于初始化 "int *" 类型的实体
6. `int *const ptr5;`错误4，常量 变量 "ptr5" 需要初始值设定项
7. `ptr5 = &m;`错误5，表达式必须是可修改的左值
8. `const int *const ptr6 = &m;`一个指向常量整数的常量指针
9. `*ptr6 = 5;`错误6，原因同错误2
10. `ptr6 = &n;`错误7，表达式必须是可修改的左值，`ptr6`是一个常量指针

### 纠错2

```c++
int* p;
*p = 3;
```

-  运行时会报错segmentation fault
- 因为没有给指针p分配内存，就直接给*p赋值，导致内存泄漏
- 解决方法：
  1. `int *p = (int*)malloc(sizeof(int));` 初始化时分配内存

### ( * (void( * )( ) ) 0 )( );详解

(*(void (*) ()) 0) ();其实可以拆分成三个部分：

1. `void(*) ()`，其实这样看起来还不是很明显，在*之后加上一个变量p，`void (*p) ();`那很明显，这就是一个*函数指针`*p`的声明，且返回值为void类型，那去掉p之后，是一个类型转换，转换的类型就是void *。
2. (void (*) ()) 0则就是对整数0做的类型转换，此时0就是一个**函数指针类型**，且返回值为void。
3. (*(void (*) ()) 0) ();我们可以用fp代替这里的类型转换，即(*fp) ();这就是一个<u>**函数调用**</u>，fp为指向该函数的指针。





---

# 数论

​	简单算法

## 快速幂

### 	原因

​		当进行幂运算的指数很大时，幂运算所需的时间会很长，不是一个好的算法，		在做题时容易超时从而失分。

### 	原理

​		<u>**底数乘方**</u>

​		<u>**指数减半**</u>

​		<u>**循环操作**</u>

### 	示例

```c++
int power(int a,int n) {
	int ans = 1;
	while(n) {
	if(n % 2)
		ans *= a;	//是否奇数
		a *= a;		//底数平方
		n /= 2;		//指数减半
	}
	return ans;
}
```

---

---

---

## 素数筛法

### 	埃式筛法

​	埃拉托斯特尼所提出的一种简单检定素数的算法。 要得到自然数n以内的全部素数，必须把不大于根号n的所有素数的倍数剔除，剩下的就是素数。

---

### 	欧拉筛法

​		在埃氏筛法的基础上，让每个合数只被它的最小质因子筛选一次，以达到不重复的目的

---

## 高斯消元

​	枚举每一列c(从左往右)

1. 找到绝对值最大的一行
2. 将该行换到最上面
3. 将改行的第一个数变成1
4. 将下面的所有行的第c列消成0

---

---

---

# 高精度

## 前言

​			1.数据的接收和存储：采用字符输入，再存入int型数组

```c++
void init(int a[]) { // 传入数组
    char s[1001];
    cin >> s; 
    len = strlen(s); // s.length --> 计算字符串位数
    for(int i = 0; i < len; i++)     
      a[len-i-1] = s[i] - '0';//将字符串s转换为数组a, 倒序存储
}
```

​             2.进位,借位处理

```c++
//加法进位 c[i] = a[i] + b[i];
x = c[i] / 10;//满10为1
c[i] %= 10;//满10消去，不满不变

//减法进位 c[i] = a[i] - b[i];
if(a[i] < b[i]) {
    --a[i+1];
    a[i] += 10;
}
//乘法进位 c[i + j] = a[i] * b[i] + x + c[i + j]
x = c[i + j] / 10;
c[i + j] % 10;
```

## 加法

```c++
#include <cstdio>
#include <cstring>
using namespace std;
int a[510],b[510],c[510];	//c存储结果
char A[510],B[510];	//字符串存储数字
int carry;//进位(准确英文哦)
int len_c;
int main() {
    scanf("%s%s",A,B);
    int len_A = strlen(A);
    int len_B = strlen(B);
    for(int i = 0;i < len_A; i++)
        a[len_A - i - 1] = A[i] - '0';	//反向把数字存入
    for(int i = 0;i < len_B; i++)
        b[len_B - i - 1] = B[i] - '0';	//另一个数
    while(len_c < len_A || len_c < len_B) {
        c[len_c] = a[len_c] + b[len_c] + carry;				//相加再加上进位的
        carry = c[len_c] / 10;	//刷新进位
        c[len_c] %= 10;	//进位后剩下的
        len_c++;
    }
    c[len_c] = carry;
    if(!c[len_c])	//首位如果没有不输出
        len_c--;
    for(int i = len_c; i >= 0; i--)	//还得反着输出
        printf("%d",c[i]);	//每一位数
    return 0;
}
```

---

## 乘法

​		code1(csdn)

```c++
#include <iostream>
#include <cstring>
#include <cstdio>
using namespace std;
char A[2010],B[2010];
int a[2010],b[2010],c[4020];
int carry;
int main() {
    scanf("%s%s",A,B);
    int len_A = strlen(A);
    int len_B = strlen(B);
    for(int i = 0;i < len_A; i++)//倒序存储
        a[len_A - i - 1] = A[i] - '0';
    for(int i = 0;i < len_B; i++)
        b[len_B - i - 1] = B[i] - '0';
    for(int i = 0;i < len_A; i++) {
        carry = 0;
        for(int j = 0;j < len_B; j++) {
            c[i + j] = a[i] * b[j] + c[i + j] + carry;   			 					 							//a*b 再加 上一回算的 再加 进位
            carry = c[i + j] / 10;//进位
            c[i + j] %= 10;//进位后剩下的
        }
        c[i + len_B] += carry;//b全部乘完后最高位的进位
    }
    int len_C = len_A + len_B;//c的最大长度就是a+b
    while(c[len_C] == 0 && len_C >= 1)//首位没有就不输出
        len_C--;
    for(int i = len_C; i >= 0; i--)//倒序输出
        cout << c[i];
    cout << endl;
    return 0;
}
```

​		code2(luogu_example)

```c++
#include<iostream>
#include<cstring>
using namespace std;
char a1[50001],b1[50001];
int a[50001],b[50001],i,x,len,j,c[50001];
int main (){
    cin >>a1 >>b1;//读入两个数
    a[0]=strlen(a1);b[0]=strlen(b1);//计算长度
    for (i=1;i<=a[0];++i)
        a[i]=a1[a[0]-i]-'0';//将字符串转换成数字
    for (i=1;i<=b[0];++i)
        b[i]=b1[b[0]-i]-'0';
    for (i=1;i<=a[0];++i)
        for (j=1;j<=b[0];++j)
            c[i+j-1]+=a[i]*b[j];//按乘法原理进行高精乘
    len=a[0]+b[0];                                       
    for (i=1;i<len;++i)
        if (c[i]>9){
            c[i+1]+=c[i]/10;c[i]%=10;
        }//进位
    while (c[len]==0&&len>1)
        len--;//判断位数
    for (i=len;i>=1;--i)
        cout <<c[i];//输出
    return 0;
}
```

​		reap:把字符的长度放到s[0]很明了

​				  第二种方法思路更好想

---

# 排序

![这里写图片描述](https://img-blog.csdn.net/20170818211941416?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvSmVhZm9yZWE=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

## 插入排序

InsertSort

​	<img src="https://img-blog.csdnimg.cn/4d5d54dcbc7b47b18c45e0a23b906780.gif#pic_center" alt="img" style="zoom:50%;" />

### 	核心思想

​		迭代，比较，移动

### 	时间复杂度&空间复杂度

- 时间复杂度：O(n^2)
- 空间复杂度：O(1)

### 	源码

```c++
#include <stdio.h>
int a[1010];
void InsterSort(int n,int *a) {
    for(int i = 0;i < n; i++) {
        int cur = a[i];
        for(int j = i - 1; j >= 0; j--) {
            if(cur <= a[j])
                a[j + 1] = a[j];
            else break;
        }
        a[j + 1] = cur;
    }
}
int main() {
    int n;
    scanf("%d",&n);
    for(int i = 0;i < n; i++)
        scanf("%d",a[i]);
    InsertSort(n,a);
    for(int i = 0;i < n; i++)
        printf("%d ",a[i]);
    printf("\n");
    return 0;
}
```

---

## 冒泡排序

BubbleSort

<img src="https://img-blog.csdnimg.cn/99f37fb95391458484b78d40005d07f5.gif#pic_center" alt="img" style="zoom:50%;" />

### 	时间复杂度&空间复杂度

- 时间复杂度：O(n^2)
- 空间复杂度：O(1)

### 	源码

```c++
#include <stdio.h>
int n,a[1010];
void BubbleSort(int n,int *a) {
    bool flag;
    int last = n;
    do{
        flag = false;
        for(int i = 0;i < last - 1; i++) {
            if(a[i] > a[i + 1]) {
                swap(a[i],a[i + 1]);
                flag = true;
            }
        }
        last--;
    }while(flag);
}
int main() {
    scanf("%d" &n);
    for(int i = 0;i < n; i++)
        scanf("%d",&a[i]);
    BubbleSort(n,a);
    for(int i = 0;i < n; i++)
        printf("%d ",a[i]);
    printf("\n");
    return 0;
}
```

---

## 选择排序

SelectSort

​	<img src="https://img-blog.csdnimg.cn/1b1ec4fcf6024ad4a659fab5f21a7075.gif#pic_center" alt="img" style="zoom:50%;" />

### 	时间复杂度&空间复杂度

- 时间复杂度：O(n^2)
- 空间复杂度：O(1)

### 	源码

```c++

```





---

---

---

## 	快速排序

重点！！！

### 		方法一：

#### 			步骤

```c++
int randomized_partition(vector<int>& nums, int l, int r) {
	int i = rand() % (r - l + 1) + l; // 随机选一个作为我们的主元在l到r范围内
    swap(nums[r], nums[i]);//把主元放到数组最后
   	return partition(nums, l, r);//开始进入排序
   }
void randomized_quicksort(vector<int>& nums, int l, int r) {
       if (l < r) {//left<right
           int pos = randomized_partition(nums, l, r);//选主元,找到主元位置
           randomized_quicksort(nums, l, pos - 1);//把左边的排序,(主元-1)就是right
           randomized_quicksort(nums, pos + 1, r);//右边排序
       }
   }
int partition(vector<int>& nums, int l, int r) {//排序主体
       int pivot = nums[r];//要比较大小的主元
       int i = l - 1;//能够保证第一个不交换
       for (int j = l; j <= r - 1; ++j) {
           if (nums[j] <= pivot) {//如果小于主元
               i = i + 1;
               swap(nums[i], nums[j]);//交换
           }
       }
       swap(nums[i + 1], nums[r]);//把主元再放回该在的地方
       return i + 1;
   }
public:
       vector<int> sortArray(vector<int>& nums) {
           srand((unsigned)time(NULL));//系统时间随机种子
           randomized_quicksort(nums, 0, (int)nums.size() - 1);
           return nums;
       }
   };
```

### 方法二：

推荐

```c++
#include <bits/stdc++.h>
using namespace std;
int a[100001];
int n;
void qsort(int a[],int l,int r) {
	int i = l;
	int j = r;
	if(i >= j)
		return;
	int temp = a[l];
	while(i != j) {
		while(a[j] >= temp && i < j)
      		j--;
    	while(a[i] <= temp && i <j)
      		i++;
    	if(i < j)
       	    swap(a[i],a[j]);
	}
	swap(a[l],a[i]);
	qsort(a,l,i-1);
	qsort(a,i+1,r);
}
int main() {
 	scanf("%d",&n);
  	for(int i = 0;i < n; i++)
    scanf("%d",&a[i]);
  	qsort(a,0,n-1);
	for(int i = 0;i < n; i++)
    printf("%d ",a[i]);
	return 0;
}
```

### 	优化最终版

(随机数)

```c++
class Solution {
public:
    void qsort(vector<int>&nums, int l, int r) {
        int i = l;
        int j = r;
        if(i >= j) 
            return;
        srand((unsigned)time(NULL));
        int pivot = nums[l + rand() % (r - l + 1)];
        while(i <= j) {
            while(nums[i] < pivot) i++;
            while(nums[j] > pivot) j--;
            if(i <= j) {
                swap(nums[i], nums[j]);
                i++;j--;
            }
        }
        qsort(nums, l, j);
        qsort(nums, i, r);
    }
    vector<int> sortArray(vector<int>& nums) {
        qsort(nums, 0, nums.size() - 1);
        return nums;
    }
};
```



### 		复杂度分析

  **时间复杂度**：基于随机选取主元的快速排序时间复杂度为期望 

✅ 最佳情况（Best Case）：

​		每次划分都刚好将数组平分，即 `n/2 + n/2`，此时复杂度为：

​					$$\mathcal O(n\log⁡n)$$

❌ 最坏情况（Worst Case）：

​		当每次划分都极端不平衡（例如已排序数组，每次都选最小或最大为主元），则递归深度变为 n，每层处理 n个元素：

​					$$\mathcal{O}(n^2)$$

  **空间复杂度**：`O(h)`,其中h为快排递归调用的层数，需要额外的`O(h)`的递归调用的栈空间，由于划分结果不同导致快排递归调用的层数也会不同，最坏情况下需要`O(n)`的空间，最优情况下每次都平衡

2023.12.16补充 ？

---

## 字典序

​	C语言中，对字符串进行字典序比较时

​	通常使用 `strcmp` 函数而不是直接使用比较运算符（如 `<=`）

​	比较运算符会直接比较字符串的内存地址

### 	`strcmp`

​		`int result = strcmp(str1,str2);`

- 如果 `str1` 小于 `str2`，则返回一个负数（通常是 -1）。
- 如果 `str1` 等于 `str2`，则返回零。
- 如果 `str1` 大于 `str2`，则返回一个正数（通常是 1）

# 类

##  非静态函数

​	没有加static的成员函数是非静态成员函数

​	非静态函数的第一个参数默认是this

​	**<u>此类函数的调用必须与类的特定对象相对！！！</u>**



```c++
class A{
    static int _cout;
public:
	int mycout() {//非静态函数
		return _cout;
	}
}
int A::_cout = 0; //给类的静态变量赋值时必须加上类作用域
//静态成员变量的定义必须在类的外部进行

int main() {
    A a1;
    cout << A::mycout << endl; //这样写错误，会报错"非静态成员引用必须与特定对象相对"
    cout << a1.mycout << endl; //正确写法
}
```

##  静态函数

​	与非静态函数相反，无需与特定对象相对

​	**注意：**

- 静态函数没有this指针，
- 静态函数不能直接访问非静态成员
  - 如果要访问非静态成员，可以通过以下方式：
    1. 将非静态成员变量作为参数传递给静态成员函数
    2. 在静态成员函数内部创建一个类的对象，然后使用该对象的成员访问非静态成员变量

```c++
class A{
    static int _cout;
public:
	static int mycout() {//静态函数
		return _cout;
	}
}
int A::_cout = 0; //给类的静态变量赋值时必须加上类作用域

int main() {
    cout << A::mycout << endl; //正确写法
}
```

> #### 总结
>
> ​	静态的意思就是拥有者是类：**无论是静态变量还是静态成员函数，都不会因为特定对象的改变而改变**

## 友元函数

- 可以访问类的私有成员，但是他不是成员函数(也就是没有this指针)
- 不能用const修饰
- 友元函数可以在类的任意地方声明(一般写在public上面)，不受访问限定符的限制
- 一个函数可以是多个类的友元函数
- 友元函数的调用和普通函数一样

##  友元类

​	若想直接访问另一个类的私有成员，可直接设置为友元类

​	减少使用，友元类会破坏封装

```c++
class Date {
	int _hour;  	  
};
class Time{
	friend class Date;  //这样写Time就可以访问Date的_hour
    //注意设置友元类前要声明要作为友元的类
};
```

##  内部类

- 内部类就是B这个类定义在A这个类之内，B就叫做内部类，B天生就是A的友元
- 内部类可以访问外部类的成员变量，但外部类不能访问内部类
- 内部类可以保护封装

## 运算符重载

- 重载函数依然是成员函数，有this指针作为参数，使用时要省略第一个参数
- 赋值运算符等记得引用(&)

## 虚析构函数

> #### 	在 C++ 中，声明一个虚析构函数（virtual destructor）是为了确保在通过基类指针<u>删除派生类对象</u>时，派生类的析构函数能够正确地被调用。这样可以避免资源泄漏和未定义行为。

### 为什么需要虚析构函数

> #### 	当一个基类指针指向一个派生类对象，并且通过这个基类指针来删除对象时，如果基类的析构函数不是虚函数，只有基类的析构函数会被调用，而派生类的析构函数将不会被调用。这可能导致派生类中分配的资源无法被正确释放，进而造成资源泄漏。

## 常见问题

- 构造函数运行顺序是从内到外
- 析构函数运行顺序是从外到内
- 当一个类中有多个对象成员时 ，对象成员的构造函数调用顺序取决于<u>对象成员在类中声明的顺序</u>





# 泛型编程

##  模板

```c++
template<class T>
void Myswap(T& a, T& b) {
	T temp = a;
	a = b;
	b = a;
}
int main() {
	int a1, a2;
    //各种数据类型都可以用，因为模板定义为类型T
    double b1, b1;
	Myswap(a1, a2);
    Myswap(b1, b2);
    Myswap<int>(a1, b1);//显式转化，注意此时函数就不能引用&
}
```

​	当传入的数据类型相同时，编译器会帮你进行隐式转化

​	若数据类型不同，则编译器会报错，需要手动显式转化

### 2024.6.19补充

```c++
Tempplate<typename T>
T min(T temp[], int b) {
    T min = temp[0];
    for(int i = 1;i < b; i++) {
        if (min > temp[i])
            min = temp[i];
    }
    return min;
}
```

# 内存 

## C语言内存

-  malloc：向内存申请一块连续可用的空间，并返回这块空间的指针，没有初始化
-  calloc：同malloc，但进行初始化，使每个字节初始化为0
- realloc：当malloc申请的空间不够用时，用realloc调整
- free()：释放动态开辟的内存

> c++中使用c语言内存申请方式不会默认调用类的构造函数和析构函数

##  C++内存

- new int	//申请内存，不初始化
- new int(10)    //申请内存，并初始化
- delete()     //释放内存

---

# 动态规划

> **“从底至顶”的方法**：
>
> 从最小子问题的解开始，迭代地构建更大子问题的解，直至得到原问题的解

## 算法对比

- 分治算法递归地将原问题划分为多个相互独立的子问题，直至最小子问题，并在回溯中合并子问题的解，最终得到原问题的解。
- 动态规划也对问题进行递归分解，但与分治算法的主要区别是，动态规划中的子问题是相互依赖的，在分解过程中会出现许多重叠子问题。
- 回溯算法在尝试和回退中穷举所有可能的解，并通过剪枝避免不必要的搜索分支。原问题的解由一系列决策步骤构成，我们可以将每个决策步骤之前的子序列看作一个子问题。

##  两大特性

- 最优子结构：**原问题的最优解是从子问题的最优解构建得来的**
- 无后效性：**给定一个确定的状态，它的未来发展只与当前状态有关，而与过去经历的所有状态无关**（值得体会）
  - 当不满足无后效性时，需要扩展状态定义来满足无后效性(也就是特判，有效区分状态定义)
  - 当具有严重的“有后效性”时，不适合使用动态规划

##  问题判断

1. 放宽条件，**先观察问题是否适合使用回溯（穷举）解决**
2. ”加分项“
   1. 问题包含最大（小）或最多（少）等**最优化**描述。
   2. 问题的状态能够使用一个列表、多维矩阵或树来表示，并且**一个状态与其周围的状态存在递推关系**
3. “减分项”
   1. 问题的目标是**找出所有可能的解决方案**，而不是找出最优解
   2. 问题描述中有**明显的排列组合的特征**，需要返回具体的多个方案

##  通用步骤

1. **描述决策**：思考每轮决策(最重要一步，也是最难一步)
2. **定义状态**
3. **建立 DP 表**：找出最优子结构
4. **推导状态转移方程**
5. **确定边界条件以及状态转移顺序**
   1. 边界条件在动态规划中用于初始化 DP 表，在搜索中用于剪枝
   2. 状态转移顺序的核心是要保证在计算当前问题的解时，所有它依赖的更小子问题的解都已经被正确地计算出来

##  思维顺序

> 子问题分解是一种从顶至底的思想

1. 暴力搜索：**寻找造成重叠子问题的原因**(e.g : 存在多条路径可以从左上角到达某一单元格)
2. 记忆化搜索：**记录各个子问题的解，并将重叠子问题进行剪枝**
3. 动态规划：将记忆化搜索的递归法**用迭代实现**，提高效率
4. 空间优化：继续优化，找到**最优子结构的核心**

##  0-1背包

###   步骤

1. 思考每轮决策，定义状态，从而得到DP表
2. 找出最优子结构，进而推导出状态转移方程
3. 确定边界条件和状态转移顺序

```c++
int knapsackDP(vector<int> &wgt, vector<int> &val, int cap) {
    int n = wgt.size();
    // 初始化 dp 表
    vector<vector<int>> dp(n + 1, vector<int>(cap + 1, 0));
    // 状态转移
    for (int i = 1; i <= n; i++) {
        for (int c = 1; c <= cap; c++) {
            if (wgt[i - 1] > c) {
                // 若超过背包容量，则不选物品 i
                dp[i][c] = dp[i - 1][c];
            } else {
                // 不选和选物品 i 这两种方案的较大值
                dp[i][c] = max(dp[i - 1][c], dp[i - 1][c - wgt[i - 1]] + val[i - 1]);
            }
        }
    }
    return dp[n][cap];
}
```

###  空间优化

- 观察可知，每个状态都是由正上方或左上方的格子转移过来的。假设只有一个数组，当开始遍历第 `i` 行时，该数组存储的仍然是第 `i−1` 行的状态
- 必须使用逆序遍历，当前状态是由正上方或左上方的状态转移过来的，而左上方储存的是放上一个物品的状态，如果正序遍历就会导致当前状态是由放当前物品的转移的造成结果偏大

```c++
int knapsackDPComp(vector<int> &wgt, vector<int> &val, int cap) {
    int n = wgt.size();
    // 初始化 dp 表
    vector<int> dp(cap + 1, 0);
    // 状态转移
    for (int i = 1; i <= n; i++) {
        // 倒序遍历
        for (int c = cap; c >= 1; c--) {
            if (wgt[i - 1] <= c) {
                // 不选和选物品 i 这两种方案的较大值
                dp[c] = max(dp[c], dp[c - wgt[i - 1]] + val[i - 1]);
            }
        }
    }
    return dp[cap];
}
```

##  完全背包

> 每种物品的数量是无限的，因此将物品 i 放入背包后，**仍可以从前 i 个物品中选择**

```c++
int unboundedKnapsackDP(vector<int> &wgt, vector<int> &val, int cap) {
    int n = wgt.size();
    // 初始化 dp 表
    vector<vector<int>> dp(n + 1, vector<int>(cap + 1, 0));
    // 状态转移
    for (int i = 1; i <= n; i++) {
        for (int c = 1; c <= cap; c++) {
            if (wgt[i - 1] > c) {
                // 若超过背包容量，则不选物品 i
                dp[i][c] = dp[i - 1][c];
            } else {
                // 不选和选物品 i 这两种方案的较大值
                dp[i][c] = max(dp[i - 1][c], dp[i][c - wgt[i - 1]] + val[i - 1]);
            }
        }
    }
    return dp[n][cap];
}
```

- 由于每个物品不止可以放一次，所以前一次对当前物品的选择会影响当下的选择
- 应是`dp[i][c-wgt[i-1]]+val[i-1]`而不是`dp[i-1][c - wgt[i - 1]] + val[i - 1]`

###  空间优化

```c++
int unboundedKnapsackDPComp(vector<int> &wgt, vector<int> &val, int cap) {
    int n = wgt.size();
    // 初始化 dp 表
    vector<int> dp(cap + 1, 0);
    // 状态转移
    for (int i = 1; i <= n; i++) {
        for (int c = 1; c <= cap; c++) {
            if (wgt[i - 1] > c) {
                // 若超过背包容量，则不选物品 i
                dp[c] = dp[c];
            } else {
                // 不选和选物品 i 这两种方案的较大值
                dp[c] = max(dp[c], dp[c - wgt[i - 1]] + val[i - 1]);
            }
        }
    }
    return dp[cap];
}
```

- 同样由于每个物品不止可以放一次，所以要进行正序遍历

# Dijkstra

> 路径规划算法中非常经典的一种算法，在很多地方都会用到
>
> 特别是在机器人的路径规划中，基本学习机器人运动相关的都会接触到该算法

##  简介

- 基于贪心思想实现的，首先把起点到所有点的距离存下来找个最短的，然后**松弛一次**再找出最短的
- 松弛操作就是：
  1. 遍历一遍看通过刚刚找到的距离最短的点作为中转站会不会更近，
  2. 如果更近了就更新距离，这样把所有的点找遍之后就存下了起点到其他所有点的最短距离
- 典型最短路径算法，用于计算一个节点到其他节点的最短路径
- 主要特点是以起始点为中心向外层层扩展(广度优先搜索思想)，直到扩展到终点为止
- 很有代表性的最短路径规划算法。一般的表述通常有两种方式：
  - 一种用永久和临时标号方式，
  - 一种是用OPEN, CLOSE表方式
  - 路径规划采用OPEN,CLOSE表的方式

##  思路

1. **指定一个节点**（例如我们要计算 ‘A’ 到其他节点的最短路径）
2. 引入两个集合（S、U）
   - S集合包含已求出的最短路径的点（以及相应的最短长度），
   - U集合包含未求出最短路径的点（以及A到该点的路径，注意 如上图所示，A->C由于没有直接相连 初始时为∞）
3. 初始化两个集合，
   - S集合初始时 只有当前要计算的节点，A->A = 0，
   - U集合初始时为 A->B = 4, A->C = ∞, A->D = 2, A->E = ∞，<u>敲黑板！！！接下来要进行核心两步骤了</u>
4. 从**U集合中找出路径最短的点**，**加入S集合**，例如 A->D = 2
5. **更新U集合路径**，if ( ‘D 到 B,C,E 的距离’ + ‘AD 距离’ < ‘A 到 B,C,E 的距离’ ) 则更新U
6. 循环执行 4、5 两步骤，直至遍历结束，得到A 到其他节点的最短路径

![在这里插入图片描述](https://img-blog.csdnimg.cn/4a612d2436bf4d6d8b915a628f7b15af.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5LiA5Y-25omn5b-1,size_20,color_FFFFFF,t_70,g_se,x_16)

<img src="https://img-blog.csdnimg.cn/8509fecc858642b4ae2f4fe866dea7b7.gif#pic_center" alt="在这里插入图片描述"  />

##  1.0   O(n * n)

```c++
#include<iostream>
using namespace std;
//vis[]表示是否被选取了，dis[]表示离源点距离 ，g[][]存储点与点之间距离
const int N = 510, inf = 0x3f3f3f3f;
bool vis[N];
int dis[N], g[N][N], n, m;

int Dijkstra(){
	//初始化源点为1
    dis[1] = 0;
    //从未被选取的点当中选取到达源点最近的点
    for(int i = 0; i < n; i ++ ){
        int t = -1;
        for(int j = 1; j <= n; j ++ ){
            if ( !vis[j] && (t == -1 || dis[j] < dis[t] ) ) 
                t = j;
        
        vis[t] = true;
        //利用这个选取的源点去更新其他未被访问的点
        for(int j = 1; j <= n; j ++ )
            //如果当前`t`点到`j`点 大于 到t点加t到j的距离，就更新t到j的距离为更短的
            if(!vis[j] && dis[j] > dis[t] + g[t][j] )
                dis[j] = dis[t] + g[t][j];
    }
    
    if(dis[n] == inf ) puts("-1");
    else cout << dis[n] << endl;
}

int main(){
	//全部初始化为inf,表示不可以到达
    fill(dis, dis + N, inf );
    fill(g[0], g[0] + N * N, inf );
	
    cin >> n >> m;
    for(int i = 0; i < m; i ++ ){
        int x, y, s;
        cin >> x >> y >> s;
        //保存点与点之间的最短路径关系即可
        g[x][y] = min(s, g[x][y] );
    }
    
    Dijkstra();
}
```



# 字符串

##  方法

###   转小写

```c++
transform(my_post[i].test_text.begin(), 
        my_post[i].test_text.end(), my_post[i].test_text.begin(), ::tolower);
```

注意：4个参数

###  string查找

```c++
string s；
size_t index = s.find("250");
```

- `size_t` 是 C/C++ 中用于表示大小或索引的数据类型。它通常被用作数组索引或者字符串搜索函数的返回类型
- index` 的类型是 `size_t`，因为 `string::find` 函数返回的就是 `size_t

# 并查集

## e.g

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/352e6b2c78598125cb0ff37af4d1137e.png)

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/309a991d440bfad56b415e4fc079daab.png)

- 数组元素储存其父节点，

- 快速查找根节点
- 实现合并，查找功能

```c++
class UnionFind {
public:
    vector<int> parent;

    UnionFind(int n) {
        parent.resize(n);
        for (int i = 0; i < n; i++)
            parent[i] = i;
    }

    void unionSet(int index1, int index2) {
        parent[find(index2)] = find(index1);
    }

    int find (int index) { // 递归版find1
        if (parent[index] != index)
            parent[x] = find(parent[x]); // 路径压缩
        return parent[index];
    }
    int find (int index) { // 迭代版find
        while (parent[index] != index) 
            index = parent[index];
        return index
    }
};
```

1. 构造函数：初始化，每个节点的父节点是自己
2. unionSet函数：设置父节点（index2的根节点的根节点设置为index1的根节点）
3. find函数：查找当前节点的根节点

# 命名空间

- `namespace`一种解决全局变量和函数名冲突的机制

- 关键点

  1. 如何解决冲突
  2. 如何合法访问变量

- 分类

  1. 标准命名空间

     `using namespace std;`

  2. 自定义命名空间

     ```c++
     namespace test {
     	int a;
     }
     namespace { //匿名命名空间
         struct std{};// 可能引起歧义，gcc有bug，msvc和clang的行为是一样的，不能通过编译
     }
     /*
     通过::std::来全局访问
     */
     ```




# 图论

- 入度和出度的概念：

  如果存在一条有向边 A --> B，则这条边给 A 增加了 1 个出度，给 B 增加了 1 个入度。

- **有向无环图**，把一个 有向无环图 转成 线性的排序 就叫 **拓扑排序**。

- 邻接表

  用哈希表记录依赖关系（也可以用二维矩阵，但有点大）

  - key：当前节点
  - value：neighbors

## 图的遍历

[133. 克隆图](https://leetcode.cn/problems/clone-graph/)

```c++
/*
// Definition for a Node.
class Node {
public:
    int val;
    vector<Node*> neighbors;
    Node() {
        val = 0;
        neighbors = vector<Node*>();
    }
    Node(int _val) {
        val = _val;
        neighbors = vector<Node*>();
    }
    Node(int _val, vector<Node*> _neighbors) {
        val = _val;
        neighbors = _neighbors;
    }
};
*/

class Solution {
public:
    //哈希表储存访问过的节点
    unordered_map<Node*, Node*> visited;
    Node* cloneGraph(Node* node) {
        if (node == nullptr)
            return node;
        
        //为了防止重复访问，当节点访问过时直接返回其克隆节点
        if (visited.find(node) != visited.end()) 
            return visited[node];
        //返回其克隆节点是为了深拷贝，因为该节点访问过，所以其邻居数组早已完善
        
        //为了深拷贝，新建对象不克隆其邻居
        Node* cloneNode = new Node(node->val);
        //将当前节点储存
        visited[node] = cloneNode;

        //遍历原图节点的邻居，并添加到克隆节点
        for (auto& neighbor : node->neighbors) 
            cloneNode->neighbors.emplace_back(cloneGraph(neighbor));
        return cloneNode;
    }
};
```

## 拓扑排序

> <u>有向无环图</u>一定是拓扑序列,有向有环图一定不是拓扑序列。
>
> <u>无向图</u>没有拓扑序列。

### 证明拓扑排序

1. 首先记录各个点的入度
2. 然后将入度为 0 的点放入队列
3. 将队列里的点依次出队列，然后找出所有出队列这个点发出的边，删除边，同时边的另一侧的点的入度 -1。
4. 如果所有点都进过队列，则可以拓扑排序，输出所有顶点。否则输出-1，代表不可以进行拓扑排序。



# 补充

2025年5月31日 第一次 `丕锐科技`笔试

1. ![PixPin_2025-05-31_14-12-41](D:\refines\refines\PixPin_2025-05-31_14-12-41.png)

   1. A: 错误；
      在 C/C++ 中，**不同类型的指针不能直接赋值**，如将 `int*` 赋值给 `double*` 是不允许的，`必须进行` **`强制类型转换`**。所以该项错误。
   2. B: 正确；
      空指针（`NULL` 或 `nullptr`）指向的是地址为 0 的地方，这个地址通常是受保护的，`不能访问`。**一旦解引用空指针，会导致`运行时错误`（例如“段错误”）**。虽然不是在编译时报错，但运行时会“出错”。
   3. C: 错误
       `p = 0;`，那么这在 `C 中是合法的`（C 中 `0` 可表示空指针）。但现代 C++ 推荐使用 `nullptr`。至于 `p = NULL;`，虽然合法，但不是唯一合法的写法。因此该项表述不清且有误。
   4. D: 错误
      **`指针是可以比较的`**，尤其是在它们`指向同一数组或对象范围内`时，可以使用 `==`, `!=`, `<`, `>`, `<=`, `>=` 等运算符进行比较，如可以进行地址大小比较。所以这项错误。

2. ![PixPin_2025-05-31_14-15-05](D:\refines\refines\PixPin_2025-05-31_14-15-05.png)

   1. `printf("%x, %o, ", ch, ch, k);`
      1. `%x`：将 `ch` 按 16 进制输出，即 `97` 的十六进制是 `61`。
      2. `%o`：将 `ch` 按 8 进制输出，即 `97` 的八进制是 `141`。
      3. 所以前一条语句输出：`61, 141,`
      4. `k` 虽然作为参数传入，但并没有匹配的格式说明符 `%d`，因此该参数**未被使用**，但这在`某些编译器中不会报错`，只是浪费一个参数。
      5. 字符型变量 `ch` 用 `%x` 和 `%o` 输出是合法的，因为在 C 中 `char` 在传给 `printf` 时会被自动提升为 `int`。
   2. `printf("k=%%dn", k);`
      - `"%%d"` 中 `%%` 输出一个 `%`，所以实际上这变成了：`"k=%dn"`（转义）
      - 所以输出为：`k=%dn`（注意这里 **没有格式替换**，`k` 被作为参数传入，但没有匹配的 `%d`，只是原样输出字符串）
   3. 正确答案是C

3. ![PixPin_2025-05-31_14-17-00](D:\refines\refines\PixPin_2025-05-31_14-17-00.png)

   1. ```c++
      ((B *)(&c)) -> func();
      ```

      - `((B*)(&c))`：将`c`的地址强转为`B*`，这是向上转型`upcasting`，因为`B`是`C`的父类，所以是合法的，然后调用`func()`
      - 因为`func()`是虚函数，实际运行时会调用`C::Test()`（运行时多态）
      - 因为指针是`B*`，但指向的是一个`c`对象，所以虚函数机制生效。

   2. > 总结：**以 `B\*` 的身份调用 `func()`，从而通过虚函数机制最终调用了 `C::Test()`**。

   3. 所以运行结果是

      ```bash
      C testn
      B testn
      ```

      

4. <img src="D:\refines\refines\PixPin_2025-05-31_14-20-32.png" alt="PixPin_2025-05-31_14-20-32" style="zoom:67%;" />

   1. 什么是按字节对齐(`Byte Alignment`)

      1. 按字节对齐是指`编译器`为了`提升CPU访问效率`，对结构体（struct/class）或联合体（union）中的`成员`在`内
         存中`的`排列方式`做出的`优化策略`。

      2. 简单说，就是为了让CPU 以高效的方式访问数据，会在结构体成员之间`插入一些"填充字节`（padding）",
         使得每个成员的起始地址`满足一定的对齐规则`。

      3. 如何使用？

         1. 使用`#pragma pack`指令（跨平台支持较好）

            1. ```C++
               // 设置为1字节对齐
               #pragma pack(push, 1)
               
               struct Test {
               	char a;
               	int b;
               	char c;
               };
               
               // 恢复默认对齐
               #pragma pack(pop)
               ```

            2. 上面设置后`sizeof(Test）=6`。

         2. 使用`GCC`的`__attribute_((packed))`

            1. ```c++
               struct _attribute((packed)) Test {
               	char a;
               	int b;
               	char c;
               };
               ```

      4. 什么时候需要手动控制对齐？

         1. **读写二进制文件**：希望结构体和文件内容一一对应，不希望填充字节。
         2. **通信协议数据结构**：与硬件或网络打交道时，结构必须精确匹配。
         3. **节省内存空间**：嵌入式开发场景对字节很敏感。

   2. 分析类的成员：

      1. 成员变量：
         1. `char m_chData`：1字节
         2. `int m_nData`：4字节
      2. 静态成员变量：
         1. `static char s_chData`
         2. 不占实例内存大小
      3. 类存在虚函数，导致类内有一个虚函数表指针`(vptr)`，大小是4字节

   3. 按4字节对齐

      1. `vptr`(虚表指针)：4字节
      2. `m_chData`：1字节 + 3字节
         由于4字节对齐，后面的`m_nData`需要在4字节对齐的地址上，因此`m_chData`后面需要3字节填充
      3. `m_nData`：4字节
      4. 总大小：4 + 1 + 3 + 4 = 12 字节

   4. 按1字节对齐

      1. 没有任何填充，所有成员顺序紧密排列
      2. `m_nData`：4字节
      3. `vptr`(虚表指针)：4字节
      4. `m_chData`：1字节 
      5. 总大小：4 + 4 + 1 = 9 字节

   5. 正确答案：C

5. ![PixPin_2025-05-31_14-23-38](D:\Desktop\PixPin_2025-05-31_14-23-38.png)

   1. A．static类变量又叫`静态成员变量`，它`不需要创建对象`就可以`已经在内存中存在`了

      **正确**

      - 静态成员变量属于类本身，不依赖于任何对象实例。
      - 程序`开始运行时`，`静态成员变量``已存在于内存中`。

   2. B．在创建实例对象的时候，内存中会为`每一个实例对象`的`每一个非静态成员变量开辟一段内存空间`，用来存储这个对象所有的非静态成员变量值

      **正确**

      - 每个对象都有自己独立的非静态成员变量。
      - 不同对象的非静态成员变量存储空间彼此独立。

   3. static类变量是所有对象共有，其中一个对象将它值改变，其他对象得到的就是改变后的结果

      **正确**

      - 静态成员变量被所有对象共享，修改会影响所有对象。

   4. 实例变量则属对象私有，某一个对象将其值改变，不影响其他对象

      **正确**

      - 非静态成员变量是对象的私有属性，修改一个对象的成员变量不会影响其他对象。

6. ![PixPin_2025-05-31_14-24-49](D:\refines\refines\PixPin_2025-05-31_14-24-49.png)

   1. A．可以在类的声明中给数据成员赋初值 (C++11新标准)

      **正确**

      - C++11 标准允许在类内直接给非静态数据成员赋初值，称为**内联初始化**。

      - 例如：

        ```c++
        class A {
            int x = 10;
        };
        ```

   2. B．数据成员的数据类型可以是 register

      **错误**

      - `register` 不是数据类型，而是存储类型说明符（storage class specifier），用于局部变量提示存储在寄存器。
      - **不能用 `register` 修饰类的数据成员**，语法不允许。

7. ![PixPin_2025-05-31_14-26-46](D:\refines\refines\PixPin_2025-05-31_14-26-46.png)

   1. A．**static 表示这个变量可以在其他文件中使用**

      ❌ **错误**

      - `static` 的作用是**`限制变量或函数的链接性为内部链接`**，即**只能在当前文件中使用**，不能在其他文件访问。
      - 所以，**static 是“限制外部使用”**，不是“允许外部使用”。

   2. B．**static 变量连接期被分配到了 data 段，即使是在函数调用中定义也不会在栈中产生，而是在程序加载期就被加入了内存**

      ✅ **基本正确**

      - 在函数中声明的 `static` 局部变量，只初始化一次，生命周期贯穿程序运行。
      - 它们通常存储在 `.data` 或 `.bss` 段，而不是栈上，也不会随函数调用次数重复创建。
      - 程序加载时，这些变量就已经被分配了内存。

   3. C．**const 表面含义是个常量，但实际上还是占据一个内存位置的变量，但是它的值一般是在编译时期就决定了**

      ✅ **基本正确**

      - `const` 修饰的变量确实是**`不可更改的值`**，但**它`本质仍然是一个变量`，`有自己的内存地址`**（除非是编译器优化掉了）。
      - 对于局部 `const int a = 3;` 这类字面值常量，编译器**可能优化成立即数**，不分配内存。
      - 但如果是 `const char* str = "abc";`，`str` 仍然是有地址的，常量存在只读数据段。

8. ![PixPin_2025-05-31_14-28-24](D:\refines\refines\PixPin_2025-05-31_14-28-24.png)

   1. A．子类必须重载父类里的虚函数     **错误**

      - 虚函数是`允许子类重写`（重载），但`不是必须重写`。
      - 如果子类不重写，调用时`仍调用父类`的实现。

   2. B．子类必须重载父类里的纯虚函数      **正确**

      - `纯虚函数`是`没有实现的虚函数`，声明形式为 `virtual void f() = 0;`。
      - 子类`必须重写`（实现）所有纯虚函数，否则`子类本身也是抽象类`，`不能实例化`。

   3. C．虚基类的构造函数在非虚基类之前调用    **错误**

      - `构造函数调用顺序`：
        1. `虚基类构造`函数`先调用`
        2. `非虚基类`构造函数`后调用`
      - 所以是`虚基类`构造函数**`先于`**`非虚基类`构造函数调用。

   4. D．带有纯虚函数的类不能直接实例化

      **正确**

      - 含有纯虚函数的类是抽象类，**不能实例化对象**。

9. <img src="D:\refines\refines\PixPin_2025-05-31_14-28-28.png" alt="PixPin_2025-05-31_14-28-28" style="zoom:67%;" />

   1. A：数组越界是一定的
   2. C：数组开太大才可能栈溢出
   3. D：内存泄漏（Memory Leak）是指程序在运行过程中，**动态分配的内存没有被释放**，导致这部分内存无法再被程序使用，最终造成内存资源浪费，甚至程序崩溃。

10. <img src="D:\refines\refines\PixPin_2025-05-31_14-30-40.png" alt="PixPin_2025-05-31_14-30-40" style="zoom:67%;" />

    1. `union`

       1. `union`的所有成员共享同一块内存
       2. **这块内存的大小是由`最大成员`的`大小决定`的**。
       3. 联合体的总大小 = 所有成员中**最大者所需的大小**
       4. `int32_t` 是一个标准的 32 位整数，**占 4 字节**。

    2. ```c++
       union X {
           int32_t a;
           struct {
               int16_t b;
               int16_t c;
           };
       };
       ```

       - 这个联合体 `X` 占用的内存大小是 **4 字节**（因为 `int32_t` 是 4 字节），`a`、`b` 和 `c` 共用这 4 字节的内存空间。
       - 结构体中的 `b` 和 `c` 各占16位，正好组成32位

    3. 内存中 `0x20150810` 的存储方式取决于系统的字节序：

    4. `x.a = 0x20150810`

       这是一个32位的十六进制数：

       - 二进制表示：`0010 0000 0001 0101 0000 1000 0001 0000`
       - 按字节分解：`20` `15` `08` `10`

    5. **小端序系统 (Little Endian)**：

       - 内存中存储为：`10 08 15 20`

       - **内存布局（从低地址到高地址）：**

         ```c++
         地址:  [0] [1] [2] [3]
         内容:   10  08  15  20
         ```

       - ```c++
         x.b：读取前2个字节 `[0][1] = 10 08
         ```

         - 小端序解释：低字节在前，所以值为 `0x0810`
         - 十进制：2064，十六进制输出：`810`

       - ```c++
         x.c：读取后2个字节 [2][3] = 15 20
         ```

         - 小端序解释：低字节在前，所以值为 `0x2015`
         - 十进制：8213，十六进制输出：`2015`

       - `x.b` (低16位) = `0x0810`

       - `x.c` (高16位) = `0x2015`

       - 输出：`810, 2015`

    6. **大端序系统 (Big Endian)**：

       - **内存布局（从低地址到高地址）：**

         ```
         地址:  [0] [1] [2] [3]
         内容:   20  15  08  10
         ```

         - x.b：读取前2个字节 `[0][1] = 20 15`
           - 大端序解释：高字节在前，所以值为 `0x2015`
           - 十进制：8213，十六进制输出：`2015`

         - `x.c`：读取后2个字节 `[2][3] = 08 10`：
           - 大端序解释：高字节在前，所以值为 `0x0810`
           - 十进制：2064，十六进制输出：`810`

       - 内存中存储为：`20 15 08 10`

       - `x.b` (前16位) = `0x2015`

       - `x.c` (后16位) = `0x0810`

       - 输出：`2015, 810`

    7. 从给出的选项看：

       - A. `2015, 810` - 对应大端序
       - C. `810, 2015` - 对应小端序

    8. 由于现代大多数系统（x86/x64）都是小端序，最可能的输出是 `810, 2015`。

11. ![PixPin_2025-05-31_13-49-30](D:\refines\refines\PixPin_2025-05-31_13-49-30.png)

    1. `std::vector<T>::at(size_type pos)`
        这个函数在访问元素时会**`进行边界检查`**，如果索引 `pos` 超出了合法范围（即 `pos >= vector.size()`），会抛出一个 `std::out_of_range` 异常。
    2. `std::vector<T>::operator[](size_type pos)`
        这个运算符不会进行边界检查，如果访问了非法索引，程序行为是**`未定义的`**，可能会导致崩溃或错误结果，但`不会抛出异常`。

12. ![PixPin_2025-05-31_14-09-34](D:\refines\refines\PixPin_2025-05-31_14-09-34.png)

    1. 结构体内存分配原理

       结构体变量的内存大小**基本上**是`各成员所需内存量的总和`，但还需要考虑**`内存对齐`**的影响。

13. <img src="D:\refines\refines\PixPin_2025-05-31_14-32-47.png" alt="PixPin_2025-05-31_14-32-47" style="zoom:67%;" />

    1. 无论函数返回类型是 `char` 还是 `int`：
       - 第二空都是：`ch<='9'`
       - 第三空都应该是：`'0'`（字符常量，不是数字0）
       - 因为这里进行的是**字符运算**，需要将字符转换为数字值，所以必须用字符常量 `'0'`。
       - `char`型与`int`运算时是其对应的ASCLL码与`int`运算，所以`0`必须加引号才能返回正确的ASCLL码值

14. <img src="D:\refines\refines\PixPin_2025-05-31_14-34-16.png" alt="PixPin_2025-05-31_14-34-16" style="zoom:67%;" />

    1. 每次循环后，`k` 的值为：

       - `k = 1 + 2 + 3 + ... + i`

       - 这是等差数列求和：`k = i(i+1)/2`

    2. 循环终止条件

       循环在 `k ≥ n` 时终止，即： `i(i+1)/2 ≥ n`

       解这个不等式：

       - `i² + i ≥ 2n`
       - `i² ≥ 2n`（近似）
       - `i ≥ √(2n)`

    3. 时间复杂度分析

       - 循环执行次数约为 `√(2n)`，即 `O(√n)`

       - 由于 `√n = n^(1/2)`，所以时间复杂度为 `O(n^(1/2))`

15. <img src="D:\refines\refines\PixPin_2025-05-31_14-34-20.png" alt="PixPin_2025-05-31_14-34-20" style="zoom:67%;" />

    1. `B-树`

       1. B-树是一种**`多路平衡搜索树`**，与二叉树有本质区别：

          1. **B-树`不是二叉树`**

             - 每个节点可以`有多个关键字`（最多m-1个）
             - 每个节点可以`有多个子树`（最多m个）
             - 不存在传统意义上的"左右子树"概念

          2. **B-树的平衡性**

             - B-树确实是`平衡的`
             - 但这种平衡是指：**`所有叶子节点都在同一层`**
             - 不是指某个节点的"左右子树"高度相等

          3. 举例说明

             假设一个3阶B-树的节点结构：

             ```c
                 [10, 20]
                /    |    \
              子树1  子树2  子树3
             ```

          4. 这个节点有3个子树，而不是2个，所以"左右子树"的概念不适用。

          5. B-树的平衡性体现在：

             - 所有`叶子节点在同一层`
             - 每个节点的`关键字数量`在`规定范围内`
             - 整体保持`平衡`，搜索效率`稳定`

16. ![PixPin_2025-05-31_14-37-21](D:\refines\refines\PixPin_2025-05-31_14-37-21.png)

    1. 最优算法：多路归并

       使用 **最小堆（优先队列）** 进行多路归并：

       算法步骤：

       1. 建立大小为 m 的最小堆

       2. 将每个数组的第一个元素放入堆中

       3. 重复以下操作直到所有元素处理完：

          - 取堆顶元素（最小值）放入结果数组
          - 从该元素所属数组取下一个元素放入堆
          - 调整堆结构

       4. 时间复杂度分析：

          **总操作次数：** mn 个元素需要处理

          **每次操作的复杂度：**

          - 从堆中取出最小元素：`O(log m)`
          - 向堆中插入新元素：`O(log m)`
          - 每个元素的处理成本：`O(log m)`

          **总时间复杂度：** `O(mn · log m)`

17. <img src="D:\refines\refines\PixPin_2025-05-31_13-49-55.png" alt="PixPin_2025-05-31_13-49-55" style="zoom:67%;" />

    1. 答案：C. 只有构造函数可以

    2. 构造函数可以抛出异常 ✓

       **原因：**

       - 构造函数抛出异常时，对象创建失败
       - 已构造的部分会自动调用析构函数清理
       - 内存会被正确释放
       - 这是处理构造失败的标准机制

    3. 析构函数不应该抛出异常 ✗

       **原因：**

       1. **栈展开问题**：当异常发生时，栈展开过程中会调用析构函数，如果析构函数再抛异常会导致程序terminate
       2. **容器安全**：STL容器依赖析构函数不抛异常的保证
       3. **RAII模式**：资源清理应该是可靠的操作

    4. **C++11标准：**

       - 析构函数默认被声明为 `noexcept`
       - 如果析构函数抛出异常，程序会调用 `std::terminate`

    5. 总结

       - **构造函数**：可以抛异常，这是正常的错误处理机制
       - **析构函数**：不应该抛异常，违反会导致程序终止

18. <img src="D:\refines\refines\PixPin_2025-05-31_13-52-36.png" alt="PixPin_2025-05-31_13-52-36" style="zoom:67%;" />

    1. 答案：`C` gets(str);

    2. `gets()` 可以读取包含空格的整行字符串,直到遇到换行符才停止

    3. **注意：** `gets()` 函数存在缓冲区溢出风险，在C11标准中已被移除，但在考试题目中仍然被认为是正确答案。

    4. D. `str = gets();` ✗

       **问题：**

       - 语法错误：`gets()` 需要参数（缓冲区地址）
       - `str` 是数组名，不能被赋值
       - `gets()` 返回指针，但用法错误

19. <img src="D:\refines\refines\PixPin_2025-05-31_13-52-50.png" alt="PixPin_2025-05-31_13-52-50" style="zoom:67%;" />

    1. 答案：B. 装载速度快

    2. 动态链接库的主要优点是`共享性`、`开发便利性`和`内存效率`，但在`装载速度`方面确实`不如静态链接快`。

    3. 动态链接库（`DLL`, `Dynamic Link Library`）详解

       **动态链接库**是一种包含代码和数据的`文件`，可以`被多个程序同时使用`，在程序运行时动态加载和链接。

    4. 基本概念

       什么是链接？

       - **静态链接**：`编译时`将库代码直接嵌入到可执行文件中
       - **动态链接**：`运行时`才加载和链接库文件

    5. 工作原理

       1. 编译阶段

       ```c
       // 程序只包含对DLL函数的声明和引用
       extern int add(int a, int b);  // 声明DLL中的函数
       
       int main() {
           int result = add(5, 3);    // 调用DLL函数
           return 0;
       }
       ```

       2. 运行阶段

       ```
       程序启动 → 检查依赖的DLL → 加载DLL到内存 → 解析符号地址 → 执行程序
       ```

    6. 总结

       动态链接库是现代软件开发的重要技术，通过运行时`链接`实现`代码共享`和`模块化`，虽然在启动速度上有所牺牲，但在`资源利用`、`开发效率`和`系统架构`方面带来`显著优势`。

20. <img src="D:\refines\refines\PixPin_2025-05-31_13-53-26.png" alt="PixPin_2025-05-31_13-53-26" style="zoom:67%;" />

    1. 答案：B. 1.2e0.5
    2. A. 0xFF ✓ (正确)
       - **十六进制整数常量**
       - 以 `0x` 或 `0X` 开头
       - `FF` 表示十六进制的255
       - 完全符合C语言语法
    3. B. 1.2e0.5 ✗ (错误)
       - **科学计数法格式错误**
       - 正确的科学计数法：`数字e整数指数`
       - 指数部分必须是**`整数`**，`不能是小数`
       - `0.5` 作为指数是非法的
    4. C. 2L ✓ (正确)
       - **长整型常量**
       - `L` 或 `l` 后缀表示 long 类型
       - `2L` 表示长整型数值2
       - 完全符合C语言语法
    5. D. '72' ✗ 
       - **多字符常量**
       - 标准C语言中字符常量应该只包含一个字符，如 `'7'` 或 `'2'`
       - 但是 `'72'` 在某些编译器中是合法的**多字符常量**
       - 实际值由编译器实现定义（通常是两个字符的ASCII值组合）

21. <img src="D:\refines\refines\PixPin_2025-05-31_13-54-10.png" alt="PixPin_2025-05-31_13-54-10" style="zoom:67%;" />

    1. A. 宏定义`不检查参数正确性`，会有`安全隐患` ✓ (正确)
    2. B. 相反，现代C++`推荐使用const`
    3. C. 宏的嵌套定义过多会影响程序的`可读性`，而且很`容易出错` ✓ (正确)
    4. D. 相对于函数调用，宏定义可以提高程序的运行效率 ✓ (正确)

22. ![PixPin_2025-05-31_13-57-40](D:\refines\refines\PixPin_2025-05-31_13-57-40.png)

    1. 答案：B. `memmove()`

    2. A. `memcpy()` ✗ (有限制)

       **功能：** `复制`指定字节数的`内存块`

       **限制：** **`不能处理内存重叠`**的情况

    3. B. `memmove()` ✓ (完全适用)

       **功能：** 安全地复制内存块，**可以`处理任意内存重叠情况`**

    4. C. memset() ✗ (功能不符)

       **功能：** 将内存块设置为指定值

    5. D. strcpy() ✗ (多重限制)

       **功能：** 复制字符串

23. <img src="D:\refines\refines\PixPin_2025-05-31_14-06-38.png" alt="PixPin_2025-05-31_14-06-38" style="zoom:67%;" />

    1. 基本信息

       - 分辨率：1024 × 640 像素
       - 色彩深度：16位/像素
       - 格式：位图文件（bitmap）

    2. 第一步：计算总像素数

       ```c
       总像素数 = 1024 × 640 = 655,360 像素
       ```

       第二步：计算图像数据大小

       ```c
       每像素 = 16位 = 2字节
       图像数据大小 = 655,360 × 2 = 1,310,720 字节
       ```

       第三步：转换为KB

       ```c
       1,310,720 字节 ÷ 1024 = 1280 KB
       ```

       第四步：考虑位图文件头

       位图文件包含：

       - **文件头**：14字节

       - **信息头**：40字节（标准BITMAPINFOHEADER）

       - **图像数据**：1280KB

       - ```c
         文件头大小 = 14 + 40 = 54 字节 ≈ 0.05KB 总文件大小 ≈ 1280KB + 0.05KB ≈ 1280KB
         ```

         

    

    

    

    

    

