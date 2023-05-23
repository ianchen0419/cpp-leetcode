# Bubble Sorting

每輪評選選出最大的那個Bubble（透過比較鄰近元素），之後將其剔除，在執行評選選出最大的，剔除，重複執行到剩下一個（最小的）

泡泡比較的概念：兩兩比較鄰近元素，小的那方下沉到馬里雅納海溝，大的那方浮起來，繼續跟右邊兩兩比較

假設有一組數列`18`、`2`、`20`、`34`、`12`，實作泡泡排序：

首先開始第一輪排序

```mermaid
flowchart

    subgraph 海溝區
        f(( )):::clear
    end
    
    a((18))
    b((2))
    c((20))
    d((34))
    e((12))
    
    classDef clear opacity:0
```

首先，比較`18`跟`2`

```mermaid
flowchart

    subgraph 海溝區
        f(( )):::clear
    end
    
    a((18)):::green
    b((2)):::green
    c((20))
    d((34))
    e((12))
    
    classDef clear opacity:0
    classDef green fill:#ecffec
```

`2`比較小，因此他被扔入了海溝（Sink Down）

```mermaid
flowchart

    subgraph 海溝區
        f((2)):::disabled
    end
    
    a((18)):::green
    b((2)):::clear
    c((20))
    d((34))
    e((12))
    
    classDef clear opacity:0
    
    classDef orange fill:#f96,stroke:#f66
    classDef green fill:#ecffec
    classDef disabled fill:#ccc,stroke:#fff,color:#fff
```

接著，比較`18`與`20`

```mermaid
flowchart

    subgraph 海溝區
        f((2)):::disabled
    end
    
    a((18)):::green
    b((2)):::clear
    c((20)):::green
    d((34))
    e((12))
    
    classDef clear opacity:0
    
    classDef orange fill:#f96,stroke:#f66
    classDef green fill:#ecffec
    classDef disabled fill:#ccc,stroke:#fff,color:#fff
```

`18`比較小，因此`18`被扔進海溝

```mermaid
flowchart

    subgraph 海溝區
        f((2)):::disabled
        g((18)):::disabled
    end
    
    a((18)):::clear
    b((2)):::clear
    c((20)):::green
    d((34))
    e((12))
    
    classDef clear opacity:0
    
    classDef orange fill:#f96,stroke:#f66
    classDef green fill:#ecffec
    classDef disabled fill:#ccc,stroke:#fff,color:#fff
```

繼續比較`20`與`34`

```mermaid
flowchart

    subgraph 海溝區
        f((2)):::disabled
        g((18)):::disabled
    end
    
    a((18)):::clear
    b((2)):::clear
    c((20)):::green
    d((34)):::green
    e((12))
    
    classDef clear opacity:0
    
    classDef orange fill:#f96,stroke:#f66
    classDef green fill:#ecffec
    classDef disabled fill:#ccc,stroke:#fff,color:#fff
```

`20`比較小，`20`被丟掉

```mermaid
flowchart

    subgraph 海溝區
        f((2)):::disabled
        g((18)):::disabled
        h((20)):::disabled
    end
    
    a((18)):::clear
    b((2)):::clear
    c((20)):::clear
    d((34)):::green
    e((12))
    
    classDef clear opacity:0
    
    classDef orange fill:#f96,stroke:#f66
    classDef green fill:#ecffec
    classDef disabled fill:#ccc,stroke:#fff,color:#fff
```

再比較`34`跟`12`

```mermaid
flowchart

    subgraph 海溝區
        f((2)):::disabled
        g((18)):::disabled
        h((20)):::disabled
    end
    
    a((18)):::clear
    b((2)):::clear
    c((20)):::clear
    d((34)):::green
    e((12)):::green
    
    classDef clear opacity:0
    
    classDef orange fill:#f96,stroke:#f66
    classDef green fill:#ecffec
    classDef disabled fill:#ccc,stroke:#fff,color:#fff
```

`12`被丟掉，`34`成為贏家，浮出水面

```mermaid
flowchart

    subgraph 海溝區
        f((2)):::disabled
        g((18)):::disabled
        h((20)):::disabled
        i((12)):::disabled
    end
    
    a((18)):::clear
    b((2)):::clear
    c((20)):::clear
    d((34)):::popup
    e((12)):::clear
    
    classDef clear opacity:0
    
    classDef orange fill:#f96,stroke:#f66
    classDef green fill:#ecffec
    classDef disabled fill:#ccc,stroke:#fff,color:#fff
    classDef popup fill:#f96,stroke:#f66,stroke-width:2px,color:#fff,stroke-dasharray: 5 5
```

第一輪評選結果是`34`，`34`因為到陸地上了，
