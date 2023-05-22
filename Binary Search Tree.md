# Binary Search Tree 二元搜尋樹

```mermaid
flowchart TB
    r((70))---a1
    a1((60))---a2((50))
    a1---a3((65))
    r---b1
    b1((80))---b2((85))
    b1---b3(( )):::clear
    
    linkStyle 5 opacity:0
    classDef clear opacity:0
```

規則：左小右大
* 左子樹的所有鍵值都小於樹根
* 右子樹的所有鍵值都大於樹根
* 左子樹也是BST、右子樹也是BST
* 每個鍵值都不一樣

## 二元搜尋樹的新增

有一BST如下，欲加入48
```mermaid
flowchart TB
    r---a1
    a1---a2
    a1---a3
    r---b1
    b1---b2
    b1---b3

    r((50))

    a1((40))
    a2((30))
    a3((45))

    b1((65))
    b2((60))
    b3(( )):::clear
    
    linkStyle 5 opacity:0
    classDef orange fill:#f96,stroke:#f66
    classDef green fill:#ecffec
    classDef clear opacity:0
```

首先檢查樹根，判斷插入節點`48`小於樹根的`50`，因此往樹根左側走


```mermaid
flowchart TB
    r:::green---a1
    a1---a2
    a1---a3
    r---b1
    b1---b2
    b1---b3

    r((50))

    a1((40))
    a2((30))
    a3((45))

    b1((65))
    b2((60))
    b3(( )):::clear
    
    linkStyle 0 stroke:#f96,stroke-width:4px 
    linkStyle 5 opacity:0
    classDef orange fill:#f96,stroke:#f66
    classDef green fill:#ecffec
    classDef clear opacity:0
```

接著，抵達樹根正左方的`40`，因為插入節點`48`大於`40`，因此往`40`右邊走

```mermaid
flowchart TB
    r---a1:::green
    a1---a2
    a1---a3
    r---b1
    b1---b2
    b1---b3

    r((50))

    a1((40))
    a2((30))
    a3((45))

    b1((65))
    b2((60))
    b3(( )):::clear
    
    linkStyle 2 stroke:#f96,stroke-width:4px 
    linkStyle 5 opacity:0
    classDef orange fill:#f96,stroke:#f66
    classDef green fill:#ecffec
    classDef clear opacity:0
```

抵達末端節點`45`，插入節點`48`大於`45`，因此在末端節點`45`的右邊設立新節點`48`

```mermaid
flowchart TB
    r---a1
    a1---a2
    a1---a3:::green
    a3---a4
    a3---a5
    r---b1
    b1---b2
    b1---b3

    r((50))

    a1((40))
    a2((30))
    a3((45))

    b1((65))
    b2((60))
    b3(( )):::clear
    a4(( )):::clear
    a5((48))
    
    linkStyle 4 stroke:#f96,stroke-width:4px 
    linkStyle 7 opacity:0
    linkStyle 3 opacity:0
    classDef orange fill:#f96,stroke:#f66
    classDef green fill:#ecffec
    classDef clear opacity:0
    style a5 fill:#bbf,stroke:#f66,stroke-width:2px,color:#fff,stroke-dasharray: 5 5
```

## 二元搜尋樹的搜尋

假設有一BST如下，欲搜尋「55」這一節點

```mermaid
flowchart TB
    r---a1
    a1---a2
    a1---a3
    a3---a4
    a3---a5
    r---b1
    b1---b2
    b1---b3
    b3---b4
    b3---b5
    b5---b6
    b5---b7

    r((40))

    a1((20))
    a2(( )):::clear
    a3((30))
    a4((28))
    a5((35))

    b1((50))
    b2(( )):::clear
    b3((70))
    b4((55))
    b5((85))
    b6((72))
    b7(( )):::clear
    
    linkStyle 1 opacity:0
    linkStyle 6 opacity:0
    linkStyle 11 opacity:0
    classDef orange fill:#f96,stroke:#f66
    classDef green fill:#ecffec
    classDef clear opacity:0
```

首先，檢查樹根40，搜尋目標55大於40，因此往右走

```mermaid
flowchart TB
    r:::green---a1
    a1---a2
    a1---a3
    a3---a4
    a3---a5
    r---b1
    b1---b2
    b1---b3
    b3---b4
    b3---b5
    b5---b6
    b5---b7

    r((40))

    a1((20))
    a2(( )):::clear
    a3((30))
    a4((28))
    a5((35))

    b1((50))
    b2(( )):::clear
    b3((70))
    b4((55))
    b5((85))
    b6((72))
    b7(( )):::clear
    
    linkStyle 5 stroke:#f96,stroke-width:4px 
    linkStyle 1 opacity:0
    linkStyle 6 opacity:0
    linkStyle 11 opacity:0
    classDef orange fill:#f96,stroke:#f66
    classDef green fill:#ecffec
    classDef clear opacity:0
```

往下檢查「50」，目標55大於50，繼續往右

```mermaid
flowchart TB
    r---a1
    a1---a2
    a1---a3
    a3---a4
    a3---a5
    r---b1:::green
    b1---b2
    b1---b3
    b3---b4
    b3---b5
    b5---b6
    b5---b7

    r((40))

    a1((20))
    a2(( )):::clear
    a3((30))
    a4((28))
    a5((35))

    b1((50))
    b2(( )):::clear
    b3((70))
    b4((55))
    b5((85))
    b6((72))
    b7(( )):::clear
    
    linkStyle 7 stroke:#f96,stroke-width:4px 
    linkStyle 1 opacity:0
    linkStyle 6 opacity:0
    linkStyle 11 opacity:0
    classDef orange fill:#f96,stroke:#f66
    classDef green fill:#ecffec
    classDef clear opacity:0
```

