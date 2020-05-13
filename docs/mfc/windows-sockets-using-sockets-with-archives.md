---
title: Windows Sockets：搭配使用通訊端與封存
ms.date: 11/04/2016
helpviewer_keywords:
- Windows Sockets [MFC], archives
- sockets [MFC], with archives
- archives [MFC], and Windows Sockets
- CSocket class [MFC], programming model
ms.assetid: 17e71a99-a09e-4e1a-9fda-13d62805c824
ms.openlocfilehash: 55b4f9a5412c1447fe2b3bde10cb934b91abf008
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81359957"
---
# <a name="windows-sockets-using-sockets-with-archives"></a>Windows Sockets：搭配使用通訊端與封存

本文介紹了[CSocket 編程模型](#_core_the_csocket_programming_model)。 類[CSocket](../mfc/reference/csocket-class.md)在比類[CAsyncSocket](../mfc/reference/casyncsocket-class.md)更高的抽象級別提供套接字支援。 `CSocket`使用 MFC 序列化協定的版本通過 MFC [CArchive](../mfc/reference/carchive-class.md)物件將數據傳遞到套接字物件。 `CSocket` 會提供封鎖 (同時管理 Windows 訊息的背景處理)，並且可讓您存取 `CArchive`，它可管理有關通訊的多個層面，否則您必須使用原始 API 或 `CAsyncSocket` 類別才能自行管理這些層面。

> [!TIP]
> 您可以單獨使用 `CSocket` 類別做為更方便的 `CAsyncSocket` 版本，不過，最簡單的程式設計模型是使用 `CSocket` 搭配 `CArchive` 物件。

有關使用存檔的 socket 實現如何的詳細資訊,請參閱 Windows[套接字:具有存檔的套接字的工作原理](../mfc/windows-sockets-how-sockets-with-archives-work.md)。 例如代碼,請參閱[Windows 通訊排序的字串,操作序列](../mfc/windows-sockets-sequence-of-operations.md)與[Windows 通訊卡字:使用存檔的 socket 範例](../mfc/windows-sockets-example-of-sockets-using-archives.md)。 有關從套接字類派生自己的類可以獲得的某些功能的資訊,請參閱[Windows 套接字:從套接字類派生](../mfc/windows-sockets-deriving-from-socket-classes.md)。

> [!NOTE]
> 如果您要撰寫 MFC 用戶端程式與所建立的 (非 MFC) 伺服器進行通訊，請不要透過封存傳送 C++ 物件。 除非伺服器是 MFC 應用程式並且了解您想要傳送的物件種類，否則它將無法接收和還原序列化您的物件。 有關與非 MFC 應用程式通訊的相關材料,請參閱[Windows 套接字:位元組排序](../mfc/windows-sockets-byte-ordering.md)。

## <a name="the-csocket-programming-model"></a><a name="_core_the_csocket_programming_model"></a>CSocket 程式設計模型

使用 `CSocket` 物件包含了建立數個 MFC 類別物件，並讓這些物件彼此相關聯。 在下面的一般程序中，每一個步驟都是由伺服器通訊端與用戶端通訊端所進行，除了步驟 3，該步驟中的每種通訊端類型需要一個不同的動作。

> [!TIP]
> 在執行階段中，伺服器應用程式通常會先啟動並準備好，然後在用戶端應用程式尋找連接時「接聽」。 如果用戶端嘗試連接時伺服器尚未準備好，通常會需要使用者應用程式嘗試再次連接。

#### <a name="to-set-up-communication-between-a-server-socket-and-a-client-socket"></a>設定伺服器通訊端與用戶端通訊端之間的通訊

1. 構造[CSocket](../mfc/reference/csocket-class.md)物件。

1. 使用 物件創建基礎**SOCKET**句柄。

   對於`CSocket`用戶端物件,通常應使用預設參數[來創建](../mfc/reference/casyncsocket-class.md#create),除非您需要數據報套接字。 對於`CSocket`伺服器物件,必須在調用中`Create`指定埠。

    > [!NOTE]
    >  `CArchive` 無法搭配資料包通訊端使用。 如果您要對資料包通訊端使用 `CSocket`，則必須使用類別，就像使用 `CAsyncSocket` 一樣，也就是沒有封存。 由於資料包並不可靠 (不保證會達到，而且可能會重複或未依照順序)，因此它們無法透過封存與序列化相容。 您會希望序列化作業能夠確實依序順利完成。 如果您嘗試對資料包使用 `CSocket` 搭配 `CArchive` 物件，MFC 判斷提示就會失敗。

1. 如果套接字是用戶端,請致電[CAsyncSocket::連接](../mfc/reference/casyncsocket-class.md#connect)以將套接字物件連接到伺服器套接字。

     -或-

   如果套接字是伺服器,請致電[CAsyncSocket::偵聽](../mfc/reference/casyncsocket-class.md#listen)開始偵聽來自用戶端的連接嘗試。 收到連接請求后,請致電[CAsyncSocket::接受](../mfc/reference/casyncsocket-class.md#accept),接受它。

    > [!NOTE]
    >  成員`Accept`函數以引用新的`CSocket`空 物件作為其參數。 在調用`Accept`之前,必須構造此物件。 如果這個通訊端物件超出範圍，連接就會關閉。 不要調用`Create`此新套接字物件。

1. 建立[CSocketFile](../mfc/reference/csocketfile-class.md)物件,`CSocket`將物件與其關聯。

1. 創建用於載入(接收)或存儲(發送)資料的[CArchive](../mfc/reference/carchive-class.md)物件。 封存會與 `CSocketFile` 物件相關聯。

   務必記住，`CArchive` 無法與資料包通訊端搭配使用。

1. 請使用 `CArchive` 物件在用戶端和伺服器通訊端之間傳遞資料。

   請記住，一個特定 `CArchive` 物件只會朝某一方向移動資料：載入 (接收) 或儲存 (傳送)。 在某些情況下，您會使用兩個 `CArchive` 物件：一個用於傳送資料，另一個用於接收認可。

   在接受連接併設定封存之後，您就可以執行像是驗證密碼這類工作。

1. 終結封存、通訊端檔案和通訊端物件。

    > [!NOTE]
    >  `CArchive` 類別明確提供了 `IsBufferEmpty` 成員函式搭配 `CSocket` 類別使用。 例如，如果緩衝區包含多個資料訊息，您就需要執行迴圈，直到所有訊息都已讀且緩衝區已清除。 否則，告知您有資料要接收的下一個通知可能會無限期延遲。 使用 `IsBufferEmpty` 可確保擷取所有資料。

文章[Windows 套接字:操作序列](../mfc/windows-sockets-sequence-of-operations.md)通過範例代碼說明了此過程的兩個方面。

如需詳細資訊，請參閱

- [Windows Sockets：資料流通訊端](../mfc/windows-sockets-stream-sockets.md)

- [Windows Sockets：資料通訊端](../mfc/windows-sockets-datagram-sockets.md)

## <a name="see-also"></a>另請參閱

[MFC 中的 Windows Sockets](../mfc/windows-sockets-in-mfc.md)<br/>
[Socket::建立](../mfc/reference/csocket-class.md#create)
