---
title: 以 Visual C++ 進行雲端和 Web 程式設計
ms.date: 05/14/2019
ms.assetid: b63611f1-9723-44d0-ba7f-c3ebef341313
ms.topic: overview
ms.openlocfilehash: 675502e9ae50c9e69ad4555502000d128d5d4cbe
ms.sourcegitcommit: efc8c32205c9d610f40597556273a64306dec15d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/26/2020
ms.locfileid: "88898675"
---
# <a name="cloud-and-web-programming-in-visual-c"></a>以 Visual C++ 進行雲端和 Web 程式設計

在 C++ 中，您有數個選項可以連接到 Web 和雲端。

## <a name="microsoft-azure-sdks-and-rest-services"></a>Microsoft Azure SDK 與 REST 服務

- [Microsoft Azure Storage Client Library for C++](https://azure.github.io/azure-storage-cpp/) \(英文\)

  「適用於 C++ 的 Azure 儲存體用戶端程式庫」提供一個可搭配 Azure 儲存體運作的全方位的 API，其中包括但不限於下列功能：

  - 建立、讀取、刪除及列出 Blob 容器、資料表和佇列。
  - 建立、讀取、刪除、列出及複製 Blob，再加上讀取和寫入 Blob 範圍。
  - 插入、刪除、取代、合併及查詢 Azure 資料表中的實體。
  - 將訊息在 Azure 佇列中加入佇列和清除佇列。
  - 延遲列出容器、Blob、資料表和佇列，以及延遲查詢實體

- 適用於物聯網的 ANSI C99 [Azure IoT 中樞 SDK](/azure/iot-hub/iot-hub-devguide-sdks) 可讓 IoT 應用程式在裝置或後端上執行。

- [Microsoft Graph 中的 OneDrive 與 SharePoint](https://dev.onedrive.com/README.htm)

  OneDrive API 提供一組 HTTP 服務，可將您的應用程式連接到 Microsoft 365 和 SharePoint Server 2016 中的檔案和資料夾。

## <a name="windows-and-cross-platform-networking-apis"></a>Windows 與跨平台網路 API

- [C++ REST SDK (代號 "Casablanca")](https://github.com/Microsoft/cpprestsdk)

  提供一個新式、跨平台的非同步 API 來與 REST 服務進行互動。

  - 具有適用於 JSON 文件剖析和序列化的內建支援，可對任何 HTTP 伺服器執行 REST 呼叫
  - 支援 OAuth 1 和 2，包括本機重新導向接聽程式
  - 對遠端服務進行 WebSocket 連線
  - 以 PPL 為基礎的完全非同步工作 API，包括內建的執行緒集區

  支援 Windows Desktop (7+)、Windows Server (2012+)、通用 Windows 平台、Linux、OSX、Android 及 iOS。

- [Windows::Web::Http::HttpClient](/uwp/api/windows.web.http.httpclient)

  Windows 執行階段 HTTP 用戶端類別會在 System.Web 命名空間中相同名稱的 .NET Framework 類別上建立模型。 `HttpClient` 完全支援透過 HTTP 的非同步上傳和下載，以及可讓自訂 HTTP 處理常式插入管線的管線篩選器。 Windows SDK 包含計量網路、OAuth 驗證等等的範例篩選條件。 針對只以「通用 Windows 平台」為目標的應用程式，建議您使用 `Windows::Web:HttpClient` 類別。

- [IXMLHTTPRequest2 介面](/windows/win32/api/msxml6/nn-msxml6-ixmlhttprequest2)

  提供一個原生 COM 介面，可供您在「Windows 執行階段」應用程式或 Windows 傳統型應用程式中使用，以透過 HTTP 連線至網際網路及發出 GET、PUT 和其他 HTTP 命令。 如需詳細資訊，請參閱 [逐步解說：使用工作和 XML HTTP 要求進行連接](../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md)。

- [Windows 網際網路 (WinInet)](/windows/win32/WinInet/portal)

  您可以在 Windows 桌面應用程式中使用，以便連接到網際網路的 Windows 應用程式開發介面。

## <a name="see-also"></a>請參閱

[Visual Studio 中的 C++](../overview/visual-cpp-in-visual-studio.md) <br/>
[Microsoft Azure C 和 C++ 開發人員中心](https://azure.microsoft.com/develop/cpp/) <br/>
[網路和 Web 服務 (UWP)](/windows/uwp/networking/)
