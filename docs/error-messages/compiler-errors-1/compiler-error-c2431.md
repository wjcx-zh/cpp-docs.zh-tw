---
title: "編譯器錯誤 C2431 | Microsoft Docs"
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
  - "C2431"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2431"
ms.assetid: 88a5b648-c89f-47d1-a20e-63231ab4f0f7
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2431
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identifier' 中有不合法的索引暫存器  
  
 ESP 暫存器被調整，或同時做為索引和基底 \(Base\) 暫存器使用。  x86 處理器的 SIB 編碼不允許上列任一情況。  
  
 下列範例會產生 C2431：  
  
```  
// C2431.cpp  
// processor: x86  
int main() {  
   _asm mov ax, [ESI + 2*ESP]   // C2431  
   _asm mov ax, [esp + esp]   // C2431  
}  
```