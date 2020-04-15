---
title: MFC 中的 Windows Sockets
ms.date: 11/04/2016
helpviewer_keywords:
- WINSOCK.DLL
- sockets [MFC], programming models
- MFC, Windows Sockets
- Windows Sockets [MFC], MFC support
- Windows Sockets [MFC], programming models
- WSOCK32.DLL
- sockets [MFC], MFC
ms.assetid: 1f3c476a-9c68-49fe-9a25-d22971a334d0
ms.openlocfilehash: 8e5562b028d3d9b7cba4b47716b63fd1392c514f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371102"
---
# <a name="windows-sockets-in-mfc"></a>MFC 中的 Windows Sockets

> [!NOTE]
> MFC 支援 Windows 通訊端 1,但不支援[Windows 套接字 2](/windows/win32/WinSock/windows-sockets-start-page-2)。 Windows 套接字 2 首次隨 Windows 98 一起提供,是 Windows 2000 附帶的版本。

MFC 提供兩種模型,用於使用 Windows 套接字編寫網路通信程式,這體現在兩個 MFC 類中。 本文介紹了這些模型,以及 MFC 套接字支援的進一步詳細資訊。 "套接字"是通信的終結點:應用程式通過網络與其他 Windows 套接字應用程式通信的物件。

有關 Windows 通訊通訊字(包括通訊端) 的資訊概念的說明,請參閱[Windows 通訊排程:背景](../mfc/windows-sockets-background.md)。

## <a name="sockets-programming-models"></a><a name="_core_sockets_programming_models"></a>Socket 開發程式

以下類別支援兩種 MFC Windows 通訊卡字編程式模型:

- `CAsyncSocket`

   此類封裝 Windows 套接字 API。 [CAsyncSocket](../mfc/reference/casyncsocket-class.md)適用於瞭解網路程式設計並希望程式設計靈活性直接到套接字 API 的程式師,但也希望回調函數的便利性用於通知網路事件。 除了以面向物件的形式打包套接字以用於C++外,此類提供的唯一附加抽象是將某些與套接字相關的 Windows 消息轉換為回調。 有關詳細資訊,請參閱[Windows 通訊排單:socket 通知](../mfc/windows-sockets-socket-notifications.md)。

- `CSocket`

   此類派生自`CAsyncSocket`,提供更高級別的抽象,用於通過 MFC [CArchive](../mfc/reference/carchive-class.md)物件處理套接字。 使用具有存檔的套接字與使用 MFC 的檔序列化協定非常相似。 這使得它比`CAsyncSocket`模型更易於使用。 [CSocket](../mfc/reference/csocket-class.md)`CAsyncSocket`從 封裝 Windows 套接字 API 繼承了許多成員函數;您必須使用其中一些函數,並瞭解套接字程式設計。 但是`CSocket`管理通訊的許多方面,您必須自己使用原始 API`CAsyncSocket`或類別 。 最重要的是,`CSocket`提供阻塞(對 Windows 消息進行後台處理),這對於`CArchive`的同步操作至關重要。

建立與使用`CSocket``CAsyncSocket`與 物件在[Windows 通訊卡字中描述:使用包含存檔](../mfc/windows-sockets-using-sockets-with-archives.md)與 Windows[通訊的 socket:使用類別 CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)。

## <a name="windows-sockets-dlls"></a><a name="_core_mfc_socket_samples_and_windows_sockets_dlls"></a>Windows 通訊通訊字 DLL

微軟 Windows 作業系統提供 Windows 套接字動態連結庫 (DLL)。 可視C++提供相應的標頭檔和庫以及Windows套接字規範。

有關 Windows 套接字的詳細資訊,請參閱:

- [Windows Sockets：資料流通訊端](../mfc/windows-sockets-stream-sockets.md)

- [Windows Sockets：資料通訊端](../mfc/windows-sockets-datagram-sockets.md)

- [Windows Sockets：搭配使用通訊端與封存](../mfc/windows-sockets-using-sockets-with-archives.md)

- [Windows Sockets：作業順序](../mfc/windows-sockets-sequence-of-operations.md)

- [Windows Sockets：使用封存的通訊端範例](../mfc/windows-sockets-example-of-sockets-using-archives.md)

- [Windows Sockets：如何搭配使用通訊端與封存](../mfc/windows-sockets-how-sockets-with-archives-work.md)

- [Windows Sockets：使用類別 CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)

- [Windows Sockets：從通訊端類別衍生](../mfc/windows-sockets-deriving-from-socket-classes.md)

- [Windows Sockets：通訊端告知](../mfc/windows-sockets-socket-notifications.md)

- [Windows Sockets：封鎖](../mfc/windows-sockets-blocking.md)

- [Windows Sockets：位元組順序](../mfc/windows-sockets-byte-ordering.md)

- [Windows Sockets：轉換字串](../mfc/windows-sockets-converting-strings.md)

- [Windows Sockets：連接埠和通訊端位址](../mfc/windows-sockets-ports-and-socket-addresses.md)

## <a name="see-also"></a>另請參閱

[Windows Sockets](../mfc/windows-sockets.md)
