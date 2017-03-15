---
title: "編譯器錯誤 C2486 | Microsoft Docs"
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
  - "C2486"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2486"
ms.assetid: 436da349-6461-4e32-bfca-4f3e620108e2
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2486
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'\_\_LOCAL\_SIZE' 只能在具有 'naked' 屬性的函式中使用  
  
 在內嵌組譯碼函式中，`__LOCAL_SIZE` 名稱是保留給使用 [naked](../../cpp/naked-cpp.md) 屬性宣告的函式。  
  
 下列範例會產生 C2486：  
  
```  
// C2486.cpp  
// processor: x86  
void __declspec(naked) f1() {  
   __asm {  
      mov   eax,   __LOCAL_SIZE  
   }  
}  
void f2() {  
   __asm {  
      mov   eax,   __LOCAL_SIZE   // C2486  
   }  
}  
```