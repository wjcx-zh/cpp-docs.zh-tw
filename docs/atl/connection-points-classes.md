---
title: "連接點類別 (ATL) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.atl.connection
dev_langs: C++
helpviewer_keywords:
- classes [C++], connection points
- connection points classes
ms.assetid: 076365fa-299a-4dce-84c3-a5dff0e0da1f
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: ef188a5fc03a60c3481477d000662d595b7d4dd9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="connection-points-classes"></a>連接點類別
下列類別會提供支援的連接點：  
  
-   [IConnectionPointContainerImpl](../atl/reference/iconnectionpointcontainerimpl-class.md)實作連接點容器。  
  
-   [IConnectionPointImpl](../atl/reference/iconnectionpointimpl-class.md)實作連接點。  
  
-   [IPropertyNotifySinkCP](../atl/reference/ipropertynotifysinkcp-class.md)實作連接點，代表[IPropertyNotifySink](http://msdn.microsoft.com/library/windows/desktop/ms692638)介面。  
  
-   [CComDynamicUnkArray](../atl/reference/ccomdynamicunkarray-class.md)管理之間的連接點和其接收無限制的連線。  
  
-   [CComUnkArray](../atl/reference/ccomunkarray-class.md)管理固定的數目的連接點和其接收器之間的連接。  
  
-   [CFirePropNotifyEvent](../atl/reference/cfirepropnotifyevent-class.md)通知用戶端接收器物件的屬性已變更或即將變更。  
  
-   [IDispEventImpl](../atl/reference/idispeventimpl-class.md)提供 ATL COM 物件的連接點的支援。 這些連線點會與事件接收對應，提供您的 COM 物件的對應。  
  
-   [IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md)搭配事件接收器的運作方式會對應至適當的處理常式函式的路由事件類別。  
  
## <a name="related-articles"></a>相關文章  
 [連接點](../atl/atl-connection-points.md)  
  
 [事件處理和 ATL](../atl/event-handling-and-atl.md)  
  
## <a name="see-also"></a>另請參閱  
 [類別概觀](../atl/atl-class-overview.md)   
 [連接點巨集](../atl/reference/connection-point-macros.md)   
 [連接點全域函式](../atl/reference/connection-point-global-functions.md)

