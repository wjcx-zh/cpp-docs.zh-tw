---
title: Concurrency 命名空間運算子 (AMP) |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: 77f1ae17-1eb2-480d-8fe5-66d4c24bb91e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8d3bb77599fc81fa29f2c8155a6fd491ed2d639c
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33686704"
---
# <a name="concurrency-namespace-operators-amp"></a>Concurrency 命名空間運算子 (AMP)
||||  
|-|-|-|  
|[operator!=](#operator_neq)|[operator%](#operator_mod)|[operator*](#operator_star)|  
|[operator+](#operator_add)|[operator-](#operator-)|[operator/](#operator_div)|  
|[operator==](#operator_eq_eq)|  
  
##  <a name="operator_eq_eq"></a> operator==   
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
 Tuple 引數的順位。  
  
 `_Lhs`  
 其中一個要比較的 tuple。  
  
 `_Rhs`  
 其中一個要比較的 tuple。  
  
### <a name="return-value"></a>傳回值  
 `true` 如果 tuple 相等;否則， `false`。  
  
##  <a name="operator_neq"></a> operator!=   
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
 Tuple 引數的順位。  
  
 `_Lhs`  
 其中一個要比較的 tuple。  
  
 `_Rhs`  
 其中一個要比較的 tuple。  
  
### <a name="return-value"></a>傳回值  
 `true` 如果 tuple 不相等。否則， `false`。  
  
##  <a name="operator_add"></a>  operator+   

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
 Tuple 引數的順位。  
  
 `_Lhs`  
 要加入引數的其中一個。  
  
 `_Rhs`  
 要加入引數的其中一個。  
  
### <a name="return-value"></a>傳回值  
 指定的引數 component-wise 的總和。  
  
##  <a name="operator-"></a>  operator-   

 計算指定的引數之間的 component-wise 差異。  
  
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
 Tuple 引數的順位。  
  
 `_Lhs`  
 要減去的引數。  
  
 `_Rhs`  
 要減去引數。  
  
### <a name="return-value"></a>傳回值  
 指定的引數 component-wise 差異。  
  
##  <a name="operator_star"></a>  operator*   

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
 Tuple 引數的順位。  
  
 `_Lhs`  
 其中一個要相乘的 tuple。  
  
 `_Rhs`  
 其中一個要相乘的 tuple。  
  
### <a name="return-value"></a>傳回值  
 指定的引數 component-wise 產品。  
  

##  <a name="operator_div"></a>  operator/   
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
 Tuple 引數的順位。  
  
 `_Lhs`  
 要當做被除數 tuple。  
  
 `_Rhs`  
 做為除數 tuple。  
  
### <a name="return-value"></a>傳回值  
 指定的引數 component-wise 的商數。  
  
##  <a name="operator_mod"></a>  operator%   

 會計算第二個指定的引數的第一個指定的引數的模數。  
  
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
 Tuple 引數的順位。  
  
 `_Lhs`  
 從中 tuple 計算模數。  
  
 `_Rhs`  
 Tuple 來模數所。  
  
### <a name="return-value"></a>傳回值  
 第一個指定的引數模數第二個指定的引數的結果。  
  
## <a name="see-also"></a>另請參閱  
 [concurrency 命名空間 ](concurrency-namespace-cpp-amp.md)
