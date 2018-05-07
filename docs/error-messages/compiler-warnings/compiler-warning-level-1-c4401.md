---
title: 編譯器警告 （層級 1） C4401 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4401
dev_langs:
- C++
helpviewer_keywords:
- C4401
ms.assetid: 2e7ca136-f144-4b40-b847-82976e8643fc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f8b8a7a2bced261bbff09422c3dfa6454061f636
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4401"></a>編譯器警告 (層級 1) C4401
'位元欄位': 成員是位元欄位  
  
 內嵌組譯程式碼嘗試存取的位元欄位成員。 內嵌組譯碼無法存取位元欄位成員，因此會使用位元欄位成員之前的最後一個封裝界限。  
  
 若要避免這個警告，轉換位元欄位，適當的型別之前在內嵌組譯碼的參考。 下列範例會產生 C4401:  
  
```  
// C4401.cpp  
// compile with: /W1  
// processor: x86  
typedef struct bitfield {  
   signed bit : 1;  
} mybitfield;  
  
int main() {  
   mybitfield bf;  
   bf.bit = 0;  
   __asm {  
      mov bf.bit,0;   // C4401  
   }  
  
   /* use the following __asm block to resolve the warning  
   int i = (int)bf.bit;  
   __asm {  
      mov i,0;  
   }  
   */  
}  
```