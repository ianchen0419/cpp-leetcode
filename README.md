# cpp-leetcode

## Linked List

連結串列，由許多節點組成，在空間分配上比傳統陣列彈性，卻也需要多餘空間來儲存節點的指標位置。

一個節點最少需要以下兩個欄位：

* 節點的值
* 下一個節點的記憶體位置

```cpp
struct Node {
  int data; // 該節點的值
  Node *next; // 下一個節點的記憶體位置
}
```

由於串連的特性，因此：

* 需要再有一個獨立指標變數，儲存第一個節點的記憶體位置，稱作`pHead`，表頭指標
* 最後一個節點的`next`連結，會是一個`null`指標

練習：建立一個Node
```cpp
struct Node {
    int data;
    Node *next;
}

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

Linked List插入與印出

```cpp
struct Node {
    int data;
    Node *next;
};

// 在鏈表尾部插入一個新節點
void insert(Node **head_ref, int new_data) {
    Node *new_node = new Node();
    new_node->data = new_data;
    new_node->next = nullptr;
    
    if(*head_ref == nullptr) {
        *head_ref = new_node;
        return;
    }
    
    Node *last_node = *head_ref;
    while (last_node->next != nullptr) {
        last_node = last_node->next;
    }
    
    last_node->next = new_node;
}

// 遍歷鏈表並輸出每個節點的值
void print_list(Node *node) {
    while (node != nullptr) {
        cout << node->data << " ";
        node = node->next;
    }
}

int main() {
    // 創建一個空的鏈表
    Node *head = nullptr;
    
    // 在鏈表尾部插入幾個節點
    insert(&head, 1);
    insert(&head, 2);
    insert(&head, 3);
    insert(&head, 4);
    insert(&head, 5);
    
    // 遍歷鏈表並輸出每個節點的值
    cout << "Linked List: "; // Linked List: 1 2 3 4 5
    print_list(head);
}
```
