---
title: "如何：定期傳送訊息 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "timer 類別，範例"
  - "定期傳送訊息 [並行執行階段]"
ms.assetid: 4b60ea6c-97c8-4d69-9f7b-ad79f3548026
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 19
---
# 如何：定期傳送訊息
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個範例示範如何使用並行存取::[timer 類別](../../parallel/concrt/reference/timer-class.md) 定期傳送訊息。  
  
## <a name="example"></a>範例  
 下列範例會使用 `timer` 長時間作業期間報告進度的物件。 此範例的連結 `timer` 物件傳遞給 [concurrency:: call](../../parallel/concrt/reference/call-class.md) 物件。  `call` 物件列印到主控台的進度列指示器以固定間隔。  [Concurrency::timer::start](../Topic/timer::start%20Method.md) 個別的內容上執行計時器的方法。  `perform_lengthy_operation` 函式呼叫 [concurrency:: wait](../Topic/wait%20Function.md) 函式，以便模擬耗時的作業在主要內容。  
  
 [!code-cpp[concrt-report-progress#1](../../parallel/concrt/codesnippet/CPP/how-to-send-a-message-at-a-regular-interval_1.cpp)]  
  
 這個範例會產生下列輸出的範例︰  
  
```Output  
Performing a lengthy operation..........done.  
```  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 複製範例程式碼並將它貼在 Visual Studio 專案中，或貼入名為的檔案 `report-progress.cpp` ，然後在 Visual Studio 命令提示字元] 視窗中執行下列命令。  
  
 **cl.exe /EHsc report-progress.cpp**  
  
## <a name="see-also"></a>另請參閱  
 [非同步代理程式庫](../../parallel/concrt/asynchronous-agents-library.md)   
 [非同步訊息區](../../parallel/concrt/asynchronous-message-blocks.md)   
 [訊息傳遞函式](../../parallel/concrt/message-passing-functions.md)
