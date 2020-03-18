---
title: Concurrency 命名空間運算子 (AMP)
ms.date: 11/04/2016
ms.assetid: 77f1ae17-1eb2-480d-8fe5-66d4c24bb91e
ms.openlocfilehash: 3b536f75e4ef6405b60d45e89290a7d97a01707d
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2020
ms.locfileid: "79419235"
---
# <a name="concurrency-namespace-operators-amp"></a>Concurrency 命名空間運算子 (AMP)

||||
|-|-|-|
|[operator!=](#operator_neq)|[operator%](#operator_mod)|[operator*](#operator_star)|
|[operator+](#operator_add)|[operator-](#operator-)|[operator/](#operator_div)|
|[operator==](#operator_eq_eq)|

## <a name="operator_eq_eq"></a> operator==

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
元組引數的次序。

*_Lhs*<br/>
其中一個要比較的元組。

*_Rhs*<br/>
其中一個要比較的元組。

### <a name="return-value"></a>傳回值

如果元組相等，則為**true** ;否則**為 false**。

## <a name="operator_neq"></a> operator!=

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
元組引數的次序。

*_Lhs*<br/>
其中一個要比較的元組。

*_Rhs*<br/>
其中一個要比較的元組。

### <a name="return-value"></a>傳回值

如果元組不相等，則為**true** ;否則**為 false**。

## <a name="operator_add"></a>  operator+

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
元組引數的次序。

*_Lhs*<br/>
要加入的其中一個引數。

*_Rhs*<br/>
要加入的其中一個引數。

### <a name="return-value"></a>傳回值

指定引數的元件成對總和。

## <a name="operator-"></a>  operator-

計算指定引數之間的元件取向差異。

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
元組引數的次序。

*_Lhs*<br/>
要減去的引數。

*_Rhs*<br/>
要減去的引數。

### <a name="return-value"></a>傳回值

指定引數之間的元件取向差異。

## <a name="operator_star"></a>  operator*

計算指定引數的元件產品。

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
元組引數的次序。

*_Lhs*<br/>
要相乘的其中一個元組。

*_Rhs*<br/>
要相乘的其中一個元組。

### <a name="return-value"></a>傳回值

指定引數的元件產品。

## <a name="operator_div"></a>  operator/

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
元組引數的次序。

*_Lhs*<br/>
要分割的元組。

*_Rhs*<br/>
要除以的元組。

### <a name="return-value"></a>傳回值

指定引數的元件的商。

## <a name="operator_mod"></a>  operator%

以第二個指定的引數來計算第一個指定引數的模數。

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
元組引數的次序。

*_Lhs*<br/>
用來計算模數的元組。

*_Rhs*<br/>
要做為模數依據的元組。

### <a name="return-value"></a>傳回值

第一個指定引數的結果會模數第二個指定的引數。

## <a name="see-also"></a>另請參閱

[Concurrency 命名空間](concurrency-namespace-cpp-amp.md)
