---
title: Concurrency 命名空間運算子 (AMP)
ms.date: 11/04/2016
ms.assetid: 77f1ae17-1eb2-480d-8fe5-66d4c24bb91e
ms.openlocfilehash: 1b6353e1edbe216dcb8aa5a342e139d826b82c6c
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88845337"
---
# <a name="concurrency-namespace-operators-amp"></a>Concurrency 命名空間運算子 (AMP)

:::row:::
   :::column span="":::
      [`operator==`](#operator_eq_eq)\
      [`operator!=`](#operator_neq)
   :::column-end:::
   :::column span="":::
      [`operator+`](#operator_add)\
      [`operator-`](#operator-)
   :::column-end:::
   :::column span="":::
      [`operator*`](#operator_star)\
      [`operator/`](#operator_div)
   :::column-end:::
   :::column span="":::
      [`operator%`](#operator_mod)
   :::column-end:::
:::row-end:::

## <a name="operator"></a><a name="operator_eq_eq"></a> operator = =

判斷指定的引數是否相等。

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
元組引數的順位。

*_Lhs*<br/>
其中一個要比較的元組。

*_Rhs*<br/>
其中一個要比較的元組。

### <a name="return-value"></a>傳回值

**`true`** 如果元組相等;否則為 **`false`** 。

## <a name="operator"></a><a name="operator_neq"></a> operator！ =

判斷指定的引數是否不相等。

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
元組引數的順位。

*_Lhs*<br/>
其中一個要比較的元組。

*_Rhs*<br/>
其中一個要比較的元組。

### <a name="return-value"></a>傳回值

**`true`** 如果元組不相等;否則為 **`false`** 。

## <a name="operator"></a><a name="operator_add"></a> 運算子 +

計算指定引數的元件成對總和。

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
元組引數的順位。

*_Lhs*<br/>
要加入的其中一個引數。

*_Rhs*<br/>
要加入的其中一個引數。

### <a name="return-value"></a>傳回值

指定引數的元件的總和。

## <a name="operator-"></a><a name="operator-"></a> 運算子

計算指定引數之間的元件方面差異。

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
元組引數的順位。

*_Lhs*<br/>
要從中減去的引數。

*_Rhs*<br/>
要減去的引數。

### <a name="return-value"></a>傳回值

指定引數之間的元件方面差異。

## <a name="operator"></a><a name="operator_star"></a> 運算子

計算指定引數的元件乘積。

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
元組引數的順位。

*_Lhs*<br/>
其中一個要相乘的元組。

*_Rhs*<br/>
其中一個要相乘的元組。

### <a name="return-value"></a>傳回值

指定引數的元件產品。

## <a name="operator"></a><a name="operator_div"></a> 運算子

計算指定引數的元件的商。

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
元組引數的順位。

*_Lhs*<br/>
要分割的元組。

*_Rhs*<br/>
要除以的元組。

### <a name="return-value"></a>傳回值

指定之引數的元件的商。

## <a name="operator"></a><a name="operator_mod"></a> 運算子

依第二個指定的引數，計算第一個指定引數的模數。

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
元組引數的順位。

*_Lhs*<br/>
從中計算模數的元組。

*_Rhs*<br/>
要做為模數依據的元組。

### <a name="return-value"></a>傳回值

第一個指定引數的結果會模數第二個指定的引數。

## <a name="see-also"></a>另請參閱

[Concurrency 命名空間](concurrency-namespace-cpp-amp.md)
