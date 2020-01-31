---
title: _alloca
ms.date: 11/04/2016
api_name:
- _alloca
api_location:
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _alloca
- alloca
helpviewer_keywords:
- memory allocation, stack
- alloca function
- _alloca function
ms.assetid: 74488eb1-b71f-4515-88e1-cdd03b6f8225
ms.openlocfilehash: 77ce6e0cdb5e1ad3f5317989c7804abc5aed4e69
ms.sourcegitcommit: b8c22e6d555cf833510753cba7a368d57e5886db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76821430"
---
# <a name="_alloca"></a>_alloca

在堆疊上配置記憶體。 此函式已被取代，因為有更安全的版本可供使用;請參閱[_malloca](malloca.md)。

## <a name="syntax"></a>語法

```C
void *_alloca(
   size_t size
);
```

### <a name="parameters"></a>參數

*size*<br/>
要從堆疊配置的位元組。

## <a name="return-value"></a>傳回值

**_Alloca**常式會傳回已配置空間的**void**指標，保證會適當地對齊任何物件類型的儲存。 如果*size*為0， **_alloca**會配置零長度專案，並傳回該專案的有效指標。

如果無法配置空間，則會產生堆疊溢位例外狀況。 堆疊溢位例外狀況不是 C++ 例外狀況，而是結構化例外狀況。 您必須使用[結構化例外狀況處理](../../cpp/structured-exception-handling-c-cpp.md) (SEH)，而不是使用 C++ 例外狀況處理。

## <a name="remarks"></a>備註

**_alloca**從程式堆疊配置*大小*位元組。 已配置的空間會在呼叫函式結束時自動釋出（而不是在配置只傳遞超出範圍時）。 因此，請勿將 **_alloca**傳回的指標值當做引數傳遞至[free](free.md)。

在例外狀況處理常式（EH）中明確呼叫 **_alloca**有一些限制。 在 x86 等級處理器上執行的 EH 常式會在自己的記憶體框架中運作︰這些常式會在不是根據封入函式之堆疊指標目前位置的記憶體空間中執行其工作。 最常見的實作包括 Windows NT 結構化例外狀況處理 (SEH) 和 C++ catch 子句運算式。 因此，在下列任一情況下明確呼叫 **_alloca** ，會導致在傳回呼叫 EH 常式期間發生程式失敗：

- Windows NT SEH 例外狀況篩選運算式： `__except ( _alloca() )`

- Windows NT SEH 最終例外狀況處理常式： `__finally { _alloca() }`

- C++ EH catch 子句運算式

不過，您可以從 EH 常式內或從應用程式提供的回呼（由先前列出的其中一個 EH 案例叫用），直接呼叫 **_alloca** 。

> [!IMPORTANT]
> 在 Windows XP 中，如果在 try/catch 區塊內呼叫 **_alloca** ，您必須在 catch 區塊中呼叫[_resetstkoflw](resetstkoflw.md) 。

除了上述限制以外，使用[/clr （Common Language Runtime 編譯）](../../build/reference/clr-common-language-runtime-compilation.md)選項時， **_alloca**不能用在 **__except**區塊中。 如需詳細資訊，請參閱 [/clr 限制](../../build/reference/clr-restrictions.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_alloca**|\<malloc.h>|

## <a name="example"></a>範例

```C
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

    // If an exception occurred with the _alloca function
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

[記憶體配置](../../c-runtime-library/memory-allocation.md)<br/>
[calloc](calloc.md)<br/>
[malloc](malloc.md)<br/>
[realloc](realloc.md)<br/>
[_resetstkoflw](resetstkoflw.md)<br/>
[_malloca](malloca.md)<br/>
