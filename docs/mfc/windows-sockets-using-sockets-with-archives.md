---
title: "Windows Sockets：搭配使用通訊端與封存 | Microsoft Docs"
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
  - "封存 [C++], 和 Windows Sockets"
  - "CSocket 類別, 程式設計模型"
  - "通訊端 [C++], 與封存"
  - "Windows Sockets [C++], 封存"
ms.assetid: 17e71a99-a09e-4e1a-9fda-13d62805c824
caps.latest.revision: 12
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Windows Sockets：搭配使用通訊端與封存
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文說明 [CSocket 程式設計模型](#_core_the_csocket_programming_model)。  [CSocket](../mfc/reference/csocket-class.md) 類別會將 [CAsyncSocket](../mfc/reference/casyncsocket-class.md)提供通訊端在較高層級的抽象支援。  `CSocket` 使用 MFC 序列化通訊協定版本來回通訊端物件傳遞資料 MFC [CArchive](../mfc/reference/carchive-class.md) 物件。  `CSocket` 提供封鎖 \(當處理背景處理視窗訊息\) 可讓您對 `CArchive`的存取，處理通訊的許多方面必須做自己使用原始應用程式開發介面或類別 `CAsyncSocket`。  
  
> [!TIP]
>  您可以單獨使用類別 `CSocket` ，做為 `CAsyncSocket`更方便的版本，不過，最簡單的程式設計模型是以 `CArchive` 物件的 `CSocket` 。  
  
 如需通訊端的實作有封存的運作方式的詳細資訊，請參閱 [Windows Sockets：如何搭配使用通訊端與封存](../mfc/windows-sockets-how-sockets-with-archives-work.md)。  如需範例程式碼，請參閱[Windows Sockets：作業順序](../mfc/windows-sockets-sequence-of-operations.md)和[Windows Sockets：使用封存的通訊端範例](../mfc/windows-sockets-example-of-sockets-using-archives.md)。  如需您可以衍生您的類別取得通訊端類別的某些功能的詳細資訊，請參閱 [Windows Sockets：從通訊端類別衍生](../mfc/windows-sockets-deriving-from-socket-classes.md)。  
  
> [!NOTE]
>  如果您正在撰寫一個 MFC 用戶端程式建立的 \(非 MFC\) 伺服器通訊，請勿將封存傳送 C\+\+ 物件。  除非伺服器是了解這種物件的 MFC 應用程式要傳送，無法接收和序列化您的物件。  如需通訊的相關資料與非 MFC 應用程式，請參閱本文件的 [Windows Sockets：位元組順序](../mfc/windows-sockets-byte-ordering.md)。  
  
##  <a name="_core_the_csocket_programming_model"></a> CSocket 程式設計模型  
 使用 `CSocket` 物件包含一起建立和關聯的 MFC 類別物件。  在下列的一般程序，每一個步驟是由伺服器通訊端與用戶端通訊端接受，除了步驟 3 中，每個通訊端類型需要一個動作。  
  
> [!TIP]
>  在執行階段，當用戶端應用程式尋找連接時，伺服器應用程式通常會先開始準備好和「接聽」。  如果伺服器未就緒，當用戶端嘗試連接時，您通常需要使用者應用程式設定來嘗試重新連接。  
  
#### 設定伺服器通訊端與用戶端通訊端之間的通訊。  
  
1.  建構 [CSocket](../mfc/reference/csocket-class.md) 物件。  
  
2.  使用物件建立基本的 **SOCKET** 控制代碼。  
  
     對於 `CSocket` 用戶端物件，除非必要，資料包通訊端，通常應該使用預設參數至 [Create](../Topic/CAsyncSocket::Create.md)。  對於 `CSocket` 伺服器物件，您必須可以在 **Create** 呼叫指定通訊埠。  
  
    > [!NOTE]
    >  `CArchive` 不是使用資料包通訊端一起使用。  如果您要為資料包通訊端使用 `CSocket` ，您必須使用類別，就像使用 `CAsyncSocket`，也就是，不會保存。  由於資料包不可靠 \(不保證達到和可能會重複或不依順序\)，它們無法透過封存與序列化相容。  您預期的序列化作業正常且依順序完成。  如果您嘗試為資料包搭配 `CArchive` 物件的 `CSocket` ， MFC 判斷提示就會失敗。  
  
3.  如果通訊是用戶端，呼叫連接至伺服器通訊端的通訊端物件的 [CAsyncSocket::Connect](../Topic/CAsyncSocket::Connect.md) 。  
  
     \-或\-  
  
     如果通訊是伺服器，呼叫啟動的 [CAsyncSocket::Listen](../Topic/CAsyncSocket::Listen.md) 接聽連接從用戶端嘗試。  當接收到連接要求後，請呼叫 [CAsyncSocket::Accept](../Topic/CAsyncSocket::Accept.md) 來接受它。  
  
    > [!NOTE]
    >  **Accept** 成員函式會取得新的，空的 `CSocket` 物件的參考做為它的參數。  在您呼叫 **Accept**之前，您必須建構此物件。  如果這個通訊端物件超出範圍，關閉連接。  不要呼叫這個新物件的通訊端 **Create** 。  
  
4.  建立 [CSocketFile](../mfc/reference/csocketfile-class.md) 物件，使 `CSocket` 物件產生關聯。  
  
5.  建立載入 \(接收\) 或儲存 \(傳送\) 資料的 [CArchive](../mfc/reference/carchive-class.md) 物件。  此文件與`CSocketFile`物件相關聯。  
  
     記住 `CArchive` 不和資料包通訊端一起使用。  
  
6.  使用傳遞資料的 `CArchive` 物件在用戶端和伺服器通訊端之間。  
  
     注意特定 `CArchive` 物件只會移動某一方向的資料:用於載入 \(接收\) 或儲存 \(傳送\)。  在某些情況下，您會使用兩個 `CArchive` 物件:傳送的資料，其他接收的通知。  
  
     在接受連線和設定封存以後，您可以執行這類工作與驗證密碼。  
  
7.  終結封存、通訊端檔案和通訊端物件。  
  
    > [!NOTE]
    >  明確地將 `CArchive` 提供 `IsBufferEmpty` 類別的成員函式與類別一起使用的 `CSocket`。  例如，如果緩衝區包含多個資料訊息需要執行迴圈，直到所有讀取，並清除緩衝區。  否則，您的下個通知接收的資料可能會無限期地延遲。  使用 `IsBufferEmpty` 以擷取所有資料。  
  
 [Windows Sockets：作業順序](../mfc/windows-sockets-sequence-of-operations.md) 文件說明此處理序與範例程式碼的兩方。  
  
 如需詳細資訊，請參閱：  
  
-   [Windows Sockets：資料流通訊端](../mfc/windows-sockets-stream-sockets.md)  
  
-   [Windows Sockets：資料包通訊端](../mfc/windows-sockets-datagram-sockets.md)  
  
## 請參閱  
 [MFC 中的 Windows Sockets](../mfc/windows-sockets-in-mfc.md)   
 [CSocket::Create](../Topic/CSocket::Create.md)