---
title: 逐步解說：使用工作和 XML HTTP 要求連線
ms.date: 04/25/2019
helpviewer_keywords:
- connecting to web services, UWP apps [C++]
- IXMLHTTPRequest2 and tasks, example
- IXHR2 and tasks, example
ms.assetid: e8e12d46-604c-42a7-abfd-b1d1bb2ed6b3
ms.openlocfilehash: 2c627a543ec18702bf5358ff0170bec177fd7497
ms.sourcegitcommit: 89d9e1cb08fa872483d1cde98bc2a7c870e505e9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "82032261"
---
# <a name="walkthrough-connecting-using-tasks-and-xml-http-requests"></a>逐步解說：使用工作和 XML HTTP 要求連線

此示例展示如何使用[IXMLHTTPRequest2](/windows/win32/api/msxml6/nn-msxml6-ixmlhttprequest2)和[IXMLHTTPRequest2 回檔](/windows/win32/api/msxml6/nn-msxml6-ixmlhttprequest2callback)介面以及向通用 Windows 平臺 (UWP) 應用中的 Web 服務發送 HTTP GET 和 POST 請求的任務。 將 `IXMLHTTPRequest2` 與工作結合之後，您就可以撰寫程式碼來撰寫其他工作。 例如，您可以使用下載工作做為工作鏈結的一部分。 當工作取消時，下載工作也可以回應。

