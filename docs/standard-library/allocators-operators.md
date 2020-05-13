---
title: '&lt;allocators&gt; 運算子'
ms.date: 11/04/2016
f1_keywords:
- allocators/std::operator!=
- allocators/std::operator==
ms.assetid: b55d67cb-3c69-46bf-ad40-e845fb096c4e
ms.openlocfilehash: 7bc37e98ed85582cac8fc7ae21e54a6d5da9e06f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364955"
---
# <a name="ltallocatorsgt-operators"></a>&lt;allocators&gt; 運算子

這些是分配器中&lt;定義的全域範本運算符函數。&gt; 有關類成員運算符函數,請參閱類文檔。

|||
|-|-|
|[操作員!](#op_neq)|[運算子*](#op_eq_eq)|

## <a name="operator"></a><a name="op_neq"></a>操作員!

測試指定類別的配置器物件之間是否不等。

```cpp
template <class Type, class Sync>
bool operator!=(
    const allocator_base<Type, Sync>& left,
    const allocator_base<Type, Sync>& right);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*離開*|要測試是否不相等的其中一個配置器物件。|
|*對*|要測試是否不相等的其中一個配置器物件。|

### <a name="return-value"></a>傳回值

如果配置器物件不相等，則為 **true**；如果配置器物件相等，則為 **false**。

### <a name="remarks"></a>備註

範本運算子會傳回 `!(left == right)`。

## <a name="operator"></a><a name="op_eq_eq"></a>運算子*

測試指定類別的配置器物件之間是否相等。

```cpp
template <class Type, class Sync>
bool operator==(
    const allocator_base<Type, Sync>& left,
    const allocator_base<Type, Sync>& right);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*離開*|要測試是否相等的其中一個配置器物件。|
|*對*|要測試是否相等的其中一個配置器物件。|

### <a name="return-value"></a>傳回值

如果配置器物件相等，則為 **true**；如果配置器物件不相等，則為 **false**。

### <a name="remarks"></a>備註

這個範本運算子會傳回 `left.equals(right)`。

## <a name="see-also"></a>另請參閱

[\<配置器>](../standard-library/allocators-header.md)
