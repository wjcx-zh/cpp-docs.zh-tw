---
title: "編譯器錯誤 C2937 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C2937"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2937"
ms.assetid: 95671ca3-79f7-4b56-a5f2-a92296da1629
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 編譯器錯誤 C2937
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'class': type\-class\-id 重複定義為全域 typedef  
  
 您無法使用泛型或樣板類別作為全域 `typedef`。  
  
 下列範例會產生 C2937：  
  
```  
// C2937.cpp // compile with: /c template<class T> struct TC { }; typedef int TC<int>;   // C2937 typedef TC<int> c;   // OK  
```  
  
 使用泛型時，也會發生 C2937：  
  
```  
// C2937b.cpp // compile with: /clr generic<class T> ref struct GC { }; typedef int GC<int>;   // C2937 typedef GC<int> xx;   // OK  
```