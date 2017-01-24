---
title: "嚴重錯誤 C1070 | Microsoft Docs"
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
  - "C1070"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1070"
ms.assetid: 1058269a-5db6-4c23-a97f-b5269eb9188b
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 嚴重錯誤 C1070
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

檔案 'filename' 中 \#if\/\#endif 的配對不相符  
  
 `#if`、`#ifdef` 或 `#ifndef` 指示詞沒有相對應的 `#endif`。  
  
 下列範例會產生 C1070：  
  
```  
// C1070.cpp #define TEST #ifdef TEST #ifdef TEST #endif // C1070  
```  
  
 可能的解決方式：  
  
```  
// C1070b.cpp // compile with: /c #define TEST #ifdef TEST #endif #ifdef TEST #endif  
```