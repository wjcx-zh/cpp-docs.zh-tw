---
title: ATL 連接點類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 289ff7ae7db1abd6a0a19577a2c567b462a2910e
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43201396"
---
# <a name="atl-connection-point-classes"></a>ATL 連接點類別
ATL 支援的連接點，使用下列類別：  
  
-   [IConnectionPointImpl](../atl/reference/iconnectionpointimpl-class.md)實作連接點。 它所代表之輸出介面的 IID 是做為範本參數傳遞。  
  
-   [IConnectionPointContainerImpl](../atl/reference/iconnectionpointcontainerimpl-class.md)實作連接點容器，並管理清單`IConnectionPointImpl`物件。  
  
-   [IPropertyNotifySinkCP](../atl/reference/ipropertynotifysinkcp-class.md)實作代表您建立的連接點[IPropertyNotifySink](/windows/desktop/api/ocidl/nn-ocidl-ipropertynotifysink)介面。  
  
-   [CComDynamicUnkArray](../atl/reference/ccomdynamicunkarray-class.md)管理任意數目的連接點和其接收器之間的連線。  
  
-   [CComUnkArray](../atl/reference/ccomunkarray-class.md)管理預先定義的範本參數所指定的連接數目。  
  
-   [CFirePropNotifyEvent](../atl/reference/cfirepropnotifyevent-class.md)通知用戶端接收器物件的屬性已變更或將要變更。  
  
-   [IDispEventImpl](../atl/reference/idispeventimpl-class.md)提供 ATL COM 物件的連接點的支援。 這些連接點會對應與事件接收對應，提供您的 COM 物件。  
  
-   [IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md)和事件接收對應，在您的類別，以將事件路由至適當的處理常式函式一起工作。  
  
## <a name="see-also"></a>另請參閱  
 [連接點](../atl/atl-connection-points.md)

