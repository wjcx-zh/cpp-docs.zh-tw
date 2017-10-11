---
title: "編譯器錯誤 C2422 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2422
dev_langs:
- C++
helpviewer_keywords:
- C2422
ms.assetid: ef0ec302-4028-4778-b134-0b8cea4bcad9
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 65412576c3c1a5e6b8205652d826d0eca6d222e6
ms.contentlocale: zh-tw
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c2422"></a>編譯器錯誤 C2422
'運算元' 中不合法的區段覆寫  
  
 內嵌組譯碼不正確地使用區段覆寫運算子 （冒號） 的運算元上。  可能的原因包括：  
  
-   運算子之前的暫存器不是區段暫存器。  
  
-   運算子之前的暫存器不在運算元中的唯一區段暫存器。  
  
-   區段覆寫運算子出現在間接取值運算子 （括號） 內。  
  
-   下列區段覆寫運算子的運算式不是為即時運算元或記憶體運算元。  
  
 下列範例會產生 C2422:  
  
```  
// C2422.cpp  
// processor: x86  
int main() {  
   _asm {  
      mov AX, [BX:ES]   // C2422  
      mov AX, ES   // OK  
   }  
}  
```
