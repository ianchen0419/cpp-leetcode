# Binary Search Tree 二元搜尋樹

```mermaid
flowchart TB
    r((70))-->a1
    a1((60))-->a2((50))
    a1-->a3((65))
    r-->b1
    b1((80))-->b2((85))
```

規則：左小右大
* 左子樹的所有鍵值都小於樹根
* 右子樹的所有鍵值都大於樹根
* 左子樹也是BST、右子樹也是BST
* 每個鍵值都不一樣

## BST的加入

有一BST如下，欲加入48
```mermaid
flowchart TB
    r:::green-->a1
    a1-->a2
    a1-->a3
    r-->b1
    b1-->b2

    r((50))

    a1((40))
    a2((30))
    a3((45))

    b1((65))
    b2((60))
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
