---
title: "IServiceProviderImpl Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL::IServiceProviderImpl<T>"
  - "ATL.IServiceProviderImpl<T>"
  - "ATL.IServiceProviderImpl"
  - "ATL::IServiceProviderImpl"
  - "IServiceProviderImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IServiceProvider 介面, ATL 實作"
  - "IServiceProviderImpl class"
ms.assetid: 251254d3-c4ce-40d7-aee0-3d676d1d72f2
caps.latest.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 25
---
# IServiceProviderImpl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別會提供 `IServiceProvider` 介面的預設實作。  
  
## 語法  
  
```  
  
      template <  
   class T  
>   
class ATL_NO_VTABLE IServiceProviderImpl :  
   public IServiceProvider  
```  
  
#### 參數  
 `T`  
 您的類別，衍生自 `IServiceProviderImpl`。  
  
## Members  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[IServiceProviderImpl::QueryService](../Topic/IServiceProviderImpl::QueryService.md)|建立或存取所指定的服務及傳回介面指標指定介面的服務。|  
  
## 備註  
 `IServiceProvider` 介面會尋找其 GUID 指定的服務並傳回所要求介面的介面指標在服務。  類別 `IServiceProviderImpl` 提供這個介面的預設實作。  
  
 **IServiceProviderImpl** 指定一個方法: [QueryService](../Topic/IServiceProviderImpl::QueryService.md)，建立或存取指定的服務並傳回介面指標服務的指定介面。  
  
 `IServiceProviderImpl` 從 [BEGIN\_SERVICE\_MAP](../Topic/BEGIN_SERVICE_MAP.md) 和結尾開始使用服務對應，以 [END\_SERVICE\_MAP](../Topic/END_SERVICE_MAP.md)。  
  
 服務對應包含兩個項目: [SERVICE\_ENTRY](../Topic/SERVICE_ENTRY.md)，指出指定的服務 ID \(SID\) 支援物件和 [SERVICE\_ENTRY\_CHAIN](../Topic/SERVICE_ENTRY_CHAIN.md)，呼叫 `QueryService` 繫結至另一個物件。  
  
## 繼承階層架構  
 `IServiceProvider`  
  
 `IServiceProviderImpl`  
  
## 需求  
 **Header:** atlcom.h  
  
## 請參閱  
 [Class Overview](../../atl/atl-class-overview.md)