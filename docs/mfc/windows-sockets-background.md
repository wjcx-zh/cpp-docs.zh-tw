---
title: Windows Sockets：背景
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
ms.openlocfilehash: 1c4a6dc6740660d1097785578cdac355983cad18
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81360120"
---
# <a name="windows-sockets-background"></a>Windows Sockets：背景

本文介紹了 Windows 套接字的性質和用途。 本文還:

- [定義術語"套接字"。](#_core_definition_of_a_socket)

- [描述 SOCKET 片態的資料型態](#_core_the_socket_data_type)。

- [描述 socket 的用數](#_core_uses_for_sockets)。

Windows 套接字規範為 Microsoft Windows 定義了二進位兼容的網路程式設計介面。 Windows 套接字基於加州大學伯克利分校的「伯克利軟體分發」(BSD,版本 4.3)中的 UNIX 套接字實現。 該規格包括 BSD 樣式的套接字例程和特定於 Windows 的擴展。 使用 Windows 套接字允許應用程式跨任何符合 Windows 套接字 API 的網路進行通信。 在 Win32 上,Windows 插槽提供線程安全性。

許多網路軟體供應商根據網路協定支援 Windows 套接字,包括傳輸控制協定/互聯網協定 (TCP/IP)、Xerox 網路系統 (XNS)、數位設備公司的 DECNet 協定、Novell 公司的互聯網數據包交換/序列打包交換 (IPX/SPX) 等。 儘管當前 Windows 套接字規範定義了 TCP/IP 的套接字抽象,但任何網路協定都可以通過提供實現 Windows 套接字的動態連結庫 (DLL) 自己的版本來符合 Windows 套接字。 使用 Windows 套接字編寫的商業應用程式的範例包括 X Windows 伺服器、終端模擬器和電子郵件系統。

> [!NOTE]
> Windows 套接字的目的是抽象化基礎網路,這樣您就不必瞭解該網路,因此應用程式可以在支援套接字的任何網路上運行。 因此,本文檔不討論網路協定的詳細資訊。

Microsoft 基礎類庫 (MFC) 通過提供兩個類支援使用 Windows 套接字 API 進行程式設計。 其中一個類`CSocket`提供了高級抽象,以簡化網路通信程式設計。

Windows 套接字規範"Windows 套接字:微軟 Windows 下網路計算的開放介面"現已推出 1.1 版,由 TCP/IP 社區中的一大群個人和公司開發為開放網路標準,可免費使用。 套接字程式設計模型目前支援一個「通信域」,使用 Internet 協定套件。 該規範在 Windows SDK 中可用。

> [!TIP]
> 由於套接字使用 Internet 協定套件,因此它們是支援「資訊高速公路」上 Internet 通信的應用程式的首選路由。

## <a name="definition-of-a-socket"></a><a name="_core_definition_of_a_socket"></a>Socket 定義

套接字是通訊終結點, Windows 套接字應用程式透過網路發送或接收資料包的物件。 套接字具有類型,並且與正在運行的進程相關聯,並且可能具有名稱。 目前,套接字通常僅與同一"通信域"中的其他套接字交換數據,後者使用 Internet 協定套件。

這兩種套接字都是雙向的;它們是可同時雙向通信的數據流(全雙工)。

有兩種套接字型態可用:

- 資料流通訊端

   流套接字提供沒有記錄邊界的數據流:位元組流。 保證流被傳遞,並正確排序和未重複。

- 資料包通訊端

   Datagram 套接字支援不保證傳遞的面向記錄的數據流,並且可能無法按已發送或未重複的順序排序。

「排序」表示數據包按發送的順序傳遞。 "未重複"表示您只能獲取一次特定數據包。

> [!NOTE]
> 在某些網路協定(如 XNS )可以面向記錄,作為記錄流而不是位元組流。 但是,在更常見的 TCP / IP 協定是位元組流。 Windows 套接字提供獨立於基礎協定的抽象級別。

有關這些類型的以及要在哪些情況下使用哪種套接字的資訊,請參閱[Windows 套接字:串流套接字](../mfc/windows-sockets-stream-sockets.md)和[Windows 通訊排接字:Datagram 通訊通訊 。](../mfc/windows-sockets-datagram-sockets.md)

## <a name="the-socket-data-type"></a><a name="_core_the_socket_data_type"></a>SOCKET 資料類型

每個 MFC 套接字物件都封裝到 Windows 套接字物件的句柄。 這個句柄的資料型態是**SOCKET**。 **SOCKET**句柄類似於視窗的`HWND`。 MFC 套接字類提供對封裝句柄的操作。

在 Windows SDK 中詳細介紹了**SOCKET**數據類型。 請參閱 Windows 套接字下的「套接字數據類型和錯誤值」。

## <a name="uses-for-sockets"></a><a name="_core_uses_for_sockets"></a>用於通訊端

套接字至少在三個通信上下文中非常有用:

- 用戶端/伺服器模型。

- 對等方案,如消息傳遞應用程式。

- 通過讓接收應用程式將消息解釋為函數調用來進行遠端過程調用 (RPC)。

> [!TIP]
> 使用 MFC 套接字的理想情況是,當您寫入通信的兩端時:在兩端使用 MFC。 有關本主題的詳細資訊(包括如何在與非 MFC 應用程式通訊時如何管理案例),請參閱[Windows 套接字:位元組排序](../mfc/windows-sockets-byte-ordering.md)。

有關詳細資訊,請參閱 Windows 套接字規範:ntohs、ntohl、Htons、htonl 。 **ntohs** **ntohl** **htons** **htonl** 此外,請參閱以下主題:

- [Windows Sockets：搭配使用通訊端與封存](../mfc/windows-sockets-using-sockets-with-archives.md)

- [Windows Sockets：使用封存的通訊端範例](../mfc/windows-sockets-example-of-sockets-using-archives.md)

- [Windows Sockets：使用類別 CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)

## <a name="see-also"></a>另請參閱

[MFC 中的 Windows Sockets](../mfc/windows-sockets-in-mfc.md)
