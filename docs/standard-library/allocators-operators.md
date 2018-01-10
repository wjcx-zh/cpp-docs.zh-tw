---
title: "&lt;allocators&gt; 運算子 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- allocators/std::operator!=
- allocators/std::operator==
dev_langs: C++
ms.assetid: b55d67cb-3c69-46bf-ad40-e845fb096c4e
caps.latest.revision: "11"
manager: ghogen
ms.openlocfilehash: 986d972bdc778ddd47c2c0098955f2b570c881ce
ms.sourcegitcommit: a7e4956c1150273e8dd39fda8b41655a6cf2cb98
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/08/2017
---
# <a name="ltallocatorsgt-operators"></a>&lt;allocators&gt; 運算子

這些是全域範本運算子函式中定義&lt;配置器&gt;。 類別成員運算子函式，請參閱類別文件。

|||
|-|-|
|[operator!=](#op_neq)|[operator==](#op_eq_eq)|

##  <a name="op_neq"></a> operator!=

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
|`left`|要測試是否不相等的其中一個配置器物件。|
|`right`|要測試是否不相等的其中一個配置器物件。|

### <a name="return-value"></a>傳回值

如果配置器物件不相等，則為 **true**；如果配置器物件相等，則為 **false**。

### <a name="remarks"></a>備註

範本運算子會傳回 `!(left == right)`。

##  <a name="op_eq_eq"></a> operator==

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
|`left`|要測試是否相等的其中一個配置器物件。|
|`right`|要測試是否相等的其中一個配置器物件。|

### <a name="return-value"></a>傳回值

如果配置器物件相等，則為 **true**；如果配置器物件不相等，則為 **false**。

### <a name="remarks"></a>備註

這個範本運算子會傳回 `left.equals(right)`。

## <a name="see-also"></a>另請參閱

[\<allocators>](../standard-library/allocators-header.md)  
