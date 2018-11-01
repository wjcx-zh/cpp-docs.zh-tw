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
ms.openlocfilehash: 0c4f83ccd9bf431f7eb910f77409199da2b1325f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50476098"
---
# <a name="windows-sockets-in-mfc"></a>MFC 中的 Windows Sockets

> [!NOTE]
>  MFC 支援 Windows 通訊端 1，但不支援[Windows Sockets 2](/windows/desktop/WinSock/windows-sockets-start-page-2)。 Windows Sockets 2 首先會隨附於 Windows 98，是隨附於 Windows 2000 的版本。

MFC 提供兩種撰寫與 Windows 通訊端，在兩個 MFC 類別的網路通訊程式的模型。 這篇文章說明這些模型，並進一步的詳細資料 MFC 通訊端支援。 「 通訊端 」 是通訊的端點： 透過您的應用程式進行通訊與其他 Windows 通訊端應用程式在網路上的物件。

如需 Windows 通訊端，包括通訊端概念，說明請參閱[Windows Sockets： 背景](../mfc/windows-sockets-background.md)。

##  <a name="_core_sockets_programming_models"></a> 通訊端程式設計模型

兩個程式設計模型的 MFC Windows 通訊端會受到下列類別：

- `CAsyncSocket`

   此類別會封裝 Windows Sockets API。 [CAsyncSocket](../mfc/reference/casyncsocket-class.md)適合程式設計人員知道網路程式設計和想要直接對通訊端 API 進行程式設計的彈性但也想要的回呼函式的方便性，不論網路事件的通知。 以外封裝物件導向的表單，以用於 c + + 中的通訊端，只能將額外的抽象概念，這個類別會提供將某些通訊端相關的 Windows 訊息轉換回撥。 如需詳細資訊，請參閱 < [Windows Sockets： 通訊端告知](../mfc/windows-sockets-socket-notifications.md)。

- `CSocket`

   這個類別衍生自`CAsyncSocket`，提供透過 MFC 的通訊端所使用的較高層級抽象[CArchive](../mfc/reference/carchive-class.md)物件。 使用通訊端與封存，可大幅類似使用 MFC 的檔案序列化通訊協定。 這可讓您更輕鬆地使用比`CAsyncSocket`模型。 [CSocket](../mfc/reference/csocket-class.md)繼承許多成員函式，從`CAsyncSocket`，它會封裝 Windows Sockets Api，您必須使用其中一些函式，並了解一般程式設計的通訊端。 但是`CSocket`管理，您必須自行使用原始 API 或類別進行通訊的許多層面`CAsyncSocket`。 最重要的是，`CSocket`提供封鎖 （具有背景處理的 Windows 訊息），這是同步作業的`CArchive`。

建立和使用`CSocket`及`CAsyncSocket`物件所述[Windows Sockets： 使用通訊端與封存](../mfc/windows-sockets-using-sockets-with-archives.md)和[Windows Sockets： 使用類別 CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)。

##  <a name="_core_mfc_socket_samples_and_windows_sockets_dlls"></a> Windows 通訊端 Dll

Microsoft Windows 作業系統提供的 Windows 通訊端動態連結程式庫 (DLL)。 Visual c + + 提供適當的標頭檔和程式庫和 Windows Sockets 規格。

如需有關 Windows 通訊端的詳細資訊，請參閱：

- [Windows Sockets：資料流通訊端](../mfc/windows-sockets-stream-sockets.md)

- [Windows Sockets：資料通訊端](../mfc/windows-sockets-datagram-sockets.md)

- [Windows Sockets：搭配使用通訊端與封存](../mfc/windows-sockets-using-sockets-with-archives.md)

- [Windows Sockets：作業順序](../mfc/windows-sockets-sequence-of-operations.md)

- [Windows Sockets：使用封存的通訊端範例](../mfc/windows-sockets-example-of-sockets-using-archives.md)

- [Windows Sockets：如何搭配使用通訊端與封存](../mfc/windows-sockets-how-sockets-with-archives-work.md)

- [Windows Sockets：使用類別 CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)

- [Windows Sockets：從通訊端類別衍生](../mfc/windows-sockets-deriving-from-socket-classes.md)

- [Windows Sockets：通訊端通知](../mfc/windows-sockets-socket-notifications.md)

- [Windows Sockets：封鎖](../mfc/windows-sockets-blocking.md)

- [Windows Sockets：位元組順序](../mfc/windows-sockets-byte-ordering.md)

- [Windows Sockets：轉換字串](../mfc/windows-sockets-converting-strings.md)

- [Windows Sockets：連接埠和通訊端位址](../mfc/windows-sockets-ports-and-socket-addresses.md)

## <a name="see-also"></a>另請參閱

[Windows Sockets](../mfc/windows-sockets.md)

