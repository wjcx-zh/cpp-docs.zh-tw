---
title: "編譯器警告 (層級 2) C4056 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4056"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4056"
ms.assetid: a3c3a9b8-ec30-452d-96cb-3694adcce789
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 編譯器警告 (層級 2) C4056
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在浮點常數算術中溢位  
  
 浮點常數算術產生超出最大容許值的結果。  
  
 這項警告可能是因在常數算術期間執行編譯器最佳化而造成。  關閉最佳化 \([\/Od](../../build/reference/od-disable-debug.md)\) 時，如果這項警告消失，您可以安然地忽略它。  
  
 下列範例會產生 C4056：  
  
```  
// C4056.cpp  
// compile with: /W2 /LD  
#pragma warning (default : 4056)  
float fp_val = 1.0e300 * 1.0e300;   // C4056  
```