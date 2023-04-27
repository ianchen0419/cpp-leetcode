# cpp-leetcode

## Linked List

連結串列，由許多節點組成，在空間分配上比傳統陣列彈性，卻也需要多餘空間來儲存節點的指標位置。

一個節點最少需要以下兩個欄位：

* 節點的值
* 下一個節點的記憶體位置

```cpp
struct Node {
  int data; // 該節點的值
  Node* next; // 下一個節點的記憶體位置
}
```

由於串連的特性，因此：

* 需要再有一個獨立指標變數，儲存第一個節點的記憶體位置，稱作`pHead`，表頭指標
* 最後一個節點的`next`連結，會是一個`null`指標

練習：建立一個
```cpp
struct Node {
    int data;
    Node* next;
};

int main() {
    // 建立一個Node結構體對象
    Node node;
    node.data = 10;
    
    // 建立一個變數儲存第一個Node的指針
    Node *p = &node;
    
    // 使用解引用操作符訪問第一個Node
    cout << (*p).data << endl; // 10
    cout << p->data << endl; // 10
}
```
