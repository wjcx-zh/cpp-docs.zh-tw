---
title: "應用程式設計選擇 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "應用程式設計 [C++], 設計目標"
  - "應用程式設計 [C++], 網際網路應用程式"
  - "應用程式 [MFC], 網際網路"
  - "用戶端應用程式 [C++], 和網際網路上伺服器應用程式比較"
  - "設計"
  - "網際網路 [C++], 和內部網路比較"
  - "網際網路應用程式 [C++], 設計應用程式"
  - "伺服器應用程式, 和網際網路上用戶端應用程式比較"
ms.assetid: 9b96172c-b4d4-4c69-bfb2-226ce0de6d08
caps.latest.revision: 12
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 應用程式設計選擇
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

當程式設計為網際網路時，本文討論一些設計問題考慮。  
  
 在此文件中包含的主題:  
  
-   [內部網路對網際網路](#_core_intranet_versus_internet)  
  
-   [用戶端或伺服器應用程式](#_core_client_or_server_application)  
  
-   [Web 網頁:HTML，主動式文件， ActiveX 控制項](#_core_the_web_page.3a_.html.2c_.activex_documents.2c_.activex_controls)  
  
-   [瀏覽器或獨立應用程式](#_core_browser_or_stand.2d.alone_application)  
  
-   [在網際網路上的 COM](#_core_com_on_the_internet)  
  
-   [用戶端資料下載服務。](#_core_client_data_download_services)  
  
 如果您準備開始於撰寫程式，請參閱 [文字 MFC 應用程式](../mfc/writing-mfc-applications.md)。  
  
##  <a name="_core_intranet_versus_internet"></a> 內部網路對網際網路  
 在網際網路執行的應用程式並對任何人存取與瀏覽器和網際網路存取。  企業也會實作內部網路，使用 TCP\/IP 通訊協定和 Web 瀏覽器，是全公司網路。  內部網路提供可升級，中央來源對於全公司資訊。  它們可以用於升級軟體，，以提供和組成表調查，為客戶支援和指定訊息傳遞。  下表比較網際網路和內部網路的功能。  
  
|網際網路|Intranet|  
|----------|--------------|  
|低頻寬|高頻寬|  
|資料和系統降低安全性|對資料和系統控制輸入|  
|內容最小控制項|內容的控制項|  
  
##  <a name="_core_client_or_server_application"></a> 用戶端或伺服器應用程式  
 您的應用程式可能會在用戶端電腦或在伺服器電腦。  您的應用程式在伺服器可能也會儲存，跨網際網路上然後下載至用戶端電腦。  MFC WinInet 類別用於用戶端應用程式可以下載檔案。  MFC 和非同步 Moniker 類別用於下載檔案和控制項的屬性。  ActiveX 控制項的類別和現用文件用於用戶端應用程式以及從伺服器在用戶端下載執行的應用程式。  
  
##  <a name="_core_the_web_page.3a_.html.2c_.activex_documents.2c_.activex_controls"></a> Web 網頁:HTML，主動式文件， ActiveX 控制項  
 Microsoft 提供內容幾個方式在 Web 網頁。  網頁可以使用標準 HTML 或 HTML 副檔名，例如物件標記，提供動態內容 \(例如 ActiveX 控制項。  
  
 典型 Web 瀏覽器顯示 HTML 網頁。  現用文件也會顯示在啟用 COM 的瀏覽器的簡單然後按一下介面的應用程式資料。  您的主動式文件伺服程式可以顯示您的資料，在整個工作區執行完整框，與其功能表和工具列。  
  
 您所撰寫的 ActiveX 控制項在 Web 網頁可以從伺服器下載非同步和顯示。  您可以使用的指令碼語言，例如 VBScript 在傳輸資訊前執行用戶端驗證的伺服器。  
  
##  <a name="_core_browser_or_stand.2d.alone_application"></a> 瀏覽器或獨立應用程式  
 您可以撰寫 HTML 網頁和主動式文件伺服程式會內嵌在瀏覽器中檢視的 ActiveX 控制項。  您可以撰寫包含按鈕送出要求是在 Web 伺服器的 ISAPI 應用程式的 HTML 網頁。  您可以撰寫使用網際網路通訊協定下載檔案並顯示資訊給使用者的獨立應用程式，不用使使用瀏覽器應用程式。  
  
##  <a name="_core_com_on_the_internet"></a> 在網際網路上的 COM  
 ActiveX 控制項、現用文件和非同步標記全部使用 \(COM 元件物件模型 \(Component Object Model，COM\) 技術。  
  
 ActiveX 控制項的動態內容給文件和頁面在網際網路網站。  使用主動式文件， COM 可以建立 ActiveX 控制項和完整架構文件。  
  
 非同步標記以網際網路環境提供功能可讓控制項正常執行，包括一個加入或進度方法下載資料。  控制項必須很好也可能非同步同時擷取其資料的其他控制項一起使用。  
  
##  <a name="_core_client_data_download_services"></a> 用戶端資料下載服務。  
 將說明傳輸資料的用戶端的兩組 API 是 WinInet 和非同步標記。  如果您有大型 .gif 和 .avi 檔案和 ActiveX 控制項的 HTML 網頁，您可以將回應給使用者透過下載非同步，使用非同步標記或使用 WinInet 非同步。  
  
 在網際網路上的一般工作傳輸資料。  如果您已經使用 Active 技術 \(例如，因此，如果您有一個 ActiveX 控制項\)，您可以使用非同步標記的呈現資料做為下載。  使用像是 HTTP、FTP 和 Gopher，常見的網際網路通訊協定可以使用 WinInet 傳輸資料。  兩個方法提供與通訊協定無關的，並提供抽象層給使用 Winsock TCP\/IP 傳輸。  您可以直接仍然使用 [Winsock](../mfc/windows-sockets-in-mfc.md) 。  
  
 下表摘要說明使用 MFC 幾個方式傳輸網際網路的資料。  
  
|使用這個通訊協定|在這些條件下|使用這些類別|  
|--------------|------------|------------|  
|[使用非同步標記的網際網路下載](../mfc/asynchronous-monikers-on-the-internet.md)|對於使用 COM、ActiveX 控制項和任何網際網路通訊協定的非同步傳送。|[CAsyncMonikerFile](../mfc/reference/casyncmonikerfile-class.md)， [CDataPathProperty](../mfc/reference/cdatapathproperty-class.md)|  
|[WinInet](../mfc/win32-internet-extensions-wininet.md)|對於 HTTP、FTP 和 Gopher 的網際網路通訊協定。  可以將資料同步或非同步和在系統範圍快取中。|[CInternetSession](../mfc/reference/cinternetsession-class.md)、 [CFtpFileFind](../mfc/reference/cftpfilefind-class.md)和 [CGopherFileFind](../mfc/reference/cgopherfilefind-class.md)，許多。|  
|[WinSock](../mfc/windows-sockets-in-mfc.md)|對於最大效率和控制項。  通訊端和 TCP\/IP 通訊協定的 Requires 理解。|[CSocket](../mfc/reference/csocket-class.md)， [CAsyncSocket](../mfc/reference/casyncsocket-class.md)|  
  
## 請參閱  
 [MFC 網際網路程式設計工作](../mfc/mfc-internet-programming-tasks.md)   
 [MFC 網際網路程式設計基本概念](../mfc/mfc-internet-programming-basics.md)   
 [Win32 網際網路擴充功能 \(WinInet\)](../mfc/win32-internet-extensions-wininet.md)   
 [網際網路上的非同步 Moniker](../mfc/asynchronous-monikers-on-the-internet.md)