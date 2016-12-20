---
title: "編譯器錯誤 C2150 | Microsoft Docs"
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
  - "C2150"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2150"
ms.assetid: 21e82a10-c1d4-4c0d-9dc6-c5d92ea42a31
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2150
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identifier' : 位元欄位必須是 'int'、'signed int' 或 'unsigned int' 類型  
  
 位元欄位必須是 `int`、`signed``int` 或 `unsigned``int`。  
  
 下列範例會產生 C2150：  
  
```  
// C2150.cpp // compile with: /c struct A { float a : 8;    // C2150 int i : 8;   // OK };  
```