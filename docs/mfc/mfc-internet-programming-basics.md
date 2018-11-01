---
title: MFC 網際網路程式設計基本概念
ms.date: 09/12/2018
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
ms.openlocfilehash: 9d44d78474ccb030184c6e79ed2f257ffb00a068
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50509457"
---
# <a name="mfc-internet-programming-basics"></a>MFC 網際網路程式設計基本概念

Microsoft 提供許多 Api 用戶端和伺服器應用程式的程式設計。 許多新的應用程式正在寫入的網際網路功能，並為技術、 瀏覽器能力和安全性選項會變更，將寫入新類型的應用程式。 瀏覽器執行用戶端電腦，提供全球資訊網存取，並顯示包含文字、 圖形、 ActiveX 控制項及文件的 HTML 網頁上。 伺服器提供 FTP、 HTTP 和 gopher 服務，並執行使用 CGI 的伺服器擴充功能應用程式。 自訂應用程式可以擷取資訊，並提供在網際網路上的資料。

>[!IMPORTANT]
> ActiveX 是舊版的技術，不應用於新的開發。 如需詳細資訊，請參閱 < [ActiveX 控制項](activex-controls.md)。

![用戶端和伺服器應用程式](../mfc/media/vc38bq1.gif "vc38bq1")

MFC 提供支援網際網路程式設計的類別。 您可以使用[COleControl](../mfc/reference/colecontrol-class.md)並[CDocObjectServer](../mfc/reference/cdocobjectserver-class.md)和相關的 MFC 類別來撰寫 ActiveX 控制項和主動式文件。 您可以使用 MFC 類別，例如[CInternetSession](../mfc/reference/cinternetsession-class.md)， [CFtpConnection](../mfc/reference/cftpconnection-class.md)，並[CAsyncMonikerFile](../mfc/reference/casyncmonikerfile-class.md)來擷取檔案和使用 FTP，例如網際網路通訊協定的資訊HTTP 和 gopher。

## <a name="in-this-section"></a>本節內容

- [網際網路相關的 MFC 類別](../mfc/internet-related-mfc-classes.md)

- [依主題分類的網際網路資訊](../mfc/internet-information-by-topic.md)

- [依工作分類的網際網路資訊](../mfc/internet-information-by-task.md)

- [網際網路上的 Active 技術](../mfc/active-technology-on-the-internet.md)

- [WinInet 基本概念](../mfc/wininet-basics.md)

- [HTML 的基本概念](../mfc/html-basics.md)

## <a name="related-sections"></a>相關章節

- [網際網路上的 ActiveX 控制項](../mfc/activex-controls-on-the-internet.md)

- [網際網路上的非同步 Moniker](../mfc/asynchronous-monikers-on-the-internet.md)

- [Win32 網際網路延伸模組 (WinInet)](../mfc/win32-internet-extensions-wininet.md)

- [MFC 網際網路程式設計工作](../mfc/mfc-internet-programming-tasks.md)

- [應用程式設計選擇](../mfc/application-design-choices.md)

- [撰寫 MFC 應用程式](../mfc/writing-mfc-applications.md)

- [測試網際網路應用程式](../mfc/testing-internet-applications.md)

- [網際網路安全性](../mfc/internet-security-cpp.md)

- [DHTML 控制項的 ATL 支援](../atl/atl-support-for-dhtml-controls.md)

##  <a name="_core_web_sites_for_more_information"></a> 如需詳細資訊的網站

如需 Microsoft 網際網路技術的詳細資訊，請參閱[Microsoft Developer Network (MSDN)](http://go.microsoft.com/fwlink/p/?linkid=56322)網站。 （恕不另行通知可能會變更連結）。

適用於開發人員這個網站包含有關使用 Microsoft 開發工具和技術，以及最新和近期會議的頭條報導。 從這個頁面上，您可以跳到許多相關的開發人員網站，包括.NET 和 XML 開發人員中心。 您也可以下載 beta 版 Sdk 與範例。

[World Wide Web Consortium (W3C)](http://go.microsoft.com/fwlink/p/?linkid=37125)發行 HTML、 HTTP、 CGI，和其他全球資訊網的技術規格。

##  <a name="_core_more_internet_help"></a> 更多的網際網路協助

Windows SDK 的 OLE 部分包含 OLE 程式設計的其他資訊。 這項資訊提供有關使用 Win32 WinInet 函式，直接管理，而不是透過 MFC 類別的詳細資料。 它也包含網際網路技術的概觀資訊。

## <a name="see-also"></a>另請參閱

