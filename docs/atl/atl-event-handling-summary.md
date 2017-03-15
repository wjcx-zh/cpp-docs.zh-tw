---
title: "ATL Event Handling Summary | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "事件處理, 實作"
ms.assetid: e8b47ef0-0bdc-47ff-9dd6-34df11dde9a2
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# ATL Event Handling Summary
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

一般而言，處理 COM 事件是相當簡單的程序。  有三個主要步驟:  
  
-   實作在物件的事件介面。  
  
-   建議您事件來源的物件要接收事件。  
  
-   Unadvise 事件來源，當您的物件不再需要接收事件。  
  
## 實作介面  
 使用 ATL 實作介面，有四種主要方式。  
  
|衍生自|適用於介面型別|您必須實作所有 methods\*|需要型別程式庫在執行階段|  
|---------|-------------|-----------------------|------------------|  
|介面|Vtable|是|否|  
|[IDispatchImpl](../atl/reference/idispatchimpl-class.md)|雙重|是|是|  
|[IDispEventImpl](../atl/reference/idispeventimpl-class.md)|分配介面|否|是|  
|[IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md)|分配介面|否|否|  
  
 \*在使用 ATL 支援類別中的時，就不需要手動執行 **IUnknown** 或 `IDispatch` 方法。  
  
## 建議和 Unadvising 事件來源  
 使用 ATL，會通知和 unadvising 事件來源三種主要方式。  
  
|告知函式|Unadvise 函式|適用。|要求您記錄 Cookie?|註解|  
|----------|-----------------|---------|-------------------|--------|  
|[AtlAdvise](../Topic/AtlAdvise.md)， [CComPtrBase::Advise](../Topic/CComPtrBase::Advise.md)|[AtlUnadvise](../Topic/AtlUnadvise.md)|Vtable 或雙重介面|是|`AtlAdvise` 是全域 ATL 函式。  [CComPtr](../atl/reference/ccomptr-class.md) 和 [CComQIPtr](../atl/reference/ccomqiptr-class.md)使用`CComPtrBase::Advise` 。|  
|[IDispEventSimpleImpl::DispEventAdvise](../Topic/IDispEventSimpleImpl::DispEventAdvise.md)|[IDispEventSimpleImpl::DispEventUnadvise](../Topic/IDispEventSimpleImpl::DispEventUnadvise.md)|[IDispEventImpl](../atl/reference/idispeventimpl-class.md) 或 [IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md)|否|少數參數小於 `AtlAdvise` ，因為基底類別完成更多工作。|  
|[CComCompositeControl::AdviseSinkMap \(True\)](../Topic/CComCompositeControl::AdviseSinkMap.md)|[CComCompositeControl::AdviseSinkMap \(錯誤\)](../Topic/CComCompositeControl::AdviseSinkMap.md)|在複合控制項的 ActiveX 控制項|否|`CComCompositeControl::AdviseSinkMap` 建議在事件接收對應中的所有項目。  相同的函式 unadvises 輸入。  這個方法是由 `CComCompositeControl` 類別自動呼叫。|  
|[CAxDialogImpl::AdviseSinkMap \(True\)](../Topic/CAxDialogImpl::AdviseSinkMap.md)|[CAxDialogImpl::AdviseSinkMap \(錯誤\)](../Topic/CAxDialogImpl::AdviseSinkMap.md)|在  對話方塊中的 ActiveX 控制項|否|在`CAxDialogImpl::AdviseSinkMap` 對話方塊資源建議和 unadvises 所有 ActiveX 控制項。  這會自動進行。|  
  
## 請參閱  
 [事件處理](../atl/event-handling-and-atl.md)   
 [Supporting IDispEventImpl](../atl/supporting-idispeventimpl.md)