---
title: _malloca
ms.date: 11/04/2016
api_name:
- _malloca
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
- malloca
- _malloca
helpviewer_keywords:
- memory allocation, stack
- malloca function
- _malloca function
ms.assetid: 293992df-cfca-4bc9-b313-0a733a6bb936
ms.openlocfilehash: d4604a6e2dfb00502e3c942c9735a077e1632843
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87232491"
---
# <a name="_malloca"></a>_malloca

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

**_Malloca**常式 **`void`** 會傳回已配置空間的指標，保證會適當地對齊任何物件類型的儲存。 如果*size*為0， **_malloca**會配置零長度專案，並傳回該專案的有效指標。

如果*大小*大於 **_ALLOCA_S_THRESHOLD**，則 **_malloca**會嘗試在堆積上配置，如果無法配置空間，則會傳回 null 指標。 如果*size*小於或等於 **_ALLOCA_S_THRESHOLD**，則 **_malloca**會嘗試在堆疊上配置，而如果無法配置空間，則會產生堆疊溢位例外狀況。 堆疊溢位例外狀況不是 c + + 例外狀況;這是結構化例外狀況。 您必須使用[結構化例外狀況處理](../../cpp/structured-exception-handling-c-cpp.md)（SEH）來攔截這個例外狀況，而不是使用 c + + 例外狀況處理。

## <a name="remarks"></a>備註

如果要求超出 **_ALLOCA_S_THRESHOLD**所指定的特定大小（以位元組為單位）， **_malloca**會從程式堆疊或堆積配置*大小*位元組。 **_Malloca**和 **_alloca**之間的差異在於， **_alloca**一律會在堆疊上配置，而不論其大小為何。 不同于 **_alloca**，這不需要或不允許**呼叫來釋放記憶體以供**配置， **_malloca**需要使用[_freea](freea.md)來釋放記憶體。 在 [debug] 模式中， **_malloca**一律會從堆積配置記憶體。

在例外狀況處理常式（EH）中明確呼叫 **_malloca**有一些限制。 在 x86 等級處理器上執行的 EH 常式會在自己的記憶體框架中運作︰這些常式會在不是根據封入函式之堆疊指標目前位置的記憶體空間中執行其工作。 最常見的實作包括 Windows NT 結構化例外狀況處理 (SEH) 和 C++ catch 子句運算式。 因此，在下列任一情況下明確呼叫 **_malloca** ，會導致在傳回呼叫 EH 常式期間發生程式失敗：

- Windows NT SEH 例外狀況篩選條件運算式： **`__except`** （ `_malloca ()` ）

- Windows NT SEH 最終例外狀況處理常式： **`__finally`** { `_malloca ()` }

- C++ EH catch 子句運算式

不過，您可以從 EH 常式內或從應用程式提供的回呼（由先前列出的其中一個 EH 案例叫用），直接呼叫 **_malloca** 。

> [!IMPORTANT]
> 在 Windows XP 中，如果在 try/catch 區塊內呼叫 **_malloca** ，您必須在 catch 區塊中呼叫[_resetstkoflw](resetstkoflw.md) 。

除了上述限制以外，使用[/clr （Common Language Runtime 編譯）](../../build/reference/clr-common-language-runtime-compilation.md)選項時， **_malloca**不能用在 **`__except`** 區塊中。 如需詳細資訊，請參閱 [/clr 限制](../../build/reference/clr-restrictions.md)。

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
