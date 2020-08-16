---
title: "Leetcode #34. Find First and Last Position of Element in Sorted Array"
type: posts
published: 2020-08-13
tag: leetcode
---
Given an array of integers nums sorted in ascending order, find the starting and ending position of a given target value.

Your algorithm's runtime complexity must be in the order of O(log n).

If the target is not found in the array, return [-1, -1].

```javascript
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number[]}
 */
var searchRange = function(nums, target) {
    /*
        1. Binary search for the left most
        2. Linear search for the right most
    */
    
    var result = [-1, -1];
    var left = 0;
    var right = nums.length;
    var mid;
    
    while (left <= right) {
        mid = Math.floor((left + right)/2);
        
        if (nums[mid] === target) {
            result[0] = mid;
            right = mid - 1;
        } else if (nums[mid] > target) {
            right = mid - 1;
        } else {
            left = mid + 1;
        }
    }
    
    if (result[0] === -1) {
        return [-1, -1];
    }
    
    for (let i = nums.length - 1; i >= result[0]; i--) {
        if (nums[i] === target) {
            result[1] = i;
            break;
        }
    }
    
    return result;
};
```

<!-- more -->