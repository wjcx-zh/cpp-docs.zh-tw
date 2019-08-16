---
title: ATL 連接點類別
ms.date: 11/04/2016
helpviewer_keywords:
- CFirePropNotifyEvent class, connection point classes
- connection points [C++], ATL classes
- ATL, connection points
- CComDynamicUnkArray class, connection point classes
- CFirePropNotifyEvent class
- CComUnkArray class, connection point classes
ms.assetid: 9582ba71-7ace-4df4-9c9b-1b0636953efc
ms.openlocfilehash: 8644fc087d7f0a651724c40d2868e96c9b6ec96a
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491817"
---
# <a name="atl-connection-point-classes"></a>ATL 連接點類別

ATL 會使用下列類別來支援連接點:

- [IConnectionPointImpl](../atl/reference/iconnectionpointimpl-class.md)會執行連接點。 它所代表之傳出介面的 IID 會當做範本參數傳遞。

- [IConnectionPointContainerImpl](../atl/reference/iconnectionpointcontainerimpl-class.md)會執行連接點容器, 並管理`IConnectionPointImpl`物件的清單。

- [IPropertyNotifySinkCP](../atl/reference/ipropertynotifysinkcp-class.md)會執行代表[IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink)介面的連接點。

- [CComDynamicUnkArray](../atl/reference/ccomdynamicunkarray-class.md)管理連接點與其接收之間的任意數目的連接。

- [CComUnkArray](../atl/reference/ccomunkarray-class.md)會管理預先定義的連接數目, 如範本參數所指定。

- [CFirePropNotifyEvent](../atl/reference/cfirepropnotifyevent-class.md)會通知用戶端的接收, 物件的屬性已變更或即將變更。

- [IDispEventImpl](../atl/reference/idispeventimpl-class.md)提供 ATL COM 物件連接點的支援。 這些連接點會對應至 COM 物件所提供的事件接收對應。

- [IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md)會與類別中的事件接收器對應搭配運作, 以將事件路由至適當的處理常式函式。

## <a name="see-also"></a>另請參閱

[連接點](../atl/atl-connection-points.md)
