---
title: is_trivial 類別
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_trivial
helpviewer_keywords:
- is_trivial
ms.assetid: 6beb11d4-2f38-4c7e-9959-ca5d26250df7
ms.openlocfilehash: 1d218848fd65ca68022e3e66df02201582626711
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68457427"
---
# <a name="istrivial-class"></a>is_trivial 類別

測試類型是否為 trivial 類型。

## <a name="syntax"></a>語法

```cpp
template <class T>
struct is_trivial;
```

### <a name="parameters"></a>參數

*而已*\
要查詢的類型。

## <a name="remarks"></a>備註

如果類型*T*是簡單類型, 則類型述詞的實例為 true, 否則為 false。 trivial 類型是純量類型、可完整複製類別類型、這些類型的陣列和 cv 限定版本。

## <a name="requirements"></a>需求

**標頭：** \<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)
