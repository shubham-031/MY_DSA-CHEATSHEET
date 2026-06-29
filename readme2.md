 #  🚀 TWO POINTER PROBLEMS
 📄 01_Move_Zeroes.md
## 🚀1. Move Zeroes --- [1]

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
# 🚀 2.Two Sum II ---[2]

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
# 3.🚀 3Sum --- [3]

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

# 4.🚀 Sort Colors --- [4]

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

```cpp
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
```

📄 05_Container_With_Most_Water.md
# 🚀5. Container With Most Water --- [5]

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

```cpp
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

```
 #  🚀 TYPE II -- SLIDING WINDOW PROBLEMS
📄 01_Maximum_Sum_Subarray_of_Size_K.md
🚀1. Maximum Sum Subarray of Size K --- [6]
```
Pattern : Fixed Size Sliding Window
```
🧠 Pattern

Question मध्ये खालील Keywords शोधा.

Maximum Sum
Size K
Consecutive
Subarray

```
👉 Window Size नेहमी K असते.

💭 Question कसा विचार करायचा?

Window मध्ये Elements Add करत जा.

Window Size K झाली की

Answer Update करा.
Left Element Remove करा.
Window Slide करा.

```
👀 Visualization

```text
nums = [2 1 5 1 3 2]
k = 3

L
R

2 1 5

Sum = 8

↓

Slide

2 1 5 1
↑     ↑
L     R

Remove 2

Window

1 5 1

Sum = 7

↓

Slide

5 1 3

Sum = 9

Maximum = 9
```
🚀 Flow


```
Add nums[right]

↓

Window Size == K ?

↓

YES

↓

Update Maximum Sum

↓

Remove nums[left]

↓

left++
```
💻 C++ Code

```CPP
class Solution {
public:
    int maximumSumSubarray(vector<int>& nums, int k) {

        int left = 0;
        int sum = 0;
        int answer = INT_MIN;

        for(int right = 0; right < nums.size(); right++)
        {
            // 1. Expand Window

            sum += nums[right];

            // 2. Window Full

            if(right - left + 1 == k)
            {
                // 3. Process Answer

                answer = max(answer, sum);

                // 4. Slide Window

                sum -= nums[left];
                left++;
            }
        }

        return answer;
    }
};

```
⚡ Memory Trick

```
Add

↓

Window Full

↓

Update Answer

↓

Remove Left

↓

Repeat

```
🚀 One Line Trick
``` text
"Window Full झाली की Answer Update करा आणि Window Slide करा."
```text
```
📄 02_Max_Consecutive_Ones.md  
🚀 2. Max Consecutive Ones --- [7]
```
Pattern : Variable Size Sliding Window
```
🧠 Pattern
```
Question मध्ये खालील Keywords शोधा.

Consecutive
Longest
Maximum Length
At Most K Zeroes
Flip

```
💭 Question कसा विचार करायचा?
```
Window Expand करा.

Zero Count वाढत जाईल.

जर Zero Count > K

तर

Left Move करून Window Shrink करा.

प्रत्येक Valid Window ला

Maximum Length Update करा.
```
👀 Visualization

```
nums

1 1 0 1 1 1 0 1

L
R

↓

Zero = 0

↓

Expand

1 1 0 1

Zero = 1

↓

Expand

1 1 0 1 1 1

↓

Zero > K ?

↓

YES

↓

Move Left

↓

Window Valid

↓

Update Length

```
🚀 Flow

```
Expand Window

↓

Add Current Element

↓

Zero Count > K ?

↓

YES

↓

Shrink Window

↓

NO

↓

Update Maximum Length

```
💻 C++ Code (Max Consecutive Ones III)

```
class Solution {
public:
    int longestOnes(vector<int>& nums, int k) {

        int left = 0;
        int zeroCount = 0;
        int answer = 0;

        for(int right = 0; right < nums.size(); right++)
        {
            // 1. Expand Window

            if(nums[right] == 0)
            {
                zeroCount++;
            }

            // 2. Shrink Window

            while(zeroCount > k)
            {
                if(nums[left] == 0)
                {
                    zeroCount--;
                }

                left++;
            }

            // 3. Process Answer

            answer = max(answer, right - left + 1);
        }

        return answer;
    }
};

```
⚡ Memory Trick

```
Expand

↓

Zero Count

↓

Too Many Zeroes?

↓

Shrink

↓

Update Length

🚀 One Line Trick

"Condition Break झाली की Left Move करा, Condition Valid झाली की Maximum Length Update करा


# 📄 03_Max_Consecutive_Ones_III.md

