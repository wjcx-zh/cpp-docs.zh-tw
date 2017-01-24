---
title: "_alloca | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_alloca"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_alloca"
  - "alloca"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_alloca 函式"
  - "alloca 函式"
  - "記憶體配置, 堆疊"
ms.assetid: 74488eb1-b71f-4515-88e1-cdd03b6f8225
caps.latest.revision: 23
caps.handback.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _alloca
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在堆疊上配置記憶體。  因為更安全的版本，才能使用這個函式已被取代;請參閱 [\_malloca](../../c-runtime-library/reference/malloca.md)。  
  
## 語法  
  
```  
void *_alloca(   
   size_t size   
);  
```  
  
#### 參數  
 \[in\] `size`  
 從堆疊中配置的位元組。  
  
## 傳回值  
 `_alloca` 方法會傳回配置空間的 `void` 指標，保證為任何型別的物件儲存一些物件的對齊。  如果 `size` 為 0，`_alloca` 會零長度的項目，並傳回指向該項目的有效指標。  
  
 如果空間無法配置，堆疊溢位例外狀況產生。  堆疊溢位例外狀況不是 C\+\+ 例外狀況，它是結構化的例外狀況。  除了使用 C\+\+ 例外狀況處理常式，您必須使用 [結構化例外處理](../../cpp/structured-exception-handling-c-cpp.md) \(SEH\)。  
  
## 備註  
 將`_alloca` 從程式堆疊配置 `size` 位元組。  這個配置的空間會自動釋放，當呼叫的函式結尾 \(沒有配置時，只會超出範圍時\)。  因此，請不要將當做引數所傳回的 `_alloca` 指標值至 [可用](../../c-runtime-library/reference/free.md)。  
  
 在在例外處理常式 \(EH\) 明確呼叫 `_alloca` 有限制。  在 x86 處理器上執行的 EH 常式在自己的記憶體架構運作：他們在記憶體空間執行其工作，該記憶體空間非以封入函式的堆疊指標之目前位置為基礎。  最常見的實作包括 Windows NT 結構化例外處理常式\(SEH\) 及 C\+\+ catch 子句運算式。  因此，在下列任何情況明確呼叫 `_alloca` 造成傳回呼叫 EH 常式時程式失敗：  
  
-   Windows NT SEH 例外狀況篩選條件運算式：`__except`\(`_alloca ()` \)  
  
-   Windows NT SEH 最後的例外處理常式：`__finally` 為`_alloca ()` 。  
  
-   C\+\+ EH catch 子句運算式  
  
 不過，可以直接從 EH 常式內部或從先前所列的其中一個 EH 案例中由應用程式所提供的回呼呼叫 `_alloca` 取得。  
  
> [!IMPORTANT]
>  在 Windows XP 上，如果 `_alloca` ，會在 try\/catch 區塊內，您必須在 catch 區塊中呼叫 [\_resetstkoflw](../../c-runtime-library/reference/resetstkoflw.md) 。  
  
 除了上述限制之外，在使用 [\/clr \(Common Language Runtime 編譯\)](../../build/reference/clr-common-language-runtime-compilation.md) 選項時， `_alloca` 無法用於 `__except` 區塊。  如需詳細資訊，請參閱 [\/clr Restrictions](../../build/reference/clr-restrictions.md)。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_alloca`|\<malloc.h\>|  
  
## 範例  
  
```  
// crt_alloca.c  
// This program demonstrates the use of  
// _alloca and trapping any exceptions  
// that may occur.  
  
#include <windows.h>  
#include <stdio.h>  
#include <malloc.h>  
  
int main()  
{  
    int     size = 1000;  
    int     errcode = 0;  
    void    *pData = NULL;  
  
    // Note: Do not use try/catch for _alloca,  
    // use __try/__except, since _alloca throws  
    // Structured Exceptions, not C++ exceptions.  
  
    __try {  
        // An unbounded _alloca can easily result in a   
        // stack overflow.  
        // Checking for a size < 1024 bytes is recommended.  
        if (size > 0 && size < 1024)  
        {  
            pData = _alloca( size );  
            printf_s( "Allocated %d bytes of stack at 0x%p",  
                      size, pData);  
        }  
        else  
        {  
            printf_s("Tried to allocate too many bytes.\n");  
        }  
    }  
  
    // If an exception occured with the _alloca function  
    __except( GetExceptionCode() == STATUS_STACK_OVERFLOW )  
    {  
        printf_s("_alloca failed!\n");  
  
        // If the stack overflows, use this function to restore.  
        errcode = _resetstkoflw();  
        if (errcode)  
        {  
            printf_s("Could not reset the stack!\n");  
            _exit(1);  
        }  
    };  
}  
```  
  
  **配置 1000 個位元組的堆疊在 0x0012FB50**   
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [記憶體配置](../../c-runtime-library/memory-allocation.md)   
 [calloc](../../c-runtime-library/reference/calloc.md)   
 [malloc](../../c-runtime-library/reference/malloc.md)   
 [realloc](../../c-runtime-library/reference/realloc.md)   
 [\_resetstkoflw](../../c-runtime-library/reference/resetstkoflw.md)   
 [\_malloca](../../c-runtime-library/reference/malloca.md)