---
title: Windows Sockets:背景
ms.date: 11/04/2016
helpviewer_keywords:
- record-oriented data [MFC]
- e-mail [MFC]
- Internet Protocol Suite
- mail [MFC]
- communications [MFC], domain
- Windows Sockets [MFC], stream sockets
- mail [MFC], programming for
- sockets [MFC], stream sockets
- datagram sockets [MFC]
- SOCKET handle
- data types [MFC], socket
- e-mail [MFC], programming for
- X Window servers
- sequenced data flow
- stream sockets [MFC]
ms.assetid: f60d4ed2-bf23-4a0e-98d2-fee77e8473dd
ms.openlocfilehash: 6ab866609d0b75aaf9d06a01c204433d80e7e3d8
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57274917"
---
# <a name="windows-sockets-background"></a>Windows Sockets:背景

這篇文章說明的性質與用途的 Windows 通訊端。 本文也：

- [定義詞彙 「 通訊端"](#_core_definition_of_a_socket)。

- [描述通訊端控制代碼的資料型別](#_core_the_socket_data_type)。

- [描述使用的通訊端](#_core_uses_for_sockets)。

Windows Sockets 規格會定義 Microsoft Windows 的二進位相容網路程式設計介面。 Windows 通訊端會根據 UNIX 通訊端中實作 Berkeley Software Distribution (BSD 發行 4.3) 從加利福尼亞大學柏克萊在。 此規格包含 BSD 樣式通訊端常式和 Windows 的特定延伸模組。 使用 Windows 通訊端，可讓您能夠透過 Windows Sockets API 符合任何網路通訊的應用程式。 在 Win32，Windows Sockets 提供執行緒安全。

許多網路軟體廠商在包括傳輸控制通訊協定/網際網路通訊協定 (TCP/IP)，Xerox 網路系統 (XNS) Digital Equipment Corporation 的 DECNet 通訊協定，Novell Corporation 網際網路的網路通訊協定支援 Windows 通訊端封包交換/循序封包交換 (IPX/SPX)，以及其他。 雖然存在的 Windows Sockets 規格定義 TCP/IP 通訊端抽象概念，任何網路通訊協定也會遵守 Windows 通訊端提供自己的版本會實作 Windows 通訊端的動態連結程式庫 (DLL)。 以 Windows 通訊端的商業應用程式的範例包括 X Windows 伺服器、 終端機模擬器，以及電子郵件系統。

> [!NOTE]
>  Windows 通訊端的目的是抽離基礎網路，讓您不一定要了解該網路，因此您的應用程式可以在任何支援通訊端的網路上執行。 因此，這份文件不討論網路通訊協定的詳細的資料。

Microsoft Foundation Class 程式庫 (MFC) 提供兩個類別，以支援使用 Windows Sockets API 進行程式設計。 其中一個類別， `CSocket`，提供高層級的抽象概念，來簡化您的網路通訊程式設計。

Windows Sockets 規格後，Windows Sockets:網路運算下 Microsoft Windows，現在是在版本 1.1 中，開啟介面由個人及公司 TCP/IP 社群的一大群開發為一種開放式網路標準，而且可供使用免費。 通訊端目前程式模型支援一個 「 通訊網域 」，並透過網際網路通訊協定套件。 使用 Windows SDK 中的規格。

> [!TIP]
>  通訊端會使用網際網路通訊協定套件，因為它們是慣用的路由支援 「 information highway。 」 的網際網路通訊的應用程式

##  <a name="_core_definition_of_a_socket"></a> 通訊端的定義

通訊端是通訊的端點，透過 Windows Sockets 應用程式傳送或接收資料封包在網路上的物件。 通訊端類型，且執行中處理序，與相關聯，它可能會有名稱。 目前，通訊端通常會交換只能與相同 「 通訊網域中，「 使用網際網路通訊協定套件的其他通訊端的資料。

這兩種通訊端是雙向;它們是以同時告知兩個方向的資料流 （全雙工）。

兩個通訊端類型可用：

- Stream 通訊端

   Stream 通訊端提供不含記錄界限的資料流程： 位元組資料流。 資料流可保證傳遞和正確排序且不會重複。

- 資料包通訊端

   資料包通訊端支援記錄導向資料流不保證傳遞，且可能不會依傳送，或不重複。

「 循序 」 表示封包，傳遞傳送的順序。 「 不重複 」 表示一次取得一個特定封包。

> [!NOTE]
>  在某些網路通訊協定，例如 XNS，資料流可以是導向，為資料流的記錄，而不是為位元組資料流的記錄。 不過，較常見的 TCP/IP 通訊協定，在資料流是位元組資料流。 Windows Sockets 提供一個基礎通訊協定無關的抽象層。

如需這些類型的詳細資訊，以及哪種通訊端在哪些情況下使用，請參閱[Windows Sockets:Stream 通訊端](../mfc/windows-sockets-stream-sockets.md)和[Windows Sockets:資料包通訊端](../mfc/windows-sockets-datagram-sockets.md)。

##  <a name="_core_the_socket_data_type"></a> 通訊端的資料類型

每個 MFC 通訊端物件會封裝 Windows 通訊端物件的控制代碼。 這個控制代碼的資料類型是**通訊端**。 A**通訊端**控制代碼是類似於`HWND`視窗。 MFC 通訊端類別會提供封裝的控制代碼上的作業。

**通訊端**Windows SDK 中的詳細說明資料類型。 在 Windows 通訊端，請參閱 「 通訊端的資料類型和錯誤值 」。

##  <a name="_core_uses_for_sockets"></a> 使用的通訊端

通訊端會在至少三個通訊內容中非常有用：

- 用戶端/伺服器模型。

- 端對端案例，例如傳訊應用程式。

- 讓接收解譯訊息做為函式呼叫的應用程式進行遠端程序呼叫 (RPC)。

> [!TIP]
>  使用 MFC 通訊端的理想案例是當您撰寫的通訊兩端： 在兩端使用 MFC。 如需有關本主題中，包括如何管理案例，您要與非 MFC 應用程式通訊時，請參閱[Windows Sockets:位元組順序](../mfc/windows-sockets-byte-ordering.md)。

如需詳細資訊，請參閱 Windows Sockets 規格： **ntohs**， **ntohl**， **htons**， **htonl**。 此外，請參閱下列主題：

- [Windows Sockets:搭配使用通訊端與封存](../mfc/windows-sockets-using-sockets-with-archives.md)

- [Windows Sockets:使用封存的通訊端範例](../mfc/windows-sockets-example-of-sockets-using-archives.md)

- [Windows Sockets:使用類別 CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)

## <a name="see-also"></a>另請參閱

[MFC 中的 Windows Sockets](../mfc/windows-sockets-in-mfc.md)
