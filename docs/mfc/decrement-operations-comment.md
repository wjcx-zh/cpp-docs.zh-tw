---
title: "// 作業註解 | Microsoft Docs"
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
  - "MFC 原始程式檔, 作業註解"
  - "MFC 原始程式檔中的作業註解"
ms.assetid: f3bff48d-26be-4db6-8435-9e4d079838c9
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# // 作業註解
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

MFC 類別宣告的 `// Operations` 區段包含您在物件上呼叫會進行或執行動作的成員函式 \(作業\)。  因為它們通常有副作用，這些函式通常是非**const** 。  它們可以是虛擬或虛擬以類別為基礎的需要。  一般來說，這些成員都是公用的。  
  
 在從類別 `CStdioFile`的範例目錄，在 [註解的範例](../mfc/an-example-of-the-comments.md)中，清單中包含兩個成員函式在此註解中: `ReadString` 和 `WriteString`。  
  
 使用屬性，可以執行作業進一步細分。  
  
## 請參閱  
 [使用 MFC 原始程式檔](../mfc/using-the-mfc-source-files.md)   
 [註解的範例](../mfc/an-example-of-the-comments.md)   
 [\/\/ 實作註解](../mfc/decrement-implementation-comment.md)   
 [\/\/ 建構函式註解](../mfc/decrement-constructors-comment.md)   
 [\/\/ 屬性註解](../mfc/decrement-attributes-comment.md)   
 [\/\/ 可覆寫函式註解](../mfc/decrement-overridables-comment.md)