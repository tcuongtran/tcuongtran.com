---
template: post
title: "Leetcode #31. Next Permutation"
slug: leetcode-31-next-permutation
draft: false
date: 2020-08-12T04:38:43.445Z
description: https://leetcode.com/problems/next-permutation/
category: Leetcode
tags:
  - leetcode
---
### Leetcode 31. Next Permutation

Implement next permutation, which rearranges numbers into the lexicographically next greater permutation of numbers.

If such arrangement is not possible, it must rearrange it as the lowest possible order (ie, sorted in ascending order).

The replacement must be in-place and use only constant extra memory.

Here are some examples. Inputs are in the left-hand column and its corresponding outputs are in the right-hand column.

1,2,3 → 1,3,2
3,2,1 → 1,2,3
1,1,5 → 1,5,1

```javascript
/**
 * @param {number[]} nums
 * @return {void} Do not return anything, modify nums in-place instead.
 */
var nextPermutation = function(nums) {
    /*
        Steps:
            1. Find the first decreasing number
            2. Swap that number with the next larger number on the right
            3. Sort the numbers to the right
    */
    
    let findNextLargerNumber = (i) => {
        for (let j = nums.length - 1; j >= i; j--) {
            if (nums[j] > nums[i]) {
                return j;
            }
        }
    }
    
    let swapIndex;
    let nextLargerIndex;
    
    for (let i = nums.length - 1; i >= 0; i--) {
        if (nums[i] < nums[i + 1]) { // 1. Find the first decreasing number
            swapIndex = i;
            nextLargerIndex = findNextLargerNumber(i); // find the next larger number to the right
            break;
        }
    }
    
    // 2. Swap that number with the next larger number on the right
    let temp = nums[swapIndex];
    nums[swapIndex] = nums[nextLargerIndex];
    nums[nextLargerIndex] = temp;
    
    //3. Sort the numbers to the right
    let toTheRight = nums.splice(swapIndex + 1);
    toTheRight.reverse();
    
    toTheRight.forEach(number => nums.push(number));
};
```