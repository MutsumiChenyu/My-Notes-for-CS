**Basic Struct Blocks**
Array-List-Tree-HashTable-Trie

Abstract data type
**queues 队列** FIFO先进先出 始终读取最早的内容

**enqueue**
**dequeue**

**stack 栈** LIFO后进先出 始终读取最上层的内容

**push**
**pop**

Dynamic stack and queue

The first type of data structure Array

unsigned char \*p 把读取到的数据转换成BYTE去处理

**Realloc** 重定向

realloc(list, 4\*sizeof(int))  自动把list的地址指向的内容复制到新的指针指向的数组中

-> 新的指针方式 直接表示指向某一个地址
```C
n -> number = 1;
```

**linked lists 链表** 直接指向某一个位置

一个连续的指针指向下一个数值 最后一个数值携带的指针指向NULL
每个数值会携带一个指向下一个数值的指针 called Node 节点  
数据结构是可以循环的

代码实现：
```C
typedef struct node//这里可以在将定义的这个数据结构node中 再次调用node本身
{
	int number;
	struct node *next;//一个指向下一个结构类型体的指针
}
node;
//在内存中构建链表的范式
```
利用链表 我可以在内存中任意位置添加新的值

 缺点：**Array versus List**
 1.链表使用了两倍的内存一个int放数字 一个放地址指针 内存占用大
 2.你不能用方括号去索引node 方括号表示内存是连续的
 
 也就是说 这个节点类型包含了1.数值 2.指针-只指向下一个相同类型的结构（即node）

内存不挨着 就不能使用二分法

问题是 你每次压入新数据 他都会成为这个list的最前面一个 而不是应该的最后一个

头插法链表的写法（ input：123；output：321 ）**压栈**
```C
#include<stdio.h>
#include<stdlib.h>
typedef struct node//这里可以在将定义的这个数据结构node中 再次调用node本身
{
    int number;
    struct node *next;//一个指向下一个结构类型体的指针
}
node;

int main(int argc, char *argv[])
{
    node *list = NULL;//新建一个list **这个*list是一个指向链表起点的入口**

    for(int i = 1;i < argc;i++)//第一个argv[0]是程序名
    {
        int number = atoi(argv[i]);//atoi把字符串转化成整数
        node *n = malloc(sizeof(node));//申请一块内存区域用来存放node这个数据结构 并且用指针n来指向他
        if(n == NULL)
        {
            return 1;
        }
        n -> number = number;//给node装填上命令行参数的数据
        n -> next = NULL;//为什么要这么写 是因为要把链表内容变成干净的“0”状态 
        n -> next = list;//每一个node结构中的下一个指针 指向list这个装填node的新起点
        list = n;//把list的内容更新成n 也就是说 循环中的下一个node将指向上一个node的地址
    }
    for(node *ptr = list;ptr != NULL)//for写法 创建一个临时指针ptr指向list 把整个链表遍历
    {
        printf("%i\n",ptr -> number);
        ptr = ptr -> next;//这个ptr临时指针将切换方向 跟随现在被指向的这个node的next指针 指向链表中下一个node
    }
    ptr = list;
    while(ptr != NULL)//while写法 统一free内存
    {
        node *tmp = ptr->next;
        free(ptr);
        ptr = tmp;
    }
}

```

**trees**
创建一个既可以二分查找 也拥有动态性的数据结构
Growing down   Binary search tree 
Actually, it is a 2-D struct, from root to find a value is just binary search.--数字必须被排序
```C
typedef struct node
{
	int number;
	struct node *left;
	struct node *right;
}
node;

bool search(node *tree,int number)//Use recursion
{
	if(tree == NULL)
	{
		return 1;
	}
	else if(number < tree->number)//RECURSION
	{
		return search(tree->left , number)
		//Directly return the value to the function search
	}
	else if()
	{}
	else
	{}
}
```
定义递归函数的一个写法 见上
```C
return search(tree->left,number)//继续把参数传回去 如果是数字小了 就指向左边 所以第一个参数是tree->left search这个函数中第一个参数刚好是一个 指向node这种类型的指针 和tree->left是相同的1第二个参数则不变 仍然是number
```
在一个函数定义的return中 再次返回该函数所需要的所有参数--recursion
A binary tree can devolve to a list

**Dictionary**
无视数据结构大小 在固定步数内找到目标
Key-Value pairs 键值对
键与值一一对应 输入Key 自动找到Value
时间复杂度---O(1)常数步数

**Hashing**
Get a simpler value -- Hash tables
可以通过细分 创建一张无限大的网络 在里面查找到每个东西都只花极其有限的常数时间
Finally all things go to the "NODE", which composing the whole network one by one.
Every character has a number attached to it and can be found using the number, which will lead to the constant time hash table using.
技术上可以实现一个复杂度为O(n/k)的哈希表

**Trie**
Retrieval
用多个数组来组成Tree 实现一个Retrieval 因为检索的东西必然有限 那么检索每一个元素都必将有有限的步数 因此他的时间复杂度为O(1) 常数时间
需要大量的内存 比较稀疏

Balance between efficiency and space
