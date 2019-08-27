---
title: underlying_type 類別
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::underlying_type
helpviewer_keywords:
- underlying_type
ms.assetid: 691ddce3-2677-4480-bd35-d933fab85d3e
ms.openlocfilehash: 465383357e6c0306c24fe8325327327c3a3b64c1
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68454978"
---
# <a name="underlyingtype-class"></a>underlying_type 類別

產生列舉類型的基礎整數類型。

## <a name="syntax"></a>語法

```cpp
template <class T>
struct underlying_type;
```

### <a name="parameters"></a>參數

*而已*\
要修改的類型。

## <a name="remarks"></a>備註

當 t 是列舉類型時, 樣板類別的 `type` 成員typedef會命名t的基礎整數類型,否則不會有成員`type` typedef。

## <a name="requirements"></a>需求

**標頭：** \<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)
