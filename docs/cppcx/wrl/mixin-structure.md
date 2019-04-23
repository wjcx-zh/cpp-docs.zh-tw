---
title: MixIn 結構
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::MixIn
helpviewer_keywords:
- MixIn structure
ms.assetid: 47e2df9b-3a2e-4ae8-8ba3-b1fd3aa73566
ms.openlocfilehash: 16fd6b46d616df7163a304afa7f32ac3c095d398
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59031072"
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
型別衍生自[實作](implements-structure.md)結構。

*MixInType*<br/>
基底類型。

*hasImplements*<br/>
**真**如果*MixInType*是衍生自目前實作的基底類型;**false**否則。

## <a name="remarks"></a>備註

如果類別衍生自 Windows 執行階段和兩種類別的 COM 介面，類別宣告清單都必須先列出的任何 Windows 執行階段介面，則任何傳統的 COM 介面。 **MixIn**可確保以正確的順序，指定介面。

## <a name="inheritance-hierarchy"></a>繼承階層

`MixIn`

## <a name="requirements"></a>需求

**標頭：** implements.h

**命名空間：** Microsoft:: wrl

## <a name="see-also"></a>另請參閱

[Microsoft::WRL 命名空間](microsoft-wrl-namespace.md)