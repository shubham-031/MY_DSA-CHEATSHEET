## 1. Move Zeroes


```cpp


class Solution {
  public:
    vector <int> moveZeroes(vector<int>& nums) {

        int n = nums.size();
        int start =0;



        for (int i =0 ; i < n ; i++){
            if (nums[i] != 0){
                swap (nums[start], nums[i]);
                start =start+1;
            }
        }
      return nums;  
    }
};


```


## 2.Two Sum II

```cpp
class Solution {
public:
    vector<int> twoSum(vector<int>& numbers, int target) {
       int left = 0;
        int right = numbers.size() - 1;

        while (left < right) {
            int total = numbers[left] + numbers[right];

            if (total == target) {
                return {left + 1, right + 1};
            } else if (total > target) {
                right--;
            } else {
                left++;
            }
        }
        return {-1, -1}; // If no solution is found    
    }
};

```

## 3. 3Sum
```cpp
class Solution {
public:
    vector<vector<int>> threeSum(vector<int>& nums) {

        vector<vector<int>> ans;

        sort(nums.begin(), nums.end());

        for(int i = 0; i < nums.size(); i++)
        {
            // skip duplicate i
            if(i > 0 && nums[i] == nums[i - 1])
                continue;

            int left = i + 1;
            int right = nums.size() - 1;

            while(left < right)
            {
                int sum = nums[i] + nums[left] + nums[right];

                if(sum == 0)
                {
                    // save answer
                    ans.push_back({nums[i], nums[left], nums[right]});

                    left++;
                    right--;

                    // skip duplicate left
                    while(left < right &&
                          nums[left] == nums[left - 1])
                    {
                        left++;
                    }

                    // skip duplicate right
                    while(left < right &&
                          nums[right] == nums[right + 1])
                    {
                        right--;
                    }
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

        return ans;
    }
};

```
// continue म्हणजे सध्याची iteration skip करून loop ची पुढची iteration सुरू करणे.


// PATTERN:

// Sort + Fix One + Two Pointers

// Steps:

// 1. Sort array

// 2. Fix nums[i]

// 3. Find pair
//    with sum = -nums[i]

// 4. Use Two Pointers

// 5. Skip duplicates

// Time:
// O(n²)

// Space:
// O(1)


## 4. Sort Colors

```cpp

class Solution {
public:
    void sortColors(vector<int>& nums) {
        int low = 0;
        int mid = 0;
        int high = nums.size() - 1;

        while (mid <= high) {
            if (nums[mid] == 0) {
                swap(nums[low], nums[mid]);
                low++;
                mid++;
            } 
            else if (nums[mid] == 1) {
                mid++;
            } 
            else { // nums[mid] == 2
                swap(nums[mid], nums[high]);
                high--;
                // Don't increment mid here because swapped element may not be processed yet
            }
        }
    }
};

```

## 5. Container With Most Water
```cpp
class Solution {
public:
    int maxArea(vector<int>& height) {

        int l = 0;
        int r = height.size() - 1;

        int maxarea = 0;

        while(l < r) {

            int width = r - l;

            int h = min(height[l], height[r]);

            int area =  width * h;

            maxarea = max(maxarea, area);

            // छोटी height move करा
            if(height[l] < height[r])
                l++;
            else
                r--;
        }

        return maxarea;
    }
};

```

## 6. Trapping Rain Water

```cpp

class Solution {
public:
    int trap(vector<int>& height) {
        int left = 0;
        int right = height.size() - 1;

        int leftMax = 0;
        int rightMax = 0;
        int answer = 0;

        while (left < right) {
            leftMax = max(leftMax, height[left]);

            rightMax = max(rightMax, height[right]);

            if (leftMax < rightMax) {
                answer += leftMax - height[left];

                left++;
            } else {
                answer += rightMax - height[right];

                right--;
            }

        }
        return answer;
    }
};

```

### Sliding Window----II
-------------------
 ## 1.Maximum Sum of Distinct Subarrays With Length K

 ## PATTERN -- Fixed Size Sliding Window + Frequency Map
```cpp
class Solution {
public:
    long long maximumSubarraySum(vector<int>& nums, int k) {  // 1.ithe long long use kele ahe  sliding window madhe , karan ithe value return karaychi ahe ,
    // 2. two pointer madhe apan vector<vector <int>> vaprato karan apan array return kart asto....

        int n = nums.size();

        int left = 0;

        long long windowSum = 0;
        long long ans = 0;

        unordered_map<int,int> freq;

        for(int right = 0; right < n; right++)
        {
            // 1. Expand Window

            windowSum += nums[right];
            freq[nums[right]]++;



            // 2. Shrink Window

            while(right - left + 1 > k)
            {
                windowSum -= nums[left];  // step 1 --nums of left kami karne

                freq[nums[left]]--;   //step 2 -- nums of left chi frequency  kami karne

                if(freq[nums[left]] == 0)   //step 3-- nums of left chi frequency he zero  asel tar   te frequency erase karne....
                {
                    freq.erase(nums[left]);
                }

                left++;           // step 4-- left pointer pude pude sarkavne...
            }



            // 3. Process Answer

            if(right - left + 1 == k)  //window sum he equal asel k chya tar cha answer process hoil
            {
                // check Distinct Condition 

                if(freq.size() == k)
                {
                    ans = max(ans, windowSum);
                }
            }
        }

        return ans;
    }
};

```

