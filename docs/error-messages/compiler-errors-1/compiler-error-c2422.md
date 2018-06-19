---
title: 編譯器錯誤 C2422 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2422
dev_langs:
- C++
helpviewer_keywords:
- C2422
ms.assetid: ef0ec302-4028-4778-b134-0b8cea4bcad9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 89a808e4b324b11c88be38ae7d8815bee4e232cd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33196343"
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