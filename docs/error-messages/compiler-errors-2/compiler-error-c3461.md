---
title: "編譯器錯誤 C3461 | Microsoft Docs"
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
  - "C3461"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3461"
ms.assetid: bd66833a-545d-445a-bdfe-dee771a450a4
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3461
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'type': 只能轉送 Managed 類型  
  
 類型轉送只能在 CLR 類型上執行。  如需詳細資訊，請參閱 [Classes and Structs](../../windows/classes-and-structs-cpp-component-extensions.md)。  
  
 如需詳細資訊，請參閱[Type Forwarding \(C\+\+\/CLI\)](../../windows/type-forwarding-cpp-cli.md)。  
  
## 範例  
 下列範例會建立元件。  
  
```  
// C3461.cpp // compile with: /clr /LD public ref class R {};  
```  
  
## 範例  
 下列範例會產生 C3461。  
  
```  
// C3461b.cpp // compile with: /clr /c #using "C3461.dll" class N {}; [assembly:TypeForwardedTo(N::typeid)];   // C3461 [assembly:TypeForwardedTo(R::typeid)];   // OK  
```