---
title: "如何：為呼叫和轉換程式類別提供工作函式 | Microsoft Docs"
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
helpviewer_keywords: 
  - "call 類別，範例"
  - "使用 transformer 類別 [並行執行階段]"
  - "使用 call 類別 [並行執行階段]"
ms.assetid: df715ce4-8507-41ca-b204-636d11707a73
caps.latest.revision: 15
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：為呼叫和轉換程式類別提供工作函式
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本主題說明許多將工作函式提供給 [concurrency::call](../../parallel/concrt/reference/call-class.md) 和 [concurrency::transformer](../../parallel/concrt/reference/transformer-class.md) 類別的方式。  
  
 第一個範例示範如何將 Lambda 運算式傳遞給 `call` 物件。  第二個範例示範如何將函式物件傳遞給 `call` 物件。  第三個範例示範如何將類別方法繫結至 `call` 物件。  
  
 為了說明方便，本主題中的每個範例都會使用 `call` 類別。  如需使用 `transformer` 類別的範例，請參閱 [如何：在資料管線中使用轉換程式](../../parallel/concrt/how-to-use-transformer-in-a-data-pipeline.md)。  
  
## 範例  
 下列範例示範使用 `call` 類別的常見方式。  這個範例會將 Lambda 函式傳遞給 `call` 建構函式。  
  
 [!code-cpp[concrt-call-lambda#1](../../parallel/concrt/codesnippet/CPP/how-to-provide-work-functions-to-the-call-and-transformer-classes_1.cpp)]  
  
 這個範例產生下列輸出。  
  
  **13的平方 是 169。**   
## 範例  
 下列範例與上一則範例很相似，不過它會使用 `call` 類別搭配函式物件 \(functor\)。  
  
 [!code-cpp[concrt-call-functor#1](../../parallel/concrt/codesnippet/CPP/how-to-provide-work-functions-to-the-call-and-transformer-classes_2.cpp)]  
  
## 範例  
 下列範例與上一則範例很相似，不過它會使用 [std::bind1st](../Topic/bind1st%20Function.md) 和 [std::mem\_fun](../Topic/mem_fun%20Function.md) 函式，將 `call` 物件繫結至類別方法。  
  
 如果您必須將 `call` 或 `transformer` 物件繫結至特定類別方法而非函式呼叫運算子 `operator()`，請使用這項技術。  
  
 [!code-cpp[concrt-call-method#1](../../parallel/concrt/codesnippet/CPP/how-to-provide-work-functions-to-the-call-and-transformer-classes_3.cpp)]  
  
 您也可以將 `bind1st` 函式的結果指派給 [std::function](../../standard-library/function-class.md) 物件或使用 `auto` 關鍵字，如下列範例所示。  
  
 [!code-cpp[concrt-call-method#2](../../parallel/concrt/codesnippet/CPP/how-to-provide-work-functions-to-the-call-and-transformer-classes_4.cpp)]  
  
## 編譯程式碼  
 請複製範例程式碼，並將它貼在 Visual Studio 專案中，或貼在名為 `call.cpp` 的檔案中，然後在 Visual Studio 的 \[命令提示字元\] 視窗中執行下列命令。  
  
 **cl.exe \/EHsc call.cpp**  
  
## 請參閱  
 [非同步代理程式程式庫](../../parallel/concrt/asynchronous-agents-library.md)   
 [非同步訊息區](../../parallel/concrt/asynchronous-message-blocks.md)   
 [如何：在資料管線中使用轉換程式](../../parallel/concrt/how-to-use-transformer-in-a-data-pipeline.md)   
 [call 類別](../../parallel/concrt/reference/call-class.md)   
 [transformer 類別](../../parallel/concrt/reference/transformer-class.md)