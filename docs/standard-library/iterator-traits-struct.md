---
title: "iterator_traits 結構 | Microsoft Docs"
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
  - "std::iterator_traits"
  - "xutility/std::iterator_traits"
  - "iterator_traits"
  - "std.iterator_traits"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "iterator_traits 類別"
  - "iterator_traits 結構"
ms.assetid: 8b92c2c5-f658-402f-8ca1-e7ae301b8514
caps.latest.revision: 19
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# iterator_traits 結構
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

用於的範本 Helper 結構指定 Iterator 應該有的所有重要型別定義。  
  
## 語法  
  
```  
template<class Iterator>  
    struct iterator_traits {  
        typedef typename Iterator::iterator_category iterator_category;  
        typedef typename Iterator::value_type value_type;  
        typedef typename Iterator::difference_type difference_type;  
        typedef difference_type distance_type;  
        typedef typename Iterator::pointer pointer;  
        typedef typename Iterator::reference reference;  
    };  
template<class Type>  
    struct iterator_traits<Type*> {  
        typedef random_access_iterator_tag iterator_category;  
        typedef Type value_type;  
        typedef ptrdiff_t difference_type;  
        typedef difference_type distance_type;  
        typedef Type *pointer;  
        typedef Type& reference;  
    };  
template<class Type>  
    struct iterator_traits<const Type*> {  
        typedef random_access_iterator_tag iterator_category;  
        typedef Type value_type;  
        typedef ptrdiff_t difference_type;  
        typedef difference_type distance_type;  
        typedef const Type *pointer;  
        typedef const Type& reference;  
    };  
```  
  
## 備註  
 範本結構定義成員型別  
  
-   **iterator\_category**: **Iterator::iterator\_category**的同義字。  
  
-   `value_type`: **Iterator::value\_type**的同義字。  
  
-   `difference_type`: **Iterator::difference\_type**的同義字。  
  
-   `distance_type`: **Iterator::difference\_type.**的同義資料表。  
  
-   **pointer**: **Iterator::pointer**的同義字。  
  
-   **reference**: **Iterator::reference**的同義字。  
  
 部分特製化判斷重要型別與型別 **Type \*** 或常數 **Type \***物件指標。  
  
 在這個實作也可以使用不使用部分特製化的幾個樣板函式:  
  
```  
template<class Category, class Type, class Diff>  
C _Iter_cat(const iterator<Category, Ty, Diff>&);  
template<class Ty>  
    random_access_iterator_tag _Iter_cat(const Ty *);  
  
template<class Category, class Ty, class Diff>  
Ty *_Val_type(const iterator<Category, Ty, Diff>&);  
template<class Ty>  
    Ty *_Val_type(const Ty *);  
  
template<class Category, class Ty, class Diff>  
Diff *_Dist_type(const iterator<Category, Ty, Diff>&);  
template<class Ty>  
    ptrdiff_t *_Dist_type(const Ty *);  
```  
  
 哪些更間接判斷數目相同的型別。  您可以使用這些函式當做函式呼叫的引數。  它們的唯一目的是提供一個有用的樣板類別界限給呼叫的函式。  
  
## 範例  
  
```  
// iterator_traits.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <iterator>  
#include <vector>  
#include <list>  
  
using namespace std;  
  
template< class it >  
void  
function( it i1, it i2 )  
{  
   iterator_traits<it>::iterator_category cat;  
   cout << typeid( cat ).name( ) << endl;  
   while ( i1 != i2 )  
   {  
      iterator_traits<it>::value_type x;  
      x = *i1;  
      cout << x << " ";  
      i1++;  
   };     
   cout << endl;  
};  
  
int main( )   
{  
   vector<char> vc( 10,'a' );  
   list<int> li( 10 );  
   function( vc.begin( ), vc.end( ) );  
   function( li.begin( ), li.end( ) );  
}  
```  
  
  **結構 std::random\_access\_iterator\_tag**  
**。**  
**結構 std::bidirectional\_iterator\_tag**  
**0 0 0 0 0 0 0 0 0 0**   
## 需求  
 **標頭：**\<迭代器\>  
  
 **命名空間:** std  
  
## 請參閱  
 [\<iterator\>](../standard-library/iterator.md)   
 [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [標準樣板程式庫](../misc/standard-template-library.md)