# 🚀 Max Consecutive Ones III

> **Pattern : Variable Size Sliding Window**

---

# 🧠 Pattern (Keywords)

Question मध्ये खालील **Keywords** शोधा.

* Longest Subarray
* Consecutive Ones
* Flip 0 → 1
* At Most K Zeroes
* Maximum Length

### 👉 Pattern

Variable Size Sliding Window

---

# 💭 Question कसा विचार करायचा?

आपल्याला सलग (Consecutive) जास्तीत जास्त 1's पाहिजेत.

पण...

आपण **जास्तीत जास्त K Zero Flip** करू शकतो.

म्हणून,

Window Expand करत जा.

जर Window मध्ये

**Zero Count > K**

झाला

तर

Window Invalid झाली.

आता

Left Move करून

Zero Count कमी करा.

पुन्हा Window Valid झाली की

Maximum Length Update करा.

---

# 👀 Visualization

```
nums

1 1 1 0 0 0 1 1 1 1 0

L
R

↓

Window = [1]

Zero = 0

↓

Expand

1 1 1

↓

Expand

1 1 1 0

Zero = 1

↓

Expand

1 1 1 0 0

Zero = 2

↓

Expand

1 1 1 0 0 0

Zero = 3

↓

Zero > K ?

YES

↓

Move Left

↓

Window Valid

↓

Update Answer
```

---

# 📝 Dry Run

Example

```
nums = [1,1,1,0,0,0,1,1]
k = 2

left = 0

right = 0

Window

[1]

Zero = 0

Answer = 1

↓

right++

[1 1]

Answer = 2

↓

right++

[1 1 1]

Answer = 3

↓

right++

[1 1 1 0]

Zero = 1

Answer = 4

↓

right++

[1 1 1 0 0]

Zero = 2

Answer = 5

↓

right++

[1 1 1 0 0 0]

Zero = 3

INVALID

↓

Move Left

↓

Window Valid

↓

Continue...
```

---

# 🧠 Pointer Thinking

```
Left

↓

Remove Old Element

-------------------------

Right

↓

Add New Element
```

Remember

```
Right

Expand

↓

Left

Shrink

↓

Answer
```

---

# 🚀 Step by Step Algorithm

```
Step 1

left = 0

↓

Step 2

Move Right

↓

Step 3

If nums[right]==0

Zero++

↓

Step 4

Zero > K ?

↓

YES

↓

Move Left

↓

If nums[left]==0

Zero--

↓

Step 5

Answer = max(answer, windowSize)
```

---

# 💻 Pattern Template

```cpp
int left = 0;

for(int right = 0; right < n; right++)
{
    // Expand Window

    // Update Current State

    while(condition_break)
    {
        // Shrink Window

        left++;
    }

    // Update Answer
}
```

---

# 💻 Final C++ Code

```cpp
class Solution {
public:
    int longestOnes(vector<int>& nums, int k) {

        int left = 0;
        int zeroCount = 0;
        int answer = 0;

        for(int right = 0; right < nums.size(); right++)
        {
            // 1. Expand Window

            if(nums[right] == 0)
            {
                zeroCount++;
            }

            // 2. Shrink Window

            while(zeroCount > k)
            {
                if(nums[left] == 0)
                {
                    zeroCount--;
                }

                left++;
            }

            // 3. Update Answer

            answer = max(answer, right - left + 1);
        }

        return answer;
    }
};
```

---

# ⚡ Time & Space Complexity

```
Time  : O(n)

Space : O(1)
```

---

# ⚡ Memory Trick

```
Expand

↓

Zero Count

↓

Too Many Zeroes?

↓

YES

↓

Shrink

↓

Answer
```

---

# 🚀 One Line Trick

> **"Zero Count K पेक्षा जास्त झाला की Left Move करा, अन्यथा Window Length Update करा."**

---

# 🎯 Similar Problems

* Maximum Consecutive Ones
* Longest Repeating Character Replacement
* Max Consecutive Ones III
* Longest Substring with At Most K Distinct Characters
* Fruit Into Baskets
```
# 📄 04_Subarray_Product_Less_Than_K.md

# 🚀 Subarray Product Less Than K

> **Pattern : Variable Size Sliding Window**

---

# 🧠 Pattern (Keywords)

Question मध्ये खालील **Keywords** शोधा.

* Subarray
* Product
* Less Than K
* Count
* Continuous / Consecutive

### 👉 Pattern

**Variable Size Sliding Window**

---

# 💭 Question कसा विचार करायचा?

या Question मध्ये **Maximum / Minimum** शोधायचं नाही.

आपल्याला **Count** शोधायचा आहे.

Question म्हणतो,

**Product < K** असलेले सर्व Subarrays Count करा.

---

### 🤔 Important Observation

जर

```text
Window Product < K
```

असेल

तर

त्या Window मध्ये **right वर संपणारे सर्व Subarrays** पण Valid असतात.

उदा.

```text
L         R

