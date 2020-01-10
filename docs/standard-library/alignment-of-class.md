---
title: alignment_of 類別
ms.date: 12/11/2019
f1_keywords:
- type_traits/std::alignment_of
helpviewer_keywords:
- alignment_of class
- alignment_of
ms.assetid: 4141c59a-f94e-41c4-93fd-9ea578b27387
ms.openlocfilehash: d241848edf57fe4876c35e22f1762abf5d6888fa
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/20/2019
ms.locfileid: "75302311"
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

## <a name="requirements"></a>需求

**標頭：** \<type_traits >

**命名空間：** std

## <a name="see-also"></a>請參閱

[<type_traits>](../standard-library/type-traits.md)\
[aligned_storage 類別](../standard-library/aligned-storage-class.md)
