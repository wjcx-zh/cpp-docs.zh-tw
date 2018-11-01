---
title: _malloca
ms.date: 11/04/2016
apiname:
- _malloca
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
- malloca
- _malloca
helpviewer_keywords:
- memory allocation, stack
- malloca function
- _malloca function
ms.assetid: 293992df-cfca-4bc9-b313-0a733a6bb936
ms.openlocfilehash: 8c8ce8bdf8ab40cae45ecec9c4b182bdf3d6bc82
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50563978"
---
# <a name="malloca"></a>_malloca

在堆疊上配置記憶體。 這是 [_alloca](alloca.md) 的版本，具有 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述的安全性增強功能。

## <a name="syntax"></a>語法

```C
void *_malloca(
   size_t size
);
```

### <a name="parameters"></a>參數

*size*<br/>
要從堆疊配置的位元組。

## <a name="return-value"></a>傳回值

**_Malloca**常式會傳回**void**指標至配置的空間保證會適當地對齊任何物件類型的儲存體。 如果*大小*為 0， **_malloca**配置零長度項目，並傳回該項目的有效指標。

如果無法配置空間，則會產生堆疊溢位例外狀況。 堆疊溢位例外狀況不是 C++ 例外狀況，而是結構化例外狀況。 您必須使用[結構化例外狀況處理](../../cpp/structured-exception-handling-c-cpp.md) (SEH)，而不是使用 C++ 例外狀況處理。

## <a name="remarks"></a>備註

**_malloca**配置*大小*從程式堆疊或堆積中，如果要求超過特定大小 （位元組） 所指定的位元組 **_ALLOCA_S_THRESHOLD**。 之間的差異 **_malloca**並 **_alloca**在於 **_alloca**一律會配置在堆疊上，不論大小為何。 不同於 **_alloca**，這並不需要或不允許呼叫**免費**釋放配置的記憶體， **_malloca**需要使用[_freea](freea.md)釋放記憶體。 在偵錯模式中， **_malloca**一律從堆積中配置記憶體。

若要明確呼叫的限制 **_malloca**例外狀況處理常式 (EH) 中。 在 x86 等級處理器上執行的 EH 常式會在自己的記憶體框架中運作︰這些常式會在不是根據封入函式之堆疊指標目前位置的記憶體空間中執行其工作。 最常見的實作包括 Windows NT 結構化例外狀況處理 (SEH) 和 C++ catch 子句運算式。 因此，明確呼叫 **_malloca**任何下列案例中的結果傳回給呼叫的 EH 常式期間的程式發生失敗：

- Windows NT SEH 例外狀況篩選條件運算式： **__except** (`_malloca ()` )

- Windows NT SEH 最終例外狀況處理常式： **__finally** {`_malloca ()` }

- C++ EH catch 子句運算式

不過， **_malloca**可以直接從 EH 常式或呼叫應用程式所提供的回呼所叫用由其中一個 EH 情節先前所列。

> [!IMPORTANT]
> 在 Windows XP 中，如果 **_malloca**稱為 try/catch 區塊中，您必須呼叫[_resetstkoflw](resetstkoflw.md) catch 區塊中。

除了上述限制，當使用[/clr （Common Language Runtime 編譯）](../../build/reference/clr-common-language-runtime-compilation.md)選項時， **_malloca**不適用於 **__except**區塊。 如需詳細資訊，請參閱 [/clr Restrictions](../../build/reference/clr-restrictions.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_malloca**|\<malloc.h>|

## <a name="example"></a>範例

```C
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

## <a name="example"></a>範例

```C
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

### <a name="input"></a>輸入

```Input
1000
```

### <a name="sample-output"></a>範例輸出

```Output
Enter the number of bytes to allocate using _malloca: 1000
```

## <a name="see-also"></a>另請參閱

[記憶體配置](../../c-runtime-library/memory-allocation.md)<br/>
[calloc](calloc.md)<br/>
[malloc](malloc.md)<br/>
[realloc](realloc.md)<br/>
[_resetstkoflw](resetstkoflw.md)<br/>
