---
title: Windows Sockets： 連接埠和通訊端位址 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7f97bfa42e379f0806eb85e3f030465b2a181d01
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46379657"
---
# <a name="windows-sockets-ports-and-socket-addresses"></a>Windows Sockets：連接埠和通訊端位址

這篇文章說明條款"port"和"address"做為與 Windows 通訊端搭配使用。

##  <a name="_core_port"></a> 連接埠

連接埠識別唯一處理程序可以提供服務。 在出現的內容中，連接埠是支援 Windows 通訊端的應用程式相關聯。 其概念是可唯一識別每個 Windows Sockets 應用程式，因此您可以有多個同時執行的電腦上的 Windows Sockets 應用程式。

特定連接埠被保留給通用的服務，例如 FTP。 您應該避免使用這些連接埠，除非您要提供這種服務。 Windows Sockets 規格會詳細說明這些保留的連接埠。 WINSOCK 檔案。H 也會列出它們。

若要讓 Windows 通訊端 DLL，讓您選取可用的連接埠，請將 0 傳遞做為連接埠值。 MFC 會選取大於 1024 的十進位的連接埠。 您可以擷取連接埠選取的值，MFC 藉由呼叫[CAsyncSocket::GetSockName](../mfc/reference/casyncsocket-class.md#getsockname)成員函式。

##  <a name="_core_socket_address"></a> 通訊端位址

每個通訊端物件是在網路上的網際網路通訊協定 (IP) 位址相關聯。 一般而言，位址是電腦名稱，例如 「 ftp.microsoft.com"或小數點的數字，例如"128.56.22.8 」。

當您試圖建立通訊端時，通常不需要指定您自己的位址。

> [!NOTE]
>  它可能是您的電腦具有多張網路卡 （或這類電腦可能會假以時日執行應用程式），每個都代表不同的網路。 如果是這樣，您可能需要授與指定的通訊端會使用的網路卡的位址。 這是一定是進階的使用方式和可能的可攜性問題。

如需詳細資訊，請參閱:

- [Windows Sockets：使用類別 CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)

- [Windows Sockets：搭配使用通訊端與封存](../mfc/windows-sockets-using-sockets-with-archives.md)

- [Windows Sockets：如何搭配使用通訊端與封存](../mfc/windows-sockets-how-sockets-with-archives-work.md)

- [Windows Sockets：資料流通訊端](../mfc/windows-sockets-stream-sockets.md)

- [Windows Sockets：資料通訊端](../mfc/windows-sockets-datagram-sockets.md)

## <a name="see-also"></a>另請參閱

[MFC 中的 Windows Sockets](../mfc/windows-sockets-in-mfc.md)

