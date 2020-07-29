---
title: alignment_of 類別
ms.date: 12/11/2019
f1_keywords:
- type_traits/std::alignment_of
helpviewer_keywords:
- alignment_of class
- alignment_of
ms.assetid: 4141c59a-f94e-41c4-93fd-9ea578b27387
ms.openlocfilehash: 5a90f481c33431d92f0f28405e6226863d2b3913
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87205011"
---
# <a name="alignment_of-class"></a>alignment_of 類別

取得指定類型的對齊方式。 這個結構是根據來執行 [`alignof`](../cpp/alignment-cpp-declarations.md) 。 **`alignof`** 當您只需要查詢對齊值時，請直接使用。 `alignment_of`當您需要整數常數（例如，在進行標記分派時）時，請使用。

## <a name="syntax"></a>語法

```cpp
template <class Ty>
struct alignment_of;
```

### <a name="parameters"></a>參數

*Ty*\
要查詢的類型。

## <a name="remarks"></a>備註

類型查詢會保存*Ty*類型的對齊值。

## <a name="requirements"></a>需求

**標頭：**\<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[`<type_traits>`](type-traits.md)\
[`aligned_storage`課堂](aligned-storage-class.md)
