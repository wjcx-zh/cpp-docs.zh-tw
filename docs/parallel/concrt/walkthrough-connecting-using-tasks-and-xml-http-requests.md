---
title: "逐步解說：使用工作和 XML HTTP 要求連線 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
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
  - "連接到 Web 服務，Windows 市集應用程式 [C++]"
  - "IXMLHTTPRequest2 和工作，範例"
  - "IXHR2 和工作，範例"
ms.assetid: e8e12d46-604c-42a7-abfd-b1d1bb2ed6b3
caps.latest.revision: 16
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 逐步解說：使用工作和 XML HTTP 要求連線
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此範例說明如何在 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)]應用程式中使用 [IXMLHTTPRequest2](http://msdn.microsoft.com/zh-tw/bbc11c4a-aecf-4d6d-8275-3e852e309908) 和 [IXMLHTTPRequest2Callback](http://msdn.microsoft.com/zh-tw/aa4b3f4c-6e28-458b-be25-6cce8865fc71) 介面，以及將 HTTP GET 和 POST 要求傳送至 Web 服務的工作。  透過結合處理工作的 `IXMLHTTPRequest2` ，您可以撰寫程式碼與其他工作的撰寫。  例如，您可以使用鏈結下載為工作的一部分。  當工作取消時，下載工作也可以回應。  
  
> [!TIP]
>  您也可以使用 C\+\+ REST SDK 執行 HTTP 要求，從 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 應用程式使用 C\+\+ 應用程式或從桌上型電腦 C\+\+ 應用程式。  如需詳細資訊，請參閱 [C\+\+ REST SDK \(Codename "Casablanca"\)](../../top/cpp-rest-sdk-codename-casablanca.md)。  
  
 如需工作的詳細資訊，請參閱 [工作平行處理原則](../../parallel/concrt/task-parallelism-concurrency-runtime.md)。  如需有關如何在 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)]應用程式中使用任務的詳細資訊，請參閱[Asynchronous programming in C\+\+](http://msdn.microsoft.com/zh-tw/512700b7-7863-44cc-93a2-366938052f31)與[使用 C\+\+ 為 Windows 市集應用程式建立非同步作業](../../parallel/concrt/creating-asynchronous-operations-in-cpp-for-windows-store-apps.md)。  
  
 文件會先顯示如何建立 `HttpRequest` 及其支援類別。  接著會顯示如何使用 C\+\+ 和使用 XAML 的 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 應用程式的類別。  
  
 對於使用 `HttpReader` 類別的更完整的範例文件中的說明，請參閱 [以 JavaScript 和 C\+\+ 開發使用 Bing 地圖服務路線最佳化程式這個 Windows 市集應用程式](../Topic/Developing%20Bing%20Maps%20Trip%20Optimizer,%20a%20Windows%20Store%20app%20in%20JavaScript%20and%20C++.md)。  如需使用 `IXMLHTTPRequest2` ，但不使用工作的其他範例，請參閱 [Quickstart: Connecting using XML HTTP Request \(IXMLHTTPRequest2\)](http://msdn.microsoft.com/zh-tw/cc7aed53-b2c5-4d83-b85d-cff2f5ba7b35)。  
  
> [!TIP]
>  `IXMLHTTPRequest2` 和 `IXMLHTTPRequest2Callback` 是建議用於 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 應用程式的介面。  您也可以調整這個範例來使用桌面應用程式。  
  
## 必要條件  
  
## 定義 HttpRequest、HttpRequestBuffersCallback 和 HttpRequestStringCallback 類別  
 當您使用 `IXMLHTTPRequest2` 介面以在 HTTP 中建立 Web 要求，您實作 `IXMLHTTPRequest2Callback` 介面接收伺服器回應和回應其他事件。  這個範例會定義 `HttpRequest` 類別建立 Web 要求和 `HttpRequestBuffersCallback` 和 `HttpRequestStringCallback` 類別處理回應。  `HttpRequestBuffersCallback` 和 `HttpRequestStringCallback` 類別不支援 `HttpRequest` 類別;您只能從應用程式程式碼的 `HttpRequest` 類別一起使用。  
  
 `GetAsync`， `HttpRequest` 類別的 `PostAsync` 方法可讓您分別啟動 HTTP GET 和 POST 作業。  這些方法會使用 `HttpRequestStringCallback` 類別來讀取伺服器回應為字串。  `SendAsync` 和 `ReadAsync` 方法可讓您在資料流區塊的主要內容。  這些方法都會傳回表示運算的 [concurrency::task](../../parallel/concrt/reference/task-class-concurrency-runtime.md) 。  `GetAsync` 和 `PostAsync` 方法所產生的 `task<std::wstring>` 值， `wstring` 組件代表伺服器的回應。  `SendAsync` 和 `ReadAsync` 方法產生 `task<void>` 值;當傳送及讀取作業完成，這些工作完成。  
  
 因為 `IXMLHTTPRequest2` 介面以非同步方式行動，這個範例回呼物件完成或取消下載作業之後，使用 [concurrency::task\_completion\_event](../../parallel/concrt/reference/task-completion-event-class.md) 來建立完成的工作。  `HttpRequest` 類別會建立從這個工作到最終結果\(以工作基底的接續\)。  `HttpRequest` 類別使用以工作為基底的接續來確保接續工作執行，即使前一個工作會產生錯誤或已取消。  如需工作基底接續的詳細資訊，請參閱 [工作平行處理原則](../../parallel/concrt/task-parallelism-concurrency-runtime.md)。  
  
 若要支援取消作業， `HttpRequest`、 `HttpRequestBuffersCallback`和 `HttpRequestStringCallback` 類別使用取消語彙基元。  `HttpRequestBuffersCallback` 和 `HttpRequestStringCallback` 類別使用 [concurrency::cancellation\_token::register\_callback](../Topic/cancellation_token::register_callback%20Method.md) 方法可讓工作完成事件回應取消。  此取消收回中止下載。  如需取消的詳細資訊，請參閱 [取消](../../parallel/concrt/cancellation-in-the-ppl.md)。  
  
#### 若要定義 HttpRequest 類別  
  
1.  使用 Visual C\+\+ 的**空白應用程式 \(XAML\)**範本建立空白 XAML 應用程式專案。  這個範例將專案命名為 `UsingIXMLHTTPRequest2`。  
  
2.  在專案中加入名為 HttpRequest.h 和原始程式檔名為 HttpRequest.cpp 的標頭檔。  
  
3.  在 pch.h中加入此程式碼:  
  
     [!CODE [concrt-using-IXMLHTTPRequest2#1](concrt-using-IXMLHTTPRequest2#1)]  
  
4.  在 HttpRequest.h中，加入此程式碼:  
  
     [!CODE [concrt-using-IXMLHTTPRequest2#2](concrt-using-IXMLHTTPRequest2#2)]  
  
5.  在 HttpRequest.cpp中，加入此程式碼:  
  
     [!CODE [concrt-using-IXMLHTTPRequest2#3](concrt-using-IXMLHTTPRequest2#3)]  
  
## 在 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 應用程式中使用 HttpRequest 類別  
 這個部分在 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 應用程式中示範如何使用 `HttpRequest` 類別。  應用程式提供定義 URL 資源的輸入方塊，執行 GET 和 POST 作業的按鈕命令和取消目前作業的按鈕命令。  
  
#### 若要使用 HttpRequest 類別  
  
1.  在 MainPage.xaml，如下定義項目 [StackPanel](http://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.stackpanel.aspx) 。  
  
     [!CODE [concrt-using-IXMLHTTPRequest2#A1](concrt-using-IXMLHTTPRequest2#A1)]  
  
2.  在 MainPage.xaml.h，請將這個 `#include` 指示詞:  
  
     [!CODE [concrt-using-IXMLHTTPRequest2#A2](concrt-using-IXMLHTTPRequest2#A2)]  
  
3.  在 MainPage.xaml.h，將這些 `private` 成員變數加入至 `MainPage` 類別:  
  
     [!CODE [concrt-using-IXMLHTTPRequest2#A3](concrt-using-IXMLHTTPRequest2#A3)]  
  
4.  在 MainPage.xaml.h，宣告 `private` `ProcessHttpRequest`方法:  
  
     [!CODE [concrt-using-IXMLHTTPRequest2#A4](concrt-using-IXMLHTTPRequest2#A4)]  
  
5.  在 MainPage.xaml.cpp，請將下列 `using` 陳述式:  
  
     [!CODE [concrt-using-IXMLHTTPRequest2#A5](concrt-using-IXMLHTTPRequest2#A5)]  
  
6.  在 MainPage.xaml.cpp，請實作 `GetButton_Click`， `PostButton_Click`， `MainPage` ，以及 `CancelButton_Click` 的方法。  
  
     [!CODE [concrt-using-IXMLHTTPRequest2#A6](concrt-using-IXMLHTTPRequest2#A6)]  
  
    > [!TIP]
    >  如果您的應用程式沒有要求取消支援，傳遞 [concurrency::cancellation\_token::none](../Topic/cancellation_token::none%20Method.md) 到 `HttpRequest::GetAsync` 和 `HttpRequest::PostAsync` 方法。  
  
7.  在 MainPage.xaml.cpp，實作 `MainPage::ProcessHttpRequest` 方法。  
  
     [!CODE [concrt-using-IXMLHTTPRequest2#A7](concrt-using-IXMLHTTPRequest2#A7)]  
  
8.  在專案屬性中，**連結器**下，**輸入**，指定 `shcore.lib` 和 `msxml6.lib`。  
  
 這個執行中的應用程式:  
  
 ![正在執行的 Windows 市集應用程式](../../parallel/concrt/media/concrt_usingixhr2.png "ConcRT\_UsingIXHR2")  
  
## 後續步驟  
 [並行執行階段逐步解說](../../parallel/concrt/concurrency-runtime-walkthroughs.md)  
  
## 請參閱  
 [工作平行處理原則](../../parallel/concrt/task-parallelism-concurrency-runtime.md)   
 [取消](../../parallel/concrt/cancellation-in-the-ppl.md)   
 [Asynchronous programming in C\+\+](http://msdn.microsoft.com/zh-tw/512700b7-7863-44cc-93a2-366938052f31)   
 [使用 C\+\+ 為 Windows 市集應用程式建立非同步作業](../../parallel/concrt/creating-asynchronous-operations-in-cpp-for-windows-store-apps.md)   
 [Quickstart: Connecting using XML HTTP Request \(IXMLHTTPRequest2\)](http://msdn.microsoft.com/zh-tw/cc7aed53-b2c5-4d83-b85d-cff2f5ba7b35)   
 [task 類別 \(並行執行階段\)](../../parallel/concrt/reference/task-class-concurrency-runtime.md)   
 [task\_completion\_event 類別](../../parallel/concrt/reference/task-completion-event-class.md)   
 [IXMLHTTPRequest2](http://msdn.microsoft.com/zh-tw/bbc11c4a-aecf-4d6d-8275-3e852e309908)   
 [IXMLHTTPRequest2Callback](http://msdn.microsoft.com/zh-tw/aa4b3f4c-6e28-458b-be25-6cce8865fc71)