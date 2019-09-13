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
ms.openlocfilehash: b205599ed3bf33e84516120b1855482797b86c9b
ms.sourcegitcommit: effb516760c0f956c6308eeded48851accc96b92
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70924908"
---
# <a name="application-design-choices"></a>應用程式設計選擇

本文討論在針對網際網路進行程式設計時要考慮的一些設計問題。

本文涵蓋的主題包括：

- [內部網路與網際網路](#_core_intranet_versus_internet)

- [用戶端或伺服器應用程式](#_core_client_or_server_application)

- [網頁](#_core_the_web_page)

- [瀏覽器或獨立應用程式](#_core_browser_or_standalone)

- [網際網路上的 COM](#_core_com_on_the_internet)

- [用戶端資料下載服務](#_core_client_data_download_services)

如果您已準備好立即開始撰寫程式，請參閱[撰寫 MFC 應用程式](../mfc/writing-mfc-applications.md)。

##  <a name="_core_intranet_versus_internet"></a>內部網路與網際網路

許多應用程式都是在網際網路上執行，並可供具有瀏覽器和網際網路存取權的任何人存取。 企業也使用 TCP/IP 通訊協定和網頁瀏覽器來實行內部網路，也就是全公司的網路。 內部網路為全公司的資訊提供容易升級的集中式來源。 它們可用於升級軟體、提供和表列出個別問卷調查、客戶支援和資訊傳遞。 下表比較網際網路和內部網路的功能。

|網際網路|內部網路|
|--------------|--------------|
|低頻寬|高頻寬|
|降低資料和系統的安全性|控制對資料和系統的存取|
|內容的最低控制|內容的高度控制|

##  <a name="_core_client_or_server_application"></a>用戶端或伺服器應用程式

您的應用程式可能會在用戶端電腦或伺服器電腦上執行。 您的應用程式也可以儲存在伺服器上，然後在網際網路上下載並在用戶端電腦上執行。 MFC WinInet 類別是用來讓用戶端應用程式下載檔案。 MFC 和非同步標記類別是用來下載檔案和控制項屬性。 ActiveX 控制項和作用中檔的類別會用於用戶端應用程式，以及從伺服器下載以在用戶端上執行的應用程式。

##  <a name="_core_the_web_page"></a>網頁：HTML、活動文檔、ActiveX 控制項

Microsoft 提供數種方式來提供網頁上的內容。 網頁可以使用標準 HTML 或 HTML 延伸模組（例如物件標記）來提供動態內容（例如 ActiveX 控制項）。

網頁瀏覽器通常會顯示 HTML 頁面。 活動文檔也可以在啟用 COM 的瀏覽器的簡單點即用介面中，顯示您的應用程式資料。 您的活動文檔伺服器可以使用自己的功能表和工具列，在整個工作區中顯示檔、完整框架。

您可以從伺服器以非同步方式下載您撰寫的 ActiveX 控制項，並顯示在網頁上。 您可以使用指令碼語言（例如 VBScript）來執行用戶端驗證，然後再將資訊傳送至伺服器。

##  <a name="_core_browser_or_standalone"></a>瀏覽器或獨立應用程式

您可以撰寫內嵌在 HTML 頁面中的 ActiveX 控制項，以及在瀏覽器中看到的活動文檔伺服器。 您可以撰寫包含按鈕的 HTML 網頁，以提交在 Web 服務器上執行 ISAPI 應用程式的要求。 您可以撰寫一個獨立應用程式，使用網際網路通訊協定來下載檔案，並向使用者顯示資訊，而不需要使用瀏覽器應用程式。

##  <a name="_core_com_on_the_internet"></a>網際網路上的 COM

ActiveX 控制項、活動文檔和非同步名字全都使用 COM （元件物件模型）技術。

ActiveX 控制項提供動態內容給網際網路網站上的檔和頁面。 有了 COM 之後，您就可以使用活動文檔來建立 ActiveX 控制項和全框架檔。

非同步標記會提供功能，讓控制項在網際網路環境中執行得很順利，包括下載資料的累加或漸進式方法。 控制項也必須與其他可能也會同時以非同步方式抓取資料的控制項搭配運作。

##  <a name="_core_client_data_download_services"></a>用戶端資料下載服務

兩組可協助將資料傳送至您的用戶端的 Api 是 WinInet 和非同步名字。 如果您的 HTML 網頁上有大型 .gif 和 .avi 檔案和 ActiveX 控制項，您可以藉由使用非同步名字或以非同步方式使用 WinInet，以非同步方式下載來增加使用者的回應能力。

網際網路上的一般工作是傳送資料。 如果您已經在使用現用技術（例如，如果您有 ActiveX 控制項），您可以使用非同步名字，在下載時逐漸呈現資料。 您可以使用 WinInet，透過 HTTP、FTP 和 gopher 等常見的網際網路通訊協定來傳輸資料。 這兩種方法都會提供通訊協定獨立性，並提供抽象層來使用 WinSock 和 TCP/IP。 您仍然可以直接使用[WinSock](../mfc/windows-sockets-in-mfc.md) 。

下表摘要說明使用 MFC 在網際網路上傳輸資料的數種方式。

|使用此通訊協定|在這些情況下|使用這些類別|
|-----------------------|----------------------------|-------------------------|
|[使用非同步名字標記的網際網路下載](../mfc/asynchronous-monikers-on-the-internet.md)|適用于使用 COM、ActiveX 控制項和任何網際網路通訊協定進行非同步傳輸。|[CAsyncMonikerFile](../mfc/reference/casyncmonikerfile-class.md)、 [CDataPathProperty](../mfc/reference/cdatapathproperty-class.md)|
|[WinInet](../mfc/win32-internet-extensions-wininet.md)|適用于 HTTP、FTP 和 gopher 的網際網路通訊協定。 您可以同步或非同步方式傳輸資料，並將其儲存在全系統的快取中。|[CInternetSession](../mfc/reference/cinternetsession-class.md)、 [CFtpFileFind](../mfc/reference/cftpfilefind-class.md)、 [CGopherFileFind](../mfc/reference/cgopherfilefind-class.md)及其他許多。|
|[WinSock](../mfc/windows-sockets-in-mfc.md)|以達到最高效率和控制。 需要瞭解通訊端和 TCP/IP 通訊協定。|[CSocket](../mfc/reference/csocket-class.md)、 [CAsyncSocket](../mfc/reference/casyncsocket-class.md)|

## <a name="see-also"></a>另請參閱

[MFC 網際網路程式設計工作](../mfc/mfc-internet-programming-tasks.md)<br/>
[MFC 網際網路程式設計基本概念](../mfc/mfc-internet-programming-basics.md)<br/>
[Win32 網際網路延伸模組 (WinInet)](../mfc/win32-internet-extensions-wininet.md)<br/>
[網際網路上的非同步 Moniker](../mfc/asynchronous-monikers-on-the-internet.md)
