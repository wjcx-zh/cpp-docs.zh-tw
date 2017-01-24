---
title: "Connection Points Classes | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.atl.connection"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "類別 [C++], 連接點"
  - "connection points classes"
ms.assetid: 076365fa-299a-4dce-84c3-a5dff0e0da1f
caps.latest.revision: 10
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Connection Points Classes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下列類別會用於連接點的支援:  
  
-   [IConnectionPointContainerImpl](../atl/reference/iconnectionpointcontainerimpl-class.md) 實作連接點容器。  
  
-   [IConnectionPointImpl](../atl/reference/iconnectionpointimpl-class.md) 實作連接點。  
  
-   [IPropertyNotifySinkCP](../atl/reference/ipropertynotifysinkcp-class.md) 實作表示 [IPropertyNotifySink](http://msdn.microsoft.com/library/windows/desktop/ms692638) 介面的連接點。  
  
-   [CComDynamicUnkArray](../atl/reference/ccomdynamicunkarray-class.md) 處理連接點和其接收之間的無限的連接。  
  
-   [CComUnkArray](../atl/reference/ccomunkarray-class.md) 處理連接固定數目的連接點和其接收之間的。  
  
-   [CFirePropNotifyEvent](../atl/reference/cfirepropnotifyevent-class.md) 告知用戶端的接收物件的屬性已經變更或將變更。  
  
-   [IDispEventImpl](../atl/reference/idispeventimpl-class.md) 為 ATL COM 物件的連接點的支援。  這些連接點對應與事件接收對應， COM 物件所提供。  
  
-   與事件一起接收對應的[IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md) 工作中的路由事件的類別為適當的處理常式函式。  
  
## 相關文件  
 [連接點](../atl/atl-connection-points.md)  
  
 [事件處理常式和 ATL](../atl/event-handling-and-atl.md)  
  
## 請參閱  
 [Class Overview](../atl/atl-class-overview.md)   
 [Connection Point Macros](../atl/reference/connection-point-macros.md)   
 [Connection Point Global Functions](../atl/reference/connection-point-global-functions.md)