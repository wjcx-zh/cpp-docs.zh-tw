---
title: is_nothrow_copy_constructible 類別
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_nothrow_copy_constructible
helpviewer_keywords:
- is_nothrow_copy_constructible
ms.assetid: f13a0bea-63b1-492a-9a45-d445df35c282
ms.openlocfilehash: 229083f4569647bd65d1ce7e640f753a9418371d
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68455953"
---
# <a name="isnothrowcopyconstructible-class"></a>is_nothrow_copy_constructible 類別

測試類型是否具有 **nothrow** 複製建構函式。

## <a name="syntax"></a>語法

```cpp
template <class Ty>
struct is_nothrow_copy_constructible;
```

### <a name="parameters"></a>參數

*Ty*\
要查詢的類型。

## <a name="remarks"></a>備註

如果類型*Ty*具有 nothrow 複製的程式, 則類型述詞的實例為 true, 否則為 false。

## <a name="requirements"></a>需求

**標頭：** \<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)
