---
title: "編譯器警告 (層級 4) C4918 | Microsoft Docs"
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
  - "C4918"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4918"
ms.assetid: 1bcf6d35-3467-4aa8-b2ef-cb33f4e70238
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 4) C4918
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'character' : 在 pragma 最佳化清單中的無效字元  
  
 在[最佳化](../../preprocessor/optimize.md) pragma 陳述式的最佳化清單中找到未知的字元。  
  
 例如，下列陳述式會產生 C4918：  
  
```  
// C4918.cpp // compile with: /W4 #pragma optimize("X", on) // C4918 expected int main() { }  
```