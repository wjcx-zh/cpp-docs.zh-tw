---
title: 事件處理原則 (ATL) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- event handling, implementing
- event handling, advising event sources
- interfaces, event and event sink
- dual interfaces, event interfaces
- event handling, dual event interfaces
ms.assetid: d17ca7cb-54f2-4658-ab8b-b721ac56801d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 239ea94343652d379048bbeee87d2650d3f1ed72
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/05/2018
ms.locfileid: "37852532"
---
# <a name="event-handling-principles"></a>事件處理原則
有三個步驟通用於所有的事件處理。 您將需要：  
  
-   在物件上實作事件介面。  
  
-   建議您物件想要接收事件的事件來源。  
  
-   當您的物件不再需要以接收事件時，請取消通知事件來源。  
  
 您將實作事件介面的方式將取決於其型別。 Vtable、 dual、 或 dispinterface，可以是事件介面。 已啟動事件來源定義的介面; 的設計工具它由您實作該介面。  
  
> [!NOTE]
>  雖然沒有任何事件介面不可以是雙重的技術原因，但有許多良好的設計以避免雙重介面使用的原因。 不過，這是由設計工具/實作器的事件所做的決策*來源*。 因為您正在從事件的觀點來看`sink`，您需要允許您可能沒有任何選擇的可能性，但實作雙重事件介面。 如需有關介面的詳細資訊，請參閱[雙重介面和 ATL](../atl/dual-interfaces-and-atl.md)。  
  
 通知事件來源可以分成三個步驟：  
  
-   查詢的來源物件[IConnectionPointContainer](http://msdn.microsoft.com/library/windows/desktop/ms683857)。  
  
-   呼叫[IConnectionPointContainer::FindConnectionPoint](http://msdn.microsoft.com/library/windows/desktop/ms692476)傳遞事件介面的 IID，將您感興趣。 如果成功，這會傳回[IConnectionPoint](http://msdn.microsoft.com/library/windows/desktop/ms694318)連接點物件上的介面。  
  
-   呼叫[IConnectionPoint::Advise](http://msdn.microsoft.com/library/windows/desktop/ms678815)傳遞`IUnknown`事件接收。 如果成功，這會傳回`DWORD`代表的連接 cookie。  
  
 一旦您已經順利註冊您要接收事件，就會呼叫物件的事件介面上的方法，根據來源物件所引發的事件。 當您不再需要接收事件時，您可以將 cookie 傳遞至透過的連接點[iconnectionpoint::](http://msdn.microsoft.com/library/windows/desktop/ms686608)。 這會中斷來源和接收器之間的連線。  
  
 請小心避免參考循環處理事件時。  
  
## <a name="see-also"></a>另請參閱  
 [事件處理](../atl/event-handling-and-atl.md)

