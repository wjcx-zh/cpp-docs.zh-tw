---
title: "編譯器警告 (層級 1) C4272 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4272"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4272"
ms.assetid: 0d6c1de4-2eef-42c4-b861-c221f8b495ef
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 編譯器警告 (層級 1) C4272
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'function' : 為 marked \_\_declspec\(dllimport\)；匯入函式時，必須指定原生呼叫慣例 \(Calling Convention\)。  
  
 匯出以 [\_\_clrcall](../../cpp/clrcall.md) 呼叫慣例標示的函式是錯誤，如果您嘗試匯入標示為 `__clrcall` 的函式，編譯器就會發出這項警告。  
  
 下列範例會產生 C4272：  
  
```  
// C4272.cpp  
// compile with: /c /W1 /clr  
__declspec(dllimport) void __clrcall Test();   // C4272  
__declspec(dllimport) void Test2();   // OK  
```