---
title: "tuple_size 類別 &lt;array&gt; | Microsoft Docs"
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
  - "tuple_size"
  - "std::tr1::tuple_size"
  - "std.tr1.tuple_size"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "tuple_size 類別 <array> (TR1)"
ms.assetid: ef95ffee-59b4-4396-817f-487d4486772d
caps.latest.revision: 20
caps.handback.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# tuple_size 類別 &lt;array&gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

包裝陣列的大小。  
  
## 語法  
  
```  
template<class Tuple>  
struct tuple_size;  
  
// struct to determine number of elements in array  
template<class T, size_t Size>  
struct tuple_size<array<T, Size> >  
: integral_constant<size_t, Size>;  
  
// size of const tuple  
template<class Tuple>  
struct tuple_size<const Tuple>;  
  
// size of volatile tuple  
template<class Tuple>  
struct tuple_size<volatile Tuple>;  
  
// size of const volatile tuple  
template<class Tuple>  
struct tuple_size<const volatile Tuple>;  
  
```  
  
## 範本參數  
 `T`  
 元素的類型。  
  
 `Size`  
 陣列的大小。  
  
## 備註  
 這個範本是特製化的範本類別 [tuple\_size 類別](../standard-library/tuple-size-class-tuple.md)。 其成員之一 `value` 是值為 `N` 的整數常數運算式，而該值是陣列的大小。  
  
## 範例  
  
```  
#include <array>   
#include <iostream>   
  
using namespace std;  
  
typedef array<int, 4> MyArray;  
  
int main()  
{  
    MyArray c0 { 0, 1, 2, 3 };  
  
    // display contents " 0 1 2 3"   
    for (const auto& e : c0)  
    {  
        cout << e;  
    }  
    cout << endl;  
  
    // display size " 4"   
    cout << " " << tuple_size<MyArray>::value << endl;  
}  
/*  
Output:  
0123  
4  
*/  
  
```  
  
## 需求  
 **標頭：**\<array\>  
  
 **命名空間：**std  
  
## 請參閱  
 [\<array\>](../standard-library/array.md)   
 [\<tuple\>](../standard-library/tuple.md)   
 [tuple\_size 類別](../standard-library/tuple-size-class-tuple.md)