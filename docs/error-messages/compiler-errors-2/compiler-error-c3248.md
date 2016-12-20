---
title: "編譯器錯誤 C3248 | Microsoft Docs"
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
  - "C3248"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3248"
ms.assetid: d00b9d7d-b6be-4a5b-bb52-48174ea71fc4
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3248
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'function1': 宣告為 '\_\_sealed' 的函式不可被 'function2' 覆寫  
  
 衍生類別已嘗試覆寫 [\_\_sealed](../../misc/sealed.md) 虛擬方法。  
  
 僅可使用 **\/clr:oldSyntax** 連接 C3248。  
  
 下列範例會產生 C3248：  
  
```  
// C3248b.cpp // compile with: /clr:oldSyntax using namespace System; __gc struct B { __sealed virtual void func(); }; __gc struct D : B { void func();   // C3248 };  
```