---
title: "註標 | Microsoft Docs"
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
  - "陣列 [C++], 註標"
  - "運算子多載, 範例"
  - "運算子 [C++], 多載"
  - "註標運算子"
  - "註標運算子, 多載"
  - "註標"
ms.assetid: eb151281-6733-401d-9787-39ab6754c62c
caps.latest.revision: 10
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 註標
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

註標運算子 \(**\[ \]**\) 和函式呼叫運算子一樣，屬於二元運算子。  註標運算子必須是使用單一引數的非靜態成員函式。  這個引數可以是任何類型，並且指定所需的陣列註標。  
  
## 範例  
 下列範例示範如何建立屬於 `int` 類型且會實作繫結檢查的向量：  
  
```  
// subscripting.cpp  
// compile with: /EHsc  
#include <iostream>  
  
using namespace std;  
class IntVector {  
public:  
   IntVector( int cElements );  
   ~IntVector() { delete [] _iElements; }  
   int& operator[](int nSubscript);  
private:  
   int *_iElements;  
   int _iUpperBound;  
};  
  
// Construct an IntVector.  
IntVector::IntVector( int cElements ) {  
   _iElements = new int[cElements];  
   _iUpperBound = cElements;  
}  
  
// Subscript operator for IntVector.  
int& IntVector::operator[](int nSubscript) {  
   static int iErr = -1;  
  
   if( nSubscript >= 0 && nSubscript < _iUpperBound )  
      return _iElements[nSubscript];  
   else {  
      clog << "Array bounds violation." << endl;  
      return iErr;  
   }  
}  
  
// Test the IntVector class.  
int main() {  
   IntVector v( 10 );  
   int i;  
  
   for( i = 0; i <= 10; ++i )  
      v[i] = i;  
  
   v[3] = v[9];  
  
   for ( i = 0; i <= 10; ++i )  
      cout << "Element: [" << i << "] = " << v[i] << endl;  
}  
```  
  
  **Array bounds violation.**  
**Element: \[0\] \= 0**  
**Element: \[1\] \= 1**  
**Element: \[2\] \= 2**  
**Element: \[3\] \= 9**  
**Element: \[4\] \= 4**  
**Element: \[5\] \= 5**  
**Element: \[6\] \= 6**  
**Element: \[7\] \= 7**  
**Element: \[8\] \= 8**  
**Element: \[9\] \= 9**  
**Array bounds violation.**  
**Element: \[10\] \= 10**   
## 註解  
 當 `i` 在前一個程式達到 10 時，`operator[]` 會偵測到正在使用超出範圍的註標並發出錯誤訊息。  
  
 請注意，`operator[]` 函式會傳回參考類型。  這會使它變成左值，讓您能夠在指派運算子的任一端使用註標運算式。  
  
## 請參閱  
 [運算子多載](../cpp/operator-overloading.md)