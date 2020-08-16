---
title: "Leetcode #56. Merge Intervals"
type: posts
published: 2020-08-14
tag: leetcode
---
Given a collection of intervals, merge all overlapping intervals.
```javascript
/**
 * @param {number[][]} intervals
 * @return {number[][]}
 */
var merge = function(intervals) {
    if (intervals.length <= 1) {
        return intervals;
    }
  
    // 1. Sort intervals ascending
    intervals.sort((a, b) => a[0] - b[0]);
    
    for (let i = 0; i < intervals.length; i++) {
        const current = intervals[i];
        const next = intervals[i + 1];

        // if i is not at the end of array and the end of current is greater than the first of next
        // eg. [1,3],[2,6]
        if (i !== intervals.length - 1 && current[1] >= next[0]) {
            current[1] = Math.max(current[1], next[1]); // set end of current to the larger number
            intervals.splice(i, 2, current); // replace the 2 items with current;
            i--; // start from beginning
        }
    }
    
    return intervals;
};
```