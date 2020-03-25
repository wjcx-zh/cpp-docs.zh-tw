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
ms.openlocfilehash: 3792ed4d0fcd86c4a4e846771c450413fda130b5
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187761"
---
# <a name="_variant_tattach"></a>_variant_t::Attach

**Microsoft 專屬**

將 `VARIANT` 物件附加至 **_variant_t**物件。

## <a name="syntax"></a>語法

```
void Attach(VARIANT& varSrc);
```

#### <a name="parameters"></a>參數

*varSrc*<br/>
要附加至這個 **_variant_t**物件的 `VARIANT` 物件。

## <a name="remarks"></a>備註

藉由封裝來取得 `VARIANT` 的擁有權。 此成員函式會釋放任何現有的封裝 `VARIANT`，然後複製提供的 `VARIANT`，並將其 `VARTYPE` 設定為 VT_EMPTY，以確保其資源只能由 **_variant_t**的析構函式釋放。

**END Microsoft 特定的**

## <a name="see-also"></a>另請參閱

[_variant_t 類別](../cpp/variant-t-class.md)
