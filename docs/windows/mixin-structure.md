---
title: MixIn 結構 |Microsoft Docs
ms.custom: ''
ms.date: 10/03/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::MixIn
dev_langs:
- C++
helpviewer_keywords:
- MixIn structure
ms.assetid: 47e2df9b-3a2e-4ae8-8ba3-b1fd3aa73566
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e4a9e9eb2804e5abbb3f84ab157043402d48166f
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/04/2018
ms.locfileid: "48789094"
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
型別衍生自[實作](../windows/implements-structure.md)結構。

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

**命名空間：** Microsoft::WRL

## <a name="see-also"></a>另請參閱

[Microsoft::WRL 命名空間](../windows/microsoft-wrl-namespace.md)