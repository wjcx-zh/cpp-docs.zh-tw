---
title: "例外狀況：從您自己的函式擲回例外狀況 | Microsoft Docs"
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
  - "例外狀況, 擲回"
  - "函式 [C++], 擲回例外狀況"
  - "擲回例外狀況, 從函式"
ms.assetid: 492976e8-8804-4234-8e8f-30dffd0501be
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 例外狀況：從您自己的函式擲回例外狀況
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

個別使用 MFC 例外狀況處理範例攔截函式所擲回的例外狀況在 MFC 或其他程式庫中是可能的。  除了程式庫程式碼擲回的攔截例外狀況之外，您可以擲回從您的程式碼的例外狀況，如果您正在撰寫可能發生例外狀況的函式。  
  
 當例外狀況擲回時，目前函式的執行會停止並直接跳到最內層的例外狀況框架的 **catch** 區塊。  例外狀況機制略過從函式的正常結束路徑。  因此，您必須確定刪除在正常結束要刪除的記憶體區塊。  
  
#### 擲回例外狀況。  
  
1.  使用其中一個 MFC Helper 函式，例如 `AfxThrowMemoryException`。  這些函式會擲回適當型別的預先配置的例外狀況物件。  
  
     在下列範例中，如果，任一組態失敗，函式嘗試指派兩個記憶體區塊時會擲回例外狀況:  
  
     [!code-cpp[NVC_MFCExceptions#17](../mfc/codesnippet/CPP/exceptions-throwing-exceptions-from-your-own-functions_1.cpp)]  
  
     如果第一個配置失敗，您可以擲回記憶體不足例外狀況。  如果第一個配置成功，但是第二個失敗，您必須在擲回例外狀況之前釋放第一個配置區塊。  如果兩個配置成功，通常可以執行和釋放區塊，當函式結束時。  
  
     \-或\-  
  
2.  使用使用者定義的例外狀況會指示問題的情況。  您可以擲回任何型別，甚至整個類別項目，為您的例外狀況。  
  
     如果發生失敗，下列範例嘗試透過聲波裝置播放音效並擲回例外狀況。  
  
     [!code-cpp[NVC_MFCExceptions#18](../mfc/codesnippet/CPP/exceptions-throwing-exceptions-from-your-own-functions_2.cpp)]  
  
> [!NOTE]
>  MFC 的例外狀況預設處理僅適用於指標對 `CException` 或 `CException`物件 \(此物件和衍生類別\)。  上述範例略過 MFC 的例外狀況機制。  
  
## 請參閱  
 [例外狀況處理](../mfc/exception-handling-in-mfc.md)