往下檢查「70」目標55小於70，往左


```mermaid
flowchart TB
    r---a1
    a1---a2
    a1---a3
    a3---a4
    a3---a5
    r---b1
    b1---b2
    b1---b3:::green
    b3---b4
    b3---b5
    b5---b6
    b5---b7

    r((40))

    a1((20))
    a2(( )):::clear
    a3((30))
    a4((28))
    a5((35))

    b1((50))
    b2(( )):::clear
    b3((70))
    b4((55))
    b5((85))
    b6((72))
    b7(( )):::clear
    
    linkStyle 8 stroke:#f96,stroke-width:4px 
    linkStyle 1 opacity:0
    linkStyle 6 opacity:0
    linkStyle 11 opacity:0
    classDef orange fill:#f96,stroke:#f66
    classDef green fill:#ecffec
    classDef clear opacity:0
```

繼續往下，找到節點「55」，目標55與該節點相等，找到目標

```mermaid
flowchart TB
    r---a1
    a1---a2
    a1---a3
    a3---a4
    a3---a5
    r---b1
    b1---b2
    b1---b3
    b3---b4:::green
    b3---b5
    b5---b6
    b5---b7

    r((40))

    a1((20))
    a2(( )):::clear
    a3((30))
    a4((28))
    a5((35))

    b1((50))
    b2(( )):::clear
    b3((70))
    b4((55))
    b5((85))
    b6((72))
    b7(( )):::clear
    
    %% linkStyle 8 stroke:#f96,stroke-width:4px 
    linkStyle 1 opacity:0
    linkStyle 6 opacity:0
    linkStyle 11 opacity:0
    classDef orange fill:#f96,stroke:#f66
    classDef green fill:#ecffec
    classDef clear opacity:0
```

## 二元搜尋樹的刪除

* 若刪除的是樹葉節點，直接刪除就好
* 若非樹葉節點，刪除後要從以下2群找一個替補原先的位置
    * 左子樹中最大的節點
    * 右子樹中最小的節點


例如，以下二元搜尋樹當中，刪除樹根「50」

```mermaid
flowchart TB
    r---a1
    a1---a2
    a1---a3
    r---b1
    b1---b2
    b1---b3

    r((50))

    a1((40))
    a2((30))
    a3((45))

    b1((65))
    b2((60))
    b3(( )):::clear
    
    linkStyle 5 opacity:0
    classDef orange fill:#f96,stroke:#f66
    classDef green fill:#ecffec
    classDef clear opacity:0
```

樹根「50」經刪除後，需要尋找替死鬼，可以選擇從左子樹尋找，或是從右子樹尋找（選擇其中一種就可）

```mermaid
flowchart TB
    r---a1
    a1---a2
    a1---a3
    r---b1
    b1---b2
    b1---b3

    r(( - ))

    a1((40))
    a2((30))
    a3((45))

    b1((65))
    b2((60))
    b3(( )):::clear
    
    classDef clear opacity:0
    linkStyle 5 opacity:0
```

### 方法一：從左子樹尋找最大節點

樹根的左子樹一共有40、30、45共三個節點

```mermaid
flowchart TB
    r---a1:::green
    a1---a2:::green
    a1---a3:::green
    r---b1
    b1---b2
    b1---b3

    r(( - ))

    a1((40))
    a2((30))
    a3((45))

    b1((65))
    b2((60))
    b3(( )):::clear
    
    classDef clear opacity:0
    linkStyle 5 opacity:0
    
    classDef orange fill:#f96,stroke:#f66
    classDef green fill:#ecffec
```

當中，最大的節點是「45」

```mermaid
flowchart TB
    r---a1:::green
    a1---a2:::green
    a1---a3:::orange
    r---b1
    b1---b2
    b1---b3

    r(( - ))

    a1((40))
    a2((30))
    a3((45))

    b1((65))
    b2((60))
    b3(( )):::clear
    
    classDef clear opacity:0
    linkStyle 5 opacity:0
    
    classDef orange fill:#f96,stroke:#f66
    classDef green fill:#ecffec
```

因此，「45」移動位置，成為了新的樹根
```mermaid
flowchart TB
    r---a1
    a1---a2
    a1---a3:::clear
    r---b1
    b1---b2
    b1---b3

    r((45))

    a1((40))
    a2((30))
    a3(( ))

    b1((65))
    b2((60))
    b3(( )):::clear
    
    classDef clear opacity:0
    linkStyle 5 opacity:0
    linkStyle 2 opacity:0
    
    classDef orange fill:#f96,stroke:#f66
    classDef green fill:#ecffec
```

### 方法二：從右子樹尋找最小節點

樹根的右子樹一共有65、60，兩個節點，當中最小的節點是「60」


```mermaid
flowchart TB
    r---a1
    a1---a2
    a1---a3
    r---b1:::green
    b1---b2:::orange
    b1---b3

    r(( - ))

    a1((40))
    a2((30))
    a3((45))

    b1((65))
    b2((60))
    b3(( )):::clear
    
    classDef clear opacity:0
    linkStyle 5 opacity:0
    
    classDef orange fill:#f96,stroke:#f66
    classDef green fill:#ecffec
```

「60」移動位置，成為新的樹根

```mermaid
flowchart TB
    r---a1
    a1---a2
    a1---a3
    r---b1
    b1---b2
    b1---b3

    r((60))

    a1((40))
    a2((30))
    a3((45))

    b1((65))
    b2(( )):::clear
    b3(( )):::clear
    
    classDef clear opacity:0
    linkStyle 5 opacity:0
    linkStyle 4 opacity:0
    
    classDef orange fill:#f96,stroke:#f66
    classDef green fill:#ecffec
```
