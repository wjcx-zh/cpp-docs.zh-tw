---
title: 連接點類別 (ATL)
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- classes [C++], connection points
- connection points classes
ms.assetid: 076365fa-299a-4dce-84c3-a5dff0e0da1f
ms.openlocfilehash: 0dba06b072e1e9ca545ccbea196fcfe371b02157
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492450"
---
# <a name="connection-points-classes"></a>連接點類別

下列類別提供連接點的支援:

- [IConnectionPointContainerImpl](../atl/reference/iconnectionpointcontainerimpl-class.md)執行連接點容器。

- [IConnectionPointImpl](../atl/reference/iconnectionpointimpl-class.md)執行連接點。

- [IPropertyNotifySinkCP](../atl/reference/ipropertynotifysinkcp-class.md)執行代表[IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink)介面的連接點。

- [CComDynamicUnkArray](../atl/reference/ccomdynamicunkarray-class.md)管理連接點與其接收之間的無限制連接。

- [CComUnkArray](../atl/reference/ccomunkarray-class.md)管理連接點與其接收之間的固定連接數目。

- [CFirePropNotifyEvent](../atl/reference/cfirepropnotifyevent-class.md)通知用戶端的接收, 物件的屬性已變更或即將變更。

- [IDispEventImpl](../atl/reference/idispeventimpl-class.md)提供 ATL COM 物件連接點的支援。 這些連接點會對應至 COM 物件所提供的事件接收對應。

- [IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md)與類別中的事件接收器對應搭配使用, 以將事件路由至適當的處理函式。

## <a name="related-articles"></a>相關文章

[連接點](../atl/atl-connection-points.md)

[事件處理和 ATL](../atl/event-handling-and-atl.md)

## <a name="see-also"></a>另請參閱

[類別總覽](../atl/atl-class-overview.md)<br/>
[連接點巨集](../atl/reference/connection-point-macros.md)<br/>
[連接點全域函式](../atl/reference/connection-point-global-functions.md)
