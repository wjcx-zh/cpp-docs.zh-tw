---
title: is_aggregate 類別
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_aggregate
helpviewer_keywords:
- is_aggregate
ms.openlocfilehash: 89749e2b4c0e6aaf00de074718cfb598333bc739
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456697"
---
# <a name="isaggregate-class"></a>is_aggregate 類別

測試類型是否是標示為 `aggregate` 的類別類型。

## <a name="syntax"></a>語法

```cpp
template <class T>
struct is_aggregate;
```

### <a name="parameters"></a>參數

*而已*\
要查詢的類型。

## <a name="remarks"></a>備註

如果類型*T*是標示`aggregate`的類別類型, 則類型述詞的實例為 true, 否則為 false。 如果*T*是類別類型, 它必須是完整的類型。

## <a name="requirements"></a>需求

**標頭：** \<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)
