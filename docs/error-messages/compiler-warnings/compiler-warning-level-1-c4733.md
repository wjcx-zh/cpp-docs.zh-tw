---
title: 編譯器警告 (層級 1) C4733 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4733
dev_langs:
- C++
helpviewer_keywords:
- C4733
ms.assetid: 7ef4f577-772d-4b66-a7bf-8958a6b250bc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 59d702867fb4950b97ee2d2c6249c26229aac975
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4733"></a>編譯器警告 (層級 1) C4733
內嵌 asm 指定給 'Fs: 0': 未註冊為安全的處理常式的處理常式  
  
 修改在加入新的例外狀況處理常式的 fs: 0 值的函式可能不適用於安全例外狀況，因為處理常式可能不會註冊為有效的例外狀況處理常式 (請參閱[/SAFESEH](../../build/reference/safeseh-image-has-safe-exception-handlers.md))。  
  
 若要解決這個警告，請移除 fs: 0 定義或關閉這個警告並使用[。SAFESEH](../../assembler/masm/dot-safeseh.md)來指定安全例外狀況處理常式。  
  
 下列範例會產生 C4733:  
  
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