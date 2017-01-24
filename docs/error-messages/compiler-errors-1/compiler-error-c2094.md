---
title: "編譯器錯誤 C2094 | Microsoft Docs"
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
  - "C2094"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2094"
ms.assetid: 9e4f8f88-f189-46e7-91c9-481bacc7af87
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2094
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

標籤 'identifier' 未定義  
  
 函式中沒有 [goto](../Topic/goto%20\(C%23%20Reference\).md) 陳述式所使用的標籤。  
  
 下列範例會產生 C2094：  
  
```  
// C2094.c int main() { goto test; }   // C2094  
```  
  
 可能的解決方式：  
  
```  
// C2094b.c int main() { goto test; test: { } }  
```