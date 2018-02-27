---
title: "雲端和 Web 程式設計，Visual c + + |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-azure
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: b63611f1-9723-44d0-ba7f-c3ebef341313
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8c04939aea508afed60b32ae51d627a1f5d902fd
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="cloud-and-web-programming-in-visual-c"></a>以 Visual C++ 進行雲端和 Web 程式設計
在 C++ 中，您有數個選項可以連接到 Web 和雲端。  
  
 [Windows Azure 行動服務](http://www.windowsazure.com/develop/mobile/)  
 提供您可以使用通用 Windows 平台 (UWP) 應用程式或 Windows 桌面應用程式中，連接到 Windows Azure Mobile Services 的原生 Api。 雖然網站上的大部分範例是採用 C#，您也可以使用 C++。 如需詳細資訊，請參閱 [快速入門：使用 C++ 新增行動服務](http://msdn.microsoft.com/library/windows/apps/dn263181.aspx)。  

 [C + + 的 Microsoft Azure 儲存體用戶端程式庫](https://blogs.msdn.microsoft.com/windowsazurestorage/2015/04/29/microsoft-azure-storage-client-library-for-c-v1-0-0-general-availability/)  
 C + + 的 Azure 儲存體用戶端程式庫提供完整的 API 來使用 Azure 儲存體，包括但不是限於下列功能：

- 建立、 讀取、 刪除及列出 blob 容器、 資料表和佇列。
- 建立、 讀取、 刪除，加上的清單和複製 blob 的讀取和寫入 blob 範圍。
- Insert、 delete、 取代、 合併和在 Azure 資料表查詢實體。
- 佇列和 Azure 佇列中的訊息清除佇列。
- 延遲的方式列出容器、 blob、 資料表和佇列，並延遲查詢實體

[OneDrive API](https://dev.onedrive.com/README.htm)  
 OneDrive 應用程式開發介面提供一組您應用程式連接到 Office 365 和 SharePoint Server 2016 中檔案和資料夾的 HTTP 服務。

[C++ REST SDK (名稱代碼 "Casablanca")](https://github.com/Microsoft/cpprestsdk)  
提供現代、 跨平台、 非同步 API 互動 REST 服務。

-   執行對任何 HTTP 伺服器，使用內建的 JSON 文件剖析和序列化支援 REST 呼叫
-   支援 OAuth 1 和 2，包括本機的重新導向接聽程式
-   請針對遠端服務的 Websocket 連線
-   完全非同步工作 PPL，包括內建的執行緒集區為基礎的應用程式開發介面

（7 +） 的 Windows 桌面、 Windows Server （2012年 +）、 通用 Windows 平台、 Linux、 OSX、 Android 和 iOS 支援。 
  
[Windows::Web::Http::HttpClient](https://msdn.microsoft.com/en-us/library/windows/apps/windows.web.http.httpclient.aspx)  
 Windows 執行階段 HTTP 用戶端類別會在 System.Web 命名空間中相同名稱的 .NET Framework 類別上建立模型。 `HttpClient` 完全支援透過 HTTP 的非同步上傳和下載，以及可讓自訂 HTTP 處理常式插入管線的管線篩選器。 Windows SDK 包含計量網路、OAuth 驗證等等的範例篩選條件。 針對只通用 Windows 平台為目標的應用程式，我們建議您使用`Windows::Web:HttpClient`類別。 
  
[IXMLHTTPRequest2 介面](http://msdn.microsoft.com/library/windows/apps/hh831151.aspx)  
 提供您可以使用 Windows 執行階段應用程式或 Windows 桌面應用程式，以便透過 HTTP 連接到網際網路，並發出 GET、 PUT 和其他 HTTP 命令的原生 COM 介面。 如需詳細資訊，請參閱[逐步解說： 使用工作和 XML HTTP 要求](../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md)。  
  
[Windows 網際網路 (WinInet)](http://msdn.microsoft.com/library/windows/desktop/aa385331\(v=vs.85\).aspx)  
 您可以在 Windows 桌面應用程式中使用，以便連接到網際網路的 Windows 應用程式開發介面。  
  
## <a name="see-also"></a>請參閱  
 [Visual c + +](../visual-cpp-in-visual-studio.md)   
 [網路和 web 服務](/windows/uwp/networking/)