> [!TIP]
> 您還可以使用 REST SDK C++使用 C++應用或桌面 C++應用執行來自 UWP 應用的 HTTP 請求。 有關詳細資訊,請參閱[C++ REST SDK(代號"卡薩布蘭卡")](https://github.com/Microsoft/cpprestsdk)。

有關工作的詳細資訊,請參閱[工作並行性](../../parallel/concrt/task-parallelism-concurrency-runtime.md)。 有關如何在 UWP 應用中使用任務的詳細資訊,請參閱[C++中的非同步程式設計](/windows/uwp/threading-async/asynchronous-programming-in-cpp-universal-windows-platform-apps),以及為[UWP 應用在 C++建立非同步操作](../../parallel/concrt/creating-asynchronous-operations-in-cpp-for-windows-store-apps.md)。

本文件會先說明如何建立 `HttpRequest` 及其支援的類別。 然後,它演示如何使用C++和 XAML 的 UWP 應用使用此類。

有關使用`IXMLHTTPRequest2`但不使用工作的範例,請參考[快速入門:使用 XML HTTP 請求 (IXMLHTTPRequest2) 連接](/previous-versions/windows/apps/hh770550\(v=win.10\))。

> [!TIP]
> `IXMLHTTPRequest2`是`IXMLHTTPRequest2Callback`我們建議在 UWP 應用中使用的介面。 您也可以調整這個範例，讓它能夠用於傳統型應用程式。

## <a name="prerequisites"></a>先決條件

UWP 支援在 Visual Studio 2017 及更高版本中是可選的。 要安裝它,請從 Windows "開始"功能表打開視覺化工作室安裝程式,然後選擇正在使用的 Visual Studio 版本。 按下 **「修改」** 按鈕,確保選中**UWP 開發**磁貼。 在 **「選擇元件**」 下,請確保**選擇C++ UWP 工具**。 將 v141 用於 Visual Studio 2017 或 v142,用於 Visual Studio 2019。

## <a name="defining-the-httprequest-httprequestbufferscallback-and-httprequeststringcallback-classes"></a>定義 HttpRequest、HttpRequestBuffersCallback 和 HttpRequestStringCallback 類別

當您使用 `IXMLHTTPRequest2` 介面建立透過 HTTP 的 Web 要求時，您會實作 `IXMLHTTPRequest2Callback` 介面來接收伺服器回應及回應其他事件。 這個範例會定義 `HttpRequest` 類別用於建立 Web 要求，以及定義 `HttpRequestBuffersCallback` 和 `HttpRequestStringCallback` 類別用於處理回應。 `HttpRequestBuffersCallback` 和 `HttpRequestStringCallback` 類別支援 `HttpRequest` 類別，不過您只會在應用程式程式碼中處理 `HttpRequest` 類別。

`GetAsync` 類別的 `PostAsync` 和 `HttpRequest` 方法可讓您分別啟動 HTTP GET 和 POST 作業。 這些方法會使用 `HttpRequestStringCallback` 類別讀取字串形式的伺服器回應。 `SendAsync` 和 `ReadAsync` 方法可讓您將大型內容區塊串流在一起。 這些方法各返回[併發::任務](../../parallel/concrt/reference/task-class.md)表示操作。 `GetAsync` 和 `PostAsync` 方法會產生 `task<std::wstring>` 值，而 `wstring` 組件則表示伺服器的回應。 `SendAsync` 和 `ReadAsync` 方法會產生 `task<void>` 值，這些工作會在傳送及讀取作業完成時完成。

由於`IXMLHTTPRequest2`介面以異步方式操作,因此此示例使用[併發::task_completion_event](../../parallel/concrt/reference/task-completion-event-class.md)創建在回調物件完成或取消下載操作後完成的任務。 `HttpRequest` 類別會從這個工作建立工作為主的接續，以設定最終結果。 `HttpRequest` 類別會使用工作為主的接續，確保前一項工作產生錯誤或取消時，接續工作仍會執行。 有關基於任務的延續的詳細資訊,請參閱[任務並行性](../../parallel/concrt/task-parallelism-concurrency-runtime.md)

為了支援取消，`HttpRequest`、`HttpRequestBuffersCallback` 和 `HttpRequestStringCallback` 類別會使用取消語彙基元。 和 類使用[併發::cancellation_token:register_callback](reference/cancellation-token-class.md#register_callback)方法使任務完成事件能夠回應`HttpRequestStringCallback``HttpRequestBuffersCallback`取消。 這個取消收回呼會中止下載。 有關取消的詳細資訊,請參閱[取消](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md#cancellation)。

### <a name="to-define-the-httprequest-class"></a>若要定義 HttpRequest 類別

1. 從主選單中,選擇 **「檔** > **新專案** > **」。。**

1. 使用C++**空白應用(通用 Windows)** 範本建立空 XAML 應用專案。 這個範例會將專案命名為 `UsingIXMLHTTPRequest2`。

1. 在專案中加入名為 HttpRequest.h 的標頭檔和名為 HttpRequest.cpp 的原始程式檔。

1. 在 pch.h 中加入下列程式碼：

   [!code-cpp[concrt-using-ixhr2#1](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_1.h)]

1. 在 HttpRequest.h 中加入下列程式碼：

   [!code-cpp[concrt-using-ixhr2#2](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_2.h)]

1. 在 HttpRequest.cpp 中加入下列程式碼：

   [!code-cpp[concrt-using-ixhr2#3](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_3.cpp)]

## <a name="using-the-httprequest-class-in-a-uwp-app"></a>在 UWP 應用程式中使用 HTTPRequest 類別

本節演示如何在`HttpRequest`UWP 應用中使用類。 應用程式提供了定義 URL 資源的輸入方塊、執行 GET 和 POST 作業的按鈕命令，以及取消目前作業的按鈕命令。

### <a name="to-use-the-httprequest-class"></a>若要使用 HttpRequest 類別

1. 在 MainPage.xaml 中,定義[堆疊面板](/uwp/api/windows.ui.xaml.controls.stackpanel)元素,如下所示。

   [!code-xml[concrt-using-ixhr2#A1](../../parallel/concrt/codesnippet/xaml/walkthrough-connecting-using-tasks-and-xml-http-requests_4.xaml)]

1. 在 MainPage.xaml.h 中加入這個 `#include` 指示詞：

   [!code-cpp[concrt-using-ixhr2#A2](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_5.h)]

1. 在 MainPage.xaml.h 中，將這些 `private` 成員變數加入至 `MainPage` 類別：

   [!code-cpp[concrt-using-ixhr2#A3](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_6.h)]

1. 在 MainPage.xaml.h 中宣告 `private` 方法 `ProcessHttpRequest`：

   [!code-cpp[concrt-using-ixhr2#A4](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_7.h)]

1. 在 MainPage.xaml.cpp 中加入下列 `using` 陳述式：

   [!code-cpp[concrt-using-ixhr2#A5](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_8.cpp)]

1. 在 MainPage.xaml.cpp 中實作 `GetButton_Click` 類別的 `PostButton_Click`、`CancelButton_Click` 和 `MainPage` 方法。

   [!code-cpp[concrt-using-ixhr2#A6](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_9.cpp)]

   > [!TIP]
   > 如果應用不需要取消支援,請傳遞[併發:cancellation_token:::無](reference/cancellation-token-class.md#none)`HttpRequest::GetAsync`到`HttpRequest::PostAsync`和 方法 。

1. 在 MainPage.xaml.cpp 中實作 `MainPage::ProcessHttpRequest` 方法。

   [!code-cpp[concrt-using-ixhr2#A7](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_10.cpp)]

1. 在項目屬性中,在**連結器**下 **,輸入**,`shcore.lib`請`msxml6.lib`指定與 。

執行的應用程式如下：

![執行的 Windows 執行時套用](../../parallel/concrt/media/concrt_usingixhr2.png "執行的 Windows 執行時套用")

## <a name="next-steps"></a>後續步驟

[併發運行時演練](../../parallel/concrt/concurrency-runtime-walkthroughs.md)

## <a name="see-also"></a>另請參閱

[工作平行](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br/>
[PPL 中的取消](cancellation-in-the-ppl.md)<br/>
[C++中的非同步程式設計](/windows/uwp/threading-async/asynchronous-programming-in-cpp-universal-windows-platform-apps)<br/>
[為 UWP 應用在C++中建立非同步操作](../../parallel/concrt/creating-asynchronous-operations-in-cpp-for-windows-store-apps.md)<br/>
[快速啟動:使用 XML HTTP 要求 (IXMLHTTPrequest2)](/previous-versions/windows/apps/hh770550\(v=win.10\))
[工作類別(並發執行時)](../../parallel/concrt/reference/task-class.md)進行連線<br/>
[task_completion_event 類別](../../parallel/concrt/reference/task-completion-event-class.md)
