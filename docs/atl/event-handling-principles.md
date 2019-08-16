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
ms.openlocfilehash: 066c8db60afed31ceba1c9ef6f4a10d5f842e608
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492148"
---
# <a name="event-handling-principles"></a>事件處理原則

所有事件處理都有三個常見的步驟。 您將需要:

- 在您的物件上執行事件介面。

- 建議您的物件要接收事件的事件來源。

- 當您的物件不再需要接收事件時, 請 Unadvise 事件來源。

您執行事件介面的方式將取決於其類型。 事件介面可以是 vtable、雙重或一個產生介面。 而是由事件來源的設計工具來定義介面。您可自行決定是否要執行該介面。

> [!NOTE]
>  雖然沒有任何技術原因是事件介面不能是雙重的, 但有一些很好的設計理由可以避免使用 duals。 不過, 這是由事件*來源*的設計人員/實施者所做的決定。 由於您是從事件`sink`的觀點來工作, 因此您必須允許您可能沒有任何選擇, 但要執行雙重事件介面。 如需雙重介面的詳細資訊, 請參閱[雙重介面和 ATL](../atl/dual-interfaces-and-atl.md)。

建議事件來源分為三個步驟:

- 查詢來源物件以進行[IConnectionPointContainer](/windows/win32/api/ocidl/nn-ocidl-iconnectionpointcontainer)。

- 呼叫[IConnectionPointContainer:: FindConnectionPoint](/windows/win32/api/ocidl/nf-ocidl-iconnectionpointcontainer-findconnectionpoint) , 傳遞您感興趣之事件介面的 IID。 如果成功, 這會傳回連接點物件上的[IConnectionPoint](/windows/win32/api/ocidl/nn-ocidl-iconnectionpoint)介面。

- 呼叫[IConnectionPoint:: Advise](/windows/win32/api/ocidl/nf-ocidl-iconnectionpoint-advise) , 傳遞`IUnknown`事件接收器的。 如果成功, 這會`DWORD`傳回代表連接的 cookie。

在您成功註冊接收事件的興趣之後, 將會根據來源物件所引發的事件來呼叫物件之事件介面上的方法。 當您不再需要接收事件時, 您可以透過[IConnectionPoint:: Unadvise](/windows/win32/api/ocidl/nf-ocidl-iconnectionpoint-unadvise)將 cookie 傳回到連接點。 這會中斷來源與接收之間的連接。

處理事件時, 請小心避免參考迴圈。

## <a name="see-also"></a>另請參閱

[事件處理](../atl/event-handling-and-atl.md)
