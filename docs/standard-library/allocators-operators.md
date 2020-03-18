---
title: '&lt;allocators&gt; 運算子'
ms.date: 11/04/2016
f1_keywords:
- allocators/std::operator!=
- allocators/std::operator==
ms.assetid: b55d67cb-3c69-46bf-ad40-e845fb096c4e
ms.openlocfilehash: b7429e298cdf14d727fc481db6c4a3bf8574b5e7
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2020
ms.locfileid: "79416897"
---
# <a name="ltallocatorsgt-operators"></a>&lt;allocators&gt; 運算子

這些是 &lt;配置器&gt;中定義的全域範本運算子函式。 如需類別成員運算子函式，請參閱類別檔。

|||
|-|-|
|[operator!=](#op_neq)|[operator==](#op_eq_eq)|

## <a name="op_neq"></a> operator!=

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
|*left*|要測試是否不相等的其中一個配置器物件。|
|*right*|要測試是否不相等的其中一個配置器物件。|

### <a name="return-value"></a>傳回值

如果配置器物件不相等，則為 **true**；如果配置器物件相等，則為 **false**。

### <a name="remarks"></a>備註

範本運算子會傳回 `!(left == right)`。

## <a name="op_eq_eq"></a> operator==

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
|*left*|要測試是否相等的其中一個配置器物件。|
|*right*|要測試是否相等的其中一個配置器物件。|

### <a name="return-value"></a>傳回值

如果配置器物件相等，則為 **true**；如果配置器物件不相等，則為 **false**。

### <a name="remarks"></a>備註

這個範本運算子會傳回 `left.equals(right)`。

## <a name="see-also"></a>另請參閱

[\<allocators>](../standard-library/allocators-header.md)
