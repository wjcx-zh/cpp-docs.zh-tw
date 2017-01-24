---
title: "使用 MFC 原始程式檔 | Microsoft Docs"
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
  - "MFC 原始程式檔"
  - "MFC, 原始程式檔"
  - "Private 成員存取"
  - "Protected 成員存取"
  - "Public 成員"
  - "原始程式檔"
  - "原始程式檔, MFC"
ms.assetid: 3230e8fb-3b69-4ddf-9538-365ac7ea5e72
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 使用 MFC 原始程式檔
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Microsoft Foundation Class \(MFC\) 程式庫提供完整的原始程式碼。  標頭檔 \(.h\) 在\\ atlmfc \\ Include 目錄;實作檔 \(.cpp\) 在\\ atlmfc \\ src \\ mfc 目錄。  
  
 本文章系列說明 MFC 使用註解每個類別的各部分的慣例，以及這些註解，方法，以及您在每一個區段應該預期尋找。  Visual C\+\+ 精靈會為您建立的類別使用類似的慣例，因此，您可能會發現這些慣例有助於您的程式碼。  
  
 您可能已經熟悉 **public**、 `protected`和 `private` C\+\+ 關鍵字。  當查看 MFC 標頭檔時，您會發現每個類別可能會有的每一個。  例如，公用成員變數和函式可能會在多個 **public** 關鍵字底下。  這是因為， MFC 分隔根據其使用和函式的成員變數，而不是允許的存取類型。  MFC 使用 `private` 謹慎;即使項目考量的實作詳細資料通常是受保護的，而許多時間是公用的。  雖然對實作詳細資料的存取是鼓勵， MFC 離開這個決定給您。  
  
 在 MFC 原始程式檔和 MFC 應用程式精靈建立的檔案，您會發現這類的註解在類別宣告內 \(通常會依此順序\):  
  
 `// Constructors`  
  
 `// Attributes`  
  
 `// Operations`  
  
 `// Overridables`  
  
 `// Implementation`  
  
 在文件包括這系列所包含的主題:  
  
-   [註解的範例](../mfc/an-example-of-the-comments.md)  
  
-   [\/\/ 實作註解](../mfc/decrement-implementation-comment.md)  
  
-   [\/\/ 建構函式註解](../mfc/decrement-constructors-comment.md)  
  
-   [取消註解屬性。](../mfc/decrement-attributes-comment.md)  
  
-   [\/\/作業註解](../mfc/decrement-operations-comment.md)  
  
-   [\/\/ 可覆寫函式註解](../mfc/decrement-overridables-comment.md)  
  
## 請參閱  
 [一般 MFC 主題](../mfc/general-mfc-topics.md)