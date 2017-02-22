---
title: "嚴重錯誤 C1018 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C1018"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1018"
ms.assetid: 2ceb8a99-30b2-4b80-bf42-e9f3305b3c52
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 嚴重錯誤 C1018
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

未預期的 \#elif  
  
 `#elif` 指示詞出現在 `#if`、`#ifdef` 或 `#ifndef` 建構外部。 請僅在其中一個建構內使用 `#elif`。  
  
 下列範例會產生 C1018：  
  
```  
// C1018.cpp #elif      // C1018 #endif int main() {}  
```  
  
 可能的解決方式：  
  
```  
// C1018b.cpp #if 1 #elif #endif int main() {}  
```