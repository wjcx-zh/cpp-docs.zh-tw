---
title: "tuple_element 類別 &lt;array&gt; | Microsoft Docs"
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
  - "std.tr1.tuple_element"
  - "tuple_element"
  - "std::tr1::tuple_element"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "tuple_element 類別 <array> (TR1)"
ms.assetid: 99201ca4-190a-4d9e-9013-de95ddfe5901
caps.latest.revision: 21
caps.handback.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# tuple_element 類別 &lt;array&gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

包裝陣列元素的類型。  
  
## 語法  
  
```  
// CLASS tuple_element (find element by index)  
template<size_t Index, class Tuple>  
struct tuple_element;  
  
template<size_t Index, class T, size_t Size>  
struct tuple_element<Index, array<T, Size>>  
  
// tuple_element for const  
template<size_t Index, class Tuple>  
struct tuple_element<Index, const Tuple>;  
  
// tuple_element for volatile  
template<size_t Index, class Tuple>  
struct tuple_element<Index, volatile Tuple>;  
  
// tuple_element for const volatile  
template<size_t Index, class Tuple>  
struct tuple_element<Index, const volatile Tuple>;  
  
template<size_t Index, class Tuple>  
using tuple_element_t = typename tuple_element<Index, Tuple>::type;  
  
```  
  
## 參數  
 `Index`  
 元素位置。  
  
 `T`  
 元素類型。  
  
 `N`  
 陣列的大小。  
  
## 備註  
 這個範本類別是特製化的陣列範本類別 [tuple\_element 類別](../standard-library/tuple-element-class-tuple.md)。 這個類別會提供陣列介面當做 N 個元素 tuple，其中每一個都有相同的類型。 每個特製化都具有巢狀的 typedef `type`，也就是類型的同義字 `array` 的 `Index` 元素類型的同義字，保留了任何 const\-volatile 限定性條件。  
  
## 範例  
  
```  
  
#include <array>   
#include <iostream>   
  
using namespace std;  
typedef array<int, 4> MyArray;  
  
int main()  
{  
    MyArray c0 { 0, 1, 2, 3 };  
  
    for (const auto& e : c0)  
    {  
        cout << " " << e;  
    }  
    cout << endl;  
  
    // display first element " 0"   
    tuple_element<0, MyArray>::type val = c0.front();  
    cout << " " << val << endl;  
}  
  
/*  
Output:  
0 1 2 3  
0  
*/  
  
```  
  
## 需求  
 **標頭：**\<array\>  
  
 **命名空間：**std  
  
## 請參閱  
 [\<array\>](../standard-library/array.md)   
 [\<tuple\>](../standard-library/tuple.md)   
 [tuple\_element 類別](../standard-library/tuple-element-class-tuple.md)