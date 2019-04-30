---
title: alignment_of 類別
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::alignment_of
helpviewer_keywords:
- alignment_of class
- alignment_of
ms.assetid: 4141c59a-f94e-41c4-93fd-9ea578b27387
ms.openlocfilehash: 2633749a72ceeea197579dca4300b58250f60d73
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62411080"
---
# <a name="alignmentof-class"></a>alignment_of 類別

取得指定類型的對齊方式。 此結構是針對 [alignof](../cpp/alignof-and-alignas-cpp.md) 所實作。 若只需要查詢對齊值，請直接使用 `alignof`。 當您需要整數常數 (例如進行標記分派時)，請使用 alignment_of。

## <a name="syntax"></a>語法

```cpp
template <class Ty>
struct alignment_of;
```

### <a name="parameters"></a>參數

*Ty*<br/>
要查詢的類型。

## <a name="remarks"></a>備註

類型查詢會保存的值類型的對齊*Ty*。

## <a name="requirements"></a>需求

**標頭：**\<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)<br/>
[aligned_storage 類別](../standard-library/aligned-storage-class.md)<br/>
