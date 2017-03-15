---
title: "編譯器警告 (層級 3) C4334 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4334"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4334"
ms.assetid: d845857f-bc95-4faf-a079-626a0cf935ba
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 編譯器警告 (層級 3) C4334
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'operator' : 32 位元位移的結果已隱含轉換為 64 位元 \(是否原來就是要進行 64 位元位移?\)  
  
 32 位元位移的結果已以隱含方式轉換為 64 位元，而編譯器以為原來是要進行 64 位元位移。若要解除這項警告，請使用 64 位元位移，或明確地將位移結果轉換為 64 位元。  
  
## 範例  
 下列範例會產生 C4334。  
  
```  
// C4334.cpp  
// compile with: /W3 /c  
void SetBit(unsigned __int64 *p, int i) {  
   *p |= (1 << i);   // C4334  
   *p |= (1i64 << i);   // OK  
}  
```