---
title: 實作事件處理介面
ms.date: 11/04/2016
helpviewer_keywords:
- ATL, event handling
- event handling, ATL
- interfaces, event and event sink
ms.assetid: eb2a5b33-88dc-4ce3-bee0-c5c38ea050d7
ms.openlocfilehash: d977b59907266a2e0141defa8c496b1e7bc66a6c
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57273409"
---
# <a name="implementing-the-event-handling-interface"></a>實作事件處理介面

ATL 可協助您處理事件所需的所有三個項目： 實作事件介面、 事件來源，為客戶提供建議和取消通知事件來源。 您需要採取的確切步驟取決於事件介面和您的應用程式的效能需求的型別。

使用 ATL 實作介面的最常見方式是：

- 直接衍生自一種自訂介面。

- 衍生自[IDispatchImpl](../atl/reference/idispatchimpl-class.md)雙重介面型別程式庫中所述。

- 衍生自[IDispEventImpl](../atl/reference/idispeventimpl-class.md)的分配介面型別程式庫中所述。

- 衍生自[IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md)的分配介面沒有說明類型程式庫中，或當您想要載入不在執行階段類型資訊來改善效率。

如果您要實作自訂或雙重介面，您還應該通知的事件來源，藉由呼叫[AtlAdvise](reference/connection-point-global-functions.md#atladvise)或是[CComPtrBase::Advise](../atl/reference/ccomptrbase-class.md#advise)。 您必須追蹤的呼叫所傳回您自己的 cookie。 呼叫[AtlUnadvise](reference/connection-point-global-functions.md#atlunadvise)中斷連線。

如果您要實作 dispinterface using`IDispEventImpl`或是`IDispEventSimpleImpl`，您應該通知的事件來源，藉由呼叫[IDispEventSimpleImpl::DispEventAdvise](../atl/reference/idispeventsimpleimpl-class.md#dispeventadvise)。 呼叫[IDispEventSimpleImpl::DispEventUnadvise](../atl/reference/idispeventsimpleimpl-class.md#dispeventunadvise)中斷連線。

如果您使用`IDispEventImpl`接收對應中所列的事件來源為複合控制項的基底類別，將會建議和 unadvised 使用自動[CComCompositeControl::AdviseSinkMap](../atl/reference/ccomcompositecontrol-class.md#advisesinkmap)。

`IDispEventImpl`和`IDispEventSimpleImpl`類別為您管理 cookie。

## <a name="see-also"></a>另請參閱

[事件處理](../atl/event-handling-and-atl.md)
