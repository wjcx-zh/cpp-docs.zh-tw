---
title: "Implementing the Event Handling Interface | Microsoft Docs"
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
  - "ATL, 事件處理"
  - "事件處理, ATL"
  - "介面, event and event sink"
ms.assetid: eb2a5b33-88dc-4ce3-bee0-c5c38ea050d7
caps.latest.revision: 10
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Implementing the Event Handling Interface
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

ATL 協助您對於處理事件所需的全部三個項目的:實作事件介面，通知事件來源和 unadvising 事件來源。  您將需要其他的確切步驟取決於事件介面的類型和應用程式的效能需求。  
  
 實作使用 ATL 的介面最常見的方式是:  
  
-   直接衍生自的自訂介面。  
  
-   衍生自之型別描述的雙重介面的 [IDispatchImpl](../atl/reference/idispatchimpl-class.md) 程式庫。  
  
-   衍生自的型別描述所描述之介面的 [IDispEventImpl](../atl/reference/idispeventimpl-class.md) 程式庫。  
  
-   衍生自的型別沒有描述的分配介面的 [IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md) 程式庫，或當您想要將不會載入此型別提升效率特定的資訊。  
  
 如果您實作自訂或雙重介面，您也應該呼叫 [AtlAdvise](../Topic/AtlAdvise.md) 或 [CComPtrBase::Advise](../Topic/CComPtrBase::Advise.md)通知事件來源。  您將需要記錄這個呼叫所傳回的 Cookie。  呼叫會中斷連接的 [AtlUnadvise](../Topic/AtlUnadvise.md) 。  
  
 使用 `IDispEventImpl` 或 `IDispEventSimpleImpl`，如果您實作分配介面 \(Dispinterface\)，您也應該呼叫 [IDispEventSimpleImpl::DispEventAdvise](../Topic/IDispEventSimpleImpl::DispEventAdvise.md)通知事件來源。  呼叫會中斷連接的 [IDispEventSimpleImpl::DispEventUnadvise](../Topic/IDispEventSimpleImpl::DispEventUnadvise.md) 。  
  
 如果您使用 `IDispEventImpl` 為複合控制項的基底類別，在接收對應中的事件來源使用 [CComCompositeControl::AdviseSinkMap](../Topic/CComCompositeControl::AdviseSinkMap.md)會自動通知和輕量的速率。  
  
 `IDispEventImpl` 和 `IDispEventSimpleImpl` 類別處理您的 Cookie。  
  
## 請參閱  
 [事件處理](../atl/event-handling-and-atl.md)