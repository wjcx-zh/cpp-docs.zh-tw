---
title: "// 建構函式註解 | Microsoft Docs"
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
  - "註解, 建構函式註解"
  - "註解, MFC"
  - "建構函式 [C++], 宣告"
  - "建構函式註解"
  - "宣告, 建構函式"
  - "宣告建構函式, 程式碼註解"
  - "執行個體建構函式, 程式碼註解"
  - "MFC 原始程式檔, 建構函式註解"
ms.assetid: f400774e-ba85-49ed-85b7-70ef2f7dcb2b
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# // 建構函式註解
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

MFC 類別宣告建構函式的 `// Constructors` 部分 \(C\+\+ 概念\) 以及要求的初始設定函式真正使用物件。  例如， `CWnd::Create` 會在建構函式中，因此，在您使用 `CWnd` 物件之前，必須藉由首先呼叫 C\+\+ 建構函式接著呼叫 **Create** 函式完全建構它」。  一般來說，這些成員都是公用的。  
  
 例如， `CStdioFile` 有三個建構函式的類別，一個在 [註解的範例](../mfc/an-example-of-the-comments.md)下的目錄顯示。  
  
## 請參閱  
 [使用 MFC 原始程式檔](../mfc/using-the-mfc-source-files.md)   
 [\/\/ 實作註解](../mfc/decrement-implementation-comment.md)   
 [\/\/ 屬性註解](../mfc/decrement-attributes-comment.md)   
 [\/\/ 作業註解](../mfc/decrement-operations-comment.md)   
 [\/\/ 可覆寫函式註解](../mfc/decrement-overridables-comment.md)