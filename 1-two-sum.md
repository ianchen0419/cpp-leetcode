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

## 哈希表

將`nums`的索引存起來，讓`result`減去`nums`的成員，檢查減去之後的數字是否存在哈希表內

時間複雜度: $O(n)$


### 知識筆記：`unordered_map`

1. 哈希表使用`unordered_map`儲存，不會儲存重複的value，需要引入標頭檔`<unordered_map>`
2. umap的寫入寫法：`umap[value] = index;`
3. umap的存取寫法：`umap[value]; // 回傳index`
4. umap中查詢是否存在：`umap.count(n);`，若存在返回`1`，反之返回`nil`

```cpp
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        vector<int> answer;
        
        // 將所有元素的索引存成哈希表，寫法為umap[value] = index
        unordered_map<int, int> indies;
        for(int i = 0; i < nums.size(); ++i) {
            indies[nums[i]] = i;
        }
        
        // 計算減去的值
        for(int i = 0; i < nums.size(); ++i) {
            int left = target - nums[i];
            // umap.count()，若存在返回1
            if (indies.count(left) && indies[left] != i) { // 因為每個元素只能被用一次，所以要排掉重復使用
                answer = {i, indies[left]};
            }
        }
        
        
        return answer;
    }
};
```

### Debug筆記

善用lldb的`po`指令印出資料，練習C++語法

練習使用umap建立資料

```cpp
unordered_map<int, int> hey;
hey[9] = 0;
hey[98] = 10;
hey[199] = 1;
```

在結尾處設定Breakpoint

![](https://user-images.githubusercontent.com/19959819/234313267-1257d46d-1f58-4afd-b779-dfeecd707f2f.png)

執行，並且在右下角的lldb視窗輸入以下：

* `po hey`，回傳size=3
* `po hey[98]`，回傳10
* `po hey.count(199)，回傳1
        
