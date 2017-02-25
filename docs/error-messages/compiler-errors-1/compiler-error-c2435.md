---
title: "編譯器錯誤 C2435 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2435"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2435"
ms.assetid: be6aa8f8-579b-42ea-bdd8-2d01393646ad
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# 編譯器錯誤 C2435
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'var' : 動態初始設定必須有 Managed CRT，不能以 \/clr:safe 編譯  
  
 每個應用程式定義域變數的全域初始設定必須要有以 `/clr:pure` 編譯的 CRT，它不會產生可驗證的影像。  
  
 如需詳細資訊，請參閱 [appdomain](../../cpp/appdomain.md) 和 [process](../../cpp/process.md)。  
  
 下列範例會產生 C2435：  
  
```  
// C2435.cpp  
// compile with: /clr:safe /c  
int globalvar = 0;   // C2435  
  
__declspec(process)  
int globalvar2 = 0;  
```