---
title: is_nothrow_move_constructible 類別
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_nothrow_move_constructible
helpviewer_keywords:
- is_nothrow_move_constructible
ms.assetid: d186d97b-7b89-470a-8d30-993046a83379
ms.openlocfilehash: 115a1b6c2157a139786c0b8762a9a614bbcd6deb
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217723"
---
# <a name="is_nothrow_move_constructible-class"></a>is_nothrow_move_constructible 類別

測試類型是否有移動的函式 **`nothrow`** 。

## <a name="syntax"></a>語法

```cpp
template <class Ty>
struct is_nothrow_move_constructible;
```

### <a name="parameters"></a>參數

*Ty*\
要查詢的類型。

## <a name="remarks"></a>備註

如果類型*Ty*具有 nothrow 移動的函式，則類型述詞的實例會保留 true，否則會保留 false。

## <a name="requirements"></a>需求

**標頭：**\<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)
