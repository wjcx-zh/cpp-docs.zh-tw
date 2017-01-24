---
title: "編譯器錯誤 C2165 | Microsoft Docs"
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
  - "C2165"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2165"
ms.assetid: b108313b-b8cb-4dce-b2ec-f2b31c9cdc87
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2165
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'keyword': 無法修飾指向資料的指標  
  
 `__stdcall`、`__cdecl` 或 `__fastcall` 關鍵字嘗試修改資料的指標。  
  
 下列範例會產生 C2165：  
  
```  
// C2165.cpp // compile with: /c char __cdecl *p;   // C2165 char *p;   // OK  
```