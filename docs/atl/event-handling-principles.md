---
title: "Event Handling Principles | Microsoft Docs"
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
  - "雙重介面, event interfaces"
  - "事件處理, advising event sources"
  - "事件處理, dual event interfaces"
  - "事件處理, 實作"
  - "介面, event and event sink"
ms.assetid: d17ca7cb-54f2-4658-ab8b-b721ac56801d
caps.latest.revision: 10
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Event Handling Principles
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

有三個步驟通用於所有事件處理常式。  您將需要:  
  
-   實作在物件的事件介面。  
  
-   建議您事件來源的物件要接收事件。  
  
-   Unadvise 事件來源，當您的物件不再需要接收事件。  
  
 您將會實作事件介面的方法取決於它的型別。  事件介面可以是雙重 vtable，或分配介面。  它是由介面所定義的事件來源的設計工具決定;它是由實作該介面的方式來決定。  
  
> [!NOTE]
>  雖然沒有事件介面不能是重複的技術原因，有一些虛擬設計理由避免使用兩倍。  不過，這是 *事件來源的*設計工具\/實作所做的決定。  當您從事件 `sink`角度的工作，您需要考慮的情形時您可能不會有任何選項，但實作雙重介面事件。  如需雙重介面的詳細資訊，請參閱 [雙重介面和 ATL](../atl/dual-interfaces-and-atl.md)。  
  
 通知事件來源可以區分為三個步驟:  
  
-   [IConnectionPointContainer](http://msdn.microsoft.com/library/windows/desktop/ms683857)查詢的來源物件。  
  
-   呼叫傳遞您感興趣事件介面的 IID 的 [IConnectionPointContainer::FindConnectionPoint](http://msdn.microsoft.com/library/windows/desktop/ms692476) 。  如果成功，則這個方法會傳回在連接點物件的 [IConnectionPoint](http://msdn.microsoft.com/library/windows/desktop/ms694318) 介面。  
  
-   呼叫傳遞事件接收的 **IUnknown** 的 [IConnectionPoint::Advise](http://msdn.microsoft.com/library/windows/desktop/ms678815) 。  如果成功，則這個方法會傳回表示連接的 `DWORD` Cookie。  
  
 一旦您將接收事件上成功註冊了感興趣，在物件的事件介面的方法會根據事件會引發由來源物件。  當您不再需要收到事件時，您可以將 Cookie 傳遞至連接點透過 [IConnectionPoint::Unadvise](http://msdn.microsoft.com/library/windows/desktop/ms686608)。  這將會破壞來源和接收之間的連接。  
  
 在處理事件時，請小心不要參考循環。  
  
## 請參閱  
 [事件處理](../atl/event-handling-and-atl.md)