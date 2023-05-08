---
title: Find lists of combinations where the numbers sum to target
type: snippet
language: javascript
tags: [math,algorithm]
cover: laptop-view
dateModified: 2023-05-07T05:00:00-04:00
---

Returns all possible lists of unique combinations of `candidates` where the sum of the list equals the target value.

- `calc()` takes in index, tempData, candidates, target and result.
- The value of `tempData` is added using `push()` with `candidates[i]` until
  `total == target` or `total > target` or `index >= candidates.length`
- The last value of `tempData` gets deleted using `pop()` and added with the next value of the `candidates`.
- Steps are repeated trying every possible combination of `candidates`
- If `total == target` the array is added to `result` using `push()`

```js
const sumTarget = (candidates, target) => {
    const result = [];
    calc(0, [], 0, candidates, target, result)
    return result;
};

const calc = (i, tempData, total, candidates, target, result) => {
    if (total == target) {
        result.push([...tempData]);
        return;
    }
    else if (i >= candidates.length || total > target) {
        return;
    }
    tempData.push(candidates[i]);
    calc(i, tempData, total + candidates[i], candidates, target, result);
    tempData.pop();
    calc(i+1, tempData, total, candidates, target, result);
};
```

```js
sumTarget([2,3,8], 12); 
// [
//   [ 2, 2, 2, 2, 2, 2 ],
//   [ 2, 2, 2, 3, 3 ],
//   [ 2, 2, 8 ],
//   [ 3, 3, 3, 3 ]
// ]

```
