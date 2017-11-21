---
title: "Windows Sockets： 搭配使用通訊端與封存 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- Windows Sockets [MFC], archives
- sockets [MFC], with archives
- archives [MFC], and Windows Sockets
- CSocket class [MFC], programming model
ms.assetid: 17e71a99-a09e-4e1a-9fda-13d62805c824
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 3eb7d6c18e1a1fd77e0c0c8506d46536add5cb21
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="windows-sockets-using-sockets-with-archives"></a>Windows Sockets：搭配使用通訊端與封存
本文說明[CSocket 程式設計模型](#_core_the_csocket_programming_model)。 類別[CSocket](../mfc/reference/csocket-class.md)提供通訊端支援，在較高層級的抽象類別比[CAsyncSocket](../mfc/reference/casyncsocket-class.md)。 `CSocket`使用 MFC 序列化通訊協定的版本來傳遞資料，經由 MFC 通訊端物件來回[CArchive](../mfc/reference/carchive-class.md)物件。 `CSocket` 會提供封鎖 (同時管理 Windows 訊息的背景處理)，並且可讓您存取 `CArchive`，它可管理有關通訊的多個層面，否則您必須使用原始 API 或 `CAsyncSocket` 類別才能自行管理這些層面。  
  
> [!TIP]
>  您可以單獨使用 `CSocket` 類別做為更方便的 `CAsyncSocket` 版本，不過，最簡單的程式設計模型是使用 `CSocket` 搭配 `CArchive` 物件。  
  
 如需實作的通訊端與封存的運作方式的詳細資訊，請參閱[Windows Sockets： 如何通訊端與封存工作](../mfc/windows-sockets-how-sockets-with-archives-work.md)。 如需範例程式碼，請參閱[Windows Sockets： 作業的順序](../mfc/windows-sockets-sequence-of-operations.md)和[Windows Sockets： 通訊端使用封存的範例](../mfc/windows-sockets-example-of-sockets-using-archives.md)。 如需某些功能的資訊便可以藉由從通訊端類別衍生您自己的類別，請參閱[Windows Sockets： 從通訊端類別衍生](../mfc/windows-sockets-deriving-from-socket-classes.md)。  
  
> [!NOTE]
>  如果您要撰寫 MFC 用戶端程式與所建立的 (非 MFC) 伺服器進行通訊，請不要透過封存傳送 C++ 物件。 除非伺服器是 MFC 應用程式並且了解您想要傳送的物件種類，否則它將無法接收和還原序列化您的物件。 相關的主體和非 MFC 應用程式通訊的詳細資料，也請參閱文件[Windows Sockets： 位元組順序](../mfc/windows-sockets-byte-ordering.md)。  
  
##  <a name="_core_the_csocket_programming_model"></a>CSocket 程式設計模型  
 使用 `CSocket` 物件包含了建立數個 MFC 類別物件，並讓這些物件彼此相關聯。 在下面的一般程序中，每一個步驟都是由伺服器通訊端與用戶端通訊端所進行，除了步驟 3，該步驟中的每種通訊端類型需要一個不同的動作。  
  
> [!TIP]
>  在執行階段中，伺服器應用程式通常會先啟動並準備好，然後在用戶端應用程式尋找連接時「接聽」。 如果用戶端嘗試連接時伺服器尚未準備好，通常會需要使用者應用程式嘗試再次連接。  
  
#### <a name="to-set-up-communication-between-a-server-socket-and-a-client-socket"></a>設定伺服器通訊端與用戶端通訊端之間的通訊  
  
1.  建構[CSocket](../mfc/reference/csocket-class.md)物件。  
  
2.  使用物件來建立基礎**通訊端**處理。  
  
     如`CSocket`用戶端物件，您通常應該使用預設的參數[建立](../mfc/reference/casyncsocket-class.md#create)，除非您需要資料包通訊端。 如`CSocket`伺服器物件，您必須指定中的連接埠**建立**呼叫。  
  
    > [!NOTE]
    >  `CArchive` 無法搭配資料包通訊端使用。 如果您要對資料包通訊端使用 `CSocket`，則必須使用類別，就像使用 `CAsyncSocket` 一樣，也就是沒有封存。 由於資料包並不可靠 (不保證會達到，而且可能會重複或未依照順序)，因此它們無法透過封存與序列化相容。 您會希望序列化作業能夠確實依序順利完成。 如果您嘗試對資料包使用 `CSocket` 搭配 `CArchive` 物件，MFC 判斷提示就會失敗。  
  
3.  如果用戶端通訊端，呼叫[CAsyncSocket::Connect](../mfc/reference/casyncsocket-class.md#connect)來連接到伺服器通訊端通訊端物件。  
  
     -或-  
  
     如果伺服器通訊端，呼叫[CAsyncSocket::Listen](../mfc/reference/casyncsocket-class.md#listen)開始接聽連接嘗試從用戶端。 在收到連線要求時，接受它藉由呼叫[CAsyncSocket::Accept](../mfc/reference/casyncsocket-class.md#accept)。  
  
    > [!NOTE]
    >  **接受**成員函式會採用新的空白參考`CSocket`做為其參數的物件。 您必須先建構這個物件，才能呼叫**接受**。 如果這個通訊端物件超出範圍，連接就會關閉。 請勿呼叫**建立**對這個新通訊端物件。  
  
4.  建立[CSocketFile](../mfc/reference/csocketfile-class.md)物件、 將相關聯`CSocket`與它的物件。  
  
5.  建立[CArchive](../mfc/reference/carchive-class.md)載入 （接收） 或儲存 （傳送） 資料的物件。 封存會與 `CSocketFile` 物件相關聯。  
  
     務必記住，`CArchive` 無法與資料包通訊端搭配使用。  
  
6.  請使用 `CArchive` 物件在用戶端和伺服器通訊端之間傳遞資料。  
  
     請記住，一個特定 `CArchive` 物件只會朝某一方向移動資料：載入 (接收) 或儲存 (傳送)。 在某些情況下，您會使用兩個 `CArchive` 物件：一個用於傳送資料，另一個用於接收認可。  
  
     在接受連接併設定封存之後，您就可以執行像是驗證密碼這類工作。  
  
7.  終結封存、通訊端檔案和通訊端物件。  
  
    > [!NOTE]
    >  `CArchive` 類別明確提供了 `IsBufferEmpty` 成員函式搭配 `CSocket` 類別使用。 例如，如果緩衝區包含多個資料訊息，您就需要執行迴圈，直到所有訊息都已讀且緩衝區已清除。 否則，告知您有資料要接收的下一個通知可能會無限期延遲。 使用 `IsBufferEmpty` 可確保擷取所有資料。  
  
 發行項[Windows Sockets： 作業的順序](../mfc/windows-sockets-sequence-of-operations.md)說明此程序範例程式碼的兩端。  
  
 如需詳細資訊，請參閱:  
  
-   [Windows Sockets：資料流通訊端](../mfc/windows-sockets-stream-sockets.md)  
  
-   [Windows Sockets：資料通訊端](../mfc/windows-sockets-datagram-sockets.md)  
  
## <a name="see-also"></a>另請參閱  
 [MFC 中的 Windows Sockets](../mfc/windows-sockets-in-mfc.md)   
 [CSocket::Create](../mfc/reference/csocket-class.md#create)

