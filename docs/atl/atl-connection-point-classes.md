---
title: "ATL Connection Point Classes | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL, 連接點"
  - "CComDynamicUnkArray class, connection point classes"
  - "CComUnkArray class, connection point classes"
  - "CFirePropNotifyEvent class"
  - "CFirePropNotifyEvent class, connection point classes"
  - "連接點 [C++], ATL 類別"
ms.assetid: 9582ba71-7ace-4df4-9c9b-1b0636953efc
caps.latest.revision: 10
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ATL Connection Point Classes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

使用下列 ATL 類別支援連接點:  
  
-   [IConnectionPointImpl](../atl/reference/iconnectionpointimpl-class.md) 實作連接點。  它代表輸出介面的 IID 會當做樣板參數。  
  
-   [IConnectionPointContainerImpl](../atl/reference/iconnectionpointcontainerimpl-class.md) 實作連接點容器和管理 `IConnectionPointImpl` 物件清單。  
  
-   [IPropertyNotifySinkCP](../atl/reference/ipropertynotifysinkcp-class.md) 實作表示 [IPropertyNotifySink](http://msdn.microsoft.com/library/windows/desktop/ms692638) 介面的連接點。  
  
-   [CComDynamicUnkArray](../atl/reference/ccomdynamicunkarray-class.md) 處理連接點和其接收之間的任意數目的介面。  
  
-   [CComUnkArray](../atl/reference/ccomunkarray-class.md) 管理連接的一個預先定義的數值由樣板參數。  
  
-   [CFirePropNotifyEvent](../atl/reference/cfirepropnotifyevent-class.md) 告知用戶端的接收物件的屬性已經變更或將變更。  
  
-   [IDispEventImpl](../atl/reference/idispeventimpl-class.md) 為 ATL COM 物件的連接點的支援。  這些連接點對應與事件接收對應， COM 物件所提供。  
  
-   與事件一起接收對應的[IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md) 工作中的路由事件的類別為適當的處理常式函式。  
  
## 請參閱  
 [連接點](../atl/atl-connection-points.md)