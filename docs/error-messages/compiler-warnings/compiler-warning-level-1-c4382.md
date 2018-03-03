---
title: "編譯器警告 （層級 1） C4382 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4382
dev_langs:
- C++
helpviewer_keywords:
- C4382
ms.assetid: 34be9ad3-bae6-411a-8f80-0c8fd0d2c092
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4b0cef09795553759487e28ef61babe75b35ce03
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4382"></a>編譯器警告 (層級 1) C4382
擲回 'type': 具有 __clrcall 解構函式或複製建構函式的型別只會攔截在 /clr: pure 模組  
  
 **/Clr: pure** Visual Studio 2015 中的編譯器選項已被取代。  
  
 編譯時**/clr** (不**/clr: pure**)，例外狀況處理為原生類型中預期的成員函式[__cdecl](../../cpp/cdecl.md)而非[__clrcall](../../cpp/clrcall.md). 原生類型與成員函式使用`__clrcall`無法攔截在編譯的模組中的呼叫慣例**/clr**。  
  
 如果將編譯的模組中攔截例外狀況**/clr: pure**，您可以忽略此警告。  
  
 如需詳細資訊，請參閱 [/clr (Common Language Runtime 編譯)](../../build/reference/clr-common-language-runtime-compilation.md)。  
  
## <a name="example"></a>範例  
 下列範例會產生 C4382。  
  
```  
// C4382.cpp  
// compile with: /clr /W1 /c  
struct S {  
   __clrcall ~S() {}  
};  
  
struct T {  
   ~T() {}  
};  
  
int main() {  
   S s;  
   throw s;   // C4382  
  
   S * ps = &s;  
   throw ps;   // OK  
  
   T t;  
   throw t;   // OK  
}  
```