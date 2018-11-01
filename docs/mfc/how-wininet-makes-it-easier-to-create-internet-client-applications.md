---
title: WinInet 如何讓您更輕鬆地建立網際網路用戶端應用程式
ms.date: 11/04/2016
helpviewer_keywords:
- Windows Sockets [MFC], vs. WinInet
- WinInet classes [MFC], vs. WinSock
- WinInet classes [MFC], Internet client applications
ms.assetid: dc0f9f47-3184-4e7a-8074-2c63e0359885
ms.openlocfilehash: 2bca338aa2a1b18e8c9ab41a887678767cf6c8c6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50636851"
---
# <a name="how-wininet-makes-it-easier-to-create-internet-client-applications"></a>WinInet 如何讓您更輕鬆地建立網際網路用戶端應用程式

Win32 網際網路擴充功能或 WinInet，提供一般的網際網路通訊協定，包括 gopher、 FTP 和 HTTP 存取。 使用 WinInet，您可以撰寫網際網路用戶端應用程式在更高的層級的程式設計，而不必應付 WinSock、 TCP/IP 或特定的網際網路通訊協定的詳細資料。 WinInet 會提供所有的三種通訊協定，使用熟悉的 Win32 API 介面中的一組一致的函式。 這種一致性最小化程式碼變更，您需要進行變更 （例如，從 FTP 變更為 HTTP) 的基礎通訊協定。

Visual c + + 提供兩種方法讓您使用 WinInet。 您可以直接呼叫 Win32 網際網路函式 （請參閱 OLE 文件，如需詳細資訊的 Windows SDK 中） 或您可以使用透過 WinInet [MFC WinInet 類別](../mfc/mfc-classes-for-creating-internet-client-applications.md)。

**您可以使用 WinInet 來：**

- 下載 HTML 頁面。

   HTTP 是用來從伺服器傳送 HTML 網頁，用戶端瀏覽器至通訊協定。

- FTP 要求傳送到上傳或下載檔案，或是取得目錄清單。

   典型的要求是匿名的登入以下載的檔案。

- 使用 gopher 的功能表系統來存取網際網路上的資源。

   功能表項目可以是數種類型，包括其他功能表、 索引的資料庫，您可以搜尋、 新聞群組或檔案。

所有的三種通訊協定，您可以建立連線、 對伺服器提出要求並關閉連線。

**MFC WinInet 類別可讓您輕鬆：**

- 做為從硬碟讀取檔案輕鬆地從 HTTP、 FTP 和 gopher 伺服器讀取資訊。

- 使用 HTTP、 FTP 和 gopher 通訊協定，不需要直接向 WinSock 或 TCP/IP 的程式設計。

   使用 Win32 網際網路函式的開發人員不需要熟悉 TCP/IP 或 Windows 通訊端。 您可以仍然在通訊端層級中，使用程式設計 WinSock 和 TCP/IP 通訊協定直接，但更容易在網際網路上使用 MFC WinInet 類別來存取 HTTP、 FTP 和 gopher 通訊協定。 許多常見的作業，開發人員不需要知道他們所使用的特定通訊協定的詳細資料。

可以為網際網路上的其他電腦的用戶端電腦所執行的許多作業可能需要很長的時間。 這些作業的速度通常會受到您的網路連線速度，但它們可能也會受到其他網路流量，以及作業的複雜性。 比方說，連接到遠端 FTP 伺服器，需要您的電腦第一次查閱來尋找其位址該伺服器的名稱。 您的應用程式則會嘗試連接到位於該位址的伺服器。 一旦開啟連接時，您的電腦和遠端伺服器會起始交談與檔案傳輸通訊協定才能實際使用連接來擷取檔案。

## <a name="see-also"></a>另請參閱

[Win32 網際網路延伸模組 (WinInet)](../mfc/win32-internet-extensions-wininet.md)<br/>
[MFC 如何讓您更輕鬆地建立網際網路用戶端應用程式](../mfc/how-mfc-makes-it-easier-to-create-internet-client-applications.md)

