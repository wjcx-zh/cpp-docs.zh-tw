---
title: "Windows Sockets： 連接埠和通訊端位址 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- ports [MFC], definition
- Windows Sockets [MFC], ports
- Windows Sockets [MFC], addresses
- ports [MFC]
- addresses [MFC], socket
- sockets [MFC], addresses
- sockets [MFC], ports
ms.assetid: e050261a-9285-4f31-a1c5-6c8033af5b4a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0c7b2e15761815b75ba8001ad4eb5a5c276f5056
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="windows-sockets-ports-and-socket-addresses"></a>Windows Sockets：連接埠和通訊端位址
本文說明的詞彙 「 連接埠 」 和 「 位址 」 做為與 Windows 通訊端搭配使用。  
  
##  <a name="_core_port"></a>連接埠  
 連接埠識別一項服務可以提供唯一的處理序。 在出現的內容中，連接埠是支援 Windows 通訊端的應用程式相關聯。 做法是可唯一識別每個 Windows 通訊端應用程式，因此您可以有多個機器上同時執行的 Windows 通訊端應用程式。  
  
 特定連接埠被保留給通用的服務，例如 FTP。 您應該避免使用這些連接埠，除非您提供此種服務。 Windows Sockets 規格詳細說明這些保留的連接埠。 WINSOCK 檔案。H 也會列出它們。  
  
 若要讓 Windows 通訊端 DLL，讓您選取可用的連接埠，請傳遞 0 做為連接埠值。 MFC 選取連接埠大於 1024 的十進位值。 您可以擷取連接埠選取的值，MFC 藉由呼叫[CAsyncSocket::GetSockName](../mfc/reference/casyncsocket-class.md#getsockname)成員函式。  
  
##  <a name="_core_socket_address"></a>通訊端位址  
 每個通訊端物件都與網路上的網際網路通訊協定 (IP) 位址。 位址通常是電腦名稱，例如"ftp.microsoft.com"或小數點的數字，例如"128.56.22.8"。  
  
 當您搜尋建立通訊端時，通常不需要指定您自己的位址。  
  
> [!NOTE]
>  它可能是您的電腦具有多張網路卡 （或您的應用程式可能會往後執行這類的機器上），每個都代表不同的網路。 如果是這樣，您可能需要授與指定之通訊端將會使用哪些網路卡的位址。 這是進階的使用方式和可能的可攜性問題。  
  
 如需詳細資訊，請參閱:  
  
-   [Windows Sockets：使用類別 CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)  
  
-   [Windows Sockets：搭配使用通訊端與封存](../mfc/windows-sockets-using-sockets-with-archives.md)  
  
-   [Windows Sockets：如何搭配使用通訊端與封存](../mfc/windows-sockets-how-sockets-with-archives-work.md)  
  
-   [Windows Sockets：資料流通訊端](../mfc/windows-sockets-stream-sockets.md)  
  
-   [Windows Sockets：資料通訊端](../mfc/windows-sockets-datagram-sockets.md)  
  
## <a name="see-also"></a>請參閱  
 [MFC 中的 Windows Sockets](../mfc/windows-sockets-in-mfc.md)

