---
title: "如何： 定期傳送訊息 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- timer class, example
- sending messages at regular intervals [Concurrency Runtime]
ms.assetid: 4b60ea6c-97c8-4d69-9f7b-ad79f3548026
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f12d9f8af028d1e2e1fc149eeb77181c2f6b1730
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-send-a-message-at-a-regular-interval"></a>如何：定期傳送訊息
這個範例示範如何使用 concurrency::[timer 類別](../../parallel/concrt/reference/timer-class.md)定期傳送訊息。  
  
## <a name="example"></a>範例  

 下列範例會使用`timer`長時間作業期間報告進度的物件。 此範例的連結`timer`物件[concurrency:: call](../../parallel/concrt/reference/call-class.md)物件。 `call`物件會以固定間隔列印進度指示器，以在主控台。 [Concurrency::timer::start](reference/timer-class.md#start)方法會在個別的內容上執行計時器。 `perform_lengthy_operation`函式呼叫[concurrency:: wait](reference/concurrency-namespace-functions.md#wait)函式來模擬耗時的作業在主要內容。  

  
 [!code-cpp[concrt-report-progress#1](../../parallel/concrt/codesnippet/cpp/how-to-send-a-message-at-a-regular-interval_1.cpp)]  
  
 這個範例會產生下列輸出範例：  
  
```Output  
Performing a lengthy operation..........done.  
```  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 範例程式碼複製並將它貼入 Visual Studio 專案中，或將它貼入名為的檔案中`report-progress.cpp`，然後在 Visual Studio 命令提示字元視窗中執行下列命令。  
  
 **cl.exe /EHsc report-progress.cpp**  
  
## <a name="see-also"></a>請參閱  
 [非同步代理程式程式庫](../../parallel/concrt/asynchronous-agents-library.md)   
 [非同步訊息區](../../parallel/concrt/asynchronous-message-blocks.md)   
 [訊息傳遞函式](../../parallel/concrt/message-passing-functions.md)
