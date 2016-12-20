---
title: "_AddressOfReturnAddress | Microsoft Docs"
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
  - "_AddressOfReturnAddress_cpp"
  - "_AddressOfReturnAddress"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_AddressOfReturnAddress 內建"
  - "AddressOfReturnAddress 內建"
ms.assetid: c7e10b8c-445e-4236-a602-e2d90200f70a
caps.latest.revision: 17
caps.handback.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _AddressOfReturnAddress
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 專有的**  
  
 提供會保留目前的函式的傳回位址的記憶體位置的位址。  這個位址不可以用於存取其他記憶體位置 \(例如，函式的引數\)。  
  
## 語法  
  
```  
void * _AddressOfReturnAddress();  
```  
  
## 需求  
  
|內建|架構|  
|--------|--------|  
|`_AddressOfReturnAddress`|x86，[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **標頭檔** \<intrin.h\>  
  
## 備註  
 當`_AddressOfReturnAddress`在編譯的程式中使用 [\/clr](../build/reference/clr-common-language-runtime-compilation.md)，函式包含`_AddressOfReturnAddress`呼叫會編譯為原生函式。  函式編譯為 managed 呼叫函式包含`_AddressOfReturnAddress`， `_AddressOfReturnAddress`可能會無法如預期般。  
  
 只有使用與內建這個常式。  
  
## 範例  
  
```  
// compiler_intrinsics_AddressOfReturnAddress.cpp  
// processor: x86, x64  
#include <stdio.h>  
#include <intrin.h>  
  
// This function will print three values:  
//   (1) The address retrieved from _AddressOfReturnAdress  
//   (2) The return address stored at the location returned in (1)  
//   (3) The return address retrieved the _ReturnAddress* intrinsic  
// Note that (2) and (3) should be the same address.  
__declspec(noinline)  
void func() {  
   void* pvAddressOfReturnAddress = _AddressOfReturnAddress();  
   printf_s("%p\n", pvAddressOfReturnAddress);  
   printf_s("%p\n", *((void**) pvAddressOfReturnAddress));  
   printf_s("%p\n", _ReturnAddress());  
}  
  
int main() {  
   func();  
}  
```  
  
  **0012FF78 00401058 00401058**   
## 結束 Microsoft 特定  
  
## 請參閱  
 [編譯器內建](../intrinsics/compiler-intrinsics.md)   
 [C\+\+ 關鍵字](../cpp/keywords-cpp.md)