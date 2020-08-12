---
title: Leetcode 31. Next Permutation
type: posts
tag: leetcode
published: 2020-08-11
---

### Leetcode 31. Next Permutation

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

<!-- more -->