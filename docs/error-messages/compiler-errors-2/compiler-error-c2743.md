---
title: 編譯器錯誤 C2743 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2743
dev_langs:
- C++
helpviewer_keywords:
- C2743
ms.assetid: 644cd444-21d2-471d-a176-f5f52c5a0b73
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a762a7c816f713f9371ff50524ccb582753535b0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2743"></a>編譯器錯誤 C2743
'type': 無法攔截原生類型具有 __clrcall 解構函式或複製建構函式  
  
 使用編譯的模組 **/clr**嘗試攔截例外狀況的原生類型和類型的解構函式或複製建構函式的使用位置`__clrcall`呼叫慣例。  
  
 編譯時 **/clr**，例外狀況處理為原生類型中預期的成員函式[__cdecl](../../cpp/cdecl.md)而非[__clrcall](../../cpp/clrcall.md)。 原生類型與成員函式使用`__clrcall`無法攔截在編譯的模組中的呼叫慣例 **/clr**。  
  
 如需詳細資訊，請參閱 [/clr (Common Language Runtime 編譯)](../../build/reference/clr-common-language-runtime-compilation.md)。  
  
## <a name="example"></a>範例  
 下列範例會產生 C2743。  
  
```  
// C2743.cpp  
// compile with: /clr  
public struct S {  
   __clrcall ~S() {}  
};  
  
public struct T {  
   ~T() {}  
};  
  
int main() {  
   try {}  
   catch(S) {}   // C2743  
   // try the following line instead  
   // catch(T) {}  
  
   try {}  
   catch(S*) {}   // OK  
}  
```