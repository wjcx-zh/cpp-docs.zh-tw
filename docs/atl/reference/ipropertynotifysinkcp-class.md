---
title: IPropertyNotifySinkCP 類別
ms.date: 11/04/2016
f1_keywords:
- IPropertyNotifySinkCP
- atlctl/ATL::IPropertyNotifySinkCP
helpviewer_keywords:
- connection points [C++], managing
- sinks, notifying of changes
- IPropertyNotifySinkCP class
ms.assetid: 1b41445e-bc88-4fa6-bb62-d68aacec2bd5
ms.openlocfilehash: 9838a48b078cbc59a5ae86669ad9f26792d9816e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495631"
---
# <a name="ipropertynotifysinkcp-class"></a>IPropertyNotifySinkCP 類別

這個類別會將[IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink)介面公開為可連線物件上的輸出介面。

> [!IMPORTANT]
>  這個類別及其成員無法在 Windows 執行階段中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
template<class T, class CDV = CComDynamicUnkArray>
class IPropertyNotifySinkCP
   : public IConnectionPointImpl<T, &IID_IPropertyNotifySink, CDV>
```

#### <a name="parameters"></a>參數

*T*<br/>
衍生自`IPropertyNotifySinkCP`的類別。

*CDV*<br/>
管理連接點與其接收之間連接的類別。 預設值為[CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md), 允許無限制的連接。 您也可以使用[CComUnkArray](../../atl/reference/ccomunkarray-class.md), 它會指定固定的連線數目。

## <a name="remarks"></a>備註

`IPropertyNotifySinkCP`會透過其基類[IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md)繼承所有方法。

[IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink)介面可讓接收物件收到有關屬性變更的通知。 類別`IPropertyNotifySinkCP`會將這個介面公開為可連線物件上的輸出介面。 用戶端必須在接收`IPropertyNotifySink`上執行方法。

當您想要`IPropertyNotifySinkCP`建立`IPropertyNotifySink`代表介面的連接點時, 請從衍生您的類別。

如需在 ATL 中使用連接點的詳細資訊, 請參閱[連接點](../../atl/atl-connection-points.md)一文。

## <a name="requirements"></a>需求

**標頭:** atlctl。h

## <a name="see-also"></a>另請參閱

[IConnectionPointImpl 類別](../../atl/reference/iconnectionpointimpl-class.md)<br/>
[IConnectionPointContainerImpl 類別](../../atl/reference/iconnectionpointcontainerimpl-class.md)<br/>
[類別總覽](../../atl/atl-class-overview.md)
