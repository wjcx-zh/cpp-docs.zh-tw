---
title: MFC 中的 Windows Sockets |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- WINSOCK.DLL
- sockets [MFC], programming models
- MFC, Windows Sockets
- Windows Sockets [MFC], MFC support
- Windows Sockets [MFC], programming models
- WSOCK32.DLL
- sockets [MFC], MFC
ms.assetid: 1f3c476a-9c68-49fe-9a25-d22971a334d0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 84fc25ab6515b22fa647b3cc32833c791b59f2b8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33385508"
---
# <a name="windows-sockets-in-mfc"></a>MFC 中的 Windows Sockets
> [!NOTE]
>  MFC 支援 Windows 通訊端 1，但不支援[Windows 通訊端 2](http://msdn.microsoft.com/library/windows/desktop/ms740673)。 Windows 通訊端 2 第一次隨附於 Windows 98，且是隨附於 Windows 2000 的版本。  
  
 MFC 提供兩種撰寫與 Windows 通訊端，卻在兩個 MFC 類別中的網路通訊程式的模型。 這篇文章描述這些模型，並進一步的詳細資料 MFC 通訊端支援。 「 通訊端 」 是通訊的端點： 透過此應用程式進行通訊與其他 Windows 通訊端應用程式在網路上的物件。  
  
 如需有關 Windows 通訊端，包括通訊端概念的說明資訊，請參閱[Windows Sockets： 背景](../mfc/windows-sockets-background.md)。  
  
##  <a name="_core_sockets_programming_models"></a> 通訊端程式設計模型  
 兩個 MFC Windows Sockets 程式設計模型支援下列類別：  
  
-   `CAsyncSocket`  
  
     這個類別會封裝 Windows Sockets API。 [CAsyncSocket](../mfc/reference/casyncsocket-class.md)適用於程式設計人員知道網路程式設計和想要直接到通訊端 API 進行程式設計的彈性但是也會想回呼函式的方便性，不論網路事件的通知。 以外封裝通訊端物件導向的表單，以用於 c + + 中，這個類別會提供唯一的額外的抽象概念將特定通訊端相關 Windows 訊息轉換成回呼。 如需詳細資訊，請參閱[Windows Sockets： 通訊端告知](../mfc/windows-sockets-socket-notifications.md)。  
  
-   `CSocket`  
  
     這個類別，衍生自`CAsyncSocket`，提供使用 MFC 透過通訊端的較高層級抽象[CArchive](../mfc/reference/carchive-class.md)物件。 使用通訊端與封存可大幅類似使用 MFC 的檔案序列化通訊協定。 這可讓您更輕鬆地使用比`CAsyncSocket`模型。 [CSocket](../mfc/reference/csocket-class.md)繼承許多成員函式，從`CAsyncSocket`，封裝 Windows Sockets Api，您必須使用其中一些函式，並了解一般程式設計通訊端。 但是`CSocket`管理的通訊，您必須自行使用原始應用程式開發介面或類別進行的許多層面`CAsyncSocket`。 最重要的是，`CSocket`提供封鎖 （具有背景處理 Windows 訊息），這是同步的作業不可或缺`CArchive`。  
  
 建立和使用`CSocket`和`CAsyncSocket`物件述[Windows Sockets： 使用通訊端與封存](../mfc/windows-sockets-using-sockets-with-archives.md)和[Windows Sockets： 使用類別 CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)。  
  
##  <a name="_core_mfc_socket_samples_and_windows_sockets_dlls"></a> Windows Sockets Dll  
 Microsoft Windows 作業系統提供的 Windows Sockets 動態連結程式庫 (DLL)。 Visual c + + 提供適當的標頭檔和程式庫和 Windows Sockets 規格。  
  
 如需 Windows 通訊端的詳細資訊，請參閱：  
  
-   [Windows Sockets：資料流通訊端](../mfc/windows-sockets-stream-sockets.md)  
  
-   [Windows Sockets：資料通訊端](../mfc/windows-sockets-datagram-sockets.md)  
  
-   [Windows Sockets：搭配使用通訊端與封存](../mfc/windows-sockets-using-sockets-with-archives.md)  
  
-   [Windows Sockets：作業順序](../mfc/windows-sockets-sequence-of-operations.md)  
  
-   [Windows Sockets：使用封存的通訊端範例](../mfc/windows-sockets-example-of-sockets-using-archives.md)  
  
-   [Windows Sockets：如何搭配使用通訊端與封存](../mfc/windows-sockets-how-sockets-with-archives-work.md)  
  
-   [Windows Sockets：使用類別 CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)  
  
-   [Windows Sockets：從通訊端類別衍生](../mfc/windows-sockets-deriving-from-socket-classes.md)  
  
-   [Windows Sockets：通訊端通知](../mfc/windows-sockets-socket-notifications.md)  
  
-   [Windows Sockets：封鎖](../mfc/windows-sockets-blocking.md)  
  
-   [Windows Sockets：位元組順序](../mfc/windows-sockets-byte-ordering.md)  
  
-   [Windows Sockets：轉換字串](../mfc/windows-sockets-converting-strings.md)  
  
-   [Windows Sockets：連接埠和通訊端位址](../mfc/windows-sockets-ports-and-socket-addresses.md)  
  
## <a name="see-also"></a>另請參閱  
 [Windows Sockets](../mfc/windows-sockets.md)

