---
title: "編譯器警告 (層級 1) C4920 | Microsoft Docs"
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
  - "C4920"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4920"
ms.assetid: 1e501f2e-93c1-4d27-a4fa-54fc86271ae7
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 1) C4920
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

enum 列舉成員 \(成員\=值\) 已出現在 enum 列舉中作為成員\=值  
  
 如果您傳遞至 \#import 的 .tlb 具有定義於兩個或多個列舉中的相同符號，則這個警告表示後續相同的符號將被忽略，而且會在 .tlh 檔中標記為註解。  
  
 假設 .tlb 包含：  
  
```  
library MyLib { typedef enum { enumMember = 512 } AProblem; typedef enum { enumMember = 1024 } BProblem; };  
```  
  
 下列範例會產生 C4920。  
  
```  
// C4920.cpp // compile with: /W1 #import "t4920.tlb"   // C4920 int main() { }  
```