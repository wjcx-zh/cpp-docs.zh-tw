---
title: "IObjectWithSiteImpl Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL::IObjectWithSiteImpl"
  - "ATL.IObjectWithSiteImpl<T>"
  - "IObjectWithSiteImpl"
  - "ATL.IObjectWithSiteImpl"
  - "ATL::IObjectWithSiteImpl<T>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IObjectWithSiteImpl class"
ms.assetid: 4e1f774f-bc3d-45ee-9a1c-c3533a511588
caps.latest.revision: 18
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IObjectWithSiteImpl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別提供方法讓物件與中的網站進行通訊。  
  
## 語法  
  
```  
  
      template<  
   class T   
>  
class ATL_NO_VTABLE IObjectWithSiteImpl :  
   public IObjectWithSite  
```  
  
#### 參數  
 `T`  
 您的類別，衍生自 `IObjectWithSiteImpl`。  
  
## Members  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[IObjectWithSiteImpl::GetSite](../Topic/IObjectWithSiteImpl::GetSite.md)|查詢介面指標的網站。|  
|[IObjectWithSiteImpl::SetChildSite](../Topic/IObjectWithSiteImpl::SetChildSite.md)|提供物件提供網站的 **IUnknown** 指標。|  
|[IObjectWithSiteImpl::SetSite](../Topic/IObjectWithSiteImpl::SetSite.md)|提供物件提供網站的 **IUnknown** 指標。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[IObjectWithSiteImpl::m\_spUnkSite](../Topic/IObjectWithSiteImpl::m_spUnkSite.md)|管理網站的 **IUnknown** 指標。|  
  
## 備註  
 [IObjectWithSite](http://msdn.microsoft.com/library/windows/desktop/ms693765) 介面允許物件與中的網站進行通訊。  類別 `IObjectWithSiteImpl` 提供這個介面的預設實作並透過傳送訊息至實作 **IUnknown** 傾印裝置偵錯組建。  
  
 `IObjectWithSiteImpl` 指定這兩個方法。  用戶端會先呼叫方法，傳遞做為 `SetSite`網站的 **IUnknown** 指標。  這個指標在物件中儲存，而且可以傳遞至 `GetSite`的呼叫之後擷取。  
  
 通常，您會從 `IObjectWithSiteImpl` 衍生您的類別時，您要建立不是控制項的物件中。  對於控制項，從 [IOleObjectImpl](../../atl/reference/ioleobjectimpl-class.md)衍生您的類別，也提供網站指標。  從 `IObjectWithSiteImpl` 和 `IOleObjectImpl`不要衍生自類別。  
  
## 繼承階層架構  
 `IObjectWithSite`  
  
 `IObjectWithSiteImpl`  
  
## 需求  
 **Header:** atlcom.h  
  
## 請參閱  
 [Class Overview](../../atl/atl-class-overview.md)