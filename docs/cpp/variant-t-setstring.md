---
title: _variant_t::SetString
ms.date: 11/04/2016
f1_keywords:
- _variant_t::SetString
helpviewer_keywords:
- SetString method [C++]
ms.assetid: 816b08e5-6830-46ca-b3d7-7689308b3be3
ms.openlocfilehash: 0cd300a09c29668c496d93109d1bc862947e948c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187553"
---
# <a name="_variant_tsetstring"></a>_variant_t::SetString

**Microsoft 專屬**

將字串指派給這個 `_variant_t` 物件。

## <a name="syntax"></a>語法

```
void SetString(const char* pSrc);
```

#### <a name="parameters"></a>參數

*.Psrc*<br/>
字元字串的指標。

## <a name="remarks"></a>備註

將 ANSI 字串轉換為 Unicode `BSTR` 字串，並將它指派給這個 `_variant_t` 物件。

**END Microsoft 特定的**

## <a name="see-also"></a>另請參閱

[_variant_t 類別](../cpp/variant-t-class.md)
