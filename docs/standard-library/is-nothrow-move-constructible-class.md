---
title: is_nothrow_move_constructible 類別
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_nothrow_move_constructible
helpviewer_keywords:
- is_nothrow_move_constructible
ms.assetid: d186d97b-7b89-470a-8d30-993046a83379
ms.openlocfilehash: 7f1ccdba11f62fcbeaf54162f80f0717feaa2fa1
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68455867"
---
# <a name="isnothrowmoveconstructible-class"></a>is_nothrow_move_constructible 類別

測試類型是否具有 **nothrow** 移動建構函式。

## <a name="syntax"></a>語法

```cpp
template <class Ty>
struct is_nothrow_move_constructible;
```

### <a name="parameters"></a>參數

*Ty*\
要查詢的類型。

## <a name="remarks"></a>備註

如果類型*Ty*具有 nothrow 移動的函式, 則類型述詞的實例會保留 true, 否則會保留 false。

## <a name="requirements"></a>需求

**標頭：** \<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)
