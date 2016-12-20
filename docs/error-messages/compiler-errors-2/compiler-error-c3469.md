---
title: "編譯器錯誤 C3469 | Microsoft Docs"
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
  - "C3469"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3469"
ms.assetid: e23b0e5c-c704-4e67-a868-bf02c2055d85
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3469
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'type': 泛型類別無法轉送  
  
 您無法對泛型類別使用類型轉送。  
  
 如需詳細資訊，請參閱[Type Forwarding \(C\+\+\/CLI\)](../../windows/type-forwarding-cpp-cli.md)。  
  
## 範例  
 下列範例會建立元件。  
  
```  
// C3469.cpp // compile with: /clr /LD generic<typename T> public ref class GR {}; public ref class GR2 {};  
```  
  
## 範例  
 下列範例會產生 C3466。  
  
```  
// C3469_b.cpp // compile with: /clr /c #using "C3469.dll" [assembly:TypeForwardedTo(GR::typeid)];   // C3469 [assembly:TypeForwardedTo(GR2::typeid)];   // OK  
```