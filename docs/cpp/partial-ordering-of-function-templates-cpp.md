---
title: "函式樣板的部分排序 (C++) | Microsoft Docs"
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
helpviewer_keywords: 
  - "函式樣板的部分排序"
ms.assetid: 0c17347d-0e80-47ad-b5ac-046462d9dc73
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 函式樣板的部分排序 (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

提供多個符合函式呼叫之引數清單的函式樣板。  C\+\+ 可定義函式樣板的部分排序，以指定應呼叫哪些函式。  進行部分排序是因為某些樣板會被視為等同於特製化。  
  
 編譯器會從可能相符的項目中選取最特殊的範本函式。  例如，若函式樣板採用類型 **T**，而其他函式樣板可以採用 **T\***，則在引數為指標類型時，會將 **T\*** 版本視為最特殊的版本，且其優先權大於一般 **T** 版本，即使兩者皆為可允許的符合項目。  
  
 請使用下列程序來判斷某個函式樣板是否為特製化程度較高的候選項目：  
  
1.  考量兩個函式樣板，T1 和 T2。  
  
2.  使用一個假設的唯一類型 X 來取代 T1 中的參數。  
  
3.  透過 T1 中的參數清單，查看 T2 對於該參數清單來說是否為有效的範本。  忽略所有隱含轉換。  
  
4.  以相反順序對 T1 和 T2 重複進行相同的程序。  
  
5.  如果某個樣板是其他範本的有效樣板引數清單，但反之則不然，則該範本會被視為比其他範本的特製化程度更低。  如果使用上一個步驟中的兩個樣板形成彼此的有效引數，則視為相等的特製化，此時可能會在嘗試使用它們時造成模稜兩可的呼叫。  
  
6.  請使用下列規則：  
  
    1.  特定類型的樣板特製化比採用泛型類型引數的樣板特製化程度更高。  
  
    2.  僅接受 **T\*** 的樣板比僅接受 **T** 的樣板更具特製化，因為假設的類型 **X\*** 是 **T** 樣板引數的有效引數，而 **X** 並不是 **T\*** 樣板引數的有效引數。  
  
    3.  **const T** 比 **T** 更具特製化，因為 **const X** 是 **T** 樣板引數的有效引數，而 **X** 並不是 **const T** 樣板引數的有效引數。  
  
    4.  **const T\*** 比 **T\*** 更具特製化，因為 **const X\*** 是 **T\*** 樣板引數的有效引數，而 **X\*** 並不是 **const T\*** 樣板引數的有效引數。  
  
7.  下列範例依標準所指定，可在 Visual C\+\+ .NET 2003 中運作：  
  
```  
// partial_ordering_of_function_templates.cpp  
// compile with: /EHsc  
#include <iostream>  
  
extern "C" int printf(const char*,...);  
template <class T> void f(T) {  
   printf_s("Less specialized function called\n");  
}  
  
template <class T> void f(T*) {  
   printf_s("More specialized function called\n");  
}  
  
template <class T> void f(const T*) {  
   printf_s("Even more specialized function for const T*\n");  
}  
  
int main() {  
   int i =0;  
   const int j = 0;  
   int *pi = &i;  
   const int *cpi = &j;  
  
   f(i);   // Calls less specialized function.  
   f(pi);  // Calls more specialized function.  
   f(cpi); // Calls even more specialized function.  
   // Without partial ordering, these calls would be ambiguous.  
}  
```  
  
### Output  
  
```  
Less specialized function called  
More specialized function called  
Even more specialized function for const T*  
```  
  
## 請參閱  
 [函式樣板](../cpp/function-templates.md)