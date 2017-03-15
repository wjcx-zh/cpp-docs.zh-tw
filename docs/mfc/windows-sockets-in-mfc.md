---
title: "MFC 中的 Windows Sockets | Microsoft Docs"
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
  - "MFC [C++], Windows Sockets"
  - "通訊端 [C++], MFC"
  - "通訊端 [C++], 程式設計模型"
  - "Windows Sockets [C++], MFC 支援"
  - "Windows Sockets [C++], 程式設計模型"
  - "WINSOCK.DLL"
  - "WSOCK32.DLL"
ms.assetid: 1f3c476a-9c68-49fe-9a25-d22971a334d0
caps.latest.revision: 12
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# MFC 中的 Windows Sockets
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  MFC 支援 Windows Sockets 1，但不支援 [Windows Sockets 2](http://msdn.microsoft.com/library/windows/desktop/ms740673)。  Windows Sockets 2 首先隨附於 Windows 98 和隨附於 Windows 2000 的版本。  
  
 MFC 將 Windows Sockets 供寫入的 Web 通訊端兩個模型，在兩個 MFC 類別。  本文說明這些模型和 MFC 通訊端支援的詳細資料。  「通訊端」是通訊端點:您的應用程式在網路上的其他 Windows Sockets 應用程式通訊的物件。  
  
 如需 Windows Sockets 的資訊，包括通訊端概念的說明，請參閱 [Windows Sockets:背景](../mfc/windows-sockets-background.md)。  
  
##  <a name="_core_sockets_programming_models"></a> 通訊端程式設計模型  
 兩個 MFC Windows Sockets 程式設計模型由下列類別支援:  
  
-   `CAsyncSocket`  
  
     這個類別會封裝 Windows Sockets API。  [CAsyncSocket](../mfc/reference/casyncsocket-class.md) 是知道網路程式設計並想要撰寫彈性直接通訊端 API 的程式設計人員，而且想要回呼函式便利 Web 事件的告知。  刪除封裝通訊端之外以物件導向的形式在 C\+\+ 中，這個類別提供的唯一其他抽象將某些通訊端相關的 Windows 訊息的回呼。  如需詳細資訊，請參閱 [Windows Sockets:通訊端告知](../mfc/windows-sockets-socket-notifications.md)。  
  
-   `CSocket`  
  
     這個類別衍生自 `CAsyncSocket`，將通訊端提供工作的高階抽象透過 MFC [CArchive](../mfc/reference/carchive-class.md) 物件。  使用 MFC 的檔案序列化通訊協定來使用類似封存的通訊端。  這比 `CAsyncSocket` 模型可讓您輕鬆地使用。  [CSocket](../mfc/reference/csocket-class.md) 繼承封裝 Windows Sockets API 從 `CAsyncSocket` 的許多成員函式;您必須使用這些函式和了解通訊端程式設計。  但是， `CSocket` 處理通訊的許多方面必須做自己使用原始應用程式開發介面或類別 `CAsyncSocket`。  最重要的是， `CSocket` 提供封鎖 \(與背景處理視窗訊息\)，對 `CArchive`的同步作業是非常重要的。  
  
 建立和使用 `CSocket` 和 `CAsyncSocket` 物件在 [Windows Sockets:使用已封存的通訊端](../mfc/windows-sockets-using-sockets-with-archives.md) 和 [Windows Sockets:使用類別 CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)所述。  
  
##  <a name="_core_mfc_socket_samples_and_windows_sockets_dlls"></a> Windows Sockets DLLs  
 Microsoft Windows 作業系統提供 Windows Sockets 動態連結程式庫 \(DLL\)。  Visual C\+\+ 提供適當的標頭檔程式庫和 Windows Sockets 規格。  
  
> [!NOTE]
>  在 Windows NT 和 Windows 2000 中， Windows Sockets 根據 WINSOCK.DLL 支援 16 位元應用程式。  對於 32 位元應用程式，支援在 WSOCK32.DLL。  提供的 API 是相同的，除了 32 位元版本有參數時擴充到 32 位元。  在 Win32 下，提供執行緒安全。  
  
 如需 Windows Sockets 的詳細資訊，請參閱 。  
  
-   [Windows Sockets：資料流通訊端](../mfc/windows-sockets-stream-sockets.md)  
  
-   [Windows Sockets：資料包通訊端](../mfc/windows-sockets-datagram-sockets.md)  
  
-   [Windows Sockets：搭配使用通訊端與封存](../mfc/windows-sockets-using-sockets-with-archives.md)  
  
-   [Windows Sockets：作業順序](../mfc/windows-sockets-sequence-of-operations.md)  
  
-   [Windows Sockets：使用封存的通訊端範例](../mfc/windows-sockets-example-of-sockets-using-archives.md)  
  
-   [Windows Sockets：如何搭配使用通訊端與封存](../mfc/windows-sockets-how-sockets-with-archives-work.md)  
  
-   [Windows Sockets：使用類別 CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)  
  
-   [Windows Sockets：從通訊端類別衍生](../mfc/windows-sockets-deriving-from-socket-classes.md)  
  
-   [Windows Sockets：通訊端告知](../mfc/windows-sockets-socket-notifications.md)  
  
-   [Windows Sockets：封鎖](../mfc/windows-sockets-blocking.md)  
  
-   [Windows Sockets：位元組順序](../mfc/windows-sockets-byte-ordering.md)  
  
-   [Windows Sockets：轉換字串](../mfc/windows-sockets-converting-strings.md)  
  
-   [Windows Sockets：連接埠和通訊端位址](../mfc/windows-sockets-ports-and-socket-addresses.md)  
  
## 請參閱  
 [Windows Sockets](../mfc/windows-sockets.md)