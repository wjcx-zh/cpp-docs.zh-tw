---
title: _variant_t::ChangeType
ms.date: 11/04/2016
f1_keywords:
- _variant_t::ChangeType
- _variant_t.ChangeType
helpviewer_keywords:
- ChangeType method [C++]
- VARIANT object [C++], ChangeType
- VARIANT object
ms.assetid: 829d2eeb-3338-4a88-9dce-0ca145f47aac
ms.openlocfilehash: b0692c9befaa6b7e787ada624dcbb56b074c9f9d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80160459"
---
# <a name="_variant_tchangetype"></a>_variant_t::ChangeType

**Microsoft 專屬**

將 `_variant_t` 物件的類型變更為指定的 `VARTYPE`。

## <a name="syntax"></a>語法

```
void ChangeType(
   VARTYPE vartype,
   const _variant_t* pSrc = NULL
);
```

#### <a name="parameters"></a>參數

*vartype*<br/>
這個 `_variant_t` 物件的 `VARTYPE`。

*.Psrc*<br/>
要轉換之 `_variant_t` 物件的指標。 如果此值為 Null，則會就地完成轉換。

## <a name="remarks"></a>備註

此成員函式會將 `_variant_t` 物件轉換成指定的 `VARTYPE`。 如果 *.psrc*為 Null，則會就地完成轉換，否則會從 *.psrc*複製此 `_variant_t` 物件，然後再進行轉換。

**END Microsoft 特定的**

## <a name="see-also"></a>另請參閱

[_variant_t 類別](../cpp/variant-t-class.md)
