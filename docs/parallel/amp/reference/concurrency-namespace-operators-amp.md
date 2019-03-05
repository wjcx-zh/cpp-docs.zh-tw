---
title: Concurrency 命名空間運算子 (AMP)
ms.date: 11/04/2016
ms.assetid: 77f1ae17-1eb2-480d-8fe5-66d4c24bb91e
ms.openlocfilehash: e2957aa84ffbf420dcf2672359a442b754866649
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57283341"
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

*_Rank*<br/>
Tuple 引數的順位。

*_Lhs*<br/>
其中一個要比較的 tuple。

*_Rhs*<br/>
其中一個要比較的 tuple。

### <a name="return-value"></a>傳回值

**真**如果 tuple 相等，否則**false**。

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

*_Rank*<br/>
Tuple 引數的順位。

*_Lhs*<br/>
其中一個要比較的 tuple。

*_Rhs*<br/>
其中一個要比較的 tuple。

### <a name="return-value"></a>傳回值

**真**如果 tuple 不相等，否則**false**。

##  <a name="operator_add"></a>  operator+

計算指定的引數的整體元件總和。

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

*_Rank*<br/>
Tuple 引數的順位。

*_Lhs*<br/>
其中一個加入的引數。

*_Rhs*<br/>
其中一個加入的引數。

### <a name="return-value"></a>傳回值

指定的引數的整體元件總和。

##  <a name="operator-"></a>  operator-

計算指定的引數之間的整體元件差值。

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

*_Rank*<br/>
Tuple 引數的順位。

*_Lhs*<br/>
要從中減去的引數。

*_Rhs*<br/>
要減去的引數。

### <a name="return-value"></a>傳回值

指定的引數之間的整體元件差值。

##  <a name="operator_star"></a>  operator*

計算指定的引數的整體元件乘積。

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

*_Rank*<br/>
Tuple 引數的順位。

*_Lhs*<br/>
其中一個要相乘的 tuple。

*_Rhs*<br/>
其中一個要相乘的 tuple。

### <a name="return-value"></a>傳回值

指定的引數分量方向上的產品。

##  <a name="operator_div"></a>  operator/

計算指定的引數的整體元件商數。

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

*_Rank*<br/>
Tuple 引數的順位。

*_Lhs*<br/>
要當做被除數的 tuple。

*_Rhs*<br/>
要除以的元組。

### <a name="return-value"></a>傳回值

指定的引數在分量方向上的商。

##  <a name="operator_mod"></a>  operator%

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

*_Rank*<br/>
Tuple 引數的順位。

*_Lhs*<br/>
Tuple 從中計算模數。

*_Rhs*<br/>
要的元組模數的。

### <a name="return-value"></a>傳回值

第一個指定的引數模數第二個指定的引數的結果。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間 ](concurrency-namespace-cpp-amp.md)
