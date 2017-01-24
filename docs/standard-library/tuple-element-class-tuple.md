---
title: "tuple_element 類別 &lt;tuple&gt; | Microsoft Docs"
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
  - "tuple_element 類別 <tuple> (TR1)"
ms.assetid: 4c51a6c1-ce81-462f-8c6c-291d69f2b77c
caps.latest.revision: 23
caps.handback.revision: 23
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# tuple_element 類別 &lt;tuple&gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

包裝 `tuple` 項目。  
  
## <a name="syntax"></a>語法  
  
```  
// CLASS tuple_element (find element by index)  
template <size_t Index, class Tuple>  
struct tuple_element;  
 
// tuple_element for const 
template <size_t Index, class Tuple>  
struct tuple_element<Index, const Tuple>;  
 
// tuple_element for volatile  
template <size_t Index, class Tuple>  
struct tuple_element<Index, volatile Tuple>;  
 
// tuple_element for const volatile  
template <size_t Index, class Tuple>  
struct tuple_element<Index, const volatile Tuple>;  
 
template <size_t Index, class Tuple>  
using tuple_element_t = typename tuple_element<Index, Tuple>::type;  
```  
  
#### <a name="parameters"></a>參數  
 `Index`  
 指定之項目的索引。  
  
 `Tuple`  
 Tuple 的類型。  
  
## <a name="remarks"></a>備註  
 此樣板類別具有巢狀的 typedef `type` 也就是在索引類型的同義字 `Index` tuple 型別的 `Tuple`。  
  
## <a name="example"></a>範例  
  
```  
#include <tuple>  
#include <string>  
#include <iostream>  
  
using namespace std;  
typedef tuple<int, double, string> MyTuple;  
  
int main()  
{  
  
    MyTuple c0{ 0, 1.5, "Tail" };  
  
    tuple_element_t<0, MyTuple> val = get<0>(c0); //get by index  
    tuple_element_t<1, MyTuple> val2 = get<1>(c0);  
    tuple_element_t<2, MyTuple> val3 = get<string>(c0); // get by type  
  
    cout << val << " " << val2 << " " << val3 << endl;  
}  
  
/*  
Output:  
0 1.5 Tail  
*/  
```  
  
## <a name="requirements"></a>需求  
 **標頭︰** \< tuple>  
  
 **命名空間︰** std  
  
## <a name="see-also"></a>請參閱  
[tuple ](../standard-library/tuple-class.md)
    
 [tuple_element](../standard-library/tuple-element-class-tuple.md)
