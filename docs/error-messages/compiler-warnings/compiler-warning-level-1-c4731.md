---
title: 編譯器警告 (層級 1) C4731 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4731
dev_langs:
- C++
helpviewer_keywords:
- C4731
ms.assetid: 5658c24c-3e6f-4505-835b-1fb92d47cab0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 31bdf972ef3791760469251dc4d0bf19627bded2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33283877"
---
# <a name="compiler-warning-level-1-c4731"></a>編譯器警告 (層級 1) C4731
'pointer': 框架指標暫存器 'register' 修改內嵌組譯碼  
  
 已修改框架指標暫存器。 您必須儲存並還原暫存器中內嵌組件區塊或框架變數 （本機或參數，取決於已修改的暫存器），或您的程式碼可能無法正常運作。  
  
 下列範例會產生 C4731:  
  
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
  
 EBP 是框架指標 （不允許 FPO） 而且正在修改。 當`p`晚參考，它參考相對於`EBP`。 但`EBP`已被覆寫的程式碼，因此程式將無法正常運作，可能也會發生錯誤。