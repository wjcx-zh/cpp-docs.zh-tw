---
title: Windows Sockets：通訊端告知
ms.date: 11/04/2016
helpviewer_keywords:
- Windows Sockets [MFC], notifications
- notifications [MFC], socket
- sockets [MFC], notifications
ms.assetid: 87d5bf70-6e77-49a9-9a64-aaadee2ad018
ms.openlocfilehash: 10dbe6c0e1f486257c50efc4acf917cd9d596630
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80167767"
---
# <a name="windows-sockets-socket-notifications"></a>Windows Sockets：通訊端告知

本文說明通訊端類別中的通知函式。 這些成員函式是回呼函式，架構會呼叫這些函式來通知您的通訊端物件有重要事件。 通知函數包括：

- [OnReceive](../mfc/reference/casyncsocket-class.md#onreceive)：通知此通訊端有緩衝區中的資料，可透過呼叫[Receive](../mfc/reference/casyncsocket-class.md#receive)來抓取。

- [OnSend](../mfc/reference/casyncsocket-class.md#onsend)：通知這個通訊端現在可以藉由呼叫[send](../mfc/reference/casyncsocket-class.md#send)來傳送資料。

- [OnAccept](../mfc/reference/casyncsocket-class.md#onaccept)：通知此接聽通訊端，它可以藉由呼叫[accept](../mfc/reference/casyncsocket-class.md#accept)來接受擱置的連線要求。

- [OnConnect](../mfc/reference/casyncsocket-class.md#onconnect)：通知此連接通訊端，其連線嘗試已完成：可能是成功或可能發生錯誤。

- [OnClose](../mfc/reference/casyncsocket-class.md#onclose)：通知這個通訊端它所連線的通訊端已關閉。

    > [!NOTE]
    >  另一個通知函數是[OnOutOfBandData](../mfc/reference/casyncsocket-class.md#onoutofbanddata)。 此通知會告訴接收通訊端，傳送通訊端有「頻外」的資料要傳送。 頻外資料是與每一對已連線串流通訊端相關聯的邏輯獨立通道。 頻外通道通常用來傳送「緊急」資料。 MFC 支援頻外資料。 使用 [類別[CAsyncSocket](../mfc/reference/casyncsocket-class.md) ] 的 Advanced 使用者可能需要使用頻外通道，但不鼓勵使用類別[CSocket](../mfc/reference/csocket-class.md)的使用者。 較簡單的方式是建立第二個通訊端來傳遞這類資料。 如需頻外資料的詳細資訊，請參閱 Windows SDK 中提供的 Windows 通訊端規格。

如果您衍生自類別 `CAsyncSocket`，則必須覆寫應用程式感關注之網路事件的通知函式。 如果您從類別 `CSocket`衍生類別，您可以選擇是否要覆寫相關的通知函數。 您也可以使用 `CSocket` 本身，在此情況下，通知函式會預設為不執行任何動作。

這些函數是可覆寫的回呼函數。 `CAsyncSocket` 和 `CSocket` 將訊息轉換為通知，但如果您想要使用通知函式，則必須執行其回應方式。 通知函式會在您的通訊端收到相關事件的通知時呼叫，例如要讀取的資料。

MFC 會呼叫通知函式，讓您在收到通知時自訂通訊端的行為。 例如，您可能會從 `OnReceive` 通知函式呼叫 `Receive`，也就是收到通知指出有資料要讀取時，您會呼叫 `Receive` 來讀取它。 這種方法並不是必要的，但這是有效的案例。 或者，您可以使用通知函式來追蹤進度、列印**追蹤**訊息等等。

您可以藉由覆寫衍生通訊端類別中的通知函式，並提供實作為，來利用這些通知。

在接收或傳送資料之類的作業期間，`CSocket` 物件會變成同步。 在同步狀態期間，所有適用于其他通訊端的通知都會排入佇列，而目前的通訊端會等待它想要的通知。 （例如，在 `Receive` 呼叫期間，通訊端需要通知來進行讀取）。一旦通訊端完成其同步作業並再次變成非同步，其他通訊端就可以開始接收佇列通知。

> [!NOTE]
> 在 `CSocket`中，永遠不會呼叫 `OnConnect` 通知函式。 針對連接，您可以呼叫 `Connect`，這會在連接完成時傳回（不論是成功或錯誤）。 連接通知的處理方式是 MFC 的執行詳細資料。

如需每個通知函式的詳細資訊，請參閱*MFC 參考*中的 class `CAsyncSocket` 下的函式。 如需原始程式碼和 MFC 範例的相關資訊，請參閱[Mfc 範例](../overview/visual-cpp-samples.md#mfc-samples)。

如需詳細資訊，請參閱

- [Windows Sockets：使用類別 CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)

- [Windows Sockets：從通訊端類別衍生](../mfc/windows-sockets-deriving-from-socket-classes.md)

- [Windows Sockets：如何搭配使用通訊端與封存](../mfc/windows-sockets-how-sockets-with-archives-work.md)

- [Windows Sockets：封鎖](../mfc/windows-sockets-blocking.md)

- [Windows Sockets：位元組順序](../mfc/windows-sockets-byte-ordering.md)

- [Windows Sockets：轉換字串](../mfc/windows-sockets-converting-strings.md)

## <a name="see-also"></a>另請參閱

[MFC 中的 Windows Sockets](../mfc/windows-sockets-in-mfc.md)
