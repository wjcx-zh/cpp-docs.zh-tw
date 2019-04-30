---
title: 應用程式設計選擇
ms.date: 11/04/2016
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
ms.openlocfilehash: cdb294e4ab808a7e4cbcec457f6e744eff9f12cb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62394659"
---
# <a name="application-design-choices"></a>應用程式設計選擇

這篇文章會討論一些設計問題，以針對網際網路程式設計時，請考慮。

本文章涵蓋的主題包括：

- [內部網路與網際網路](#_core_intranet_versus_internet)

- [用戶端或伺服器應用程式](#_core_client_or_server_application)

- [](#_core_the_web_page)

- [瀏覽器或獨立的應用程式](#_core_browser_or_standalone)

- [在網際網路上的 COM](#_core_com_on_the_internet)

- [用戶端資料下載服務](#_core_client_data_download_services)

如果您已準備好開始撰寫您的程式，現在，請參閱 <<c0> [ 撰寫 MFC 應用程式](../mfc/writing-mfc-applications.md)。

##  <a name="_core_intranet_versus_internet"></a> 內部網路與網際網路

許多應用程式在網際網路上執行，且可供瀏覽器和網際網路存取的任何人存取。 企業也會實作內部網路，它會使用 TCP/IP 通訊協定的全公司的網路和網頁瀏覽器。 內部網路提供可輕鬆地升級、 中央的來源，如全公司的資訊。 它們可用來升級軟體、 傳遞和製作問卷調查、 客戶支援及資訊傳遞。 下表比較網際網路與內部網路的功能。

|網際網路|內部網路|
|--------------|--------------|
|低頻寬|高頻寬|
|資料和系統的安全性降低|資料和系統的控制的存取|
|最小的控制項的內容|內容的高度控制權|

##  <a name="_core_client_or_server_application"></a> 用戶端或伺服器應用程式

在用戶端電腦或伺服器電腦上，可能會執行您的應用程式。 您的應用程式可能也會儲存在伺服器上，然後透過網際網路下載並執行用戶端電腦上。 MFC WinInet 類別被用戶端應用程式用來下載檔案。 MFC 和非同步 moniker 類別用來下載檔案，並控制屬性中。 用戶端應用程式以及從用戶端上執行的伺服器下載的應用程式，會使用 ActiveX 控制項和主動式文件的類別。

##  <a name="_core_the_web_page"></a> 網頁中：HTML，主動式文件，ActiveX 控制項

Microsoft 提供幾個方法可在網頁上提供內容。 網頁可以使用標準 HTML 或 HTML 擴充功能，例如物件標記，以提供動態內容，例如 ActiveX 控制項。

Web 瀏覽器通常會顯示的 HTML 網頁。 主動式文件也可以在簡單的點按一下介面，在啟用 COM 的瀏覽器中顯示您的應用程式資料。 您使用中文件的伺服器可以在整個用戶端區域中，使用自己的功能表和工具列顯示您的文件、 完整的畫面格。

您撰寫的 ActiveX 控制項可以以非同步方式從伺服器下載，並顯示在網頁上。 您可以使用指令碼的語言，例如 VBScript 來執行用戶端驗證，然後再將資訊傳送到伺服器。

##  <a name="_core_browser_or_standalone"></a> 瀏覽器或獨立的應用程式

您可以撰寫會內嵌在 HTML 網頁和瀏覽器中檢視的使用中文件伺服器的 ActiveX 控制項。 您可以撰寫包含按鈕以提交要求給 Web 伺服器上執行 ISAPI 應用程式的 HTML 頁面。 您可以撰寫使用網際網路通訊協定下載檔案，並顯示您的使用者，不需使用瀏覽器應用程式資訊的獨立應用程式。

##  <a name="_core_com_on_the_internet"></a> 在網際網路上的 COM

ActiveX 控制項、 使用中的文件，以及非同步 moniker 所有使用 COM （元件物件模型） 技術。

ActiveX 控制項提供網際網路網站上的文件和頁面的動態內容。 以 COM 中，您可以建立 ActiveX 控制項與使用主動式文件的完整框架文件。

非同步 moniker 提供功能，可讓控制項來執行也是在網際網路環境中，包括增量或漸進式表示若要下載資料。 控制項必須也適用於其他控制項，可能也會擷取其資料以非同步方式在相同的時間。

##  <a name="_core_client_data_download_services"></a> 用戶端資料下載服務

兩個可協助您的用戶端傳送資料的 Api 集是 WinInet 和非同步 moniker。 如果您有大型的.gif 和.avi 檔案和 HTML 網頁上的 ActiveX 控制項，您可以藉由使用非同步 moniker，或以非同步方式使用 WinInet 以非同步方式下載來增加使用者的回應能力。

在網際網路上常見的工作正在傳送資料。 如果您已經使用 Active 技術 （例如，如果您有 ActiveX 控制項），您可以使用非同步 moniker 漸進式呈現資料，因為它會下載。 您可以使用 WinInet 傳輸使用常用的網際網路通訊協定，例如 HTTP、 FTP 和 gopher 的資料。 這兩種方法提供通訊協定獨立性，並提供一個抽象層使用 WinSock 和 TCP/IP。 您仍然可以使用[WinSock](../mfc/windows-sockets-in-mfc.md)直接。

下表摘要說明使用 MFC 透過網際網路傳輸資料的數種方式。

|使用此通訊協定|在這些情況下|使用這些類別|
|-----------------------|----------------------------|-------------------------|
|[網際網路下載使用非同步 Moniker](../mfc/asynchronous-monikers-on-the-internet.md)|使用 COM，ActiveX 控制項的非同步傳送和任何的網際網路通訊協定。|[CAsyncMonikerFile](../mfc/reference/casyncmonikerfile-class.md)， [CDataPathProperty](../mfc/reference/cdatapathproperty-class.md)|
|[WinInet](../mfc/win32-internet-extensions-wininet.md)|HTTP、 FTP 和 gopher 的網際網路通訊協定。 資料可以同步或非同步方式傳輸和儲存在全系統快取。|[CInternetSession](../mfc/reference/cinternetsession-class.md)， [CFtpFileFind](../mfc/reference/cftpfilefind-class.md)， [CGopherFileFind](../mfc/reference/cgopherfilefind-class.md)，和其他項目。|
|[WinSock](../mfc/windows-sockets-in-mfc.md)|適用於最高效率和控制。 需要了解通訊端與 TCP/IP 通訊協定。|[CSocket](../mfc/reference/csocket-class.md), [CAsyncSocket](../mfc/reference/casyncsocket-class.md)|

## <a name="see-also"></a>另請參閱

[MFC 網際網路程式設計工作](../mfc/mfc-internet-programming-tasks.md)<br/>
[MFC 網際網路程式設計基本概念](../mfc/mfc-internet-programming-basics.md)<br/>
[Win32 網際網路延伸模組 (WinInet)](../mfc/win32-internet-extensions-wininet.md)<br/>
[網際網路上的非同步 Moniker](../mfc/asynchronous-monikers-on-the-internet.md)
