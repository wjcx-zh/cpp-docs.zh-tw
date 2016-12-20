---
title: "編譯器錯誤 C3085 | Microsoft Docs"
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
  - "C3085"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3085"
ms.assetid: 1ac40bf2-f63e-439e-8921-47e6dadc8354
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3085
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'constructor': 建構函式不能是 'keyword'  
  
 建構函式宣告不正確。 如需詳細資訊，請參閱 [覆寫規範](../../windows/override-specifiers-cpp-component-extensions.md)。  
  
## 範例  
 下列範例會產生 C3085：  
  
```  
// C3085.cpp // compile with: /c /clr ref struct S { S() abstract;   // C3085 S(S%) abstract;   // C3085 }; ref struct T { T() sealed {}   // C3085 T(T%) sealed {}   // C3085 };  
```