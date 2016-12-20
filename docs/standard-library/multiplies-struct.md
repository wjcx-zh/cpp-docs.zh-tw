---
title: "multiplies 結構 | Microsoft Docs"
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
  - "std::multiplies"
  - "multiplies"
  - "xfunctional/std::multiplies"
  - "std.multiplies"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "multiplies 類別"
  - "multiplies 結構"
ms.assetid: ec85e8af-70ad-44ad-90f0-d961a5847864
caps.latest.revision: 21
caps.handback.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# multiplies 結構
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在它的引數執行乘法運算 \(二進位\) `operator*`的預先定義功能物件。  
  
## 語法  
  
```  
template<class Type = void>  
   struct multiplies : public binary_function <Type, Type, Type>   
   {  
      Type operator()(  
         const Type& Left,   
         const Type& Right  
      ) const;  
   };  
  
// specialized transparent functor for operator*  
template<>  
   struct multiplies<void>  
   {  
      template<class Type1, class Type2>  
      auto operator()(Type1&& Left, Type2&& Right) const  
         -> decltype(std::forward<Type1>(Left)  
            * std::forward<Type2>(Right));  
   };  
  
```  
  
#### 參數  
 `Type`, `Type1`, `Type2`  
 任何支援位元運算 `operator*`接受指定或推斷型別的運算元。  
  
 `Left`  
 乘法作業的左運算元。  非特製化樣板接受型別 `Type` 的左值參考引數。  特製化樣板在左值和右值推斷型別 `Type1` 參考引數能完美轉送。  
  
 `Right`  
 乘法作業的右運算元。  非特製化樣板接受型別 `Type` 的左值參考引數。  特製化樣板在左值和右值推斷的型別 `Type2`參考引數能完美轉送。  
  
## 傳回值  
 `Left` `*` `Right` 的結果。  特製化樣板能完善結果的轉送，其具有 `operator*`所傳回的型別。  
  
## 範例  
  
```  
// functional_multiplies.cpp  
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
   for ( i = 1 ; i <= 6 ; i++ )  
   {  
      v1.push_back( 2 * i );  
   }  
  
   int j;  
   for ( j = 1 ; j <= 6 ; j++ )  
   {  
      v2.push_back( 3 * j );  
   }  
  
   cout << "The vector v1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")" << endl;  
  
   cout << "The vector v2 = ( " ;  
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )  
      cout << *Iter2 << " ";  
   cout << ")" << endl;  
  
   // Finding the element-wise products of the elements of v1 & v2  
   transform ( v1.begin( ),  v1.end( ), v2.begin( ), v3.begin ( ),   
      multiplies<int>( ) );  
  
   cout << "The element-wise products of vectors V1 & v2\n are: ( " ;  
   for ( Iter3 = v3.begin( ) ; Iter3 != v3.end( ) ; Iter3++ )  
      cout << *Iter3 << " ";  
   cout << ")" << endl;  
}  
```  
  
  **向量 v1 \= \(2 4 6 8 10 12\)。**  
**向量 v2 \= \( 3 6 9 12 15 18 \)**  
**向量 V1 & v2 元素對元素的積**  
 **為: \(6 24 54 96 150 216\)**   
## 需求  
 **標題:** \<functional\>  
  
 **命名空間:** std  
  
## 請參閱  
 [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [標準樣板程式庫](../misc/standard-template-library.md)