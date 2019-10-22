---
title: underlying_type 類別
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::underlying_type
helpviewer_keywords:
- underlying_type
ms.assetid: 691ddce3-2677-4480-bd35-d933fab85d3e
ms.openlocfilehash: ea4768d78047112a7584ca49b0e4487fad55a970
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688847"
---
# <a name="underlying_type-class"></a>underlying_type 類別

產生列舉類型的基礎整數類型。

## <a name="syntax"></a>語法

```cpp
template <class T>
struct underlying_type;
```

### <a name="parameters"></a>參數

*T* \
要修改的類型。

## <a name="remarks"></a>備註

當*t*是列舉類型時，類別樣板的 `type` 成員 typedef 會命名*t*的基礎整數類型，否則不會有成員 typedef `type`。

## <a name="requirements"></a>需求

**標頭：** \<type_traits>

**命名空間:** std

## <a name="see-also"></a>請參閱

[<type_traits>](../standard-library/type-traits.md)
