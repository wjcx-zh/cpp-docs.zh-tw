---
title: "嚴重錯誤 C1019 | Microsoft Docs"
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
  - "C1019"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1019"
ms.assetid: c4f8968b-bc62-4200-b3ca-69d06c163236
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 嚴重錯誤 C1019
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

未預期的 \#else  
  
 `#else` 指示詞出現在 `#if`、`#ifdef` 或 `#ifndef` 建構外部。 請僅在其中一個建構內使用 `#else`。  
  
 下列範例會產生 C1019：  
  
```  
// C1019.cpp #else   // C1019 #endif int main() {}  
```  
  
 可能的解決方式：  
  
```  
// C1019b.cpp #if 1 #else #endif int main() {}  
```