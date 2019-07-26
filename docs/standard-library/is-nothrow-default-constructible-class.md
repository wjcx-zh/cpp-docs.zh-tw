---
title: is_nothrow_default_constructible 類別
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_nothrow_default_constructible
helpviewer_keywords:
- is_nothrow_default_constructible
ms.assetid: c576fcc9-5be1-43aa-b93a-64d3f1848887
ms.openlocfilehash: 76b58800a454f42f6b5b6fcea23df161c37564b2
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68455936"
---
# <a name="isnothrowdefaultconstructible-class"></a>is_nothrow_default_constructible 類別

測試類型是否有非擲回預設建構函式。

## <a name="syntax"></a>語法

```cpp
template <class Ty>
struct is_nothrow_default_constructible;
```

### <a name="parameters"></a>參數

*Ty*\
要查詢的類型。

## <a name="remarks"></a>備註

如果類型*Ty*具有 nothrow 預設的函式, 則類型述詞的實例為 true, 否則為 false。 類型述詞的執行個體相當於 `is_nothrow_constructible<Ty>`。

## <a name="requirements"></a>需求

**標頭：** \<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)
