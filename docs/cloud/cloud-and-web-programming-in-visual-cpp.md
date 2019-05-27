---
title: 以 Visual C++ 進行雲端和 Web 程式設計
ms.date: 11/04/2016
ms.assetid: b63611f1-9723-44d0-ba7f-c3ebef341313
ms.openlocfilehash: 3d71e36b6209c693940f2ebe6b5e9c73bc0c9d9d
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65708034"
---
# <a name="cloud-and-web-programming-in-visual-c"></a>以 Visual C++ 進行雲端和 Web 程式設計

在 C++ 中，您有數個選項可以連接到 Web 和雲端。

## <a name="cloud-programming-options"></a>雲端程式設計選項

- [Windows Azure 行動服務](http://www.windowsazure.com/develop/mobile/)

  提供原生 API，可供您在「通用 Windows 平台」(UWP) 應用程式或 Windows 傳統型應用程式中使用，以連線至「Windows Azure 行動服務」。 雖然網站上的大部分範例是採用 C#，您也可以使用 C++。 如需詳細資訊，請參閱[快速入門：使用 C++ 來新增行動服務](https://msdn.microsoft.com/library/windows/apps/dn263181.aspx) \(英文\)。

- [適用於 C++ 的 Microsoft Azure 儲存體用戶端程式庫](https://blogs.msdn.microsoft.com/windowsazurestorage/2015/04/29/microsoft-azure-storage-client-library-for-c-v1-0-0-general-availability/) \(英文\)

  「適用於 C++ 的 Azure 儲存體用戶端程式庫」提供一個可搭配 Azure 儲存體運作的全方位的 API，其中包括但不限於下列功能：

  - 建立、讀取、刪除及列出 Blob 容器、資料表和佇列。
  - 建立、讀取、刪除、列出及複製 Blob，再加上讀取和寫入 Blob 範圍。
  - 插入、刪除、取代、合併及查詢 Azure 資料表中的實體。
  - 將訊息在 Azure 佇列中加入佇列和清除佇列。
  - 延遲列出容器、Blob、資料表和佇列，以及延遲查詢實體

- [OneDrive API](https://dev.onedrive.com/README.htm)

  OneDrive API 提供一組 HTTP 服務，可將您的應用程式連線至 Office 365 及 SharePoint Server 2016 中的檔案和資料夾。

- [C++ REST SDK (名稱代碼 "Casablanca")](https://github.com/Microsoft/cpprestsdk)

  提供一個新式、跨平台的非同步 API 來與 REST 服務進行互動。

  - 具有適用於 JSON 文件剖析和序列化的內建支援，可對任何 HTTP 伺服器執行 REST 呼叫
  - 支援 OAuth 1 和 2，包括本機重新導向接聽程式
  - 對遠端服務進行 WebSocket 連線
  - 以 PPL 為基礎的完全非同步工作 API，包括內建的執行緒集區

  支援 Windows Desktop (7+)、Windows Server (2012+)、通用 Windows 平台、Linux、OSX、Android 及 iOS。

- [Windows::Web::Http::HttpClient](/uwp/api/windows.web.http.httpclient)

  Windows 執行階段 HTTP 用戶端類別會在 System.Web 命名空間中相同名稱的 .NET Framework 類別上建立模型。 `HttpClient` 完全支援透過 HTTP 的非同步上傳和下載，以及可讓自訂 HTTP 處理常式插入管線的管線篩選器。 Windows SDK 包含計量網路、OAuth 驗證等等的範例篩選條件。 針對只以「通用 Windows 平台」為目標的應用程式，建議您使用 `Windows::Web:HttpClient` 類別。

- [IXMLHTTPRequest2 介面](/windows/desktop/api/msxml6/nn-msxml6-ixmlhttprequest2)

  提供一個原生 COM 介面，可供您在「Windows 執行階段」應用程式或 Windows 傳統型應用程式中使用，以透過 HTTP 連線至網際網路及發出 GET、PUT 和其他 HTTP 命令。 如需詳細資訊，請參閱[逐步解說：使用工作和 XML HTTP 要求來進行連線](../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md)。

- [Windows 網際網路 (WinInet)](/windows/desktop/WinInet/portal)

  您可以在 Windows 桌面應用程式中使用，以便連接到網際網路的 Windows 應用程式開發介面。

## <a name="see-also"></a>另請參閱

[Visual Studio 中的 C++](../overview/visual-cpp-in-visual-studio.md) <br/>
[網路和 Web 服務](/windows/uwp/networking/)
