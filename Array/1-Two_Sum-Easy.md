## 题目描述

给定一个整数数组 ***nums*** 和一个目标值 ***target*** ，请你在该数组中找出和为目标值的那 **两个** 整数，并返回他们的数组下标。

*你可以假设每种输入只会对应一个答案。但是，数组中同一个元素不能使用两遍*

> nums = [2, 7, 11, 15] , target = 9
>
> nums [0] + nums [1] = 2 + 7 = 9
> return [0, 1]

# 暴力法

## 		分析

​		遍历 ***nums[i]*** 查找是否存在另一个元素等于 ***target - nums[i]***

## 		算法



## 		代码

```java
class Solution {
    public int[] twoSum(int[] nums, int target) {
        for (int i = 0; i < nums.length; i++) {
            for (int j = i + 1; j < nums.length; j++) {
                if (nums[j] == target - nums[i]) {
                    return new int[] { i, j };
                }
            }
        }
        throw new IllegalArgumentException("No two sum solution");
    }
}
```

## 		复杂度分析

- 时间复杂度：两层嵌套循环
  $$
  O(n^2)
  $$

- 空间复杂度：
  $$
  O(1)
  $$

# 哈希表

## 	分析

​		遍历数组，若 ***Map*** 中不存在元素等于 ***target-nums[i]*** ，则将 元素值（key）和 数组下标（value）存入 ***Map*** ，否则返回两个值的下标

## 	算法



## 	代码

```java
class Solution {
    public int[] twoSum(int[] nums, int target) {
        Map<Integer,Integer> map=new HashMap<>();
        for(int i=0;i<nums.length;i++){
            int complement=target-nums[i];
            if(map.containsKey(complement)){
                return new int[]{map.get(complement),i};
            }
            map.put(nums[i],i);
        }
        throw new IllegalArgumentException("No two sum solution");
    }
}
```

## 	复杂度分析

- ​	时间复杂度：一次循环，哈希表的查找用时为 *O(1)*
  $$
  O(n)
  $$
- ​	时间复杂度：最多需要 n 个 ***Map*** 元素
  $$
  O(n)
  $$

