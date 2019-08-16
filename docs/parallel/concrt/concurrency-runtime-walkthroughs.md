---
title: 並行執行階段逐步解說
ms.date: 11/04/2016
helpviewer_keywords:
- walkthroughs [Concurrency Runtime]
- Concurrency Runtime, walkthroughs
ms.assetid: 7374c5e9-54eb-44bf-9ed9-5e190cfd290b
ms.openlocfilehash: 7c5973f8010d7c428406a8a3f69574eab20edf82
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69512833"
---
# <a name="concurrency-runtime-walkthroughs"></a>並行執行階段逐步解說

本節中以案例為基礎的主題會示範如何使用並行執行階段的許多功能。

## <a name="in-this-section"></a>本節內容

[逐步解說：使用工作和 XML HTTP 要求進行連線](../../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md)<br/>
說明如何搭配使用[IXMLHTTPRequest2](/windows/win32/api/msxml6/nn-msxml6-ixmlhttprequest2)和[IXMLHTTPRequest2Callback](/windows/win32/api/msxml6/nn-msxml6-ixmlhttprequest2callback)介面與工作, 將 HTTP GET 和 POST 要求傳送至通用 Windows 平臺 (UWP) 應用程式中的 web 服務。

[逐步解說：建立代理程式型的應用程式](../../parallel/concrt/walkthrough-creating-an-agent-based-application.md)<br/>
描述如何建立以代理程式為基礎的基本應用程式。

[逐步解說：建立資料流程代理程式](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md)<br/>
示範如何建立以資料流程為基礎的以代理程式為基礎的應用程式, 而不是控制流程。

[逐步解說：建立影像處理網路](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)<br/>
示範如何建立可執行影像處理的非同步訊息區塊網路。

[逐步解說：實作 Future](../../parallel/concrt/walkthrough-implementing-futures.md)<br/>
示範如何以非同步方式計算值, 以供稍後使用。

[逐步解說：使用聯結以預防死結](../../parallel/concrt/walkthrough-using-join-to-prevent-deadlock.md)<br/>
使用哲學家就餐問題來說明如何使用[concurrency:: join](../../parallel/concrt/reference/join-class.md)類別, 以避免應用程式中發生鎖死。

[逐步解說：從使用者介面執行緒移除工作](../../parallel/concrt/walkthrough-removing-work-from-a-user-interface-thread.md)<br/>
示範如何改善繪製 Mandelbrot 碎形之 MFC 應用程式的效能。

[逐步解說：在啟用 COM 的應用程式中使用並行執行階段](../../parallel/concrt/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application.md)<br/>
示範如何在使用元件物件模型 (COM) 的應用程式中使用並行執行階段。

[逐步解說：改寫現有程式碼以使用輕量型工作](../../parallel/concrt/walkthrough-adapting-existing-code-to-use-lightweight-tasks.md)<br/>
示範如何調整使用 Windows API 的現有程式碼, 以建立和執行執行緒以使用輕量工作。

[逐步解說：建立自訂訊息區](../../parallel/concrt/walkthrough-creating-a-custom-message-block.md)<br/>
描述如何建立依優先順序排序傳入訊息的自訂訊息區塊類型。

## <a name="related-sections"></a>相關章節

[並行執行階段](../../parallel/concrt/concurrency-runtime.md)<br/>
介紹 Visual C++的並行程式設計架構。
