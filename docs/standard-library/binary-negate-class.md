---
title: "binary_negate 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "xfunctional/std::binary_negate"
  - "std::binary_negate"
  - "binary_negate"
  - "std.binary_negate"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "binary_negate 類別"
ms.assetid: 7b86f02c-af7e-4c7f-9df1-08addae4dd65
caps.latest.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 20
---
# binary_negate 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

提供一個成員函式的樣板類別，此成員函式否定指定的二元函式之傳回值。  
  
## 語法  
  
```  
  
   template<class Operation>  
class binary_negate  
   : public binary_function <  
      typename Operation::first_argument_type,  
      typename Operation::second_argument_type,   
      bool>   
{  
public:  
explicit binary_negate(  
   const Operation& _Func  
);  
bool operator()(  
   const typename Operation::first_argument_type& _Left,  
   const typename Operation::second_argument_type& _Right  
) const;  
};  
```  
  
#### 參數  
 `_Func`  
 要變成相反值的二元函式。  
  
 `_Left`  
 要變成相反值的二元函式的左運算元。  
  
 `_Right`  
 要變成相反值的二元函式的右運算元。  
  
## 傳回值  
 二元函式的負值。  
  
## 備註  
 樣板類別儲存二元函式物件 \_Func 的複本。  它會定義成員的函式 `operator()` 為傳回 **\!**\_Func*\(\_Left， \_Right\)。*  
  
 直接很少使用 `binary_negate` 建構函式。  Helper 函式 [not2](../Topic/not2%20Function.md) 通常慣用宣告和使用 **binary\_negator** 配接器述詞。  
  
## 範例  
  
```  
// functional_binary_negate.cpp  
// compile with: /EHsc  
#define _CRT_RAND_S  
#include <stdlib.h>  
  
#include <vector>  
#include <algorithm>  
#include <functional>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   vector <unsigned int> v1;  
   vector <unsigned int>::iterator Iter1;  
  
   unsigned int i;  
   v1.push_back( 6262 );  
   v1.push_back( 6262 );  
   unsigned int randVal = 0;  
   for ( i = 0 ; i < 5 ; i++ )  
   {  
      rand_s(&randVal);  
      v1.push_back( randVal );  
   }  
  
   cout << "Original vector v1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")" << endl;  
  
   // To sort in ascending order,  
   // use default binary predicate less<unsigned int>( )  
   sort( v1.begin( ), v1.end( ) );  
   cout << "Sorted vector v1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")" << endl;  
  
   // To sort in descending order,  
   // use the binary_negate function  
   sort( v1.begin( ), v1.end( ),  
   binary_negate<less<unsigned int> >(less<unsigned int>( ) ) );  
  
   // The helper function not2 could also have been used  
   // in the above line and is usually preferred for convenience  
   // sort( v1.begin( ), v1.end( ), not2(less<unsigned int>( ) ) );  
  
   cout << "Resorted vector v1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")" << endl;  
}  
```  
  
  **原始向量 v1 \= \(6262 6262 2233879413 2621500314 580942933 3715465425 3739828298\)。**  
**排序的向量 v1 \= \(6262 6262 580942933 2233879413 2621500314 3715465425 3739828298\)。**  
**所依賴的向量 v1 \= \(3739828298 3715465425 2621500314 2233879413 580942933 6262 6262\)。**   
## 需求  
 **標題:** \<functional\>  
  
 std  
  
## 請參閱  
 [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [標準樣板程式庫](../misc/standard-template-library.md)