---
title: "應用程式設計選擇 |Microsoft 文件"
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
- design
- application design [MFC], design goals
- application design [MFC], Internet applications
- Internet applications [MFC], designing applications
- Internet [MFC], vs. intranets
- applications [MFC], Internet
- server applications [MFC], vs. client applications on Internet
- client applications [MFC], vs. server applications on Internet
ms.assetid: 9b96172c-b4d4-4c69-bfb2-226ce0de6d08
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4b78c4c086b40f786d86411c99279245704a48a8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="application-design-choices"></a>應用程式設計選擇
這篇文章討論針對網際網路程式設計時所要考慮的設計問題。  
  
 本文涵蓋的主題包括：  
  
-   [內部網路與網際網路](#_core_intranet_versus_internet)  
  
-   [用戶端或伺服器應用程式](#_core_client_or_server_application)  
  
-   [](#_core_the_web_page)  
  
-   [瀏覽器或獨立的應用程式](#_core_browser_or_standalone)  
  
-   [在網際網路上 COM](#_core_com_on_the_internet)  
  
-   [用戶端資料下載服務](#_core_client_data_download_services)  
  
 如果您已經準備好開始撰寫您的程式，現在，請參閱[撰寫 MFC 應用程式](../mfc/writing-mfc-applications.md)。  
  
##  <a name="_core_intranet_versus_internet"></a>內部網路與網際網路  
 許多應用程式在網際網路上執行，而且瀏覽器和網際網路存取的任何人存取。 企業也會實作內部網路，也就是使用 TCP/IP 通訊協定的全公司的網路，然後在網頁瀏覽器。 內部網路提供全公司的資訊可輕鬆地升級、 中央來源。 它們可以用於升級軟體、 傳遞和製作調查、 客戶支援，以及資訊傳遞。 下表比較網際網路和內部網路的功能。  
  
|網際網路|內部網路|  
|--------------|--------------|  
|低頻寬|高頻寬|  
|降低的資料和系統的安全性|控制的存取資料和系統|  
|最小的內容控制項|內容的高度控制權|  
  
##  <a name="_core_client_or_server_application"></a>用戶端或伺服器應用程式  
 應用程式可能會在用戶端電腦或伺服器電腦上。 您的應用程式可能也會儲存在伺服器上，然後透過網際網路下載並執行用戶端電腦上。 MFC WinInet 類別會用於用戶端應用程式，以下載檔案。 MFC 和非同步 moniker 類別可用來下載檔案，並控制屬性。 用戶端應用程式和從用戶端上執行伺服器下載的應用程式使用 ActiveX 控制項和主動式文件的類別。  
  
##  <a name="_core_the_web_page"></a>網頁： HTML、 主動式文件，ActiveX 控制項  
 Microsoft 提供數種方式提供內容在網頁上。 網頁可以使用標準 HTML 或 HTML 擴充方法，例如物件標記，以提供動態內容，例如 ActiveX 控制項。  
  
 網頁瀏覽器通常顯示的 HTML 網頁。 主動式文件也可以啟用 COM 的瀏覽器的簡單點按一下介面中顯示您的應用程式資料。 您使用中文件的伺服器可以在整個工作區中，使用自己的功能表和工具列顯示您的文件、 完整的畫面格。  
  
 您撰寫的 ActiveX 控制項可以從伺服器以非同步方式下載，並顯示在網頁上。 若要執行用戶端驗證，再將資訊傳送至伺服器，您可以使用指令碼語言，例如 VBScript。  
  
##  <a name="_core_browser_or_standalone"></a>瀏覽器或獨立的應用程式  
 您可以撰寫嵌入 HTML 網頁和主動式文件伺服所檢視的瀏覽器中的 ActiveX 控制項。 您可以撰寫包含在 Web 伺服器上執行 ISAPI 應用程式的要求送出按鈕的 HTML 網頁。 您可以撰寫使用網際網路通訊協定，下載檔案，並顯示您的使用者不需使用瀏覽器應用程式資訊的獨立應用程式。  
  
##  <a name="_core_com_on_the_internet"></a>在網際網路上 COM  
 ActiveX 控制項、 主動式文件，以及非同步 moniker 所有使用 COM （元件物件模型） 技術。  
  
 ActiveX 控制項的網際網路站台上提供文件和頁面的動態內容。 您可以使用 COM 建置 ActiveX 控制項與使用主動式文件的完整框架文件。  
  
 非同步 moniker 提供功能，可讓控制項來執行也是在網際網路環境中，包括增量或漸進式下載資料的方法。 控制項也必須適用於其他控制項，可能也會擷取其資料以非同步方式在相同的時間。  
  
##  <a name="_core_client_data_download_services"></a>用戶端資料下載服務  
 兩個 Api，以便協助您的用戶端傳送資料集為 WinInet 和非同步 moniker。 如果您有大型.gif.avi 檔案和 HTML 網頁上的 ActiveX 控制項，您可以藉由以非同步方式下載，可以使用非同步 moniker 或以非同步方式使用 WinInet 增加給使用者的回應能力。  
  
 在網際網路上是常見的工作正在傳送資料。 如果您已經在使用 Active 技術 （例如，如果您有 ActiveX 控制項），您可以使用非同步 moniker 漸進式呈現它所下載的資料。 您可以使用 WinInet 傳輸使用常用的網際網路通訊協定，例如 HTTP、 FTP 和 gopher 的資料。 這兩種方法提供通訊協定獨立性，並提供一個抽象層來使用 WinSock 和 TCP/IP。 您仍然可以使用[WinSock](../mfc/windows-sockets-in-mfc.md)直接。  
  
 下表摘要說明使用 MFC 透過網際網路傳輸資料的數種方式。  
  
|使用此通訊協定|在這些情況下|使用這些類別|  
|-----------------------|----------------------------|-------------------------|  
|[網際網路下載使用非同步 Moniker](../mfc/asynchronous-monikers-on-the-internet.md)|非同步傳輸使用 COM、 ActiveX 控制項和任何的網際網路通訊協定。|[CAsyncMonikerFile](../mfc/reference/casyncmonikerfile-class.md)， [CDataPathProperty](../mfc/reference/cdatapathproperty-class.md)|  
|[WinInet](../mfc/win32-internet-extensions-wininet.md)|HTTP、 FTP 和 gopher 的網際網路通訊協定。 資料可以同步或非同步方式傳輸和儲存系統快取中。|[CInternetSession](../mfc/reference/cinternetsession-class.md)， [CFtpFileFind](../mfc/reference/cftpfilefind-class.md)， [CGopherFileFind](../mfc/reference/cgopherfilefind-class.md)，等等。|  
|[WinSock](../mfc/windows-sockets-in-mfc.md)|最大效率和控制。 需要了解通訊端以及 TCP/IP 通訊協定。|[CSocket](../mfc/reference/csocket-class.md)， [CAsyncSocket](../mfc/reference/casyncsocket-class.md)|  
  
## <a name="see-also"></a>請參閱  
 [MFC 網際網路程式設計工作](../mfc/mfc-internet-programming-tasks.md)   
 [MFC 網際網路程式設計基本概念](../mfc/mfc-internet-programming-basics.md)   
 [Win32 網際網路擴充功能 (WinInet)](../mfc/win32-internet-extensions-wininet.md)   
 [網際網路上的非同步 Moniker](../mfc/asynchronous-monikers-on-the-internet.md)

