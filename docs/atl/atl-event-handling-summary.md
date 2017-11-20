---
title: "ATL 事件處理摘要 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: event handling, implementing
ms.assetid: e8b47ef0-0bdc-47ff-9dd6-34df11dde9a2
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 8c4aec5679ae7a880bd5305037e880de9ff7d93a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="atl-event-handling-summary"></a>ATL 事件處理摘要
一般情況下，處理 COM 事件是相當簡單的程序。 有三個主要步驟：  
  
-   在物件上實作事件介面。  
  
-   您的物件，想要接收事件通知事件來源。  
  
-   當物件不再需要接收事件時，請取消通知的事件來源。  
  
## <a name="implementing-the-interface"></a>實作介面  
 有四個主要的方式實作介面使用 ATL 的  
  
|衍生自|適用於介面類型|您必須實作所有方法 *|在執行階段需要型別程式庫|  
|-----------------|---------------------------------|---------------------------------------------|-----------------------------------------|  
|介面|Vtable|是|否|  
|[IDispatchImpl](../atl/reference/idispatchimpl-class.md)|雙重|是|是|  
|[IDispEventImpl](../atl/reference/idispeventimpl-class.md)|Dispinterface|否|是|  
|[IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md)|Dispinterface|否|否|  
  
 \*當使用 ATL 支援類別，您永遠不會實作所需**IUnknown**或`IDispatch`方法以手動方式。  
  
## <a name="advising-and-unadvising-the-event-source"></a>通知和取消通知的事件來源  
 有三個層面的通知和取消通知使用 ATL 的事件來源  
  
|通知函式|取消通知函式|最適合搭配使用|需要您追蹤的 cookie|註解|  
|---------------------|-----------------------|--------------------------------|---------------------------------------------|--------------|  

|[AtlAdvise](reference/connection-point-global-functions.md#atladvise)， [CComPtrBase::Advise](../atl/reference/ccomptrbase-class.md#advise)|[AtlUnadvise](reference/connection-point-global-functions.md#atlunadvise)|Vtable 或雙重介面 |[是] |`AtlAdvise`是全域的 ATL 函式。 `CComPtrBase::Advise`正由[CComPtr](../atl/reference/ccomptr-class.md)和[CComQIPtr](../atl/reference/ccomqiptr-class.md)。 |  

|[IDispEventSimpleImpl::DispEventAdvise](../atl/reference/idispeventsimpleimpl-class.md#dispeventadvise)|[IDispEventSimpleImpl::DispEventUnadvise](../atl/reference/idispeventsimpleimpl-class.md#dispeventunadvise)|[IDispEventImpl](../atl/reference/idispeventimpl-class.md)或[IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md)|否 |較少的參數，比`AtlAdvise`因為基底類別會更多工作。 |  
|[CComCompositeControl::AdviseSinkMap(TRUE)](../atl/reference/ccomcompositecontrol-class.md#advisesinkmap)|[CComCompositeControl::AdviseSinkMap(FALSE)](../atl/reference/ccomcompositecontrol-class.md#advisesinkmap)|複合控制項中的 ActiveX 控制項 |否 |`CComCompositeControl::AdviseSinkMap`建議的所有項目在事件接收對應。 相同的函式取消通知的項目。 這個方法就會呼叫自動`CComCompositeControl`類別。 |  
|[CAxDialogImpl::AdviseSinkMap(TRUE)](../atl/reference/caxdialogimpl-class.md#advisesinkmap)|[CAxDialogImpl::AdviseSinkMap(FALSE)](../atl/reference/caxdialogimpl-class.md#advisesinkmap)|在對話方塊中的 ActiveX 控制項 |否 |`CAxDialogImpl::AdviseSinkMap`建議和取消通知對話方塊資源中的所有 ActiveX 控制項。 這會為您自動完成。 |  
  
## <a name="see-also"></a>另請參閱  
 [事件處理](../atl/event-handling-and-atl.md)   
 [支援 IDispEventImpl](../atl/supporting-idispeventimpl.md)

