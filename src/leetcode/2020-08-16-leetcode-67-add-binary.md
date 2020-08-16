---
title: "Leetcode #67. Add Binary"
type: posts
published: 2020-08-16
tag: leetcode
---
Given two binary strings, return their sum (also a binary string).

The input strings are both non-empty and contains only characters `1` or `0`.
```javascript
/**
 * @param {string} a
 * @param {string} b
 * @return {string}
 */
var addBinary = function(a, b) {
    /*
        Goals:
        1. Start at the end of both strings, calculate the sum
        2. At each position, append to the result string by mod sum by 2
        3. Calculate carry by divided sum by 2
        4. After the while loop, if there is still a 1 carry, append to string
        5. Reverse string
    */
    var aLength = a.length - 1;
    var bLength = b.length - 1;
    var result = '';
    
    var carry = 0;
    
    while (aLength >= 0 || bLength >= 0) {
        var sum = carry;
        
        sum += a[aLength] ? Number(a[aLength]) : 0;
        sum += b[bLength] ? Number(b[bLength]) : 0;
        
        result += sum % 2;
        carry = Math.floor(sum / 2);
        
        aLength--;
        bLength--;
    }
    
    if (carry !== 0) {
        result += carry;
    }
    
    return result.split('').reverse().join('');
};
```

<!-- more -->