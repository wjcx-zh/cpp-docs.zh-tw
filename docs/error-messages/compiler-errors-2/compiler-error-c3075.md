---
title: "編譯器錯誤 C3075 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3075"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3075"
ms.assetid: f431daa9-e0fa-48f0-a5c3-f99be96b55e3
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# 編譯器錯誤 C3075
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'instance' : 不可將參考類型的執行個體 'type' 嵌入實值類型中  
  
 實值類型不能包含參考類型的執行個體。  
  
 如需詳細資訊，請參閱[參考類型的 C\+\+ 堆疊語意](../../dotnet/cpp-stack-semantics-for-reference-types.md)。  
  
## 範例  
 下列範例會產生 C3075。  
  
```  
// C3075.cpp // compile with: /clr /c ref struct U {}; value struct X { U y;   // C3075 }; ref struct Y { U y;   // OK };  
```