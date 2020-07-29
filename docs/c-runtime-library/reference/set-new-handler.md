---
title: _set_new_handler
ms.date: 4/2/2020
api_name:
- _set_new_handler
- _o__set_new_handler
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
- api-ms-win-crt-runtime-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _set_new_handler
- set_new_handler
helpviewer_keywords:
- _set_new_handler function
- set_new_handler function
- error handling
- transferring control to error handler
ms.assetid: 1d1781b6-5cf8-486a-b430-f365e0bb023f
ms.openlocfilehash: cd6e4df47b28e84bb0ac5ee857cfa1a3e7cf805a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218542"
---
# <a name="_set_new_handler"></a>_set_new_handler

如果運算子無法配置記憶體，則將控制權轉移至您的錯誤處理機制 **`new`** 。

## <a name="syntax"></a>語法

```cpp
_PNH _set_new_handler( _PNH pNewHandler );
```

### <a name="parameters"></a>參數

*pNewHandler*<br/>
應用程式所提供記憶體處理函式的指標。 引數 0 會移除新的處理常式。

## <a name="return-value"></a>傳回值

傳回 **_set_new_handler**所註冊之先前例外狀況處理函式的指標，以便之後可以還原先前的函式。 如果未設定先前的函式，則會使用傳回值來還原預設行為。這個值可以是**Null**。

## <a name="remarks"></a>備註

如果 **_set_new_handler** **`new`** 運算子無法配置記憶體，c + + _set_new_handler 函式會指定可取得控制權的例外狀況處理函數。 如果 **`new`** 失敗，執行時間系統會自動呼叫當做引數傳遞至 **_set_new_handler**的例外狀況處理函式。 **_PNH**（定義于 New .h 中）是函式的指標，該函式會傳回類型 **`int`** ，並接受**size_t**類型的引數。 使用**size_t**來指定要配置的空間量。

沒有預設處理常式。

**_set_new_handler**基本上是垃圾收集配置。 每次函式傳回非零值時，執行階段系統都會重試配置，如果函式傳回 0 則失敗。

在程式中出現的 **_set_new_handler**函式會向執行時間系統註冊引數清單中所指定的例外狀況處理函式：

```cpp
// set_new_handler1.cpp
By default, this function's global state is scoped to the application. To change this, see [Global state in the CRT](../global-state.md).

#include <new.h>

int handle_program_memory_depletion( size_t )
{
   // Your code
}

int main( void )
{
   _set_new_handler( handle_program_memory_depletion );
   int *pi = new int[BIG_NUMBER];
}
```

您可以儲存上次傳遞至 **_set_new_handler**函式的函式位址，並于稍後再復原：

```cpp
   _PNH old_handler = _set_new_handler( my_handler );
   // Code that requires my_handler
   // . . .
   _set_new_handler( old_handler )
   // Code that requires old_handler
   // . . .
```

C++ [_set_new_mode](set-new-mode.md) 函式會設定 [malloc](malloc.md) 的新處理常式模式。 新的處理常式模式指出，在失敗時， **malloc**是否會呼叫 **_set_new_handler**所設定的新處理常式常式。 根據預設， **malloc**不會在失敗時呼叫新的處理常式常式來配置記憶體。 您可以覆寫此預設行為，如此一來，當**malloc**無法配置記憶體時， **malloc**會呼叫新的處理常式常式， **`new`** 其方式與運算子因相同原因而失敗時所執行的相同。 若要覆寫預設值，請及早在程式中呼叫：

```cpp
_set_new_mode(1);
```

，或使用 Newmode.obj 連結。

如果提供使用者定義 `operator new` ，則不會在失敗時自動呼叫新的處理常式函數。

如需詳細資訊，請參閱《C++ 語言參考》** 中的 [new](../../cpp/new-operator-cpp.md) 和 [delete](../../cpp/delete-operator-cpp.md)。

所有動態連結的 Dll 或可執行檔都有單一 **_set_new_handler**處理常式;即使您呼叫 **_set_new_handler**您的處理常式可能會被另一個取代，或者您要取代由另一個 DLL 或可執行檔所設定的處理常式。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_set_new_handler**|\<new.h>|

如需詳細的相容性資訊，請參閱 [Compatibility](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

在此範例中，配置失敗時，控制權會轉移到 MyNewHandler。 傳遞至 MyNewHandler 的引數是所要求的位元組數目。 從 MyNewHandler 傳回的值是指出是否應該重試配置的旗標︰非零值表示應該重試配置，零值則表示配置失敗。

```cpp
// crt_set_new_handler.cpp
// compile with: /c
#include <stdio.h>
#include <new.h>
#define BIG_NUMBER 0x1fffffff

int coalesced = 0;

int CoalesceHeap()
{
   coalesced = 1;  // Flag RecurseAlloc to stop
   // do some work to free memory
   return 0;
}
// Define a function to be called if new fails to allocate memory.
int MyNewHandler( size_t size )
{
   printf("Allocation failed. Coalescing heap.\n");

   // Call a function to recover some heap space.
   return CoalesceHeap();
}

int RecurseAlloc() {
   int *pi = new int[BIG_NUMBER];
   if (!coalesced)
      RecurseAlloc();
   return 0;
}

int main()
{
   // Set the failure handler for new to be MyNewHandler.
   _set_new_handler( MyNewHandler );
   RecurseAlloc();
}
```

```Output
Allocation failed. Coalescing heap.

This application has requested the Runtime to terminate it in an unusual way.
Please contact the application's support team for more information.
```

## <a name="see-also"></a>另請參閱

[記憶體配置](../../c-runtime-library/memory-allocation.md)<br/>
[calloc](calloc.md)<br/>
[受](free.md)<br/>
[realloc](realloc.md)<br/>
