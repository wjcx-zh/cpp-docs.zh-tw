---
title: "編譯器錯誤 C2283 | Microsoft Docs"
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
  - "C2283"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2283"
ms.assetid: 8a5b3175-b480-4598-a1f7-0b50504c5caa
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2283
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identifier': 不允許在未命名的結構上使用純虛擬函式規範或抽象覆寫規範  
  
 不允許使用純規範來宣告未命名的類別或結構的成員函式。  
  
 下列範例會產生 C2283：  
  
```  
// C2283.cpp // compile with: /c struct { virtual void func() = 0;   // C2283 }; struct T { virtual void func() = 0;   // OK };  
```