---
title: concurrency 命名空間運算子
ms.date: 11/04/2016
f1_keywords:
- concrt/concurrency::operator!=
- concrt/concurrency:[operator&amp;&amp
ms.assetid: 8e373f23-fc8e-49f7-82e6-ba0c57b822f8
ms.openlocfilehash: 97553276a7c4ff687dd8bea4627f943d5666b2e9
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88836007"
---
# <a name="concurrency-namespace-operators"></a>concurrency 命名空間運算子

:::row:::
   :::column span="":::
      [`operator||`](#operator_lor)\
      [`operator&&`](#operator_amp_amp)
   :::column-end:::
   :::column span="":::
      [`operator==`](#operator_eq_eq)\
      [`operator!=`](#operator_neq)
   :::column-end:::
   :::column span="":::
      [`operator<`](#operator_lt)\
      [`operator<=`](#operator_lt_eq)
   :::column-end:::
   :::column span="":::
      [`operator>`](#operator_gt)\
      [`operator>=`](#operator_gt_eq)
   :::column-end:::
:::row-end:::

## <a name="operator124124-operator"></a><a name="operator_lor"></a> 運算子&#124;&#124; 運算子

建立工作，這個工作將會在兩個當做引數提供的任一工作已順利完成時成功完成。

```cpp
template<typename ReturnType>
task<ReturnType> operator||(
    const task<ReturnType>& lhs,
    const task<ReturnType>& rhs);

template<typename ReturnType>
task<std::vector<ReturnType>> operator||(
    const task<std::vector<ReturnType>>& lhs,
    const task<ReturnType>& rhs);

template<typename ReturnType>
task<std::vector<ReturnType>> operator||(
    const task<ReturnType>& lhs,
    const task<std::vector<ReturnType>>& rhs);

inline task<void> operator||(
    const task<void>& lhs,
    const task<void>& rhs);
```

### <a name="parameters"></a>參數

*ReturnType*<br/>
所傳回工作的類型。

*lhs*<br/>
合併至所產生工作的第一個工作。

*rhs*<br/>
合併至所產生工作的第二個工作。

### <a name="return-value"></a>傳回值

當其中一個輸入工作成功完成時，就會順利完成的工作。 如果輸入工作屬於類型 `T`，此函式的輸出將會是 `task<std::vector<T>`。 如果輸入工作的類型為 **`void`** ，則輸出工作也會是 `task<void>` 。

### <a name="remarks"></a>備註

如果兩個工作都取消或擲回例外狀況，則傳回的工作會以已取消狀態完成，而且其中一個例外狀況 (如果有發生) 會在您呼叫該工作上的 `get()` 或 `wait()` 時擲回。

## <a name="operatorampamp-operator"></a><a name="operator_amp_amp"></a>運算子 &amp; &amp; 運算子

建立工作，當提供做為引數的兩個工作順利完成時，將會順利完成。

```cpp
template<typename ReturnType>
task<std::vector<ReturnType>>  operator&&(
    const task<ReturnType>& lhs,
    const task<ReturnType>& rhs);

template<typename ReturnType>
task<std::vector<ReturnType>>  operator&&(
    const task<std::vector<ReturnType>>& lhs,
    const task<ReturnType>& rhs);

template<typename ReturnType>
task<std::vector<ReturnType>>  operator&&(
    const task<ReturnType>& lhs,
    const task<std::vector<ReturnType>>& rhs);

template<typename ReturnType>
task<std::vector<ReturnType>>  operator&&(
    const task<std::vector<ReturnType>>& lhs,
    const task<std::vector<ReturnType>>& rhs);

inline task<void>  operator&&(
    const task<void>& lhs,
    const task<void>& rhs);
```

### <a name="parameters"></a>參數

*ReturnType*<br/>
所傳回工作的類型。

*lhs*<br/>
合併至所產生工作的第一個工作。

*rhs*<br/>
合併至所產生工作的第二個工作。

### <a name="return-value"></a>傳回值

會在兩個輸入工作都順利完成時，順利完成的工作。 如果輸入工作屬於類型 `T`，此函式的輸出將會是 `task<std::vector<T>>`。 如果輸入工作的類型為 **`void`** ，則輸出工作也會是 `task<void>` 。

### <a name="remarks"></a>備註

如果其中一項工作已取消或擲回例外狀況，則傳回的工作會提早完成，而且如果發生例外狀況，則如果您在該工作上呼叫或，將會擲回例外狀況（如果有的話） `get()` `wait()` 。

## <a name="operator-operator"></a><a name="operator_eq_eq"></a> operator = = 運算子

測試運算子左邊的 `concurrent_vector` 物件是否等於右邊的 `concurrent_vector` 物件。

```cpp
template<typename T, class A1, class A2>
inline bool operator== (
    const concurrent_vector<T, A1>& _A,
    const concurrent_vector<T, A2>& _B);
```

### <a name="parameters"></a>參數

*T*<br/>
並行向量中儲存之元素的資料類型。

*A1*<br/>
第一個物件的配置器類型 `concurrent_vector` 。

*A2*<br/>
第二個物件的配置器類型 `concurrent_vector` 。

*_A*<br/>
`concurrent_vector` 類型的物件。

*_B*<br/>
`concurrent_vector` 類型的物件。

### <a name="return-value"></a>傳回值

**`true`** 如果運算子左邊的並行向量等於運算子右邊的並行向量，則為，否則為 **`false`** 。

### <a name="remarks"></a>備註

如果兩個並行向量具有相同數目的元素，且其個別元素的值相同，則兩個並行向量相等。 反之則為不相等。

這種方法對於其他可修改其中一個並行向量或的方法而言，並不是並行安全的 `_A` `_B` 。

## <a name="operator-operator"></a><a name="operator_neq"></a> operator！ = 運算子

測試運算子左邊的 `concurrent_vector` 物件是否不等於右邊的 `concurrent_vector` 物件。

```cpp
template<typename T, class A1, class A2>
inline bool operator!= (
    const concurrent_vector<T, A1>& _A,
    const concurrent_vector<T, A2>& _B);
```

### <a name="parameters"></a>參數

*T*<br/>
並行向量中儲存之元素的資料類型。

*A1*<br/>
第一個物件的配置器類型 `concurrent_vector` 。

*A2*<br/>
第二個物件的配置器類型 `concurrent_vector` 。

*_A*<br/>
`concurrent_vector` 類型的物件。

*_B*<br/>
`concurrent_vector` 類型的物件。

### <a name="return-value"></a>傳回值

**`true`** 如果並行向量不相等; **`false`** 如果並行向量相等。

### <a name="remarks"></a>備註

如果兩個並行向量具有相同數目的元素，且其個別元素的值相同，則兩個並行向量相等。 反之則為不相等。

這種方法對於其他可修改其中一個並行向量或的方法而言，並不是並行安全的 `_A` `_B` 。

## <a name="operatorlt-operator"></a><a name="operator_lt"></a> 運算子 &lt; 運算子

測試運算子左邊的 `concurrent_vector` 物件是否小於右邊的 `concurrent_vector` 物件。

```cpp
template<typename T, class A1, class A2>
inline bool operator<(
    const concurrent_vector<T, A1>& _A,
    const concurrent_vector<T, A2>& _B);
```

### <a name="parameters"></a>參數

*T*<br/>
並行向量中儲存之元素的資料類型。

*A1*<br/>
第一個物件的配置器類型 `concurrent_vector` 。

*A2*<br/>
第二個物件的配置器類型 `concurrent_vector` 。

*_A*<br/>
`concurrent_vector` 類型的物件。

*_B*<br/>
`concurrent_vector` 類型的物件。

### <a name="return-value"></a>傳回值

**`true`** 如果運算子左邊的並行向量小於運算子右邊的並行向量，則為。否則為 **`false`** 。

### <a name="remarks"></a>備註

這個運算子的行為等同于 `vector` 命名空間中類別的對等運算子 `std` 。

這種方法對於其他可修改其中一個並行向量或的方法而言，並不是並行安全的 `_A` `_B` 。

## <a name="operatorlt-operator"></a><a name="operator_lt_eq"></a> operator &lt; = 運算子

測試運算子左邊的 `concurrent_vector` 物件是否小於或等於右邊的 `concurrent_vector` 物件。

```cpp
template<typename T, class A1, class A2>
inline bool operator<= (
    const concurrent_vector<T, A1>& _A,
    const concurrent_vector<T, A2>& _B);
```

### <a name="parameters"></a>參數

*T*<br/>
並行向量中儲存之元素的資料類型。

*A1*<br/>
第一個物件的配置器類型 `concurrent_vector` 。

*A2*<br/>
第二個物件的配置器類型 `concurrent_vector` 。

*_A*<br/>
`concurrent_vector` 類型的物件。

*_B*<br/>
`concurrent_vector` 類型的物件。

### <a name="return-value"></a>傳回值

**`true`** 如果運算子左邊的並行向量小於或等於運算子右邊的並行向量，則為，否則為 **`false`** 。

### <a name="remarks"></a>備註

這個運算子的行為等同于 `vector` 命名空間中類別的對等運算子 `std` 。

這種方法對於其他可修改其中一個並行向量或的方法而言，並不是並行安全的 `_A` `_B` 。

## <a name="operatorgt-operator"></a><a name="operator_gt"></a> 運算子 &gt; 運算子

測試運算子左邊的 `concurrent_vector` 物件是否大於右邊的 `concurrent_vector` 物件。

```cpp
template<typename T, class A1, class A2>
inline bool operator>(
    const concurrent_vector<T, A1>& _A,
    const concurrent_vector<T, A2>& _B);
```

### <a name="parameters"></a>參數

*T*<br/>
並行向量中儲存之元素的資料類型。

*A1*<br/>
第一個物件的配置器類型 `concurrent_vector` 。

*A2*<br/>
第二個物件的配置器類型 `concurrent_vector` 。

*_A*<br/>
`concurrent_vector` 類型的物件。

*_B*<br/>
`concurrent_vector` 類型的物件。

### <a name="return-value"></a>傳回值

**`true`** 如果運算子左邊的並行向量大於運算子右邊的並行向量，則為。否則為 **`false`** 。

### <a name="remarks"></a>備註

這個運算子的行為等同于 `vector` 命名空間中類別的對等運算子 `std` 。

這種方法對於其他可修改其中一個並行向量或的方法而言，並不是並行安全的 `_A` `_B` 。

## <a name="operatorgt-operator"></a><a name="operator_gt_eq"></a> operator &gt; = 運算子

測試運算子左邊的 `concurrent_vector` 物件是否大於或等於右邊的 `concurrent_vector` 物件。

```cpp
template<typename T, class A1, class A2>
inline bool operator>= (
    const concurrent_vector<T, A1>& _A,
    const concurrent_vector<T, A2>& _B);
```

### <a name="parameters"></a>參數

*T*<br/>
並行向量中儲存之元素的資料類型。

*A1*<br/>
第一個物件的配置器類型 `concurrent_vector` 。

*A2*<br/>
第二個物件的配置器類型 `concurrent_vector` 。

*_A*<br/>
`concurrent_vector` 類型的物件。

*_B*<br/>
`concurrent_vector` 類型的物件。

### <a name="return-value"></a>傳回值

**`true`** 如果運算子左邊的並行向量大於或等於運算子右邊的並行向量，則為，否則為 **`false`** 。

### <a name="remarks"></a>備註

這個運算子的行為等同于 `vector` 命名空間中類別的對等運算子 `std` 。

這種方法對於其他可修改其中一個並行向量或的方法而言，並不是並行安全的 `_A` `_B` 。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)
