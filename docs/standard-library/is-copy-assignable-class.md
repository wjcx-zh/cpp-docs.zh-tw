---
title: is_copy_assignable 類別
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_copy_assignable
helpviewer_keywords:
- is_copy_assignable
ms.assetid: 3ae6bca1-85fb-4829-9ee9-0183b081ff50
ms.openlocfilehash: 5fedd32f026828e49ea29cb2975a2529ca28c862
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68452831"
---
# <a name="iscopyassignable-class"></a>is_copy_assignable 類別

測試類型是否可以在指派上複製。

## <a name="syntax"></a>語法

```cpp
template <class Ty>
struct is_copy_assignable;
```

### <a name="parameters"></a>參數

*Ty*\
要查詢的類型。

## <a name="remarks"></a>備註

如果類型*Ty*是具有複製指派運算子的類別, 則類型述詞的實例會保留 true, 否則會保留 false。 相當於 is_assignable\<Ty&, const Ty&>。

## <a name="requirements"></a>需求

**標頭：** \<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)
