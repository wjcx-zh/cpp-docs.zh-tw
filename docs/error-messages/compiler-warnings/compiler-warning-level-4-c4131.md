---
title: "編譯器警告 (層級 4) C4131 | Microsoft Docs"
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
  - "C4131"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4131"
ms.assetid: 7903b3e1-454f-4be2-aa9b-230992f96a2d
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 4) C4131
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'function': 使用舊樣式的宣告子  
  
 指定的函式宣告不是原型形式。  
  
 舊樣式函式宣告應該轉換成原型形式。  
  
 下列範例示範舊樣式函式宣告：  
  
```  
// C4131.c // compile with: /W4 /c void addrec( name, id ) // C4131 expected char *name; int id; { }  
```  
  
 下列範例示範原型形式：  
  
```  
void addrec( char *name, int id ) { }  
```