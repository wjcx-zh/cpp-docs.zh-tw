---
title: Windows Sockets:通訊端告知
ms.date: 11/04/2016
helpviewer_keywords:
- Windows Sockets [MFC], notifications
- notifications [MFC], socket
- sockets [MFC], notifications
ms.assetid: 87d5bf70-6e77-49a9-9a64-aaadee2ad018
ms.openlocfilehash: df7bfe8a95221682d0f7f4ebb123bd15b79144d5
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/05/2019
ms.locfileid: "58774330"
---
# <a name="windows-sockets-socket-notifications"></a>Windows Sockets:通訊端告知

本文說明通知中的函式的通訊端類別。 這些成員函式是在架構呼叫以通知您的通訊端物件的重要事件的回呼函式。 告知函式如下：

- [OnReceive](../mfc/reference/casyncsocket-class.md#onreceive):它藉由呼叫擷取緩衝區中沒有資料會告知此通訊端[接收](../mfc/reference/casyncsocket-class.md#receive)。

- [OnSend](../mfc/reference/casyncsocket-class.md#onsend):它現在可以傳送資料的呼叫會通知此通訊端[傳送](../mfc/reference/casyncsocket-class.md#send)。

- [OnAccept](../mfc/reference/casyncsocket-class.md#onaccept):它可以接受暫止連接要求，藉由呼叫這個接聽通訊端會告知[接受](../mfc/reference/casyncsocket-class.md#accept)。

- [OnConnect](../mfc/reference/casyncsocket-class.md#onconnect):通知其連線嘗試完成此連線通訊端： 可能是成功或是發生錯誤。

- [OnClose](../mfc/reference/casyncsocket-class.md#onclose):通知已關閉通訊端連線到此通訊端。

    > [!NOTE]
    >  另一個通知函式[OnOutOfBandData](../mfc/reference/casyncsocket-class.md#onoutofbanddata)。 此通知會告知接收通訊端傳送的通訊端具有 「 超出頻外 」 的資料，來傳送。 超出訊號範圍的資料是每一對連接的資料流通訊端相關聯的邏輯上獨立通道。 頻外通道通常用來傳送 「 urgent 」 的資料。 MFC 支援頻外的資料。 進階使用者使用類別[CAsyncSocket](../mfc/reference/casyncsocket-class.md)可能需要使用頻外通道，但類別的使用者[CSocket](../mfc/reference/csocket-class.md)不鼓勵使用它。 更簡單的方法是建立傳遞這類資料的第二個通訊端。 如需頻外資料的詳細資訊，請參閱 Windows Sockets 規格，可在 Windows SDK。

如果您從類別衍生`CAsyncSocket`，那些網路到您的應用程式感興趣的事件，您必須覆寫通知函式。 如果您從類別衍生類別`CSocket`，它是您選擇是否要覆寫感興趣的通知函式。 您也可以使用`CSocket`本身，在此情況下通知函式預設為不進行任何動作。

這些函式是可覆寫的回呼函式。 `CAsyncSocket` 和`CSocket`轉換訊息通知，但您必須實作通知如何運作回應，如果您想要使用它們。 告知函式會在您的通訊端會收到通知的事件感興趣，例如要讀取資料的目前狀態的時間呼叫。

MFC 呼叫通知函式，讓您自訂您的通訊端行為時，會收到通知。 例如，您可能會呼叫`Receive`從您`OnReceive`通知函式，也就是上正在執行通知可讀取的資料時，您呼叫`Receive`讀取它。 這種方法並非必要，但它是有效的案例。 或者，您可以使用您的通知函式，來追蹤進度，列印**追蹤**訊息，依此類推。

您可以利用這些通知藉由覆寫衍生通訊端類別中的通知函式，並提供實作。

例如，接收或傳送資料，作業期間`CSocket`物件會變成同步。 在同步的狀態，任何適用於其他通訊端的通知已排入佇列等候它想要的通知的目前通訊端時。 (例如，在期間`Receive`呼叫時，通訊端想要讀取的通知。)一旦通訊端完成它的同步作業，並再次變成非同步，另一個通訊端可以開始接收已排入佇列的通知。

> [!NOTE]
>  在  `CSocket`，則`OnConnect`絕不會呼叫通知函式。 在您呼叫的連接， `Connect`，這會傳回時 （成功或錯誤），就可以完成連線。 如何處理連接通知是 MFC 實作細節。

如需每個通知函式的詳細資訊，請參閱函式類別之下`CAsyncSocket`中*MFC 參考 》*。 原始程式碼和 MFC 範例的相關資訊，請參閱[MFC 範例](../overview/visual-cpp-samples.md)。

如需詳細資訊，請參閱:

- [Windows Sockets:使用類別 CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)

- [Windows Sockets:衍生自通訊端類別](../mfc/windows-sockets-deriving-from-socket-classes.md)

- [Windows Sockets:通訊端與封存的運作方式](../mfc/windows-sockets-how-sockets-with-archives-work.md)

- [Windows Sockets:封鎖](../mfc/windows-sockets-blocking.md)

- [Windows Sockets:位元組順序](../mfc/windows-sockets-byte-ordering.md)

- [Windows Sockets:將字串轉換](../mfc/windows-sockets-converting-strings.md)

## <a name="see-also"></a>另請參閱

[MFC 中的 Windows Sockets](../mfc/windows-sockets-in-mfc.md)
