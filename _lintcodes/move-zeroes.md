---
title: Move Zeroes
author: Haijun (Navy) Su
layout: page
difficulty: Easy
lintcode_link: http://www.lintcode.com/en/problem/move-zeroes/
leetcode_link: https://leetcode.com/problems/move-zeroes/#/description
tags: [Array,Two Pointers]
---
## Question
Given an array <font style="color: #C72541; background: #F9F2F4;">nums</font>, write a function to move all <font style="color: #C72541; background: #F9F2F4;">0</font>'s to the end of it while maintaining the relative order of the non-zero elements.

<i class="fa fa-info-circle" aria-hidden="true"></i> Notice
a) You must do this in-place without making a copy of the array.
b) Minimize the total number of operations.
{: .note}

**Example**
Given <font style="color: #C72541; background: #F9F2F4;">nums = [0, 1, 0, 3, 12]</font>, after calling your function, <font style="color: #C72541; background: #F9F2F4;">nums</font> should be <font style="color: #C72541; background: #F9F2F4;">[1, 3, 12, 0, 0]</font>.

## Thinking
* 0 always be moved to the last position
* Shift all elements
* Make sure to check current element again.

## Review
* Using Two Pointers
![Move Zeros](/images/Lintcode/MoveZeros.png)

## Solution
#### Java (Two pointers)
~~~ java
public class Solution {
    public void moveZeroes(int[] nums) {
        if (nums == null || nums.length <= 1) {
            return;
        }
        for (int i = 0, j = 0; i < nums.length; i++) {
            if (nums[i] != 0) {
                int tmp = nums[j];
                nums[j++] = nums[i];
                nums[i] = tmp;
            }
        }
        
    }
}
~~~

#### Java (Two for loop. Not good)
~~~ java
public class Solution {
    /**
     * @param nums an integer array
     * @return nothing, do this in-place
     */
    public void moveZeroes(int[] nums) {
        // Write your code here
        if (nums == null) {
            return;
        }
        int zeroCount = 0;
        for (int i = 0; i < nums.length; i++) {
            if ((i + zeroCount) == nums.length) {
                break;
            }
            if (nums[i] == 0) {
                for (int j = i; j < nums.length - 1; j++) {
                    nums[j] = nums[j + 1];
                }
                nums[nums.length - 1] = 0;
                zeroCount++;
                i--; // check current element again
            }
        }
    }
}
~~~
