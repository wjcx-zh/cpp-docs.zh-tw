---
title: "逐步解說： 使用工作和 XML HTTP 要求連線 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- connecting to web services, Windows Store apps [C++]
- IXMLHTTPRequest2 and tasks, example
- IXHR2 and tasks, example
ms.assetid: e8e12d46-604c-42a7-abfd-b1d1bb2ed6b3
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5fef2e682f8e2036eb2919c20879c60e879ec845
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="walkthrough-connecting-using-tasks-and-xml-http-requests"></a>逐步解說：使用工作和 XML HTTP 要求連線
這個範例示範如何使用[IXMLHTTPRequest2](http://msdn.microsoft.com/en-us/bbc11c4a-aecf-4d6d-8275-3e852e309908)和[IXMLHTTPRequest2Callback](http://msdn.microsoft.com/en-us/aa4b3f4c-6e28-458b-be25-6cce8865fc71)介面，以及將 HTTP GET 和 POST 要求傳送至 web 服務中的工作[!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)]應用程式。 將 `IXMLHTTPRequest2` 與工作結合之後，您就可以撰寫程式碼來撰寫其他工作。 例如，您可以使用下載工作做為工作鏈結的一部分。 當工作取消時，下載工作也可以回應。  
  
> [!TIP]
>  您也可以使用 C++ REST SDK，透過使用 C++ 應用程式從 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)]應用程式或從傳統型 C++ 應用程式執行 HTTP 要求。 如需詳細資訊，請參閱[c + + REST SDK （代號"Casablanca"）](https://github.com/Microsoft/cpprestsdk)。  
  
 如需工作的詳細資訊，請參閱[工作平行處理原則](../../parallel/concrt/task-parallelism-concurrency-runtime.md)。 如需有關如何使用中的工作[!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)]應用程式，請參閱[c + + 中的非同步程式設計](http://msdn.microsoft.com/en-us/512700b7-7863-44cc-93a2-366938052f31)和[c + + 為 Windows 市集應用程式建立非同步作業](../../parallel/concrt/creating-asynchronous-operations-in-cpp-for-windows-store-apps.md)。  
  
 本文件會先說明如何建立 `HttpRequest` 及其支援的類別。 接著會說明如何從使用 C++ 和 XAML 的 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)]應用程式中使用這個類別。  
  
 如需更完整的範例，其使用`HttpReader`類別描述在此文件，請參閱[開發 Bing Maps Trip Optimizer，JavaScript 和 c + + 中的 Windows 市集應用程式](http://msdn.microsoft.com/library/974cf025-de1a-4299-b7dd-c6c7bf0e5d30)。 如需使用的其他範例`IXMLHTTPRequest2`但不使用工作，請參閱[快速入門： 使用 XML HTTP 要求 (IXMLHTTPRequest2) 連線](http://msdn.microsoft.com/en-us/cc7aed53-b2c5-4d83-b85d-cff2f5ba7b35)。  
  
> [!TIP]
>  `IXMLHTTPRequest2` 和 `IXMLHTTPRequest2Callback` 是建議在 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)]應用程式中使用的介面。 您也可以調整這個範例，讓它能夠用於傳統型應用程式。  
  
## <a name="prerequisites"></a>必要條件  
  
