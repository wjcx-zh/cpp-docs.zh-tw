---
title: "例外狀況：釋放例外狀況中的物件 | Microsoft Docs"
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
  - "終結物件"
  - "例外狀況處理, 終結物件"
  - "釋放物件"
  - "本機例外狀況處理"
  - "記憶體遺漏, 由例外狀況所造成"
  - "擲回例外狀況, 終結後"
  - "擲回例外狀況, 釋放例外狀況中的物件"
  - "try-catch 例外狀況處理, 終結物件"
ms.assetid: 3b14b4ee-e789-4ed2-b8e3-984950441d97
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 例外狀況：釋放例外狀況中的物件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文說明當例外狀況發生時，為何需要釋放物件以及其方法。  主題包括：  
  
-   [在本機處理例外狀況](#_core_handling_the_exception_locally)  
  
-   [在終結物件之後擲回例外狀況](#_core_throwing_exceptions_after_destroying_objects)  
  
 架構或您的應用程式執回例外狀況會中斷一般程式流程。  因此，保留物件存取追蹤是非常重要的，這讓您能在擲回例外狀況時正確處理它們。  
  
 執行這項作業的方法有兩種。  
  
-   使用 **try** 和 **catch** 關鍵字在本機處理例外狀況，然後以一個陳述式終結所有物件。  
  
-   在區塊外擲回例外狀況之前，終結 **catch** 區塊中的所有物件，以進一步繼續處理。  
  
 下列兩種方法為以下問題的範例方案：  
  
 [!code-cpp[NVC_MFCExceptions#14](../mfc/codesnippet/CPP/exceptions-freeing-objects-in-exceptions_1.cpp)]  
  
 如前述，若 `SomeFunc` 擲回例外狀況，則 `myPerson` 不會被刪除。  執行會直接跳至下一個外部例外處理常式，略過正常功能結束和刪除物件的程式碼。  當例外狀況離開函式時，物件的指標會超出範圍，而只要程式執行，物件所佔用的記憶體不會復原。  這是記憶體遺漏 \(Memory Leak\)；若使用記憶體診斷將會偵測到它。  
  
##  <a name="_core_handling_the_exception_locally"></a> 在本機處理例外狀況  
 **try\/catch** 範例為避免記憶體遺漏提供一個安全的程式設計方式，並確保在例外狀況發生時終結您的物件。  例如，在本文先前的範例可以重新撰寫如下：  
  
 [!code-cpp[NVC_MFCExceptions#15](../mfc/codesnippet/CPP/exceptions-freeing-objects-in-exceptions_2.cpp)]  
  
 這個新範例設定例外處理常式，攔截例外狀況並在本機處理它。  它接著會正常地結束函式，並終結物件。  這個範例的重點是，攔截例外狀況的內容是與 **try\/catch** 區塊一起建立。  沒有本機例外狀況框架，函式永遠不會知道有擲回例外狀況，也不會有機會正常關閉並終結物件。  
  
##  <a name="_core_throwing_exceptions_after_destroying_objects"></a> 在終結物件之後擲回例外狀況  
 另一個處理例外狀況的方式為傳遞至下一個外部例外狀況處理內容。  在 **catch** 區塊中，您可以為本機配置的物件進行一些清除，然後擲回例外狀況做進一步的處理。  
  
 擲回的函式不一定需要解除配置的物件。  如果函式在一般情況返回之前總是解除配置堆積物件，則函式應該在擲回例外狀況之前也解除配置的物件。  另一方面，如果函式在一般情況返回之前不會解除配置堆積物件，則您必須根據特定條件決定堆積物件是否應該解除配置。  
  
 下列範例顯示本機配置的物件可以如何被清除：  
  
 [!code-cpp[NVC_MFCExceptions#16](../mfc/codesnippet/CPP/exceptions-freeing-objects-in-exceptions_3.cpp)]  
  
 例外狀況機制會自動解除配置的框架物件；框架物件的解構函式也會被呼叫。  
  
 如果您呼叫會擲回例外狀況的函式，您可以使用 **try\/catch** 區塊，以確定您攔截例外狀況並有機會終結任何您建立的物件。  尤其，請注意許多 MFC 函式可以擲回例外狀況。  
  
 如需詳細資訊，請參閱 [例外狀況：攔截和刪除例外狀況](../mfc/exceptions-catching-and-deleting-exceptions.md)。  
  
## 請參閱  
 [例外狀況處理](../mfc/exception-handling-in-mfc.md)