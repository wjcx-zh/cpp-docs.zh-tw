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
ms.openlocfilehash: 87d4f0eb57f9e26dbf73da06b5d7ca6d61d6c174
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81359988"
---
# <a name="windows-sockets-blocking"></a>Windows Sockets：封鎖

本文和兩個方針手冊說明了 Windows Sockets 程式設計的幾個問題。 本文包含封鎖問題。 其他問題在文章中介紹[:Windows套接字:位元組排序](../mfc/windows-sockets-byte-ordering.md), 與 Windows 通訊排序與 Windows[socket:轉換字串](../mfc/windows-sockets-converting-strings.md)。

如果您使用或派生自類[CAsyncSocket,](../mfc/reference/casyncsocket-class.md)則需要自己管理這些問題。 如果您使用或派生自[CSocket](../mfc/reference/csocket-class.md)類,MFC 會為您管理它們。

## <a name="blocking"></a>封鎖

通訊端可能會處於「封鎖模式」或「未封鎖模式」。 處於封鎖 (或同步) 模式下的通訊端函式在完成其動作之後才會傳回。 之所以將這種情形稱為封鎖，是因為函式呼叫的通訊端在呼叫傳回之前無法執行任何動作 (即遭到封鎖)。 例如,對成員`Receive`函數的調用可能需要任意很長時間才能完成,因為它等待發送應用程式發送(這是如果您正在`CSocket`使用 或與阻塞一起使用`CAsyncSocket`)。 如果`CAsyncSocket`物件處於非阻塞模式(非同步操作),則調用會立即返回,並且當前錯誤代碼(使用[GetLastError](../mfc/reference/casyncsocket-class.md#getlasterror)成員函數可檢索)為**WSAEANDBLOCK,** 指示如果呼叫由於該模式而沒有立即返回,則該調用將被阻止。 (`CSocket`從不返回**WSAEE.BLOCK**。 而類別會為您管理封鎖的問題)。

32 位元和 64 位元作業系統 (例如 Windows 95 或 Windows 98) 下的通訊端行為與 16 位元作業系統 (例如 Windows 3.1) 下的通訊端行為不同。 和 16 位元作業系統不同的是，32 位元與 64 位元作業系統使用先佔式多工作業，並提供多執行緒。 在 32 位元和 64 位元作業系統下，您可以將通訊端放在不同的背景工作執行緒中。 您可以封鎖執行緒中的某個通訊端，而不會影響應用程式中的其他活動，而且不需花費計算時間在封鎖上。 有關多線程程式設計的資訊,請參閱文章[「多線程」。。](../parallel/multithreading-support-for-older-code-visual-cpp.md)

> [!NOTE]
> 在多執行緒應用程式中，您可以使用 `CSocket` 的封鎖性質來簡化您程式的設計，而不會影響使用者介面的回應性。 藉由在主執行緒中處理使用者互動，並在其他執行緒中處理 `CSocket`，您可以將這些邏輯作業分離。 在未採用多執行緒的應用程式中，這兩種活動必須合併並視為單一執行緒來處理，這通常表示使用 `CAsyncSocket` 時，您可以視需要處理通訊要求，或覆寫 `CSocket::OnMessagePending` 以便在長時間的同步處理活動期間處理使用者動作。

其餘的討論適用於以 16 位元作業系統為目標的程式設計人員：

通常，如果您使用 `CAsyncSocket`，則應該避免使用封鎖作業，而改用非同步作業。 在非同步操作中,從呼叫`Receive`後收到**WSAETOBLOCK**錯誤代碼的點開始,例如`OnReceive`,等待成員 函數調用以通知您可以再次讀取。 非同步調用是透過調用套接字的相應回檔通知功能(如[OnReceive)](../mfc/reference/casyncsocket-class.md#onreceive)進行的。

在視窗中不建議採用封鎖呼叫。 預設情況下[,CAsyncSocket](../mfc/reference/casyncsocket-class.md)支援非同步調用,您必須使用回調通知自行管理阻止。 另一方面[,CSocket](../mfc/reference/csocket-class.md)類是同步的。 它會提取 Windows 訊息並為您管理封鎖。

如需封鎖的詳細資訊，請參閱 Windows Sockets 規格。 有關"開"功能的詳細資訊,請參閱[Windows 套接字:套接字通知](../mfc/windows-sockets-socket-notifications.md)和[Windows 套接字:從套接字類派生](../mfc/windows-sockets-deriving-from-socket-classes.md)。

如需詳細資訊，請參閱

- [Windows Sockets：使用類別 CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)

- [Windows Sockets：搭配使用通訊端與封存](../mfc/windows-sockets-using-sockets-with-archives.md)

- [Windows Sockets：背景](../mfc/windows-sockets-background.md)

- [Windows Sockets：資料流通訊端](../mfc/windows-sockets-stream-sockets.md)

- [Windows Sockets：資料通訊端](../mfc/windows-sockets-datagram-sockets.md)

## <a name="see-also"></a>另請參閱

[MFC 中的 Windows Sockets](../mfc/windows-sockets-in-mfc.md)<br/>
[CAsyncSocket:開啟傳送](../mfc/reference/casyncsocket-class.md#onsend)
