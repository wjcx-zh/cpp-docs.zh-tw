---
title: "tuple_size 類別 &lt;tuple&gt; | Microsoft Docs"
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
  - "tuple_size 類別 <tuple> (TR1)"
ms.assetid: 73852fc5-eb68-41f1-8379-465cedc2314a
caps.latest.revision: 23
caps.handback.revision: 23
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# tuple_size 類別 &lt;tuple&gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

報告的項目數， `tuple` 包含。  
  
## <a name="syntax"></a>語法  
  
```  
// TEMPLATE STRUCT tuple_size  
template <class Tuple>  
struct tuple_size;  
 
// size of tuple  
template <class... Types>  
struct tuple_size<tuple<Types...>>  
: integral_constant<size_t, sizeof...(Types)>;  
 
// size of const tuple  
template <class Tuple>  
struct tuple_size<const Tuple>;  
 
// size of volatile tuple  
template <class Tuple>  
struct tuple_size<volatile Tuple>;  
 
// size of const volatile tuple  
template <class Tuple>  
struct tuple_size<const volatile Tuple>;   
```  
  
#### <a name="parameters"></a>參數  
 `Tuple`  
 Tuple 的類型。  
  
## <a name="remarks"></a>備註  
 此樣板類別具有成員 `value` 也就是整數常數運算式的值是 tuple 型別的範圍 `Tuple`。  
  
## <a name="example"></a>範例  
  
```  
#include <tuple>   
#include <iostream>  
  
using namespace std;  
  
typedef tuple<int, double, int, double> MyTuple;  
int main()  
{  
    MyTuple c0(0, 1.5, 2, 3.7);  
  
    // display contents " 0 1 2 3"   
    cout << " " << get<0>(c0);  
    cout << " " << get<1>(c0);  
    cout << " " << get<2>(c0);  
    cout << " " << get<3>(c0) << endl;  
  
    // display size " 4"   
    cout << " " << tuple_size<MyTuple>::value << endl;  
}  
  
/*  
Output:  
0 1.5 2 3.7  
4  
*/  
```  
  
## <a name="requirements"></a>需求  
 **標頭︰** \< tuple>  
  
 **命名空間︰** std  
  
## <a name="see-also"></a>請參閱  
 [\< tuple>](../standard-library/tuple.md)   
 [tuple](../standard-library/tuple-class.md)  
 [tuple_element 類別](../standard-library/tuple-element-class-tuple.md)
