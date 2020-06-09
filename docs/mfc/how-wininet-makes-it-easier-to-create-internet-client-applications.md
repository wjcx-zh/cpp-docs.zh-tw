---
title: WinInet 如何讓您更輕鬆地建立網際網路用戶端應用程式
ms.date: 11/04/2016
helpviewer_keywords:
- Windows Sockets [MFC], vs. WinInet
- WinInet classes [MFC], vs. WinSock
- WinInet classes [MFC], Internet client applications
ms.assetid: dc0f9f47-3184-4e7a-8074-2c63e0359885
ms.openlocfilehash: 54f63da7451dfef39a33e6b437be938cb1652326
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84624579"
---
# <a name="how-wininet-makes-it-easier-to-create-internet-client-applications"></a>WinInet 如何讓您更輕鬆地建立網際網路用戶端應用程式

Win32 網際網路延伸模組（或 WinInet）提供一般網際網路通訊協定的存取權，包括 gopher、FTP 和 HTTP。 您可以使用 WinInet，以較高的程式設計層級撰寫網際網路用戶端應用程式，而不需要處理 WinSock、TCP/IP 或特定網際網路通訊協定的詳細資料。 WinInet 提供一組一致的函式，適用于這三個通訊協定，並具有熟悉的 WIN32 API 介面。 如果基礎通訊協定有所變更（例如，從 FTP 到 HTTP），這種一致性可將您需要進行的程式碼變更降至最低。

Visual C++ 提供兩種方式讓您使用 WinInet。 您可以直接呼叫 Win32 網際網路函式（如需詳細資訊，請參閱 Windows SDK 中的 OLE 檔），也可以透過[MFC wininet 類別](mfc-classes-for-creating-internet-client-applications.md)使用 WinInet。

**您可以使用 WinInet 來執行下列動作：**

- 下載 HTML 網頁。

   HTTP 是一種通訊協定，用來將 HTML 網頁從伺服器傳送至用戶端瀏覽器。

- 傳送 FTP 要求以上傳或下載檔案，或取得目錄清單。

   一般的要求是以匿名的登入來下載檔案。

- 使用 gopher 的功能表系統來存取網際網路上的資源。

   功能表項目可以是數種類型，包括其他功能表、可搜尋的索引資料庫、新聞群組或檔案。

對於這三種通訊協定，您可以建立連接、對伺服器提出要求，然後關閉連線。

**MFC WinInet 類別可讓您輕鬆地：**

- 讀取來自 HTTP、FTP 和 Gopher 伺服器的資訊，就像從硬碟讀取檔案一樣容易。

- 使用 HTTP、FTP 和 gopher 通訊協定，而不需要直接對 WinSock 或 TCP/IP 進行程式設計。

   使用 Win32 網際網路功能的開發人員不需要熟悉 TCP/IP 或 Windows 通訊端。 您仍然可以在通訊端層級進行程式設計，直接使用 WinSock 和 TCP/IP 通訊協定，但更容易使用 MFC WinInet 類別來存取網際網路上的 HTTP、FTP 和 gopher 通訊協定。 針對許多常見的作業，開發人員不需要知道所使用之特定通訊協定的詳細資料。

您的電腦在網際網路上做為用戶端執行的許多作業可能需要很長的時間。 這些作業的速度通常會受到網路連線速度的限制，但也可能受到其他網路流量和作業複雜度的影響。 例如，連接到遠端 FTP 伺服器時，您的電腦必須先查閱該伺服器的名稱，才能找到其位址。 然後，您的應用程式會嘗試連接到該位址的伺服器。 一旦開啟連線，您的電腦和遠端伺服器就會起始與檔案傳輸協定的交談，您才能實際使用該連線來抓取檔案。

## <a name="see-also"></a>另請參閱

[Win32 網際網路擴充功能 (WinInet)](win32-internet-extensions-wininet.md)<br/>
[MFC 如何讓您更輕鬆地建立網際網路用戶端應用程式](how-mfc-makes-it-easier-to-create-internet-client-applications.md)
