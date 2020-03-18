---
title: concurrency 命名空間運算子
ms.date: 11/04/2016
f1_keywords:
- concrt/concurrency::operator!=
- concrt/concurrency:[operator&amp;&amp
ms.assetid: 8e373f23-fc8e-49f7-82e6-ba0c57b822f8
ms.openlocfilehash: 676e1936af317a6ab19959f8fd09b1de06dfaf69
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2020
ms.locfileid: "79422140"
---
# <a name="concurrency-namespace-operators"></a>concurrency 命名空間運算子

||||
|-|-|-|
|[operator!=](#operator_neq)|[operator&amp;&amp;](#operator_amp_amp)|[operator&gt;](#operator_gt)|
|[operator&gt;=](#operator_gt_eq)|[operator&lt;](#operator_lt)|[operator&lt;=](#operator_lt_eq)|
|[operator==](#operator_eq_eq)|[operator&#124;&#124;](#operator_lor)| |

## <a name="operator_lor"></a>運算子&#124; &#124;運算子

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

當其中一個輸入工作順利完成時，成功完成的工作。 如果輸入工作屬於類型 `T`，此函式的輸出將會是 `task<std::vector<T>`。 如果輸入工作屬於類型 `void`，則輸出工作也會是 `task<void>`。

### <a name="remarks"></a>備註

如果兩個工作都取消或擲回例外狀況，則傳回的工作會以已取消狀態完成，而且其中一個例外狀況 (如果有發生) 會在您呼叫該工作上的 `get()` 或 `wait()` 時擲回。

## <a name="operator_amp_amp"></a>運算子&amp;&amp; 運算子

建立當兩個當做引數提供的工作都順利完成時，將會順利完成的工作。

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

會在兩個輸入工作都順利完成時，順利完成的工作。 如果輸入工作屬於類型 `T`，此函式的輸出將會是 `task<std::vector<T>>`。 如果輸入工作屬於類型 `void`，則輸出工作也會是 `task<void>`。

### <a name="remarks"></a>備註

如果其中一個工作已取消或擲回例外狀況，則傳回的工作將會提早完成（處於已取消狀態），而且如果您在該工作上呼叫 `get()` 或 `wait()`，則會擲回例外狀況（如果發生的話）。

## <a name="operator_eq_eq"></a>operator = = 運算子

測試運算子左邊的 `concurrent_vector` 物件是否等於右邊的 `concurrent_vector` 物件。

```cpp
template<typename T, class A1, class A2>
inline bool operator== (
    const concurrent_vector<T, A1>& _A,
    const concurrent_vector<T, A2>& _B);
```

### <a name="parameters"></a>參數

*T*<br/>
儲存在並行向量中之元素的資料類型。

*A1*<br/>
第一個 `concurrent_vector` 物件的配置器類型。

*A2*<br/>
第二個 `concurrent_vector` 物件的配置器類型。

*_A*<br/>
`concurrent_vector` 類型的物件。

*_B*<br/>
`concurrent_vector` 類型的物件。

### <a name="return-value"></a>傳回值

如果運算子左邊的並行向量等於運算子右邊的並行向量，**則為 true** ;否則**為 false**。

### <a name="remarks"></a>備註

如果兩個並行向量具有相同數目的元素，且其個別元素具有相同的值，則兩者相等。 反之則為不相等。

這個方法與其他可修改並行向量 `_A` 或 `_B`的方法而言，並不是並行安全。

## <a name="operator_neq"></a>operator！ = 運算子

測試運算子左邊的 `concurrent_vector` 物件是否不等於右邊的 `concurrent_vector` 物件。

```cpp
template<typename T, class A1, class A2>
inline bool operator!= (
    const concurrent_vector<T, A1>& _A,
    const concurrent_vector<T, A2>& _B);
```

### <a name="parameters"></a>參數

*T*<br/>
儲存在並行向量中之元素的資料類型。

*A1*<br/>
第一個 `concurrent_vector` 物件的配置器類型。

*A2*<br/>
第二個 `concurrent_vector` 物件的配置器類型。

*_A*<br/>
`concurrent_vector` 類型的物件。

*_B*<br/>
`concurrent_vector` 類型的物件。

### <a name="return-value"></a>傳回值

如果並行向量不相等，則為**true** ;如果並行向量相等，則**為 false** 。

### <a name="remarks"></a>備註

如果兩個並行向量具有相同數目的元素，且其個別元素具有相同的值，則兩者相等。 反之則為不相等。

這個方法與其他可修改並行向量 `_A` 或 `_B`的方法而言，並不是並行安全。

## <a name="operator_lt"></a>運算子&lt; 運算子

測試運算子左邊的 `concurrent_vector` 物件是否小於右邊的 `concurrent_vector` 物件。

```cpp
template<typename T, class A1, class A2>
inline bool operator<(
    const concurrent_vector<T, A1>& _A,
    const concurrent_vector<T, A2>& _B);
```

### <a name="parameters"></a>參數

*T*<br/>
儲存在並行向量中之元素的資料類型。

*A1*<br/>
第一個 `concurrent_vector` 物件的配置器類型。

*A2*<br/>
第二個 `concurrent_vector` 物件的配置器類型。

*_A*<br/>
`concurrent_vector` 類型的物件。

*_B*<br/>
`concurrent_vector` 類型的物件。

### <a name="return-value"></a>傳回值

如果運算子左邊的並行向量小於運算子右邊的並行向量，**則為 true** ;否則**為 false**。

### <a name="remarks"></a>備註

這個運算子的行為等同于 `std` 命名空間中 `vector` 類別的對等運算子。

這個方法與其他可修改並行向量 `_A` 或 `_B`的方法而言，並不是並行安全。

## <a name="operator_lt_eq"></a>運算子&lt;= 運算子

測試運算子左邊的 `concurrent_vector` 物件是否小於或等於右邊的 `concurrent_vector` 物件。

```cpp
template<typename T, class A1, class A2>
inline bool operator<= (
    const concurrent_vector<T, A1>& _A,
    const concurrent_vector<T, A2>& _B);
```

### <a name="parameters"></a>參數

*T*<br/>
儲存在並行向量中之元素的資料類型。

*A1*<br/>
第一個 `concurrent_vector` 物件的配置器類型。

*A2*<br/>
第二個 `concurrent_vector` 物件的配置器類型。

*_A*<br/>
`concurrent_vector` 類型的物件。

*_B*<br/>
`concurrent_vector` 類型的物件。

### <a name="return-value"></a>傳回值

如果運算子左邊的並行向量小於或等於運算子右邊的並行向量，**則為 true** ;否則**為 false**。

### <a name="remarks"></a>備註

這個運算子的行為等同于 `std` 命名空間中 `vector` 類別的對等運算子。

這個方法與其他可修改並行向量 `_A` 或 `_B`的方法而言，並不是並行安全。

## <a name="operator_gt"></a>運算子&gt; 運算子

測試運算子左邊的 `concurrent_vector` 物件是否大於右邊的 `concurrent_vector` 物件。

```cpp
template<typename T, class A1, class A2>
inline bool operator>(
    const concurrent_vector<T, A1>& _A,
    const concurrent_vector<T, A2>& _B);
```

### <a name="parameters"></a>參數

*T*<br/>
儲存在並行向量中之元素的資料類型。

*A1*<br/>
第一個 `concurrent_vector` 物件的配置器類型。

*A2*<br/>
第二個 `concurrent_vector` 物件的配置器類型。

*_A*<br/>
`concurrent_vector` 類型的物件。

*_B*<br/>
`concurrent_vector` 類型的物件。

### <a name="return-value"></a>傳回值

如果運算子左邊的並行向量大於運算子右邊的並行向量，**則為 true** ;否則**為 false**。

### <a name="remarks"></a>備註

這個運算子的行為等同于 `std` 命名空間中 `vector` 類別的對等運算子。

這個方法與其他可修改並行向量 `_A` 或 `_B`的方法而言，並不是並行安全。

## <a name="operator_gt_eq"></a>運算子&gt;= 運算子

測試運算子左邊的 `concurrent_vector` 物件是否大於或等於右邊的 `concurrent_vector` 物件。

```cpp
template<typename T, class A1, class A2>
inline bool operator>= (
    const concurrent_vector<T, A1>& _A,
    const concurrent_vector<T, A2>& _B);
```

### <a name="parameters"></a>參數

*T*<br/>
儲存在並行向量中之元素的資料類型。

*A1*<br/>
第一個 `concurrent_vector` 物件的配置器類型。

*A2*<br/>
第二個 `concurrent_vector` 物件的配置器類型。

*_A*<br/>
`concurrent_vector` 類型的物件。

*_B*<br/>
`concurrent_vector` 類型的物件。

### <a name="return-value"></a>傳回值

如果運算子左邊的並行向量大於或等於運算子右邊的並行向量，**則為 true** ;否則**為 false**。

### <a name="remarks"></a>備註

這個運算子的行為等同于 `std` 命名空間中 `vector` 類別的對等運算子。

這個方法與其他可修改並行向量 `_A` 或 `_B`的方法而言，並不是並行安全。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)
