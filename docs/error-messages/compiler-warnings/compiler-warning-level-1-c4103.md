---
title: "編譯器警告 (層級 1) C4103 | Microsoft Docs"
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
  - "C4103"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4103"
ms.assetid: 9021b514-375e-4d62-b261-ccb06f299e8e
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 1) C4103
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'filename' : 記憶體對齊在包含標頭之後變更了，可能是遺漏了 \#pragma pack\(pop\)  
  
 封裝會影響類別的配置，而且通常，如果封裝在跨標頭檔時變更，就可能會出問題。  
  
 結束標頭檔之前，使用 \#pragma [pack](../../preprocessor/pack.md)\(pop\) 解除這項警告。  
  
 下列範例會產生 C4103：  
  
```  
// C4103.h  
#pragma pack(push, 4)  
  
// defintions and declarations  
  
// uncomment the following line to resolve  
// #pragma pack(pop)  
```  
  
 然後，  
  
```  
// C4103.cpp  
// compile with: /LD /W1  
#include "c4103.h"   // C4103  
```