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
ms.openlocfilehash: 424fcf5b960182326dc1192d8d60f168ead59d98
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2018
ms.locfileid: "38965411"
---
# <a name="isnothrowassignable-class"></a>is_nothrow_assignable 類別

測試的值是否*從*型別可以指派給*到*類型和指派已知不會擲回。

## <a name="syntax"></a>語法

```cpp
template <class To, class From>
struct is_nothrow_assignable;
```

### <a name="parameters"></a>參數

*若要*接收指派的物件型別。

*從*提供值的物件型別。

## <a name="remarks"></a>備註

運算式 `declval<To>() = declval<From>()` 必須格式正確，且編譯器必須已知它不會擲回。 兩者*從*並*要*必須是完整的類型**void**，或界限未知的陣列。

## <a name="requirements"></a>需求

**標頭：**\<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)<br/>
