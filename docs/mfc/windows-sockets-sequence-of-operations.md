---
title: Windows Sockets： 作業順序 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Windows Sockets [MFC], operations
- Windows Sockets [MFC], stream sockets
- sockets [MFC], stream sockets
- sockets [MFC], operations
- stream sockets [MFC]
ms.assetid: 43ce76f5-aad3-4247-b8a6-16cc7d012796
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c27856b2bb6b843ce60404ea389c28082bf1dc5a
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2018
ms.locfileid: "36953941"
---
# <a name="windows-sockets-sequence-of-operations"></a>Windows Sockets：作業順序
這篇文章並存，說明一系列的伺服器通訊端和用戶端通訊端作業。 由於通訊端使用`CArchive`物件，它們一定是[串流處理通訊端](../mfc/windows-sockets-stream-sockets.md)。  
  
## <a name="sequence-of-operations-for-a-stream-socket-communication"></a>資料流通訊端通訊的作業順序  
 建構為止`CSocketFile`物件，以下列順序正確無誤 （有一些參數的差異） 兩者`CAsyncSocket`和`CSocket`。 從該點上，順序是嚴格的`CSocket`。 下表說明一系列的作業，設定用戶端與伺服器之間的通訊。  
  
### <a name="setting-up-communication-between-a-server-and-a-client"></a>設定伺服器的用戶端之間的通訊  
  
|伺服器|用戶端|  
|------------|------------|  
|`// construct a socket`<br /><br /> `CSocket sockSrvr;`|`// construct a socket`<br /><br /> `CSocket sockClient;`|  
|`// create the SOCKET`<br /><br /> `sockSrvr.Create(nPort);`1,2|`// create the SOCKET`<br /><br /> `sockClient.Create( );`2|  
|`// start listening`<br /><br /> `sockSrvr.Listen( );`||  
||`// seek a connection`<br /><br /> `sockClient.Connect(strAddr, nPort);`3,4|  
|`// construct a new, empty socket`<br /><br /> `CSocket sockRecv;`<br /><br /> `// accept connection`<br /><br /> `sockSrvr.Accept( sockRecv );` 5||  
|`// construct file object`<br /><br /> `CSocketFile file(&sockRecv);`|`// construct file object`<br /><br /> `CSocketFile file(&sockClient);`|  
|`// construct an archive`<br /><br /> `CArchive arIn(&file, CArchive::load);`<br /><br /> -或-<br /><br /> `CArchive arOut(&file, CArchive::store);`<br /><br /> -或者-|`// construct an archive`<br /><br /> `CArchive arIn(&file, CArchive::load);`<br /><br /> -或-<br /><br /> `CArchive arOut(&file, CArchive::store);`<br /><br /> -或者-|  
|`// use the archive to pass data:`<br /><br /> `arIn >> dwValue;`<br /><br /> -或-<br /><br /> `arOut << dwValue;`6|`// use the archive to pass data:`<br /><br /> `arIn >> dwValue;`<br /><br /> -或-<br /><br /> `arOut << dwValue;`6|  
  
 1. 其中*nPort*的通訊埠編號。 請參閱[Windows Sockets： 連接埠和通訊端位址](../mfc/windows-sockets-ports-and-socket-addresses.md)連接埠的詳細資料。  
  
 2. 讓用戶端可以連接的伺服器一定要指定連接埠。 `Create`有時也會呼叫指定的位址。 在用戶端，使用預設參數，這會要求 MFC 使用任何可用的通訊埠。  
  
 3. 其中*nPort*的通訊埠編號和*strAddr*是電腦位址或網際網路通訊協定 (IP) 位址。  
  
 4. 電腦位址可以採用數種格式:"ftp.microsoft.com"、"microsoft.com"。 IP 位址使用"點分隔的數字 「 表單 」 127.54.67.32"。 `Connect`函式會檢查位址是否為十進位數字 （雖然它不會檢查數字是否有效的電腦在網路上）。 如果沒有，`Connect`假設其中一個其他形式的電腦名稱。  
  
 5. 當您呼叫`Accept`在伺服器端，您將參考傳遞給新的通訊端物件。 您必須先建構這個物件，但不要呼叫`Create`它。 請注意，如果這個通訊端物件超出範圍，連接會關閉。 MFC 會連接至新的物件**通訊端**處理。 您可以建構在堆疊上，如所示，或在堆積上的通訊端。  
  
 6. 在超出範圍時，會關閉封存和通訊端檔案。 通訊端物件的解構函式也會呼叫[關閉](../mfc/reference/casyncsocket-class.md#close)通訊端物件，當物件超出範圍，或已刪除的成員函式。  
  
## <a name="additional-notes-about-the-sequence"></a>有關順序的其他注意事項  
 上表中所顯示的呼叫順序是資料流通訊端。 資料包通訊端，也就是無連線，不需要[CAsyncSocket::Connect](../mfc/reference/casyncsocket-class.md#connect)，[接聽](../mfc/reference/casyncsocket-class.md#listen)，和[接受](../mfc/reference/casyncsocket-class.md#accept)呼叫 (雖然您可以選擇性地使用`Connect`). 相反地，如果您使用類別`CAsyncSocket`，資料包通訊端使用`CAsyncSocket::SendTo`和`ReceiveFrom`成員函式。 (如果您使用`Connect`資料包通訊端中，您使用`Send`和`Receive`。)因為`CArchive`無法運作的資料流，請勿使用`CSocket`資料包通訊端是否封存。  
  
 [CSocketFile](../mfc/reference/csocketfile-class.md)不支援的所有`CFile`的功能。`CFile`這類成員`Seek`，其意義的通訊端通訊，就無法使用。 因此，有些預設 MFC`Serialize`函式與不相容`CSocketFile`。 特別的是`CEditView`類別。 您不應嘗試序列化`CEditView`資料透過`CArchive`物件附加至`CSocketFile`物件使用`CEditView::SerializeRaw`; 使用`CEditView::Serialize`改為 （未記載）。 [SerializeRaw](../mfc/reference/ceditview-class.md#serializeraw)函數必須要有 「 檔案 」 物件具有函式，例如`Seek`、 該`CSocketFile`不支援。  
  
 如需詳細資訊，請參閱:  
  
-   [Windows Sockets：搭配使用通訊端與封存](../mfc/windows-sockets-using-sockets-with-archives.md)  
  
-   [Windows Sockets：使用類別 CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)  
  
-   [Windows Sockets：連接埠和通訊端位址](../mfc/windows-sockets-ports-and-socket-addresses.md)  
  
-   [Windows Sockets：資料流通訊端](../mfc/windows-sockets-stream-sockets.md)  
  
-   [Windows Sockets：資料通訊端](../mfc/windows-sockets-datagram-sockets.md)  
  
## <a name="see-also"></a>另請參閱  
 [MFC 中的 Windows Sockets](../mfc/windows-sockets-in-mfc.md)   
 [CSocket 類別](../mfc/reference/csocket-class.md)   
 [CAsyncSocket::Create](../mfc/reference/casyncsocket-class.md#create)   
 [CAsyncSocket::Close](../mfc/reference/casyncsocket-class.md#close)

