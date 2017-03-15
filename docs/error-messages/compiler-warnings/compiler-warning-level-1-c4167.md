---
title: "編譯器警告 (層級 1) C4167 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4167"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4167"
ms.assetid: 74a420bd-9371-4167-b1ee-74dd8680f97b
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 編譯器警告 (層級 1) C4167
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

函式：僅供用為內建函式  
  
 **\#pragma 函式**嘗試強制編譯器對必須用於內建形式的函式使用傳統呼叫。 忽略 pragma。  
  
 若要避免這個警告，請移除 **\#pragma 函式**。  
  
## 範例  
  
```  
// C4167.cpp // compile with: /W1 #include <malloc.h> #pragma function(_alloca )   // C4167: _alloca() is intrinsic only int main(){}  
```