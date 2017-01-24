---
title: "編譯器錯誤 C2375 | Microsoft Docs"
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
  - "C2375"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2375"
ms.assetid: 193c5e8b-1b20-4928-8a02-8c1cddaf2a26
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2375
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'function': 重複定義; 連結規範不相同  
  
 已使用不同的連結規範宣告的函式。  
  
 下列範例會產生 C2375：  
  
```  
// C2375.cpp // compile with: /Za /c extern void func( void ); static void func( void );   // C2375 static void func2( void );   // OK  
```