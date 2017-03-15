---
title: "Concurrency 命名空間運算子 (AMP) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 77f1ae17-1eb2-480d-8fe5-66d4c24bb91e
caps.latest.revision: 9
author: mikeblome
ms.author: mblome
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: 22ba62ab8b3b4f9d14953dbab3edd8228ea85193
ms.openlocfilehash: 676f3e836082dc3286a45f8d59db83c969964058
ms.lasthandoff: 02/24/2017

---
# <a name="concurrency-namespace-operators-amp"></a>Concurrency 命名空間運算子 (AMP)
||||  
|-|-|-|  
|[operator!=](#operator_neq)|[operator%](#operator_mod)|[operator*](#operator_star)|  
|[operator+](#operator_add)|[operator-](#operator-)|[operator/](#operator_div)|  
|[operator==](#operator_eq_eq)|  
  
##  <a name="a-nameoperatoreqeqa--operator"></a><a name="operator_eq_eq"></a> operator==   
 判斷指定的引數是否相等。  
  
```  
template <
    int _Rank,  
    template <int> class _Tuple_type  
>  
bool operator== (
    const _Tuple_type<_Rank>& _Lhs,  
    const _Tuple_type<_Rank>& _Rhs) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_Rank`  
 Tuple 引數的陣序規範。  
  
 `_Lhs`  
 其中一個要比較的 tuple。  
  
 `_Rhs`  
 其中一個要比較的 tuple。  
  
### <a name="return-value"></a>傳回值  
 `true`如果 tuple 是相等。否則， `false`。  
  
##  <a name="a-nameoperatorneqa--operator"></a><a name="operator_neq"></a> operator!=   
 判斷指定的引數是否不相等。  
  
```  
template <
    int _Rank,  
    template <int> class _Tuple_type  
>  
bool operator!= (
    const _Tuple_type<_Rank>& _Lhs,  
    const _Tuple_type<_Rank>& _Rhs) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_Rank`  
 Tuple 引數的陣序規範。  
  
 `_Lhs`  
 其中一個要比較的 tuple。  
  
 `_Rhs`  
 其中一個要比較的 tuple。  
  
### <a name="return-value"></a>傳回值  
 `true`如果 tuple 不相等。否則， `false`。  
  
##  <a name="a-nameoperatoradda--operator"></a><a name="operator_add"></a>  operator+   

 計算 component-wise 指定的引數的總和。  
  
```  
template <
    int _Rank,  
    template <int> class _Tuple_type  
>  
class _Tuple_type> _Tuple_type<_Rank>   operator+(
    const _Tuple_type<_Rank>& _Lhs,  
    const _Tuple_type<_Rank>& _Rhs) restrict(amp,cpu);

 
template <
    int _Rank,  
    template <int> class _Tuple_type  
>  
class _Tuple_type> _Tuple_type<_Rank>   operator+(
    const _Tuple_type<_Rank>& _Lhs,  
    typename _Tuple_type<_Rank>::value_type _Rhs) restrict(amp,cpu);

 
template <
    int _Rank,  
    template <int> class _Tuple_type  
>  
class _Tuple_type> _Tuple_type<_Rank>   operator+(
    typename _Tuple_type<_Rank>::value_type _Lhs,  
    const _Tuple_type<_Rank>& _Rhs) restrict(amp,cpu);
```  
  
### <a name="parameters"></a>參數  
 `_Rank`  
 Tuple 引數的陣序規範。  
  
 `_Lhs`  
 其中一個加入的引數。  
  
 `_Rhs`  
 其中一個加入的引數。  
  
### <a name="return-value"></a>傳回值  
 Component-wise 指定的引數的總和。  
  
##  <a name="a-nameoperator-a--operator-"></a><a name="operator-"></a>  operator-   

 計算指定的引數的 component-wise 差異。  
  
```  
template <
    int _Rank,  
    template <int> class _Tuple_type  
>  
_Tuple_type<_Rank>   operator-(
    const _Tuple_type<_Rank>& _Lhs,  
    const _Tuple_type<_Rank>& _Rhs) restrict(amp,cpu);

 
template <
    int _Rank,  
    template <int> class _Tuple_type  
>  
_Tuple_type<_Rank>   operator-(
    const _Tuple_type<_Rank>& _Lhs,  
    typename _Tuple_type<_Rank>::value_type _Rhs) restrict(amp,cpu);

 
template <
    int _Rank,  
    template <int> class _Tuple_type  
>  
_Tuple_type<_Rank>   operator-(
    typename _Tuple_type<_Rank>::value_type _Lhs,  
    const _Tuple_type<_Rank>& _Rhs) restrict(amp,cpu);
```  
  
### <a name="parameters"></a>參數  
 `_Rank`  
 Tuple 引數的陣序規範。  
  
 `_Lhs`  
 要減去的引數。  
  
 `_Rhs`  
 要減去引數。  
  
### <a name="return-value"></a>傳回值  
 指定的引數 component-wise 差異。  
  
##  <a name="a-nameoperatorstara--operator"></a><a name="operator_star"></a>  operator*   

 計算指定的引數的 component-wise 的乘積。  
  
```  
template <
    int _Rank,  
    template <int> class _Tuple_type  
>  
_Tuple_type<_Rank>   operator*(
    const _Tuple_type<_Rank>& _Lhs,  
    typename _Tuple_type<_Rank>::value_type _Rhs) restrict(amp,cpu);

 
template <
    int _Rank,  
    template <int> class _Tuple_type  
>  
_Tuple_type<_Rank>   operator*(
    typename _Tuple_type<_Rank>::value_type _Lhs,  
    const _Tuple_type<_Rank>& _Rhs) restrict(amp, cpu);
```  
  
### <a name="parameters"></a>參數  
 `_Rank`  
 Tuple 引數的陣序規範。  
  
 `_Lhs`  
 要相乘的 tuple 的其中一個。  
  
 `_Rhs`  
 要相乘的 tuple 的其中一個。  
  
### <a name="return-value"></a>傳回值  
 指定的引數 component-wise 產品。  
  

##  <a name="a-nameoperatordiva--operator"></a><a name="operator_div"></a>  operator/   
 計算指定的引數的 component-wise 的商數。  
  
```  
template <
    int _Rank,  
    template <int> class _Tuple_type  
>  
_Tuple_type<_Rank>   operator/(
    const _Tuple_type<_Rank>& _Lhs,  
    typename _Tuple_type<_Rank>::value_type _Rhs) restrict(amp,cpu);

 
template <
    int _Rank,  
    template <int> class _Tuple_type  
>  
_Tuple_type<_Rank>   operator/(
    typename _Tuple_type<_Rank>::value_type _Lhs,  
    const _Tuple_type<_Rank>& _Rhs) restrict(amp,cpu);
```  
  
### <a name="parameters"></a>參數  
 `_Rank`  
 Tuple 引數的陣序規範。  
  
 `_Lhs`  
 要當做被除數 tuple。  
  
 `_Rhs`  
 要當做除數 tuple。  
  
### <a name="return-value"></a>傳回值  
 指定的引數 component-wise 的商數。  
  
##  <a name="a-nameoperatormoda--operator"></a><a name="operator_mod"></a>  operator%   

 計算的第一個指定的引數，第二個指定的引數的模數。  
  
```  
template <
    int _Rank,  
    template <int> class _Tuple_type  
>  
_Tuple_type<_Rank>   operator%(
    const _Tuple_type<_Rank>& _Lhs,  
    typename _Tuple_type<_Rank>::value_type _Rhs) restrict(amp,cpu);

 
template <
    int _Rank,  
    template <int> class _Tuple_type  
>  
_Tuple_type<_Rank>   operator%(
    typename _Tuple_type<_Rank>::value_type _Lhs,  
    const _Tuple_type<_Rank>& _Rhs) restrict(amp,cpu);
```  
  
### <a name="parameters"></a>參數  
 `_Rank`  
 Tuple 引數的陣序規範。  
  
 `_Lhs`  
 從中 tuple 計算模數。  
  
 `_Rhs`  
 Tuple 至模數的。  
  
### <a name="return-value"></a>傳回值  
 第一個指定的引數模數第二個指定的引數的結果。  
  
## <a name="see-also"></a>另請參閱  
 [Concurrency 命名空間](concurrency-namespace-cpp-amp.md)

