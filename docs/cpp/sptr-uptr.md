---
title: "__sptr、__uptr | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "__uptr_cpp"
  - "__sptr"
  - "__uptr"
  - "__sptr_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__sptr 修飾詞"
  - "__uptr 修飾詞"
ms.assetid: c7f5f3b2-9106-4a0b-a6de-d1588ab153ed
caps.latest.revision: 7
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# __sptr、__uptr
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## Microsoft 特定的  
 在 32 位元指標宣告使用 `__sptr` 或 `__uptr` 修飾詞，指定編譯器將 32 位元指標轉換為 64 位元指標的方式。  例如，將 32 位元指標指派給 64 位元指標變數，或在 64 位元平台取值時，就會轉換 32 位元指標。  
  
 有關 64 位元平台支援的 Microsoft 文件有時會將 32 位元指標的最高有效位元稱為正負號位元。  根據預設，編譯器會使用正負號擴充項目將 32 位元指標轉換為 64 位元指標。  也就是說，64 位元指標的最低有效 32 位元設為 32 位元指標的值，而最高有效 32 位元則設為 32 位元指標的正負號位元的值。  如果正負號位元是 0，此類轉換會產生正確的結果，如果正負號位元是 1，則不會產生正確結果。  例如，32 位元位址 0x7FFFFFFF 會產生相等的 64 位元位址 0x000000007FFFFFFF，但會將 32 位元位址 0x80000000 錯誤地變更為 0xFFFFFFFF80000000。  
  
 `__sptr` \(或帶正負號的指標\) 修飾詞指定指標轉換將 64 位元指標的最高有效位元轉換為 32 位元指標的正負號位元。  `__uptr` \(或不帶正負號的指標\) 修飾詞指定轉換將最高有效位元設為零。  下列宣告顯示 `__sptr` 和 `__uptr` 修飾詞搭配兩個不合格指標、兩個類型為 [\_\_ptr32](../cpp/ptr32-ptr64.md) 的合格指標，以及一個函式參數。  
  
```  
int * __sptr psp;  
int * __uptr pup;  
int * __ptr32 __sptr psp32;  
int * __ptr32 __uptr pup32;  
void MyFunction(char * __uptr __ptr32 myValue);  
```  
  
 使用 `__sptr` 和 `__uptr` 修飾詞搭配指標宣告。  在[指標類型限定詞](../c-language/pointer-declarations.md)的位置使用修飾詞，表示修飾詞必須在星號之後。  您不能使用修飾詞搭配[成員指標](../cpp/pointers-to-members.md)。  修飾詞不影響非指標宣告。  
  
 如果您不使用 `__sptr` 或 `__uptr` 修飾詞，而且您啟用 [編譯器警告 \(層級 2\) C4826](../error-messages/compiler-warnings/compiler-warning-level-2-c4826.md)，編譯器會在將 32 位元指標轉換為 64 位元指標時發出警告。  
  
## 範例  
 下列範例宣告使用 `__sptr` 及 `__uptr` 修飾詞的 32 位元指標，將每個 32 位元指標指派給一個 64 位元指標變數，然後顯示每個 64 位元指標的十六進位值。  此範例是以原生 64 位元編譯器編譯，並且在 64 位元平台上執行。  
  
```  
// sptr_uptr.cpp  
// processor: x64  
#include "stdio.h"  
  
// Warning C4826 is off by default.  
  
int main()  
{  
    void *        __ptr64 p64;  
    void *        __ptr32 p32d; //default signed pointer  
    void * __sptr __ptr32 p32s; //explicit signed pointer  
    void * __uptr __ptr32 p32u; //explicit unsigned pointer  
  
// Set the 32-bit pointers to a value whose sign bit is 1.  
    p32d = reinterpret_cast<void *>(0x87654321);  
    p32s = p32d;  
    p32u = p32d;  
  
// The printf() function automatically displays leading zeroes with each 32-bit pointer. These are unrelated   
// to the __sptr and __uptr modifiers.   
    printf("Display each 32-bit pointer (as an unsigned 64-bit pointer):\n");  
    printf("p32d:       %p\n", p32d);   
    printf("p32s:       %p\n", p32s);  
    printf("p32u:       %p\n", p32u);  
  
    printf("\nDisplay the 64-bit pointer created from each 32-bit pointer:\n");  
    p64 = p32d;   
    printf("p32d: p64 = %p\n", p64);  
    p64 = p32s;  
    printf("p32s: p64 = %p\n", p64);  
    p64 = p32u;  
    printf("p32u: p64 = %p\n", p64);  
    return 0;  
}  
```  
  
  **顯示每個 32 位元指標 \(做為不帶正負號的 64 位元指標\)：**  
**p32d:       0000000087654321**  
**p32s:       0000000087654321**  
**p32u:       0000000087654321**  
**顯示以每個 32 位元指標建立的 64 位元指標：**  
**p32d: p64 \= FFFFFFFF87654321**  
**p32s: p64 \= FFFFFFFF87654321**  
**p32u: p64 \= 0000000087654321**   
## END Microsoft 特定的  
  
## 請參閱  
 [Microsoft 專有的修飾詞](../cpp/microsoft-specific-modifiers.md)