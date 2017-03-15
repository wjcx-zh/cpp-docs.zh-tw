---
title: "Windows Sockets：從通訊端類別衍生 | Microsoft Docs"
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
  - "衍生類別, 從通訊端類別"
  - "通訊端 [C++], 衍生自通訊端類別"
  - "Windows Sockets [C++], 衍生自通訊端類別"
ms.assetid: 3a26e67a-e323-433b-9b05-eca018799801
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Windows Sockets：從通訊端類別衍生
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文說明您可以從其中一個通訊端類別衍生自己的類別，進而得到的某些功能。  
  
 您可以從 [CAsyncSocket](../mfc/reference/casyncsocket-class.md) 或 [CSocket](../mfc/reference/csocket-class.md) 衍生您自己的通訊端類別，以加入您的功能。  特別是，這些類別提供大量可以覆寫的虛擬成員函式。  這些功能包括 [OnReceive](../Topic/CAsyncSocket::OnReceive.md)、[OnSend](../Topic/CAsyncSocket::OnSend.md)、 [OnAccept](../Topic/CAsyncSocket::OnAccept.md)、[OnConnect](../Topic/CAsyncSocket::OnConnect.md) 和 [OnClose](../Topic/CAsyncSocket::OnClose.md)。  您可以在您的衍生通訊端類別覆寫函式，在網路事件發生時使用它們提供的功能。  架構會呼叫這些通知回呼函式，以通知您重要的事件，例如您可以開始讀取資料的收據。  如需告知函式的詳細資訊，請參閱 [Windows Sockets：通訊端告知](../mfc/windows-sockets-socket-notifications.md)。  
  
 此外，類別 `CSocket` 提供 [OnMessagePending](../Topic/CSocket::OnMessagePending.md) 成員函式 \(可進階覆寫\)。  當通訊端提取 Windows 訊息時， MFC 呼叫此函式。  您可以覆寫 `OnMessagePending`，搜尋來自視窗的特定資訊和回應它們。  
  
 類別 `CSocket` 提供的預設版本 `OnMessagePending` 會在等待封鎖呼叫完成時，檢查 `WM_PAINT` 訊息的訊息佇列。  它會繪製訊息以改善顯示品質。  除了這些好用的功能以外，以下說明您可能會覆寫函式的一種方式。  此為另一個範例，請考慮為下列工作使用 `OnMessagePending` 。  假設您在等待網路交易完成時，顯示非強制回應對話方塊。  對話方塊包含取消按鈕，讓使用者可以用來取消花費太久的交易。  您的 `OnMessagePending` 覆寫可能出現與這個非強制回應對話方塊相關的訊息。  
  
 在 `OnMessagePending` 的覆寫中，請傳回  **TRUE** 或傳回呼叫 `OnMessagePending` 基底類別版本的結果。  若基底類別版本執行您仍然希望完成的工作，請呼叫它。  
  
 如需詳細資訊，請參閱：  
  
-   [Windows Sockets：搭配使用通訊端與封存](../mfc/windows-sockets-using-sockets-with-archives.md)  
  
-   [Windows Sockets：使用類別 CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)  
  
-   [Windows Sockets：封鎖](../mfc/windows-sockets-blocking.md)  
  
-   [Windows Sockets：位元組順序](../mfc/windows-sockets-byte-ordering.md)  
  
-   [Windows Sockets：轉換字串](../mfc/windows-sockets-converting-strings.md)  
  
## 請參閱  
 [MFC 中的 Windows Sockets](../mfc/windows-sockets-in-mfc.md)