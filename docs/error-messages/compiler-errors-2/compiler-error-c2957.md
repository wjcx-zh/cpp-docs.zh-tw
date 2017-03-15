---
title: "編譯器錯誤 C2957 | Microsoft Docs"
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
  - "C2957"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2957"
ms.assetid: 9cb4526f-4af8-47e9-b786-56192627ca72
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2957
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'delim': 左分隔符號無效: 必須是 '\<'  
  
 泛型類別的格式錯誤。  
  
 下列範例會產生 C2957：  
  
```  
// C2957.cpp // compile with: /clr /LD generic << class T>   // C2957 // try the following line instead // generic < class T> gc class C {};  
```