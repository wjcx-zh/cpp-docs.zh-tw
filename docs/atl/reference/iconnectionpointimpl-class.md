---
title: "IConnectionPointImpl Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL.IConnectionPointImpl"
  - "IConnectionPointImpl"
  - "ATL::IConnectionPointImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "連接點 [C++], 實作"
  - "IConnectionPointImpl class"
ms.assetid: 27992115-3b86-45dd-bc9e-54f32876c557
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# IConnectionPointImpl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別會實作連接點。  
  
## 語法  
  
```  
  
      template<  
   class T,  
   const IID* piid,  
   class CDV = CComDynamicUnkArray   
>  
class ATL_NO_VTABLE IConnectionPointImpl :  
   public _ICPLocator< piid >  
```  
  
#### 參數  
 `T`  
 您的類別，衍生自 `IConnectionPointImpl`。  
  
 `piid`  
 對連接點物件表示介面的 IID 的指標。  
  
 `CDV`  
 管理連接的類別。  預設值為 [CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md)，允許無限制的連接。  您也可以使用 [CComUnkArray](../../atl/reference/ccomunkarray-class.md)，指定連接的固定項目數。  
  
## Members  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[IConnectionPointImpl::Advise](../Topic/IConnectionPointImpl::Advise.md)|在連接點和接收之間的連接。|  
|[IConnectionPointImpl::EnumConnections](../Topic/IConnectionPointImpl::EnumConnections.md)|建立列舉值在連接點的連接逐一查看。|  
|[IConnectionPointImpl::GetConnectionInterface](../Topic/IConnectionPointImpl::GetConnectionInterface.md)|擷取連接點表示介面的 IID。|  
|[IConnectionPointImpl::GetConnectionPointContainer](../Topic/IConnectionPointImpl::GetConnectionPointContainer.md)|擷取介面指標。可連接物件。|  
|[IConnectionPointImpl::Unadvise](../Topic/IConnectionPointImpl::Unadvise.md)|結束藉由 `Advise`先前建立的連接。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[IConnectionPointImpl::m\_vec](../Topic/IConnectionPointImpl::m_vec.md)|處理連接點的連接。|  
  
## 備註  
 `IConnectionPointImpl` 實作連接點，可讓物件將一個輸出介面在用戶端。  用戶端實作在呼叫接收的物件的介面。  
  
 使用 ATL [IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md) 實作可連接物件。  在可連接物件內的每個連接點表示輸出介面，由 `piid`。  類別 *CDV* 處理連接點和接收之間的連接。  每個連結都有專門 Cookie 「{0}」。  
  
 如需使用連接點的詳細資訊，請參閱 ATL 中本文 [連接點](../../atl/atl-connection-points.md)。  
  
## 繼承階層架構  
 `_ICPLocator`  
  
 `IConnectionPointImpl`  
  
## 需求  
 **Header:** atlcom.h  
  
## 請參閱  
 [IConnectionPoint](http://msdn.microsoft.com/library/windows/desktop/ms694318)   
 [Class Overview](../../atl/atl-class-overview.md)