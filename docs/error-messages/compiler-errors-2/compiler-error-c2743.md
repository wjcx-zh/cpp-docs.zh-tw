---
title: "編譯器錯誤 C2743 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2743
dev_langs:
- C++
helpviewer_keywords:
- C2743
ms.assetid: 644cd444-21d2-471d-a176-f5f52c5a0b73
caps.latest.revision: 8
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
translationtype: Machine Translation
ms.sourcegitcommit: cc82b83860786ffc3f0aee73ede18ecadef16a7a
ms.openlocfilehash: 7420231e64515b556cfe81fc695eda5f75231506
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-error-c2743"></a>編譯器錯誤 C2743
'type': 無法攔截 __clrcall 解構函式或複製建構函式的原生型別  
  
 使用編譯的模組**/clr**嘗試攔截例外狀況的原生型別，並使用該類型的解構函式或複製建構函式`__clrcall`呼叫慣例。  
  
 編譯時**/clr**，例外狀況處理預期要讓原生類型中的成員函式[__cdecl](../../cpp/cdecl.md)而非[__clrcall](../../cpp/clrcall.md)。 原生型別搭配使用的成員函式`__clrcall`無法攔截以編譯的模組中的呼叫慣例**/clr**。  
  
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
