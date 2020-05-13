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
ms.openlocfilehash: 5a8fb7bf07ec631869075c5977dcec468143ad56
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366280"
---
# <a name="mfc-internet-programming-basics"></a>MFC 網際網路程式設計基本概念

Microsoft 提供了許多 API 來程式設計用戶端和伺服器應用程式。 許多新應用程式正在為 Internet 編寫,隨著技術、瀏覽器功能和安全選項的變化,將編寫新型應用程式。 瀏覽器在用戶端計算機上運行,提供對萬維網的訪問,並顯示包含文本、圖形、ActiveX 控制項和文件的 HTML 頁面。 伺服器提供 FTP、HTTP 和 gopher 服務,並使用 CGI 運行伺服器擴展應用程式。 自定義應用程式可以檢索資訊並在 Internet 上提供數據。

>[!IMPORTANT]
> ActiveX 是一種不應用於新開發的傳統技術。 有關詳細資訊,請參閱[ActiveX 控制件](activex-controls.md)。

![用戶端和伺服器應用程式](../mfc/media/vc38bq1.gif "用戶端和伺服器應用程式")

MFC 提供支援 Internet 程式設計的類。 您可以使用[COleControl](../mfc/reference/colecontrol-class.md)和[CDocObjectServer](../mfc/reference/cdocobjectserver-class.md)以及相關的 MFC 類來編寫 ActiveX 控制件和活動文件。 您可以使用 MFC 類別(如[CInternetSession、CFtpConnect](../mfc/reference/cftpconnection-class.md)和[CAsyncMonikerFile)](../mfc/reference/casyncmonikerfile-class.md)使用 Internet 協定(如 FTP、HTTP 和[CInternetSession](../mfc/reference/cinternetsession-class.md)gopher)檢索檔和資訊。

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

- [Win32 網際網路擴充功能 (WinInet)](../mfc/win32-internet-extensions-wininet.md)

- [MFC 網際網路程式設計工作](../mfc/mfc-internet-programming-tasks.md)

- [應用程式設計選擇](../mfc/application-design-choices.md)

- [撰寫 MFC 應用程式](../mfc/writing-mfc-applications.md)

- [測試網際網路應用程式](../mfc/testing-internet-applications.md)

- [網際網路安全性](../mfc/internet-security-cpp.md)

- [DHTML 控制項的 ATL 支援](../atl/atl-support-for-dhtml-controls.md)

## <a name="web-sites-for-more-information"></a><a name="_core_web_sites_for_more_information"></a>網站瞭解更多資訊

有關Microsoft網路技術的其他資訊,請參閱[Microsoft開發人員網路 (MSDN)](https://go.microsoft.com/fwlink/p/?linkid=56322)網站。 (連結可能會更改,恕不另行通知。

此開發人員網站包含有關使用 Microsoft 開發工具和技術的資訊,以及有關最近和即將舉辦的會議的頭條新聞。 從此頁面中,您可以跳轉到許多相關的開發人員網站,包括 .NET 和 XML 開發人員中心。 您還可以下載測試版 SDK 和範例。

[萬維網聯盟 (W3C)](https://go.microsoft.com/fwlink/p/?linkid=37125)發布 HTML、HTTP、CGI 和其他萬維網技術的規範。

## <a name="more-internet-help"></a><a name="_core_more_internet_help"></a>更多網際網路說明

Windows SDK 的 OLE 部分包含有關 OLE 程式設計的其他資訊。 此資訊提供有關直接使用 Win32 WinInet 函數的詳細資訊,而不是透過 MFC 類。 它還包含有關互聯網技術的概述資訊。