## <a name="defining-the-httprequest-httprequestbufferscallback-and-httprequeststringcallback-classes"></a>定義 HttpRequest、HttpRequestBuffersCallback 和 HttpRequestStringCallback 類別  
 當您使用 `IXMLHTTPRequest2` 介面建立透過 HTTP 的 Web 要求時，您會實作 `IXMLHTTPRequest2Callback` 介面來接收伺服器回應及回應其他事件。 這個範例會定義 `HttpRequest` 類別用於建立 Web 要求，以及定義 `HttpRequestBuffersCallback` 和 `HttpRequestStringCallback` 類別用於處理回應。 `HttpRequestBuffersCallback` 和 `HttpRequestStringCallback` 類別支援 `HttpRequest` 類別，不過您只會在應用程式程式碼中處理 `HttpRequest` 類別。  
  
 `GetAsync` 類別的 `PostAsync` 和 `HttpRequest` 方法可讓您分別啟動 HTTP GET 和 POST 作業。 這些方法會使用 `HttpRequestStringCallback` 類別讀取字串形式的伺服器回應。 `SendAsync` 和 `ReadAsync` 方法可讓您將大型內容區塊串流在一起。 這些方法都會傳回[concurrency:: task](../../parallel/concrt/reference/task-class.md)代表作業。 `GetAsync` 和 `PostAsync` 方法會產生 `task<std::wstring>` 值，而 `wstring` 組件則表示伺服器的回應。 `SendAsync` 和 `ReadAsync` 方法會產生 `task<void>` 值，這些工作會在傳送及讀取作業完成時完成。  
  
 因為`IXMLHTTPRequest2`介面是以非同步方式執行，此範例會使用[concurrency:: task_completion_event](../../parallel/concrt/reference/task-completion-event-class.md)建立在回呼物件完成或取消下載作業之後完成的工作。 `HttpRequest` 類別會從這個工作建立工作為主的接續，以設定最終結果。 `HttpRequest` 類別會使用工作為主的接續，確保前一項工作產生錯誤或取消時，接續工作仍會執行。 如需以工作為基礎的接續的詳細資訊，請參閱[工作平行處理原則](../../parallel/concrt/task-parallelism-concurrency-runtime.md)  
  
 為了支援取消，`HttpRequest`、`HttpRequestBuffersCallback` 和 `HttpRequestStringCallback` 類別會使用取消語彙基元。 `HttpRequestBuffersCallback`和`HttpRequestStringCallback`類別會使用[concurrency::cancellation_token::register_callback](reference/cancellation-token-class.md#register_callback)方法讓工作完成事件回應取消。 這個取消收回呼會中止下載。 如需取消的詳細資訊，請參閱[取消](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md#cancellation)。  
  
#### <a name="to-define-the-httprequest-class"></a>若要定義 HttpRequest 類別  
  
1.  使用 Visual c + +**空白應用程式 (XAML)**範本來建立空白 XAML 應用程式專案。 這個範例會將專案命名為 `UsingIXMLHTTPRequest2`。  
  
2.  在專案中加入名為 HttpRequest.h 的標頭檔和名為 HttpRequest.cpp 的原始程式檔。  
  
3.  在 pch.h 中加入下列程式碼：  
  
     [!code-cpp[concrt-using-ixhr2#1](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_1.h)]  
  
4.  在 HttpRequest.h 中加入下列程式碼：  
  
     [!code-cpp[concrt-using-ixhr2#2](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_2.h)]  
  
5.  在 HttpRequest.cpp 中加入下列程式碼：  
  
     [!code-cpp[concrt-using-ixhr2#3](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_3.cpp)]  
  
## <a name="using-the-httprequest-class-in-a-includewin8appnamelongbuildincludeswin8appnamelongmdmd-app"></a>在 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 應用程式中使用 HttpRequest 類別  
 本結將示範如何在 `HttpRequest`應用程式中使用 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 類別。 應用程式提供了定義 URL 資源的輸入方塊、執行 GET 和 POST 作業的按鈕命令，以及取消目前作業的按鈕命令。  
  
#### <a name="to-use-the-httprequest-class"></a>若要使用 HttpRequest 類別  
  
1.  在 MainPage.xaml 中，定義[StackPanel](http://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.stackpanel.aspx)項目，如下所示。  
  
     [!code-xml[concrt-using-ixhr2#A1](../../parallel/concrt/codesnippet/xaml/walkthrough-connecting-using-tasks-and-xml-http-requests_4.xaml)]  
  
2.  在 MainPage.xaml.h 中加入這個 `#include` 指示詞：  
  
     [!code-cpp[concrt-using-ixhr2#A2](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_5.h)]  
  
3.  在 MainPage.xaml.h 中，將這些 `private` 成員變數加入至 `MainPage` 類別：  
  
     [!code-cpp[concrt-using-ixhr2#A3](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_6.h)]  
  
4.  在 MainPage.xaml.h 中宣告 `private` 方法 `ProcessHttpRequest`：  
  
     [!code-cpp[concrt-using-ixhr2#A4](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_7.h)]  
  
5.  在 MainPage.xaml.cpp 中加入下列 `using` 陳述式：  
  
     [!code-cpp[concrt-using-ixhr2#A5](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_8.cpp)]  
  
6.  在 MainPage.xaml.cpp 中實作 `GetButton_Click` 類別的 `PostButton_Click`、`CancelButton_Click` 和 `MainPage` 方法。  
  
     [!code-cpp[concrt-using-ixhr2#A6](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_9.cpp)]  
  
    > [!TIP]


    >  如果您的應用程式不需要支援取消，則傳遞[concurrency:: cancellation_token:: none](reference/cancellation-token-class.md#none)至`HttpRequest::GetAsync`和`HttpRequest::PostAsync`方法。  


  
7.  在 MainPage.xaml.cpp 中實作 `MainPage::ProcessHttpRequest` 方法。  
  
     [!code-cpp[concrt-using-ixhr2#A7](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_10.cpp)]  
  
8.  在專案屬性中，在**連結器**，**輸入**，指定`shcore.lib`和`msxml6.lib`。  
  
 執行的應用程式如下：  
  
 ![執行 Windows 市集應用程式](../../parallel/concrt/media/concrt_usingixhr2.png "concrt_usingixhr2")  
  
## <a name="next-steps"></a>後續步驟  
 [並行執行階段逐步解說](../../parallel/concrt/concurrency-runtime-walkthroughs.md)  
  
## <a name="see-also"></a>請參閱  
 [工作平行處理原則](../../parallel/concrt/task-parallelism-concurrency-runtime.md)   
 [PPL 中的取消](cancellation-in-the-ppl.md)   
 [C + + 中的非同步程式設計](http://msdn.microsoft.com/en-us/512700b7-7863-44cc-93a2-366938052f31)   
 [C + + 中建立非同步作業的 Windows 市集應用程式](../../parallel/concrt/creating-asynchronous-operations-in-cpp-for-windows-store-apps.md)   
 [使用 XML HTTP 要求 (IXMLHTTPRequest2) 連線的快速入門：](http://msdn.microsoft.com/en-us/cc7aed53-b2c5-4d83-b85d-cff2f5ba7b35)   
 [task 類別 （並行執行階段）](../../parallel/concrt/reference/task-class.md)   
 [task_completion_event 類別](../../parallel/concrt/reference/task-completion-event-class.md)
