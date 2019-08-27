---
title: '&lt;variant&gt;運算子'
ms.date: 04/04/2019
f1_keywords:
- variant/std::operator!=
- variant/std::operator==
- variant/std::operatoroperator&gt;
- variant/std::operatoroperator&gt=;
- variant/std::operatoroperator&lt;
- variant/std::operatoroperator&lt;=
helpviewer_keywords:
- std::operator!= (variant)
- std::operator== (variant)
- std::operatoroperator&gt; (variant)
- std::operatoroperator&gt=; (variant)
- std::operatoroperator&lt; (variant)
- std::operatoroperator&lt;= (variant)
ms.openlocfilehash: 0c4042ca1d89f9835b32924b268ef17a56619009
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/16/2019
ms.locfileid: "68268560"
---
# <a name="ltvariantgt-operators"></a>&lt;variant&gt;運算子

## <a name="op_eq_eq"></a> 運算子 = =

測試運算子左邊的轉送清單物件是否等於右邊的轉送清單物件。

```cpp
template <class... Types>
    constexpr bool operator==(const variant<Types...>&, const variant<Types...>&);
```

## <a name="op_neq"></a> 運算子 ！ =

測試運算子左邊的轉送清單物件是否不等於右邊的轉送清單物件。

```cpp
template <class... Types>
    constexpr bool operator!=(const variant<Types...>&, const variant<Types...>&);
```

## <a name="op_lt"></a> 運算子&lt;

測試運算子左邊的轉送清單物件是否小於右邊的轉送清單物件。

```cpp
template <class... Types>
    constexpr bool operator<(const variant<Types...>&, const variant<Types...>&);
```

## <a name="op_lt_eq"></a> 運算子&lt;=

測試運算子左邊的轉送清單物件是否小於或等於右邊的轉送清單物件。

```cpp
template <class... Types>
    constexpr bool operator<=(const variant<Types...>&, const variant<Types...>&);
```

## <a name="op_gt"></a> 運算子&gt;

測試運算子左邊的轉送清單物件是否大於右邊的轉送清單物件。

```cpp
template <class... Types> constexpr
    bool operator>(const variant<Types...>&, const variant<Types...>&);
```

## <a name="op_gt_eq"></a> 運算子&gt;=

測試運算子左邊的轉送清單物件是否大於或等於右邊的轉送清單物件。

```cpp
template <class... Types> constexpr
    bool operator>=(const variant<Types...>&, const variant<Types...>&);
```
