---
title: "Windows Sockets：封鎖 | Microsoft Docs"
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
  - "封鎖模式通訊端"
  - "通訊端 [C++], 不同 Windows 平台上的行為"
  - "通訊端 [C++], 封鎖模式"
  - "Windows Sockets [C++], 封鎖模式"
  - "Windows Sockets [C++], Windows 平台"
ms.assetid: 10aca9b1-bfba-41a8-9c55-ea8082181e63
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Windows Sockets：封鎖
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文和兩個方針手冊說明視窗通訊端程式設計的幾個問題。  本文包含封鎖。  其他問題的文章報表: [Windows Sockets:位元組排序](../mfc/windows-sockets-byte-ordering.md) 和 [Windows Sockets:將字串轉換](../mfc/windows-sockets-converting-strings.md)。  
  
 如果您從 [CAsyncSocket](../mfc/reference/casyncsocket-class.md)類別使用或衍生自類別，您必須處理這些問題。  如果您從 [CSocket](../mfc/reference/csocket-class.md)類別使用或衍生， MFC 會為您處理它們。  
  
## 封鎖  
 通訊端可以在「區塊模式」或「未封鎖模式」。通訊端的函式在封鎖 \(或同步\) 模式不會傳回，直到它們可以完成其動作。  這個呼叫封鎖，因為函式呼叫的通訊端無法執行的動作—被封鎖—直到呼叫傳回。  對 **Receive** 成員函式的呼叫，例如，可能需要隨機很長的時間才能完成，在等候傳送應用程式傳送 \(這是如果您使用 `CSocket`，或者使用封鎖的 `CAsyncSocket` \)。  如果 `CAsyncSocket` 物件在直接未封鎖模式 \(執行非同步\)，呼叫會傳回與目前錯誤碼可擷取與 [GetLastError](../Topic/CAsyncSocket::GetLastError.md) 成員函式，是 **WSAEWOULDBLOCK**，表示呼叫會封鎖讓它不會立即傳回由於模式。\(`CSocket` 絕不會傳回 **WSAEWOULDBLOCK**。  類別會為您處理封鎖\)。  
  
 通訊端行為不同於 32 位元和 64 位元作業系統 \(例如 Windows 95 或 Windows 98\) 和 16 位元作業系統 \(例如 Windows 3.1\)。  不同於 16 位元作業系統， 32 位元和 64 位元作業系統使用先佔式多工作業並提供多執行緒。  在 32 位元和 64 位元作業系統中，您可以將通訊端放在不同的背景工作執行緒。  在執行緒的通訊可能封鎖，而不會干擾在應用程式的其他活動，且不需花費計算時間內封鎖上。  如需多執行緒應用程式設計的詳細資訊，請參閱本文件的 [多執行緒](../parallel/multithreading-support-for-older-code-visual-cpp.md)。  
  
> [!NOTE]
>  在多執行緒應用程式，您可以使用 `CSocket` 的封鎖本質簡化您的程式設計，而不會影響使用者介面的回應。  藉由處理在處理其他執行緒的主執行緒和 `CSocket` 的使用者互動，您可以將這些邏輯作業分離。  在不多執行緒的應用程式，必須合併和處理這兩個活動為單一執行緒，在長時間的同步處理活動期間，通常表示使用 `CAsyncSocket` ，以便您管理通訊需要隨選或覆寫 `CSocket::OnMessagePending` 來處理使用者動作。  
  
 其餘討論適用於目標 16 位元作業系統的程式設計人員:  
  
 通常，如果您使用 `CAsyncSocket`，您應該避免使用封鎖作業和操作非同步。  在非同步作業，在呼叫 **Receive**之後接收 **WSAEWOULDBLOCK** 錯誤碼，例如，等到直到您的 `OnReceive` 成員函式呼叫通知您可以重新讀取。  非同步呼叫會呼叫您的通訊端的適當的回呼告知函式呼叫，例如 [OnReceive](../Topic/CAsyncSocket::OnReceive.md)。  
  
 在 Windows 中，封鎖呼叫會視為不當的自訂。  根據預設， [CAsyncSocket](../mfc/reference/casyncsocket-class.md) 支援非同步呼叫，使用回呼告知，因此，您必須先處理封鎖。  [CSocket](../mfc/reference/csocket-class.md)類別，另一方面，則為同步。  它提取 Windows 訊息和管理您的封鎖。  
  
 如需封鎖的詳細資訊，請參閱 Windows Sockets 規格。  如需 "On" 函式的詳細資訊，請參閱 [Windows Sockets:通訊端告知](../mfc/windows-sockets-socket-notifications.md) 和 [Windows Sockets:衍生自的類別](../mfc/windows-sockets-deriving-from-socket-classes.md)。  
  
 如需詳細資訊，請參閱：  
  
-   [Windows Sockets：使用類別 CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)  
  
-   [Windows Sockets：搭配使用通訊端與封存](../mfc/windows-sockets-using-sockets-with-archives.md)  
  
-   [Windows Sockets：背景](../mfc/windows-sockets-background.md)  
  
-   [Windows Sockets：資料流通訊端](../mfc/windows-sockets-stream-sockets.md)  
  
-   [Windows Sockets：資料包通訊端](../mfc/windows-sockets-datagram-sockets.md)  
  
## 請參閱  
 [MFC 中的 Windows Sockets](../mfc/windows-sockets-in-mfc.md)   
 [CAsyncSocket::OnSend](../Topic/CAsyncSocket::OnSend.md)