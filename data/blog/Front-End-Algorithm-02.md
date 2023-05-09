---
title: Basic Leetcode with JavaScript 2
date: '2023-01-11'
tags: ['LeetCode', 'JavaScript']
draft: false
summary: Basic Foundation using JavaScipt for LeetCode
images: []
layout: PostLayout
canonicalUrl: frontentleetcode01
---

# Introducing Time & Space Complexity,Data Structure with using JavaScript.

此篇属于前端算法入门系列的第二篇，主要介绍如何分析算法的时间复杂度和空间复杂度，以及介绍算法题中涉及到的八大常见数据结构，并且给出相应的 JavaScript（TypeScript）实现代码，还罗列其使用场景，以及相关 leetcode 题目。

```md
文章主要包含以下内容：

时间&空间复杂度分析介绍
时间复杂度分析方法
空间复杂度分析方法
八大数据结构的 JS 实现
栈
队列
链表
集合
字典
树
图
堆
```

## One. Time & Space Complexity 时间&空间复杂度

- 复杂度是数量级（方便记忆、推广），不是具体数字。
- 常见复杂度大小比较：O(n^2) > O(nlogn) > O(n) > O(logn) > O(1)

### 1.Time Complexity 时间复杂度

常见时间复杂度对应关系：

- O(n^2)：2 层循环（嵌套循环）
- O(nlogn)：快速排序（循环 + 二分）
- O(n)：1 层循环
- O(logn)：二分

### 2.Space Complexity

常见空间复杂度对应关系：

- O(n)：传入一个数组，处理过程生成一个新的数组大小与传入数组一致

## Two.8 Data Structure with using JavaScript 八大数据结构的 JS 实现

### 1.Stack 栈

栈是一个后进先出的数据结构。JavaScript 中没有栈，但是可以用 Array 实现栈的所有功能。

```js
// 数组实现栈数据结构
const stack = []
// 入栈
stack.push(0)
stack.push(1)
stack.push(2)
// 出栈
const popVal = stack.pop() // popVal 为 2
```

使用场景

- 十进制转二进制
- 有效括号
- 函数调用堆栈

LeetCode 题目

