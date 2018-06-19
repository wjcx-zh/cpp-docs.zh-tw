---
title: 實作事件處理介面 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ATL, event handling
- event handling, ATL
- interfaces, event and event sink
ms.assetid: eb2a5b33-88dc-4ce3-bee0-c5c38ea050d7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ea37aa4c84cb0824d11f0081e38d9e8157b77ed1
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32356304"
---
# <a name="implementing-the-event-handling-interface"></a>實作事件處理介面
ATL 可協助您處理事件所需的全部三個元素： 實作事件介面、 通知事件來源，並取消通知事件來源。 您必須採取的確切步驟取決於事件介面和應用程式的效能需求的型別。  
  
 最常見的使用 ATL 實作介面方法如下：  
  
-   直接衍生自自訂介面。  
  
-   衍生自[IDispatchImpl](../atl/reference/idispatchimpl-class.md)雙重介面類型程式庫中所述。  
  
-   衍生自[IDispEventImpl](../atl/reference/idispeventimpl-class.md)的分配介面類型程式庫中所述。  
  
-   衍生自[IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md)的分配介面未描述的類型程式庫中，或當您想要載入不在執行階段類型資訊來改善效率。  
  

 如果您實作自訂或雙重介面，您應該藉由呼叫通知事件來源[AtlAdvise](reference/connection-point-global-functions.md#atladvise)或[CComPtrBase::Advise](../atl/reference/ccomptrbase-class.md#advise)。 您必須追蹤的呼叫所傳回自己的 cookie。 呼叫[AtlUnadvise](reference/connection-point-global-functions.md#atlunadvise)中斷連線。  

  
 如果您實作 dispinterface 使用`IDispEventImpl`或`IDispEventSimpleImpl`，您應該藉由呼叫通知事件來源[IDispEventSimpleImpl::DispEventAdvise](../atl/reference/idispeventsimpleimpl-class.md#dispeventadvise)。 呼叫[IDispEventSimpleImpl::DispEventUnadvise](../atl/reference/idispeventsimpleimpl-class.md#dispeventunadvise)中斷連線。  
  
 如果您使用`IDispEventImpl`接收對應中列出的事件來源為複合控制項的基底類別，將會建議使用和 unadvised 自動使用[CComCompositeControl::AdviseSinkMap](../atl/reference/ccomcompositecontrol-class.md#advisesinkmap)。  
  
 `IDispEventImpl`和`IDispEventSimpleImpl`類別為您管理 cookie。  
  
## <a name="see-also"></a>另請參閱  
 [事件處理](../atl/event-handling-and-atl.md)

