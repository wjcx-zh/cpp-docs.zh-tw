---
title: "編譯器錯誤 C2935 | Microsoft Docs"
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
  - "C2935"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2935"
ms.assetid: e11ef90d-0756-4e43-8a09-4974c6aa72a3
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2935
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'class': type\-class\-id 重複定義為全域函式  
  
 您無法使用泛型或樣板類別作為全域函式。  
  
 此錯誤可能是大括弧不對稱所造成。  
  
 下列範例會產生 C2935：  
  
```  
// C2935.cpp // compile with: /c template<class T> struct TC {}; void TC<int>() {}   // C2935 // OK struct TC2 {}; void TC2() {}  
```  
  
 使用泛型時，也會發生 C2935：  
  
```  
// C2935b.cpp // compile with: /clr /c generic<class T> ref struct GC { }; void GC<int>() {}   // C2935 void GC() {}   // OK  
```