- [20.有效括号](https://leetcode.cn/problems/valid-parentheses/)
- [144.二叉树的前序遍历](https://leetcode.cn/problems/binary-tree-preorder-traversal/)

### 2.Queue 队列

队列是一个先进先出的数据结构。JavaScript 中没有队列，但是可以用 Array 实现队列的所有功能。

```js
// 数组实现队列数据结构
const queue = []
// 入队
stack.push(0)
stack.push(1)
stack.push(2)
// 出队
const shiftVal = stack.shift() // shiftVal 为 0
```

使用场景

- 日常测核酸排队
- JS 异步中的任务队列
- 计算最近请求次数

LeetCode 题目

- [933. 最近的请求次数](https://leetcode.cn/problems/number-of-recent-calls/)

### 3.Linked list 链表

链表是多个元素组成的列表，元素存储不连续，用 next 指针连在一起。JavaScript 中没有链表，但是可以用 Object 模拟链表。
TS 实现

```ts
/**
 * 定义一个 node 节点
 */
interface ILinkListNode {
  value: number
  next?: ILinkListNode
}

/**
 * 根据数组创建单向链表
 * @param arr
 * @returns
 */
function createLinkList(arr: number[]): ILinkListNode {
  const len = arr.length
  if (len === 0) throw new Error('arr is empty')

  let curNode: ILinkListNode = {
    value: arr[len - 1],
  }
  if (len === 1) return curNode

  for (let i = len - 2; i >= 0; i--) {
    curNode = {
      value: arr[i],
      next: curNode,
    }
  }

  return curNode
}
```

使用场景

- JS 中的原型链
- 使用链表指针获取 JSON 的节点值

LeetCode 题目

- [237. 删除链表中的节点](https://leetcode.cn/problems/delete-node-in-a-linked-list/)
- [2. 两数相加](https://leetcode.cn/problems/add-two-numbers/)
- [206. 反转链表](https://leetcode.cn/problems/reverse-linked-list/)
- [83. 删除排序链表中的重复元素](https://leetcode.cn/problems/remove-duplicates-from-sorted-list/)
- [141. 环形链表](https://leetcode.cn/problems/linked-list-cycle/)

### 4. Set 集合

集合是一个无序且唯一的数据结构。ES6 中有集合：Set，集合常用操作：去重、判断某元素是否在集合中、求交集。

```js
// 去重
const arr = [1, 1, 2, 2]
const arr2 = [...new Set(arr)]
// 判断元素是否在集合中
const set = new Set(arr)
const has = set.has(3) // false
// 求交集
const set2 = new Set([2, 3])
const set3 = new Set([...set].filter((item) => set2.has(item)))
```

使用场景

- 求交集、差集
  LeetCode 题目
- [349. 两个数组的交集](https://leetcode.cn/problems/intersection-of-two-arrays/)

### 5.Hash 字典(哈希)

字典也是一种存储唯一值的数据结构，但它以键值对的形式存储。ES6 中的字典名为 Map，

```js
// 字典
const map = new Map()
// 增
map.set('key1', 'value1')
map.set('key2', 'value2')
map.set('key3', 'value3')
// 删
map.delete('key3')
// map.clear()
// 改
map.set('key2', 'value222')
// 查
map.get('key2')
```

使用场景

- leetcode 刷题
  LeetCode 题目
- [349. 两个数组的交集](https://leetcode.cn/problems/intersection-of-two-arrays/)
- [20.有效括号](https://leetcode.cn/problems/valid-parentheses/)
- [1. 两数之和](https://leetcode.cn/problems/two-sum/)
- [3. 无重复字符的最长子串](https://leetcode.cn/problems/longest-substring-without-repeating-characters/)
- [76. 最小覆盖子串](https://leetcode.cn/problems/minimum-window-substring/)

### 6.Tree 树

树是一种分层的数据模型。前端常见的树包括：DOM、树、级联选择、树形控件……。JavaScript 中没有树，但是可以通过 Object 和 Array 构建树。树的常用操作：深度/广度优先遍历、先中后序遍历。

#### TS 实现

```ts
/**
 * 前序遍历：root -> left -> right
 * 中序遍历：left -> root -> right
 * 后序遍历：left -> right -> root
 * 问1：为什么二叉树很重要，而不是三叉树、四叉树？
 * 答：
 * （1）数组、链表各有缺点
 * （2）特定的二叉树（BBST，平衡二叉树）可以结合数组 & 链表的优点，让整体查找效果最优（可用二分法）
 * （3）各种高级二叉树（红黑数、B树），继续优化，满足不同场景
 * 问2：堆特点？和二叉树的关系？
 * 答：
 * （1）逻辑结构是一棵二叉树
 * （2）物理结构是一个数组
 * （3）数组：连续内存 + 节省空间
 * （4）查询比 BST 慢
 * （5）增删比 BST 快，维持平衡更快
 * （6）整体时间复杂度都在 O(logn) 级别，与树一致
 * @description 二叉搜索树
 * @author hovinghuang
 */

interface ITreeNode {
  value: number
  left: ITreeNode | null
  right: ITreeNode | null
}

const treeArr: number[] = []

/**
 * 前序遍历
 * @param node
 * @returns
 */
function preOrderTraverse(node: ITreeNode | null): void {
  if (node == null) return
  console.info(node.value)
  treeArr.push(node.value)
  preOrderTraverse(node.left)
  preOrderTraverse(node.right)
}

/**
 * 中序遍历
 * @param node
 * @returns
 */
function inOrderTraverse(node: ITreeNode | null): void {
  if (node == null) return
  inOrderTraverse(node.left)
  console.info(node.value)
  treeArr.push(node.value)
  inOrderTraverse(node.right)
}

/**
 * 后序遍历
 * @param node
 * @returns
 */
function postOrderTraverse(node: ITreeNode | null): void {
  if (node == null) return
  postOrderTraverse(node.left)
  postOrderTraverse(node.right)
  console.info(node.value)
  treeArr.push(node.value)
}

function getKthValue(node: ITreeNode, k: number): number | null {
  inOrderTraverse(bst)
  return treeArr[k - 1] || null
}

const bst: ITreeNode = {
  value: 5,
  left: {
    value: 3,
    left: {
      value: 2,
      left: null,
      right: null,
    },
    right: {
      value: 4,
      left: null,
      right: null,
    },
  },
  right: {
    value: 7,
    left: {
      value: 6,
      left: null,
      right: null,
    },
    right: {
      value: 8,
      left: null,
      right: null,
    },
  },
}

// 功能测试
// preOrderTraverse(bst)
// inOrderTraverse(bst)
// postOrderTraverse(bst)
// console.info('第3小值', getKthValue(bst, 3))
```

使用场景

- DOM 树
- 级联选择器
  LeetCode 题目
- [104. 二叉树的最大深度](https://leetcode.cn/problems/maximum-depth-of-binary-tree/)
- [111. 二叉树的最小深度](https://leetcode.cn/problems/minimum-depth-of-binary-tree/)
- [102. 二叉树的层序遍历](https://leetcode.cn/problems/binary-tree-level-order-traversal/)
- [94. 二叉树的中序遍历](https://leetcode.cn/problems/binary-tree-inorder-traversal/)
- [112. 路径总和](https://leetcode.cn/problems/path-sum/)

### 7. Graph 图

图是网络结构的抽象模型，是一组由边连接的节点。图可以表示任何二元关系，比如道路、航班。JS 中没有图，但是可以用 Object 和 Array 构建图。图的表示法：邻接矩阵、邻接表、关联矩阵。

```js
// 邻接表表示图结构
const graph = {
  0: [1, 2],
  1: [2],
  2: [0, 3],
  3: [3],
}

// 深度优先遍历
const visited = new Set()
function dfs(n, visited) {
  // n 表示开始访问的根节点
  console.log(n)
  visited.add(n)
  graph[n].forEach((item) => {
    if (!visited.has(item)) dfs(item, visited)
  })
}
dfs(2, visited) // 2 0 1 3
console.log(visited) // {2, 0, 1, 3}

// 广度优先遍历
function bfs(n) {
  // n 表示开始访问的根节点
  const visited = new Set()
  visited.add(n)
  const queue = [n]
  while (queue.length) {
    const shiftVal = queue.shift()
    graph[shiftVal].forEach((item) => {
      if (!visited.has(item)) {
        queue.push(item)
        visited.add(item)
      }
    })
  }
  console.log(visited) // {2, 0, 3, 1}
}
bfs(2)
```

使用场景

- 道路
- 航班

LeetCode 题目

- [65. 有效数字](https://leetcode.cn/problems/valid-number/)
- [417. 太平洋大西洋水流问题](https://leetcode.cn/problems/pacific-atlantic-water-flow/)
- [133. 克隆图](https://leetcode.cn/problems/clone-graph/)

### 8. Heap 堆

堆是一种特殊的完全二叉树。所有的节点都大于等于（最大堆）或小于等于（最小堆）它的子节点。由于堆的特殊结构，我们可以用数组表示堆。

```js
    1
   / \
  2   3
 / \  /\
4  5 6

// 数组表示堆结构
const heap = [1, 2, 3, 4, 5, 6]

// 实现一个最小堆类
class MinHeap {
    constructor() {
        this.heap = [];
    }
    swap(i1, i2) {
        const temp = this.heap[i1];
        this.heap[i1] = this.heap[i2];
        this.heap[i2] = temp;
    }
    getParentIndex(i) {
        return (i - 1) >> 1;
    }
    getLeftIndex(i) {
        return i * 2 + 1;
    }
    getRightIndex(i) {
        return i * 2 + 2;
    }
    shiftUp(index) {
        if (index == 0) { return; }
        const parentIndex = this.getParentIndex(index);
        if (this.heap[parentIndex] > this.heap[index]) {
            this.swap(parentIndex, index);
            this.shiftUp(parentIndex);
        }
    }
    shiftDown(index) {
        const leftIndex = this.getLeftIndex(index);
        const rightIndex = this.getRightIndex(index);
        if (this.heap[leftIndex] < this.heap[index]) {
            this.swap(leftIndex, index);
            this.shiftDown(leftIndex);
        }
        if (this.heap[rightIndex] < this.heap[index]) {
            this.swap(rightIndex, index);
            this.shiftDown(rightIndex);
        }
    }
    insert(value) {
        this.heap.push(value);
        this.shiftUp(this.heap.length - 1);
    }
    pop() {
        this.heap[0] = this.heap.pop();
        this.shiftDown(0);
    }
    peek() {
        return this.heap[0];
    }
    size() {
        return this.heap.length;
    }
}

const h = new MinHeap();
h.insert(3);
h.insert(2);
h.insert(1);
h.pop();
```

使用场景

- 场景：leetcode 刷题
  LeetCode 题目
- [215. 数组中的第 K 个最大元素](https://leetcode.cn/problems/kth-largest-element-in-an-array/)
- [347. 前 K 个高频元素](https://leetcode.cn/problems/top-k-frequent-elements/)
- [23. 合并 K 个升序链表](https://leetcode.cn/problems/merge-k-sorted-lists/)

参考文章

- [慕课网：2 周刷完 100 道前端优质面试真题](https://coding.imooc.com/class/562.html)
- [慕课网：JavaScript 版数据结构与算法](https://coding.imooc.com/class/446.html)
- [前端算法入门二：时间空间复杂度&8 大数据结构的 JS 实现](https://juejin.cn/post/7087286814230183943#heading-12)
