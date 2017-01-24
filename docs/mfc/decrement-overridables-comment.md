---
title: "// 可覆寫函式註解 | Microsoft Docs"
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
  - "註解, MFC"
  - "MFC 原始程式檔, 可覆寫函式註解"
  - "MFC 原始程式檔中的可覆寫函式註解"
  - "覆寫, MFC 原始程式檔中的可覆寫函式註解"
ms.assetid: 8968dea5-0d94-451f-bcb2-991580e65ba2
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# // 可覆寫函式註解
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

MFC 類別宣告的 `// Overridables` 區段包含您可以覆寫衍生類別中的虛擬函式時，您必須修改基底類別行為時。  它們的名稱通常是開頭為" on "，不過，不是絕對必要的。  此函式會覆寫並經常實作或提供某種「回呼」或「請將」。一般來說，這些成員會受到保護。  
  
 在 MFC 中，純虛擬函式本節永遠放置。  C\+\+ 中的純虛擬函式是一個表單:  
  
 `virtual void OnDraw( ) = 0;`  
  
 在從類別 `CStdioFile`的範例目錄，在 [註解的範例](../mfc/an-example-of-the-comments.md)中，清單不包含 overridables 部分。  將 **CDocument**，另一方面，清單大約 10 可覆寫成員函式。  
  
 在部分類別中，您可能會看到註解 `// Advanced Overridables`。  這些是只進階程式設計人員應該嘗試覆寫的函式。  您可能永遠不需要覆寫它們。  
  
> [!NOTE]
>  本文所述的慣例為自動化 \(先前稱為 OLE Automation\) 方法和屬性很好，一般而言，也工作。  Automation 方法類似於 MFC 作業。  Automation 屬性類似於 MFC 屬性。  Automation 事件 \(支援 ActiveX 控制項，先前稱為 OLE automation 控制項\) 類似於 MFC 可覆寫成員函式。  
  
## 請參閱  
 [使用 MFC 原始程式檔](../mfc/using-the-mfc-source-files.md)   
 [註解的範例](../mfc/an-example-of-the-comments.md)   
 [\/\/ 實作註解](../mfc/decrement-implementation-comment.md)   
 [\/\/ 建構函式註解](../mfc/decrement-constructors-comment.md)   
 [\/\/ 屬性註解](../mfc/decrement-attributes-comment.md)   
 [\/\/ 作業註解](../mfc/decrement-operations-comment.md)