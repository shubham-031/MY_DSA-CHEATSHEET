## Move Zeroes


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


## Two Sum II

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

## 3Sum
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
