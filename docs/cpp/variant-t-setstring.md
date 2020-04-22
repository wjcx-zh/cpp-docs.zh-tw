---
title: _variant_t::SetString
ms.date: 11/04/2016
f1_keywords:
- _variant_t::SetString
helpviewer_keywords:
- SetString method [C++]
ms.assetid: 816b08e5-6830-46ca-b3d7-7689308b3be3
ms.openlocfilehash: 60ad1c1bd95eb35f2a4f2800f79d0326c68a1176
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81745856"
---
# <a name="_variant_tsetstring"></a>_variant_t::SetString

**Microsoft 特定的**

將字串指派給這個 `_variant_t` 物件。

## <a name="syntax"></a>語法

```cpp
void SetString(const char* pSrc);
```

#### <a name="parameters"></a>參數

*pSrc*<br/>
字元字串的指標。

## <a name="remarks"></a>備註

將 ANSI 字串轉換為 Unicode `BSTR` 字串，並將它指派給這個 `_variant_t` 物件。

**結束微軟的**

## <a name="see-also"></a>另請參閱

[_variant_t類](../cpp/variant-t-class.md)
