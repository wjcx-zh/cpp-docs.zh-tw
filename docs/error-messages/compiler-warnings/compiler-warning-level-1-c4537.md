---
title: "編譯器警告 (層級 1) C4537 | Microsoft Docs"
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
  - "C4537"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4537"
ms.assetid: 9454493c-d419-475e-8f35-9c00233c9329
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 1) C4537
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'object' : 'operator' 套用至非 UDT 型別  
  
 參考被傳遞到預期物件 \(使用者定義型別\) 之處。  參考不是物件，但內嵌組譯語言 \(Inline Assembler\) 程式碼無法區別。  編譯器會將 ***object*** 當做執行個體而產生程式碼。  
  
 下列範例會產生 C4537：  
  
```  
// C4537.cpp  
// compile with: /W1 /c  
// processor: x86  
struct S {  
   int member;  
};  
  
void f1(S &s) {  
   __asm mov eax, s.member;   // C4537  
   // try the following code instead  
   // or, make the declaration "void f1(S s)"  
   /*  
   mov eax, s  
   mov eax, [eax]s.member  
   */  
}  
```