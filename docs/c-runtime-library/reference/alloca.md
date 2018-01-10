---
title: "_alloca |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _alloca
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
apitype: DLLExport
f1_keywords:
- _alloca
- alloca
dev_langs: C++
helpviewer_keywords:
- memory allocation, stack
- alloca function
- _alloca function
ms.assetid: 74488eb1-b71f-4515-88e1-cdd03b6f8225
caps.latest.revision: "23"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a48b0ab3e9717416736acf4187a27df2c737089b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="alloca"></a>_alloca
在堆疊上配置記憶體。 此函式已被取代，因為更安全的版本可用;請參閱[_malloca](../../c-runtime-library/reference/malloca.md)。  
  
## <a name="syntax"></a>語法  
  
```  
void *_alloca(   
   size_t size   
);  
```  
  
#### <a name="parameters"></a>參數  
 [輸入] `size`  
 要從堆疊配置的位元組。  
  
## <a name="return-value"></a>傳回值  
 `_alloca` 常式會傳回 `void` 指標至配置的空間，此空間保證會經過適當調整，因此可儲存任何物件類型。 如果 `size` 為 0，`_alloca` 會配置零長度項目，並傳回該項目的有效指標。  
  
 如果無法配置空間，則會產生堆疊溢位例外狀況。 堆疊溢位例外狀況不是 C++ 例外狀況，而是結構化例外狀況。 您必須使用[結構化例外狀況處理](../../cpp/structured-exception-handling-c-cpp.md) (SEH)，而不是使用 C++ 例外狀況處理。  
  
## <a name="remarks"></a>備註  
 `_alloca`配置`size`位元組程式堆疊。 （不超出範圍只是通過配置） 時，呼叫的函式結束時，會自動釋放已配置的空間。 因此，不會傳遞所傳回的指標值`_alloca`做為引數[可用](../../c-runtime-library/reference/free.md)。  
  
 在例外狀況處理常式 (EH) 中明確呼叫 `_alloca` 有一些限制。 在 x86 等級處理器上執行的 EH 常式會在自己的記憶體框架中運作︰這些常式會在不是根據封入函式之堆疊指標目前位置的記憶體空間中執行其工作。 最常見的實作包括 Windows NT 結構化例外狀況處理 (SEH) 和 C++ catch 子句運算式。 因此，在下列任何情節中明確呼叫 `_alloca`，會在傳回至呼叫的 EH 常式期間導致程式失敗：  
  
-   Windows NT SEH 例外狀況篩選條件運算式︰`__except` (`_alloca ()` )  
  
-   Windows NT SEH 最終例外狀況處理常式︰`__finally` {`_alloca ()` }  
  
-   C++ EH catch 子句運算式  
  
 不過，您可以直接從 EH 常式或應用程式提供的回呼 (由之前列出的其中一個 EH 情節所叫用) 呼叫 `_alloca`。  
  
> [!IMPORTANT]
>  在 Windows XP 中，如果在 try/catch 區塊中呼叫 `_alloca`，則必須在 catch 區塊中呼叫 [_resetstkoflw](../../c-runtime-library/reference/resetstkoflw.md)。  
  
 除了上述的限制，當使用[/clr （Common Language Runtime 編譯）](../../build/reference/clr-common-language-runtime-compilation.md)選項，`_alloca`不能用於在`__except`區塊。 如需詳細資訊，請參閱 [/clr Restrictions](../../build/reference/clr-restrictions.md)。  
  
## <a name="requirements"></a>需求  
  
|常式傳回的值|必要的標頭|  
|-------------|---------------------|  
|`_alloca`|\<malloc.h>|  
  
## <a name="example"></a>範例  
  
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
  
```Output  
Allocated 1000 bytes of stack at 0x0012FB50  
```  
  
## <a name="see-also"></a>請參閱  
 [記憶體配置](../../c-runtime-library/memory-allocation.md)   
 [calloc](../../c-runtime-library/reference/calloc.md)   
 [malloc](../../c-runtime-library/reference/malloc.md)   
 [realloc](../../c-runtime-library/reference/realloc.md)   
 [_resetstkoflw](../../c-runtime-library/reference/resetstkoflw.md)   
 [_malloca](../../c-runtime-library/reference/malloca.md)