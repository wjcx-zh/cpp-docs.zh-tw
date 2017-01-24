---
title: "編譯器錯誤 C3413 | Microsoft Docs"
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
  - "C3413"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3413"
ms.assetid: de6c9b05-c373-4bd8-8cb0-12c2cd2e5674
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3413
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'name': 無效的明確具現化  
  
 編譯器偵測到格式不正確的明確具現化。  
  
 下列範例會產生 C3413：  
  
```  
// C3413.cpp template class MyClass {};   // C3413  
```  
  
 可能的解決方式：  
  
```  
// C3413b.cpp // compile with: /c template <class T> class MyClass {}; template <> class MyClass<int> {};  
```