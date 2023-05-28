---
# date:   2023-05-26 22:03:29 +0000
categories: CS
tags: Data-Structures
---
# 数据结构

## 1. 数组Array

### 1.1 二分查找 Binary Search

> 二分查找Binary Search[LeetCode](https://leetcode.com/problems/binary-search/)&[Solutions](https://github.com/youngyangyang04/leetcode-master/blob/master/problems/0704.二分查找.md)


#### 左闭右闭

```python
class Solution:
    def search(self, nums: List[int], target: int) -> int:
        left, right = 0, len(nums) - 1  # 定义target在左闭右闭的区间里，[left, right]

        while left <= right:
            middle = left + (right - left) // 2
            
            if nums[middle] > target:
                right = middle - 1  # target在左区间，所以[left, middle - 1]
            elif nums[middle] < target:
                left = middle + 1  # target在右区间，所以[middle + 1, right]
            else:
                return middle  # 数组中找到目标值，直接返回下标
        return -1  # 未找到目标值
```

#### 左闭右开

```python
class Solution:
    def search(self, nums: List[int], target: int) -> int:
        left, right = 0, len(nums)  # 定义target在左闭右开的区间里，即：[left, right)

        while left < right:  # 因为left == right的时候，在[left, right)是无效的空间，所以使用 <
            middle = left + (right - left) // 2

            if nums[middle] > target:
                right = middle  # target 在左区间，在[left, middle)中
            elif nums[middle] < target:
                left = middle + 1  # target 在右区间，在[middle + 1, right)中
            else:
                return middle  # 数组中找到目标值，直接返回下标
        return -1  # 未找到目标值
```



### 1.2 双指针法 Two-pointer technique

1.  快慢指针法
    *   快指针：寻找新数组的元素，新数组就是不含有目标元素的数组
    *   慢指针：指向更新 新数组下标的位置
    
    > 移除元素Remove Element[LeetCode](https://leetcode.com/problems/remove-element/)&[Solutions](https://github.com/youngyangyang04/leetcode-master/blob/master/problems/0027.移除元素.md)
2.  相向双指针法
    > 有序数组的平方Squares of a Sorted Array[LeetCode](https://leetcode.com/problems/squares-of-a-sorted-array/)&[Solutions](https://programmercarl.com/0977.%E6%9C%89%E5%BA%8F%E6%95%B0%E7%BB%84%E7%9A%84%E5%B9%B3%E6%96%B9.html)
    > 三数之和3Sum[LeetCode](https://leetcode.com/problems/3sum/)&[Solutions](https://programmercarl.com/0015.%E4%B8%89%E6%95%B0%E4%B9%8B%E5%92%8C.html)
    > 四数之和4Sum[LeetCode](https://leetcode.com/problems/4sum/)&[Solutions](https://programmercarl.com/0018.%E5%9B%9B%E6%95%B0%E4%B9%8B%E5%92%8C.html)
    > 反转字符串Reverse String[LeetCode](https://leetcode.com/problems/reverse-string/)&[Solutions](https://programmercarl.com/0344.%E5%8F%8D%E8%BD%AC%E5%AD%97%E7%AC%A6%E4%B8%B2.html)

### 1.3 滑动窗口Sliding window

> 长度最小的子数组Minimum Size Subarray Sum[LeetCode](https://leetcode.com/problems/minimum-size-subarray-sum/)&[Solutions](https://programmercarl.com/0209.%E9%95%BF%E5%BA%A6%E6%9C%80%E5%B0%8F%E7%9A%84%E5%AD%90%E6%95%B0%E7%BB%84.html)

## 2. 链表Linked list

### 2.1 类型

*   单链表
*   双链表
*   循环链表

### 2.1 定义Definition

```python
class ListNode:
    def __init__(self, val, next=None):
        self.val = val
        self.next = next
```

### 2.2 插入/删除节点操作operations

> 设计链表Design Linked List[LeetCode](https://leetcode.com/problems/design-linked-list/)&[Solutions](https://programmercarl.com/0707.%E8%AE%BE%E8%AE%A1%E9%93%BE%E8%A1%A8.html)

### 2.3 虚拟头节点Virtual head nodes

> 移除链表元素Remove Linked List Elements[LeetCode](https://leetcode.com/problems/remove-linked-list-elements/)&[Solutions](https://programmercarl.com/0203.%E7%A7%BB%E9%99%A4%E9%93%BE%E8%A1%A8%E5%85%83%E7%B4%A0.html)

> 两两交换链表中的节点Swap Nodes in Pairs[LeetCode](https://leetcode.com/problems/swap-nodes-in-pairs/)&[Solutions](https://programmercarl.com/0024.%E4%B8%A4%E4%B8%A4%E4%BA%A4%E6%8D%A2%E9%93%BE%E8%A1%A8%E4%B8%AD%E7%9A%84%E8%8A%82%E7%82%B9.html)

### 2.4 双指针Two-pointer technique

> 反转链表Reverse Linked List[LeetCode](https://leetcode.com/problems/reverse-linked-list/)&[Solutions](https://programmercarl.com/0206.%E7%BF%BB%E8%BD%AC%E9%93%BE%E8%A1%A8.html)

> 删除链表的倒数第N个节点Remove Nth Node From End of List[LeetCode](https://leetcode.com/problems/remove-nth-node-from-end-of-list/)&[Solutions](https://programmercarl.com/0019.%E5%88%A0%E9%99%A4%E9%93%BE%E8%A1%A8%E7%9A%84%E5%80%92%E6%95%B0%E7%AC%ACN%E4%B8%AA%E8%8A%82%E7%82%B9.html)

1.  快慢指针法Fast and slow pointer method
    > 链表相交Intersection of Two Linked Lists[LeetCode](https://leetcode.com/problems/intersection-of-two-linked-lists/)&[Solution](https://programmercarl.com/%E9%9D%A2%E8%AF%95%E9%A2%9802.07.%E9%93%BE%E8%A1%A8%E7%9B%B8%E4%BA%A4.html)
    > 环形链表II Linked List Cycle II[LeetCode](https://leetcode.com/problems/linked-list-cycle-ii/)&[Solutions](https://programmercarl.com/0142.%E7%8E%AF%E5%BD%A2%E9%93%BE%E8%A1%A8II.html)

## 3. 哈希表 Hash table

### 3.1 哈希函数Hash Function

    Hash Function = hashCode(name) % tableSize

### 3.2 哈希碰撞 Hash Collision

#### 3.2.1 拉链法

位置发生了冲突，发生冲突的元素都被存储在此位置后的链表中

#### 3.2.2 线性探测法

一定要保证tableSize大于dataSize，需要依靠哈希表中的空位来解决碰撞问题

### 3.3 数组作为哈希Array

> 有效的字母异位词Valid Anagram[LeetCode](https://leetcode.com/problems/valid-anagram/)&[Solutions](https://programmercarl.com/0242.%E6%9C%89%E6%95%88%E7%9A%84%E5%AD%97%E6%AF%8D%E5%BC%82%E4%BD%8D%E8%AF%8D.html)

### 3.4 集合作为哈希Set

> 两个数组的交集Intersection of Two Arrays[LeetCode](https://leetcode.com/problems/intersection-of-two-arrays/)&[Solutions](https://programmercarl.com/0349.%E4%B8%A4%E4%B8%AA%E6%95%B0%E7%BB%84%E7%9A%84%E4%BA%A4%E9%9B%86.html)
> 快乐数Happy Number[LeetCode](https://leetcode.com/problems/happy-number/)&[Solutions](https://programmercarl.com/0202.%E5%BF%AB%E4%B9%90%E6%95%B0.html)

### 3.5映射作为哈希Map

> 两数之和Two Sum[LeetCode](https://leetcode.com/problems/two-sum/)&[Solutions](https://programmercarl.com/0001.%E4%B8%A4%E6%95%B0%E4%B9%8B%E5%92%8C.html)
> 四数相加II 4Sum II[LeetCode](https://leetcode.com/problems/4sum-ii/)&[Solutions](https://programmercarl.com/0454.%E5%9B%9B%E6%95%B0%E7%9B%B8%E5%8A%A0II.html)
> 赎金信Ransom Note[LeetCode](https://leetcode.com/problems/ransom-note/)&[Solutions](https://programmercarl.com/0383.%E8%B5%8E%E9%87%91%E4%BF%A1.html)

## 4. 字符串 String

### 4.1 双指针法

1.  相向双指针法

> 反转字符串 II Reverse String II[LeetCode](https://leetcode.com/problems/reverse-string-ii/)&[Solutions](https://programmercarl.com/0541.%E5%8F%8D%E8%BD%AC%E5%AD%97%E7%AC%A6%E4%B8%B2II.html)

1.  快慢指针法

> 反转字符串中的单词Reverse Words in a String[LeetCode](https://leetcode.com/problems/reverse-words-in-a-string/)&[Solutions](https://programmercarl.com/0151.%E7%BF%BB%E8%BD%AC%E5%AD%97%E7%AC%A6%E4%B8%B2%E9%87%8C%E7%9A%84%E5%8D%95%E8%AF%8D.html)

### 4.2 KMP算法

模式串
前缀表
最长公共前后缀

> 找出字符串中第一个匹配项的下标Find the Index of the First Occurrence in a String[leetCode](https://leetcode.com/problems/find-the-index-of-the-first-occurrence-in-a-string/)&[Solutions](https://programmercarl.com/0028.%E5%AE%9E%E7%8E%B0strStr.html)
> 重复的子字符串Repeated Substring Pattern[LeetCode](https://leetcode.com/problems/repeated-substring-pattern/)&&[Solutions](https://programmercarl.com/0459.%E9%87%8D%E5%A4%8D%E7%9A%84%E5%AD%90%E5%AD%97%E7%AC%A6%E4%B8%B2.html)

## 5. 栈和队列 Stack & Queue

### 5.1 定义

栈Stack和队列Queue的底层实现可以是：vector数组，list链表，deque双向队列 **(默认)**

> 用栈实现队列Implement Queue using Stacks[LeetCode](https://leetcode.com/problems/implement-queue-using-stacks/)&[Solutions](https://programmercarl.com/0232.%E7%94%A8%E6%A0%88%E5%AE%9E%E7%8E%B0%E9%98%9F%E5%88%97.html)
> 用队列实现栈Implement Stack using Queues[LeetCode](https://leetcode.com/problems/implement-stack-using-queues/)&[Solutions](https://programmercarl.com/0225.%E7%94%A8%E9%98%9F%E5%88%97%E5%AE%9E%E7%8E%B0%E6%A0%88.html)

### 5.2 栈的应用

> 有效的括号Valid Parentheses[LeetCode](https://leetcode.com/problems/valid-parentheses/)&[Solutions](https://programmercarl.com/0020.%E6%9C%89%E6%95%88%E7%9A%84%E6%8B%AC%E5%8F%B7.html)
> 删除字符串中的所有相邻重复项Remove All Adjacent Duplicates In String[LeetCode](https://leetcode.com/problems/remove-all-adjacent-duplicates-in-string/)&[Solutions](https://programmercarl.com/1047.%E5%88%A0%E9%99%A4%E5%AD%97%E7%AC%A6%E4%B8%B2%E4%B8%AD%E7%9A%84%E6%89%80%E6%9C%89%E7%9B%B8%E9%82%BB%E9%87%8D%E5%A4%8D%E9%A1%B9.html)
> 逆波兰表达式求值Evaluate Reverse Polish Notation[LeetCode](https://leetcode.com/problems/evaluate-reverse-polish-notation/)&[Solutions](https://programmercarl.com/0150.%E9%80%86%E6%B3%A2%E5%85%B0%E8%A1%A8%E8%BE%BE%E5%BC%8F%E6%B1%82%E5%80%BC.html)

### 5.3 队列的应用

> 滑动窗口最大值Sliding Window Maximum[LeetCode](https://leetcode.com/problems/sliding-window-maximum/)&[Solutions](https://programmercarl.com/0239.%E6%BB%91%E5%8A%A8%E7%AA%97%E5%8F%A3%E6%9C%80%E5%A4%A7%E5%80%BC.html)

#### 5.3.1 优先级队列priority\_queue

[优先级队列priority\_queue](https://programmercarl.com/0347.%E5%89%8DK%E4%B8%AA%E9%AB%98%E9%A2%91%E5%85%83%E7%B4%A0.html): 一个披着队列外衣的堆。
堆是一棵完全二叉树，树中每个结点的值都不小于（或不大于）其左右孩子的值。

```python
import heapq

# 最小堆（min heap）
min_heap = []
heapq.heappush(min_heap, 3)
heapq.heappush(min_heap, 1)
heapq.heappush(min_heap, 2)
while min_heap:
    print(heapq.heappop(min_heap))

# 最大堆（max heap）
max_heap = []
# 使用元素的相反数来实现最大堆的效果
heapq.heappush(max_heap, -3)
heapq.heappush(max_heap, -1)
heapq.heappush(max_heap, -2)
while max_heap:
    print(-heapq.heappop(max_heap))
```



> 前 K 个高频元素Top K Frequent Elements[LeetCode](https://leetcode.com/problems/top-k-frequent-elements/description/)&[Solutions](https://programmercarl.com/0347.%E5%89%8DK%E4%B8%AA%E9%AB%98%E9%A2%91%E5%85%83%E7%B4%A0.html)
>
> ```python
> import heapq
> class Solution:
>  def topKFrequent(self, nums: List[int], k: int) -> List[int]:
>      # Get frequency of each item
>      numDic = {}
>      for num in nums:
>          numDic[num] = numDic.get(num, 0) + 1
> 
>      # Sort The Frequency
>      pri_que = []
>      for key, freq in numDic.items():
>          heapq.heappush(pri_que,(freq, key))
>          if len(pri_que)>k:
>              heapq.heappop(pri_que)
> 
>      # Get Top K
>      result = [0]*k
>      for i in range(k-1, -1, -1):
>          result[i] = heapq.heappop(pri_que)[1]
> 
>      return result
> ```
>
> 数组中的第K个最大元素 Kth Largest Element in an Array [LeetCode](https://leetcode.com/problems/kth-largest-element-in-an-array/description/)
>
> ```python
> import heapq
> class Solution:
>     def findKthLargest(self, nums: List[int], k: int) -> int:
>         heap = []
> 
>         for num in nums:
>             heapq.heappush(heap, num)
>             if len(heap) > k:
>                 heapq.heappop(heap)
> 
>         return heap[0]
> ```
>
> 



## 6. 二叉树 Binomial tree

### 6.1 分类

#### 6.1.1 满二叉树Full binary tree

1.  定义：如果一棵二叉树只有度为0的结点和度为2的结点，并且度为0的结点在同一层上，则这棵二叉树为满二叉树。
2.  性质：深度为k，则节点数为2^k-1
    ![Full Binary Tree](https://img-blog.csdnimg.cn/20200806185805576.png)

#### 6.1.2 完全二叉树Complete binary tree

1.  定义：在完全二叉树中，除了最底层节点可能没填满外，其余每层节点数都达到最大值，并且最下面一层的节点都集中在该层最左边的若干位置。
2.  性质：若最底层为第 h 层，则该层包含 1\~ 2^(h-1)  个节点。
    ![Complete Binary Tree](https://img-blog.csdnimg.cn/20200920221638903.png)

#### 6.1.3 二叉搜索树 Binary search tree

1.  定义：是带有数值的，是一个有序树。

*   若它的左子树不空，则左子树上所有结点的值均小于它的根结点的值；
*   若它的右子树不空，则右子树上所有结点的值均大于它的根结点的值；
*   它的左、右子树也分别为二叉排序树
    ![Binary Search Tree](https://img-blog.csdnimg.cn/20200806190304693.png)

#### 6.1.4 平衡二叉搜索树 Balanced binary search tree（AVL Adelson-Velsky and Landis)

1.  定义：它是一棵空树或它的左右两个子树的高度差的绝对值不超过1，并且左右两个子树都是一棵平衡二叉树。
    ![AVL](https://img-blog.csdnimg.cn/20200806190511967.png)

### 6.2 存储方式

#### 6.2.1 链式存储(荐)

> 使用指针

![Chain Storage](https://img-blog.csdnimg.cn/2020092019554618.png)

#### 6.2.2 顺序存储

> 使用数组
> 如果父节点的数组下标是 i，那么它的左孩子就是 i \* 2 + 1，右孩子就是 i \* 2 + 2。
> ![Sequential storage](https://img-blog.csdnimg.cn/20200920200429452.png)

```python
class TreeNode: 
    def __init__(self, value):
        self.value = value
        self.left = None
        self.right = None
```

### 6.3 遍历方式Mode of traversal

#### 6.3.1 深度优先遍历Depth-first search

![Depth First](https://img-blog.csdnimg.cn/20200806191109896.png)

##### 6.3.1.1 前序遍历Preorder traversal（递归法，迭代法）

1.  递归法

> 二叉树的前序遍历Binary Tree Preorder Traversal[LeetCode](https://leetcode.com/problems/binary-tree-preorder-traversal/)&[递归法Solutions](https://programmercarl.com/%E4%BA%8C%E5%8F%89%E6%A0%91%E7%9A%84%E9%80%92%E5%BD%92%E9%81%8D%E5%8E%86.html)&[迭代法Solutions](https://programmercarl.com/%E4%BA%8C%E5%8F%89%E6%A0%91%E7%9A%84%E8%BF%AD%E4%BB%A3%E9%81%8D%E5%8E%86.html)

1.  迭代法
    ![Iteration](https://tva1.sinaimg.cn/large/008eGmZEly1gnbmss7603g30eq0d4b2a.gif)

##### 6.3.1.2 中序遍历Inorder traversal（递归法，迭代法）

1.  递归法

> 二叉树的中序遍历Binary Tree Inorder Traversal[LeetCode](https://leetcode.com/problems/binary-tree-inorder-traversal/)&[递归法Solutions](https://programmercarl.com/%E4%BA%8C%E5%8F%89%E6%A0%91%E7%9A%84%E9%80%92%E5%BD%92%E9%81%8D%E5%8E%86.html)&[迭代法Solutions](https://programmercarl.com/%E4%BA%8C%E5%8F%89%E6%A0%91%E7%9A%84%E8%BF%AD%E4%BB%A3%E9%81%8D%E5%8E%86.html)

1.  迭代法
    ![Iteration](https://tva1.sinaimg.cn/large/008eGmZEly1gnbmuj244bg30eq0d4kjm.gif)

##### 6.3.1.3 后序遍历Postorder traversal（递归法，迭代法）

1.  递归法

> 二叉树的后序遍历Binary Tree Postorder Traversal[LeetCode](https://leetcode.com/problems/binary-tree-postorder-traversal/)&[递归法Solutions](https://programmercarl.com/%E4%BA%8C%E5%8F%89%E6%A0%91%E7%9A%84%E9%80%92%E5%BD%92%E9%81%8D%E5%8E%86.html)&[迭代法Solutions](https://programmercarl.com/%E4%BA%8C%E5%8F%89%E6%A0%91%E7%9A%84%E8%BF%AD%E4%BB%A3%E9%81%8D%E5%8E%86.html)

1.  迭代法
    ![Iteration](https://img-blog.csdnimg.cn/20200808200338924.png)

#### 6.3.1 广度优先遍历Breadth-first search

##### 6.3.1.1 层次遍历Level Order Traversal（迭代法）

> 二叉树的层序遍历Binary Tree Level Order Traversal[LeetCode](https://leetcode.com/problems/binary-tree-level-order-traversal/)&[Solutions](https://programmercarl.com/0102.%E4%BA%8C%E5%8F%89%E6%A0%91%E7%9A%84%E5%B1%82%E5%BA%8F%E9%81%8D%E5%8E%86.html)

***

> 翻转二叉树Invert Binary Tree[LeetCode](https://leetcode.com/problems/invert-binary-tree/)&[Solutions](https://programmercarl.com/0226.%E7%BF%BB%E8%BD%AC%E4%BA%8C%E5%8F%89%E6%A0%91.html)
> 对称二叉树Symmetric Tree[LeetCode](https://leetcode.com/problems/symmetric-tree/description/)&[Solutions](https://programmercarl.com/0101.%E5%AF%B9%E7%A7%B0%E4%BA%8C%E5%8F%89%E6%A0%91.html)

> 二叉树的最大深度Maximum Depth of Binary Tree[LeetCode](https://leetcode.com/problems/maximum-depth-of-binary-tree/description/)&[Solutions](https://programmercarl.com/0104.%E4%BA%8C%E5%8F%89%E6%A0%91%E7%9A%84%E6%9C%80%E5%A4%A7%E6%B7%B1%E5%BA%A6.html)
> N 叉树的最大深度Maximum Depth of N-ary Tree[LeetCode](https://leetcode.com/problems/maximum-depth-of-n-ary-tree/)&[Solutions](https://programmercarl.com/0104.%E4%BA%8C%E5%8F%89%E6%A0%91%E7%9A%84%E6%9C%80%E5%A4%A7%E6%B7%B1%E5%BA%A6.html)
> 二叉树的最小深度Minimum Depth of Binary Tree[LeetCode](https://leetcode.com/problems/minimum-depth-of-binary-tree/description/)&[Solutions](https://programmercarl.com/0111.%E4%BA%8C%E5%8F%89%E6%A0%91%E7%9A%84%E6%9C%80%E5%B0%8F%E6%B7%B1%E5%BA%A6.html)

> 完全二叉树的节点个数Count Complete Tree Nodes[LeetCode](https://leetcode.com/problems/count-complete-tree-nodes/description/)&[Solutions](https://programmercarl.com/0222.%E5%AE%8C%E5%85%A8%E4%BA%8C%E5%8F%89%E6%A0%91%E7%9A%84%E8%8A%82%E7%82%B9%E4%B8%AA%E6%95%B0.html)
> 平衡二叉树Balanced Binary Tree[LeetCode](https://leetcode.com/problems/balanced-binary-tree/description/)&[Solutions](https://programmercarl.com/0110.%E5%B9%B3%E8%A1%A1%E4%BA%8C%E5%8F%89%E6%A0%91.html)
> 二叉树的所有路径Binary Tree Paths[LeetCode](https://leetcode.com/problems/binary-tree-paths/description/)&[Solutions](https://programmercarl.com/0257.%E4%BA%8C%E5%8F%89%E6%A0%91%E7%9A%84%E6%89%80%E6%9C%89%E8%B7%AF%E5%BE%84.html)
> 左叶子之和Sum of Left Leaves[LeetCode](https://leetcode.com/problems/sum-of-left-leaves/description/)&[Solutions](https://programmercarl.com/0404.%E5%B7%A6%E5%8F%B6%E5%AD%90%E4%B9%8B%E5%92%8C.html)
> 找树左下角的值 Find Bottom Left Tree Value[LeetCode](https://leetcode.com/problems/find-bottom-left-tree-value/description/)&[Solutions](https://programmercarl.com/0513.%E6%89%BE%E6%A0%91%E5%B7%A6%E4%B8%8B%E8%A7%92%E7%9A%84%E5%80%BC.html)

> 路径总和Path Sum[LeetCode](https://leetcode.com/problems/path-sum/)&[Solutions](https://programmercarl.com/0112.%E8%B7%AF%E5%BE%84%E6%80%BB%E5%92%8C.html)
> 路径总和 II Path Sum II[LeetCode](https://leetcode.com/problems/path-sum-ii/description/)&[Solutions](https://programmercarl.com/0112.%E8%B7%AF%E5%BE%84%E6%80%BB%E5%92%8C.html#%E6%80%9D%E8%B7%AF-2)

> 从中序与后序遍历序列构造二叉树Construct Binary Tree from Inorder and Postorder Traversal[LeetCode](https://leetcode.com/problems/construct-binary-tree-from-inorder-and-postorder-traversal/description/)&[Solutions](https://programmercarl.com/0106.%E4%BB%8E%E4%B8%AD%E5%BA%8F%E4%B8%8E%E5%90%8E%E5%BA%8F%E9%81%8D%E5%8E%86%E5%BA%8F%E5%88%97%E6%9E%84%E9%80%A0%E4%BA%8C%E5%8F%89%E6%A0%91.html)
> 从前序与中序遍历序列构造二叉树Construct Binary Tree from Preorder and Inorder Traversal[LeetCode](https://leetcode.com/problems/construct-binary-tree-from-preorder-and-inorder-traversal/description/)&[Solutions](https://programmercarl.com/0106.%E4%BB%8E%E4%B8%AD%E5%BA%8F%E4%B8%8E%E5%90%8E%E5%BA%8F%E9%81%8D%E5%8E%86%E5%BA%8F%E5%88%97%E6%9E%84%E9%80%A0%E4%BA%8C%E5%8F%89%E6%A0%91.html)
> 最大二叉树Maximum Binary Tree[LeetCode](https://leetcode.com/problems/maximum-binary-tree/)&[Solutions](https://programmercarl.com/0654.%E6%9C%80%E5%A4%A7%E4%BA%8C%E5%8F%89%E6%A0%91.html)

> 合并二叉树Merge Two Binary Trees[LeetCode](https://leetcode.com/problems/merge-two-binary-trees/description/)&[Solutions](https://programmercarl.com/0617.%E5%90%88%E5%B9%B6%E4%BA%8C%E5%8F%89%E6%A0%91.html)

> 二叉搜索树中的搜索Search in a Binary Search Tree[LeetCode](https://leetcode.com/problems/search-in-a-binary-search-tree/description/)&[Solutions](https://programmercarl.com/0700.%E4%BA%8C%E5%8F%89%E6%90%9C%E7%B4%A2%E6%A0%91%E4%B8%AD%E7%9A%84%E6%90%9C%E7%B4%A2.html)
> 验证二叉搜索树Validate Binary Search Tree[LeetCode](https://leetcode.com/problems/validate-binary-search-tree/description/)&[Solutions](https://programmercarl.com/0098.%E9%AA%8C%E8%AF%81%E4%BA%8C%E5%8F%89%E6%90%9C%E7%B4%A2%E6%A0%91.html)
> 二叉搜索树的最小绝对差Minimum Absolute Difference in BST[LeetCode](https://leetcode.com/problems/minimum-absolute-difference-in-bst/description/)&[Solutions](https://programmercarl.com/0530.%E4%BA%8C%E5%8F%89%E6%90%9C%E7%B4%A2%E6%A0%91%E7%9A%84%E6%9C%80%E5%B0%8F%E7%BB%9D%E5%AF%B9%E5%B7%AE.html)
> 二叉搜索树中的众数Find Mode in Binary Search Tree[LeetCode](https://leetcode.com/problems/find-mode-in-binary-search-tree/description/)&[Solutions](https://programmercarl.com/0501.%E4%BA%8C%E5%8F%89%E6%90%9C%E7%B4%A2%E6%A0%91%E4%B8%AD%E7%9A%84%E4%BC%97%E6%95%B0.html)

> 二叉树的最近公共祖先Lowest Common Ancestor of a Binary Tree[LeetCode](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-tree/description/)&[Solutions](https://programmercarl.com/0236.%E4%BA%8C%E5%8F%89%E6%A0%91%E7%9A%84%E6%9C%80%E8%BF%91%E5%85%AC%E5%85%B1%E7%A5%96%E5%85%88.html)
> 二叉搜索树的最近公共祖先 Lowest Common Ancestor of a Binary Search Tree[LeetCode](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-search-tree/description/)&[Solutions](https://programmercarl.com/0235.%E4%BA%8C%E5%8F%89%E6%90%9C%E7%B4%A2%E6%A0%91%E7%9A%84%E6%9C%80%E8%BF%91%E5%85%AC%E5%85%B1%E7%A5%96%E5%85%88.html)

> 二叉搜索树中的插入操作Insert into a Binary Search Tree[LeetCode](https://leetcode.com/problems/insert-into-a-binary-search-tree/description/)&[Solution](https://programmercarl.com/0701.%E4%BA%8C%E5%8F%89%E6%90%9C%E7%B4%A2%E6%A0%91%E4%B8%AD%E7%9A%84%E6%8F%92%E5%85%A5%E6%93%8D%E4%BD%9C.html)
> 删除二叉搜索树中的节点Delete Node in a BST[LeetCode](https://leetcode.com/problems/delete-node-in-a-bst/description/)&[Solutions](https://programmercarl.com/0450.%E5%88%A0%E9%99%A4%E4%BA%8C%E5%8F%89%E6%90%9C%E7%B4%A2%E6%A0%91%E4%B8%AD%E7%9A%84%E8%8A%82%E7%82%B9.html)
> 修剪二叉搜索树Trim a Binary Search Tree[LeetCode](https://leetcode.com/problems/trim-a-binary-search-tree/description/)&[Solutions](https://programmercarl.com/0669.%E4%BF%AE%E5%89%AA%E4%BA%8C%E5%8F%89%E6%90%9C%E7%B4%A2%E6%A0%91.html)
> 将有序数组转换为二叉搜索树Convert Sorted Array to Binary Search Tree[LeetCode](https://leetcode.com/problems/convert-sorted-array-to-binary-search-tree/description/)&[Solutions](https://programmercarl.com/0108.%E5%B0%86%E6%9C%89%E5%BA%8F%E6%95%B0%E7%BB%84%E8%BD%AC%E6%8D%A2%E4%B8%BA%E4%BA%8C%E5%8F%89%E6%90%9C%E7%B4%A2%E6%A0%91.html)
> 把二叉搜索树转换为累加树Convert BST to Greater Tree[LeetCode](https://leetcode.com/problems/convert-bst-to-greater-tree/description/)&[Solutions](https://programmercarl.com/0538.%E6%8A%8A%E4%BA%8C%E5%8F%89%E6%90%9C%E7%B4%A2%E6%A0%91%E8%BD%AC%E6%8D%A2%E4%B8%BA%E7%B4%AF%E5%8A%A0%E6%A0%91.html)

***

# 算法Algorithms

## 1. 递归算法Recursive algorithm

### 1.1 方法论Methodology

1. **确定递归函数的参数和返回值**
   确定哪些参数是递归的过程中需要处理的，那么就在递归函数里加上这个参数， 并且还要明确每次递归的返回值是什么进而确定递归函数的返回类型。

2. **确定终止条件**
   写完了递归算法, 运行的时候，经常会遇到栈溢出的错误，就是没写终止条件或者终止条件写的不对，操作系统也是用一个栈的结构来保存每一层递归的信息，如果递归没有终止，操作系统的内存栈必然就会溢出。

3. **确定单层递归的逻辑**
   确定每一层递归需要处理的信息。在这里也就会重复调用自己来实现递归的过程。

#### 1.1.1 Demo
```python
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def preorderTraversal(self, root: Optional[TreeNode]) -> List[int]:
        result = []
        def traversal(root):
            if root==None:
                return
            result.append(root.val)
            traversal(root.left)
            traversal(root.right)
        traversal(root)
        return result
```

### 1.2 例题Example questions

> 二叉树的前序遍历Binary Tree Preorder Traversal[LeetCode](https://leetcode.com/problems/binary-tree-preorder-traversal/)&[Solutions](https://programmercarl.com/%E4%BA%8C%E5%8F%89%E6%A0%91%E7%9A%84%E9%80%92%E5%BD%92%E9%81%8D%E5%8E%86.html)
> 二叉树的中序遍历Binary Tree Inorder Traversal[LeetCode](https://leetcode.com/problems/binary-tree-inorder-traversal/)&[Solutions](https://programmercarl.com/%E4%BA%8C%E5%8F%89%E6%A0%91%E7%9A%84%E9%80%92%E5%BD%92%E9%81%8D%E5%8E%86.html)
> 二叉树的后序遍历Binary Tree Postorder Traversal[LeetCode](https://leetcode.com/problems/binary-tree-postorder-traversal/)&[Solutions](https://programmercarl.com/%E4%BA%8C%E5%8F%89%E6%A0%91%E7%9A%84%E9%80%92%E5%BD%92%E9%81%8D%E5%8E%86.html)

## 2.回溯算法Backtracking

### 2.0 回溯算法题目分类

![回溯算法题目分类](https://img-blog.csdnimg.cn/20210219192050666.png)

### 2.1 定义Definition

1.  回溯是递归的副产品，只要有递归就会有回溯。回溯函数也就是递归函数。
2.  回溯法解决的问题都可以抽象为树形结构；因为回溯法解决的都是在集合中递归查找子集，集合的大小就构成了树的宽度，递归的深度，都构成的树的深度。

### 2.2 方法论Methodology

1.  **返回值以及参数**
    返回值一般为void；因为回溯算法需要的参数可不像二叉树递归的时候那么容易一次性确定下来，所以一般是先写逻辑，然后需要什么参数，就填什么参数。

```python
void backtracking(参数)
```

2.  **终止条件**

```python
if (终止条件) {
    存放结果;
    return;
}
```

3.  **遍历过程**
    <img src="https://img-blog.csdnimg.cn/20210130173631174.png" alt="递归和遍历" style="zoom:50%;" />
    剪枝优化（与上图题目不同）
    <img src="20210130194335207.png" alt="剪枝优化" style="zoom:50%;" />
    for循环可以理解是横向遍历
    backtracking（递归)就是纵向遍历

```python
for (选择：本层集合中元素（树中节点孩子的数量就是集合的大小）) {
    处理节点;
    backtracking(路径，选择列表); // 递归
    回溯，撤销处理结果
}
```

### 2.3 组合问题

> 组合Combinations[LeetCode](https://leetcode.com/problems/combinations/description/)&[Solutions](https://programmercarl.com/0077.%E7%BB%84%E5%90%88.html)
> 组合总和 IIICombination Sum III[LeetCode](https://leetcode.com/problems/combination-sum-iii/description/)&[Solutions](https://programmercarl.com/0216.%E7%BB%84%E5%90%88%E6%80%BB%E5%92%8CIII.html)
> 电话号码的字母组合Letter Combinations of a Phone Number[LeetCode](https://leetcode.com/problems/letter-combinations-of-a-phone-number/description/)&[Solutions](https://programmercarl.com/0017.%E7%94%B5%E8%AF%9D%E5%8F%B7%E7%A0%81%E7%9A%84%E5%AD%97%E6%AF%8D%E7%BB%84%E5%90%88.html)
> 组合总和Combination Sum[LeetCode](https://leetcode.com/problems/combination-sum/description/)&[Solutions](https://programmercarl.com/0039.%E7%BB%84%E5%90%88%E6%80%BB%E5%92%8C.html)
> 组合总和 IICombination Sum II[LeetCode](https://leetcode.com/problems/combination-sum-ii/description/)&[Solutions](https://programmercarl.com/0040.%E7%BB%84%E5%90%88%E6%80%BB%E5%92%8CII.html)

### 2.4 分割问题

![分割问题](https://code-thinking.cdn.bcebos.com/pics/131.%E5%88%86%E5%89%B2%E5%9B%9E%E6%96%87%E4%B8%B2.jpg)

> 分割回文串Palindrome Partitioning[LeetCode](https://leetcode.com/problems/palindrome-partitioning/description/)&[Solutions](https://programmercarl.com/0131.%E5%88%86%E5%89%B2%E5%9B%9E%E6%96%87%E4%B8%B2.html)
> 复原 IP 地址Restore IP Addresses[LeetCode](https://leetcode.com/problems/restore-ip-addresses/description/)&[Solutions](https://programmercarl.com/0093.%E5%A4%8D%E5%8E%9FIP%E5%9C%B0%E5%9D%80.html)

### 2.5 子集问题

![subsets](https://img-blog.csdnimg.cn/202011232041348.png)

1.  子集：收集树形结构中树的所有节点的结果
2.  组合问题、分割问题：收集树形结构中叶子节点的结果

> 子集Subsets[LeetCode](https://leetcode.com/problems/subsets/description/)&[Solutions](https://programmercarl.com/0078.%E5%AD%90%E9%9B%86.html)
> 子集IISubsets II[LeetCode](https://leetcode.com/problems/subsets-ii/description/)&[Solutions](https://programmercarl.com/0090.%E5%AD%90%E9%9B%86II.html)
> 递增子序列Non-decreasing Subsequences[LeetCode](https://leetcode.com/problems/non-decreasing-subsequences/description/)&[Solutions](https://programmercarl.com/0491.%E9%80%92%E5%A2%9E%E5%AD%90%E5%BA%8F%E5%88%97.html)

### 2.6 排列问题

> 全排列Permutations[LeetCode](https://leetcode.com/problems/permutations/description/)&[Solutions](https://programmercarl.com/0046.%E5%85%A8%E6%8E%92%E5%88%97.html)
> 全排列 IIPermutations II[LeetCode](https://leetcode.com/problems/permutations-ii/description/)&[Solutions](https://programmercarl.com/0047.%E5%85%A8%E6%8E%92%E5%88%97II.html)
> 重新安排行程Reconstruct Itinerary[LeetCode](https://leetcode.com/problems/reconstruct-itinerary/description/)&[Solutions](https://programmercarl.com/0332.%E9%87%8D%E6%96%B0%E5%AE%89%E6%8E%92%E8%A1%8C%E7%A8%8B.html)

### 2.7 棋盘问题
> N 皇后N-Queens[LeetCode](https://leetcode.com/problems/n-queens/description/)&[Solutions](https://programmercarl.com/0051.N%E7%9A%87%E5%90%8E.html)
> 解数独Sudoku Solver[LeetCode](https://leetcode.com/problems/sudoku-solver/)&[Solutions](https://programmercarl.com/0037.%E8%A7%A3%E6%95%B0%E7%8B%AC.html)

## 3.贪心算法Greedy algorithm
### 3.0 题目分类
![题目分类](https://code-thinking-1253855093.file.myqcloud.com/pics/20210917104315.png)
### 3.1 算法选择
选择每一阶段的局部最优，从而达到全局最优：**贪心算法**
否则：试试**动态规划**

### 3.2 解题步骤
1. 将问题分解为若干个子问题
2. 找出适合的贪心策略
3. 求解每一个子问题的最优解
4. 将局部最优解堆叠成全局最优解

>分发饼干Assign Cookies[LeetCode](https://leetcode.com/problems/assign-cookies)&[Solutions](https://programmercarl.com/0455.%E5%88%86%E5%8F%91%E9%A5%BC%E5%B9%B2.html)
>K 次取反后最大化的数组和Maximize Sum Of Array After K Negations[LeetCode](https://leetcode.com/problems/maximize-sum-of-array-after-k-negations/description/)&[Solutions](https://programmercarl.com/1005.K%E6%AC%A1%E5%8F%96%E5%8F%8D%E5%90%8E%E6%9C%80%E5%A4%A7%E5%8C%96%E7%9A%84%E6%95%B0%E7%BB%84%E5%92%8C.html)
>柠檬水找零Lemonade Change[LeetCode](https://leetcode.com/problems/lemonade-change/description/)&[Solutions](https://programmercarl.com/0860.%E6%9F%A0%E6%AA%AC%E6%B0%B4%E6%89%BE%E9%9B%B6.html)

### 3.3 序列问题
>摆动序列Wiggle Subsequence[LeetCode](https://leetcode.com/problems/wiggle-subsequence/description/)&[Solutions](https://programmercarl.com/0376.%E6%91%86%E5%8A%A8%E5%BA%8F%E5%88%97.html)
>单调递增的数字Monotone Increasing Digits[LeetCode](https://leetcode.com/problems/monotone-increasing-digits)&[Solutions](https://programmercarl.com/0738.%E5%8D%95%E8%B0%83%E9%80%92%E5%A2%9E%E7%9A%84%E6%95%B0%E5%AD%97.html)

### 3.4 股票问题
>买卖股票的最佳时机 IIBest Time to Buy and Sell Stock II[LeetCode](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-ii)&[Solutions](https://programmercarl.com/0122.%E4%B9%B0%E5%8D%96%E8%82%A1%E7%A5%A8%E7%9A%84%E6%9C%80%E4%BD%B3%E6%97%B6%E6%9C%BAII.html)
>买卖股票的最佳时机含手续费Best Time to Buy and Sell Stock with Transaction Fee[LeetCode](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-with-transaction-fee/description/)&[Solutions](https://programmercarl.com/0714.%E4%B9%B0%E5%8D%96%E8%82%A1%E7%A5%A8%E7%9A%84%E6%9C%80%E4%BD%B3%E6%97%B6%E6%9C%BA%E5%90%AB%E6%89%8B%E7%BB%AD%E8%B4%B9.html)

### 3.5 两个维度权衡问题
>分发糖果Candy[LeetCode](https://leetcode.com/problems/candy/)&[Solutions](https://programmercarl.com/0135.%E5%88%86%E5%8F%91%E7%B3%96%E6%9E%9C.html)
>根据身高重建队列Queue Reconstruction by Height[LeetCode](https://leetcode.com/problems/queue-reconstruction-by-height/description/)&[Solutions](https://programmercarl.com/0406.%E6%A0%B9%E6%8D%AE%E8%BA%AB%E9%AB%98%E9%87%8D%E5%BB%BA%E9%98%9F%E5%88%97.html)

### 3.6 区间问题
>跳跃游戏Jump Game[LeetCode](https://leetcode.com/problems/jump-game/description/)&[Solutions](https://programmercarl.com/0055.%E8%B7%B3%E8%B7%83%E6%B8%B8%E6%88%8F.html)
>跳跃游戏IIJump Game II[LeetCode](https://leetcode.com/problems/jump-game-ii/description/)&[Solutions](https://programmercarl.com/0045.%E8%B7%B3%E8%B7%83%E6%B8%B8%E6%88%8FII.html)
>用最少数量的箭引爆气球Minimum Number of Arrows to Burst Balloons[LeetCode](https://leetcode.com/problems/minimum-number-of-arrows-to-burst-balloons/description/)&[Solutions](https://programmercarl.com/0452.%E7%94%A8%E6%9C%80%E5%B0%91%E6%95%B0%E9%87%8F%E7%9A%84%E7%AE%AD%E5%BC%95%E7%88%86%E6%B0%94%E7%90%83.html)
>无重叠区间Non-overlapping Intervals[LeetCode](https://leetcode.com/problems/non-overlapping-intervals/description/)&[Solutions](https://programmercarl.com/0435.%E6%97%A0%E9%87%8D%E5%8F%A0%E5%8C%BA%E9%97%B4.html)
>划分字母区间Partition Labels[LeetCode](https://leetcode.com/problems/partition-labels/)&[Solutions](https://programmercarl.com/0763.%E5%88%92%E5%88%86%E5%AD%97%E6%AF%8D%E5%8C%BA%E9%97%B4.html)
>合并区间Merge Intervals[LeetCode](https://leetcode.com/problems/merge-intervals/description/)&[Solutions](https://programmercarl.com/0056.%E5%90%88%E5%B9%B6%E5%8C%BA%E9%97%B4.html)

>最大子数组和Maximum Subarray[LeetCode](https://leetcode.com/problems/maximum-subarray/description/)&[Solutions](https://programmercarl.com/0053.%E6%9C%80%E5%A4%A7%E5%AD%90%E5%BA%8F%E5%92%8C.html)
>加油站Gas Station[LeetCode](https://leetcode.com/problems/gas-station)&[Solutions](https://programmercarl.com/0134.%E5%8A%A0%E6%B2%B9%E7%AB%99.html)
>监控二叉树Binary Tree Cameras[LeetCode](https://leetcode.com/problems/binary-tree-cameras/description/)&[Solutions](https://programmercarl.com/0968.%E7%9B%91%E6%8E%A7%E4%BA%8C%E5%8F%89%E6%A0%91.html)

## 4. 动态规划Dynamic Programming
### 4.0 题目分类
![image](https://code-thinking.cdn.bcebos.com/pics/动态规划-总结大纲1.jpg)
### 4.1 解题步骤
区别：
- 动规是由前一个状态推导出来的
- 贪心是局部直接选最优的
1. 确定dp数组（dp table）以及下标的含义
2. 确定递推公式
3. dp数组如何初始化
4. 确定遍历顺序
5. 举例推导dp数组

### 4.2 基础题目
> 斐波那契数Fibonacci Number[LeetCode](https://leetcode.com/problems/fibonacci-number/description/)&[Solutions](https://programmercarl.com/0509.%E6%96%90%E6%B3%A2%E9%82%A3%E5%A5%91%E6%95%B0.html)
> 爬楼梯Climbing Stairs[LeetCode](https://leetcode.com/problems/climbing-stairs/description/)&[Solutions](https://programmercarl.com/0509.%E6%96%90%E6%B3%A2%E9%82%A3%E5%A5%91%E6%95%B0.html)
> 使用最小花费爬楼梯Min Cost Climbing Stairs[LeetCode](https://leetcode.com/problems/min-cost-climbing-stairs/description/)&[Solutions](https://programmercarl.com/0746.%E4%BD%BF%E7%94%A8%E6%9C%80%E5%B0%8F%E8%8A%B1%E8%B4%B9%E7%88%AC%E6%A5%BC%E6%A2%AF.html)
> 不同路径Unique Paths[LeetCode](https://leetcode.com/problems/unique-paths/description/)&[Solutions](https://programmercarl.com/0062.%E4%B8%8D%E5%90%8C%E8%B7%AF%E5%BE%84.html)
> 不同路径 IIUnique Paths II[LeetCode](https://leetcode.com/problems/unique-paths-ii/description/)&[Solutions](https://programmercarl.com/0063.%E4%B8%8D%E5%90%8C%E8%B7%AF%E5%BE%84II.html)
> 整数拆分Integer Break[LeetCode](https://leetcode.com/problems/integer-break/) & [Solutions](https://programmercarl.com/0343.%E6%95%B4%E6%95%B0%E6%8B%86%E5%88%86.html)
> 不同的二叉搜索树Unique Binary Search Trees[LeetCode](https://leetcode.com/problems/unique-binary-search-trees/description/) & [Solutions](https://programmercarl.com/0096.%E4%B8%8D%E5%90%8C%E7%9A%84%E4%BA%8C%E5%8F%89%E6%90%9C%E7%B4%A2%E6%A0%91.html)

### 4.3 背包问题

> 组合问题
>
> ```python
> dp[i] += dp[i-num]
> ```
> True、False问题
> ```python
> dp[i] = dp[i] or dp[i-num]
> ```
>
> 最大最小问题
>
> ```python
> dp[i] = min(dp[i], dp[i-num]+1)
> dp[i] = max(dp[i], dp[i-num]+1)
> ```



> 1.如果是0-1背包，即数组中的元素不可重复使用，nums放在外循环，target在内循环，且内循环倒序；
>
> ```python
> for num in nums:
>     for i in range(target, nums-1, -1):
> ```
>
> 2.如果是完全背包，即数组中的元素可重复使用，nums放在外循环，target在内循环。且内循环正序。
>
> ```python
> for num in nums:
>     for i in range(nums, target+1):
> ```
>
> 3.如果组合问题需考虑元素之间的顺序，需将target放在外循环，将nums放在内循环。
>
> ```python
> for i in range(1, target+1):
>     for num in nums:
> ```

#### 4.3.1 0-1背包

##### 4.3.1.1 [0-1背包理论基础](https://programmercarl.com/%E8%83%8C%E5%8C%85%E7%90%86%E8%AE%BA%E5%9F%BA%E7%A1%8001%E8%83%8C%E5%8C%85-1.html)

```python
dp[i][j] 
= 
max(
  dp[i - 1][j], 
  dp[i - 1][j - weight[i]] + value[i]
)
```

![0-1bag](https://img-blog.csdnimg.cn/20210118163425129.jpg)

```python
def test_2_wei_bag_problem1(bag_size, weight, value) -> int: 
	rows, cols = len(weight), bag_size + 1
	dp = [[0 for _ in range(cols)] for _ in range(rows)]
    
	# 初始化dp数组. 
	for i in range(rows): 
		dp[i][0] = 0
	first_item_weight, first_item_value = weight[0], value[0]
	for j in range(1, cols): 	
		if first_item_weight <= j: 
			dp[0][j] = first_item_value

	# 更新dp数组: 先遍历物品, 再遍历背包. 
	for i in range(1, len(weight)): 
		cur_weight, cur_val = weight[i], value[i]
		for j in range(1, cols): 
			if cur_weight > j: # 说明背包装不下当前物品. 
				dp[i][j] = dp[i - 1][j] # 所以不装当前物品. 
			else: 
				# 定义dp数组: dp[i][j] 前i个物品里，放进容量为j的背包，价值总和最大是多少。
				dp[i][j] = max(dp[i - 1][j], dp[i - 1][j - cur_weight]+ cur_val)

	print(dp)
```



##### 4.3.1.2 [0-1背包理论基础-滚动数组](https://programmercarl.com/%E8%83%8C%E5%8C%85%E7%90%86%E8%AE%BA%E5%9F%BA%E7%A1%8001%E8%83%8C%E5%8C%85-2.html)

```python
dp[j] 
= 
max(
  dp[j], 
  dp[j - weight[i]] + value[i]
)
```

![0-1bag](https://img-blog.csdnimg.cn/20210110103614769.png)

```python
def test_1_wei_bag_problem():
    weight = [1, 3, 4]
    value = [15, 20, 30]
    bag_weight = 4
    # 初始化: 全为0
    dp = [0] * (bag_weight + 1)

    # 先遍历物品, 再遍历背包容量
    for i in range(len(weight)):
        for j in range(bag_weight, weight[i] - 1, -1):
            # 递归公式
            dp[j] = max(dp[j], dp[j - weight[i]] + value[i])

    print(dp)
```



##### 4.3.1.2 例题

> 分割等和子集Partition Equal Subset Sum[LeetCode](https://leetcode.com/problems/partition-equal-subset-sum/description/) & [Solutions](https://programmercarl.com/0416.%E5%88%86%E5%89%B2%E7%AD%89%E5%92%8C%E5%AD%90%E9%9B%86.html)
> 最后一块石头的重量 IILast Stone Weight II[LeetCode](https://leetcode.com/problems/last-stone-weight-ii/description/) & [Solutions](https://programmercarl.com/1049.%E6%9C%80%E5%90%8E%E4%B8%80%E5%9D%97%E7%9F%B3%E5%A4%B4%E7%9A%84%E9%87%8D%E9%87%8FII.html)
> 目标和Target Sum[LeetCode](https://leetcode.com/problems/target-sum/description/)&[Solutions](https://programmercarl.com/0494.%E7%9B%AE%E6%A0%87%E5%92%8C.html)
> >$$
> >left - right = target
> >\\
> >left + right = sum
> >\\\\
> >left = \frac{target + sum}{2}
> >$$
>
> 一和零Ones and Zeroes[LeetCode](https://leetcode.com/problems/ones-and-zeroes/description/) & [Solutions](https://programmercarl.com/0474.%E4%B8%80%E5%92%8C%E9%9B%B6.html)

#### 4.3.2 完全背包

##### 4.3.2.1 完全背包理论基础

> 完全背包和01背包问题唯一不同的地方就是，每种物品有无限件
>
> **对于纯完全背包问题，其for循环的先后循环是可以颠倒的！**

```python
for j in range(bag_weight + 1):
  for i in range(len(weight)):
    if j >= weight[i]: dp[j] = max(dp[j], dp[j - weight[i]] + value[i])##价值
    dp[j] += dp[j - nums[i]]##组合
//如果求组合数就是外层for循环遍历物品，内层for遍历背包。
//如果求排列数就是外层for遍历背包，内层for循环遍历物品。
```

##### 4.3.2.2 例题

> 零钱兑换 II Coin Change II[LeetCode](https://leetcode.com/problems/coin-change-ii/description/) & [Solutions](https://programmercarl.com/0518.%E9%9B%B6%E9%92%B1%E5%85%91%E6%8D%A2II.html)
> 组合总和 ⅣCombination Sum IV[LeetCode](https://leetcode.com/problems/combination-sum-iv/) & [Solutions](https://programmercarl.com/0377.%E7%BB%84%E5%90%88%E6%80%BB%E5%92%8C%E2%85%A3.html)
> 零钱兑换Coin Change[LeetCode](https://leetcode.com/problems/coin-change/description/) & [Solutions](https://programmercarl.com/0322.%E9%9B%B6%E9%92%B1%E5%85%91%E6%8D%A2.html)
>完全平方数Perfect Squares[LeetCode](https://leetcode.com/problems/perfect-squares/description/)&[Solutions](https://programmercarl.com/0279.%E5%AE%8C%E5%85%A8%E5%B9%B3%E6%96%B9%E6%95%B0.html)
> 单词拆分Word Break[LeetCode](https://leetcode.com/problems/word-break/description/)&[Solutions](https://programmercarl.com/0139.%E5%8D%95%E8%AF%8D%E6%8B%86%E5%88%86.html)

### 4.4 打家劫舍
> 打家劫舍House Robber[LeetCode](https://leetcode.com/problems/house-robber/description/)&[Solutions](https://programmercarl.com/0198.%E6%89%93%E5%AE%B6%E5%8A%AB%E8%88%8D.html)
> 打家劫舍 IIHouse Robber II[LeetCode](https://leetcode.com/problems/house-robber-ii/description/)&[Solutions](https://programmercarl.com/0213.%E6%89%93%E5%AE%B6%E5%8A%AB%E8%88%8DII.html)
>打家劫舍 IIIHouse Robber III[LeetCode](https://leetcode.com/problems/house-robber-iii/description/)&[Solutions](https://programmercarl.com/0337.%E6%89%93%E5%AE%B6%E5%8A%AB%E8%88%8DIII.html)

### 4.5 股票问题

> 买卖股票的最佳时机Best Time to Buy and Sell Stock[LeetCode](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/description/)&[Solutions](https://programmercarl.com/0121.%E4%B9%B0%E5%8D%96%E8%82%A1%E7%A5%A8%E7%9A%84%E6%9C%80%E4%BD%B3%E6%97%B6%E6%9C%BA.html)
> 买卖股票的最佳时机 IIIBest Time to Buy and Sell Stock III[LeetCode](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-iii/description/)&[Solutions](https://programmercarl.com/0123.%E4%B9%B0%E5%8D%96%E8%82%A1%E7%A5%A8%E7%9A%84%E6%9C%80%E4%BD%B3%E6%97%B6%E6%9C%BAIII.html)
> 买卖股票的最佳时机 IVBest Time to Buy and Sell Stock IV[LeetCode](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-iv/description/)&[Solutions](https://programmercarl.com/0188.%E4%B9%B0%E5%8D%96%E8%82%A1%E7%A5%A8%E7%9A%84%E6%9C%80%E4%BD%B3%E6%97%B6%E6%9C%BAIV.html)
>  最佳买卖股票时机含冷冻期Best Time to Buy and Sell Stock with Cooldown[LeetCode](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-with-cooldown/description/)&[Solutions](https://programmercarl.com/0309.%E6%9C%80%E4%BD%B3%E4%B9%B0%E5%8D%96%E8%82%A1%E7%A5%A8%E6%97%B6%E6%9C%BA%E5%90%AB%E5%86%B7%E5%86%BB%E6%9C%9F.html)
### 4.6 子序列问题

#### 4.6.1 子序列（不连续）
> 最长递增子序列Longest Increasing Subsequence[LeetCode](https://leetcode.com/problems/longest-increasing-subsequence/description/)&[Solutions](https://programmercarl.com/0300.%E6%9C%80%E9%95%BF%E4%B8%8A%E5%8D%87%E5%AD%90%E5%BA%8F%E5%88%97.html)
> 最长公共子序列Longest Common Subsequence[LeetCode](https://leetcode.com/problems/longest-common-subsequence/description/)&[Solutions](https://programmercarl.com/1143.%E6%9C%80%E9%95%BF%E5%85%AC%E5%85%B1%E5%AD%90%E5%BA%8F%E5%88%97.html)
> ```python
> if text1[j-1] == text2[i-1]:
>     dp[i][j] = dp[i-1][j-1]+1
> else:
>     dp[i][j] = max(dp[i-1][j], dp[i][j-1])
> ```
> 不相交的线Uncrossed Lines[LeetCode](https://leetcode.com/problems/uncrossed-lines/description/)&[Solutions](https://programmercarl.com/1035.%E4%B8%8D%E7%9B%B8%E4%BA%A4%E7%9A%84%E7%BA%BF.html)
#### 4.6.2 子序列（连续）
> 最长连续递增序列Longest Continuous Increasing Subsequence[LeetCode](https://leetcode.com/problems/longest-continuous-increasing-subsequence/description/)&[Solutions](https://programmercarl.com/0674.%E6%9C%80%E9%95%BF%E8%BF%9E%E7%BB%AD%E9%80%92%E5%A2%9E%E5%BA%8F%E5%88%97.html)
> 最长重复子数组Maximum Length of Repeated Subarray[LeetCode](https://leetcode.com/problems/maximum-length-of-repeated-subarray/description/)&[Solutions](https://programmercarl.com/0718.%E6%9C%80%E9%95%BF%E9%87%8D%E5%A4%8D%E5%AD%90%E6%95%B0%E7%BB%84.html)
#### 4.6.3 编辑距离
>判断子序列Is Subsequence[LeetCode](https://leetcode.com/problems/is-subsequence/description/)&[Solutions](https://programmercarl.com/0392.%E5%88%A4%E6%96%AD%E5%AD%90%E5%BA%8F%E5%88%97.html)
>不同的子序列Distinct Subsequences[LeetCode](https://leetcode.com/problems/distinct-subsequences/description/)&[Solutions](https://programmercarl.com/0115.%E4%B8%8D%E5%90%8C%E7%9A%84%E5%AD%90%E5%BA%8F%E5%88%97.html#%E6%80%9D%E8%B7%AF)
>```python
>if t[j-1] == s[i-1]:
>    dp[j][i] = dp[j-1][i-1]+dp[j][i-1]
>else:
>    dp[j][i] = dp[j][i-1]
>```
>两个字符串的删除操作Delete Operation for Two Strings[LeetCode](https://leetcode.com/problems/delete-operation-for-two-strings/description/)&[Solutions](https://programmercarl.com/0583.%E4%B8%A4%E4%B8%AA%E5%AD%97%E7%AC%A6%E4%B8%B2%E7%9A%84%E5%88%A0%E9%99%A4%E6%93%8D%E4%BD%9C.html#%E6%80%9D%E8%B7%AF)
>编辑距离Edit Distance[LeetCode](https://leetcode.com/problems/edit-distance/description/)&[Solutions](https://programmercarl.com/0072.%E7%BC%96%E8%BE%91%E8%B7%9D%E7%A6%BB.html)
#### 4.6.4 回文
> 回文子串Palindromic Substrings[LeetCode](https://leetcode.com/problems/palindromic-substrings/description/)&[Solutions](https://programmercarl.com/0647.%E5%9B%9E%E6%96%87%E5%AD%90%E4%B8%B2.html)
> 最长回文子序列Longest Palindromic Subsequence[LeetCode](https://leetcode.com/problems/longest-palindromic-subsequence/description/)&[Solutions](https://programmercarl.com/0516.%E6%9C%80%E9%95%BF%E5%9B%9E%E6%96%87%E5%AD%90%E5%BA%8F%E5%88%97.html)

## 5. 单调栈
> 每日温度Daily Temperatures[LeetCode](https://leetcode.com/problems/daily-temperatures/)&[Solutions](https://programmercarl.com/0739.%E6%AF%8F%E6%97%A5%E6%B8%A9%E5%BA%A6.html)
> 下一个更大元素 I Next Greater Element I [LeetCode](https://leetcode.com/problems/next-greater-element-i/) & [Solutions](https://programmercarl.com/0496.%E4%B8%8B%E4%B8%80%E4%B8%AA%E6%9B%B4%E5%A4%A7%E5%85%83%E7%B4%A0I.html)
> 下一个更大元素 II Next Greater Element II[LeetCode](https://leetcode.com/problems/next-greater-element-ii/description/)&[Solutions](https://programmercarl.com/0503.%E4%B8%8B%E4%B8%80%E4%B8%AA%E6%9B%B4%E5%A4%A7%E5%85%83%E7%B4%A0II.html)
> 接雨水Trapping Rain Water[LeetCode](https://leetcode.com/problems/trapping-rain-water/description/)&[Solutions](https://programmercarl.com/0042.%E6%8E%A5%E9%9B%A8%E6%B0%B4.html#%E5%85%B6%E4%BB%96%E8%AF%AD%E8%A8%80%E7%89%88%E6%9C%AC)
> 柱状图中最大的矩形Largest Rectangle in Histogram[LeetCode](https://leetcode.com/problems/largest-rectangle-in-histogram/description/)&[Solutions](https://programmercarl.com/0084.%E6%9F%B1%E7%8A%B6%E5%9B%BE%E4%B8%AD%E6%9C%80%E5%A4%A7%E7%9A%84%E7%9F%A9%E5%BD%A2.html#%E5%85%B6%E4%BB%96%E8%AF%AD%E8%A8%80%E7%89%88%E6%9C%AC)

## 6. 分治

> 一种递归算法
> 将问题划分为更小的子问题，然后将子问题的解组合起来以获得原始问题的解决方案。
>
> 该算法包含三个基本步骤：
> - 分解
> - 解决
> - 合并
>
> One of  recursive algorithm
> divides a problem into smaller subproblems and then combines the solutions to the subproblems to obtain a solution to the original problem. 
> The algorithm consists of three basic steps: 
> - decomposition
> - resolution
> - merging

```python
def find_max_element(arr):
    # 基本情况：数组为空或只有一个元素
    if len(arr) == 0:
        return None
    if len(arr) == 1:
        return arr[0]
    
    # 分解步骤：将数组划分为两个子数组
    mid = len(arr) // 2
    left_arr = arr[:mid]
    right_arr = arr[mid:]
    
    # 解决步骤：递归调用分治算法求解左右子数组的最大元素
    left_max = find_max_element(left_arr)
    right_max = find_max_element(right_arr)
    
    # 合并步骤：比较左右子数组的最大元素，返回较大的一个
    return max(left_max, right_max)

# 示例用法
array = [3, 8, 2, 5, 1, 9, 4]
max_element = find_max_element(array)
print("最大元素是:", max_element)
```

### 6.1 快速排序quick_sort

```python
def quick_sort(arr):
    if len(arr) <= 1:
        return arr
    else:
        pivot = arr[-1]
        smaller, equal, larger = [], [], []
        for num in arr:
            if num < pivot:
                smaller.append(num)
            elif num == pivot:
                equal.append(num)
            else:
                larger.append(num)
        return quick_sort(smaller) + equal + quick_sort(larger)

# 示例用法
arr = [7, 2, 1, 6, 8, 5, 3, 4]
sorted_arr = quick_sort(arr)
print(sorted_arr)
```

#### 6.1.1 快速选择quick_select

```python
def quick_select(arr, k):
    if len(arr) == 1:
        return arr[0]
    else:
        pivot = arr[-1]
        smaller, equal, larger = [], [], []
        for num in arr:
            if num < pivot:
                smaller.append(num)
            elif num == pivot:
                equal.append(num)
            else:
                larger.append(num)
        if k <= len(smaller):
            return quick_select(smaller, k)
        elif k > len(smaller) + len(equal):
            return quick_select(larger, k - len(smaller) - len(equal))
        else:
            return pivot

# 示例用法
arr = [7, 2, 1, 6, 8, 5, 3, 4]
k = 3
kth_smallest = quick_select(arr, k)
print(kth_smallest)
```
> 数组中的第K个最大元素 Kth Largest Element in an Array [LeetCode](https://leetcode.com/problems/kth-largest-element-in-an-array/description/)