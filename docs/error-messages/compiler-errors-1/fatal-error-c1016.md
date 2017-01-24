---
title: "嚴重錯誤 C1016 | Microsoft Docs"
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
  - "C1016"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1016"
ms.assetid: 33f45c3e-2d8f-43ad-a445-c412d1d54ce1
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 嚴重錯誤 C1016
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

\#ifdef 必須是識別項\#ifndef 必須是識別項  
  
 條件式編譯指示詞 \([\#ifdef](../../preprocessor/hash-ifdef-and-hash-ifndef-directives-c-cpp.md) 或 `#ifndef`\) 沒有要評估的識別項。 若要解決這個錯誤，請指定識別項。  
  
 下列範例會產生 C1016：  
  
```  
// C1016.cpp #ifdef   // C1016 #define FC1016 #endif int main() {}  
```  
  
 可能的解決方式：  
  
```  
// C1016b.cpp #ifdef X #define FC1016 #endif int main() {}  
```