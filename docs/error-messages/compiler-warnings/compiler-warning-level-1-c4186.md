---
title: "編譯器警告 (層級 1) C4186 | Microsoft Docs"
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
  - "C4186"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4186"
ms.assetid: caf3f7d8-f305-426b-8d4e-2b96f5c269ea
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 1) C4186
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

\#import 屬性 'attribute' 需要計數引數；己忽略  
  
 `#import` 屬性的引數數目錯誤。  
  
## 範例  
  
```  
// C4186.cpp // compile with: /W1 /c #import "stdole2.tlb" no_namespace("abc") rename("a","b","c")  // C4186  
```  
  
 `no_namespace` 屬性不需使用引數。**rename** 屬性僅需使用兩個引數。