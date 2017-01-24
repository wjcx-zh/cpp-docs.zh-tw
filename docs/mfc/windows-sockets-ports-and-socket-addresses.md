---
title: "Windows Sockets：連接埠和通訊端位址 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
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
  - "位址 [C++], 通訊端"
  - "連接埠 [C++]"
  - "連接埠 [C++], 定義"
  - "通訊端 [C++], 位址"
  - "通訊端 [C++], 通訊埠"
  - "Windows Sockets [C++], 位址"
  - "Windows Sockets [C++], 通訊埠"
ms.assetid: e050261a-9285-4f31-a1c5-6c8033af5b4a
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Windows Sockets：連接埠和通訊端位址
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文所述詞移植」，而「請解決」如搭配 Windows Sockets。  
  
##  <a name="_core_port"></a> 連接埠  
 連接埠識別服務可以提供唯一的處理序。  在目前內容中，連接埠與支援 Windows Sockets 的應用程式。  這個概念是唯一識別每個 Windows Sockets 應用程式，因此您可以有多個同時在電腦的 Windows 通訊端應用程式。  
  
 某些通訊埠為通用服務是保留字，例如 FTP。  除非您提供一種服務，您應該避免使用這些通訊埠。  Windows Sockets 規格詳述這些保留通訊埠。  檔案 WINSOCK.H 也列出。  
  
 若要讓 Windows DLL 為您選取可用的通訊埠的通訊端，您可以指定 0 做為通訊埠值。  MFC 選取的通訊埠值大於 1,024 \(十進位\)。  您可以擷取 MFC 藉由呼叫 [CAsyncSocket::GetSockName](../Topic/CAsyncSocket::GetSockName.md) 成員函式選取的通訊埠值。  
  
##  <a name="_core_socket_address"></a> 通訊端位址。  
 每個通訊端物件與網路上的 Internet Protocol \(IP\) 位址。  通常，這個位址是電腦名稱，例如「ftp.microsoft.com」或是點狀的數字，例如「128.56.22.8」。  
  
 當您搜尋要求建立通訊端時，通常不需要指定自己的位址。  
  
> [!NOTE]
>  很可能您的電腦上有多個網路介面卡 \(或您的應用程式在這類電腦可能某天執行\)，代表不同的網路中的每一個。  如果是這樣，您可能需要將位址指定哪個網路介面卡通訊端將會使用。  確定這是進階的使用方式和一個可能的問題。  
  
 如需詳細資訊，請參閱：  
  
-   [Windows Sockets：使用類別 CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)  
  
-   [Windows Sockets：搭配使用通訊端與封存](../mfc/windows-sockets-using-sockets-with-archives.md)  
  
-   [Windows Sockets:有封存的通訊端的運作方式。](../mfc/windows-sockets-how-sockets-with-archives-work.md)  
  
-   [Windows Sockets:資料流通訊端](../mfc/windows-sockets-stream-sockets.md)  
  
-   [Windows Sockets:資料包通訊端](../mfc/windows-sockets-datagram-sockets.md)  
  
## 請參閱  
 [MFC 中的 Windows Sockets](../mfc/windows-sockets-in-mfc.md)