---
title: "編譯器警告 (層級 1) C4722 | Microsoft Docs"
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
  - "C4722"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4722"
ms.assetid: d8660710-f67b-4f59-a5fd-59259475529e
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 1) C4722
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'function' : 解構函式從未返回，可能有記憶體遺漏  
  
 控制流程會在解構函式終止。 執行緒或整個程式會終止，且可能不會釋放已配置的資源。  此外，如果例外狀況的處理期間將呼叫解構函式以進行堆疊回溯，則未定義可執行檔的行為。  
  
 若要解決，請移除導致解構函式不返回的函式呼叫。  
  
## 範例  
 下列範例會產生 C4722：  
  
```  
// C4722.cpp // compile with: /O1 /W1 /c #include <stdlib.h> class C { public: C(); ~C() { exit(1); };   // C4722 }; extern void func (C*); void Test(){ C x; func(&x); // control will not leave Test because destructor will exit }  
```