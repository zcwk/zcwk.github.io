---
layout: post
title: 快速开发必备利器-备忘录
category: Android
tags: 快速开发
keywords: Android,工具
---

平时在其他人的博客或者网站上看到的快速开发工具的集合。自己备份一下，利于下次用到时快速找到

## 1. 冒泡排序 (Bubble Sort)

冒泡排序是最简单粗暴的排序方法之一。它的原理很简单，每次从左到右两两比较，把大的交换到后面，每次可以确保将前M个元素的最大值移动到最右边。

**步骤**

1. 从左开始比较相邻的两个元素x和y，如果 x > y 就交换两者
2. 执行比较和交换，直到到达数组的最后一个元素
3. 重复执行1和2，直到执行n次，也就是n个最大元素都排到了最后

```CPP
void bubble_sort(vector<int> &nums)
{
    for (int i = 0; i < nums.size() - 1; i++) { // times
        for (int j = 0; j < nums.size() - i - 1; j++) { // position
            if (nums[j] > nums[j + 1]) {
                int temp = nums[j];
                nums[j] = nums[j + 1];
                nums[j + 1] = temp;
            }
        }
    }
}
```

交换的那一步可以不借助temp，方法是

```CPP
nums[j] += nums[j + 1];
nums[j + 1] = num[j] - nums[j + 1];
nums[j] -= num[j + 1];
```


## 0. 参考

- 维基百科
- [经典排序算法总结与实现](http://wuchong.me/blog/2014/02/09/algorithm-sort-summary/)
- [堆排序C++实现](http://segmentfault.com/a/1190000002466215)
- [常见排序算法 - 堆排序 (Heap Sort)](http://bubkoo.com/2014/01/14/sort-algorithm/heap-sort/)
