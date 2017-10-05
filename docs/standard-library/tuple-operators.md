---
title: "&lt;tuple&gt; 運算子 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- tuple/std::operator!=
- tuple/std::operator>
- tuple/std::operator>=
- tuple/std::operator<
- tuple/std::operator<=
- tuple/std::operator==
dev_langs:
- C++
ms.assetid: f25752dc-d3e2-4e12-b5ac-9a8682ca60ed
caps.latest.revision: 13
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 65f4e356ad0d46333b0d443d0fd6ac0b9f2b6f58
ms.openlocfilehash: c336ed5e11a7db00475da735c827c23dadfa56c7
ms.contentlocale: zh-tw
ms.lasthandoff: 10/03/2017

---
# <a name="lttuplegt-operators"></a>&lt;tuple&gt; 運算子
||||  
|-|-|-|  
|[operator!=](#op_neq)|[operator&gt;](#op_gt)|[operator&gt;=](#op_gt_eq)|  
|[operator&lt;](#op_lt)|[operator&lt;=](#op_lt_eq)|[operator==](#op_eq_eq)|  
  
##  <a name="op_neq"></a>  operator!=  
 比較兩個 `tuple` 物件是否不相等。  
  
```  
template <class T1, class T2, ..., class TN,  
    class U1, class U2, ..., class UN>  
bool operator!=(const tuple<T1, T2, ..., TN>& tpl1,  
    const tuple<U1, U2, ..., UN>& tpl2);
```  
  
### <a name="parameters"></a>參數  
 `TN`  
 第 N 個 tuple 項目類型。  
  
### <a name="remarks"></a>備註  
 當 `N` 為 0 時，此函式會傳回 false，否則 `get<0>(tpl1) != get<0>(tpl2) || get<1>(tpl1) != get<1>(tpl2) || ... || get<N - 1>(tpl1) == get<N - 1>(tpl2)`。  
  
### <a name="example"></a>範例  
  
```cpp  
// std__tuple__operator_ne.cpp   
// compile with: /EHsc   
#include <tuple>   
#include <iostream>   
  
typedef std::tuple<int, double, int, double> Mytuple;   
int main() {   
    Mytuple c0(0, 1, 2, 3);   
  
// display contents " 0 1 2 3"   
    std::cout << " " << std::get<0>(c0);   
    std::cout << " " << std::get<1>(c0);   
    std::cout << " " << std::get<2>(c0);   
    std::cout << " " << std::get<3>(c0);   
    std::cout << std::endl;   
  
    Mytuple c1 = std::make_tuple(4, 5, 6, 7);   
  
// display contents " 4 5 6 7"   
    std::cout << " " << std::get<0>(c0);   
    std::cout << " " << std::get<1>(c0);   
    std::cout << " " << std::get<2>(c0);   
    std::cout << " " << std::get<3>(c0);   
    std::cout << std::endl;   
  
// display results of comparisons   
    std::cout << std::boolalpha << " " << (c0 != c0);   
    std::cout << std::endl;   
    std::cout << std::boolalpha << " " << (c0 != c1);   
    std::cout << std::endl;   
  
    return (0);   
}  
```  
  
```Output  
0 1 2 3  
0 1 2 3  
false  
true  
```  
  
##  <a name="op_lt"></a>  operator&lt;  
 比較 `tuple` 物件為小於。  
  
```  
template <class T1, class T2, ..., class TN,  
    class U1, class U2, ..., class UN>  
bool operator<(const tuple<T1, T2, ..., TN>& tpl1,  
    const tuple<U1, U2, ..., UN>& tpl2);
```  
  
### <a name="parameters"></a>參數  
 `TN`  
 第 N 個 tuple 項目類型。  
  
### <a name="remarks"></a>備註  
 當 `N` 大於 0 且 `tpl1` 中的第一個不同值在比較後小於 `tpl2` 中的對應值時，函式傳回會 true，否則會傳回 false。  
  
### <a name="example"></a>範例  
  
```cpp  
// std__tuple__operator_lt.cpp   
// compile with: /EHsc   
#include <tuple>   
#include <iostream>   
  
typedef std::tuple<int, double, int, double> Mytuple;   
int main() {   
    Mytuple c0(0, 1, 2, 3);   
  
// display contents " 0 1 2 3"   
    std::cout << " " << std::get<0>(c0);   
    std::cout << " " << std::get<1>(c0);   
    std::cout << " " << std::get<2>(c0);   
    std::cout << " " << std::get<3>(c0);   
    std::cout << std::endl;   
  
    Mytuple c1 = std::make_tuple(4, 5, 6, 7);   
  
// display contents " 4 5 6 7"   
    std::cout << " " << std::get<0>(c0);   
    std::cout << " " << std::get<1>(c0);   
    std::cout << " " << std::get<2>(c0);   
    std::cout << " " << std::get<3>(c0);   
    std::cout << std::endl;   
  
// display results of comparisons   
    std::cout << std::boolalpha << " " << (c0 < c0);   
    std::cout << std::endl;   
    std::cout << std::boolalpha << " " << (c0 < c1);   
    std::cout << std::endl;   
  
    return (0);   
}  
```  
  
```Output  
0 1 2 3  
0 1 2 3  
false  
true  
```  
  
##  <a name="op_lt_eq"></a>  operator&lt;=  
 比較 `tuple` 物件為小於或等於。  
  
```  
template <class T1, class T2, ..., class TN,  
    class U1, class U2, ..., class UN>  
bool operator<=(const tuple<T1, T2, ..., TN>& tpl1,  
    const tuple<U1, U2, ..., UN>& tpl2);
```  
  
### <a name="parameters"></a>參數  
 `TN`  
 第 N 個 tuple 項目類型。  
  
### <a name="remarks"></a>備註  
 函式會傳回 `!(tpl2 < tpl1)`。  
  
### <a name="example"></a>範例  
  
```cpp  
// std__tuple__operator_le.cpp   
// compile with: /EHsc   
#include <tuple>   
#include <iostream>   
  
typedef std::tuple<int, double, int, double> Mytuple;   
int main() {   
    Mytuple c0(0, 1, 2, 3);   
  
// display contents " 0 1 2 3"   
    std::cout << " " << std::get<0>(c0);   
    std::cout << " " << std::get<1>(c0);   
    std::cout << " " << std::get<2>(c0);   
    std::cout << " " << std::get<3>(c0);   
    std::cout << std::endl;   
  
    Mytuple c1 = std::make_tuple(4, 5, 6, 7);   
  
// display contents " 4 5 6 7"   
    std::cout << " " << std::get<0>(c0);   
    std::cout << " " << std::get<1>(c0);   
    std::cout << " " << std::get<2>(c0);   
    std::cout << " " << std::get<3>(c0);   
    std::cout << std::endl;   
  
// display results of comparisons   
    std::cout << std::boolalpha << " " << (c0 <= c0);   
    std::cout << std::endl;   
    std::cout << std::boolalpha << " " << (c1 <= c0);   
    std::cout << std::endl;   
  
    return (0);   
}  
```  
  
```Output  
0 1 2 3  
0 1 2 3  
true  
false  
```  
  
##  <a name="op_eq_eq"></a>  operator==  
 比較兩個 `tuple` 物件是否相等。  
  
```  
template <class T1, class T2, ..., class TN,  
    class U1, class U2, ..., class UN>  
bool operator==(const tuple<T1, T2, ..., TN>& tpl1,  
    const tuple<U1, U2, ..., UN>& tpl2);
```  
  
### <a name="parameters"></a>參數  
 `TN`  
 第 N 個 tuple 項目類型。  
  
### <a name="remarks"></a>備註  
 當 `N` 為 0 時，此函式會傳回 true，否則 `get<0>(tpl1) == get<0>(tpl2) && get<1>(tpl1) == get<1>(tpl2) && ... && get<N - 1>(tpl1) == get<N - 1>(tpl2)`。  
  
### <a name="example"></a>範例  
  
```cpp  
// std__tuple__operator_eq.cpp   
// compile with: /EHsc   
#include <tuple>   
#include <iostream>   
  
typedef std::tuple<int, double, int, double> Mytuple;   
int main() {   
    Mytuple c0(0, 1, 2, 3);   
  
// display contents " 0 1 2 3"   
    std::cout << " " << std::get<0>(c0);   
    std::cout << " " << std::get<1>(c0);   
    std::cout << " " << std::get<2>(c0);   
    std::cout << " " << std::get<3>(c0);   
    std::cout << std::endl;   
  
    Mytuple c1 = std::make_tuple(4, 5, 6, 7);   
  
// display contents " 4 5 6 7"   
    std::cout << " " << std::get<0>(c0);   
    std::cout << " " << std::get<1>(c0);   
    std::cout << " " << std::get<2>(c0);   
    std::cout << " " << std::get<3>(c0);   
    std::cout << std::endl;   
  
// display results of comparisons   
    std::cout << std::boolalpha << " " << (c0 == c0);   
    std::cout << std::endl;   
    std::cout << std::boolalpha << " " << (c0 == c1);   
    std::cout << std::endl;   
  
    return (0);   
}  
```  
  
```Output  
0 1 2 3  
0 1 2 3  
true  
false  
```  
  
##  <a name="op_gt"></a>  operator&gt;  
 比較 `tuple` 物件為大於。  
  
```  
template <class T1, class T2, ..., class TN,  
    class U1, class U2, ..., class UN>  
bool operator>(const tuple<T1, T2, ..., TN>& tpl1,  
    const tuple<U1, U2, ..., UN>& tpl2);
```  
  
### <a name="parameters"></a>參數  
 `TN`  
 第 N 個 tuple 項目類型。  
  
### <a name="remarks"></a>備註  
 函式會傳回 `tpl2 < tpl1`。  
  
### <a name="example"></a>範例  
  
```cpp  
// std__tuple__operator_gt.cpp   
// compile with: /EHsc   
#include <tuple>   
#include <iostream>   
  
typedef std::tuple<int, double, int, double> Mytuple;   
int main() {   
    Mytuple c0(0, 1, 2, 3);   
  
// display contents " 0 1 2 3"   
    std::cout << " " << std::get<0>(c0);   
    std::cout << " " << std::get<1>(c0);   
    std::cout << " " << std::get<2>(c0);   
    std::cout << " " << std::get<3>(c0);   
    std::cout << std::endl;   
  
    Mytuple c1 = std::make_tuple(4, 5, 6, 7);   
  
// display contents " 4 5 6 7"   
    std::cout << " " << std::get<0>(c0);   
    std::cout << " " << std::get<1>(c0);   
    std::cout << " " << std::get<2>(c0);   
    std::cout << " " << std::get<3>(c0);   
    std::cout << std::endl;   
  
// display results of comparisons   
    std::cout << std::boolalpha << " " << (c0 > c0);   
    std::cout << std::endl;   
    std::cout << std::boolalpha << " " << (c1 > c0);   
    std::cout << std::endl;   
  
    return (0);   
}  
```  
  
```Output  
0 1 2 3  
0 1 2 3  
false  
true  
```  
  
##  <a name="op_gt_eq"></a>  operator&gt;=  
 比較 `tuple` 物件為大於或等於。  
  
```  
template <class T1, class T2, ..., class TN,  
    class U1, class U2, ..., class UN>  
bool operator>=(const tuple<T1, T2, ..., TN>& tpl1,  
    const tuple<U1, U2, ..., UN>& tpl2);
```  
  
### <a name="parameters"></a>參數  
 `TN`  
 第 N 個 tuple 項目類型。  
  
### <a name="remarks"></a>備註  
 函式會傳回 `!(tpl1 < tpl2)`。  
  
### <a name="example"></a>範例  
  
```cpp  
// std__tuple__operator_ge.cpp   
// compile with: /EHsc   
#include <tuple>   
#include <iostream>   
  
typedef std::tuple<int, double, int, double> Mytuple;   
int main() {   
    Mytuple c0(0, 1, 2, 3);   
  
// display contents " 0 1 2 3"   
    std::cout << " " << std::get<0>(c0);   
    std::cout << " " << std::get<1>(c0);   
    std::cout << " " << std::get<2>(c0);   
    std::cout << " " << std::get<3>(c0);   
    std::cout << std::endl;   
  
    Mytuple c1 = std::make_tuple(4, 5, 6, 7);   
  
// display contents " 4 5 6 7"   
    std::cout << " " << std::get<0>(c0);   
    std::cout << " " << std::get<1>(c0);   
    std::cout << " " << std::get<2>(c0);   
    std::cout << " " << std::get<3>(c0);   
    std::cout << std::endl;   
  
// display results of comparisons   
    std::cout << std::boolalpha << " " << (c0 >= c0);   
    std::cout << std::endl;   
    std::cout << std::boolalpha << " " << (c0 >= c1);   
    std::cout << std::endl;   
  
    return (0);   
}  
```  
  
```Output  
0 1 2 3  
0 1 2 3  
true  
false  
```  
  
## <a name="see-also"></a>另請參閱  
 [\<tuple>](../standard-library/tuple.md)


