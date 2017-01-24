---
title: "_ReturnAddress | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_ReturnAddress"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "內建 _ReturnAddress"
  - "內建 ReturnAddress"
ms.assetid: 7f4a5811-35e6-4f64-ba7c-21203380eeda
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _ReturnAddress
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## Microsoft 專有的  
 `_ReturnAddress`內建提供控制項傳回給呼叫者後，就會執行呼叫函式中的指令位址。  
  
 建立下列的程式和偵錯工具的逐步執行它。  當您逐步執行程式，請注意傳回的地址`_ReturnAddress`。  然後，從函式傳回之後，立即在`_ReturnAddress`所使用的開啟[如何：使用反組譯碼視窗](../Topic/How%20to:%20Use%20the%20Disassembly%20Window.md) ，並記下所執行的下一個指令的位址符合所傳回的位址`_ReturnAddress`。  
  
 這類的內嵌月最佳化會影響到 \[寄件地址。  比方說，如果下面這個範例程式時加以編譯[是 \/Ob1](../build/reference/ob-inline-function-expansion.md)， `inline_func`將會內嵌到呼叫的函式， `main`。  因此，呼叫`_ReturnAddress`的`inline_func`和`main`每一個將會產生相同的值。  
  
 當`_ReturnAddress`在編譯的程式中使用 [\/clr](../build/reference/clr-common-language-runtime-compilation.md)，函式包含`_ReturnAddress`呼叫就會編譯成原生函式。  函式編譯為 managed 呼叫函式包含`_ReturnAddress`， `_ReturnAddress`可能會無法如預期般。  
  
## 需求  
 **標頭檔** \<intrin.h\>  
  
## 範例  
  
```  
// compiler_intrinsics__ReturnAddress.cpp  
#include <stdio.h>  
#include <intrin.h>  
  
#pragma intrinsic(_ReturnAddress)  
  
__declspec(noinline)  
void noinline_func(void)  
{  
   printf("Return address from %s: %p\n", __FUNCTION__, _ReturnAddress());  
}  
  
__forceinline  
void inline_func(void)  
{  
   printf("Return address from %s: %p\n", __FUNCTION__, _ReturnAddress());  
}  
  
int main(void)  
{  
   noinline_func();   
   inline_func();  
   printf("Return address from %s: %p\n", __FUNCTION__, _ReturnAddress());  
  
   return 0;  
}  
```  
  
## 結束 Microsoft 特定  
  
## 請參閱  
 [\_AddressOfReturnAddress](../intrinsics/addressofreturnaddress.md)   
 [編譯器內建](../intrinsics/compiler-intrinsics.md)   
 [C\+\+ 關鍵字](../cpp/keywords-cpp.md)