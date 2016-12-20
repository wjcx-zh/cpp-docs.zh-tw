---
title: "編譯器錯誤 C2432 | Microsoft Docs"
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
  - "C2432"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2432"
ms.assetid: 0e3326e8-cab1-45a5-b48d-61edd33793e8
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2432
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

參考 'identifier' 中 16 位元資料不合法  
  
 16 位元暫存器可做為索引或基底暫存器。  編譯器並不支援參考 16 位元的資料。在編譯 32 位元的程式碼時，16 位元的暫存器不能做為索引或基底暫存器。  
  
 下列範例會產生 C2432：  
  
```  
// C2432.cpp  
// processor: x86  
int main() {  
   _asm mov eax, DWORD PTR [bx]   // C2432  
}  
```