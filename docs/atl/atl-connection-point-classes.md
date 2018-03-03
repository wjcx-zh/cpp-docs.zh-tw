---
title: "ATL 連接點類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- CFirePropNotifyEvent class, connection point classes
- connection points [C++], ATL classes
- ATL, connection points
- CComDynamicUnkArray class, connection point classes
- CFirePropNotifyEvent class
- CComUnkArray class, connection point classes
ms.assetid: 9582ba71-7ace-4df4-9c9b-1b0636953efc
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9845fdffdd951809ee7127c5fec86097a6219354
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="atl-connection-point-classes"></a>ATL 連接點類別
ATL 連接點，才能使用下列類別：  
  
-   [IConnectionPointImpl](../atl/reference/iconnectionpointimpl-class.md)實作連接點。 它所代表之輸出介面的 IID 是做為範本參數傳遞。  
  
-   [IConnectionPointContainerImpl](../atl/reference/iconnectionpointcontainerimpl-class.md)實作連接點容器，並管理清單`IConnectionPointImpl`物件。  
  
-   [IPropertyNotifySinkCP](../atl/reference/ipropertynotifysinkcp-class.md)實作連接點，代表[IPropertyNotifySink](http://msdn.microsoft.com/library/windows/desktop/ms692638)介面。  
  
-   [CComDynamicUnkArray](../atl/reference/ccomdynamicunkarray-class.md)管理任意數目的連接點和其接收器之間的連接。  
  
-   [CComUnkArray](../atl/reference/ccomunkarray-class.md)管理預先定義的範本參數所指定的連接數目。  
  
-   [CFirePropNotifyEvent](../atl/reference/cfirepropnotifyevent-class.md)通知用戶端接收器物件的屬性已變更或即將變更。  
  
-   [IDispEventImpl](../atl/reference/idispeventimpl-class.md)提供 ATL COM 物件的連接點的支援。 這些連線點會與事件接收對應，提供您的 COM 物件的對應。  
  
-   [IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md)事件接收對應至適當的處理常式函式的路由事件類別中一起運作。  
  
## <a name="see-also"></a>請參閱  
 [連接點](../atl/atl-connection-points.md)

