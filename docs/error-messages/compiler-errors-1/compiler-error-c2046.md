---
title: "編譯器錯誤 C2046 | Microsoft Docs"
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
  - "C2046"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2046"
ms.assetid: f0c8f9dd-dbd7-4c4a-8838-fde54208ec71
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2046
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

case 的使用不合法  
  
 關鍵字 `case` 僅可出現在 `switch` 陳述式中。  
  
 下列範例會產生 C2046：  
  
```  
// C2046.cpp int main() { case 0:   // C2046 }  
```  
  
 可能的解決方式：  
  
```  
// C2046b.cpp int main() { int i = 0; switch(i) { case 0: break; default: break; } }  
```