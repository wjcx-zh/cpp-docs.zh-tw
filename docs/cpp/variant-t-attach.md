---
title: _variant_t::Attach
ms.date: 11/04/2016
f1_keywords:
- _variant_t::Attach
- _variant_t.Attach
helpviewer_keywords:
- Attach method [C++]
- VARIANT object [C++], attach
- VARIANT object
ms.assetid: 2f02bd08-2306-4477-aa88-d2a5dee2b859
ms.openlocfilehash: 510267c7ab00fe22a93dc01342def5fc262ddb04
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62166214"
---
# <a name="varianttattach"></a>_variant_t::Attach

**Microsoft 專屬**

附加`VARIANT`物件插入 **_variant_t**物件。

## <a name="syntax"></a>語法

```
void Attach(VARIANT& varSrc);
```

#### <a name="parameters"></a>參數

*varSrc*<br/>
A`VARIANT`物件，以附加至此 **_variant_t**物件。

## <a name="remarks"></a>備註

取得擁有權的`VARIANT`透過封裝方式。 此成員函式會釋放所有現有的封裝`VARIANT`，然後複製提供`VARIANT`，並設定其`VARTYPE`設為 VT_EMPTY 以確定其可以只會釋放資源 **_variant_t**解構函式。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[_variant_t 類別](../cpp/variant-t-class.md)