---
title: "編譯器錯誤 C3084 | Microsoft Docs"
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
  - "C3084"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3084"
ms.assetid: 0362cb70-e24e-476f-a24d-8f5bb97c3afd
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3084
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'function': 完成項\/解構函式不能是 'keyword'  
  
 不正確地宣告完成項或解構函式。  
  
 例如，解構函式不應該標示為密封。  衍生類型將無法存取解構函式。  如需詳細資訊，請參閱[明確覆寫](../../windows/explicit-overrides-cpp-component-extensions.md)和[Visual C\+\+ 中的解構函式和完成項](../../misc/destructors-and-finalizers-in-visual-cpp.md)。  
  
## 範例  
 下列範例會產生 C3084。  
  
```  
// C3084.cpp // compile with: /clr /c ref struct R { protected: !R() sealed;   // C3084 !R() abstract;   // C3084 !R(); };  
```