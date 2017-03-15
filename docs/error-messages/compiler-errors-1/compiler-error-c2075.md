---
title: "編譯器錯誤 C2075 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C2075"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2075"
ms.assetid: 8b1865d2-540b-4117-b982-e7a58a0b6cf7
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 編譯器錯誤 C2075
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identifier': 陣列初始化需要使用大括號  
  
 指定的陣列初始設定式未以大括號括住。  
  
 下列範例會產生 C2075：  
  
```  
// C2075.c int main() { int i[] = 1, 2, 3 };   // C2075 }  
```  
  
 可能的解決方式：  
  
```  
// C2075b.c int main() { int j[] = { 1, 2, 3 }; }  
```