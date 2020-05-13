---
title: 應用程式設計選擇
ms.date: 09/12/2019
helpviewer_keywords:
- design
- application design [MFC], design goals
- application design [MFC], Internet applications
- Internet applications [MFC], designing applications
- Internet [MFC], vs. intranets
- applications [MFC], Internet
- server applications [MFC], vs. client applications on Internet
- client applications [MFC], vs. server applications on Internet
ms.assetid: 9b96172c-b4d4-4c69-bfb2-226ce0de6d08
ms.openlocfilehash: 89f3e5c108de1cf7b3b73a33a08e2c50b1333c92
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374635"
---
# <a name="application-design-choices"></a>應用程式設計選擇

本文討論了在為 Internet 程式設計時需要考慮的一些設計問題。

本文涵蓋的主題包括:

- [內聯網與互聯網](#_core_intranet_versus_internet)

- [用戶端或伺服器應用程式](#_core_client_or_server_application)

- [網頁](#_core_the_web_page)

- [瀏覽器或獨立應用程式](#_core_browser_or_standalone)

- [網際網路上的 COM](#_core_com_on_the_internet)

- [用戶端資料下載服務](#_core_client_data_download_services)

如果您現在準備開始編寫程式,請參閱[編寫 MFC 應用程式](../mfc/writing-mfc-applications.md)。

## <a name="intranet-versus-internet"></a><a name="_core_intranet_versus_internet"></a>內聯網與互聯網

許多應用程式在 Internet 上運行,任何具有瀏覽器和 Internet 訪問許可權的人都可以訪問這些應用程式。 企業還在實施內部網,這些內部網是使用 TCP/IP 協定和 Web 瀏覽器的全公司網路。 內聯網為全公司的資訊提供了易於升級的中央來源。 它們可用於升級軟體、交付和制表調查、客戶支援以及信息傳遞。 下表比較了互聯網和內聯網的功能。

|Internet|內部網路|
|--------------|--------------|
|低頻寬|高頻寬|
|降低資料和系統的安全性|對資料與系統的受控存取|
|對內容的最小控制|對內容的高度控制|

## <a name="client-or-server-application"></a><a name="_core_client_or_server_application"></a>用戶端或伺服器應用程式

您的應用程式可能在用戶端電腦或伺服器電腦上運行。 您的應用程式也可能存儲在伺服器上,然後通過 Internet 下載並在用戶端電腦上運行。 MFC WinInet 類用於用戶端應用程式下載檔。 MFC 和非同步名字物件類用於下載檔案和控制屬性。 ActiveX 控制件和活動文件的類用於用戶端應用程式和從伺服器下載以在用戶端上運行的應用程式。

## <a name="the-web-page-html-active-documents-activex-controls"></a><a name="_core_the_web_page"></a>網頁:HTML、活動文件、活動X控制項

Microsoft 提供了幾種在網頁上提供內容的方法。 網頁可以使用標準 HTML 或 HTML 副檔名(如物件標記)來提供動態內容(如 ActiveX 控制件)。

Web 瀏覽器通常顯示 HTML 頁面。 活動文件還可以在啟用 COM 的瀏覽器的簡單點擊介面中顯示應用程式的數據。 活動文件伺服器可以顯示文檔,整個工作區中的完整框架,並擁有自己的功能表和工具列。

可以從伺服器非同步下載您編寫的 ActiveX 控制件,並顯示在網頁上。 在將資訊發送到伺服器之前,可以使用腳本語言(如 VBScript)執行客戶端驗證。

## <a name="browser-or-stand-alone-application"></a><a name="_core_browser_or_standalone"></a>瀏覽器或獨立應用程式

您可以編寫嵌入在 HTML 頁中的 ActiveX 控制件,也可以編寫在瀏覽器中查看的 Active 文件伺服器。 您可以編寫包含按鈕的 HTML 頁,以提交在 Web 伺服器上執行 ISAPI 應用程式的請求。 您可以編寫一個獨立的應用程式,該應用程式使用 Internet 協定下載檔和向使用者顯示資訊,而無需使用瀏覽器應用程式。

## <a name="com-on-the-internet"></a><a name="_core_com_on_the_internet"></a>網際網路上的 COM

ActiveX 控制件、活動文件和非同步名字器都使用 COM(元件物件模型)技術。

ActiveX 控制件為 Internet 網站上的文件和頁面提供動態內容。 使用 COM,您可以使用 Active 文件建構 ActiveX 控制件和全幀文件。

非同步名字器提供功能,使控制項能夠在 Internet 環境中很好地運行,包括下載資料的增量或漸進方法。 控件還必須與可能同時異步檢索其數據的其他控制項很好地配合。

## <a name="client-data-download-services"></a><a name="_core_client_data_download_services"></a>用戶端資料下載服務

兩組有助於將數據傳輸到用戶端的 API 是 WinInet 和非同步名字。 如果您的 HTML 頁面上有較大的 .gif 和 .avi 檔和 ActiveX 控件,則可以通過非同步下載(透過使用非同步名字)或使用 WinInet 同步來提高使用者的回應能力。

互聯網上的一項常見任務是傳輸數據。 如果您已經在使用 Active 技術(例如,如果您有 ActiveX 控制件),則可以使用非同步名字物件在資料下載時逐步呈現資料。 您可以使用 WinInet 使用常見的 Internet 協定(如 HTTP、FTP 和 gopher)傳輸數據。 這兩種方法都提供了協定獨立性,並提供一個抽象層來使用 WinSock 和 TCP/IP。 您仍然可以直接使用[溫索克](../mfc/windows-sockets-in-mfc.md)。

下表總結了使用 MFC 通過互聯網傳輸數據的幾種方法。

|使用此協定|在這些條件下|使用這些類別|
|-----------------------|----------------------------|-------------------------|
|[使用非同步網站下載網際網路下載](../mfc/asynchronous-monikers-on-the-internet.md)|對於使用 COM、ActiveX 控制件和任何 Internet 協定進行非同步傳輸。|[CAsyncMoniker 檔案](../mfc/reference/casyncmonikerfile-class.md), [CDataPath 屬性](../mfc/reference/cdatapathproperty-class.md)|
|[WinInet](../mfc/win32-internet-extensions-wininet.md)|用於 HTTP、FTP 和 gopher 的 Internet 協定。 數據可以同步或異步傳輸,並存儲在系統範圍的緩存中。|[C網際網路工作階段](../mfc/reference/cinternetsession-class.md), [CFtpFile 搜尋](../mfc/reference/cftpfilefind-class.md), [CGopher 檔搜尋](../mfc/reference/cgopherfilefind-class.md), 並更多.|
|[溫索克](../mfc/windows-sockets-in-mfc.md)|實現最高的效率和控制。 需要瞭解套接字和 TCP/IP 協定。|[Socket](../mfc/reference/csocket-class.md), [CAsyncSocket](../mfc/reference/casyncsocket-class.md)|

## <a name="see-also"></a>另請參閱

[MFC 網際網路程式設計工作](../mfc/mfc-internet-programming-tasks.md)<br/>
[MFC 網際網路程式設計基本概念](../mfc/mfc-internet-programming-basics.md)<br/>
[Win32 網際網路擴充功能 (WinInet)](../mfc/win32-internet-extensions-wininet.md)<br/>
[網際網路上的非同步 Moniker](../mfc/asynchronous-monikers-on-the-internet.md)
