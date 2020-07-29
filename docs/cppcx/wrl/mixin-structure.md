---
title: MixIn 結構
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::MixIn
helpviewer_keywords:
- MixIn structure
ms.assetid: 47e2df9b-3a2e-4ae8-8ba3-b1fd3aa73566
ms.openlocfilehash: cfa03706bc6030b337009f7228466a26e242aa6b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221532"
---
# <a name="mixin-structure"></a>MixIn 結構

確保執行階段類別衍生自 Windows 執行階段介面 (若有的話)，然後才是傳統 COM 介面。

## <a name="syntax"></a>語法

```cpp
template<
    typename Derived,
    typename MixInType,
    bool hasImplements = __is_base_of(Details::ImplementsBase, MixInType)
>
struct MixIn;
```

### <a name="parameters"></a>參數

*衍生*<br/>
衍生自[Implements](implements-structure.md)結構的類型。

*MixInType*<br/>
基底類型。

*hasImplements*<br/>
**`true`** 如果*MixInType*衍生自目前的實作為基底類型，則為，**`false`** 否則為。

## <a name="remarks"></a>備註

如果類別衍生自 Windows 執行階段和類別 COM 介面，則類別宣告清單必須先列出任何 Windows 執行階段介面，然後是任何傳統的 COM 介面。 **MixIn**可確保以正確的順序指定介面。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`MixIn`

## <a name="requirements"></a>需求

**標頭：** implements。h

**命名空間：** Microsoft::WRL

## <a name="see-also"></a>另請參閱

[Microsoft：： WRL 命名空間](microsoft-wrl-namespace.md)
