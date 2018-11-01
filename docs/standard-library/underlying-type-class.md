---
title: underlying_type 類別
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::underlying_type
helpviewer_keywords:
- underlying_type
ms.assetid: 691ddce3-2677-4480-bd35-d933fab85d3e
ms.openlocfilehash: 23e5e9bc5406265f49fca2ed220c597cb32e2a9a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50609699"
---
# <a name="underlyingtype-class"></a>underlying_type 類別

產生列舉類型的基礎整數類型。

## <a name="syntax"></a>語法

```cpp
template <class T>
struct underlying_type;
```

### <a name="parameters"></a>參數

*T*<br/>
要修改的類型。

## <a name="remarks"></a>備註

`type`範本類別的成員 typedef 名稱的基礎整數類資料類型*T*，當*T*是列舉類型，否則沒有任何成員 typedef `type`。

## <a name="requirements"></a>需求

**標頭：**\<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)<br/>
