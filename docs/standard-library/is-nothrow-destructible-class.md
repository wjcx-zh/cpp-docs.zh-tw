---
title: is_nothrow_destructible 類別
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_nothrow_destructible
helpviewer_keywords:
- is_nothrow_destructible
ms.assetid: 0bbd8a28-e312-4d72-bd28-aac027f974d3
ms.openlocfilehash: 44de1f1fae1ea542aa247c0b39f04ee6bbd6308a
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68455910"
---
# <a name="isnothrowdestructible-class"></a>is_nothrow_destructible 類別

測試類型是否易損壞，且編譯器已知解構函式不會擲回。

## <a name="syntax"></a>語法

```cpp
template <class T>
struct is_nothrow_destructible;
```

### <a name="parameters"></a>參數

*而已*\
要查詢的類型。

## <a name="remarks"></a>備註

如果類型*T*是易損壞類型, 而且編譯器已知不會擲回此析構函式, 則類型述詞的實例會保留 true。 否則值會是 false。

## <a name="requirements"></a>需求

**標頭：** \<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)
