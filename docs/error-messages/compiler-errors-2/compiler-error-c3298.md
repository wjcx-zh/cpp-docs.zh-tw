---
title: "編譯器錯誤 C3298 | Microsoft Docs"
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
  - "C3298"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3298"
ms.assetid: 458c2680-95bb-4d5e-895f-ce4115844193
caps.latest.revision: 3
caps.handback.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3298
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'constraint\_1': 無法將 'constraint\_2' 當做條件約束使用，因為 'constraint\_2' 具有 ref 條件約束，而且 'constraint\_1' 具有值條件約束  
  
 您不能指定條件約束的互斥特性。 例如，泛型類型參數不能同時限制為實值類型和參考類型。  
  
 如需詳細資訊，請參閱[Constraints on Generic Type Parameters \(C\+\+\/CLI\)](../../windows/constraints-on-generic-type-parameters-cpp-cli.md)。  
  
## 範例  
 下列範例會產生 C3298。  
  
```  
// C3298.cpp // compile with: /clr /c generic<class T, class U> where T : ref class where U : T, value class   // C3298 public ref struct R {};  
```