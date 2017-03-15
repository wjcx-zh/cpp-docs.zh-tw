---
title: "編譯器警告 (層級 1) C4602 | Microsoft Docs"
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
  - "C4602"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4602"
ms.assetid: c1f0300f-e2a2-4c9e-a7c3-4c7318d10509
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 1) C4602
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

\#pragma pop\_macro: 必須先將 'macro name' 的名稱傳遞至 \#pragma push\_macro，才能使用這個識別項  
  
 如果您使用特定巨集的 [pop\_macro](../../preprocessor/pop-macro.md)，則必須先將該巨集名稱傳遞給 [push\_macro](../../preprocessor/push-macro.md)。 例如，下列範例會產生 C4602：  
  
```  
// C4602.cpp // compile with: /W1 int main() { #pragma pop_macro("x")   // C4602 x is not on the stack }  
```