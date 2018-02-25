---
title: "_ReturnAddress |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- _ReturnAddress
dev_langs:
- C++
helpviewer_keywords:
- _ReturnAddress intrinsic
- ReturnAddress intrinsic
ms.assetid: 7f4a5811-35e6-4f64-ba7c-21203380eeda
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ae1437d6523b94071a5e7655bfa2e7094d89305a
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="returnaddress"></a>_ReturnAddress
## <a name="microsoft-specific"></a>Microsoft 特定的  
 `_ReturnAddress`內建函式提供呼叫的函式，將控制項傳回給呼叫者後執行指令的位址。  
  
 建立下列的程式並逐步偵錯工具。 當您逐步執行程式，請注意，從傳回位址`_ReturnAddress`。 然後會在從函數傳回之後，立即其中`_ReturnAddress`已使用，請開啟[How to： 使用反組譯碼視窗](/visualstudio/debugger/how-to-use-the-disassembly-window)並記下一個要執行指令的位址符合從傳回的位址`_ReturnAddress`.  
  
 最佳化，例如內嵌可能會影響傳回的位址。 例如，如果下面的範例程式會以編譯[/Ob1](../build/reference/ob-inline-function-expansion.md)，`inline_func`都將予以內嵌到呼叫的函式、 `main`。 因此，若要呼叫`_ReturnAddress`從`inline_func`和`main`皆將會產生相同的值。  
  
 當`_ReturnAddress`用於編譯的程式[/clr](../build/reference/clr-common-language-runtime-compilation.md)，函式包含`_ReturnAddress`呼叫將會編譯為原生函式。 函式編譯為 managed 呼叫函式包含`_ReturnAddress`，`_ReturnAddress`可能無法如預期般運作。  
  
## <a name="requirements"></a>需求  
 **標頭檔** \<intrin.h >  
  
## <a name="example"></a>範例  
  
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
  
**結束 Microsoft 特定的**  
  
## <a name="see-also"></a>請參閱  
 [_AddressOfReturnAddress](../intrinsics/addressofreturnaddress.md)   
 [編譯器內建函式](../intrinsics/compiler-intrinsics.md)   
 [關鍵字](../cpp/keywords-cpp.md)