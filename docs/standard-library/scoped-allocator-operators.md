---
title: '&lt;scoped_allocator&gt; 運算子'
ms.date: 11/04/2016
f1_keywords:
- scoped_allocator/std::operator!=
- scoped_allocator/std::operator==
ms.assetid: 4dfe0805-cc6e-479f-887f-a1c164f73837
ms.openlocfilehash: 45da89793c3f4ea131404fc3392413e7aea9ef3e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373386"
---
# <a name="ltscoped_allocatorgt-operators"></a>&lt;scoped_allocator&gt; 運算子

|||
|-|-|
|[操作員!](#op_neq)|[運算子*](#op_eq_eq)|

## <a name="operator"></a><a name="op_neq"></a>操作員!

測試兩個 `scoped_allocator_adaptor` 物件是否不相等。

```cpp
template <class Outer, class... Inner>
bool operator!=(
    const scoped_allocator_adaptor<Outer, Inner...>& left,
    const scoped_allocator_adaptor<Outer, Inner...>& right) noexcept;
```

### <a name="parameters"></a>參數

*離開*\
左 `scoped_allocator_adaptor` 物件。

*對*\
右 `scoped_allocator_adaptor` 物件。

### <a name="return-value"></a>傳回值

`!(left == right)`

## <a name="operator"></a><a name="op_eq_eq"></a>運算子*

測試兩個 `scoped_allocator_adaptor` 物件是否相等。

```cpp
template <class Outer, class... Inner>
bool operator==(
    const scoped_allocator_adaptor<Outer, Inner...>& left,
    const scoped_allocator_adaptor<Outer, Inner...>& right) noexcept;
```

### <a name="parameters"></a>參數

*離開*\
左 `scoped_allocator_adaptor` 物件。

*對*\
右 `scoped_allocator_adaptor` 物件。

### <a name="return-value"></a>傳回值

`left.outer_allocator() == right.outer_allocator() && left.inner_allocator() == right.inner_allocator()`

## <a name="see-also"></a>另請參閱

[<scoped_allocator>](../standard-library/scoped-allocator.md)
