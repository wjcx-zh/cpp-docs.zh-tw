---
title: "IConnectionPointContainerImpl Class | Microsoft Docs"
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
  - "ATL::IConnectionPointContainerImpl"
  - "ATL.IConnectionPointContainerImpl"
  - "ATL.IConnectionPointContainerImpl<T>"
  - "IConnectionPointContainerImpl"
  - "ATL::IConnectionPointContainerImpl<T>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "connectable objects"
  - "連接點 [C++], container"
  - "IConnectionPointContainerImpl class"
ms.assetid: 10db5a8d-8be9-4d9d-8a82-8ab9ffe3e9d6
caps.latest.revision: 19
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IConnectionPointContainerImpl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別會實作連接點容器 [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md) 管理物件的集合。  
  
## 語法  
  
```  
  
      template<  
   class T   
>  
class ATL_NO_VTABLE IConnectionPointContainerImpl :   
   public IConnectionPointContainer  
```  
  
#### 參數  
 `T`  
 您的類別，衍生自 `IConnectionPointContainerImpl`。  
  
## Members  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[IConnectionPointContainerImpl::EnumConnectionPoints](../Topic/IConnectionPointContainerImpl::EnumConnectionPoints.md)|建立列舉值傳入可連接物件支援的連接點逐一查看。|  
|[IConnectionPointContainerImpl::FindConnectionPoint](../Topic/IConnectionPointContainerImpl::FindConnectionPoint.md)|擷取介面指標支援特定 IID 的連接點。|  
  
## 備註  
 `IConnectionPointContainerImpl` 實作連接點容器 [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md) 管理物件的集合。  `IConnectionPointContainerImpl` 提供用戶端可以呼叫來擷取關於可連接物件的詳細資訊的兩種方法:  
  
-   `EnumConnectionPoints` 允許用戶端決定哪些輸出介面物件支援。  
  
-   `FindConnectionPoint` 允許用戶端決定物件是否支援特定的輸出介面。  
  
 如需使用連接點的詳細資訊，請參閱 ATL 中本文 [連接點](../../atl/atl-connection-points.md)。  
  
## 繼承階層架構  
 `IConnectionPointContainer`  
  
 `IConnectionPointContainerImpl`  
  
## 需求  
 **Header:** atlcom.h  
  
## 請參閱  
 [IConnectionPointContainer](http://msdn.microsoft.com/library/windows/desktop/ms683857)   
 [Class Overview](../../atl/atl-class-overview.md)