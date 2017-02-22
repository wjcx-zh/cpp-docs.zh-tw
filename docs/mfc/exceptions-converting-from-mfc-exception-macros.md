---
title: "例外狀況：從 MFC 例外狀況巨集轉換 | Microsoft Docs"
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
  - "catch 區塊, 分隔"
  - "CException 類別, 刪除 CException 類別物件"
  - "轉換, 以 MFC 巨集撰寫的程式碼"
  - "轉換例外狀況"
  - "例外狀況處理, 轉換例外狀況"
  - "例外狀況物件"
  - "例外狀況物件, 刪除"
  - "例外狀況, 轉換"
  - "例外狀況, 刪除例外狀況物件"
  - "關鍵字 [C++], 巨集"
  - "巨集, C++ 關鍵字"
ms.assetid: bd3ac3b3-f3ce-4fdd-a168-a2cff13ed796
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 例外狀況：從 MFC 例外狀況巨集轉換
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

這是一個進階主題。  
  
 本文說明如何將現有的程式碼與 MFC 巨集 **TRY**， **CATCH**， **THROW**等等\)，使用 C\+\+ 例外狀況處理關鍵字、 **catch**和 **try**`throw`。  主題包括：  
  
-   [轉換優點](#_core_advantages_of_converting)  
  
-   [轉換與例外狀況巨集的程式碼使用 C\+\+ 例外狀況。](#_core_doing_the_conversion)  
  
##  <a name="_core_advantages_of_converting"></a> 要轉換的優點  
 您可能不需要轉換現有的程式碼，不過，您應該知道在巨集實作在 MFC 3.0 版和實作之間的差異在舊版。  這些差異並後續變更程式碼行為上 [例外狀況:對例外狀況巨集的變更在 3.0 版上](../mfc/exceptions-changes-to-exception-macros-in-version-3-0.md)中討論。  
  
 要轉換的主要優點是:  
  
-   程式碼使用 C\+\+ 例外狀況處理關鍵字編譯成稍微小的 .EXE 或 .DLL。  
  
-   C\+\+ 例外狀況處理關鍵字用途較廣的:它們可以處理可以複製任何資料型別的例外狀況 \( **float**，`int`、 `char`等\)，，，而巨集只處理例外狀況從它衍生的類別和 `CException` 類別。  
  
 當發生例外狀況時，超出範圍時，巨集和關鍵字之間的主要差異在於該程式碼會使用巨集自動刪除已攔截的例外狀況。  使用關鍵字的程式碼，因此，您必須明確地刪除已攔截的例外狀況。  如需詳細資訊，請參閱文件 [例外狀況:攔截和刪除例外狀況。](../mfc/exceptions-catching-and-deleting-exceptions.md)。  
  
 另一個差異是語法。  巨集和關鍵字的語法在三個方面不同:  
  
1.  巨集引數和例外狀況宣告:  
  
     **CATCH** 巨集引動過程有下列語法:  
  
     **CATCH\(** *exception\_class*， *exception\_object\_pointer\_name* **\)**  
  
     請注意在類別名稱和物件指標名稱之間的逗號。  
  
     **catch** 關鍵字的例外狀況宣告使用這個語法:  
  
     **catch\(** *exception\_type* *exception\_name***\)**  
  
     這個例外狀況宣告陳述式表示例外狀況類型的 catch 區塊控制代碼。  
  
2.  Catch 區塊的分隔:  
  
     巨集， **CATCH** 巨集 \(與其引數\) 啟動第一個 catch 區塊; `AND_CATCH` 巨集啟動後續 Catch 區塊，因此， `END_CATCH` 巨集終止 catch 區塊序列。  
  
     關鍵字， **catch** 關鍵字 \(與其例外狀況宣告\) 啟動每個 catch 區塊。  未對應至 `END_CATCH` 巨集;與其右邊的大括號的 catch 區塊結尾。  
  
3.  擲回運算式:  
  
     巨集使用 `THROW_LAST` 重新擲回目前的例外狀況。  `throw` 關鍵字，沒有引數，具有相同的效果。  
  
##  <a name="_core_doing_the_conversion"></a> 進行轉換  
  
#### 轉換程式碼會使用巨集使用 C\+\+ 例外狀況處理關鍵字  
  
1.  找出 MFC 巨集 **TRY**和 **CATCH**、 `AND_CATCH`、 `END_CATCH`、 **THROW**和 `THROW_LAST`的所有項目。  
  
2.  取代或刪除下列巨集的所有項目:  
  
     **TRY** \(以 **try**取代\)  
  
     **CATCH** \(以 **catch**取代\)  
  
     `AND_CATCH` \(以 **catch**取代\)  
  
     `END_CATCH` \(刪除\)  
  
     **THROW** \(以 `throw`取代\)  
  
     `THROW_LAST` \(以 `throw`取代\)  
  
3.  修改巨集引數，讓它們構成有效例外狀況宣告。  
  
     例如，變更  
  
     [!code-cpp[NVC_MFCExceptions#6](../mfc/codesnippet/CPP/exceptions-converting-from-mfc-exception-macros_1.cpp)]  
  
     設為  
  
     [!code-cpp[NVC_MFCExceptions#7](../mfc/codesnippet/CPP/exceptions-converting-from-mfc-exception-macros_2.cpp)]  
  
4.  修改 catch 區塊中的程式碼，以視需要刪除例外狀況物件。  如需詳細資訊，請參閱文件 [例外狀況:攔截和刪除例外狀況。](../mfc/exceptions-catching-and-deleting-exceptions.md)。  
  
 使用 MFC 例外狀況巨集，這個例外狀況處理程式碼的範例。  請注意，因為在下列範例中的程式碼會使用巨集，例外狀況 `e` 自動刪除:  
  
 [!code-cpp[NVC_MFCExceptions#8](../mfc/codesnippet/CPP/exceptions-converting-from-mfc-exception-macros_3.cpp)]  
  
 在下一個範例中的程式碼使用 C\+\+ 例外狀況關鍵字，因此，必須明確地刪除例外狀況:  
  
 [!code-cpp[NVC_MFCExceptions#9](../mfc/codesnippet/CPP/exceptions-converting-from-mfc-exception-macros_4.cpp)]  
  
 如需詳細資訊，請參閱 [例外狀況:使用 MFC 巨集和 C\+\+ 例外狀況。](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md)。  
  
## 請參閱  
 [例外狀況處理](../mfc/exception-handling-in-mfc.md)