---
title: "編譯器警告 (層級 1) C4384 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4384"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4384"
ms.assetid: fafa8eb2-cbfc-4edb-8b0f-511ff5d37ac0
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 1) C4384
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

\#pragma 'make\_public' 只應使用於全域範圍  
  
 [make\_public](../../preprocessor/make-public.md) pragma 套用不正確。  
  
## 範例  
 下列範例會產生 C4384。  
  
```  
// C4384.cpp  
// compile with: /c /W1  
namespace n {  
   #pragma make_public(N::C)   // C4384  
   namespace N {  
      class C {};  
   }  
}  
```