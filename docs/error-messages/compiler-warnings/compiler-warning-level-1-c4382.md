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
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: cc82b83860786ffc3f0aee73ede18ecadef16a7a
ms.openlocfilehash: 4571fe618b0ae89251d2748fbbcdfcb654201054
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-warning-level-1-c4382"></a>編譯器警告 (層級 1) C4382
擲回 'type': 具有 __clrcall 解構函式或複製建構函式的型別只會攔截在 /clr: pure 模組  
  
 **/Clr: pure** Visual Studio 2015 中的編譯器選項已被取代。  
  
 編譯時**/clr** (不**/clr: pure**)，例外狀況處理預期要讓原生類型中的成員函式[__cdecl](../../cpp/cdecl.md)而非[__clrcall](../../cpp/clrcall.md)。 原生型別搭配使用的成員函式`__clrcall`無法攔截以編譯的模組中的呼叫慣例**/clr**。  
  
 以編譯的模組中，將會攔截例外狀況**/clr: pure**，您可以忽略此警告。  
  
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
