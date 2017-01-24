---
title: "編譯器警告 (層級 1) C4733 | Microsoft Docs"
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
  - "C4733"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4733"
ms.assetid: 7ef4f577-772d-4b66-a7bf-8958a6b250bc
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 1) C4733
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

內嵌 asm 指定給 'FS:0' : 處理常式沒有註冊為安全的處理常式  
  
 修改 FS:0 處的值以加入新的例外處理常式之函式，可能不適用於安全例外狀況，因為處理常式可能未登錄為有效的例外處理常式 \(請參閱 [\/SAFESEH](../../build/reference/safeseh-image-has-safe-exception-handlers.md)\)。  
  
 若要解除這個警告，請移除 FS:0 定義，或是關閉此警告，並使用 [.SAFESEH](../../assembler/masm/dot-safeseh.md) 來指定安全例外狀況處理常式。  
  
 下列範例會產生 C4733：  
  
```  
// C4733.cpp  
// compile with: /W1 /c  
// processor: x86  
#include "stdlib.h"  
#include "stdio.h"  
void my_handler()  
{  
   printf("Hello from my_handler\n");  
   exit(1);  
}  
  
int main()  
{  
   _asm {  
      push    my_handler  
      mov     eax, DWORD PTR fs:0  
      push    eax  
      mov     DWORD PTR fs:0, esp   // C4733  
   }  
  
   *(int*)0 = 0;  
}  
```