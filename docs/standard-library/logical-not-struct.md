---
title: "logical_not 結構 | Microsoft Docs"
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
  - "std.logical_not"
  - "logical_not"
  - "xfunctional/std::logical_not"
  - "std::logical_not"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "logical_not 類別"
  - "logical_not 結構"
ms.assetid: 892db678-31da-4540-974b-17b05efc0849
caps.latest.revision: 21
caps.handback.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# logical_not 結構
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

預先定義的功能物件在它的引數執行邏輯 NOT 作業 \(`operator!`\)。  
  
## 語法  
  
```  
template<class Type = void>  
   struct logical_not : public unary_function<Type, bool>   
   {  
      bool operator()(  
         const Type& Left  
      ) const;  
   };  
  
// specialized transparent functor for operator!  
template<>  
   struct logical_not<void>  
   {  
      template<class Type>  
      auto operator()(Type&& Left) const  
         -> decltype(!std::forward<Type>(Left));  
   };  
  
```  
  
#### 參數  
 `Type`  
 任何支援`operator!` 接受指定或推斷型別的運算元之類型。  
  
 `Left`  
 邏輯 NOT 作業的運算元。  非特製化樣板接受型別 `Type` 的左值參考引數。  特製化樣板在左值和右值推斷的型別 `Type` 參考引數能完美轉送。  
  
## 傳回值  
 `!` `Left` 的結果。  特製化樣板能完善結果的轉送，其具有 `operator!`所傳回的型別。  
  
## 範例  
  
```  
// functional_logical_not.cpp  
// compile with: /EHsc  
#include <deque>  
#include <algorithm>  
#include <functional>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   deque<bool> d1, d2 ( 7 );  
   deque<bool>::iterator iter1, iter2;  
  
   int i;  
   for ( i = 0 ; i < 7 ; i++ )  
   {  
      d1.push_back((bool)((i % 2) != 0));  
   }  
  
   cout << boolalpha;    // boolalpha I/O flag on  
  
   cout << "Original deque:\n d1 = ( " ;  
   for ( iter1 = d1.begin( ) ; iter1 != d1.end( ) ; iter1++ )  
      cout << *iter1 << " ";  
   cout << ")" << endl;  
  
   // To flip all the truth values of the elements,  
   // use the logical_not function object  
   transform( d1.begin( ), d1.end( ), d2.begin( ),logical_not<bool>( ) );  
   cout << "The deque with its values negated is:\n d2 = ( " ;  
   for ( iter2 = d2.begin( ) ; iter2 != d2.end( ) ; iter2++ )  
      cout << *iter2 << " ";  
   cout << ")" << endl;  
}  
```  
  
  **原始的雙向佇列:**  
 **d1 \= \( false true false true false true false \)**  
**The deque with its values negated is:**  
 **d2 \= \( true false true false true false true \)**   
## 需求  
 **標題:** \<functional\>  
  
 **命名空間:** std  
  
## 請參閱  
 [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [標準樣板程式庫](../misc/standard-template-library.md)