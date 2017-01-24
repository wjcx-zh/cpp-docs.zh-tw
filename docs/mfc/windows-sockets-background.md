---
title: "Windows Sockets：背景 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "通訊 [C++], 網域"
  - "資料類型 [C++], 通訊端"
  - "資料包通訊端 [C++]"
  - "電子郵件 [C++]"
  - "電子郵件 [C++], 的程式設計"
  - "網際網路通訊協定套件"
  - "郵件 [C++]"
  - "郵件 [C++], 的程式設計"
  - "資料錄導向的資料 [C++]"
  - "循序資料流程"
  - "SOCKET 控制代碼"
  - "通訊端 [C++], 資料流通訊端"
  - "資料流通訊端 [C++]"
  - "Windows Sockets [C++], 資料流通訊端"
  - "X Window 伺服器"
ms.assetid: f60d4ed2-bf23-4a0e-98d2-fee77e8473dd
caps.latest.revision: 12
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Windows Sockets：背景
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文說明 Windows Sockets 的本質與目的。  也文件說明：  
  
-   [定義一詞「通訊端」](#_core_definition_of_a_socket)。  
  
-   [描述通訊端控制代碼資料型別](#_core_the_socket_data_type)。  
  
-   [描述通訊端的用途](#_core_uses_for_sockets)。  
  
 Windows Sockets 規格定義 Microsoft Windows 的二進位相容網路程式設計介面。  Windows Sockets 根據來自柏克萊的加州大學的柏克萊軟體配置 \(BSD， 4.3 版\) 的 UNIX 通訊端實作。  這個規格中包含 Windows 的兩個 BSD 通訊端常式和擴充。  使用 Windows Sockets 允許您的應用程式依照 Windows Sockets API 的所有網路通訊。  就 Win32 而言， Windows Sockets 提供執行緒安全。  
  
 許多網路軟體廠商支援 Windows Sockets 在網路通訊協定，包括傳輸控制通訊協定\/網際網路通訊協定 \(TCP\/IP\)，Xerox 網路系統 \(XNS\)， DEC 電腦公司的 DECnet 網路通訊協定、Novell Corporation 的網際網路封包交換\/序列包裝交換 \(IPX\/SPX 通訊協定\) 等。  雖然現存的 Windows Sockets 規格定義 TCP\/IP 通訊端抽象，即可以符合藉由提供其動態連結程式庫 \(DLL\) 的版本實作 Windows Sockets 的所有網路通訊協定。  商用應用軟體的範例會使用 Windows Sockets 由 X Windows Server、終端模擬器和電子郵件系統。  
  
> [!NOTE]
>  Windows Sockets 的目的是要擷取基礎網路，讓您不需要為了平台學習該網路，因此您的應用程式在支援通訊端的所有網路上執行。  因此，本文件不探討網路通訊協定的詳細資料。  
  
 Microsoft 基礎類別程式庫 \(MFC\) 支援 Windows Sockets API 提供的兩個類別。  其中一個類別 `CSocket`，提供高階抽象簡化您的網路通訊程序。  
  
 Windows Sockets 規格， Windows Sockets：在 Microsoft Windows 中網路計算之開啟介面，現在為版本 1.1 ，已經為個人和公司的大量 TCP\/IP 社群開啟網路標準且是可供免費使用。  通訊端程式設計模型目前支援的「通訊網域」且使用網際網路通訊協定組。  這個規格可用於 [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)]。  
  
> [!TIP]
>  由於通訊端使用網際網路通訊協定組，它們是支援「資訊快速公路」的網際網路通訊協定的應用程式的進階路徑。  
  
##  <a name="_core_definition_of_a_socket"></a> 通訊端的定義  
 通訊端是通訊端點— Windows Sockets 應用程式跨網路傳送或接收資料的物件。  通訊端有一個型別與執行中的處理序，因此它可能有名稱。  目前，一般來說通訊端只與其它在相同「通訊網域的其他通訊端」，使用網際網路通訊協定組件集的通訊端交換資料。  
  
 兩種通訊端都是雙向的;它們是兩個方向可以同時傳送的資料流 \(全雙工\)。  
  
 兩個可用的通訊端類型:  
  
-   資料流通訊端  
  
     資料流通訊端提供未記錄界限的資料流:位元組資料流。  資料流被保證送達以及依序且無副本的傳輸。  
  
-   資料包通訊端  
  
     資料包通訊端支援記錄導向的資料流，不保證送達且不一定依序或無副本的傳輸。  
  
 「依序」表示封包按傳送的順序傳遞。「無副本的」 是指您一次只能取得一個特定封包。  
  
> [!NOTE]
>  在某些網路通訊協定下，例如 XNS，資料流可以是做為資料列導向的，為資料列資料流而不是位元組資料流。  不過，在較常見的 TCP\/IP 通訊協定下，資料流是位元組資料流。  Windows Sockets 提供獨立於基礎通訊協定的抽象層。  
  
 如需這些類型以及通訊端於哪些情況使用的詳細資訊，請參閱 [Windows Sockets:資料流通訊端](../mfc/windows-sockets-stream-sockets.md) 和 [Windows Sockets:資料包通訊端](../mfc/windows-sockets-datagram-sockets.md)。  
  
##  <a name="_core_the_socket_data_type"></a> SOCKET 資料型別  
 每個 MFC 通訊端物件封裝一個 Windows Sockets 物件的檔案控制代碼。  這個控制代碼的資料型別是 **SOCKET**。  **SOCKET** 控制代碼是類似於視窗的 `HWND` 。  MFC 通訊端類別提供對封裝的控制代碼的操作。  
  
 **SOCKET** 資料型別在 [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)]中有詳細說明。  請在 Windows Sockets 下參閱「通訊端資料型別和錯誤值」。  
  
##  <a name="_core_uses_for_sockets"></a> 通訊端的用途  
 通訊端在三種通訊環境下是非常有用的:  
  
-   主從模型。  
  
-   點對點的案例，例如訊息應用程式。  
  
-   進行遠端程序呼叫 \(RPC\) 讓接收應用程式解譯訊息為函式呼叫。  
  
> [!TIP]
>  使用 MFC 通訊端的理想情況是當您在撰寫兩端通訊:在兩端使用 MFC。  如需本主題的詳細資訊，包括如何處理當您與非 MFC 應用程式進行通訊的案例，請參閱 [Windows Sockets:位元組順序](../mfc/windows-sockets-byte-ordering.md)。  
  
 如需詳細資訊，請參閱 Windows Sockets 規格: **ntohs**， **ntohl**， **htons**， **htonl**。  也請參閱下列主題：  
  
-   [Windows Sockets：搭配使用通訊端與封存](../mfc/windows-sockets-using-sockets-with-archives.md)  
  
-   [Windows Sockets：使用封存的通訊端範例](../mfc/windows-sockets-example-of-sockets-using-archives.md)  
  
-   [Windows Sockets：使用類別 CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)  
  
## 請參閱  
 [MFC 中的 Windows Sockets](../mfc/windows-sockets-in-mfc.md)