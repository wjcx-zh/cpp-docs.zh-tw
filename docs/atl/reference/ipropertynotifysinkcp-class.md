---
title: IPropertyNotifySinkCP 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IPropertyNotifySinkCP
- atlctl/ATL::IPropertyNotifySinkCP
dev_langs:
- C++
helpviewer_keywords:
- connection points [C++], managing
- sinks, notifying of changes
- IPropertyNotifySinkCP class
ms.assetid: 1b41445e-bc88-4fa6-bb62-d68aacec2bd5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 13ddd14ad530fa2b7ce2892ce8838b27e307381f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46135758"
---
# <a name="ipropertynotifysinkcp-class"></a>IPropertyNotifySinkCP 類別

這個類別會公開[IPropertyNotifySink](/windows/desktop/api/ocidl/nn-ocidl-ipropertynotifysink)作為可連接物件上的連出介面的介面。

> [!IMPORTANT]
>  此類別和其成員不能在 Windows 執行階段中執行的應用程式。

## <a name="syntax"></a>語法

```
template<class T, class CDV = CComDynamicUnkArray>
class IPropertyNotifySinkCP 
   : public IConnectionPointImpl<T, &IID_IPropertyNotifySink, CDV>
```

#### <a name="parameters"></a>參數

*T*<br/>
您的類別，衍生自`IPropertyNotifySinkCP`。

*CDV*<br/>
類別可管理的連接點和其接收器之間的連線。 預設值是[CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md)，可讓連接無限制。 您也可以使用[CComUnkArray](../../atl/reference/ccomunkarray-class.md)，指定固定的連接數目。

## <a name="remarks"></a>備註

`IPropertyNotifySinkCP` 繼承其基底類別，透過的所有方法[IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md)。

[IPropertyNotifySink](/windows/desktop/api/ocidl/nn-ocidl-ipropertynotifysink)介面可讓接收物件，以接收有關屬性變更通知。 類別`IPropertyNotifySinkCP`會將此介面公開為可連接物件上的連出介面。 用戶端必須實作`IPropertyNotifySink`接收上的方法。

衍生您的類別，從`IPropertyNotifySinkCP`當您要建立連接點，表示`IPropertyNotifySink`介面。

如需有關如何使用 ATL 中的連接點的詳細資訊，請參閱[連接點](../../atl/atl-connection-points.md)。

## <a name="requirements"></a>需求

**標頭：** atlctl.h

## <a name="see-also"></a>另請參閱

[IConnectionPointImpl 類別](../../atl/reference/iconnectionpointimpl-class.md)<br/>
[IConnectionPointContainerImpl 類別](../../atl/reference/iconnectionpointcontainerimpl-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)
