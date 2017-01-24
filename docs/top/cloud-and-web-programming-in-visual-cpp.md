---
title: "以 Visual C++ 進行雲端和 Web 程式設計 | Microsoft Docs"
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
ms.assetid: b63611f1-9723-44d0-ba7f-c3ebef341313
caps.latest.revision: 13
caps.handback.revision: 13
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# 以 Visual C++ 進行雲端和 Web 程式設計
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在 C\+\+ 中，您有數個選項可以連接到 Web 和雲端。  
  
 [Windows Azure 行動服務](http://www.windowsazure.com/develop/mobile/)  
 提供您可以在 Windows 市集應用程式或 Windows 桌面應用程式中使用，以便連接到 Windows Azure 行動服務的原生應用程式開發介面。 雖然網站上的大部分範例是採用 C\#，您也可以使用 C\+\+。 如需詳細資訊，請參閱[快速入門：使用 C\+\+ 新增行動服務](http://msdn.microsoft.com/library/windows/apps/dn263181.aspx)。  
  
 [Live REST 介面](http://msdn.microsoft.com/library/live/hh243648.aspx)  
 提供您可以在 Windows 市集應用程式、Windows 桌面應用程式或 C\+\+ Linux 應用程式中使用，以便連接到 SkyDrive、Outlook.com 及 Skype 等 [Live](http://msdn.microsoft.com/live/ff519582) 服務的 REST 端點。 C\+\+ 應用程式會直接使用這些端點，而不是經過 Live SDK，它僅適用 .NET 應用程式。  
  
 [C\+\+ REST SDK \(Codename "Casablanca"\)](../top/cpp-rest-sdk-codename-casablanca.md)  
 提供專為跨平台相容性與在桌面應用程式中使用 \(回溯到 Windows 7 和 Windows Server 2012 作業系統\) 方便的非同步 HTTP 包裝函式方法。 您也可以在通用 Windows 平台應用程式中使用這些方法；不過，針對只以通用 Windows 平台為目標的應用程式，建議您使用 `Windows::Web:HttpClient` 類別。 C\+\+ REST SDK \(代號 "Casablanca"\) 也會提供支援 REST 呼叫並將 JSON 資料轉換成 C\+\+ 類型的協助程式類別。 您可以在 [CodePlex](http://casablanca.codeplex.com/) 上取得此 SDK，其中包含 [live\_connect.h](http://casablanca.codeplex.com/SourceControl/latest#Release/collateral/Samples/WindowsLiveAuth/live_connect.h) 等範例檔案，以提供用於連接到 [Live](http://msdn.microsoft.com/live/ff519582) 服務的協助程式方法。  
  
 [Windows::Web::Http::HttpClient](https://msdn.microsoft.com/en-us/library/windows/apps/windows.web.http.httpclient.aspx)  
 Windows 執行階段 HTTP 用戶端類別會在 System.Web 命名空間中相同名稱的 .NET Framework 類別上建立模型。`HttpClient` 完全支援透過 HTTP 的非同步上傳和下載，以及可讓自訂 HTTP 處理常式插入管線的管線篩選器。 Windows SDK 包含計量網路、OAuth 驗證等等的範例篩選條件。  
  
 [IXMLHTTPRequest2 介面](http://msdn.microsoft.com/library/windows/apps/hh831151.aspx)  
 提供您可以在 Windows 市集應用程式或 Windows 桌面應用程式中使用，以便透過 HTTP 連接到網際網路，並發出 GET、PUT 和其他 HTTP 命令的原生 COM 介面。 如需詳細資訊，請參閱[逐步解說：使用工作和 XML HTTP 要求連線](../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md)。  
  
 [Windows 網際網路 \(WinInet\)](http://msdn.microsoft.com/library/windows/desktop/aa385331\(v=vs.85\).aspx)  
 您可以在 Windows 桌面應用程式中使用，以便連接到網際網路的 Windows 應用程式開發介面。  
  
## 請參閱  
 [Visual C\+\+](../top/visual-cpp-in-visual-studio-2015.md)   
 [連線到網路和 Web 服務 \(使用 C\#\/VB\/C\+\+ 和 XAML 的 Windows 市集應用程式\)](http://msdn.microsoft.com/library/windows/apps/br229573.aspx)