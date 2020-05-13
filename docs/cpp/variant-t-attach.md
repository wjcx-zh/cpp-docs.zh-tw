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
ms.openlocfilehash: d0822dfc730cbbb64f8364e6fa8fe8bc7207f9f9
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81750737"
---
# <a name="_variant_tattach"></a>_variant_t::Attach

**Microsoft 特定的**

將`VARIANT`物件附加到 **_variant_t**物件。

## <a name="syntax"></a>語法

```cpp
void Attach(VARIANT& varSrc);
```

#### <a name="parameters"></a>參數

*varSrc*<br/>
要`VARIANT`附加到此 **_variant_t**物件的物件。

## <a name="remarks"></a>備註

通過封裝獲取`VARIANT`的擁有權。 此成員函數釋放任何現有的`VARIANT`封裝,然後複製`VARIANT`提供的 ,`VARTYPE`並將其 設置到VT_EMPTY以確保其資源只能由 **_variant_t**析構函數釋放。

**結束微軟的**

## <a name="see-also"></a>另請參閱

[_variant_t類](../cpp/variant-t-class.md)
