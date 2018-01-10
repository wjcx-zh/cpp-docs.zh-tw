---
title: "MFC 網際網路程式設計基本概念 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- ISAPI extensions, programming with ISAPI
- Internet applications [MFC]
- ISAPI
- ActiveX controls [MFC], Internet
- programming [MFC], Internet
- Web applications [MFC], MFC classes
- ISAPI filters [MFC], programming with ISAPI
- Internet applications [MFC], ActiveX controls
- Internet applications [MFC], writing
- Internet applications [MFC], Active technology
- Active technology [MFC]
- Internet content [MFC]
- WinInet classes [MFC]
ms.assetid: 6df2dfd0-6e3f-4587-9d01-2a32f00f8a6f
caps.latest.revision: "18"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1c03cdca832dcf0627ad033082085661c3b26847
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/03/2018
---
# <a name="mfc-internet-programming-basics"></a>MFC 網際網路程式設計基本概念
Microsoft 提供許多應用程式開發介面撰寫用戶端和伺服器應用程式。 許多新的應用程式正在寫入的網際網路功能，並做為技術、 瀏覽器能力和安全性選項會變更，將寫入新類型的應用程式。 用戶端電腦，提供對 World Wide Web 存取，並顯示包含文字、 圖形、 ActiveX 控制項和文件的 HTML 網頁瀏覽器執行。 伺服器提供 FTP、 HTTP 和 gopher 服務，並執行使用 CGI 的伺服器延伸應用程式。 自訂應用程式可以擷取資訊，並提供在網際網路上的資料。  
  
 ![用戶端和伺服器應用程式](../mfc/media/vc38bq1.gif "vc38bq1")  
  
 MFC 提供類別，可支援網際網路程式設計。 您可以使用[COleControl](../mfc/reference/colecontrol-class.md)和[CDocObjectServer](../mfc/reference/cdocobjectserver-class.md)和相關的 MFC 類別來撰寫 ActiveX 控制項和主動式文件。 您可以使用 MFC 類別，例如[CInternetSession](../mfc/reference/cinternetsession-class.md)， [CFtpConnection](../mfc/reference/cftpconnection-class.md)，和[CAsyncMonikerFile](../mfc/reference/casyncmonikerfile-class.md)擷取檔案與使用網際網路通訊協定，例如 FTP 資訊HTTP 和 gopher。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [網際網路相關的 MFC 類別](../mfc/internet-related-mfc-classes.md)  
  
-   [依主題分類的網際網路資訊](../mfc/internet-information-by-topic.md)  
  
-   [依工作分類的網際網路資訊](../mfc/internet-information-by-task.md)  
  
-   [網際網路上的 Active 技術](../mfc/active-technology-on-the-internet.md)  
  
-   [WinInet 基本概念](../mfc/wininet-basics.md)  
  
-   [HTML 的基本概念](../mfc/html-basics.md)  
  
-   [HTTP 的基本概念](../mfc/http-basics.md)  
  
## <a name="related-sections"></a>相關章節  
  
-   [網際網路上的 ActiveX 控制項](../mfc/activex-controls-on-the-internet.md)  
  
-   [網際網路上的主動式文件](../mfc/active-documents-on-the-internet.md)  
  
-   [網際網路上的非同步 Moniker](../mfc/asynchronous-monikers-on-the-internet.md)  
  
-   [Win32 網際網路延伸模組 (WinInet)](../mfc/win32-internet-extensions-wininet.md)  
  
-   [MFC 網際網路程式設計工作](../mfc/mfc-internet-programming-tasks.md)  
  
-   [應用程式設計選擇](../mfc/application-design-choices.md)  
  
-   [撰寫 MFC 應用程式](../mfc/writing-mfc-applications.md)  
  
-   [測試網際網路應用程式](../mfc/testing-internet-applications.md)  
  
-   [網際網路安全性](../mfc/internet-security-cpp.md)  
  
-   [DHTML 控制項的 ATL 支援](../atl/atl-support-for-dhtml-controls.md)  
  
##  <a name="_core_web_sites_for_more_information"></a>如需詳細資訊的網站  
 如需 Microsoft 網際網路技術的詳細資訊，請參閱[Microsoft Developer Network (MSDN)](http://go.microsoft.com/fwlink/p/?linkid=56322)網站。 （連結可能會變更恕不另行通知。）  
  
 開發人員針對此網站包含有關使用 Microsoft 開發工具和技術，以及有關最近和即將發行所做的心得頭條新聞。 從這個頁面上，您可以跳到許多相關的開發人員網站，包括.NET 和 XML 開發人員中心。 您也可以下載 beta Sdk 和範例。  
  
 [World Wide Web Consortium (W3C)](http://go.microsoft.com/fwlink/p/?linkid=37125)發行 HTML、 HTTP、 CGI，和其他全球資訊網的技術規格。  
  
##  <a name="_core_more_internet_help"></a>更多協助以網際網路  
 Windows sdk 的 OLE 部分包含 OLE 程式設計的其他資訊。 這項資訊提供直接管理，而不是透過 MFC 類別使用的 Win32 WinInet 函式詳細資料。 它也會包含網際網路技術的概觀資訊。  
  
## <a name="see-also"></a>請參閱  



