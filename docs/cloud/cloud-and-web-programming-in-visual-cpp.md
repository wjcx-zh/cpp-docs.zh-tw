---
title: 以 Visual C++ 進行雲端和 Web 程式設計
ms.date: 11/04/2016
ms.assetid: b63611f1-9723-44d0-ba7f-c3ebef341313
ms.openlocfilehash: 197d3d344d4be809c81f52f30e2462d35ebefbbe
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2018
ms.locfileid: "51519629"
---
# <a name="cloud-and-web-programming-in-visual-c"></a>以 Visual C++ 進行雲端和 Web 程式設計

在 C++ 中，您有數個選項可以連接到 Web 和雲端。

## <a name="cloud-programming-options"></a>雲端程式設計的選項

- [Windows Azure 行動服務](http://www.windowsazure.com/develop/mobile/)

  提供您可以使用通用 Windows 平台 (UWP) 應用程式或 Windows 桌面應用程式中，連接到 Windows Azure 行動服務的原生 Api。 雖然網站上的大部分範例是採用 C#，您也可以使用 C++。 如需詳細資訊，請參閱 [快速入門：使用 C++ 新增行動服務](https://msdn.microsoft.com/library/windows/apps/dn263181.aspx)。

- [C + + 的 Microsoft Azure 儲存體用戶端程式庫](https://blogs.msdn.microsoft.com/windowsazurestorage/2015/04/29/microsoft-azure-storage-client-library-for-c-v1-0-0-general-availability/)

  Azure Storage Client Library for c + + 提供完整的 API 使用 Azure 儲存體，包括但不是限於下列能力：

  - 建立、 讀取、 刪除及列出 blob 容器、 資料表和佇列。
  - 建立、 讀取、 刪除，加上的清單和複製 blob 的讀取和寫入 blob 範圍。
  - Insert、 delete、 replace、 合併及 Azure 資料表中的查詢實體。
  - 加入佇列，或將在 Azure 佇列的訊息。
  - 延遲列出容器、 blob、 資料表和佇列，並以延遲的方式查詢實體

- [OneDrive API](https://dev.onedrive.com/README.htm)

  OneDrive API 提供一組您應用程式連接到 Office 365 和 SharePoint Server 2016 中檔案和資料夾的 HTTP 服務。

- [C++ REST SDK (名稱代碼 "Casablanca")](https://github.com/Microsoft/cpprestsdk)

  提供現代化、 跨平台、 非同步 API 與 REST 服務互動。

  - 執行 REST 呼叫，針對任何 HTTP 伺服器，並內建支援 JSON 文件剖析和序列化
  - 支援 OAuth 1 和 2，包括本機重新導向的接聽程式
  - 建立 Websocket 連線針對遠端服務
  - PPL，包括內建的執行緒集區為基礎的 API 完全非同步工作

  支援 Windows Desktop （7 +）、 Windows Server （2012年 +）、 通用 Windows 平台、 Linux、 OSX、 Android 和 iOS。

- [Windows::Web::Http::HttpClient](https://msdn.microsoft.com/library/windows/apps/windows.web.http.httpclient.aspx)

  Windows 執行階段 HTTP 用戶端類別會在 System.Web 命名空間中相同名稱的 .NET Framework 類別上建立模型。 `HttpClient` 完全支援透過 HTTP 的非同步上傳和下載，以及可讓自訂 HTTP 處理常式插入管線的管線篩選器。 Windows SDK 包含計量網路、OAuth 驗證等等的範例篩選條件。 對於只有通用 Windows 平台為目標的應用程式，我們建議您使用`Windows::Web:HttpClient`類別。

- [IXMLHTTPRequest2 介面](/windows/desktop/api/msxml6/nn-msxml6-ixmlhttprequest2)

  提供您可以使用 Windows 執行階段應用程式或 Windows 桌面應用程式中，透過 HTTP 連線到網際網路，並發出 GET、 PUT 和其他 HTTP 命令的原生 COM 介面。 如需詳細資訊，請參閱 <<c0> [ 逐步解說： 使用工作和 XML HTTP 要求](../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md)。

- [Windows 網際網路 (WinInet)](/windows/desktop/WinInet/portal)

  您可以在 Windows 桌面應用程式中使用，以便連接到網際網路的 Windows 應用程式開發介面。

## <a name="see-also"></a>另請參閱

[Visual C++](../visual-cpp-in-visual-studio.md) <br/>
[網路和 web 服務](/windows/uwp/networking/)
