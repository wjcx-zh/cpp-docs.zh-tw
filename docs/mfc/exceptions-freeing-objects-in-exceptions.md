---
title: "例外狀況： 釋放例外狀況中的物件 |Microsoft 文件"
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
- throwing exceptions [MFC], freeing objects in exceptions
- local exception handling
- memory leaks, caused by exception
- try-catch exception handling [MFC], destroying objects
- destroying objects [MFC]
- freeing objects [MFC]
- throwing exceptions [MFC], after destroying
- exception handling [MFC], destroying objects
ms.assetid: 3b14b4ee-e789-4ed2-b8e3-984950441d97
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a422347e319fabbd91f20e0ebf7897865f1ca4c7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="exceptions-freeing-objects-in-exceptions"></a>例外狀況：釋放例外狀況中的物件
本文說明需和例外狀況發生時釋放物件的方法。 主題包括：  
  
-   [處理本機的例外狀況](#_core_handling_the_exception_locally)  
  
-   [終結物件之後擲回例外狀況](#_core_throwing_exceptions_after_destroying_objects)  
  
 由架構或由應用程式中斷一般程式流程會擲回的例外狀況。 因此，它是您一定要保持關閉追蹤的物件，以便您可以適當地處置它們萬一擲回例外狀況。  
  
 有兩種主要的方法，若要這樣做。  
  
-   在本機使用處理例外狀況**再試一次**和**攔截**關鍵字，然後終結使用一個陳述式的所有物件。  
  
-   終結中的任何物件**攔截**擲回的例外狀況區塊外部的進一步處理之前的區塊。  
  
 下例會有問題的解決方案為下面說明這兩種方法：  
  
 [!code-cpp[NVC_MFCExceptions#14](../mfc/codesnippet/cpp/exceptions-freeing-objects-in-exceptions_1.cpp)]  
  
 與上面，`myPerson`將不會刪除所擲回的例外狀況時`SomeFunc`。 執行直接跳到下一個外部例外狀況處理常式，略過一般函式結束和刪除物件的程式碼。 物件的指標超出範圍時例外狀況離開函式，而且將不會復原物件所佔用的記憶體，只要執行程式。 這是記憶體流失。它會使用記憶體診斷偵測到。  
  
##  <a name="_core_handling_the_exception_locally"></a>處理本機的例外狀況  
 **Try/catch**範例提供防禦的程式設計方法，讓您避免記憶體流失，並確認您的物件被終結時，會發生例外狀況。 比方說，在本文前段所示的範例可以改寫，如下所示：  
  
 [!code-cpp[NVC_MFCExceptions#15](../mfc/codesnippet/cpp/exceptions-freeing-objects-in-exceptions_2.cpp)]  
  
 這個新的範例會設定攔截例外狀況，並在本機處理的例外狀況處理常式。 然後通常會結束函式，並終結物件。 這個範例的重點就是內容，才能攔截例外狀況以建立**try/catch**區塊。 不在本機的例外狀況範圍內，函式永遠不會知道已擲回例外狀況，而不會有機會正常結束，並終結物件。  
  
##  <a name="_core_throwing_exceptions_after_destroying_objects"></a>終結物件之後擲回例外狀況  
 若要處理的例外狀況的另一個方法是將其傳遞至下一個外部例外狀況處理內容。 在您**攔截**區塊中，您可以執行某些清除您在本機上所配置的物件，並再擲回例外狀況以便進一步處理。  
  
 擲回的函式可能會或可能不需要取消配置堆積物件。 如果函式一律會取消堆積物件配置在一般案例中，傳回前，則函式也應該取消堆積物件配置之前擲回例外狀況。 相反地，如果函式不會無法正常解除配置物件在正常情況下傳回之前，然後您必須決定根據案例為基礎的堆積物件是否應該取消配置。  
  
 下列範例會示範如何在本機配置的物件可以清除：  
  
 [!code-cpp[NVC_MFCExceptions#16](../mfc/codesnippet/cpp/exceptions-freeing-objects-in-exceptions_3.cpp)]  
  
 例外狀況機制會自動解除配置框架物件;也稱為框架物件的解構函式。  
  
 如果您呼叫可能會擲回例外狀況的函式，您可以使用**try/catch**區塊來確定您攔截的例外狀況，並有機會摧毀任何您已建立的物件。 特別是，請注意，許多 MFC 函式可以擲回例外狀況。  
  
 如需詳細資訊，請參閱[例外狀況： 攔截及刪除例外狀況](../mfc/exceptions-catching-and-deleting-exceptions.md)。  
  
## <a name="see-also"></a>請參閱  
 [例外狀況處理](../mfc/exception-handling-in-mfc.md)

