---
title: "編譯器錯誤 C2430 | Microsoft Docs"
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
  - "C2430"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2430"
ms.assetid: 07c20f76-63e1-4d22-b2a9-98b0d45c5cac
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2430
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identifier' 中有超過一個以上的索引暫存器  
  
 調整了一個以上的暫存器。  編譯器可支援數值索引 \(Scaled Indexing\)，但您只能調整一個暫存器。  
  
## 範例  
 下列範例會產生 C2430。  
  
```  
// C2430.cpp  
// processor: x86  
int main() {  
   _asm mov eax, [ebx*2+ecx*4] // C2430  
}  
```