---
title: _variant_t::ChangeType |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _variant_t::ChangeType
- _variant_t.ChangeType
dev_langs:
- C++
helpviewer_keywords:
- ChangeType method [C++]
- VARIANT object [C++], ChangeType
- VARIANT object
ms.assetid: 829d2eeb-3338-4a88-9dce-0ca145f47aac
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5a2883cba0d04bbed38ec44e8d00fdab0d4d5695
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46021040"
---
# <a name="varianttchangetype"></a>_variant_t::ChangeType

**Microsoft 專屬**

變更的型別`_variant_t`指定的物件`VARTYPE`。

## <a name="syntax"></a>語法

```
void ChangeType(
   VARTYPE vartype,
   const _variant_t* pSrc = NULL
);
```

#### <a name="parameters"></a>參數

*vartype*<br/>
`VARTYPE`這個`_variant_t`物件。

*pSrc*<br/>
要轉換之 `_variant_t` 物件的指標。 如果這個值是 NULL，就會就地進行轉換。

## <a name="remarks"></a>備註

此成員函式會轉換`_variant_t`到指定的物件`VARTYPE`。 如果*pSrc*是 NULL 時，轉換已就地完成，否則這`_variant_t`物件會從複製*pSrc* ，然後再轉換。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[_variant_t 類別](../cpp/variant-t-class.md)