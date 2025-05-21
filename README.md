# DSAPractice2025

189. Rotate Array
Solved
Medium
Topics
Companies
Hint
Given an integer array nums, rotate the array to the right by k steps, where k is non-negative.

 

Example 1:

Input: nums = [1,2,3,4,5,6,7], k = 3
Output: [5,6,7,1,2,3,4]
Explanation:
rotate 1 steps to the right: [7,1,2,3,4,5,6]
rotate 2 steps to the right: [6,7,1,2,3,4,5]
rotate 3 steps to the right: [5,6,7,1,2,3,4]
Example 2:

Input: nums = [-1,-100,3,99], k = 2
Output: [3,99,-1,-100]
Explanation: 
rotate 1 steps to the right: [99,-1,-100,3]
rotate 2 steps to the right: [3,99,-1,-100]
 

Constraints:

1 <= nums.length <= 105
-231 <= nums[i] <= 231 - 1
0 <= k <= 105


Here's a working **two-pointer** approach using **reversals** (in-place rotation):

```js
var rotate = function(nums, k) {
    k = k % nums.length;

    // Helper to reverse elements between two indices
    function reverse(start, end) {
        while (start < end) {
            [nums[start], nums[end]] = [nums[end], nums[start]];
            start++;
            end--;
        }
    }

    reverse(0, nums.length - 1);        // Reverse entire array
    reverse(0, k - 1);                  // Reverse first k elements
    reverse(k, nums.length - 1);        // Reverse rest
};

let nums = [1, 2, 3, 4, 5, 6, 7];
let k = 3;

rotate(nums, k);
console.log(nums); // Output: [5,6,7,1,2,3,4]
```

### Steps:

1. Reverse the full array: `[7,6,5,4,3,2,1]`
2. Reverse first `k` elements: `[5,6,7,4,3,2,1]`
3. Reverse the rest: `[5,6,7,1,2,3,4]`


Sure! Let me explain it like you're a school kid. 😊

### Goal:

You have this list of numbers:

```
[1, 2, 3, 4, 5, 6, 7]
```

And you want to **rotate it to the right by 3 steps**, so the last 3 numbers go to the front:

```
Result: [5, 6, 7, 1, 2, 3, 4]
```

---

### Trick: Reverse in 3 steps! 🔄

#### ✅ Step 1: Reverse the whole list

Imagine you turn the list around:

```
Before: [1, 2, 3, 4, 5, 6, 7]
After:  [7, 6, 5, 4, 3, 2, 1]
```

---

#### ✅ Step 2: Reverse just the first 3 numbers (because `k = 3`)

Now flip only the first 3 numbers:

```
Before: [7, 6, 5, 4, 3, 2, 1]
After:  [5, 6, 7, 4, 3, 2, 1]
```

---

#### ✅ Step 3: Reverse the rest (from index 3 to end)

Now flip the remaining numbers:

```
Before: [5, 6, 7, 4, 3, 2, 1]
After:  [5, 6, 7, 1, 2, 3, 4]
```

---

🎉 Done! You rotated the list by 3 steps to the right!
Isn’t that like a magic trick using 3 flips? 😊

Sure! Here's a **simple algorithm** (like in school steps) to **rotate an array to the right by `k` steps** using the reverse method:

---

### 🧠 **Rotate Array (Right) Algorithm**

**Input:**

* An array `nums`
* A number `k` (how many steps to rotate)

**Steps:**

1. Set `k = k % length of nums`
   *(This makes sure we don’t rotate more than needed)*

2. **Reverse the whole array**
   (Flip the order from start to end)

3. **Reverse the first `k` elements**
   (Flip from index `0` to `k - 1`)

4. **Reverse the rest of the array**
   (Flip from index `k` to the end)

5. Done! The array is now rotated.

---

### ✨ Example:

`nums = [1, 2, 3, 4, 5, 6, 7]`
`k = 3`

After Step 2 → `[7, 6, 5, 4, 3, 2, 1]`
After Step 3 → `[5, 6, 7, 4, 3, 2, 1]`
After Step 4 → `[5, 6, 7, 1, 2, 3, 4]` ✅

---

Absolutely! Let me explain this line:

```js
k = k % nums.length;
```

### 🏫 Imagine this:

You have a group of 7 kids standing in a line:

```
[1, 2, 3, 4, 5, 6, 7]
```

You want to rotate them to the right by `k` steps.

But what if someone says:

> "Rotate by 10 steps"

Hmm… 10 steps? But there are only 7 kids! 🤔
After 7 full steps, **they’ll be back to the same place**!

So, rotating by 10 is the same as rotating by:

```
10 % 7 = 3
```

That `%` is called **modulo** — it tells us **what’s left after full rounds**.

---

### 🎯 Why do we write this?

```js
k = k % nums.length;
```

Because:

* If `k` is **bigger than the array size**, we only care about the **extra steps**.
* It **saves time** and avoids extra work.

---

### Example:

* `nums.length = 7`
* If `k = 10` → `k % 7 = 3` → we just rotate 3 steps

So this line makes sure `k` is never more than the array length. ✅

Sure! Let's explain this like a school kid 😊

You have an array:

```js
nums = [1, 2, 3, 4, 5, 6, 7]
k = 3
```

Your goal: Rotate it **right** by `k = 3` steps → Final answer should be:

```
[5, 6, 7, 1, 2, 3, 4]
```

---

### ✨ Trick: Flip parts of the array in 3 steps!

#### Step 1: `reverse(0, nums.length - 1)`

**Flip the whole array**

```js
Before: [1, 2, 3, 4, 5, 6, 7]  
After:  [7, 6, 5, 4, 3, 2, 1]
```

---

#### Step 2: `reverse(0, k - 1)`

**Flip the first `k` = 3 numbers**

```js
Before: [7, 6, 5, 4, 3, 2, 1]  
After:  [5, 6, 7, 4, 3, 2, 1]
```

---

#### Step 3: `reverse(k, nums.length - 1)`

**Flip the rest of the numbers (from index 3 to end)**

```js
Before: [5, 6, 7, 4, 3, 2, 1]  
After:  [5, 6, 7, 1, 2, 3, 4]
```

---

### 🎉 Final Result:

```
[5, 6, 7, 1, 2, 3, 4]
```

So, by flipping 3 times — whole, first part, and rest — you **magically rotated the array!** 🧙‍♂️🔄
