📄 01_Move_Zeroes.md
# 🚀 Move Zeroes

> **Pattern : Two Pointer**

---

## 🧠 Pattern

Question मध्ये खालील **Keywords** शोधा.

- **Move Zeroes**
- **Relative Order Maintain**
- **In-place**

**Pattern**

```text
Two Pointer
```

---

## 💭 Question कसा विचार करायचा?

Zero शेवटी पाठवायचे.

Non-Zero Elements चा **Order बदलायचा नाही.**

नवीन Array बनवायचा नाही.

**Pointer Thinking**

```text
left  → पुढचा Non-Zero ठेवायची जागा

right → पूर्ण Array Traverse करणार
```

**Flow**

```text
nums[right] != 0

↓

Swap(nums[left], nums[right])

↓

left++

↓

right++
```

---

## ⚡ Memory Trick

```text
Zero

↓

Ignore

↓

Non-Zero

↓

Swap

↓

left++

↓

right++
```
📄 01_Move_Zeroes.cpp
class Solution {
public:
    void moveZeroes(vector<int>& nums) {

        int left = 0;

        for(int right = 0; right < nums.size(); right++)
        {
            if(nums[right] != 0)
            {
                swap(nums[left], nums[right]);
                left++;
            }
        }
    }
};
📄 02_Two_Sum_II.md
# 🚀 Two Sum II

> **Pattern : Two Pointer**

---

## 🧠 Pattern

Question मध्ये खालील **Keywords** शोधा.

- **Sorted Array**
- **Pair**
- **Target Sum**

**Pattern**

```text
Two Pointer
```

---

## 💭 Question कसा विचार करायचा?

Array **Sorted** आहे.

म्हणून Binary Search नाही, **Two Pointer** वापरायचा.

**Flow**

```text
left + right

↓

Sum == Target

↓

Return

↓

Sum < Target

↓

left++

↓

Sum > Target

↓

right--
```

---

## ⚡ Memory Trick

```text
Sorted

↓

Two Pointer

↓

Small Sum

↓

left++

↓

Large Sum

↓

right--
```
📄 02_Two_Sum_II.cpp
class Solution {
public:
    vector<int> twoSum(vector<int>& numbers, int target) {

        int left = 0;
        int right = numbers.size() - 1;

        while(left < right)
        {
            int sum = numbers[left] + numbers[right];

            if(sum == target)
                return {left + 1, right + 1};

            else if(sum < target)
                left++;

            else
                right--;
        }

        return {};
    }
};
📄 03_3Sum.md
# 🚀 3Sum

> **Pattern : Sorting + Two Pointer**

---

## 🧠 Pattern

Question मध्ये खालील **Keywords** शोधा.

- **Triplet**
- **Sum = 0**
- **Unique Answer**

**Pattern**

```text
Sorting

+

Two Pointer
```

---

## 💭 Question कसा विचार करायचा?

सर्वप्रथम Array **Sort** करा.

एक Number **Fix** करा.

उरलेल्या दोन Numbers साठी **Two Pointer** वापरा.

Duplicate Triplets Skip करा.

**Flow**

```text
Sort

↓

Fix One Number

↓

left = i + 1

↓

right = n - 1

↓

Sum == 0

↓

Store Answer

↓

Duplicate Skip

↓

Sum < 0

↓

left++

↓

Sum > 0

↓

right--
```

---

## ⚡ Memory Trick

```text
Sort

↓

Fix One

↓

Two Pointer

↓

Store

↓

Duplicate Skip
```
📄 03_3Sum.cpp
class Solution {
public:
    vector<vector<int>> threeSum(vector<int>& nums) {

        sort(nums.begin(), nums.end());

        vector<vector<int>> answer;

        int n = nums.size();

        for(int i = 0; i < n; i++)
        {
            if(i > 0 && nums[i] == nums[i - 1])
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

                    while(left < right && nums[left] == nums[left - 1])
                        left++;

                    while(left < right && nums[right] == nums[right + 1])
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
