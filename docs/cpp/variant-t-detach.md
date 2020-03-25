---
title: _variant_t::Detach
ms.date: 11/04/2016
f1_keywords:
- _variant_t::Detach
- _variant_t.Detach
helpviewer_keywords:
- VARIANT object [C++], detatch
- Detach method [C++]
- VARIANT object
ms.assetid: c348ac08-62cf-4657-a16f-974a79c12158
ms.openlocfilehash: 9737db6b77483fa55e1dad90b9464752cd8537a5
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187735"
---
# <a name="_variant_tdetach"></a>_variant_t::Detach

**Microsoft 專屬**

從這個 `_variant_t` 物件卸離封裝的 `VARIANT` 物件。

## <a name="syntax"></a>語法

```
VARIANT Detach( );
```

## <a name="return-value"></a>傳回值

封裝的 `VARIANT`。

## <a name="remarks"></a>備註

解壓縮並傳回封裝的 `VARIANT`，然後清除此 `_variant_t` 物件，而不會終結它。 此成員函式會移除封裝中的 `VARIANT`，並將這個 `_variant_t` 物件的 `VARTYPE` 設定為 VT_EMPTY。 您必須呼叫[VariantClear](/windows/win32/api/oleauto/nf-oleauto-variantclear)函式，以釋放傳回的 `VARIANT`。

**END Microsoft 特定的**

## <a name="see-also"></a>另請參閱

[_variant_t 類別](../cpp/variant-t-class.md)
