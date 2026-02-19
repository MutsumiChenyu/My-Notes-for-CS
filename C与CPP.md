#### 1.改值
传参时候传入 
```cpp
// 函数定义：加个 &
void swap(int& a, int& b) { 
    int temp = a; 
    a = b; 
    b = temp; 
}
// 调用：像普通变量一样传，不用写 &
swap(x, y);
```
int &a 直接修改a的参数

```C
void print_score(const player* p) {
    if (p == NULL) return; // 还要检查安全性
    printf("%d", p->score); // 必须用箭头
}
```
```cpp
// const Player& p 表示：我引用了这个玩家，但我保证不修改他
void print_score(const Player& p) {
    // p 实际上是指针，但用法上像普通对象
    std::cout << p.score; // 直接用点 (.)，不用箭头 (->)
}

int main() {
    Player me;
    print_score(me); // 零拷贝，极快
}
```

在引用逻辑上，cpp不需要写`player *p` 这种写法来传参数
对于指针对象 传参部分写 ` const player &p`  即可
然后在函数引用部分可以直接用`p`本身 不需要写`*p`或者`p->`这样的写法

在 C++ 中，如果传递的对象不是 `int` / `bool` 这种小类型，而是 `vector`、`string` 或自定义 `class`，**参数永远写成 `const Type&`**。

注意这里的&不是取地址 而是引用 是一种新写法 引用必须有值 所以引用是不需要判断是否为nullptr的 可以直接随便用

总结一下引用的应用场景：
我先用**指针**初始化一个头节点 然后自己写好了这个链表 这里的不用list也不用引用
然后在一切需要引用这种参数的函数都用**引用**的写法

引用 不能用来创建 可以用来对创建的东西进行修改 具有更高的性能（不会创建数据拷贝）

#### 2.STL标准库--容器·迭代器·算法
##### 2.1 动态数组`vector`
```cpp

#include <vector> 这边使用一个vector的头文件

// 定义：创建一个存 Card 的动态数组
std::vector<Card> hand; 

// 1. 尾部插入 (自动扩容)
hand.push_back(card1); 
hand.push_back(card2);

// 2. 访问 (和 C 数组一样)
// 就像 hand[0], 但更安全的是 .at()，越界会报错而不是崩得莫名其妙
Card c = hand[0]; 

// 3. 获取长度
int count = hand.size(); // 不用自己维护 cardcount 变量了！

// 4. 删除 (比如删掉手牌里的第 3 张)
// begin() 是头，+2 就是偏移 2 个位置
hand.erase(hand.begin() + 2); 
// 5. 清空
hand.clear(); // 内存自动标记为可用，不用 free
```
AAA变量名

`AAA.push_back` `AAA.begin()` `AAA.erase` `AAA.clear` `AAA.size`
`hand.erase(hand.begin() + 2); ` 为什么要这么写？ 因为这么写可以很确定的告诉我要删除哪一个 在多种数据结构中 直接写第几个是不好的写法 这样符合“解耦”的思想
##### 2.2 字符串--智能字符数组
cpp有自带的字符串 `include <string>`
`std::string` 可以调用这个数据结构 可以自由相加减 可以自由定义 可以写==
```cpp
#include <string>

std::string name = "Player1";
std::string action = " played ";

// 拼接
std::string log = name + action + "Ace"; // "Player1 played Ace"

// 比较
if (name == "Player1") { ... } // 不需要 strcmp

// 获取 C 风格指针 (为了兼容老 C 接口)
const char* c_str = name.c_str();
```
##### 2.3映射与字典 `std::map`
```cpp
#include <map>
#include <string>

std::map<std::string, int> scoreBoard;

// 插入数据
scoreBoard["Alice"] = 100;
scoreBoard["Bob"] = 85;

// 查找/修改
scoreBoard["Alice"] += 10; // Alice 变成 110

// 检查是否存在
if (scoreBoard.count("Eve") == 0) {
    // Eve 不在榜单上
}
```
可以直接引用一个字典 相当于是dict
标准的写法：`std::map<std::string, int> AAA(变量名)`
先写map 然后写map的对应 一个什么变量对应一个什么变量 最后写你定义的这个字典的名称 **注意一定是先写索引变量 再写内容变量的类型的**
##### 2.4迭代器 Iterators 用在没有下表的容器中
比如用C给每个玩家发牌 你给1号发完牌之后必须要写一个p = p->next
但是有了迭代器就不需要，不用手动移动底层的指针

迭代器替代了这三个东西：
**1. 下标寻址
2.手动解引用 ->
3.边界检查，手动避免越界**

两种遍历：
```cpp
std::vector<int> vec = {10, 20, 30};
// vec.begin() 返回指向第一个元素的迭代器
// vec.end() 返回指向“最后一个元素后面”的迭代器 (哨兵)
for (std::vector<int>::iterator it = vec.begin(); it != vec.end(); ++it) 
{
    std::cout << *it << endl; // *it 取出值
}
```
```cpp
for (int val : vec) 
{
    std::cout << val << endl;
}
```

```cpp
for 
(std::vector<int>::iterator it = vec.begin(); it != vec.end(); ++it) 
{
    std::cout << *it << endl; // *it 取出值
}
```
如何理解这个for循环中的内容：
第一个分号初始化一个迭代器 声明这个迭代器`it`基于vector动态数组 同时告知数据类型为整数型 并且告诉迭代器 迭代从我已经定义的动态数组`vec`开始，也就是`vec.begin()` 
第二个分号就是终止符 告诉迭代器 当迭代器碰到了这个vec动态数组的末尾， 就停下来
第三个分号就是重载++ 告诉迭代器往后挪一位

