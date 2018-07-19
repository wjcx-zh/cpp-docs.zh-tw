---
title: ATL 事件處理摘要 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- event handling, implementing
ms.assetid: e8b47ef0-0bdc-47ff-9dd6-34df11dde9a2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 743939683d212de529816a165907e12063df03be
ms.sourcegitcommit: 76fd30ff3e0352e2206460503b61f45897e60e4f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/13/2018
ms.locfileid: "39027189"
---
# <a name="atl-event-handling-summary"></a>ATL 事件處理摘要
一般情況下，處理 COM 事件是相當簡單的程序。 有三個主要步驟：  
  
-   在物件上實作事件介面。  
  
-   建議您物件想要接收事件的事件來源。  
  
-   當您的物件不再需要以接收事件時，請取消通知事件來源。  
  
## <a name="implementing-the-interface"></a>實作介面  
 有四個主要的方式來實作使用 ATL 的介面  
  
|衍生自|適用於介面類型|您必須實作所有方法 *|在執行階段需要型別程式庫|  
|-----------------|---------------------------------|---------------------------------------------|-----------------------------------------|  
|介面|Vtable|[是]|否|  
|[IDispatchImpl](../atl/reference/idispatchimpl-class.md)|雙重|[是]|[是]|  
|[IDispEventImpl](../atl/reference/idispeventimpl-class.md)|分配介面 (Dispinterface)|否|[是]|  
|[IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md)|分配介面 (Dispinterface)|否|否|  
  
 \* 當您使用 ATL 支援類別，您永遠不會實作所需`IUnknown`或`IDispatch`方法以手動方式。  
  
## <a name="advising-and-unadvising-the-event-source"></a>通知和取消通知的事件來源  
 有三種主要方式通知和取消通知使用 ATL 的事件來源  
  
|通知函式|取消通知函式|最適合搭配使用|您必須要追蹤的 cookie|註解|  
|---------------------|-----------------------|--------------------------------|---------------------------------------------|--------------|
|[AtlAdvise](reference/connection-point-global-functions.md#atladvise)， [CComPtrBase::Advise](../atl/reference/ccomptrbase-class.md#advise)|[AtlUnadvise](reference/connection-point-global-functions.md#atlunadvise)|Vtable 或雙重介面|[是]|`AtlAdvise` 是全域的 ATL 函式。 `CComPtrBase::Advise` 由[CComPtr](../atl/reference/ccomptr-class.md)並[CComQIPtr](../atl/reference/ccomqiptr-class.md)。|  
|[IDispEventSimpleImpl::DispEventAdvise](../atl/reference/idispeventsimpleimpl-class.md#dispeventadvise)|[IDispEventSimpleImpl::DispEventUnadvise](../atl/reference/idispeventsimpleimpl-class.md#dispeventunadvise)|[IDispEventImpl](../atl/reference/idispeventimpl-class.md)或[IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md)|否|較少的參數，比`AtlAdvise`因為基底類別沒有更多工作。|  
|[CComCompositeControl::AdviseSinkMap(TRUE)](../atl/reference/ccomcompositecontrol-class.md#advisesinkmap)|[CComCompositeControl::AdviseSinkMap(FALSE)](../atl/reference/ccomcompositecontrol-class.md#advisesinkmap)|複合控制項中的 ActiveX 控制項|否|`CComCompositeControl::AdviseSinkMap` 建議的所有項目在事件接收對應。 相同的函式取消通知項目。 此方法稱為自動`CComCompositeControl`類別。|  
|[CAxDialogImpl::AdviseSinkMap(TRUE)](../atl/reference/caxdialogimpl-class.md#advisesinkmap)|[CAxDialogImpl::AdviseSinkMap(FALSE)](../atl/reference/caxdialogimpl-class.md#advisesinkmap)|在對話方塊中的 ActiveX 控制項|否|`CAxDialogImpl::AdviseSinkMap` 建議，並取消通知對話方塊資源中的所有 ActiveX 控制項。 這會為您自動完成。|  
  
## <a name="see-also"></a>另請參閱  
 [事件處理](../atl/event-handling-and-atl.md)   
 [支援 IDispEventImpl](../atl/supporting-idispeventimpl.md)

