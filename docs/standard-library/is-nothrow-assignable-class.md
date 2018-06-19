---
title: is_nothrow_assignable 類別 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
f1_keywords:
- type_traits/std::is_nothrow_assignable
dev_langs:
- C++
helpviewer_keywords:
- is_nothrow_assignable
ms.assetid: aa3aca92-308b-4b1d-b3f3-c54216c48fe7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0f11e1ce8b016ab8c6e8af04e351e80307b2189e
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33843440"
---
# <a name="isnothrowassignable-class"></a>is_nothrow_assignable 類別

測試是否可將 `From` 類型的值指派給 `To` 類型，且該指派已知不會擲回。

## <a name="syntax"></a>語法

```cpp
template <class To, class From>
struct is_nothrow_assignable;
```

### <a name="parameters"></a>參數

若要接收指派的物件類型。

從提供的值的物件類型。

## <a name="remarks"></a>備註

運算式 `declval<To>() = declval<From>()` 必須格式正確，且編譯器必須已知它不會擲回。 `From` 和 `To` 兩者必須是完整類型 `void`，或是界限未知的陣列。

## <a name="requirements"></a>需求

**標頭：**\<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)<br/>
