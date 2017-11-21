---
title: "Windows Sockets： 通訊端通知 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- Windows Sockets [MFC], notifications
- notifications [MFC], socket
- sockets [MFC], notifications
ms.assetid: 87d5bf70-6e77-49a9-9a64-aaadee2ad018
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d37a45443efe1ad45e21c5729907135d0e037baa
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="windows-sockets-socket-notifications"></a>Windows Sockets：通訊端告知
本文說明通知中的函式的通訊端類別。 這些成員函式是在架構呼叫以通知您重要事件的通訊端物件的回呼函式。 通知函式會：  
  
-   [OnReceive](../mfc/reference/casyncsocket-class.md#onreceive)： 通知這個通訊端，才能藉由呼叫擷取緩衝區中沒有資料[接收](../mfc/reference/casyncsocket-class.md#receive)。  
  
-   [OnSend](../mfc/reference/casyncsocket-class.md#onsend)： 通知這個通訊端，則它現在可以藉由呼叫傳送資料[傳送](../mfc/reference/casyncsocket-class.md#send)。  
  
-   [OnAccept](../mfc/reference/casyncsocket-class.md#onaccept)： 通知其可接受暫止的連接要求，藉由呼叫這個接聽通訊端[接受](../mfc/reference/casyncsocket-class.md#accept)。  
  
-   [OnConnect](../mfc/reference/casyncsocket-class.md#onconnect)： 通知其連線嘗試完成此連接通訊端： 可能是成功或是發生錯誤。  
  
-   [OnClose](../mfc/reference/casyncsocket-class.md#onclose)： 告知通訊端連接到已關閉這個通訊端。  
  
    > [!NOTE]
    >  其他通知函式是[OnOutOfBandData](../mfc/reference/casyncsocket-class.md#onoutofbanddata)。 此通知會告知接收通訊端傳送的通訊端有要傳送的 「 超出訊號範圍 」 資料。 超出訊號範圍的資料是邏輯上獨立通道與連接的資料流通訊端每一對相關聯。 超出訊號範圍通道通常用來傳送 「 緊急 」 的資料。 MFC 支援的頻外的資料。 進階使用者使用類別[CAsyncSocket](../mfc/reference/casyncsocket-class.md)可能需要使用不足的頻外通道，但類別的使用者[CSocket](../mfc/reference/csocket-class.md)不建議使用它。 更簡單的方法是建立第二個通訊端，用來傳遞這類資料。 如需超出頻外資料的詳細資訊，請參閱 Windows Sockets 規格，可在 Windows SDK。  
  
 如果您是衍生自類別`CAsyncSocket`，那些網路應用程式的感興趣的事件，您必須覆寫通知函式。 如果您在衍生類別的類別`CSocket`，它是您選擇是否要覆寫感興趣的通知函式。 您也可以使用`CSocket`本身，在此情況下通知功能預設為不進行任何動作。  
  
 這些函式是可覆寫的回呼函式。 `CAsyncSocket`和`CSocket`轉換訊息通知，但如果您想要使用這些通知運作回應的方式，您必須實作。 在您的通訊端會收到通知的事件感興趣，例如要讀取的資料存在的時間稱為通知函式。  
  
 MFC 呼叫告知函式可讓您自訂您的通訊端行為時，會收到通知。 例如，您可能會呼叫**接收**從您`OnReceive`通知函式，也就是上正在執行通知可讀取的資料，您呼叫**接收**讀取它。 這種方法並非必要，但它是有效的案例。 或者，您可能會使用您的通知函式來追蹤進度，列印**追蹤**訊息，依此類推。  
  
 您可以利用這些通知告知函式，通訊端在衍生的類別中覆寫並提供實作。  
  
 在接收或傳送資料，例如作業期間`CSocket`物件變成同步。 在同步的狀態，適用於其他通訊端的任何通知會排入佇列等候它想要的通知的目前的通訊端時。 (例如，在**接收**呼叫時，通訊端想要讀取的通知。)一旦通訊端完成它的同步作業，並再次變成非同步，另一個通訊端可以開始接收佇列的通知。  
  
> [!NOTE]
>  在`CSocket`、`OnConnect`絕不會呼叫通知函式。 進行連線，您呼叫**連接**，這將會傳回時 （成功或錯誤），就可以完成連線。 連接告知的處理方式為 MFC 實作詳細資料。  
  
 如需每個通知函式的詳細資訊，請參閱類別底下函式`CAsyncSocket`中*MFC 參考*。 原始程式碼和 MFC 範例的相關資訊，請參閱[MFC 範例](../visual-cpp-samples.md)。  
  
 如需詳細資訊，請參閱:  
  
-   [Windows Sockets：使用類別 CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)  
  
-   [Windows Sockets：從通訊端類別衍生](../mfc/windows-sockets-deriving-from-socket-classes.md)  
  
-   [Windows Sockets：如何搭配使用通訊端與封存](../mfc/windows-sockets-how-sockets-with-archives-work.md)  
  
-   [Windows Sockets：封鎖](../mfc/windows-sockets-blocking.md)  
  
-   [Windows Sockets：位元組順序](../mfc/windows-sockets-byte-ordering.md)  
  
-   [Windows Sockets：轉換字串](../mfc/windows-sockets-converting-strings.md)  
  
## <a name="see-also"></a>另請參閱  
 [MFC 中的 Windows Sockets](../mfc/windows-sockets-in-mfc.md)

