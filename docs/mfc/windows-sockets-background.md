---
title: Windows Sockets： 背景 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fda86bbbeb49bcb253348ed02abef4fb8d4cff9c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33384933"
---
# <a name="windows-sockets-background"></a>Windows Sockets：背景
本文說明的本質與用途的 Windows 通訊端。 發行項也：  
  
-   [定義詞彙 「 通訊端"](#_core_definition_of_a_socket)。  
  
-   [描述的通訊端控制代碼的資料類型](#_core_the_socket_data_type)。  
  
-   [說明使用的通訊端](#_core_uses_for_sockets)。  
  
 Windows Sockets 規格會定義 Microsoft Windows 的二進位檔相容的網路程式設計介面。 Windows Sockets 會根據 UNIX 通訊端實作在 Berkeley Software Distribution (BSD，釋放 4.3) 從加利福尼亞大學柏克萊在。 此規格包含 BSD 樣式通訊端常式和 Windows 特定的擴充功能。 使用 Windows 通訊端，可讓您能夠透過 Windows Sockets API 符合任何網路通訊的應用程式。 在 Win32 中，Windows Sockets 提供執行緒安全。  
  
 許多網路軟體廠商在包括傳輸控制通訊協定/網際網路通訊協定 (TCP/IP)，Xerox 網路系統 (XNS) 數位設備公司的 DECNet 通訊協定、 Novell 公司網際網路的網路通訊協定支援 Windows Sockets封包交換/循序封包交換 (IPX/SPX) 和其他人。 雖然存在的 Windows Sockets 規格會定義 TCP/IP 通訊端抽象概念，任何網路通訊協定可以遵守 Windows Sockets 藉由提供自己的版本會實作 Windows 通訊端的動態連結程式庫 (DLL)。 使用 Windows Sockets 撰寫的商業應用程式的範例包括 X Windows 伺服器、 終端機模擬器，以及電子郵件系統。  
  
> [!NOTE]
>  Windows Sockets 的目的是提取出基礎網路，讓您不一定要了解該網路，因此您的應用程式可以在任何支援通訊端的網路上執行。 因此，這份文件不討論網路通訊協定的詳細的資料。  
  
 Microsoft Foundation 類別庫 (MFC) 支援使用 Windows Sockets API 進行程式設計，藉由提供兩個類別。 其中一個類別， `CSocket`，提供高階的抽象概念，以簡化您的網路通訊程式設計。  
  
 Windows Sockets 規格，Windows Sockets： 網路運算下 Microsoft Windows 中，現在是在 1.1 版中開啟的介面由大型個人及公司 TCP/IP 社群中的群組開發為開放的網路標準，且自由可供使用。 通訊端目前程式設計模型支援一個 「 通訊網域 」，請使用網際網路通訊協定組合。 使用 Windows SDK 中的規格。  
  
> [!TIP]
>  由於通訊端使用網際網路通訊協定組合，它們是支援 「 資訊高速公路。 」 上的網際網路通訊的應用程式的慣用的路由  
  
##  <a name="_core_definition_of_a_socket"></a> 通訊端的定義  
 通訊端是通訊之端點，透過此 Windows 通訊端應用程式傳送或接收的資料封包在網路上的物件。 通訊端具有型別，而且與執行的處理序相關聯，它可能會有名稱。 目前，通訊端通常會交換資料只能搭配其他通訊端在相同 」 通訊網域中，「 使用網際網路通訊協定組合。  
  
 這兩種通訊端會雙向;它們是可以同時傳送兩個方向的資料流 （全雙工）。  
  
 通訊端可用兩種類型：  
  
-   資料流通訊端  
  
     資料流通訊端提供不含記錄界限的資料流： 位元組資料流。 資料流保證傳遞，並且將正確排序且不會重複。  
  
-   資料包通訊端  
  
     資料包通訊端支援記錄導向資料流不保證傳遞，且可能不會依傳送或不重複。  
  
 「 排序 」 表示封包傳遞傳送的順序。 「 不重複的 」 表示一次取得特定的封包。  
  
> [!NOTE]
>  在某些網路通訊協定，例如 XNS，資料流可以是記錄導向，為記錄的資料流，而不是資料流的位元組。 不過，更常見的 TCP/IP 通訊協定，在資料流是位元組資料流。 Windows Sockets 提供一個獨立的基礎通訊協定的抽象層。  
  
 如需有關這些類型資訊和哪一種通訊端在哪些情況下使用，請參閱[Windows Sockets： 資料流通訊端](../mfc/windows-sockets-stream-sockets.md)和[Windows Sockets： 資料包通訊端](../mfc/windows-sockets-datagram-sockets.md)。  
  
##  <a name="_core_the_socket_data_type"></a> 通訊端的資料類型  
 每個 MFC 通訊端物件會封裝 Windows 通訊端物件的控制代碼。 這個控制代碼的資料類型是**通訊端**。 A**通訊端**控點是類似於`HWND`視窗。 MFC 通訊端類別會提供封裝的控制代碼上的作業。  
  
 **通訊端**資料類型中有詳細說明 Windows SDK 中。 Windows Sockets 下，請參閱 「 通訊端的資料類型和錯誤值 」。  
  
##  <a name="_core_uses_for_sockets"></a> 使用的通訊端  
 通訊端已至少三個通訊的內容中非常有用：  
  
-   用戶端/伺服器模型。  
  
-   端對端案例，例如訊息應用程式。  
  
-   讓接收解譯訊息做為函式呼叫的應用程式進行遠端程序呼叫 (RPC)。  
  
> [!TIP]
>  您要撰寫這兩個端點的通訊時，理想的情況下，使用 MFC 通訊端： 在兩端使用 MFC。 如需有關本主題中，包括如何管理案例，當您正在通訊非 MFC 應用程式，請參閱[Windows Sockets： 位元組順序](../mfc/windows-sockets-byte-ordering.md)。  
  
 如需詳細資訊，請參閱 Windows Sockets 規格： **ntohs**， **ntohl**， **htons**， **htonl**。 另請參閱下列主題：  
  
-   [Windows Sockets：搭配使用通訊端與封存](../mfc/windows-sockets-using-sockets-with-archives.md)  
  
-   [Windows Sockets：使用封存的通訊端範例](../mfc/windows-sockets-example-of-sockets-using-archives.md)  
  
-   [Windows Sockets：使用類別 CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)  
  
## <a name="see-also"></a>另請參閱  
 [MFC 中的 Windows Sockets](../mfc/windows-sockets-in-mfc.md)

