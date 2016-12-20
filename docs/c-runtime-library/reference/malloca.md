---
title: "_malloca | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_malloca"
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
  - "malloca"
  - "_malloca"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_malloca 函式"
  - "malloca 函式"
  - "記憶體配置, 堆疊"
ms.assetid: 293992df-cfca-4bc9-b313-0a733a6bb936
caps.latest.revision: 27
caps.handback.revision: 27
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _malloca
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在堆疊上配置記憶體。  這是 [\_alloca](../../c-runtime-library/reference/alloca.md) 的安全性強化版本，如 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md) 所述。  
  
## 語法  
  
```  
void *_malloca(   
   size_t size   
);  
```  
  
#### 參數  
 `size`  
 從堆疊中配置的位元組。  
  
## 傳回值  
 `_malloca` 方法會傳回配置空間的 `void` 指標，保證為任何型別的物件儲存一些物件的對齊。  如果 `size` 為 0，`_malloca` 會零長度的項目，並傳回指向該項目的有效指標。  
  
 如果空間無法配置，堆疊溢位例外狀況產生。  堆疊溢位例外狀況不是 C\+\+ 例外狀況，它是結構化的例外狀況。  除了使用 C\+\+ 例外狀況處理常式，您必須使用 [結構化例外處理](../../cpp/structured-exception-handling-c-cpp.md) \(SEH\)。  
  
## 備註  
 如果要求超過在 `_ALLOCA_S_THRESHOLD` 所指定的位元組特定大小，`_malloca` 從程式堆疊或堆積配置 `size` 位元組。  在 `_malloca` 和 `_alloca` 之間的差數是無論大小，`_alloca` 永遠在堆疊上配置。  不同於 `_alloca` 如此配置不需要也不允許呼叫 `free` 釋放記憶體，`_malloca` 需要使用 [\_freea](../../c-runtime-library/reference/freea.md) 來釋放記憶體。  在偵錯模式，`_malloca` 永遠從堆積配置記憶體。  
  
 在在例外處理常式 \(EH\) 明確呼叫 `_malloca` 有限制。  在 x86 處理器上執行的 EH 常式在自己的記憶體架構運作：他們在記憶體空間執行其工作，該記憶體空間非以封入函式的堆疊指標之目前位置為基礎。  最常見的實作包括 Windows NT 結構化例外處理常式\(SEH\) 及 C\+\+ catch 子句運算式。  因此，在下列任何情況明確呼叫 `_malloca` 造成傳回呼叫 EH 常式時程式失敗：  
  
-   Windows NT SEH 例外狀況篩選條件運算式：`__except` \(`_malloca ()` \)  
  
-   Windows NT SEH 最後的例外處理常式：`__finally` 為`_malloca ()` 。  
  
-   C\+\+ EH catch 子句運算式  
  
 不過，可以直接從 EH 常式內部或從先前所列的其中一個 EH 案例中由應用程式所提供的回呼呼叫 `_malloca` 取得。  
  
> [!IMPORTANT]
>  在 Windows XP 上，如果 `_malloca` ，會在 try\/catch 區塊內，您必須在 catch 區塊中呼叫 [\_resetstkoflw](../../c-runtime-library/reference/resetstkoflw.md) 。  
  
 除了上述限制之外，在使用 [\/clr \(Common Language Runtime 編譯\)](../../build/reference/clr-common-language-runtime-compilation.md) 選項時， `_malloca` 無法用於 `__except` 區塊。  如需詳細資訊，請參閱 [\/clr Restrictions](../../build/reference/clr-restrictions.md)。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_malloca`|\<malloc.h\>|  
  
## 範例  
  
```  
// crt_malloca_simple.c  
#include <stdio.h>  
#include <malloc.h>  
  
void Fn()  
{  
   char * buf = (char *)_malloca( 100 );  
   // do something with buf  
   _freea( buf );  
}  
  
int main()  
{  
   Fn();  
}  
```  
  
## 範例  
  
```  
// crt_malloca_exception.c  
// This program demonstrates the use of  
// _malloca and trapping any exceptions  
// that may occur.  
  
#include <windows.h>  
#include <stdio.h>  
#include <malloc.h>  
  
int main()  
{  
    int     size;  
    int     numberRead = 0;  
    int     errcode = 0;  
    void    *p = NULL;  
    void    *pMarker = NULL;  
  
    while (numberRead == 0)  
    {  
        printf_s("Enter the number of bytes to allocate "  
                 "using _malloca: ");  
        numberRead = scanf_s("%d", &size);  
    }  
  
    // Do not use try/catch for _malloca,  
    // use __try/__except, since _malloca throws  
    // Structured Exceptions, not C++ exceptions.  
  
    __try  
    {  
        if (size > 0)  
        {  
            p =  _malloca( size );  
        }  
        else  
        {  
            printf_s("Size must be a positive number.");  
        }  
        _freea( p );  
    }  
  
    // Catch any exceptions that may occur.  
    __except( GetExceptionCode() == STATUS_STACK_OVERFLOW )  
    {  
        printf_s("_malloca failed!\n");  
  
        // If the stack overflows, use this function to restore.  
        errcode = _resetstkoflw();  
        if (errcode)  
        {  
            printf("Could not reset the stack!");  
            _exit(1);  
        }  
    };  
}  
```  
  
## 輸入  
  
```  
1000  
```  
  
## 範例輸出  
  
```  
Enter the number of bytes to allocate using _malloca: 1000  
```  
  
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [記憶體配置](../../c-runtime-library/memory-allocation.md)   
 [calloc](../../c-runtime-library/reference/calloc.md)   
 [malloc](../../c-runtime-library/reference/malloc.md)   
 [realloc](../../c-runtime-library/reference/realloc.md)   
 [\_resetstkoflw](../../c-runtime-library/reference/resetstkoflw.md)