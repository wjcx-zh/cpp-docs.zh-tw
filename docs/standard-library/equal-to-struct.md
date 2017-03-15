---
title: "equal_to 結構 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std::equal_to"
  - "equal_to"
  - "xfunctional/std::equal_to"
  - "std.equal_to"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "equal_to 函式"
  - "equal_to 結構"
ms.assetid: 8e4f2b50-b2db-48e3-b4cc-6cc03362c2a6
caps.latest.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 17
---
# equal_to 結構
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

二進位的斷詞使用引述執行等於計算 \(`運算元operator==`\)。  
  
## 語法  
  
```  
template<class Type = void>  
   struct equal_to : public binary_function<Type, Type, bool>   
   {  
      bool operator()(  
         const Type& Left,   
         const Type& Right  
      ) const;  
   };  
  
// specialized transparent functor for operator==  
template<>  
   struct equal_to<void>  
   {  
      template<class Type1, class Type2>  
      auto operator()(Type1&& Left, Type2&& Right) const  
         -> decltype(std::forward<Type1>(Left)  
            == std::forward<Type2>(Right));  
   };  
  
```  
  
#### 參數  
 `Type`, `Type1`, `Type2`  
 任何支援`operator==`接受指定或推斷型別的運算元之類型。  
  
 `Left`  
 等比較運算的左運算元。  非特製化樣板接受型別 `Type` 的左值參考引數。  特製化樣板在左值和右值推斷型別 `Type1` 參考引數能完美轉送。  
  
 `Right`  
 等比較運算的右運算元。  非特製化樣板接受型別 `Type` 的左值參考引數。  特製化樣板在左值和右值推斷的型別 `Type2`參考引數能完美轉送。  
  
## 傳回值  
 `Left` `==` `Right` 的結果。  特製化樣板能完善結果的轉送，其具有 `operator==`所傳回的型別。  
  
## 備註  
 型別 `Type` 的物件必須是相等可比較的。  這需要 `operator==` 定義在物件符合等價關聯的屬性上。  所有內建數值和指標型別滿足這個要求。  
  
## 範例  
  
```  
// functional_equal_to.cpp  
// compile with: /EHsc  
#include <vector>  
#include <functional>  
#include <algorithm>  
#include <iostream>  
  
using namespace std;  
  
int main( )  
{  
   vector <double> v1, v2, v3 ( 6 );  
   vector <double>::iterator Iter1, Iter2, Iter3;  
  
   int i;  
   for ( i = 0 ; i <= 5 ; i+=2 )  
   {  
      v1.push_back( 2.0 *i );  
      v1.push_back( 2.0 * i + 1.0 );  
   }  
  
   int j;  
   for ( j = 0 ; j <= 5 ; j+=2 )  
   {  
      v2.push_back( - 2.0 * j );  
      v2.push_back( 2.0 * j + 1.0 );  
   }  
  
   cout << "The vector v1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")" << endl;  
  
   cout << "The vector v2 = ( " ;  
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )  
      cout << *Iter2 << " ";  
   cout << ")" << endl;  
  
   // Testing for the element-wise equality between v1 & v2  
   transform ( v1.begin( ),  v1.end( ), v2.begin( ), v3.begin ( ),   
      equal_to<double>( ) );  
  
   cout << "The result of the element-wise equal_to comparison\n"  
      << "between v1 & v2 is: ( " ;  
   for ( Iter3 = v3.begin( ) ; Iter3 != v3.end( ) ; Iter3++ )  
      cout << *Iter3 << " ";  
   cout << ")" << endl;  
}  
```  
  
  **The vector v1 \= \( 0 1 4 5 8 9 \)**  
**The vector v2 \= \( \-0 1 \-4 5 \-8 9 \)**  
**The result of the element\-wise equal\_to comparison**  
**between v1 & v2 is: \( 1 1 0 1 0 1 \)**