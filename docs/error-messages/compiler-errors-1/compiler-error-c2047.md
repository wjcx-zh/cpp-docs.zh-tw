---
title: "編譯器錯誤 C2047 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C2047"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2047"
ms.assetid: 686a5a81-3857-4753-84a0-5c2e7149cbee
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 編譯器錯誤 C2047
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

default 的使用不合法  
  
 關鍵字 `default` 僅可出現在 `switch` 陳述式中。  
  
 下列範例會產生C2047：  
  
```  
// C2047.cpp int main() { int i = 0; default:   // C2047 switch(i) { case 0: break; } }  
```  
  
 可能的解決方式：  
  
```  
// C2047b.cpp int main() { int i = 0; switch(i) { case 0: break; default: break; } }  
```