---
title: concurrency 命名空間運算子
ms.date: 11/04/2016
f1_keywords:
- concrt/concurrency::operator!=
- concrt/concurrency:[operator&amp;&amp
ms.assetid: 8e373f23-fc8e-49f7-82e6-ba0c57b822f8
ms.openlocfilehash: aac43a15b09bd792118fbfe7ea51493b73b8ac9d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374387"
---
# <a name="concurrency-namespace-operators"></a>concurrency 命名空間運算子

||||
|-|-|-|
|[操作員!](#operator_neq)|[算子&amp;&amp;](#operator_amp_amp)|[算子&gt;](#operator_gt)|
|[算子&gt;=](#operator_gt_eq)|[算子&lt;](#operator_lt)|[算子&lt;=](#operator_lt_eq)|
|[運算子*](#operator_eq_eq)|[運算子&#124;&#124;](#operator_lor)| |

## <a name="operator124124-operator"></a><a name="operator_lor"></a>操作員&#124;&#124; 操作員

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

*傳回類型*<br/>
所傳回工作的類型。

*lhs*<br/>
合併至所產生工作的第一個工作。

*rhs*<br/>
合併至所產生工作的第二個工作。

### <a name="return-value"></a>傳回值

當任一輸入任務成功完成時,該任務成功完成。 如果輸入工作屬於類型 `T`，此函式的輸出將會是 `task<std::vector<T>`。 如果輸入工作屬於類型 `void`，則輸出工作也會是 `task<void>`。

### <a name="remarks"></a>備註

如果兩個工作都取消或擲回例外狀況，則傳回的工作會以已取消狀態完成，而且其中一個例外狀況 (如果有發生) 會在您呼叫該工作上的 `get()` 或 `wait()` 時擲回。

## <a name="operatorampamp-operator"></a><a name="operator_amp_amp"></a>操作員&amp;&amp;

創建一個任務,當作為參數提供的兩個任務成功完成時,該任務將成功完成。

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

*傳回類型*<br/>
所傳回工作的類型。

*lhs*<br/>
合併至所產生工作的第一個工作。

*rhs*<br/>
合併至所產生工作的第二個工作。

### <a name="return-value"></a>傳回值

會在兩個輸入工作都順利完成時，順利完成的工作。 如果輸入工作屬於類型 `T`，此函式的輸出將會是 `task<std::vector<T>>`。 如果輸入工作屬於類型 `void`，則輸出工作也會是 `task<void>`。

### <a name="remarks"></a>備註

如果其中一個任務被取消或引發異常,則返回的任務將提前完成,處於已取消狀態,如果發生異常,則在調用`get()``wait()`或執行該任務時將引發異常。

## <a name="operator-operator"></a><a name="operator_eq_eq"></a>運算子 = 運算子

測試運算子左邊的 `concurrent_vector` 物件是否等於右邊的 `concurrent_vector` 物件。

```cpp
template<typename T, class A1, class A2>
inline bool operator== (
    const concurrent_vector<T, A1>& _A,
    const concurrent_vector<T, A2>& _B);
```

### <a name="parameters"></a>參數

*T*<br/>
存儲在併發向量中的元素的數據類型。

*A1*<br/>
第一`concurrent_vector`個對象的分配器類型。

*A2*<br/>
第二`concurrent_vector`個對象的分配器類型。

*_A*<br/>
`concurrent_vector` 類型的物件。

*_B*<br/>
`concurrent_vector` 類型的物件。

### <a name="return-value"></a>傳回值

如果運算元左側的併發向量等於運算符右側的併發向量,**則為 true;** 否則**錯誤**。

### <a name="remarks"></a>備註

如果兩個併發向量具有相同的元素數,並且其各自的元素具有相同的值,則它們相等。 反之則為不相等。

對於可以修改併發向量`_A``_B`或的其他方法,此方法並不併發安全。

## <a name="operator-operator"></a><a name="operator_neq"></a>操作員!= 操作員

測試運算子左邊的 `concurrent_vector` 物件是否不等於右邊的 `concurrent_vector` 物件。

```cpp
template<typename T, class A1, class A2>
inline bool operator!= (
    const concurrent_vector<T, A1>& _A,
    const concurrent_vector<T, A2>& _B);
```

### <a name="parameters"></a>參數

*T*<br/>
存儲在併發向量中的元素的數據類型。

*A1*<br/>
第一`concurrent_vector`個對象的分配器類型。

*A2*<br/>
第二`concurrent_vector`個對象的分配器類型。

*_A*<br/>
`concurrent_vector` 類型的物件。

*_B*<br/>
`concurrent_vector` 類型的物件。

### <a name="return-value"></a>傳回值

如果併發向量不相等,**則為 true;** 如果併發向量相等,**則為 false。**

### <a name="remarks"></a>備註

如果兩個併發向量具有相同的元素數,並且其各自的元素具有相同的值,則它們相等。 反之則為不相等。

對於可以修改併發向量`_A``_B`或的其他方法,此方法並不併發安全。

## <a name="operatorlt-operator"></a><a name="operator_lt"></a>操作員&lt;

測試運算子左邊的 `concurrent_vector` 物件是否小於右邊的 `concurrent_vector` 物件。

```cpp
template<typename T, class A1, class A2>
inline bool operator<(
    const concurrent_vector<T, A1>& _A,
    const concurrent_vector<T, A2>& _B);
```

### <a name="parameters"></a>參數

*T*<br/>
存儲在併發向量中的元素的數據類型。

*A1*<br/>
第一`concurrent_vector`個對象的分配器類型。

*A2*<br/>
第二`concurrent_vector`個對象的分配器類型。

*_A*<br/>
`concurrent_vector` 類型的物件。

*_B*<br/>
`concurrent_vector` 類型的物件。

### <a name="return-value"></a>傳回值

如果運算元左側的併發向量小於運算符右側的併發向量,**則為 true;** 否則**錯誤**。

### <a name="remarks"></a>備註

此運算符的行為與`vector``std`命名空間中類的等效運算符相同。

對於可以修改併發向量`_A``_B`或的其他方法,此方法並不併發安全。

## <a name="operatorlt-operator"></a><a name="operator_lt_eq"></a>運算子&lt;= 運算子

測試運算子左邊的 `concurrent_vector` 物件是否小於或等於右邊的 `concurrent_vector` 物件。

```cpp
template<typename T, class A1, class A2>
inline bool operator<= (
    const concurrent_vector<T, A1>& _A,
    const concurrent_vector<T, A2>& _B);
```

### <a name="parameters"></a>參數

*T*<br/>
存儲在併發向量中的元素的數據類型。

*A1*<br/>
第一`concurrent_vector`個對象的分配器類型。

*A2*<br/>
第二`concurrent_vector`個對象的分配器類型。

*_A*<br/>
`concurrent_vector` 類型的物件。

*_B*<br/>
`concurrent_vector` 類型的物件。

### <a name="return-value"></a>傳回值

如果運算元左側的併發向量小於或等於運算符右側的併發向量,**則為 true;** 否則**錯誤**。

### <a name="remarks"></a>備註

此運算符的行為與`vector``std`命名空間中類的等效運算符相同。

對於可以修改併發向量`_A``_B`或的其他方法,此方法並不併發安全。

## <a name="operatorgt-operator"></a><a name="operator_gt"></a>操作員&gt;

測試運算子左邊的 `concurrent_vector` 物件是否大於右邊的 `concurrent_vector` 物件。

```cpp
template<typename T, class A1, class A2>
inline bool operator>(
    const concurrent_vector<T, A1>& _A,
    const concurrent_vector<T, A2>& _B);
```

### <a name="parameters"></a>參數

*T*<br/>
存儲在併發向量中的元素的數據類型。

*A1*<br/>
第一`concurrent_vector`個對象的分配器類型。

*A2*<br/>
第二`concurrent_vector`個對象的分配器類型。

*_A*<br/>
`concurrent_vector` 類型的物件。

*_B*<br/>
`concurrent_vector` 類型的物件。

### <a name="return-value"></a>傳回值

如果運算元左側的併發向量大於運算符右側的併發向量,**則為 true;** 否則**錯誤**。

### <a name="remarks"></a>備註

此運算符的行為與`vector``std`命名空間中類的等效運算符相同。

對於可以修改併發向量`_A``_B`或的其他方法,此方法並不併發安全。

## <a name="operatorgt-operator"></a><a name="operator_gt_eq"></a>運算子&gt;= 運算子

測試運算子左邊的 `concurrent_vector` 物件是否大於或等於右邊的 `concurrent_vector` 物件。

```cpp
template<typename T, class A1, class A2>
inline bool operator>= (
    const concurrent_vector<T, A1>& _A,
    const concurrent_vector<T, A2>& _B);
```

### <a name="parameters"></a>參數

*T*<br/>
存儲在併發向量中的元素的數據類型。

*A1*<br/>
第一`concurrent_vector`個對象的分配器類型。

*A2*<br/>
第二`concurrent_vector`個對象的分配器類型。

*_A*<br/>
`concurrent_vector` 類型的物件。

*_B*<br/>
`concurrent_vector` 類型的物件。

### <a name="return-value"></a>傳回值

如果運算元左側的併發向量大於或等於運算符右側的併發向量,**則為 true;** 否則**錯誤**。

### <a name="remarks"></a>備註

此運算符的行為與`vector``std`命名空間中類的等效運算符相同。

對於可以修改併發向量`_A``_B`或的其他方法,此方法並不併發安全。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)
