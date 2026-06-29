# MY_DSA-CHEATSHEET

सर्वात आधी
int answer = INT_MAX;

याचा अर्थ:

answer मध्ये सर्वात मोठी possible integer value ठेवा.

म्हणजे:

answer = 2147483647

(32-bit int साठी)Step 1 : Question कसा वाचायचा?

Question मध्ये keywords शोध.

Subarray

Minimum Length

Sum >= Target

आता स्वतःला विचार.

Subarray आहे?

YES

Fixed Length दिली आहे?

NO

Condition आहे?

Sum >= target

Return काय?

Minimum Length

Brain मध्ये लगेच trigger
Universal Pattern
int left = 0;

for(int right = 0; right < n; right++)
{
    // 1. Expand Window

    add(nums[right]);



    // 2. Shrink Window

    while(window becomes valid)
    {
        update answer

        remove(nums[left]);

        left++;
    }
}




Golden Rule

हे तीन rules कायम लक्षात ठेव:

Count Subarrays
→ answer += windowSize

Longest / Maximum
→ answer = max(answer, windowSize)

Shortest / Minimum
→ answer = min(answer, windowSize)
````markdown
# MY_DSA-CHEATSHEET

# Variable Sliding Window

## सर्वात आधी

```cpp
int answer = INT_MAX;
```

याचा अर्थ:

`answer` मध्ये सर्वात मोठी possible integer value ठेवा.

म्हणजे:

```cpp
answer = 2147483647
```

(32-bit `int` साठी)

---

## Step 1 : Question कसा वाचायचा?

Question मध्ये keywords शोध.

```
Subarray

Minimum Length

Sum >= Target
```

आता स्वतःला विचार.

```
Subarray आहे?

YES

Fixed Length दिली आहे?

NO

Condition आहे?

Sum >= target

Return काय?

Minimum Length
```

---

## Brain मध्ये लगेच trigger

### Universal Pattern

```cpp
int left = 0;

for(int right = 0; right < n; right++)
{
    // 1. Expand Window

    add(nums[right]);



    // 2. Shrink Window

    while(window becomes valid)
    {
        update answer;

        remove(nums[left]);

        left++;
    }
}
```

---

## Golden Rule

हे तीन rules कायम लक्षात ठेव:

### Count Subarrays

```cpp
answer += windowSize;
```

### Longest / Maximum

```cpp
answer = max(answer, windowSize);
```

### Shortest / Minimum

```cpp
answer = min(answer, windowSize);
```
````




Variable Sliding Window


````markdown
# 🚀 Array - Two Pointer

---

# 01. Move Zeroes

**Pattern :** Two Pointer

---

## 🧠 Pattern

Question मध्ये Keywords शोध.

```
Move Zeroes

Relative Order Maintain

In-place
```

Pattern

```
Two Pointer
```

---

## 💭 Question कसा विचार करायचा?

```
Zero शेवटी पाठवायचे.

↓

Non-Zero Elements चा Order बदलायचा नाही.

↓

i → Next Non-Zero ठेवायची जागा

j → पूर्ण Array Traverse करणार
```

---

## 💻 C++ Solution

```cpp
class Solution {
public:
    void moveZeroes(vector<int>& nums) {

        int i = 0;

        for(int j = 0; j < nums.size(); j++)
        {
            if(nums[j] != 0)
            {
                swap(nums[i], nums[j]);
                i++;
            }
        }
    }
};
```

---

## ⚡ Memory Trick

```
Zero

↓

Ignore

↓

Non-Zero

↓

Swap

↓

i++

↓

j++
```

---

# 02. Two Sum II

**Pattern :** Two Pointer

---

## 🧠 Pattern

Question मध्ये Keywords शोध.

```
Sorted Array

Pair

Target Sum
```

Pattern

```
Two Pointer
```

---

## 💭 Question कसा विचार करायचा?

```
Array Sorted आहे.

↓

left + right

↓

Sum == Target

Return

↓

Sum < Target

left++

↓

Sum > Target

right--
```

---

## 💻 C++ Solution

```cpp
class Solution {
public:
    vector<int> twoSum(vector<int>& numbers, int target) {

        int left = 0;
        int right = numbers.size()-1;

        while(left < right)
        {
            int sum = numbers[left] + numbers[right];

            if(sum == target)
                return {left+1,right+1};

            else if(sum < target)
                left++;

            else
                right--;
        }

        return {};
    }
};
```

---

## ⚡ Memory Trick

```
Sorted

↓

Two Pointer

↓

Small Sum

left++

↓

Large Sum

right--
```

---

# 03. 3Sum

**Pattern :** Sorting + Two Pointer

---

## 🧠 Pattern

Question मध्ये Keywords शोध.

```
Triplet

Sum = 0

Unique Answer
```

Pattern

```
Sorting

+

Two Pointer
```

---

## 💭 Question कसा विचार करायचा?

```
Array Sort करा.

↓

एक Number Fix करा.

↓

बाकी दोन Numbers

Two Pointer ने शोधा.

↓

Duplicate Skip करा.
```

---

## 💻 C++ Solution

```cpp
class Solution {
public:
    vector<vector<int>> threeSum(vector<int>& nums) {

        sort(nums.begin(), nums.end());

        vector<vector<int>> answer;

        int n = nums.size();

        for(int i = 0; i < n; i++)
        {
            if(i > 0 && nums[i] == nums[i-1])
                continue;

            int left = i + 1;
            int right = n - 1;

            while(left < right)
            {
                int sum = nums[i] + nums[left] + nums[right];

                if(sum == 0)
                {
                    answer.push_back({nums[i], nums[left], nums[right]});

                    left++;
                    right--;

                    while(left < right && nums[left] == nums[left-1])
                        left++;

                    while(left < right && nums[right] == nums[right+1])
                        right--;
                }
                else if(sum < 0)
                {
                    left++;
                }
                else
                {
                    right--;
                }
            }
        }

        return answer;
    }
};
```

---

## ⚡ Memory Trick

```
Sort

↓

Fix One

↓

Two Pointer

↓

Duplicate Skip
```
````


