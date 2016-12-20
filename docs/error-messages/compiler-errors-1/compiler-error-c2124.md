---
title: "編譯器錯誤 C2124 | Microsoft Docs"
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
  - "C2124"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2124"
ms.assetid: 93392aaa-5582-4d68-8cc5-bd9c62a0ae7e
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2124
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

除以 0 或取除以 0 的餘數  
  
 常數運算式的分母為零。 若要解決此錯誤，請勿除以零。  
  
 下列範例會產生 C2124：  
  
```  
// C2124.cpp int main() { int i = 1 / 0;   // C2124  do not divide by zero int i2 = 12 / 2;   // OK }  
```