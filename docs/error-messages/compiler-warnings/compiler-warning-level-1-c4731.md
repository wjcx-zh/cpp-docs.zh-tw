---
title: "編譯器警告 (層級 1) C4731 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4731
dev_langs: C++
helpviewer_keywords: C4731
ms.assetid: 5658c24c-3e6f-4505-835b-1fb92d47cab0
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: bfddf524678da34d514c32bfe86b98b32e87d195
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
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