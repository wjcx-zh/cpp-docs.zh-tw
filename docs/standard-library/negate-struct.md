---
title: "negate 結構 | Microsoft Docs"
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
  - "negate"
  - "std.negate"
  - "std::negate"
  - "xfunctional/std::negate"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "negate 結構"
  - "negate 類別"
ms.assetid: 8a372686-786e-4262-b37c-ca13dc11e62f
caps.latest.revision: 20
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# negate 結構
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

一個是先定義好的函式物件將對引述執行 negation 運算\( unary `operator-`\) 使用現有的引數。  
  
## 語法  
  
```  
template<class Type = void>  
   struct negate : public unary_function<Type, Type>   
   {  
      Type operator()(  
         const Type& Left  
      ) const;  
   };  
  
// specialized transparent functor for unary operator-  
template<>  
   struct negate<void>  
   {  
      template<class Type>  
      auto operator()(Type&& Left) const  
         -> decltype(-std::forward<Type>(Left));  
   };  
  
```  
  
#### 參數  
 `Type`  
 任何支援`operator-`接受指定或推斷型別的運算元之類型。  
  
 `Left`  
 要變成相反值的運算元。  特製化樣板在左值和右值推斷的型別 `Type` 參考引數能完美轉送。  
  
## 傳回值  
 `-` `Left.` 的結果，特製化樣板完善轉送結果，其有由元素 `operator-` 傳回的型別 。  
  
## 範例  
  
```  
// functional_negate.cpp  
// compile with: /EHsc  
#include <vector>  
#include <functional>  
#include <algorithm>  
#include <iostream>  
  
using namespace std;  
  
int main( )  
{  
   vector <int> v1, v2 ( 8 );  
   vector <int>::iterator Iter1, Iter2;  
  
   int i;  
   for ( i = -2 ; i <= 5 ; i++ )  
   {  
      v1.push_back( 5 * i );  
   }  
  
   cout << "The vector v1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")" << endl;  
  
   // Finding the element-wise negatives of the vector v1  
   transform ( v1.begin( ),  v1.end( ), v2.begin( ), negate<int>( ) );  
  
   cout << "The negated elements of the vector = ( " ;  
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )  
      cout << *Iter2 << " ";  
   cout << ")" << endl;  
}  
```  
  
  **The vector v1 \= \( \-10 \-5 0 5 10 15 20 25 \)**  
**The negated elements of the vector \= \( 10 5 0 \-5 \-10 \-15 \-20 \-25 \)**   
## 需求  
 **標題:** \<functional\>  
  
 **命名空間:** std  
  
## 請參閱  
 [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [標準樣板程式庫](../misc/standard-template-library.md)