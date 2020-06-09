---
title: alignment_of 類別
ms.date: 12/11/2019
f1_keywords:
- type_traits/std::alignment_of
helpviewer_keywords:
- alignment_of class
- alignment_of
ms.assetid: 4141c59a-f94e-41c4-93fd-9ea578b27387
ms.openlocfilehash: c2af00ac32b3013820a3109783c4bf7eb42ec445
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84623736"
---
# <a name="alignment_of-class"></a>alignment_of 類別

取得指定類型的對齊方式。 此結構是針對 [alignof](../cpp/alignment-cpp-declarations.md) 所實作。 當您只需要查詢對齊值時，請直接使用**alignof** 。 當您需要整數常數 (例如進行標記分派時)，請使用 alignment_of。

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

## <a name="requirements"></a>規格需求

**標頭：**\<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](type-traits.md)\
[aligned_storage 類別](aligned-storage-class.md)
