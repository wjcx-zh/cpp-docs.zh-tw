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
ms.openlocfilehash: c2283158856a6781ab2e12c51f4e2ad0e4f1d531
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81750724"
---
# <a name="_variant_tchangetype"></a>_variant_t::ChangeType

**Microsoft 特定的**

將`_variant_t`物件的類型變更為`VARTYPE`指示的 。

## <a name="syntax"></a>語法

```cpp
void ChangeType(
   VARTYPE vartype,
   const _variant_t* pSrc = NULL
);
```

#### <a name="parameters"></a>參數

*vartype*<br/>
此`VARTYPE``_variant_t`物件的 。

*pSrc*<br/>
要轉換之 `_variant_t` 物件的指標。 如果此值為 NULL,則轉換將就地完成。

## <a name="remarks"></a>備註

此成員函數將`_variant_t`物件轉換為`VARTYPE`指示的 。 如果*pSrc*為 NULL,則轉換就`_variant_t`位,否則 此物件將從*pSrc*複製,然後轉換。

**結束微軟的**

## <a name="see-also"></a>另請參閱

[_variant_t類](../cpp/variant-t-class.md)