## 2.  Max Consecutive Ones

```cpp
class Solution {
public:
    int findMaxConsecutiveOnes(vector<int>& nums) {

        int n = nums.size();

        int left = 0;
        int answer = 0;

        for (int right = 0; right < n; right++)
        {
            // 1. Expand Window
            // right automatically expands

            // 2. Shrink Window
            if(nums[right] == 0)
            {
                left = right + 1;
            }

            // 3. Update Answer
            answer = max(answer, right - left + 1);
        }

        return answer;
    }
};

```
## 3.Max Consecutive ones III

```cpp
class Solution {
public:
    int longestOnes(vector<int>& nums, int k) {
        int i = 0;
        int j = 0;
        int zerocount = 0;
        int ans = 0;

        for (int j = 0; j < nums.size(); j++) {
            if (nums[j] == 0) {
                zerocount = zerocount + 1;
            }

            // zerocount limit chya baher gele ki window shrink (choti) hoil...
            while (zerocount > k) {

                if (nums[i] == 0) {
                    zerocount = zerocount - 1;
                }

                i++;
            }

            ans = max(ans, j - i + 1);
        }
        return ans;
    }
};

```

## 4.Subarray Product Less Than K

## PATTERN --  Variable Size Sliding Window +  Count All Valid Subarrays

```cpp
class Solution {
public:
    int numSubarrayProductLessThanK(vector<int>& nums, int k) {
        if(k <= 1){
            return 0;
            }

        int n = nums.size();

        int left = 0;

        int product = 1;

        int ans = 0;
 

  for(int right = 0; right < n; right++){
            // 1. Expand Window

            product = product * nums[right];

            // 2. Shrink Window

            while(product >= k){
                product = product / nums[left];
                left++;
            }

            // 3. Count All Valid Subarrays

            ans =ans + (right - left + 1);

        }

        return ans;
    }
};

```


## 5.Fruits Into Baskets

## PATTERN --  Fruit Into Baskets = Longest Continuous Subarray   (length kadne) having at most 2 distinct numbers.

## At Most K Distinct Sliding Window
  
```cpp

class Solution {
public:
    int totalFruit(vector<int>& fruits) {

        int n = fruits.size();

        int left = 0;

        int ans = 0;

        unordered_map<int, int> freq; //{}

        for (int right = 0; right < n; right++) {

            // 1. Expand Window

            freq[fruits[right]]++; // 1

            // 2. Shrink Window

            while (freq.size() > 2) // condition check karne...
            {
                freq[fruits[left]]--;

                if (freq[fruits[left]] == 0) {
                    freq.erase(fruits[left]);
                }

                left++;
            }

            // 3. Update Answer

            ans = max(ans, right - left + 1);
        }

        return ans;
    }
};

```

## 6.Minimum Size Subarray Sum

## PATTERN

```cpp

class Solution {
public:
    int minSubArrayLen( int target,vector<int>& nums) {  
        int n = nums.size();

        int l = 0;

        int windowSum = 0;

        int ans = INT_MAX;

        for (int r = 0; r < n; r++) {
            // 1. Expand Window

            windowSum += nums[r];  //main point *********************

            // 2. Shrink Window

            while (windowSum >= target) {
                
                // Update Minimum Length

                ans = min(ans, r - l + 1);

                windowSum -= nums[l];

                l++;
            }
        }

        if (ans == INT_MAX) {

            return 0;

        }
        return ans;
    }
};
```

## 7.Sliding Window Maximum

## PATTERN -- MONOTONIC QUEUE (SLIDING WINDOW MAXIMUM)

```cpp
class Solution {
public:

    vector<int> maxSlidingWindow(vector<int>& nums, int k) {

        int n = nums.size();

        int left = 0;

        deque<int> dq;

        vector<int> ans;

        for(int right = 0; right < n; right++)
        {
            // 1. Remove Smaller Elements

            while(!dq.empty() &&
                  nums[dq.back()] <= nums[right])
            {
                dq.pop_back();
            }



            // 2. Add Current Index

            dq.push_back(right);



            // 3. Remove Expired Index

            if(dq.front() < left)   //check index , compare with (index of deque) < left ;
            {
                dq.pop_front();
            }



            // 4. Process Window

            if(right-left+1 == k)
            {
                ans.push_back(nums[dq.front()]);

                left++;
            }
      
        }

        return ans;
    }
};

```

## 8.Subarray with k distinct integers


## PATTERN --SLIDING WINDOW + EXACTLY K ELEMENTS

```cpp
class Solution {
public:

    int countAtMost(vector<int>& nums, int k)
    {
        int n = nums.size();

        int left = 0;

        int answer = 0;   

        unordered_map<int,int> freq;

        for(int right = 0; right < n; right++)
        {
            // 1. Expand Window

            freq[nums[right]]++;



            // 2. Shrink Window

            while(freq.size() > k)
            {
                freq[nums[left]]--;

                if(freq[nums[left]] == 0)
                {
                    freq.erase(nums[left]);
                }

                left++;
            }



            // 3. Count Valid Subarrays

            answer += (right - left + 1);
        }

        return answer;
    }

    int subarraysWithKDistinct(vector<int>& nums, int k) {

        // Exactly K = AtMost(K) - AtMost(K-1)

        return countAtMost(nums, k) - countAtMost(nums, k - 1);
    }
};

```


