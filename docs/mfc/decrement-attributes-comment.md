---
title: "// 屬性註解 | Microsoft Docs"
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
  - "MFC 原始程式檔中的屬性註解"
  - "註解, 屬性"
  - "MFC 原始程式檔, 屬性註解"
  - "公用屬性註解"
ms.assetid: 96388e11-42df-4994-aedf-decd152961a7
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# // 屬性註解
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

MFC 類別宣告的 `// Attributes` 區段包含公用屬性 \(或屬性\) 的物件。  這些通常是成員變數，或是取得\/設定函式。  「Get」和「Set」函式不一定是虛擬的。  所以在大部分情況下沒有副作用， 「Get」函式通常是 **const**。  這些成員通常是公用的;受保護的私用和屬性在實作部分通常會找到。  
  
 在從類別 `CStdioFile`的範例目錄，在 [註解的範例](../mfc/an-example-of-the-comments.md)下，清單包含 10% 成員變數，則為 `m_pStream`。  類別 `CDC` 清單幾乎 20 個成員在此註解中。  
  
> [!NOTE]
>  擴充類別，例如 `CDC` 和 `CWnd`，可能有列出所有屬性在一個群組中會加入清晰的許多成員。  在這種情況下，類別庫使用其他註解，標題進一步描述成員。  例如， `CDC` 會使用 `// Device-Context Functions`、 `// Drawing Tool Functions`， `// Drawing Attribute Functions`等等。  表示屬性的群組會遵循中說明的頂端一般語法。  許多 OLE 類別有 `// Interface Maps`一部分實作。  
  
## 請參閱  
 [使用 MFC 原始程式檔](../mfc/using-the-mfc-source-files.md)   
 [註解的範例](../mfc/an-example-of-the-comments.md)   
 [\/\/ 實作註解](../mfc/decrement-implementation-comment.md)   
 [\/\/ 建構函式註解](../mfc/decrement-constructors-comment.md)   
 [\/\/ 作業註解](../mfc/decrement-operations-comment.md)   
 [\/\/ 可覆寫函式註解](../mfc/decrement-overridables-comment.md)