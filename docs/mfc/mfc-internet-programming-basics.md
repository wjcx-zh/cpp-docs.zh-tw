---
title: "MFC 網際網路程式設計基本概念 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "Active 技術 [C++]"
  - "ActiveX 控制項 [C++], 網際網路"
  - "網際網路應用程式 [C++]"
  - "網際網路應用程式 [C++], Active 技術"
  - "網際網路應用程式 [C++], ActiveX 控制項"
  - "網際網路應用程式 [C++], 撰寫"
  - "網際網路內容 [C++]"
  - "ISAPI"
  - "ISAPI 擴充功能, 使用 ISAPI 進行程式設計"
  - "ISAPI 篩選器, 使用 ISAPI 進行程式設計"
  - "程式設計 [C++], 網際網路"
  - "Web 應用程式 [C++], MFC 類別"
  - "WinInet 類別"
ms.assetid: 6df2dfd0-6e3f-4587-9d01-2a32f00f8a6f
caps.latest.revision: 18
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# MFC 網際網路程式設計基本概念
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Microsoft 為撰寫的用戶端和伺服器應用程式提供許多 API。  許多應用程式是為了網際網路所撰寫，像是科技、瀏覽器功能和安全性選項變更時，應用程式的新型別將會寫入其中的。  瀏覽器在用戶端電腦上執行，以存取全球資訊網和顯示包含文字、圖形、ActiveX 控制項和文件的 HTML 網頁。  使用 CGI，伺服器的 FTP、HTTP 和 Gopher 服務並執行伺服器擴充應用程式。  您的自訂應用程式是在網際網路可擷取資訊並提供資料。  
  
 ![用戶端和伺服器應用程式](../mfc/media/vc38bq1.png "vc38BQ1")  
  
 MFC 提供支援網際網路程式設計的類別。  您可以使用 [COleControl](../mfc/reference/colecontrol-class.md) 和 [CDocObjectServer](../mfc/reference/cdocobjectserver-class.md) 以及相關的 MFC 類別時將 ActiveX 控制項和現用文件。  使用網際網路通訊協定 \(例如 HTTP、FTP 和 Gopher，您可以使用 MFC 類別 \(如 [CInternetSession](../mfc/reference/cinternetsession-class.md)、 [CFtpConnection](../mfc/reference/cftpconnection-class.md)和 [CAsyncMonikerFile](../mfc/reference/casyncmonikerfile-class.md) 擷取檔案和資訊。  
  
## 本章節內容  
  
-   [網際網路相關的 MFC 類別](../mfc/internet-related-mfc-classes.md)  
  
-   [依主題分類的網際網路資訊](../mfc/internet-information-by-topic.md)  
  
-   [依工作分類的網際網路資訊](../mfc/internet-information-by-task.md)  
  
-   [網際網路上的 Active 技術](../mfc/active-technology-on-the-internet.md)  
  
-   [WinInet 基本概念](../mfc/wininet-basics.md)  
  
-   [HTML 的基本概念](../mfc/html-basics.md)  
  
-   [HTTP 的基本概念](../mfc/http-basics.md)  
  
## 相關章節  
  
-   [網際網路上的 ActiveX 控制項](../mfc/activex-controls-on-the-internet.md)  
  
-   [網際網路上的主動式文件](../mfc/active-documents-on-the-internet.md)  
  
-   [網際網路上的非同步 Moniker](../mfc/asynchronous-monikers-on-the-internet.md)  
  
-   [Win32 網際網路擴充功能 \(WinInet\)](../mfc/win32-internet-extensions-wininet.md)  
  
-   [MFC 網際網路程式設計工作](../mfc/mfc-internet-programming-tasks.md)  
  
-   [應用程式設計選擇](../mfc/application-design-choices.md)  
  
-   [撰寫 MFC 應用程式](../mfc/writing-mfc-applications.md)  
  
-   [測試網際網路應用程式](../mfc/testing-internet-applications.md)  
  
-   [網際網路安全性](../mfc/internet-security-cpp.md)  
  
-   [DHTML 控制項的 ATL 支援](../atl/atl-support-for-dhtml-controls.md)  
  
##  <a name="_core_web_sites_for_more_information"></a> 有更多詳細資訊的網站  
 如需 Microsoft 網際網路技術的詳細資訊，請參閱網站 [Microsoft Developer Network \(MSDN\)](http://go.microsoft.com/fwlink/?LinkID=56322) 。\(連結可能會在沒有通知的情況下變更\)。  
  
 開發人員的這個網站包含使用 Microsoft 開發工具和技術的資訊以及有關最新將來的工作階段的最新消息。  從這個頁面，您可以跳到許多相關的開發人員網站，包括 .NET 和 XML Developer Center。  您也可以下載 Beta SDK 和範例。  
  
 [全球資訊網協會 \(W3C\) \(W3C\)](http://go.microsoft.com/fwlink/?LinkID=37125) HTML、HTTP、CGI 和其他全球資訊網技術發行規格。  
  
##  <a name="_core_more_internet_help"></a> 多個網際網路說明  
 [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)] 的 OLE 部分包含 OLE 程式設計的其他資訊。  這個資訊傳遞提供有關直接使用 Win32 WinInet 函式的詳細資料而不是使用 MFC 類別。  它也包含網際網路技術的概觀資訊。  
  
## 請參閱  
 [MFC Internet Programming \(NIB\)](http://msdn.microsoft.com/zh-tw/0f7a1f3a-385b-4d56-a55b-0d766840c58a)