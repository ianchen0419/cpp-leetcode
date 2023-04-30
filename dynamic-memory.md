# Dynamic Memory

在運作程式時，電腦的記憶體分為四個部分：

* Code (Text)：程式碼文本
* Static/Global：Static Variable與Global Variable
* Stack：Function Calls與Local Variable
* Heap

這4個部分中，除了Heap以外的其他3個，都不會在程式運作時增長

## 範例解說


```c
int total;

int Square(int x) {
 return x*x;
}

int SquareOfSum(int x, int y) {
  int z = Square(x+y);
  return z;
}

int main {
  int a = 4;
  int b = 8;
  
  total = SquareOfSum(a, b);
  
  printf("output = %d", total);

  return 0;
}
```

### 1. 調用`main()`

```diff c
int total;

int Square(int x) {
 return x*x;
}

int SquareOfSum(int x, int y) {
  int z = Square(x+y);
  return z;
}

+int main {
  int a = 4;
  int b = 8;
  
  total = SquareOfSum(a, b);
  
  printf("output = %d", total);

  return 0;
}
```

C++程式的第一步會調用`main()`，在Stack區塊建立一個名為`main()`的堆疊禎（Stack Frame），並且，該堆疊禎會儲存此函數的所有參數以及返回值

```mermaid
flowchart
    subgraph Stack
    a1["main()\na, b"]
    end
```

### 2. 建立全域變數`total`

```diff c
int total;

int Square(int x) {
 return x*x;
}

int SquareOfSum(int x, int y) {
  int z = Square(x+y);
  return z;
}

int main {
  int a = 4;
  int b = 8;
  
+ total = SquareOfSum(a, b);
  
  printf("output = %d", total);

  return 0;
}
```

接下來，在Global/Static區塊，畫出一塊位置，建立全域變數`total`


```mermaid
flowchart
    subgraph Stack
    a1["main()\na, b"]
    end

    subgraph Global/Static
    b1[total]
    end
```

### 3.調用`SquareOfSum()`

```diff c
int total;

int Square(int x) {
 return x*x;
}

+int SquareOfSum(int x, int y) {
  int z = Square(x+y);
  return z;
}

int main {
  int a = 4;
  int b = 8;
  
  total = SquareOfSum(a, b);
  
  printf("output = %d", total);

  return 0;
}
```

由於前一行`total = SquareOfSum(a, b);`，呼叫了`SquareOfSum()`函數，因此，在Stack區塊，推入`SquareOfSum()`的堆疊禎，儲存`SquareOfSum()`的所有參數、區域變數、回傳值：`x`, `y`, `z`

```mermaid
flowchart
    subgraph Stack
    a2["SquareOfSum()\nx, y, z"]
    a1["main()\na, b"]
    end

    subgraph Global/Static
    b1[total]
    end
```

### 4. 調用`Square()`

因為`int z = Square(x+y);`呼叫了`Square()`函數，在Stack區塊，推入`Square()`的堆疊禎，並且儲存參數`x`


```diff c
int total;

+int Square(int x) {
 return x*x;
}

int SquareOfSum(int x, int y) {
  int z = Square(x+y);
  return z;
}

int main {
  int a = 4;
  int b = 8;
  
  total = SquareOfSum(a, b);
  
  printf("output = %d", total);

  return 0;
}
```

```mermaid
flowchart
    subgraph Stack
    a3["Square()\nx"]
    a2["SquareOfSum()\nx, y, z"]
    a1["main()\na, b"]
    end

    subgraph Global/Static
    b1[total]
    end
```

### 5. 決定Stack列表上的執行順序

現在，Stack上面一共用3組堆疊禎，電腦不會同時執行這3組，而是先暫停底下2組，優先執行最上面那組，因此，執行順序如下所示：

`main()`暫停、`SquareOfSum()`暫停、執行`Square()`

```mermaid
flowchart
    subgraph Stack
    a3["Square()\nx"]
    a2["SquareOfSum()\nx, y, z"]:::disabled
    a1["main()\na, b"]:::disabled
    end

    subgraph Global/Static
    b1[total]
    end
    
    classDef disabled fill:#ccc,stroke:#ccc,color:#fff
```
    
`Square()`計算完畢，Stack清除`Square()`堆疊禎

```mermaid
flowchart
    subgraph Stack
    a2["SquareOfSum()\nx, y, z"]:::disabled
    a1["main()\na, b"]:::disabled
    end

    subgraph Global/Static
    b1[total]
    end
    
    classDef disabled fill:#ccc,stroke:#ccc,color:#fff
```

`SquareOfSum()`復活，執行`SquareOfSum()`

```mermaid
flowchart
    subgraph Stack
    a2["SquareOfSum()\nx, y, z"]
    a1["main()\na, b"]:::disabled
    end

    subgraph Global/Static
    b1[total]
    end
    
    classDef disabled fill:#ccc,stroke:#ccc,color:#fff
```

`Square()`計算完畢，Stack清除`Square()`堆疊禎

```mermaid
flowchart
    subgraph Stack
    a1["main()\na, b"]:::disabled
    end

    subgraph Global/Static
    b1[total]
    end
    
    classDef disabled fill:#ccc,stroke:#ccc,color:#fff
```

`main()`復活，繼續執行`main()`

```mermaid
flowchart
    subgraph Stack
    a1["main()\na, b"]
    end

    subgraph Global/Static
    b1[total]
    end
    
    classDef disabled fill:#ccc,stroke:#ccc,color:#fff
```

### 6. 執行`printf()`

程式回到了`main()`繼續往下執行剩下的部分

```diff c
int total;

int Square(int x) {
 return x*x;
}

int SquareOfSum(int x, int y) {
  int z = Square(x+y);
  return z;
}

int main {
  int a = 4;
  int b = 8;
  
  total = SquareOfSum(a, b);
  
+ printf("output = %d", total);

  return 0;
}
```

因為遇到了新的函示，因此往Stack放入堆疊禎`printf()`，暫停運作`main()`，`執行printf()`

```mermaid
flowchart
    subgraph Stack
    a4["printf()"]
    a1["main()\na, b"]:::disabled
    end

    subgraph Global/Static
    b1[total]
    end
    
    classDef disabled fill:#ccc,stroke:#ccc,color:#fff
```

當`printf()`執行完畢後，Stack刪除`printf()`，並且讓`main()`恢復

```mermaid
flowchart
    subgraph Stack
    a1["main()\na, b"]
    end

    subgraph Global/Static
    b1[total]
    end
```


### 7. 結束

最後，`main()`執行完畢，Stack清除`main()`

```mermaid
flowchart
    subgraph Stack
    a0["  "]
    end

    subgraph Global/Static
    b1[total]
    end
```

C++結束程式，將Global/Static當中儲存的Global變數`total`清空，Stack跟Global/Static都淨空了

```mermaid
flowchart
    subgraph Stack
    a0["  "]
    end

    subgraph Global/Static
    b0["  "]
    end
  
```

## 堆疊溢出 StackOverflow

當電腦一開始執行程式時，會預留一些空間給Stack做使用（例如：1mb），但是，假如程式當中出現了無限遞迴呼叫，`A()`調用`B()`、`B()`調用`C()`、`C()`調用`D()`

```mermaid
flowchart
    subgraph Stack
    a3["C()"]-->a4["D()"]
    a2["B()"]-->a3["C()"]
    a1["A()"]-->a2["B()"]
    a0["main()"]-->a1["A()"]
    end
```

最開始規劃的1mb會被用完，程式會壞掉，這就是堆疊溢出
