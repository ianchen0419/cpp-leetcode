# 中位數

假設該數組共有n項元素

## 數組為偶數

中位數索引為`(左中位數+右中位數)/2`  

* 左中位數索引：`n/2`
* 右中位數索引：`(n/2)+1`

```mermaid
flowchart
    a1[1]
    a2[2]
    a3[3]:::orange
    a4[4]:::orange
    a5[5]
    a6[6]

    classDef orange fill:#f96,stroke:#f66
```

左中位數為`3`，右中位數為`4`，`(3+4)/2 = 3.5`，中位數為3.5

## 數組為奇數

中位數為索引：`(n+1)/2`

```mermaid
flowchart
    a1[1]
    a2[2]
    a3[3]:::orange
    a4[4]
    a5[5]

    classDef orange fill:#f96,stroke:#f66
```

n為5，`(5+1)/2=3`，第3項元素為3，中位數為3

