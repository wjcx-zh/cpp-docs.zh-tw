---
title: "IPropertyNotifySinkCP Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "IPropertyNotifySinkCP"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "連接點 [C++], 管理"
  - "IPropertyNotifySinkCP class"
  - "sinks, notifying of changes"
ms.assetid: 1b41445e-bc88-4fa6-bb62-d68aacec2bd5
caps.latest.revision: 21
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IPropertyNotifySinkCP Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別會公開 \(Expose\) [IPropertyNotifySink](http://msdn.microsoft.com/library/windows/desktop/ms692638) 介面做為可連接物件的輸出介面。  
  
> [!IMPORTANT]
>  這個類別和其成員不能用於 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]執行的應用程式。  
  
## 語法  
  
```  
  
      template< class   
      T  
      , class  
      CDV   
      = CComDynamicUnkArray >  
class IPropertyNotifySinkCP :   
public IConnectionPointImpl< T, &IID_IPropertyNotifySink, CDV>  
```  
  
#### 參數  
 `T`  
 您的類別，衍生自 `IPropertyNotifySinkCP`。  
  
 `CDV`  
 處理連接點和其接收之間的連接的類別。  預設值為 [CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md)，允許無限制的連接。  您也可以使用 [CComUnkArray](../../atl/reference/ccomunkarray-class.md)，指定連接的固定項目數。  
  
## 備註  
 `IPropertyNotifySinkCP` 傳遞給它的基底類別， [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md)繼承任何方法。  
  
 [IPropertyNotifySink](http://msdn.microsoft.com/library/windows/desktop/ms692638) 介面允許接收物件接收有關屬性變更的通知。  類別 `IPropertyNotifySinkCP` 公開此介面做為可連接物件的輸出介面。  用戶端必須執行所接收到 `IPropertyNotifySink` 方法。  
  
 從 `IPropertyNotifySinkCP` 衍生您的類別時，您要建立一 `IPropertyNotifySink` 介面的連接點 \(Connection Point\) 時。  
  
 如需使用連接點的詳細資訊，請參閱 ATL 中本文 [連接點](../../atl/atl-connection-points.md)。  
  
## 需求  
 **Header:** atlctl.h  
  
## 請參閱  
 [IConnectionPointImpl Class](../../atl/reference/iconnectionpointimpl-class.md)   
 [IConnectionPointContainerImpl Class](../../atl/reference/iconnectionpointcontainerimpl-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)