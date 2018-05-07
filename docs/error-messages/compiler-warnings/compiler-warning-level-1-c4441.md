---
title: 編譯器警告 （層級 1） C4441 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4441
dev_langs:
- C++
helpviewer_keywords:
- C4441
ms.assetid: 7fc540a5-e41f-47cf-aa37-b2b699c2685e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6c2abf64be0e9b80bb4158b0ed163906adc09945
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4441"></a>編譯器警告 (層級 1) C4441
呼叫慣例 'cc1' 忽略;' cc2' 代替  
  
 中受管理的使用者定義型別和全域函式的泛型成員函式必須使用[__clrcall](../../cpp/clrcall.md)呼叫慣例。  使用編譯器`__clrcall`。  
  
## <a name="example"></a>範例  
 下列範例會產生 C4441。  
  
```  
// C4441.cpp  
// compile with: /clr /W1 /c  
generic <class ItemType>  
void __cdecl Test(ItemType item) {}   // C4441  
// try the following line instead  
// void Test(ItemType item) {}  
  
ref struct MyStruct {  
   void __cdecl Test(){}   // C4441  
   void Test2(){}   // OK  
};  
```