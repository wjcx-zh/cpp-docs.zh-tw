---
title: "編譯器錯誤 C2710 | Microsoft Docs"
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
  - "C2710"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2710"
ms.assetid: a2a6bb5b-86ad-4a6c-acd0-e2bef8464e0e
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2710
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'construct' : '\_\_declspec\(modifier\)' 只可以套用至傳回指標的函式  
  
 傳回值為指標的函式是可以套用 `modifier` 的唯一建構。  
  
 下列範例會產生 C2710：  
  
```  
// C2710.cpp  
__declspec(restrict) void f();   // C2710  
// try the following line instead  
__declspec(restrict) int * g();  
```