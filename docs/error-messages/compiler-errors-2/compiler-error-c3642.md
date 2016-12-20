---
title: "編譯器錯誤 C3642 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3642"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3642"
ms.assetid: 429790c2-9614-4d85-b31c-687c8d8f83ff
caps.latest.revision: 13
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3642
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'return\_type\/args' : 無法從機器碼以 \_\_clrcall 呼叫慣例呼叫函式  
  
 以 [\_\_clrcall](../../cpp/clrcall.md) 呼叫慣例標示的函式不能從機器碼 \(Unmanaged\) 進行呼叫。  
  
 *return\_type\/args* 是您嘗試要呼叫的函式名稱或 `__clrcall` 函式的型別。透過函式指標呼叫時，使用型別。  
  
 若要呼叫原生內容中的 Managed 函式，您可以加入一個將呼叫 `__clrcall` 函式的包裝函式。  或者，您也可以使用 CLR 封送處理機制；如需詳細資訊，請參閱 [如何：使用 PInvoke 封送處理函式指標](../../dotnet/how-to-marshal-function-pointers-using-pinvoke.md)。  
  
 下列範例會產生 C3642：  
  
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