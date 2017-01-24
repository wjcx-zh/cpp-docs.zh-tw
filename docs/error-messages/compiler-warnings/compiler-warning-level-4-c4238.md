---
title: "編譯器警告 (層級 4) C4238 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4238"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4238"
ms.assetid: 5d4051d3-7b0f-43ea-8c8d-d194bfdceb71
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 4) C4238
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用非標準的擴充：類別右值當做左值使用  
  
 為了能與前一版的 Visual C\+\+ 相容，Microsoft 擴充功能 \(**\/Ze**\) 可以讓您在隱含或明確取得其位址的內容中，將類別型別當做右值使用。  在某些情況下，如同下列範例所示，這麼做可能會有危險。  
  
## 範例  
  
```  
// C4238.cpp  
// compile with: /W4 /c  
struct C {  
   C() {}  
};  
  
C * pC = &C();   // C4238  
```  
  
 這種用法在 ANSI 相容性 \([\/Za](../../build/reference/za-ze-disable-language-extensions.md)\) 會引起錯誤。