2 5 3

Product = 30
```

Valid Window आहे.

मग खालील सर्व Valid आहेत.

```text
[2 5 3]

[5 3]

[3]
```

म्हणजे

```text
Count = Window Size
```

यामुळे प्रत्येक वेळेस

```cpp
answer += windowSize;
```

हे करतो.

हीच या Problem ची Main Trick आहे.

---

# 👀 Visualization

Example

```text
nums = [10 5 2 6]

k = 100


L
R

10

Product = 10

Window Size = 1

Answer += 1

----------------------------

10 5

Product = 50

Window Size = 2

Answer += 2

Subarrays

[10 5]

[5]

----------------------------

10 5 2

Product = 100

INVALID

↓

Shrink

----------------------------

5 2

Product = 10

Window Size = 2

Answer += 2

Subarrays

[5 2]

[2]
```

---

# 📝 Dry Run

```text
nums = [10,5,2,6]

k = 100


Initially

Product = 1

Answer = 0

--------------------------------

Add 10

Product = 10

Window = [10]

Answer +=1

Answer = 1

--------------------------------

Add 5

Product = 50

Window = [10 5]

Answer +=2

Answer = 3

--------------------------------

Add 2

Product =100

INVALID

Remove 10

Product =10

Window = [5 2]

Answer +=2

Answer =5

--------------------------------

Add 6

Product =60

Window = [5 2 6]

Answer +=3

Answer =8
```

Final Answer

```text
8
```

---

# 🧠 Pointer Thinking

```text
left

↓

Remove Product

----------------------

right

↓

Multiply Product
```

Remember

```text
Right

↓

Multiply

↓

Product >= K ?

↓

YES

↓

Left Divide

↓

Valid Window

↓

Count Window Size
```

---

# 🚀 Step by Step Algorithm

```text
Step 1

left = 0

product = 1

answer = 0

↓

Step 2

Multiply nums[right]

↓

Step 3

Product >= K ?

↓

YES

↓

Divide nums[left]

↓

left++

↓

Repeat

↓

Step 4

Window Valid

↓

answer += windowSize
```

---

# 💻 Pattern Template

```cpp
int left = 0;

for(int right = 0; right < n; right++)
{
    // Expand Window

    // Update Product

    while(product >= k)
    {
        // Shrink Window

        left++;
    }

    // Count Current Window
}
```

---

# 💻 Final C++ Code

```cpp
class Solution {
public:
    int numSubarrayProductLessThanK(vector<int>& nums, int k) {

        if(k <= 1)
        {
            return 0;
        }

        int left = 0;
        int answer = 0;

        long long product = 1;

        for(int right = 0; right < nums.size(); right++)
        {
            // 1. Expand Window

            product *= nums[right];

            // 2. Shrink Window

            while(product >= k)
            {
                product /= nums[left];
                left++;
            }

            // 3. Count Valid Subarrays

            answer += (right - left + 1);
        }

        return answer;
    }
};
```

---

# ⚡ Time & Space Complexity

```text
Time  : O(n)

Space : O(1)
```

---

# ⚡ Memory Trick

```text
Multiply

↓

Product >= K ?

↓

YES

↓

Divide

↓

Window Valid

↓

Add Window Size
```

---

# 🚀 One Line Trick

> **"Window Valid झाली की `windowSize` इतके नवीन Subarrays मिळतात."**

---

# 🔥 Most Important Trick ⭐⭐⭐⭐⭐

Normal Sliding Window मध्ये आपण

```cpp
answer = max(answer, windowSize);
```

करतो.

पण या Question मध्ये

```cpp
answer += (right - left + 1);
```

का?

कारण

Current Window Valid असेल तर

```text
L           R

2 5 3
```

हे सर्व नवीन Subarrays Valid असतात.

```text
[2 5 3]

[5 3]

[3]
```

म्हणून

```text
Count = Window Size
```

हा Rule या Problem चा **Golden Rule** आहे.

---

# 🎯 Similar Problems

* Binary Subarrays With Sum
* Count Number of Nice Subarrays
* Number of Substrings Containing All Three Characters
* Count Vowel Substrings
* Count Complete Subarrays

```



