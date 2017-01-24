---
title: "編譯器錯誤 C3384 | Microsoft Docs"
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
  - "C3384"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3384"
ms.assetid: c9f92c6a-62a9-4333-b2b1-bc55c7f288b6
caps.latest.revision: 3
caps.handback.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3384
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'type\_parameter': 數值條件約束和 ref 條件約束互斥  
  
 您不能將泛型類型限制為 `value class` 和 `ref class`。  
  
 如需詳細資訊，請參閱 [Constraints on Generic Type Parameters \(C\+\+\/CLI\)](../../windows/constraints-on-generic-type-parameters-cpp-cli.md)。  
  
## 範例  
 下列範例會產生 C3384。  
  
```  
// C3384.cpp // compile with: /c /clr generic <typename T> where T : ref class where T : value class   // C3384 ref class List {};  
```