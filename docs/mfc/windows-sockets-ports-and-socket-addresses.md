---
title: Windows Sockets：連接埠和通訊端位址
ms.date: 11/04/2016
helpviewer_keywords:
- ports [MFC], definition
- Windows Sockets [MFC], ports
- Windows Sockets [MFC], addresses
- ports [MFC]
- addresses [MFC], socket
- sockets [MFC], addresses
- sockets [MFC], ports
ms.assetid: e050261a-9285-4f31-a1c5-6c8033af5b4a
ms.openlocfilehash: 791bf07c927e80e65e0fda79fae8a50235bc2def
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371038"
---
# <a name="windows-sockets-ports-and-socket-addresses"></a>Windows Sockets：連接埠和通訊端位址

本文介紹了與 Windows 套接字一起使用的術語"埠"和"位址"。

## <a name="port"></a><a name="_core_port"></a>港口

埠標識可為其提供服務的唯一進程。 在本上下文中,埠與支援 Windows 套接字的應用程式相關聯。 其理念是唯一標識每個 Windows 套接字應用程式,以便可以同時在電腦上運行多個 Windows 套接字應用程式。

某些埠保留用於公共服務,如 FTP。 除非提供此類服務,否則應避免使用這些埠。 Windows 套接字規範詳細介紹了這些保留埠。 檔 WINSOCK。H 還列出了它們。

要讓 Windows 套接字 DLL 為您選擇可用的連接埠,請傳遞 0 作為連接埠值。 MFC 選擇大於 1,024 小數的埠值。 您可以通過調用[CAsyncSocket::getSockName](../mfc/reference/casyncsocket-class.md#getsockname)成員函數來檢索 MFC 選擇的埠值。

## <a name="socket-address"></a><a name="_core_socket_address"></a>Socket 位址

每個套接字物件都與網路上的 Internet 協定 (IP) 地址相關聯。 通常,位址是計算機名稱,如"ftp.microsoft.com"或虛線數位,如"128.56.22.8"。

當您尋求創建套接字時,通常不需要指定自己的位址。

> [!NOTE]
> 您的電腦可能有多個網卡(或者您的應用程式可能有一天在這樣的計算機上運行),每個網卡代表不同的網路。 如果是這樣,您可能需要提供一個位址來指定套接字將使用的網卡。 這肯定是一個高級用法和可能的可移植性問題。

如需詳細資訊，請參閱

- [Windows Sockets：使用類別 CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)

- [Windows Sockets：搭配使用通訊端與封存](../mfc/windows-sockets-using-sockets-with-archives.md)

- [Windows Sockets：如何搭配使用通訊端與封存](../mfc/windows-sockets-how-sockets-with-archives-work.md)

- [Windows Sockets：資料流通訊端](../mfc/windows-sockets-stream-sockets.md)

- [Windows Sockets：資料通訊端](../mfc/windows-sockets-datagram-sockets.md)

## <a name="see-also"></a>另請參閱

[MFC 中的 Windows Sockets](../mfc/windows-sockets-in-mfc.md)
