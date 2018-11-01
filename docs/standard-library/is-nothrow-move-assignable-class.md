---
title: is_nothrow_move_assignable 類別
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_nothrow_move_assignable
helpviewer_keywords:
- is_nothrow_move_assignable
ms.assetid: 000baa02-cbba-49de-9870-af730033348e
ms.openlocfilehash: eb1ddcace7a68bf60154a15117a1c16a438d263d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50535924"
---
# <a name="isnothrowmoveassignable-class"></a>is_nothrow_move_assignable 類別

測試類型是否具有 **nothrow** 移動指派運算子。

## <a name="syntax"></a>語法

```cpp
template <class Ty>
struct is_nothrow_move_assignable;
```

### <a name="parameters"></a>參數

*Ty*<br/>
要查詢的類型。

## <a name="remarks"></a>備註

如果型別述詞的執行個體保留 true 的型別*Ty*具有 nothrow 移動指派運算子，否則為 false。

## <a name="requirements"></a>需求

**標頭：**\<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)<br/>
