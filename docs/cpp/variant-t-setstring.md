---
title: _variant_t::SetString
ms.date: 11/04/2016
f1_keywords:
- _variant_t::SetString
helpviewer_keywords:
- SetString method [C++]
ms.assetid: 816b08e5-6830-46ca-b3d7-7689308b3be3
ms.openlocfilehash: d07e995be0ecd99974356a7516e7c4deee677637
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50628237"
---
# <a name="varianttsetstring"></a>_variant_t::SetString

**Microsoft 專屬**

將字串指派給這個 `_variant_t` 物件。

## <a name="syntax"></a>語法

```
void SetString(const char* pSrc);
```

#### <a name="parameters"></a>參數

*pSrc*<br/>
字元字串的指標。

## <a name="remarks"></a>備註

將 ANSI 字串轉換為 Unicode `BSTR` 字串，並將它指派給這個 `_variant_t` 物件。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[_variant_t 類別](../cpp/variant-t-class.md)