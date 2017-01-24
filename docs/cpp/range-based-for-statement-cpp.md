---
title: "以範圍為基礎的 for 陳述式 (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
ms.assetid: 5750ba1d-ba48-4236-a923-e32de8345c2d
caps.latest.revision: 10
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 以範圍為基礎的 for 陳述式 (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

對於 `expression` 中的每個項目重複且循序地執行 `statement` 。  
  
## 語法  
  
```  
  
      for ( for-range-declaration : expression )  
   statement   
```  
  
## 備註  
 使用範圍架構的 `for` 陳述式來建構迴圈時，必須定義一個可以逐一查看的範圍一例如 `std::vector` 或其他 STL 序列的範圍是由 `begin()` 和 `end()` 所定義。  在 `for-range-declaration` 區段宣告的名稱是 `for` 陳述式的區域變數，不可在 `expression` 或 `statement` 重複宣告。  請注意 [auto](../cpp/auto-cpp.md) 關鍵字建議陳述式的在 `for-range-declaration` 區段使用。  
  
 以下程式碼示範如何使用排列的 `for` 迴圈逐一查看一個陣列和一個向量：  
  
```cpp  
  
// range-based-for.cpp  
// compile by using: cl /EHsc /nologo /W4  
#include <iostream>  
#include <vector>  
using namespace std;  
  
int main()   
{  
    // Basic 10-element integer array.  
    int x[10] = { 1, 2, 3, 4, 5, 6, 7, 8, 9, 10 };  
  
    // Range-based for loop to iterate through the array.  
    for( int y : x ) { // Access by value using a copy declared as a specific type.   
                       // Not preferred.  
        cout << y << " ";  
    }  
    cout << endl;  
  
    // The auto keyword causes type inference to be used. Preferred.  
  
    for( auto y : x ) { // Copy of 'x', almost always undesirable  
        cout << y << " ";  
    }  
    cout << endl;  
  
    for( auto &y : x ) { // Type inference by reference.  
        // Observes and/or modifies in-place. Preferred when modify is needed.  
        cout << y << " ";  
    }  
    cout << endl;  
  
    for( const auto &y : x ) { // Type inference by reference.  
        // Observes in-place. Preferred when no modify is needed.  
        cout << y << " ";  
    }  
    cout << endl;  
    cout << "end of integer array test" << endl;  
    cout << endl;  
  
    // Create a vector object that contains 10 elements.  
    vector<double> v;  
    for (int i = 0; i < 10; ++i) {  
        v.push_back(i + 0.14159);  
    }  
  
    // Range-based for loop to iterate through the vector, observing in-place.  
    for( const auto &j : v ) {  
        cout << j << " ";  
    }  
    cout << endl;  
    cout << "end of vector test" << endl;  
}  
  
```  
  
 輸出如下：  
  
 `1 2 3 4 5 6 7 8 9 10`  
  
 `1 2 3 4 5 6 7 8 9 10`  
  
 `1 2 3 4 5 6 7 8 9 10`  
  
 `1 2 3 4 5 6 7 8 9 10`  
  
 `end of integer array test`  
  
 `0.14159 1.14159 2.14159 3.14159 4.14159 5.14159 6.14159 7.14159 8.14159 9.14159`  
  
 `end of vector test`  
  
 執行以下其中一個 `statement` 時，範圍架構的 `for` 會終止： [break](../cpp/break-statement-cpp.md) 、 [return](../cpp/return-statement-cpp.md) ，或 [goto](../cpp/goto-statement-cpp.md) 至範圍架構的 **for** 迴圈之外被標記的陳述式。  [continue](../cpp/continue-statement-cpp.md) 陳述式僅終止目前所在的 `for` 迴圈項目。  
  
 請謹記有關範圍架構的 `for` 迴圈的這些特性：  
  
-   自動辨識陣列。  
  
-   辨識具有 `.begin()` 和 `.end()`的容器。  
  
-   使用引數相關查閱 `begin()` 和 `end()` 。  
  
## 請參閱  
 [auto](../cpp/auto-cpp.md)   
 [反覆運算陳述式](../cpp/iteration-statements-cpp.md)   
 [C\+\+ 關鍵字](../cpp/keywords-cpp.md)   
 [while 陳述式 \(C\+\+\)](../cpp/while-statement-cpp.md)   
 [do\-while 陳述式 \(C\+\+\)](../cpp/do-while-statement-cpp.md)   
 [for 陳述式 \(C\+\+\)](../cpp/for-statement-cpp.md)