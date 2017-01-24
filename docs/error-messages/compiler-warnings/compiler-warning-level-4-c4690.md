---
title: "編譯器警告 (層級 4) C4690 | Microsoft Docs"
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
  - "C4690"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4690"
ms.assetid: 080a0ea1-458b-477b-a37a-4a34c94709ff
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 4) C4690
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

\[ emitidl\( pop \) \]: pop 的數目必須和 push 相同，否則可能導致非預期的行為  
  
 [emitidl](../../windows/emitidl.md) 屬性的 pop 作業比 push 作業多一次。  
  
## 範例  
 下列範例會產生 C4690。  
  
```  
// C4690.cpp // compile with: /c /W4 [emitidl(pop)];   // C4690 class x {};  
```