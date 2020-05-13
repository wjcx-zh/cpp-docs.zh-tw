---
title: Concurrency 命名空間運算子 (AMP)
ms.date: 11/04/2016
ms.assetid: 77f1ae17-1eb2-480d-8fe5-66d4c24bb91e
ms.openlocfilehash: c4086029b71d71091a12b9b6023cc6098faf2f85
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376298"
---
# <a name="concurrency-namespace-operators-amp"></a>Concurrency 命名空間運算子 (AMP)

||||
|-|-|-|
|[操作員!](#operator_neq)|[操作員百分比](#operator_mod)|[運算子*](#operator_star)|
|[運算子*](#operator_add)|[操作員-](#operator-)|[操作員/](#operator_div)|
|[運算子*](#operator_eq_eq)|

## <a name="operator"></a><a name="operator_eq_eq"></a>運算子*

確定指定的參數是否相等。

```cpp
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
元組參數的排名。

*_Lhs*<br/>
要比較的元數之一。

*_Rhs*<br/>
要比較的元數之一。

### <a name="return-value"></a>傳回值

如果元數相等,**則為 true;** 否則,**假**。

## <a name="operator"></a><a name="operator_neq"></a>操作員!

確定指定的參數是否不相等。

```cpp
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
元組參數的排名。

*_Lhs*<br/>
要比較的元數之一。

*_Rhs*<br/>
要比較的元數之一。

### <a name="return-value"></a>傳回值

如果元結不相等,**則為 true;** 否則,**假**。

## <a name="operator"></a><a name="operator_add"></a>運算子*

計算指定參數的元件級總和。

```cpp
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
元組參數的排名。

*_Lhs*<br/>
要添加的參數之一。

*_Rhs*<br/>
要添加的參數之一。

### <a name="return-value"></a>傳回值

指定參數的元件與

## <a name="operator-"></a><a name="operator-"></a>操作員-

計算指定參數之間的元件差異。

```cpp
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
元組參數的排名。

*_Lhs*<br/>
要從中減去的參數。

*_Rhs*<br/>
要減去的參數。

### <a name="return-value"></a>傳回值

指定參數之間的元件差異。

## <a name="operator"></a><a name="operator_star"></a>運算子*

計算指定參數的元件級積。

```cpp
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
元組參數的排名。

*_Lhs*<br/>
要乘法的元數之一。

*_Rhs*<br/>
要乘法的元數之一。

### <a name="return-value"></a>傳回值

指定參數的元件級積。

## <a name="operator"></a><a name="operator_div"></a>操作員/

計算指定參數的按元件商。

```cpp
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
元組參數的排名。

*_Lhs*<br/>
要分割的元組。

*_Rhs*<br/>
要除以的元組。

### <a name="return-value"></a>傳回值

指定參數的元件商。

## <a name="operator"></a><a name="operator_mod"></a>操作員百分比

計算第二個指定參數的第一個指定參數的模數。

```cpp
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
元組參數的排名。

*_Lhs*<br/>
計算莫杜洛的元組。

*_Rhs*<br/>
元組通過。

### <a name="return-value"></a>傳回值

第一個指定參數的結果調製第二個指定的參數。

## <a name="see-also"></a>另請參閱

[併發命名空間](concurrency-namespace-cpp-amp.md)
