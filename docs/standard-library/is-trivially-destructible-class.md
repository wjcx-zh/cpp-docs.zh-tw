---
title: is_trivially_destructible 類別
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_trivially_destructible
helpviewer_keywords:
- is_trivially_destructible
ms.assetid: 3f7a787d-2448-40c5-ac51-a228318e02ce
ms.openlocfilehash: 6a978b7cc32e6de3d4b1d811b9aa6f52cf0370d7
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68459630"
---
# <a name="istriviallydestructible-class"></a>is_trivially_destructible 類別

測試類型是否是可透過極簡方式損壞的類型。

## <a name="syntax"></a>語法

```cpp
template <class T>
struct is_trivially_destructible;
```

### <a name="parameters"></a>參數

*而已*\
要查詢的類型。

## <a name="remarks"></a>備註

如果類型*T*是易損壞類型, 則類型述詞的實例為 true, 而編譯器知道此析構函式不會使用任何非一般作業。 否則值會是 false。

## <a name="requirements"></a>需求

**標頭：** \<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)
