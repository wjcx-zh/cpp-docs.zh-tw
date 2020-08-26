---
title: '&lt;allocators&gt; 運算子'
ms.date: 11/04/2016
f1_keywords:
- allocators/std::operator!=
- allocators/std::operator==
ms.assetid: b55d67cb-3c69-46bf-ad40-e845fb096c4e
ms.openlocfilehash: 969c9f8e05a9fafad4d3a1102060e2b3d4d0eb2e
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88844778"
---
# <a name="ltallocatorsgt-operators"></a>&lt;allocators&gt; 運算子

這些是配置器中定義的全域範本運算子函式 &lt; &gt; 。 如需類別成員運算子函式的詳細說明，請參閱類別檔。

[operator！ =](#op_neq)\
[operator = =](#op_eq_eq)

## <a name="operator"></a><a name="op_neq"></a> operator！ =

測試指定類別的配置器物件之間是否不等。

```cpp
template <class Type, class Sync>
bool operator!=(
    const allocator_base<Type, Sync>& left,
    const allocator_base<Type, Sync>& right);
```

### <a name="parameters"></a>參數

*離開*\
要測試是否不相等的其中一個配置器物件。

*對*\
要測試是否不相等的其中一個配置器物件。

### <a name="return-value"></a>傳回值

**`true`** 如果配置器物件不相等; **`false`** 如果配置器物件相等則為。

### <a name="remarks"></a>備註

範本運算子會傳回 `!(left == right)`。

## <a name="operator"></a><a name="op_eq_eq"></a> operator = =

測試指定類別的配置器物件之間是否相等。

```cpp
template <class Type, class Sync>
bool operator==(
    const allocator_base<Type, Sync>& left,
    const allocator_base<Type, Sync>& right);
```

### <a name="parameters"></a>參數

*離開*\
要測試是否相等的其中一個配置器物件。

*對*\
要測試是否相等的其中一個配置器物件。

### <a name="return-value"></a>傳回值

**`true`** 如果配置器物件相等; **`false`** 如果配置器物件不相等。

### <a name="remarks"></a>備註

這個範本運算子會傳回 `left.equals(right)`。

## <a name="see-also"></a>另請參閱

[\<allocators>](allocators-header.md)
