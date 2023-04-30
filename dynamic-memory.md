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