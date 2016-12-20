---
title: "編譯器錯誤 C3467 | Microsoft Docs"
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
  - "C3467"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3467"
ms.assetid: e2b844d0-4920-412f-99fd-cd8051c4aa41
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3467
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'type': 這個類型已經轉送了  
  
 編譯器發現相同類型的多個轉送類型宣告。 每種類型只允許一個宣告。  
  
 如需詳細資訊，請參閱[Type Forwarding \(C\+\+\/CLI\)](../../windows/type-forwarding-cpp-cli.md)。  
  
## 範例  
 下列範例會建立元件。  
  
```  
// C3467.cpp // compile with: /LD /clr public ref class R {};  
```  
  
## 範例  
 下列範例會產生 C3467。  
  
```  
// C3467_b.cpp // compile with: /clr /c #using "C3467.dll" [ assembly:TypeForwardedTo(R::typeid) ]; [ assembly:TypeForwardedTo(R::typeid) ];   // C3467  
```