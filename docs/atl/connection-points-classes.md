---
title: 連接點類別 (ATL) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- vc.atl.connection
dev_langs:
- C++
helpviewer_keywords:
- classes [C++], connection points
- connection points classes
ms.assetid: 076365fa-299a-4dce-84c3-a5dff0e0da1f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 490084ef16afb1f00f05bea07f95d13209661343
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46024343"
---
# <a name="connection-points-classes"></a>連接點類別

下列類別會提供支援的連接點：

- [IConnectionPointContainerImpl](../atl/reference/iconnectionpointcontainerimpl-class.md)實作連接點容器。

- [IConnectionPointImpl](../atl/reference/iconnectionpointimpl-class.md)實作連接點。

- [IPropertyNotifySinkCP](../atl/reference/ipropertynotifysinkcp-class.md)實作代表您建立的連接點[IPropertyNotifySink](/windows/desktop/api/ocidl/nn-ocidl-ipropertynotifysink)介面。

- [CComDynamicUnkArray](../atl/reference/ccomdynamicunkarray-class.md)管理無限制的連接點和其接收器之間的連線。

- [CComUnkArray](../atl/reference/ccomunkarray-class.md)管理固定的連接點和其接收器之間的連線數目。

- [CFirePropNotifyEvent](../atl/reference/cfirepropnotifyevent-class.md)通知用戶端接收器物件的屬性已變更或將要變更。

- [IDispEventImpl](../atl/reference/idispeventimpl-class.md)提供 ATL COM 物件的連接點的支援。 這些連接點會對應與事件接收對應，提供您的 COM 物件。

- [IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md)事件路由傳送至適當的處理常式函式類別中對應的事件接收器搭配運作。

## <a name="related-articles"></a>相關文章

[連接點](../atl/atl-connection-points.md)

[事件處理和 ATL](../atl/event-handling-and-atl.md)

## <a name="see-also"></a>另請參閱

[類別概觀](../atl/atl-class-overview.md)<br/>
[連接點巨集](../atl/reference/connection-point-macros.md)<br/>
[連接點全域函式](../atl/reference/connection-point-global-functions.md)

