---
title: "tuple_element 類別 &lt;utility&gt; | Microsoft Docs"
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
  - "tuple_element 類別 <utility> (TR1)"
ms.assetid: f9db79e8-685c-49e3-97ee-81763e516ce3
caps.latest.revision: 20
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# tuple_element 類別 &lt;utility&gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

包裝 `pair` 元素的類型。  
  
## 語法  
  
```  
// CLASS tuple_element (find element by index)  
template<size_t Index, class Tuple>  
struct tuple_element;  
  
// struct to determine type of element 0 in pair  
template<class Ty1, class Ty2>  
struct tuple_element<0, pair<Ty1, Ty2> >;  
  
// struct to determine type of element 1 in pair  
template<class Ty1, class Ty2>  
struct tuple_element<1, pair<Ty1, Ty2> >;  
  
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
  
#### 參數  
 索引  
 元素的位置，如為 pair 這個值就是 0 或 1。  
  
 `T1`  
 第一個配對元素的類型。  
  
 `T2`  
 第二個配對元素的類型。  
  
 類型  
  
## 備註  
 此範本是特製化的範本類別 [tuple\_element 類別](../standard-library/tuple-element-class-tuple.md)。 每個都有單一成員 typedef，`type`，也就是在 `pair` 指定位置的元素類型同義字，保留了任何 const 及\/或 volatile 限定性條件。`tuple_element_t` 是 `tuple_element<N, pair<T1, T2>>::type` 的方便別名。 使用 [get 函式](../Topic/get%20Function%20%3Cutility%3E.md) 傳回指定位置的元素或 \(在 C\+\+14 \/ Visual Studio 2015\) 指定類型的元素。  
  
## 範例  
  
```  
#include <utility>   
#include <iostream>   
  
using namespace std;  
  
typedef pair<int, double> MyPair;  
int main()  
{  
    MyPair c0(0, 1.333);  
  
    // display contents " 0 1"   
    cout << " " << get<0>(c0);  
    cout << " " << get<1>(c0) << endl;  
  
    // display first element " 0" by index  
    tuple_element<0, MyPair>::type val = get<0>(c0);  
    cout << " " << val;  
  
    // display second element by type   
    tuple_element<1, MyPair>::type val2 = get<double>(c0);  
    cout << " " << val2 << endl;  
}  
  
/*  
Output:  
0 1.333  
0 1.333  
*/  
```  
  
## 需求  
 **標頭：**\<utility\>  
  
 **命名空間：**std  
  
## 請參閱  
 [\<utility\>](../standard-library/utility.md)   
 [get 函式](../Topic/get%20Function%20%3Cutility%3E.md)   
 [tuple\_size 類別](../standard-library/tuple-size-class-utility.md)