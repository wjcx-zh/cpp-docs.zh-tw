---
title: "Windows Sockets：作業順序 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "通訊端 [C++], 作業"
  - "通訊端 [C++], 資料流通訊端"
  - "資料流通訊端 [C++]"
  - "Windows Sockets [C++], 作業"
  - "Windows Sockets [C++], 資料流通訊端"
ms.assetid: 43ce76f5-aad3-4247-b8a6-16cc7d012796
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Windows Sockets：作業順序
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文詳細說明通訊端伺服器和用戶端通訊端之作業序列。  由於通訊端使用 `CArchive` 物件，它們必須是 [資料流通訊端](../mfc/windows-sockets-stream-sockets.md)。  
  
## 資料流通訊端通訊的作業序列  
 直到建構 `CSocketFile` 物件為止，`CAsyncSocket` 和 `CSocket` 的下列序列是正確的 \(但有一些參數差異\)。  從這時起，序列完全是為了 `CSocket`。  下表說明設定用戶端和伺服器之間的通訊之作業序列。  
  
### 設定用戶端和伺服器之間的通訊  
  
|伺服器|用戶端|  
|---------|---------|  
|`// construct a socket`<br /><br /> `CSocket sockSrvr;`|`// construct a socket`<br /><br /> `CSocket sockClient;`|  
|`// create the SOCKET`<br /><br /> `sockSrvr.Create(nPort);`1,2|`// create the SOCKET`<br /><br /> `sockClient.Create( );`2|  
|`// start listening`<br /><br /> `sockSrvr.Listen( );`||  
||`// seek a connection`<br /><br /> `sockClient.Connect(strAddr, nPort);`3,4|  
|`// construct a new, empty socket`<br /><br /> `CSocket sockRecv;`<br /><br /> `// accept connection`<br /><br /> `sockSrvr.Accept( sockRecv );` 5||  
|`// construct file object`<br /><br /> `CSocketFile file(&sockRecv);`|`// construct file object`<br /><br /> `CSocketFile file(&sockClient);`|  
|`// construct an archive`<br /><br /> `CArchive arIn(&file,`  `CArchive::load);`<br /><br /> \-或\-<br /><br /> `CArchive arOut(&file,`  `CArchive::store);`<br /><br /> –或是兩者–|`// construct an archive`<br /><br /> `CArchive arIn(&file,`  `CArchive::load);`<br /><br /> \-或\-<br /><br /> `CArchive arOut(&file,`  `CArchive::store);`<br /><br /> –或是兩者–|  
|`// use the archive to pass data:`<br /><br /> `arIn >> dwValue;`<br /><br /> \-或\-<br /><br /> `arOut << dwValue;`6|`// use the archive to pass data:`<br /><br /> `arIn >> dwValue;`<br /><br /> \-或\-<br /><br /> `arOut << dwValue;`6|  
  
 1.  其中 `nPort` 是通訊埠編號。  如需通訊埠的詳細資訊，請參閱 [Windows Sockets：通訊埠和通訊端位址](../mfc/windows-sockets-ports-and-socket-addresses.md) 。  
  
 2.  伺服器一定要指定連接埠，如此用戶端才可以連接。  **Create** 呼叫有時也會指定位址。  在用戶端上，請使用預設參數，要求 MFC 使用任何可用的通訊埠。  
  
 3.  其中 `nPort` 是通訊埠編號， *strAddr* 是 MAC 位址或 Internet Protocol \(IP\) 位址。  
  
 4.  MAC 位址可能採用數種形式：「ftp.microsoft.com」或「microsoft.com」。  IP 位址使用「點狀數目」格式，例如「127.54.67.32」。  **Connect** 函式驗證位址是否為點狀數字 \(雖然它不會檢查數值是否為網路中有效的電腦\)。  如果不是，**Connect** 假設使用電腦名稱是其他種類的格式。  
  
 5.  當您在伺服器端呼叫 **Accept** 時，會傳遞參考至新的通訊端物件。  您必須先建構此物件，但是請不要呼叫 **Create** 。  請記住，如果這個通訊端物件超出範圍，連接會關閉。  MFC 連接新物件至 **SOCKET** 控制代碼。  您可以在堆疊上或者在堆積上建構通訊端，如下所示。  
  
 6.  當超出範圍時，封存和通訊端檔案會關閉。  當物件超出範圍或刪除時，通訊端物件的解構函式也會呼叫通訊端物件的 [Close](../Topic/CAsyncSocket::Close.md) 成員函式。  
  
## 序列的其他注意事項  
 在上表所列的呼叫序列是資料流通訊端所用。  資料包通訊端是無連接的，不需要 [CAsyncSocket::Connect](../Topic/CAsyncSocket::Connect.md)、[Listen](../Topic/CAsyncSocket::Listen.md) 和 [Accept](../Topic/CAsyncSocket::Accept.md) 呼叫 \(雖然您可以選擇性地使用 **Connect**\)。  相反地，如果您使用了類別 `CAsyncSocket`，資料包通訊端會使用 `CAsyncSocket::SendTo` 和 `ReceiveFrom` 成員函式。\(如果您使用資料包通訊端的 **Connect** ，請使用 **Send** 和 **Receive**\)。因為 `CArchive` 無法與資料包一起使用，如果通訊是資料包，請不要與封存的 `CSocket` 一起使用。  
  
 [CSocketFile](../mfc/reference/csocketfile-class.md) 不支援 `CFile` 的全部功能；`CFile` 成員 \(例如 `Seek`\) 在通訊端通訊不具意義，無法使用。  因此，有些預設 MFC `Serialize` 函式與 `CSocketFile` 不相容。  特別是的 `CEditView` 類別。  您不應嘗試使用 `CEditView::SerializeRaw`，透過附加至 `CSocketFile` 物件的 `CArchive` 物件來序列化 `CEditView` 資料；請改使用 **CEditView::Serialize** \(未記載\)。  [SerializeRaw](../Topic/CEditView::SerializeRaw.md) 函式預期檔案物件有函式，例如 `Seek`，而 `CSocketFile` 不支援。  
  
 如需詳細資訊，請參閱：  
  
-   [Windows Sockets：搭配使用通訊端與封存](../mfc/windows-sockets-using-sockets-with-archives.md)  
  
-   [Windows Sockets：使用類別 CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)  
  
-   [Windows Sockets：連接埠和通訊端位址](../mfc/windows-sockets-ports-and-socket-addresses.md)  
  
-   [Windows Sockets：資料流通訊端](../mfc/windows-sockets-stream-sockets.md)  
  
-   [Windows Sockets：資料包通訊端](../mfc/windows-sockets-datagram-sockets.md)  
  
## 請參閱  
 [MFC 中的 Windows Sockets](../mfc/windows-sockets-in-mfc.md)   
 [CSocket Class](../mfc/reference/csocket-class.md)   
 [CAsyncSocket::Create](../Topic/CAsyncSocket::Create.md)   
 [CAsyncSocket::Close](../Topic/CAsyncSocket::Close.md)