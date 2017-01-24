---
title: "編譯器錯誤 C2033 | Microsoft Docs"
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
  - "C2033"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2033"
ms.assetid: fd5a1637-9db2-4c98-a7cc-b63b39737cd9
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2033
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identifier': 位元欄位無法間接取值  
  
 位元欄位已宣告為指標，這是不允許的做法。  
  
 下列範例會產生 C2033：  
  
```  
// C2033.cpp struct S { int *b : 1;  // C2033 };  
```  
  
 可能的解決方式：  
  
```  
// C2033b.cpp // compile with: /c struct S { int b : 1; };  
```