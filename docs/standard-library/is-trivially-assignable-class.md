---
title: is_trivially_assignable 類別
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_trivially_assignable
helpviewer_keywords:
- is_trivially_assignable
ms.assetid: 1284a8f7-4093-426d-9c9a-dabb46f90d6d
ms.openlocfilehash: eeef85a0b26c25eb745258c7e0e35394f0cab979
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50495156"
---
# <a name="istriviallyassignable-class"></a>is_trivially_assignable 類別

測試是否可將 `From` 類型的值透過極簡方式指派給 `To` 類型

## <a name="syntax"></a>語法

```cpp
template <class To, class From>
struct is_trivially_assignable;
```

### <a name="parameters"></a>參數

*若要*<br/>
接收指派的物件類型。

*From*<br/>
提供值的物件類型。

## <a name="remarks"></a>備註

運算式 `declval<To>() = declval<From>()` 必須格式正確，且編譯器必須已知它不需要任何非極簡作業。 兩者`From`並`To`必須是完整的類型**void**，或是界限未知的陣列。

## <a name="requirements"></a>需求

**標頭：**\<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)<br/>
