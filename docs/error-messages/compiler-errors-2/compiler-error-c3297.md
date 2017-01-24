---
title: "編譯器錯誤 C3297 | Microsoft Docs"
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
  - "C3297"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3297"
ms.assetid: 2a718b4c-6cdb-4418-92c0-fc3a259431c4
caps.latest.revision: 3
caps.handback.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3297
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'constraint\_2': 因為 'constraint\_1' 有值條件約束，所以 'constraint\_1' 不能用做條件約束  
  
 值類別已密封。 如果條件約束是值類別，它絕對不會衍生其他的條件約束。  
  
 如需詳細資訊，請參閱[Constraints on Generic Type Parameters \(C\+\+\/CLI\)](../../windows/constraints-on-generic-type-parameters-cpp-cli.md)。  
  
## 範例  
 下列範例會產生 C3297。  
  
```  
// C3297.cpp // compile with: /clr /c generic<class T, class U> where T : value class where U : T   // C3297 public ref struct R {};  
```