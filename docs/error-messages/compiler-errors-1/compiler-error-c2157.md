---
title: "編譯器錯誤 C2157 | Microsoft Docs"
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
  - "C2157"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2157"
ms.assetid: babbca24-16dc-4b69-be14-a675029249c1
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2157
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'function': 在 pragma 清單中使用之前必須先宣告  
  
 未宣告函式名稱，便在 [alloc\_text](../../preprocessor/alloc-text.md) pragma 的函式清單中參考此名稱。  
  
 下列範例會產生 C2157：  
  
```  
// C2157.cpp // compile with: /c #pragma alloc_text( "func", func)   // C2157 // OK extern "C" void func(); #pragma alloc_text( "func", func)  
```