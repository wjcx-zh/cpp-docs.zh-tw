---
title: "並行執行階段逐步解說 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- walkthroughs [Concurrency Runtime]
- Concurrency Runtime, walkthroughs
ms.assetid: 7374c5e9-54eb-44bf-9ed9-5e190cfd290b
caps.latest.revision: "14"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c9aaff86eb5781872675a46863ccfbafff60d24e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="concurrency-runtime-walkthroughs"></a>並行執行階段逐步解說
本節中以案例為基礎的主題示範如何使用多個並行執行階段功能。  
  
## <a name="in-this-section"></a>本節內容  
 [逐步解說：使用工作和 XML HTTP 要求連接](../../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md)  
 示範如何使用[IXMLHTTPRequest2](http://msdn.microsoft.com/en-us/bbc11c4a-aecf-4d6d-8275-3e852e309908)和[IXMLHTTPRequest2Callback](http://msdn.microsoft.com/en-us/aa4b3f4c-6e28-458b-be25-6cce8865fc71)介面，以及將 HTTP GET 和 POST 要求傳送至 web 服務中的工作[!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)]應用程式。  
  
 [逐步解說：建立代理程式架構應用程式](../../parallel/concrt/walkthrough-creating-an-agent-based-application.md)  
 描述如何建立基本的代理程式架構應用程式。  
  
 [逐步解說：建立資料流程代理程式](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md)  
 示範如何建立代理程式為基礎的應用程式為基礎的資料流程，而不是在控制流程。  
  
 [逐步解說：建立影像處理網路](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)  
 示範如何建立執行映像處理的非同步訊息區的網路。  
  
 [逐步解說：實作未來](../../parallel/concrt/walkthrough-implementing-futures.md)  
 示範如何以非同步方式計算值供日後使用。  
  
 [逐步解說：使用聯結以避免死結](../../parallel/concrt/walkthrough-using-join-to-prevent-deadlock.md)  
 使用哲學家用餐問題，說明如何使用[concurrency:: join](../../parallel/concrt/reference/join-class.md)類別避免應用程式中的死結。  
  
 [逐步解說：從使用者介面執行緒中移除工作](../../parallel/concrt/walkthrough-removing-work-from-a-user-interface-thread.md)  
 示範如何改善繪製 Mandelbrot 不規則的 MFC 應用程式的效能。  
  
 [逐步解說：在啟用 COM 的應用程式中使用並行執行階段](../../parallel/concrt/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application.md)  
 示範如何使用並行執行階段中使用元件物件模型 (COM) 的應用程式。  
  
 [逐步解說：改寫現有程式碼以使用輕量型工作](../../parallel/concrt/walkthrough-adapting-existing-code-to-use-lightweight-tasks.md)  
 顯示如何調整現有程式碼使用 Windows API 來建立和執行使用輕量型工作的執行緒。  
  
 [逐步解說：建立自訂訊息區](../../parallel/concrt/walkthrough-creating-a-custom-message-block.md)  
 描述如何建立依優先順序排序內送訊息的自訂訊息區塊類型。  
  
## <a name="related-sections"></a>相關章節  
 [並行執行階段](../../parallel/concrt/concurrency-runtime.md)  
 介紹 Visual c + + 的並行程式設計架構。

