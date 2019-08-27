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
ms.openlocfilehash: 44a4838a1cd863bd484701966a156be9f61f8988
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69510622"
---
# <a name="windows-sockets-in-mfc"></a>MFC 中的 Windows Sockets

> [!NOTE]
>  MFC 支援 Windows Socket 1, 但不支援[Windows socket 2](/windows/win32/WinSock/windows-sockets-start-page-2)。 Windows Socket 2 第一次隨附于 Windows 98, 是 Windows 2000 隨附的版本。

MFC 提供兩種模型來撰寫具有 Windows 通訊端的網路通訊程式, 其中包含在兩個 MFC 類別中。 本文說明這些模型, 以及 MFC 通訊端支援的進一步詳細資料。 「通訊端」是通訊的端點: 您的應用程式與網路上的其他 Windows 通訊端應用程式通訊的物件。

如需 Windows 通訊端的相關資訊, 包括通訊端概念的說明[, 請參閱 windows 通訊端:背景](../mfc/windows-sockets-background.md)。

##  <a name="_core_sockets_programming_models"></a>通訊端程式設計模型

下列類別支援兩個 MFC Windows 通訊端程式設計模型:

- `CAsyncSocket`

   此類別會封裝 Windows 通訊端 API。 [CAsyncSocket](../mfc/reference/casyncsocket-class.md)適用于瞭解網路程式設計的程式設計師, 而且想要能夠直接對通訊端 API 進行程式設計, 但也希望回呼函式的便利性可用於網路事件的通知。 除了以物件導向形式封裝通訊端以供使用之外C++, 此類別唯一提供的額外抽象概念是將特定通訊端相關的 Windows 訊息轉換成回呼。 如需詳細資訊, [請參閱 Windows socket:通訊端](../mfc/windows-sockets-socket-notifications.md)通知。

- `CSocket`

   這個衍生自`CAsyncSocket`的類別提供較高層級的抽象概念, 可讓您透過 MFC [CArchive](../mfc/reference/carchive-class.md)物件使用通訊端。 使用具有封存的通訊端, 與使用 MFC 的檔案序列化通訊協定很大類似。 這可讓您更輕鬆地使用`CAsyncSocket`模型。 [CSocket](../mfc/reference/csocket-class.md)繼承自`CAsyncSocket`的許多成員函式, 這些函式會封裝 Windows 通訊端 api; 您必須使用其中一些函式, 並以一般的來瞭解通訊端程式設計。 但是`CSocket` , 您必須使用原始 API 或類別`CAsyncSocket`來管理通訊的許多層面。 最重要的`CSocket`是, 會提供封鎖 (以 Windows 訊息的背景處理), 這對於的同步`CArchive`作業而言是不可或缺的。

建立和使用`CSocket`和`CAsyncSocket`物件的說明請[見 Windows socket:搭配使用通訊端](../mfc/windows-sockets-using-sockets-with-archives.md)與[封存和 Windows 通訊端:使用 [類別](../mfc/windows-sockets-using-class-casyncsocket.md)CAsyncSocket]。

##  <a name="_core_mfc_socket_samples_and_windows_sockets_dlls"></a>Windows 通訊端 Dll

Microsoft Windows 作業系統提供 Windows 通訊端動態連結程式庫 (DLL)。 視覺C++效果會提供適當的標頭檔和程式庫, 以及 Windows 通訊端規格。

如需 Windows 通訊端的詳細資訊, 請參閱:

- [Windows Socket：資料流通訊端](../mfc/windows-sockets-stream-sockets.md)

- [Windows Socket：資料包通訊端](../mfc/windows-sockets-datagram-sockets.md)

- [Windows Socket：搭配使用通訊端與封存](../mfc/windows-sockets-using-sockets-with-archives.md)

- [Windows Socket：作業序列](../mfc/windows-sockets-sequence-of-operations.md)

- [Windows Socket：使用封存的通訊端範例](../mfc/windows-sockets-example-of-sockets-using-archives.md)

- [Windows Socket：如何搭配使用通訊端與封存](../mfc/windows-sockets-how-sockets-with-archives-work.md)

- [Windows Socket：使用類別 CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)

- [Windows Socket：從通訊端類別衍生](../mfc/windows-sockets-deriving-from-socket-classes.md)

- [Windows Socket：通訊端通知](../mfc/windows-sockets-socket-notifications.md)

- [Windows Socket：封鎖](../mfc/windows-sockets-blocking.md)

- [Windows Socket：位元組順序](../mfc/windows-sockets-byte-ordering.md)

- [Windows Socket：轉換字串](../mfc/windows-sockets-converting-strings.md)

- [Windows Socket：連接埠和通訊端位址](../mfc/windows-sockets-ports-and-socket-addresses.md)

## <a name="see-also"></a>另請參閱

[Windows Sockets](../mfc/windows-sockets.md)
