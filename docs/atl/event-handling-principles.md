---
title: 事件處理原則 (ATL)
ms.date: 11/04/2016
helpviewer_keywords:
- event handling, implementing
- event handling, advising event sources
- interfaces, event and event sink
- dual interfaces, event interfaces
- event handling, dual event interfaces
ms.assetid: d17ca7cb-54f2-4658-ab8b-b721ac56801d
ms.openlocfilehash: 2e810853e7c81f279039e0b3dfda5199d38deee2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319571"
---
# <a name="event-handling-principles"></a>事件處理原則

所有事件處理共有三個步驟。 您需要:

- 在對象上實現事件介面。

- 建議物件要接收事件的事件源。

- 當物件不再需要接收事件時,取消通知事件源。

實現事件介面的方式將取決於其類型。 事件介面可以是可 v 可的、雙介面的,也可以是介面。 由事件源的設計器來定義介面;由您來實現該介面。

> [!NOTE]
> 儘管事件介面不能是雙重的,但是有許多良好的設計原因可以避免使用雙重。 但是,這是事件*源*的設計者/實現者做出的決定。 由於您從事件`sink`的角度工作,您需要允許除了實現雙事件介面外可能別無選擇。 有關雙介面的詳細資訊,請參閱[雙介面和 ATL](../atl/dual-interfaces-and-atl.md)。

建議事件源可以分為三個步驟:

- 查詢[IConnectPoint 容器](/windows/win32/api/ocidl/nn-ocidl-iconnectionpointcontainer)的源物件。

- 呼叫[IConnectPoint 容器:尋找連接點](/windows/win32/api/ocidl/nf-ocidl-iconnectionpointcontainer-findconnectionpoint)傳遞您感興趣的事件介面的 IID。 如果成功,這將返回連接點物件上的[IConnectPoint](/windows/win32/api/ocidl/nn-ocidl-iconnectionpoint)介面。

- 呼叫[IConnectionPoint::建議](/windows/win32/api/ocidl/nf-ocidl-iconnectionpoint-advise)傳遞`IUnknown`事件接收器。 如果成功,這將返回表示連接`DWORD`的 Cookie。

成功註冊了接收事件的興趣后,將根據源物件觸發的事件調用對象事件介面上的方法。 當您不再需要接收事件時,您可以通過[IConnectionPoint::::un建議](/windows/win32/api/ocidl/nf-ocidl-iconnectionpoint-unadvise)將 Cookie 傳回連接點。 這將中斷源和接收器之間的連接。

在處理事件時,請小心避免引用週期。

## <a name="see-also"></a>另請參閱

[事件處理](../atl/event-handling-and-atl.md)
