---
title: '&lt;allocators&gt; 運算子'
ms.date: 11/04/2016
f1_keywords:
- allocators/std::operator!=
- allocators/std::operator==
ms.assetid: b55d67cb-3c69-46bf-ad40-e845fb096c4e
ms.openlocfilehash: a21708ca090b0db561391308f347d90b77c62645
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84623564"
---
# <a name="ltallocatorsgt-operators"></a>&lt;allocators&gt; 運算子

這些是定義在配置器中的全域範本運算子函式 &lt; &gt; 。 如需類別成員運算子函式，請參閱類別檔。

|||
|-|-|
|[operator！ =](#op_neq)|[operator = =](#op_eq_eq)|

## <a name="operator"></a><a name="op_neq"></a>operator！ =

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
|*左面*|要測試是否不相等的其中一個配置器物件。|
|*再*|要測試是否不相等的其中一個配置器物件。|

### <a name="return-value"></a>傳回值

如果配置器物件不相等，則為 **true**；如果配置器物件相等，則為 **false**。

### <a name="remarks"></a>備註

範本運算子會傳回 `!(left == right)`。

## <a name="operator"></a><a name="op_eq_eq"></a>operator = =

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
|*左面*|要測試是否相等的其中一個配置器物件。|
|*再*|要測試是否相等的其中一個配置器物件。|

### <a name="return-value"></a>傳回值

如果配置器物件相等，則為 **true**；如果配置器物件不相等，則為 **false**。

### <a name="remarks"></a>備註

這個範本運算子會傳回 `left.equals(right)`。

## <a name="see-also"></a>另請參閱

[\<allocators>](allocators-header.md)
