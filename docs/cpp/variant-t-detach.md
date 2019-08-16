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
ms.openlocfilehash: 8426c80af04b2c0906af150ea3e91304335e9f69
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69500552"
---
# <a name="_variant_tdetach"></a>_variant_t::Detach

**Microsoft 專屬**

從這個`VARIANT` `_variant_t`物件卸離封裝的物件。

## <a name="syntax"></a>語法

```
VARIANT Detach( );
```

## <a name="return-value"></a>傳回值

封裝`VARIANT`的。

## <a name="remarks"></a>備註

解壓縮並傳回已封裝`VARIANT`的, 然後清除`_variant_t`此物件而不終結它。 此成員函式會`VARIANT`從封裝中移除, `VARTYPE`並將`_variant_t`這個物件的設定為 VT_EMPTY。 您必須呼叫[VariantClear](/windows/win32/api/oleauto/nf-oleauto-variantclear)函式, 以釋放`VARIANT`傳回的。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[_variant_t 類別](../cpp/variant-t-class.md)