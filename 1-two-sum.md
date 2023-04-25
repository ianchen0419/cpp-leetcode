## 題目概述

給定一組以下資料：

* 一串包含數字的vector `num`
* 整數 `target`

`num`當中會有2個成員相加等於`target`，找出那兩個成員的索引值

## 窮舉法

列舉出所有可能的組合，相加檢查是否等於`target`

時間複雜度: $n^2 \over 2$

```cpp
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        vector<int> answer;
        cout << __cplusplus << endl;

        for(int i = 0; i < nums.size(); ++i) {
            for(int j = i + 1; j < nums.size(); ++j) {
                // 因為限制住了邊界為nums.size()，因此j不會超出去
                // cout << i << endl;
                // cout << j << endl;
                // cout << "=======" << endl;
                
                int sum = nums[i] + nums[j];
                if (sum == target) {
                    answer = {i, j};
                }
            }
        }
        
        // 如果找不到的話，返回空vector
        return answer;
    }
};
```
