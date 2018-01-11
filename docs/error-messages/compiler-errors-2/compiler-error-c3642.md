---
title: "編譯器錯誤 C3642 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3642
dev_langs: C++
helpviewer_keywords: C3642
ms.assetid: 429790c2-9614-4d85-b31c-687c8d8f83ff
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3dace0204f4534ee630924bd443d028efc2afc14
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3642"></a>編譯器錯誤 C3642
' return_type/args ': 無法以 __clrcall 呼叫慣例，從機器碼呼叫的函式  
  
 函式標示為[__clrcall](../../cpp/clrcall.md)無法呼叫原生 (unmanaged) 程式碼的呼叫慣例。  
  
 *return_type/args*是函式的名稱，或是類型`__clrcall`您嘗試呼叫的函式。  一種，透過函式指標呼叫時可用。  
  
 若要從原生內容呼叫 managed 函式，您可以加入的 「 包裝函式 」 函式會呼叫`__clrcall`函式。 或者，您可以使用 CLR 封送處理機制。請參閱[如何： 封送處理函式指標使用 PInvoke](../../dotnet/how-to-marshal-function-pointers-using-pinvoke.md)如需詳細資訊。  
  
 下列範例會產生 C3642:  
  
```  
// C3642.cpp  
// compile with: /clr  
using namespace System;  
struct S {  
   void Test(String ^ s) {   // CLR type in signature, implicitly __clrcall  
      Console::WriteLine(s);  
   }  
   void Test2(char * s) {  
      Test(gcnew String(s));  
   }  
};  
  
#pragma unmanaged  
int main() {  
   S s;  
   s.Test("abc");   // C3642  
   s.Test2("abc");   // OK  
}  
```