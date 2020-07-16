---
title: MFC 網際網路程式設計基本概念
ms.date: 11/19/2018
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
ms.openlocfilehash: c9825cdcb5cb0963a4e0d3acdeb36dfee54b70fc
ms.sourcegitcommit: 6b3d793f0ef3bbb7eefaf9f372ba570fdfe61199
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2020
ms.locfileid: "86405022"
---
# <a name="mfc-internet-programming-basics"></a>MFC 網際網路程式設計基本概念

Microsoft 提供許多 Api 來設計用戶端和伺服器應用程式。 許多新的應用程式都是針對網際網路撰寫，而且隨著技術、瀏覽器功能和安全性選項的變更，將會撰寫新類型的應用程式。 瀏覽器會在用戶端電腦上執行，以提供全球 Web 的存取權，並顯示包含文字、圖形、ActiveX 控制項和檔的 HTML 頁面。 伺服器提供 FTP、HTTP 和 gopher 服務，並使用 CGI 執行伺服器擴充應用程式。 您的自訂應用程式可以在網際網路上取得資訊並提供資料。

>[!IMPORTANT]
> ActiveX 是不應該用於新開發的舊版技術。 如需詳細資訊，請參閱[ActiveX 控制項](activex-controls.md)。

![用戶端和伺服器應用程式](../mfc/media/vc38bq1.gif "用戶端和伺服器應用程式")

MFC 提供支援網際網路程式設計的類別。 您可以使用[COleControl](reference/colecontrol-class.md)和[CDocObjectServer](reference/cdocobjectserver-class.md)和相關的 MFC 類別來撰寫 ActiveX 控制項和作用中的檔。 您可以使用[CInternetSession](reference/cinternetsession-class.md)、 [CFtpConnection](reference/cftpconnection-class.md)和[CAsyncMonikerFile](reference/casyncmonikerfile-class.md)等 MFC 類別，使用網際網路通訊協定（例如 FTP、HTTP 和 gopher）來取出檔案和資訊。

## <a name="in-this-section"></a>本節內容

- [網際網路相關的 MFC 類別](internet-related-mfc-classes.md)

- [依主題分類的網際網路資訊](internet-information-by-topic.md)

- [依工作分類的網際網路資訊](internet-information-by-task.md)

- [網際網路上的 Active 技術](active-technology-on-the-internet.md)

- [WinInet 基本概念](wininet-basics.md)

- [HTML 的基本概念](html-basics.md)

## <a name="related-sections"></a>相關章節

- [網際網路上的 ActiveX 控制項](activex-controls-on-the-internet.md)

- [網際網路上的非同步 Moniker](asynchronous-monikers-on-the-internet.md)

- [Win32 網際網路擴充功能 (WinInet)](win32-internet-extensions-wininet.md)

- [MFC 網際網路程式設計工作](mfc-internet-programming-tasks.md)

- [應用程式設計選擇](application-design-choices.md)

- [撰寫 MFC 應用程式](writing-mfc-applications.md)

- [測試網際網路應用程式](testing-internet-applications.md)

- [網際網路安全性](internet-security-cpp.md)

- [DHTML 控制項的 ATL 支援](../atl/atl-support-for-dhtml-controls.md)

## <a name="websites-for-more-information"></a><a name="_core_web_sites_for_more_information"></a>網站以取得詳細資訊

如需 Microsoft 網際網路技術的詳細資訊，請參閱[Microsoft Docs](https://docs.microsoft.com/)。

[全球資訊網協會（W3C）](https://go.microsoft.com/fwlink/p/?linkid=37125)會發行 HTML、HTTP、CGI 和其他 World Wide Web 技術的規格。

## <a name="more-internet-help"></a><a name="_core_more_internet_help"></a>其他網際網路協助

Windows SDK 的 OLE 區段包含 OLE 程式設計的其他相關資訊。 此資訊提供直接使用 Win32 WinInet 函式（而非透過 MFC 類別）的詳細資料。 其中也包含有關網際網路技術的總覽資訊。
