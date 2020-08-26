---
title: '&lt;scoped_allocator&gt; 運算子'
ms.date: 11/04/2016
f1_keywords:
- scoped_allocator/std::operator!=
- scoped_allocator/std::operator==
ms.assetid: 4dfe0805-cc6e-479f-887f-a1c164f73837
ms.openlocfilehash: 907772069c192b3ef75c7366e079b1da1dd36f8d
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88846247"
---
# <a name="ltscoped_allocatorgt-operators"></a>&lt;scoped_allocator&gt; 運算子

[operator！ =](#op_neq)\
[operator = =](#op_eq_eq)

## <a name="operator"></a><a name="op_neq"></a> operator！ =

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

## <a name="operator"></a><a name="op_eq_eq"></a> operator = =

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
