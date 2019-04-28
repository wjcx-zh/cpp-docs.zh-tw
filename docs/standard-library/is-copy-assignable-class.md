---
title: is_copy_assignable 類別
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_copy_assignable
helpviewer_keywords:
- is_copy_assignable
ms.assetid: 3ae6bca1-85fb-4829-9ee9-0183b081ff50
ms.openlocfilehash: 75e0e8d995fbb3c6bfb1af3142a98651d7a29e96
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62336747"
---
# <a name="iscopyassignable-class"></a>is_copy_assignable 類別

測試類型是否可以在指派上複製。

## <a name="syntax"></a>語法

```cpp
template <class Ty>
struct is_copy_assignable;
```

### <a name="parameters"></a>參數

*Ty*<br/>
要查詢的類型。

## <a name="remarks"></a>備註

如果型別述詞的執行個體保留 true 的型別*Ty*是具有複製指派運算子，否則為 false 的類別。 相當於 is_assignable\<Ty&, const Ty&>。

## <a name="requirements"></a>需求

**標頭：**\<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)<br/>
