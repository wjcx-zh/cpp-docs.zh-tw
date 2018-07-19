---
title: '&lt;scoped_allocator&gt; 運算子 | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- scoped_allocator/std::operator!=
- scoped_allocator/std::operator==
dev_langs:
- C++
ms.assetid: 4dfe0805-cc6e-479f-887f-a1c164f73837
ms.openlocfilehash: c2c61e3fce5d1cf58f59bc9dd51920bccc0eb2f3
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2018
ms.locfileid: "38966468"
---
# <a name="ltscopedallocatorgt-operators"></a>&lt;scoped_allocator&gt; 運算子

|||
|-|-|
|[operator!=](#op_neq)|[operator==](#op_eq_eq)|

## <a name="op_neq"></a> operator!=

測試兩個 `scoped_allocator_adaptor` 物件是否不相等。

```cpp
template <class Outer, class... Inner>
bool operator!=(
    const scoped_allocator_adaptor<Outer, Inner...>& left,
    const scoped_allocator_adaptor<Outer, Inner...>& right) noexcept;
```

### <a name="parameters"></a>參數

*左*左側`scoped_allocator_adaptor`物件。

*右*右`scoped_allocator_adaptor`物件。

### <a name="return-value"></a>傳回值

`!(left == right)`

## <a name="op_eq_eq"></a> operator==

測試兩個 `scoped_allocator_adaptor` 物件是否相等。

```cpp
template <class Outer, class... Inner>
bool operator==(
    const scoped_allocator_adaptor<Outer, Inner...>& left,
    const scoped_allocator_adaptor<Outer, Inner...>& right) noexcept;
```

### <a name="parameters"></a>參數

*左*左側`scoped_allocator_adaptor`物件。

*右*右`scoped_allocator_adaptor`物件。

### <a name="return-value"></a>傳回值

`left.outer_allocator() == right.outer_allocator() && left.inner_allocator() == right.inner_allocator()`

## <a name="see-also"></a>另請參閱

[<scoped_allocator>](../standard-library/scoped-allocator.md)<br/>
