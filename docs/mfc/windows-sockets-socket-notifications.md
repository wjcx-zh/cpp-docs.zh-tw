---
title: "Windows Sockets：通訊端告知 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "告知, 通訊端"
  - "通訊端 [C++], 告知"
  - "Windows Sockets [C++], 告知"
ms.assetid: 87d5bf70-6e77-49a9-9a64-aaadee2ad018
caps.latest.revision: 13
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Windows Sockets：通訊端告知
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文將通訊端類別描述告知函式。  這些成員函式是重要事件通知您的通訊端物件的框架所呼叫的回呼函式。  告知函式為：  
  
-   [OnReceive](../Topic/CAsyncSocket::OnReceive.md):告知這個通訊端有緩衝區中資料的可以擷取呼叫 [接收](../Topic/CAsyncSocket::Receive.md)。  
  
-   [OnSend](../Topic/CAsyncSocket::OnSend.md):告知這個通訊端可以呼叫 [傳送](../Topic/CAsyncSocket::Send.md)現在會傳送資料。  
  
-   [OnAccept](../Topic/CAsyncSocket::OnAccept.md):告知接聽通訊端可以接受暫止連接要求透過呼叫 [接受](../Topic/CAsyncSocket::Accept.md)。  
  
-   [OnConnect](../Topic/CAsyncSocket::OnConnect.md):告知這個連接通訊端其連接嘗試完成:或許可能成功或錯誤。  
  
-   [OnClose](../Topic/CAsyncSocket::OnClose.md):通知它連接至這個通訊端的通訊端關閉。  
  
    > [!NOTE]
    >  額外的告知函式是 [OnOutOfBandData](../Topic/CAsyncSocket::OnOutOfBandData.md)。  此通知會通知接收的通訊端傳送通訊端有「傳送 Out\-of\-Band」的資料。  Out\-of\-Band Data 是邏輯上獨立整合通道的與每個至已連接的資料流通訊端。  Out\-of\-Band 通道通常用來傳送「緊急」資料。  MFC 支援 Out\-of\-Band 資料。  進階使用者使用 [CAsyncSocket](../mfc/reference/casyncsocket-class.md) 一起使用可能需要使用 Out\-of\-Band 通道，不過， [CSocket](../mfc/reference/csocket-class.md) 類別的使用者從使用它被鼓勵。  最簡單的方法是建立傳遞的這類資料的第二個通訊端。  如需 Out\-of\-Band 資料的詳細資訊，請參閱 Windows Sockets 規格，在 [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)]中使用。  
  
 如果您從類別衍生自 `CAsyncSocket`，您必須覆寫這些 Web 事件的告知函式想要加入至應用程式。  如果您從類別衍生自 `CSocket`的類別，它是您選擇的覆寫函式相關通知。  在告知函式會預設為的情況下，您也可以使用 `CSocket` 。  
  
 這些函式是可覆寫的回呼函式。  `CAsyncSocket` 和 `CSocket` 轉換訊息告知，不過，您必須實作告知函式如何回應，如果要使用它們。  告知函式呼叫，則通訊端會收到相關事件的時間，例如要讀取的資料隨即出現。  
  
 會通知時， MFC 會告知函式可讓您自訂的通訊端的行為。  例如，您可能會從您的 `OnReceive` 告知函式的 **Receive** ，也就是說，在收到具有讀取資料，您可以呼叫 **Receive** 讀取它。  這個方法不是必要的，不過，它是有效的案例。  或者，您可以使用您的告知函式追蹤進度，列印 **TRACE** 訊息，依此類推。  
  
 您可以覆寫衍生的通訊端類別的告知功能和提供實作利用這些通知。  
  
 在執行作業時 \(例如接收或傳送資料， `CSocket` 物件會同步處理。  在這個同步處理狀態期間，做為其他通訊端表示所有通知排入佇列時，若要的目前通訊端等候告知時。在 **Receive** 呼叫期間， \(例如，通訊端要通知讀取\)。一旦通訊端完成同步作業並再次變成非同步，其他通訊端可開始接收佇列的通知。  
  
> [!NOTE]
>  在 `CSocket`中， `OnConnect` 告知函式絕不會呼叫。  如需連接，您呼叫 **Connect**，將傳回，當連接完成時 \(成功或錯誤\)。  連接通知的處理方式是 MFC 實作詳細資料。  
  
 如需每個告知函式的詳細資訊，請參閱函式在《 *MFC 參考》中的*類別 `CAsyncSocket` 下。  如需原始程式碼以及有關 MFC 範例，請參閱 [MFC 範例](../top/visual-cpp-samples.md)。  
  
 如需詳細資訊，請參閱：  
  
-   [Windows Sockets：使用類別 CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)  
  
-   [Windows Sockets：從通訊端類別衍生](../mfc/windows-sockets-deriving-from-socket-classes.md)  
  
-   [Windows Sockets：如何搭配使用通訊端與封存](../mfc/windows-sockets-how-sockets-with-archives-work.md)  
  
-   [Windows Sockets：封鎖](../mfc/windows-sockets-blocking.md)  
  
-   [Windows Sockets：位元組順序](../mfc/windows-sockets-byte-ordering.md)  
  
-   [Windows Sockets：轉換字串](../mfc/windows-sockets-converting-strings.md)  
  
## 請參閱  
 [MFC 中的 Windows Sockets](../mfc/windows-sockets-in-mfc.md)