**现代迭代器写法**
```cpp
for (auto& card : hand) 
{
    card.show();
}
```
这里的auto 是一个自动数据类型 让编译器自己找 引用&的目的是为了让直接取一个别名 不再需要把每一个数据都拷贝一边才能重新传输

样例：
```cpp
std::vector<int> nums = {1, 2, 3, 4};

// 只读
for (int x : nums) 
{ 
    
}

// 修改 (配合引用 &)
for (int& x : nums)
{
    x = x * 2; 
}
```
总结：迭代器的写法类似`for i in range(n)` 修改要加引用符号 不修改不用加（为了提升性能
##### 2.5算法
`std::sort(nums.begin(), nums.end())`
STL本身支持的排序算法封装函数
`std::find`
不用再写循环 直接在hand里面找一张特定的牌
`auto it = std::find(hand.begin(), hand.end(), targetCard);`
以及`auto`本身 类似python 不需要再写数据类型 让编译器自己猜
##### 2.6 class，成员函数，析构函数
样例：
```cpp
class Player {
private: 
    // 私有成员：外面的人不能直接改（安全性）
    int id;
    int score;
    std::vector<Card> hand;

public: 
    // 公有成员：外面可以调用的“接口”
    
    // 构造函数：名字和类名一样，创建对象时自动调用
    Player(int _id) : id(_id), score(0) {} 

    // 成员函数：在这个函数里，你可以直接访问 id 和 score，不需要指针
    void addScore(int points) {
        score += points; 
    }

    void show() const {
        std::cout << "Player " << id << " Score: " << score << std::endl;
    }
};
```
**什么是public和private？**
public：公开的内容 在结构体外部的函数中可以调用的部分 比如`card.show()`
private：只能被结构体本身的成员函数修改 外部没有对于private的修改权限 一旦修改 编译器立即报错

private：通常是结构体本身携带的数据 比如玩家的名字 编号 成绩 手牌之类的数据
public：通常是结构体本身能用的一些函数 比如构造函数和成员函数

**构造函数**
定义一个构造函数 数据本身自动初始化 不需要手动操作 也不会是垃圾值 不同于C的自身初始化
三个特殊规定：
1.函数名必须和结构体类名完全相同
2.不能有任何返回值类型 包括void
3.必须要放在public区域
```cpp
class Player {
private:
    int id;
    int score;

public:
    // 构造函数
    Player(int _id, int _score) {
        id = _id;
        score = _score;
        std::cout << "Player " << id << " has been created!" << std::endl;//这部分就是日志 无所谓 流式输出的部分不用管
    }
};
```
```cpp
class Player {
private:
    int id;
    int score;

public:
    // 使用 : 后面跟着变量初始化
    // 语法：变量名(参数名)
    Player(int _id, int _score) : id(_id), score(_score) 
    {
        // 函数体通常是空的，除非你想打印日志
    }
};
```
`_id`这种下划线表示法不是必须的 理论上什么都行 约定为下划线是为了增强代码可读性和解决重名问题
	**构造函数重载**
	这个问题出现在一个class中有多个构造函数
	编译器会自己识别 比如：
```cpp
	class Player {
	private:
    int id_;
    std::string name_;
    int score_;

	public:
    // 构造函数 A：全参数版本
    Player(int id, std::string name, int score) 
        : id_(id), name_(name), score_(score) {}

    // 构造函数 B：简化版，只需要 ID 和名字，分数默认为 0
    Player(int id, std::string name) 
        : id_(id), name_(name), score_(0) {}

    // 构造函数 C：极简版（默认构造函数），什么都不传时调用
    Player() 
        : id_(0), name_("Unknown"), score_(0) {}
	};
```
可以看到这边有很多的构造函数 在初始化的时候 如果少了哪个参数 编译器会自动识别并且调用对应的正确的构造函数 如果没有 才报错

**成员函数**
比如`append, popleft, show, ...`这些都是成员函数 在结构体自身中就被包含定义
```cpp
class Player {
private:
    int id; // 私有变量，外部无法直接访问

public:
    /**
     * 获取玩家 ID 的 Getter 函数
     * 返回值类型：int
     * 函数属性：const（保证不修改类内部的任何成员）
     */
    int getId() const 
    {
        return id; 
    }
    
    void receiveCard(const Card& c) 
    { 
    hand.push_back(c); 
    }
    
};
```
成员函数基本都需要声明**const** 表示自己不会修改私有内容

**析构函数**
无参数 无返回值
一个类 仅有一个析构函数
是一个结构体的删除处理 告别手动free

**什么情况会用到析构函数**
我们常用的定义里 `vector, list`这些本身就拥有自己的析构函数，根据析构递归，我们不需要在自己的新结构体里再写一个析构函数 这是画蛇添足 我们没有堆上内存

但是下面这种需要 因为在结构体定义中 我们使用了`int*` 这个结构体本身包含了一个不会自动消除的堆上内存 我们就需要定义析构函数了 很简单 直接delete就可以
语法参考：
```cpp

class Player {
private:
    int* data; // 假设我们在堆上申请了额外空间

public:
    // 构造函数：领养资源
    Player() {
        data = new int[100]; 
    }//new会自动调用构造函数 而且不需要写sizeof 语法更智能

    // 析构函数：归还资源
    ~Player() {
        delete[] data;//这里的[]代表一个智能查找 让编译器自动把这边的内存全部释放
        std::cout << "清理完毕，内存已释放" << std::endl;
    }
};
```

~代表取反 本质上析构函数也是构造函数的反面 消除一个结构体
大括号结构 析构函数自动调用 摧毁结构体






































