---
title: is_nothrow_move_assignable 類別
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_nothrow_move_assignable
helpviewer_keywords:
- is_nothrow_move_assignable
ms.assetid: 000baa02-cbba-49de-9870-af730033348e
ms.openlocfilehash: 92e3364843b5614c9fa108d33605b35962726aa2
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217736"
---
# <a name="is_nothrow_move_assignable-class"></a>is_nothrow_move_assignable 類別

測試類型是否有 **`nothrow`** 移動指派運算子。

## <a name="syntax"></a>語法

```cpp
template <class Ty>
struct is_nothrow_move_assignable;
```

### <a name="parameters"></a>參數

*Ty*\
要查詢的類型。

## <a name="remarks"></a>備註

如果型別*Ty*有 nothrow 的移動指派運算子，則型別述詞的實例為 true，否則保留 false。

## <a name="requirements"></a>需求

**標頭：**\<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)
