---
title: "編譯器錯誤 C3080 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3080"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3080"
ms.assetid: ff62a3f7-9b3b-44bd-b8d9-f3a8e5354560
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3080
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'finalizer\_function': 完成項不能有儲存類別規範  
  
 如需詳細資訊，請參閱[Visual C\+\+ 中的解構函式和完成項](../../misc/destructors-and-finalizers-in-visual-cpp.md)。  
  
## 範例  
 下列範例會產生 C3080。  
  
```  
// C3080.cpp // compile with: /clr /c ref struct rs { protected: static !rs(){}   // C3080 !rs(){}   // OK };  
```