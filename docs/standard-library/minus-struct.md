---
title: "minus 結構 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "minus"
  - "std.minus"
  - "std::minus"
  - "xfunctional/std::minus"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "minus 結構"
  - "minus 類別"
ms.assetid: 7bce784e-2be6-413a-b516-004e9ecb2a39
caps.latest.revision: 20
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# minus 結構
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在引數上執行減法作業（二元 `operator-`）的預先定義功能物件。  
  
## 語法  
  
```  
template<class Type = void>  
   struct minus : public binary_function <Type, Type, Type>   
   {  
      Type operator()(  
         const Type& Left,   
         const Type& Right  
      ) const;  
   };  
  
// specialized transparent functor for operator-  
template<>  
   struct minus<void>  
   {  
      template<class Type1, class Type2>  
      auto operator()(Type1&& Left, Type2&& Right) const  
         -> decltype(std::forward<Type1>(Left)  
            - std::forward<Type2>(Right));  
   };  
  
```  
  
#### 參數  
 `Type`, `Type1`, `Type2`  
 一個支援二進位 `operator-` （接受指定或推斷型別的運算元）的型別。  
  
 `Left`  
 此作業的左運算元。  非特製化樣板接受型別 `Type` 的左值參考引數。  特製化樣板在左值和右值推斷型別 `Type1` 參考引數能完美轉送。  
  
 `Right`  
 此作業的右運算元。  非特製化樣板接受型別 `Type` 的左值參考引數。  特製化樣板在左值和右值推斷的型別 `Type2`參考引數能完美轉送。  
  
## 傳回值  
 `Left` `-` `Right` 的結果。  特製化樣板能對結果進行完美轉送，其具有 `operator-` 所傳回的型別。  
  
## 範例  
  
```  
// functional_minus.cpp  
// compile with: /EHsc  
#include <vector>  
#include <functional>  
#include <algorithm>  
#include <iostream>  
  
using namespace std;  
  
int main( )  
{  
   vector <int> v1, v2, v3 ( 6 );  
   vector <int>::iterator Iter1, Iter2, Iter3;  
  
   int i;  
   for ( i = 0 ; i <= 5 ; i++ )  
   {  
      v1.push_back( 4 * i + 1);  
   }  
  
   int j;  
   for ( j = 0 ; j <= 5 ; j++ )  
   {  
      v2.push_back( 3 * j - 1);  
   }  
  
   cout << "The vector v1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")" << endl;  
  
   cout << "The vector v2 = ( " ;  
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )  
      cout << *Iter2 << " ";  
   cout << ")" << endl;  
  
   // Finding the element-wise diference of the elements of v1 & v2  
   transform ( v1.begin( ),  v1.end( ), v2.begin( ), v3.begin ( ),   
      minus<int>( ) );  
  
   cout << "The element-wise differences between v1 and v2 are: ( " ;  
   for ( Iter3 = v3.begin( ) ; Iter3 != v3.end( ) ; Iter3++ )  
      cout << *Iter3 << " ";  
   cout << ")" << endl;  
}  
```  
  
  **The vector v1 \= \( 1 5 9 13 17 21 \)**  
**The vector v2 \= \( \-1 2 5 8 11 14 \)**  
**The element\-wise differences between v1 and v2 are: \( 2 3 4 5 6 7 \)**   
## 需求  
 **標題:** \<functional\>  
  
 **命名空間:** std  
  
## 請參閱  
 [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [標準樣板程式庫](../misc/standard-template-library.md)