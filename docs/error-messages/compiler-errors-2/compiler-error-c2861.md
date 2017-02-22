---
title: "編譯器錯誤 C2861 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2861"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2861"
ms.assetid: 012bb44d-6c9b-4def-b54e-b19f1f8ddd1b
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 編譯器錯誤 C2861
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'function name' : 無法定義的介面成員函式  
  
 編譯器 \(Compiler\) 遇到 interface 關鍵字或將結構推算為介面，但之後卻找到成員函式定義。介面無法包含成員函式的定義。  
  
## 範例  
 下列範例會產生 C2861：  
  
```  
// C2861.cpp  
// compile with: /c  
#include <objbase.h>   // required for IUnknown definition  
[ object, uuid("00000000-0000-0000-0000-000000000001") ]  
__interface IMyInterface : IUnknown {  
   HRESULT mf(int a);  
};  
  
HRESULT IMyInterface::mf(int a) {}   // C2861  
  
```