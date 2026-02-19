#### `git commit`
把最新进度提交 git会记录版本 记录每个版本的差异值

#### `git checkout & git switch`
切换分支的操作 有\*代表在当前的分支下

**一种直接创建分支并且切换的写法** `git checkout -b AAAA`

#### `git branch`
创建新的分支 本质是一个**指针**名称 所以要多建分支 可以使提交版本库更加清晰

#### `git merge`
git merge 加上一个版本库名称 是把这个版本库融合到**当前分支**里面 所以是你在哪就往那里融合

#### `git rebase`
本质上也是用来融合分支 但他这个是复制直接接过去（复制分支）
不同于cherry-pick的摘樱桃 他这个是一整串 应该是摘葡萄

#### HEAD
一个头 改变checkout本质上是改变这个头指向的位置
头可以指向提交历史版本

#### `git log & 相对引用`

```git
>>>git checkout C4
>>>git checkout HEAD^(相对引用 移动到C4的上一级)
```
相对引用 HEAD\^ 代表走到HEAD的上一级 几个\^走几步
checkout指令本质上是把HEAD移到一个你指定的位置
`git log`是找哈希值 也可以定位到某个地标

#### `git branch -f 分支名 地名`
把你创建的分支标签 移到某一个特定位置
把我想移动的分支的指针指向另一个位置
HEAD~3 == HEAD^^^

#### `git reset & git revert 撤销提交`
都是撤销提交 有什么不同呢？
git reset 只适用于自己 多人共同操作的时候别人看不到
reset的逻辑是在本地隐去本次提交的记录与内容 查找不到
git revert 适用于多人协作
revert的逻辑是在当前分支下继续创建一个新的记录 这个记录和上一次完全相同 来达到回溯版本的问题

#### `git cherry-pick C1 C2 C3 摘樱桃`
把某几个特定的提交记录直接pick到当前HEAD指向的分支下面（副本）不是迁移 而是复制

#### `git rebase -i HEAD^`
可以自由选择顺序 （有一个GUI或者vim界面）
选择不同提交版本rebase出来 出来的结果和revert类似 都是副本

#### `git tag v0 C1`
给某一个提交记录打标签 tag不会像分支那样随意移动 一般一直指向某一个位置
tag可以被checkout指向（HEAD指针被切换到tag这边)

###### 命令语法小逻辑
观察到git命令的对象写法一般是：
先写受体 再写配体 比如把HEAD的东西移到side那边 我们就写`git AAAAAA side HEAD`

CHECK123456789

#### ``