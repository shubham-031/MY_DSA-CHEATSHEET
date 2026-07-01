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
