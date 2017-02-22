---
title: "嚴重錯誤 C1202 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C1202"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1202"
ms.assetid: c859adb8-17a7-4fa1-a1f3-5820b7bf3849
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# 嚴重錯誤 C1202
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

遞迴類型或函式相依內容太複雜  
  
 範本定義是遞迴的或超過複雜度限制。  
  
## 範例  
 下列範例會產生 C1202。  
  
```  
// C1202.cpp // processor: x86 IPF template<int n> class Factorial : public Factorial<n-1>  {   // C1202 public: operator int () { return Factorial <n-1>::operator int () * n; } }; Factorial<7> facSeven;  
```  
  
## 範例  
 可能的解決方式。  
  
```  
// C1202b.cpp // compile with: /c template<int n> class Factorial : public Factorial<n-1> { public: operator int () { return Factorial <n-1>::operator int () * n; } }; template <> class Factorial<0> { public: operator int () { return 1; } }; Factorial<7> facSeven;  
```