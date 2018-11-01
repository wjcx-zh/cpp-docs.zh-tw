---
title: Windows Sockets：封鎖
ms.date: 11/04/2016
helpviewer_keywords:
- sockets [MFC], blocking mode
- Windows Sockets [MFC], Windows platforms
- Windows Sockets [MFC], blocking mode
- sockets [MFC], behavior on different Windows platforms
- blocking mode sockets
ms.assetid: 10aca9b1-bfba-41a8-9c55-ea8082181e63
ms.openlocfilehash: 7b41f034e08570e418bf24d9d720795eafc37932
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50610570"
---
# <a name="windows-sockets-blocking"></a>Windows Sockets：封鎖

本文和兩個方針手冊說明了 Windows Sockets 程式設計的幾個問題。 本文包含封鎖問題。 文章中所涵蓋的其他問題： [Windows Sockets： 位元組順序](../mfc/windows-sockets-byte-ordering.md)並[Windows Sockets： 轉換字串](../mfc/windows-sockets-converting-strings.md)。

如果您使用或衍生自類別[CAsyncSocket](../mfc/reference/casyncsocket-class.md)，您必須自行管理這些問題。 如果您使用或衍生自類別[CSocket](../mfc/reference/csocket-class.md)，MFC 會為您管理它們。

## <a name="blocking"></a>封鎖

通訊端可能會處於「封鎖模式」或「未封鎖模式」。 處於封鎖 (或同步) 模式下的通訊端函式在完成其動作之後才會傳回。 之所以將這種情形稱為封鎖，是因為函式呼叫的通訊端在呼叫傳回之前無法執行任何動作 (即遭到封鎖)。 呼叫`Receive`成員函式，例如，可能需要很長的時間才能完成，它會等候傳送的應用程式傳送 (這是如果您使用`CSocket`，或使用`CAsyncSocket`與封鎖)。 如果`CAsyncSocket`物件處於封鎖模式 （非同步），則呼叫會立即傳回與目前錯誤的程式碼，以擷取[GetLastError](../mfc/reference/casyncsocket-class.md#getlasterror)成員函式，是**WSAEWOULDBLOCK**，表示會有封鎖的呼叫已因為該模式未立即傳回。 (`CSocket`絕對不會傳回**WSAEWOULDBLOCK**。 而類別會為您管理封鎖的問題)。

32 位元和 64 位元作業系統 (例如 Windows 95 或 Windows 98) 下的通訊端行為與 16 位元作業系統 (例如 Windows 3.1) 下的通訊端行為不同。 和 16 位元作業系統不同的是，32 位元與 64 位元作業系統使用先佔式多工作業，並提供多執行緒。 在 32 位元和 64 位元作業系統下，您可以將通訊端放在不同的背景工作執行緒中。 您可以封鎖執行緒中的某個通訊端，而不會影響應用程式中的其他活動，而且不需花費計算時間在封鎖上。 如需多執行緒程式設計的詳細資訊，請參閱文章[進行多執行緒處理](../parallel/multithreading-support-for-older-code-visual-cpp.md)。

> [!NOTE]
>  在多執行緒應用程式中，您可以使用 `CSocket` 的封鎖性質來簡化您程式的設計，而不會影響使用者介面的回應性。 藉由在主執行緒中處理使用者互動，並在其他執行緒中處理 `CSocket`，您可以將這些邏輯作業分離。 在未採用多執行緒的應用程式中，這兩種活動必須合併並視為單一執行緒來處理，這通常表示使用 `CAsyncSocket` 時，您可以視需要處理通訊要求，或覆寫 `CSocket::OnMessagePending` 以便在長時間的同步處理活動期間處理使用者動作。

其餘的討論適用於以 16 位元作業系統為目標的程式設計人員：

通常，如果您使用 `CAsyncSocket`，則應該避免使用封鎖作業，而改用非同步作業。 在非同步作業中，從您收到的點**WSAEWOULDBLOCK**之後呼叫的錯誤碼`Receive`，例如，您等到您`OnReceive`成員函式會呼叫以通知您，您可以讀取一次。 非同步呼叫會藉由呼叫傳回通訊端的適當的回呼通知函式，例如[OnReceive](../mfc/reference/casyncsocket-class.md#onreceive)。

在視窗中不建議採用封鎖呼叫。 根據預設， [CAsyncSocket](../mfc/reference/casyncsocket-class.md)支援非同步呼叫，而且您必須管理封鎖自行使用回呼通知。 類別[CSocket](../mfc/reference/csocket-class.md)，相反地，是同步的。 它會提取 Windows 訊息並為您管理封鎖。

如需封鎖的詳細資訊，請參閱 Windows Sockets 規格。 "On"函式的相關資訊，請參閱[Windows Sockets： 通訊端告知](../mfc/windows-sockets-socket-notifications.md)並[Windows Sockets： 從通訊端類別衍生](../mfc/windows-sockets-deriving-from-socket-classes.md)。

如需詳細資訊，請參閱:

- [Windows Sockets：使用類別 CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)

- [Windows Sockets：搭配使用通訊端與封存](../mfc/windows-sockets-using-sockets-with-archives.md)

- [Windows Sockets：背景](../mfc/windows-sockets-background.md)

- [Windows Sockets：資料流通訊端](../mfc/windows-sockets-stream-sockets.md)

- [Windows Sockets：資料通訊端](../mfc/windows-sockets-datagram-sockets.md)

## <a name="see-also"></a>另請參閱

[MFC 中的 Windows Sockets](../mfc/windows-sockets-in-mfc.md)<br/>
[CAsyncSocket::OnSend](../mfc/reference/casyncsocket-class.md#onsend)

