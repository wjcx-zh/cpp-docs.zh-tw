---
title: "編譯器警告 (層級 1) C4731 | Microsoft Docs"
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
  - "C4731"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4731"
ms.assetid: 5658c24c-3e6f-4505-835b-1fb92d47cab0
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 1) C4731
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'pointer' : 內嵌組譯碼程式碼已經修改框架指標暫存器 'register'  
  
 框架指標暫存器被修改。  您必須在內嵌組譯碼區塊或框架變數 \(區域或參數，視被修正的暫存器而定\) 中儲存並還原暫存器，否則您的程式碼可能無法正確地運作。  
  
 下列範例會產生 C4731：  
  
```  
// C4731.cpp  
// compile with: /W1 /LD  
// processor: x86  
// C4731 expected  
void bad(int p) {  
   __asm  
   {  
      mov ebp, 1  
   }  
  
   if (p == 1)  
   {  
      // ...  
   }  
}  
```  
  
 EBP 是被修改的框架指標 \(FPO 是不被允許的\)。  當 `p` 稍後被參考時，會被相關參考至 `EBP`。  但 `EBP` 已被程式碼覆寫，因此程式將無法正常運作，甚至會引起錯誤。