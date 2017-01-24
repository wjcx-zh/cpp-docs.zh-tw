---
title: "編譯器錯誤 C3395 | Microsoft Docs"
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
  - "C3395"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3395"
ms.assetid: 26a9ebc9-ed97-47ce-b436-19aa2bcf6e50
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3395
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'function' : \_\_declspec\(dllexport\) 無法套用至使用 \_\_clrcall 呼叫慣例的函式  
  
 `__declspec(dllexport)` 和 [\_\_clrcall](../../cpp/clrcall.md) 不相容。如需詳細資訊，請參閱[dllexport、dllimport](../../cpp/dllexport-dllimport.md)。  
  
 下列範例會產生 C3395：  
  
```  
// C3395.cpp  
// compile with: /clr /c  
  
__declspec(dllexport) void __clrcall Test(){}   // C3395  
void __clrcall Test2(){}   // OK  
__declspec(dllexport) void Test3(){}   // OK  
```