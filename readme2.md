 #  🚀 TWO POINTER PROBLEMS
 📄 01_Move_Zeroes.md
## 🚀1. Move Zeroes

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

```cpp
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

```
📄 02_Two_Sum_II.md
# 🚀 2.Two Sum II

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
```cpp
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

```
📄 03_3Sum.md
# 3.🚀 3Sum

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


```cpp
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

```

# 4.🚀 Sort Colors

> **Pattern : Dutch National Flag (Three Pointer)**

---

## 🧠 Pattern

Question मध्ये खालील **Keywords** शोधा.

- **Sort Colors**
- **Only 0, 1, 2**
- **In-place**
- **One Pass**

**Pattern**

```text
Dutch National Flag

(Three Pointer)
```

---

## 💭 Question कसा विचार करायचा?

Question म्हणतो,

Array मध्ये फक्त **0, 1, 2** आहेत.

Sorting करायची आहे.

पण Extra Array वापरायचा नाही.

म्हणून तीन भाग तयार करा.

```text
0 चा भाग

↓

1 चा भाग

↓

Unknown भाग

↓

2 चा भाग
```

**Pointer Thinking**

```text
left

↓

0 ठेवायची जागा


mid

↓

Current Element Check करणार


right

↓

2 ठेवायची जागा
```

**Flow**

```text
nums[mid] == 0

↓

Swap(left, mid)

↓

left++

↓

mid++


--------------------


nums[mid] == 1

↓

mid++


--------------------


nums[mid] == 2

↓

Swap(mid, right)

↓

right--
```

---

## ⚡ Memory Trick

```text
0

↓

Left ला पाठवा


1

↓

Ignore


2

↓

Right ला पाठवा
```
📄 04_Sort_Colors.cpp
class Solution {
public:
    void sortColors(vector<int>& nums) {

        int left = 0;
        int mid = 0;
        int right = nums.size() - 1;

        while(mid <= right)
        {
            if(nums[mid] == 0)
            {
                swap(nums[left], nums[mid]);
                left++;
                mid++;
            }
            else if(nums[mid] == 1)
            {
                mid++;
            }
            else
            {
                swap(nums[mid], nums[right]);
                right--;
            }
        }
    }
};


📄 05_Container_With_Most_Water.md
# 🚀 Container With Most Water

> **Pattern : Two Pointer**

---

## 🧠 Pattern

Question मध्ये खालील **Keywords** शोधा.

- **Maximum Area**
- **Container**
- **Height**
- **Width**
- **Maximum Water**

**Pattern**

```text
Two Pointer
```

---

## 💭 Question कसा विचार करायचा?

Question म्हणतो,

दोन Lines निवडायच्या आहेत.

त्या दोन Lines मध्ये **जास्तीत जास्त पाणी (Maximum Area)** साठलं पाहिजे.

Area काढायचं Formula आहे.

```text
Area = Width × Minimum Height
```

सुरुवातीला,

- **left** = पहिली Line
- **right** = शेवटची Line

प्रत्येक Step ला,

Area काढा.

Maximum Answer Update करा.

आता विचार करा,

**कोणता Pointer Move करायचा?**

👉 मोठी Height Move करू नका.

कारण,

**Area ला नेहमी छोटी Height मर्यादित करते.**

म्हणून,

👉 **छोटी Height असलेला Pointer Move करा.**

---

### Pointer Thinking

```text
left

↓

डावीकडची Height


right

↓

उजवीकडची Height
```

---

### Flow

```text
Area = Width × Minimum Height

↓

Maximum Area Update करा

↓

nums[left] < nums[right]

↓

YES

↓

left++

↓

NO

↓

right--
```

---

## ⚡ Memory Trick

```text
Area

=

Width

×

Minimum Height

↓

Maximum Area Update करा

↓

नेहमी

छोटी Height Move करा

↓

मोठी Height तशीच ठेवा
```

### 🚀 One Line Trick

> **"Area ला नेहमी छोटी Height मर्यादित करते, म्हणून छोटी Height Move करा."**
📄 05_Container_With_Most_Water.cpp
class Solution {
public:
    int maxArea(vector<int>& height) {

        int left = 0;
        int right = height.size() - 1;

        int answer = 0;

        while(left < right)
        {
            int width = right - left;

            int currentArea = width * min(height[left], height[right]);

            answer = max(answer, currentArea);

            if(height[left] < height[right])
            {
                left++;
            }
            else
            {
                right--;
            }
        }

        return answer;
    }
};
